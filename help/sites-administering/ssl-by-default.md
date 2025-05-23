---
title: SSL/TLS by Default
description: Erfahren Sie, wie Sie die Funktion SSL by Default in AEM 6.5 verwenden.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
exl-id: 3fd6a54b-9220-4bb2-9625-4f459c4d3aa8
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 100%

---

# SSL/TLS By Default{#ssl-tls-by-default}

Im Bestreben, die Sicherheit von AEM kontinuierlich weiter zu verbessern, hat Adobe eine Funktion namens „SSL By Default“ (SSL als Standard) eingeführt. Der Zweck besteht darin, die Verwendung von HTTPS für die Verbindung mit AEM-Instanzen zu fördern.

## Aktivieren von „SSL/TLS By Default“ {#enabling-ssl-tls-by-default}

Sie können mit der Konfiguration von „SSL/TLS By Default“ beginnen, indem Sie in Ihrem AEM-Startbildschirm auf die entsprechende Posteingangsnachricht klicken. Um den Posteingang zu erreichen, klicken Sie auf das Glockensymbol in der oberen rechten Ecke des Bildschirms. Klicken Sie dann auf **Alle anzeigen**. Dadurch wird eine Liste aller bestellten Warnungen in einer Listenansicht angezeigt.

Wählen und öffnen Sie in der Liste die Warnung **HTTPS konfigurieren**:

![chlimage_1-103](assets/chlimage_1-103.png)

>[!NOTE]
>
>Wenn die Warnung **HTTPS konfigurieren** nicht im Posteingang vorhanden ist, können Sie direkt zum HTTPS-Assistenten navigieren, indem Sie *<http://serveraddress:serverport/libs/granite/security/content/sslConfig.html?item=configuration%2fconfiguressl&_charset_=utf-8>* aufrufen.

Ein Service-Benutzer mit dem Namen **ssl-service** wurde für diese Funktion erstellt. Nachdem Sie die Warnung geöffnet haben, werden Sie durch den folgenden Konfigurationsassistenten geleitet:

1. Richten Sie zunächst die Store-Anmeldedaten ein. Dies sind Anmeldedaten für den KeyStore des Systembenutzers **ssl-service**, der den privaten Schlüssel und den TrustStore für den HTTPS-Listener enthält.

   ![chlimage_1-104](assets/chlimage_1-104.png)

1. Nachdem Sie die Anmeldedaten eingegeben haben, klicken Sie auf **Weiter** in der rechten oberen Ecke der Seite. Laden Sie dann den zugehörigen privaten Schlüssel und das zugehörige Zertifikat für die SSL/TLS-Verbindung hoch.

   ![chlimage_1-105](assets/chlimage_1-105.png)

   >[!NOTE]
   >
   >Weitere Informationen dazu, wie Sie einen privaten Schlüssel und ein Zertifikat für die Verwendung im Assistenten erzeugen, finden Sie in [diesem Verfahren](/help/sites-administering/ssl-by-default.md#generating-a-private-key-certificate-pair-to-use-with-the-wizard).

1. Geben Sie anschließend den HTTPS-Hostnamen und den TCP-Port für den HTTPS-Listener an.

   ![screen_shot_2018-07-25at31658pm](assets/screen_shot_2018-07-25at31658pm.png)

## Automatisierung von „SSL/TLS By Default“ {#automating-ssl-tls-by-default}

Es gibt drei Möglichkeiten, „SSL/TLS By Default“ automatisch zu konfigurieren.

### Über eine HTTP-POST-Anfrage {#via-http-post}

Die erste Methode umfasst das Posten auf dem SSLSetup-Server, der vom Konfigurationsassistenten verwendet wird:

```shell
POST /libs/granite/security/post/sslSetup.html
```

Sie können die folgende Payload in Ihrem POST verwenden, um die Konfiguration zu automatisieren:

```xml
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="keystorePassword"

test
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="keystorePasswordConfirm"
test
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="truststorePassword"
test
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="truststorePasswordConfirm"
test
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="privatekeyFile"; filename="server.der"
Content-Type: application/x-x509-ca-cert

------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="certificateFile"; filename="server.crt"
Content-Type: application/x-x509-ca-cert

------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="httpsPort"
8443
```

Das Servlet antwortet wie jedes Sling-POST-Servlet mit 200 OK oder einem Fehler-HTTP-Statuscode. Details zum Status finden Sie im HTML-Textkörper der Antwort.

Im Folgenden finden Sie Beispiele für eine erfolgreiche Antwort und einen Fehler.

**BEISPIEL FÜR EINE ERFOLGREICHE ANTWORT** (Status = 200):

```xml
<!DOCTYPE html>
<html lang='en'>
<head>
<title>OK</title>
</head>
<body>
<h1>OK</h1>
<dl>
<dt class='foundation-form-response-status-code'>Status</dt>
<dd>200</dd>
<dt class='foundation-form-response-status-message'>Message</dt>
<dd>SSL successfully configured</dd>
<dt class='foundation-form-response-title'>Title</dt>
<dd>OK</dd>
<dt class='foundation-form-response-description'>Description</dt>
<dd>HTTPS has been configured on port 8443. The private key and
certificate were stored in the key store of the user ssl-service.
Take note of the key store password you provided. You need
it for any subsequent updating of the private key or certificate.</dd>
</dl>
<h2>Links</h2>
<ul class='foundation-form-response-links'>
<li><a class='foundation-form-response-redirect' href='/'>Done</a></li>
</ul>
</body>
</html>
```

**BEISPIEL FÜR EINEN FEHLER** (Status = 500):

```xml
<!DOCTYPE html>
<html lang='en'>
<head>
<title>Error</title>
</head>
<body>
<h1>Error</h1>
<dl>
<dt class='foundation-form-response-status-code'>Status</dt>
<dd>500</dd>
<dt class='foundation-form-response-status-message'>Message</dt>
<dd>The provided file is not a valid key, DER format expected</dd>
<dt class='foundation-form-response-title'>Title</dt>
<dd>Error</dd>
</dl>
</body>
</html>
```

### Über ein Paket {#via-package}

Alternativ können Sie die SSL/TLS-Einrichtung automatisieren, indem Sie ein Paket hochladen, das bereits die folgenden erforderlichen Elemente enthält:

* Der Keystore des SSL-Service-Benutzers bzw. -Benutzerin. Dieser befindet sich unter */home/users/system/security/ssl-service/keystore* im Repository.
* Die `GraniteSslConnectorFactory`-Konfiguration

### Generieren eines Paares aus privatem Schlüssel/Zertifikat für die Verwendung im Assistenten {#generating-a-private-key-certificate-pair-to-use-with-the-wizard}

Nachstehend finden Sie ein Beispiel für das Erstellen eines selbstsignierten Zertifikats im DER-Format, das der SSL/TSL-Assistent verwenden kann. Installieren Sie OpenSSL basierend auf dem Betriebssystem, öffnen Sie die OpenSSL-Eingabeaufforderung und ändern Sie das Verzeichnis in den Ordner, in dem Sie den privaten Schlüssel/das Zertifikat generieren möchten.

>[!NOTE]
>
>Die Verwendung eines selbstsignierten Zertifikats dient nur zu Beispielzwecken. Verwenden Sie dies nicht in der Produktion.

1. Erstellen Sie zunächst den privaten Schlüssel:

   ```shell
   openssl genrsa -aes256 -out localhostprivate.key 4096
   openssl rsa -in localhostprivate.key -out localhostprivate.key
   ```

1. Generieren Sie dann mithilfe des privaten Schlüssels ein Certificate Signing Request (CSR):

   ```shell
   openssl req -sha256 -new -key localhostprivate.key -out localhost.csr -subj "/CN=localhost"
   ```

1. Generieren Sie das SSL/TLS-Zertifikat und signieren Sie es mit dem privaten Schlüssel. In diesem Beispiel läuft es in einem Jahr ab:

   ```shell
   openssl x509 -req -days 365 -in localhost.csr -signkey localhostprivate.key -out localhost.crt
   ```

1. Konvertieren Sie den privaten Schlüssel in das DER-Format. Dies liegt daran, dass der SSL-Assistent den Schlüssel im DER-Format erfordert:

   ```shell
   openssl pkcs8 -topk8 -inform PEM -outform DER -in localhostprivate.key -out localhostprivate.der -nocrypt
   ```

1. Laden Sie abschließend in Schritt 2 des visuellen SSL/TLS-Assistenten, der am Anfang dieser Seite beschrieben wird, die Datei **localhostprivate.der** als privaten Schlüssel und **localhost.crt** als SSL-/TLS-Zertifikat hoch.

### Aktualisieren der SSL-/TLS-Konfiguration über cURL {#updating-the-ssl-tls-configuration-via-curl}

>[!NOTE]
>
>Eine zentrale Liste mit nützlichen cURL-Befehlen in AEM finden Sie unter [Verwenden von cURL in AEM](https://helpx.adobe.com/de/experience-manager/6-4/sites/administering/using/curl.html).

Sie können die SSL-/TLS-Konfiguration auch mithilfe des cURL-Tools automatisieren. Sie können dies tun, indem Sie die Konfigurationsparameter an die folgende URL senden:

*https://&lt;Server-Adresse>:&lt;Serverport>/libs/granite/security/post/sslSetup.html*

Nachfolgend finden Sie die Parameter, mit denen Sie die verschiedenen Einstellungen im Konfigurationsassistenten ändern können:

* `-F "keystorePassword=password"` – KeyStore-Kennwort

* `-F "keystorePasswordConfirm=password"` – Bestätigung des KeyStore-Kennworts

* `-F "truststorePassword=password"` – TrustStore-Kennwort

* `-F "truststorePasswordConfirm=password"` – Bestätigung des TrustStore-Kennworts

* `-F "privatekeyFile=@localhostprivate.der"` – Angabe des privaten Schlüssels

* `-F "certificateFile=@localhost.crt"` – Angabe des Zertifikats

* `-F "httpsHostname=host.example.com"` – Angabe des Host-Namens
* `-F "httpsPort=8443"` – Port, den der HTTPS-Listener abhört

>[!NOTE]
>
>Die schnellste Art, cURL auszuführen, um die SSL-/TLS-Konfiguration zu automatisieren, ist über den Ordner, in dem sich die DER- und CRT-Dateien befinden. Alternativ dazu können Sie den vollständigen Pfad in den Argumenten `privatekeyFile` und „certificateFile“ festlegen.
>
>Außerdem müssen Sie authentifiziert sein, um die Aktualisierung durchzuführen. Stellen Sie also sicher, dass Sie den cURL-Befehl mit dem angehängten Parameter `-u user:passeword` versehen.
>
>Ein korrekter cURL-Post-Befehl sollte wie folgt aussehen:

```shell
curl -u user:password -F "keystorePassword=password" -F "keystorePasswordConfirm=password" -F "truststorePassword=password" -F "truststorePasswordConfirm=password" -F "privatekeyFile=@localhostprivate.der" -F "certificateFile=@localhost.crt" -F "httpsHostname=host.example.com" -F "httpsPort=8443" https://host:port/libs/granite/security/post/sslSetup.html
```

#### Mehrere Zertifikate verwenden cURL {#multiple-certificates-using-curl}

Sie können dem Servlet eine Kette von Zertifikaten senden, indem Sie den Parameter „certificateFile“ wie folgt wiederholen:

`-F "certificateFile=@root.crt" -F "certificateFile=@localhost.crt"..`

Stellen Sie nach Ausführung des Befehls sicher, dass alle Zertifikate an den KeyStore gesendet wurden. Überprüfen Sie die **Keystore-Einträge** von:
[http://localhost:4502/libs/granite/security/content/v2/usereditor.html/home/users/system/security/ssl-service](http://localhost:4502/libs/granite/security/content/v2/usereditor.html/home/users/system/security/ssl-service)

### Aktivieren einer TLS 1.3-Verbindung {#enabling-tls-connection}

1. Wechseln Sie zur Web-Konsole.
1. Navigieren Sie dann zu **OSGi** –> **Konfiguration** –> **Adobe Granite SSL Connector Factory**.
1. Gehen Sie zum Feld **Enthaltene Chiffre-Suites** und fügen Sie die folgenden Einträge hinzu. Sie können jede Ergänzung bestätigen, indem Sie die Schaltfläche „**+**“ auf der linken Seite des Felds betätigen, nachdem jede hinzugefügt wurde:

   * `TLS_AES_256_GCM_SHA384`
   * `TLS_AES_128_GCM_SHA256`
   * `TLS_CHACHA20_POLY1305_SHA256`
   * `TLS_AES_128_CCM_SHA256`
   * `TLS_AES_128_CCM_8_SHA256`
