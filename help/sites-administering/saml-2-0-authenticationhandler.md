---
title: SAML 2.0-Authentifizierungs-Handler
description: Hier finden Sie Informationen zum SAML 2.0-Authentifizierungs-Handler in AEM.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
exl-id: ee438c55-88cd-4f55-873e-16376b36fa7b
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 100%

---

# SAML 2.0-Authentifizierungs-Handler {#saml-authentication-handler}

AEM umfasst einen [SAML](https://saml.xml.org/saml-specifications)-Authentifizierungs-Handler. Dieser Handler unterstützt das [SAML](https://saml.xml.org/saml-specifications) 2.0-Authentifizierungsanforderungsprotokoll (Web-SSO-Profil), das die `HTTP POST`-Bindung verwendet.

Folgendes wird unterstützt:

* Signierung und Verschlüsselung von Nachrichten
* Automatische Erstellung von Benutzern
* Synchronisieren von Gruppen mit vorhandenen Gruppen in AEM
* Durch Dienstleister und Identitätsanbieter eingeleitete Authentifizierung

Dieser Handler speichert die verschlüsselte SAML-Antwortnachricht im Benutzerknoten (`usernode/samlResponse`), um die Kommunikation mit Dienstleistern von Drittanbietern zu erleichtern.

>[!NOTE]
>
>[Hier](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17481.html?lang=de) finden Sie eine Demonstration zur Integration von AEM und SAML.

## Konfigurieren des SAML 2.0-Authentifizierungs-Handlers {#configuring-the-saml-authentication-handler}

Die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) bietet Zugriff auf die [SAML](https://saml.xml.org/saml-specifications) 2.0-Authentifizierungs-Handler-Konfiguration namens **Adobe Granite SAML 2.0 Authentication Handler**. Die folgenden Eigenschaften können festgelegt werden.

>[!NOTE]
>
>Der SAML 2.0-Authentifizierungs-Handler ist standardmäßig deaktiviert. Legen Sie mindestens eine der folgenden Eigenschaften fest, um den Handler zu aktivieren:
>
>* Die POST-URL des Identitätsanbieters bzw. die IDP-URL.
>* Entitäts-ID des Dienstleisters
>

>[!NOTE]
>
>SAML-Assertionen werden signiert und können optional verschlüsselt sein. Damit dies funktioniert, müssen Sie zumindest das öffentliche Zertifikat des Identitätsanbieters im TrustStore angeben. Weitere Informationen finden Sie im Abschnitt [Hinzufügen des Identitätsanbieterzertifikats zum TrustStore](/help/sites-administering/saml-2-0-authenticationhandler.md#add-the-idp-certificate-to-the-aem-truststore).

**Pfad** Repository-Pfad, für den dieser Authentifizierungs-Handler von Sling verwendet werden soll. Wenn dieser leer ist, wird der Authentifizierungs-Handler deaktiviert.

**Service-Rangfolge** Position in der Rangfolge der OSGi-Framework-Services. Gibt an, mit welcher Priorität dieser Service aufgerufen wird. Dies ist ein ganzzahliger Wert, wobei höhere Werte Vorrang haben.

**IDP-Zertifikatalias** Das Alias des IDP-Zertifikats im globalen TrustStore. Wenn diese Eigenschaft nicht angegeben wird, ist der Authentifizierungs-Handler deaktiviert. Im Kapitel „Hinzufügen des Identitätsanbieterzertifikats zum AEM-TrustStore“ weiter unten finden Sie Informationen dazu, wie Sie dies einrichten.

**IDP-URL** Die URL des IDP, an den die SAML-Authentifizierungsanfrage gesendet werden soll. Wenn diese Eigenschaft nicht angegeben wird, ist der Authentifizierungs-Handler deaktiviert.

>[!CAUTION]
>
>Der Hostname des Identitätsanbieters muss der OSGi-Konfiguration **Apache Sling Referrer Filter** hinzugefügt werden. Weitere Informationen finden Sie im Abschnitt [Web-Konsole](/help/sites-deploying/configuring-osgi.md).

**Entitäts-ID des Dienstleisters** ID, die diesen Dienstleister eindeutig beim Identitätsanbieter identifiziert. Wenn diese Eigenschaft nicht angegeben wird, ist der Authentifizierungs-Handler deaktiviert.

**Standardweiterleitung** Der Standardort, an den nach einer erfolgreichen Authentifizierung weitergeleitet wird.

>[!NOTE]
>
>Dieser Ort wird nur verwendet, wenn das Cookie `request-path` nicht festgelegt ist. Wenn Sie eine Seite unterhalb des konfigurierten Pfads ohne gültiges Anmelde-Token anfordern, wird der angeforderte Pfad in einem Cookie gespeichert
>und der Browser wird nach erfolgreicher Authentifizierung erneut an diesen Ort weitergeleitet.

**Benutzer-ID-Attribut** Der Name des Attributs, das die Benutzer-ID enthält, die zur Authentifizierung und Erstellung des Benutzers im CRX-Repository verwendet wird.

>[!NOTE]
>
>Die Benutzer-ID wird nicht aus dem Knoten `saml:Subject` der SAML-Assertion abgerufen, sondern aus diesem `saml:Attribute`.

**Verschlüsselung verwenden** Gibt an, ob dieser Authentifizierungs-Handler verschlüsselte SAML-Assertionen erwartet.

**CRX-Benutzer automatisch erstellen** Gibt an, ob nicht vorhandene Benutzer nach erfolgreicher Authentifizierung automatisch im Repository erstellt werden sollen.

>[!CAUTION]
>
>Falls die automatische Erstellung von CRX-Benutzern deaktiviert ist, müssen die Benutzer manuell erstellt werden.

**Zu Gruppen hinzufügen** Gibt an, ob Benutzer nach erfolgreicher Authentifizierung automatisch zu CRX-Gruppen hinzugefügt werden sollen.

**Gruppenmitgliedschaft** Der Name des „saml:Attribute“, das eine Liste von CRX-Gruppen enthält, denen dieser Benutzer hinzugefügt werden muss.

## Hinzufügen des Identitätsanbieterzertifikats zum AEM-TrustStore {#add-the-idp-certificate-to-the-aem-truststore}

SAML-Assertionen werden signiert und können optional verschlüsselt sein. Damit dies funktionieren kann, müssen Sie mindestens das öffentliche Identitätsanbieterzertifikat im Repository bereitstellen. Dazu müssen Sie folgende Schritte durchführen:

1. Wechseln Sie zu *http:/Server-Adresse:Serverport/libs/granite/security/content/truststore.html*.
1. Klicken Sie auf **[!UICONTROL TrustStore-Link erstellen]**.
1. Geben Sie das Kennwort für den TrustStore ein und klicken Sie auf **[!UICONTROL Speichern]**.
1. Klicken Sie auf **[!UICONTROL TrustStore verwalten]**.
1. Laden Sie das Identitätsanbieterzertifikat hoch.
1. Notieren Sie sich den Zertifikatsalias. Im Folgenden Beispiel lautet das Alias **[!UICONTROL admin#1436172864930]**.

   ![chlimage_1-372](assets/chlimage_1-372.png)

## Hinzufügen des Schlüssels und der Zertifikatkette des Dienstleisters zum AEM-Schlüsselspeicher {#add-the-service-provider-key-and-certificate-chain-to-the-aem-keystore}

>[!NOTE]
>
>Die folgenden Schritte sind obligatorisch. Andernfalls wird die folgende Ausnahme ausgelöst: `com.adobe.granite.keystore.KeyStoreNotInitialisedException: Uninitialised system trust store`

1. Wechseln Sie zu [http://localhost:4502/libs/granite/security/content/useradmin.html](http://localhost:4502/libs/granite/security/content/useradmin.html).
1. Bearbeiten Sie den Benutzer `authentication-service`.
1. Erstellen Sie einen KeyStore, indem Sie unter **Kontoeinstellungen** auf **KeyStore erstellen** klicken.

>[!NOTE]
>
>Die folgenden Schritte sind nur erforderlich, wenn der Handler in der Lage sein muss, Nachrichten zu signieren oder zu verschlüsseln.

1. Erstellen Sie das Zertifikat/Schlüsselpaar für AEM. Der Befehl zur Erzeugung über OpenSSL sollte dem folgenden Beispiel ähneln:

   `openssl req -newkey rsa:2048 -new -x509 -days 3652 -nodes -out certificate.crt -keyout key.pem`

1. Konvertieren Sie den Schlüssel mit DER-Codierung in das PKCS#8-Format. Dies ist das Format, das für den AEM-Keystore erforderlich ist.

   `openssl pkcs8 -topk8 -inform PEM -outform DER -in key.pem -out key.der -nocrypt`

1. Laden Sie die Datei mit dem privaten Schlüssel hoch, indem Sie auf **Datei mit privatem Schlüssel auswählen** klicken.
1. Laden Sie die Zertifikatdatei hoch, indem Sie auf **Zertifikatkettendateien auswählen** klicken.
1. Weisen Sie einen Alias zu, wie im Folgenden gezeigt:

   ![chlimage_1-373](assets/chlimage_1-373.png)

## Konfigurieren eines Loggers für SAML {#configure-a-logger-for-saml}

Sie können einen Logger einrichten, um alle Probleme zu debuggen, die aufgrund der falschen Konfiguration von SAML entstehen können. Gehen Sie dazu wie folgt vor:

1. Wechseln Sie zur Web-Konsole unter *http://localhost:4502/system/console/configMgr*.
1. Suchen Sie nach dem Eintrag **Apache Sling Logging-Logger-Konfiguration** und klicken Sie darauf.
1. Erstellen Sie einen Logger mit folgender Konfiguration:

   * **Protokollebene:** Debugging
   * **Protokolldatei**: logs/saml.log
   * **Logger**: com.adobe.granite.auth.saml
