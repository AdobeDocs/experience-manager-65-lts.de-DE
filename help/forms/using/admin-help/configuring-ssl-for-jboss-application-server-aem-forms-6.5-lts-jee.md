---
title: Konfigurieren von SSL für JBoss Application Server (AEM 6.5 LTS JEE)
description: Hier finden Sie Informationen dazu, wie Sie SSL für den JBoss-Anwendungs-Server konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Document Security
role: User, Developer
exl-id: 8a2fbfdc-2b6a-4c9d-beab-1908a9261003
source-git-commit: e48d0604cc8fd1cf745aafa9c70aab17944f4882
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 1%

---

# Konfigurieren von SSL für JBoss Application Server (AEM 6.5 LTS JEE)

## Überblick

Um SSL auf dem JBoss Application Server für Adobe Experience Manager (AEM) 6.5 LTS zu konfigurieren, der auf Java EE ausgeführt wird, müssen Sie die sichere HTTPS-Kommunikation aktivieren. Durch die Aktivierung von SSL werden die zwischen den Clients und dem Server ausgetauschten Daten verschlüsselt, was sie zu einer wichtigen Sicherheitsanforderung für jede AEM Forms-Produktionsbereitstellung macht.

Der Prozess umfasst zwei Hauptschritte:

- **Erhalten einer SSL** Berechtigung - entweder durch Generieren eines selbstsignierten Zertifikats oder durch Anforderung eines Zertifikats bei einer Zertifizierungsstelle.
- **Aktivieren von SSL auf JBoss** - Verwenden des Elytron-Subsystems über JBoss-CLI-Befehle.

In diesem Handbuch werden die folgenden Platzhalterwerte verwendet:

- `[appserver root]` - Der Basisordner des JBoss-Anwendungsservers, auf dem AEM Forms ausgeführt wird.
- `[type]` - Ein Ordnername, der je nach Art der durchgeführten Installation variiert.
- `[JAVA_HOME]` - Der Ordner, in dem das JDK installiert ist.

## Teil 1: Erstellen einer SSL-Berechtigung (selbstsigniert)

Wenn Sie kein Zertifikat von einer Zertifizierungsstelle haben, können Sie mit dem Java-`keytool`-Dienstprogramm eine selbstsignierte SSL-Berechtigung generieren. Dies eignet sich für Entwicklungs- oder Testumgebungen.

### Schritt 1 - KeyStore generieren

Navigieren Sie in einer Eingabeaufforderung zu `[JAVA_HOME]/bin` und führen Sie den folgenden Befehl aus, wobei Sie die Werte durch die für Ihre Umgebung geeigneten Werte ersetzen. Der Hostname muss der vollständig qualifizierte Domain-Name (FQDN) Ihres Anwendungsservers sein:

```bash
keytool -genkey -dname "CN=Host Name, OU=Group Name, O=Company Name, L=City Name, S=State, C=Country Code" \
  -alias "AEMForms Cert" -keyalg RSA \
  -keypass key_password -keystore keystorename.keystore
```

Geben Sie nach Aufforderung die `keystore_password` ein. Beachten Sie, dass das Kennwort für den Keystore und der Schlüssel identisch sein müssen.

### Schritt 2: Kopieren Sie den Keystore in das Konfigurationsverzeichnis.

Kopieren Sie den generierten Keystore in den entsprechenden Konfigurationsordner für Ihren Installationstyp:

```bash
# Windows Single Server
copy keystorename.keystore [appserver root]\standalone\configuration

# Windows Server Cluster
copy keystorename.keystore [appserver root]\domain\configuration

# Linux Single Server
cp keystorename.keystore [appserver root]/standalone/configuration

# Linux Server Cluster
cp keystorename.keystore [appserver root]/domain/configuration
```

### Schritt 3 - Zertifikatsdatei exportieren

Exportieren Sie das Zertifikat aus dem KeyStore mit einem der folgenden Befehle:

```bash
# Single Server
keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer \
  -keystore [appserver root]/standalone/configuration/keystorename.keystore

# Server Cluster
keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer \
  -keystore [appserver root]/domain/configuration/keystorename.keystore
```

Geben Sie bei Aufforderung den `keystore_password` ein.

### Schritt 4: Kopieren und Überprüfen des Zertifikats

Kopieren Sie `AEMForms_cert.cer` in das Konfigurationsverzeichnis und überprüfen Sie dann seinen Inhalt:

```bash
# Copy (Linux Single Server example)
cp AEMForms_cert.cer [appserver root]/standalone/configuration

# Verify certificate contents (Single Server)
keytool -printcert -v -file [appserver root]/standalone/configuration/AEMForms_cert.cer

# Verify certificate contents (Server Cluster)
keytool -printcert -v -file [appserver root]/domain/configuration/AEMForms_cert.cer
```

### Schritt 5 - Zertifikat in den Java TrustStore importieren

Stellen Sie vor dem Import sicher, dass auf die `cacerts` geschrieben werden kann:

```bash
# Windows: Right-click cacerts → Properties → deselect Read-only

# Linux:
chmod 777 [JAVA_HOME]/jre/lib/security/cacerts
```

Importieren Sie dann das Zertifikat:

```bash
keytool -import -alias "AEMForms Cert" -file AEMForms_cert.cer \
  -keystore [JAVA_HOME]/jre/lib/security/cacerts
```

Wenn Sie nach dem Kennwort gefragt werden, geben Sie `changeit` ein (das standardmäßige Java-TrustStore-Kennwort; fragen Sie Ihren Administrator, ob dies geändert wurde). Auf die Frage **Diesem Zertifikat vertrauen? [Nein]**, geben Sie `yes` ein. Es sollte eine Bestätigungsmeldung angezeigt werden: *„Zertifikat wurde zu Keystore hinzugefügt.“*

>[!NOTE]
>
> Wenn Sie von Workbench aus über SSL eine Verbindung zu AEM Forms herstellen, müssen Sie das Zertifikat auch auf dem Workbench-Computer installieren.

## Teil 2: Aktivieren von SSL auf JBoss mithilfe des Elytron-Subsystems

Wenn die SSL-Anmeldeinformationen eingerichtet sind, können Sie jetzt HTTPS auf JBoss mithilfe des Elytron-Sicherheits-Subsystems über die JBoss-CLI aktivieren. Vergewissern Sie sich, dass sich Ihre Keystore-Datei im entsprechenden Konfigurationsverzeichnis befindet, bevor Sie fortfahren.

>[!NOTE]
>
> Unter Windows muss jeder CLI-Befehl einzeilig und ohne Zeilenumbrüche eingegeben werden. Ersetzen Sie `keystorename.keystore` durch den tatsächlichen Dateinamen und `changeit` Sie durch Ihren Keystore/Ihr Schlüsselkennwort.

### Schritt 6a - Erstellen eines Elytron Key-Store

```bash
/subsystem=elytron/key-store=aemKeyStore:add(
  path="keystorename.keystore",
  relative-to=jboss.server.config.dir,
  type="JKS",
  credential-reference={clear-text="changeit"})
```

Ersetzen Sie `JKS` durch `PKCS12`, wenn Ihr Keystore dieses Format verwendet.

### Schritt 6b - Erstellen des Elytron Key-Managers

```bash
/subsystem=elytron/key-manager=aemKeyManager:add(
  key-store=aemKeyStore,
  credential-reference={clear-text="changeit"})
```

Wenn Ihr Keystore mehrere Zertifikateinträge enthält, geben Sie den Alias explizit an:

```bash
/subsystem=elytron/key-manager=aemKeyManager:add(
  key-store=aemKeyStore,
  alias="AEMForms Cert",
  credential-reference={clear-text="changeit"})
```

### Schritt 6c — Server-SSL-Kontext aktualisieren

```bash
/subsystem=elytron/server-ssl-context=applicationSSC:write-attribute(
  name=key-manager,
  value=aemKeyManager)
```

### Schritt 6d - Konfigurieren des Undertow-HTTPS-Listeners

Verbinden Sie den SSL-Kontext mit Undertow (dem JBoss-Webserver), um den HTTPS-Listener zu aktivieren:

```bash
/subsystem=undertow/server=default-server/https-listener=https:add(
  socket-binding=https,
  ssl-context=applicationSSC)
```

## Teil 3: Starten Sie den Anwendungsserver neu

Starten Sie JBoss nach Abschluss der Elytron-Konfiguration neu, um die Änderungen anzuwenden.

### Turnkey-Installationen (Windows-Dienste)

- Öffnen Sie **Systemsteuerung > Verwaltung > Dienste**.
- Wählen Sie **JBoss für Adobe Experience Manager Forms**.
- Wählen Sie **Aktion > Beenden** und warten Sie, bis der Dienst beendet wird.
- Wählen Sie **Aktion > Start** aus.

### Vorkonfigurierte oder manuelle JBoss-Installationen

Wechseln Sie ausgehend von einer Eingabeaufforderung zu `[appserver root]/bin`:

```bash
# Stop the server
Windows: shutdown.bat -S
Linux:   ./shutdown.sh -S

# Wait until JBoss fully shuts down, then start the server
Windows: run.bat -c <profile>
Linux:   ./run.sh -c <profile>
```

## Teil 4: Anfordern einer Berechtigung von einer Zertifizierungsstelle

Für Produktionsumgebungen sollten Sie ein Zertifikat verwenden, das von einer vertrauenswürdigen Zertifizierungsstelle (CA) ausgestellt wurde. Der Prozess umfasst das Generieren eines Schlüsselpaars, das Erstellen eines Certificate Signing Request (CSR) und den anschließenden Import des von der Zertifizierungsstelle signierten Zertifikats.

### Generieren des Keystores und Erstellen einer CSR

Navigieren Sie zu `[JAVA_HOME]/bin` und generieren Sie den Keystore:

```bash
keytool -genkey -dname "CN=Host Name, OU=Group Name, O=Company Name, L=City Name, S=State, C=Country Code" \
  -alias "AEMForms Cert" -keyalg RSA \
  -keypass key_password -keystore keystorename.keystore
```

Generieren Sie dann die CSR-Datei, die an Ihre Zertifizierungsstelle gesendet werden soll:

```bash
keytool -certreq -alias "AEMForms Cert" \
  -keystore keystorename.keystore \
  -file AEMFormscertRequest.csr
```

Senden Sie die `.csr` an Ihre Zertifizierungsstelle. Nachdem Sie das signierte Zertifikat zurückerhalten haben, führen Sie die folgenden Schritte aus.

### CA-signiertes Zertifikat importieren

Importieren Sie zuerst das CA-Stammzertifikat:

```bash
keytool -import -trustcacerts -file rootcert.pem \
  -keystore keystorename.keystore -alias root
```

Wenn das Stammzertifikat noch nicht vom Browser als vertrauenswürdig eingestuft wird, importieren Sie es ebenfalls dorthin. Importieren Sie dann das von der Zertifizierungsstelle signierte Zertifikat:

```bash
keytool -import -trustcacerts -file CACertificateName.crt \
  -keystore keystorename.keystore
```

>[!NOTE]
>
> Das importierte, von der Zertifizierungsstelle signierte Zertifikat ersetzt alle vorhandenen, selbstsignierten öffentlichen Zertifikate, sofern diese im Keystore vorhanden sind.

Nachdem das CA-Zertifikat importiert wurde, fahren Sie mit **Schritte 6a-6d** in Teil 2 (Elytron-Konfiguration) fort, starten Sie den Server neu (Teil 3) und überprüfen Sie den SSL-Zugriff.

## SSL-Zugriff überprüfen

Stellen Sie nach dem Neustart des Servers sicher, dass SSL ordnungsgemäß funktioniert, indem Sie über HTTPS auf die AEM Forms Administration Console zugreifen. Der standardmäßige SSL-Port für JBoss ist `8443`:

```
https://[host name]:8443/adminui
```

Wenn die Administration-Console erfolgreich über HTTPS geladen wurde, wurde SSL korrekt konfiguriert. Verwenden Sie Port `8443` für alle nachfolgenden SSL-Verbindungen zu AEM Forms.
