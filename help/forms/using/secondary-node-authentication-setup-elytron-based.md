---
title: Einrichtung der Sekundären Knotenauthentifizierung (auf Elytron-Basis)
description: JBoss EAP 8 verwendet Elytron, um eine sichere Kommunikation und Registrierung sekundärer Knoten mit dem primären Domain-Controller zu ermöglichen.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
source-git-commit: f093f39fb535209297940cff13a99c7631812152
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 5%

---


# Einrichtung der Sekundären Knotenauthentifizierung (auf Elytron-Basis)

## Konfigurieren der Sekundären Knotenauthentifizierung mit Elytron

JBoss EAP 8 verwendet **Elytron** zur Authentifizierung der Kommunikation zwischen **primären und sekundären Knoten** in einer Cluster-Bereitstellung. Diese Konfiguration gewährleistet eine sichere Registrierung und Kommunikation von sekundären Knoten mit dem primären Domain-Controller.

Je nach Umgebung und Sicherheitsanforderungen stehen zwei Einrichtungsoptionen zur Verfügung.


## Voraussetzungen

* Ein **Verwaltungsbenutzer mit dem Namen`secondary`** muss auf dem **primären Knoten“ erstellt**.
* Führen Sie diese Konfiguration **nur auf sekundären Knoten)**.
* Wiederholen Sie die Konfiguration für **jeden sekundären Knoten** im Cluster.
* **JBoss muss auf** primären und sekundären Knoten vollständig angehalten werden.
* Alle Vorgänge zum Speichern von Anmeldeinformationen müssen im **Offline-Modus** ausgeführt werden.

So stoppen Sie JBoss, wenn es ausgeführt wird:

* **Windows**

  ```
  <JBOSS_HOME>\bin\jboss-cli.bat --connect command=:shutdown
  ```

* **Linux/UNIX**

  ```
  <JBOSS_HOME>/bin/jboss-cli.sh --connect command=:shutdown
  ```

## Setup-Option auswählen

* **Option 1: Schnelleinrichtung mit dem standardmäßigen Berechtigungsspeicher**
Empfohlen für niedrigere Umgebungen und Tests.

* **Option 2: Einrichtung eines benutzerdefinierten Berechtigungsspeichers**
Wird für Produktions- und sichere Umgebungen empfohlen.

## Option 1: Schnelleinrichtung mit dem standardmäßigen Berechtigungsspeicher

**Am besten geeignet für:** Entwicklung, Tests und Schnellsetup-Szenarien.

### Überblick

* Eine standardmäßige Datei für den Berechtigungsspeicher (`cs_secondary_hc.p12`) ist vorkonfiguriert.
* Das Standardkennwort für den Berechtigungsspeicher ist bereits in `domain.conf` festgelegt.
* Nur der Authentifizierungskennwort-Alias muss hinzugefügt werden.

### Konfigurationsschritte

#### Schritt 1: Standardberechtigungsspeicher überprüfen

Bestätigen, dass die standardmäßige Datei für den Berechtigungsspeicher vorhanden ist:

* **Windows**

  ```
  <JBOSS_HOME>\domain\configuration\cs_secondary_hc.p12
  ```

* **Linux**

  ```
  <JBOSS_HOME>/domain/configuration/cs_secondary_hc.p12
  ```

Wenn die Datei nicht vorhanden ist, verwenden Sie **Option 2**.

#### Schritt 2: Authentifizierungs-Passwort-Alias hinzufügen

Führen Sie den folgenden Befehl aus `<JBOSS_HOME>/bin` aus:

* **Windows**

  ```
  elytron-tool.bat credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "password" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "password" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

> Der geheime Wert muss mit dem Kennwort übereinstimmen, das beim Erstellen des `secondary` Benutzers auf dem primären Knoten verwendet wurde.

#### Schritt 3: Überprüfen der domain.conf-Konfiguration

Stellen Sie sicher, dass der folgende Eintrag bereits existiert (keine Änderungen erforderlich):

* **Windows**

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DSec_Auth_PASS=password"
  ```

* **Linux**

  ```
  JAVA_OPTS="$JAVA_OPTS -DSec_Auth_PASS=password"
  ```

#### Schritt 4: Knoten starten

1. Starten Sie den **primären Knoten** und warten Sie, bis er vollständig initialisiert wurde.
2. Starten Sie den **sekundären Knoten**.

### Überprüfung

Überprüfen Sie die Protokolle:

* **Primärer Knoten**

  ```
  <JBOSS_HOME>/domain/log/host-controller.log
  ```

  ```
  Registered remote secondary host "secondary"
  ```

* **Sekundärer Knoten**

  ```
  Connected to primary host controller
  ```

## Option 2: Einrichtung eines Speichers für benutzerdefinierte Anmeldeinformationen (Produktion)

**Am besten geeignet für:** Produktionsumgebungen, die erhöhte Sicherheit erfordern.

### Konfigurationsschritte

#### Schritt 1: Standard-Berechtigungsspeicher entfernen (falls vorhanden)

Wenn der Standardberechtigungsspeicher vorhanden ist, benennen Sie ihn um:

* **Windows**

  ```
  rename cs_secondary_hc.p12 cs_secondary_hc.p12.bak
  ```

* **Linux**

  ```
  mv cs_secondary_hc.p12 cs_secondary_hc.p12.bak
  ```

#### Schritt 2: Erstellen eines benutzerdefinierten Berechtigungsspeichers

Von `<JBOSS_HOME>/bin`:

* **Windows**

  ```
  elytron-tool.bat credential-store --create --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --create --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12"
  ```

#### Schritt 3: Authentifizierungs-Passwort-Alias hinzufügen

* **Windows**

  ```
  elytron-tool.bat credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

#### Schritt 4: Aktualisieren Sie domain.conf

Aktualisieren Sie die Kennwortreferenz für den Berechtigungsspeicher:

* **Windows**

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DSec_Auth_PASS=YourCustomPassword"
  ```

* **Linux**

  ```
  JAVA_OPTS="$JAVA_OPTS -DSec_Auth_PASS=YourCustomPassword"
  ```

#### Schritt 5: Überprüfen der XML-Konfiguration

Stellen Sie sicher, dass `host-secondary.xml` den konfigurierten Berechtigungsspeicher und die Authentifizierungs-Client-Einträge enthält.
Wenn die Standardkonfiguration vorhanden ist, sind keine Änderungen erforderlich.


#### Schritt 6: Knoten starten

1. Starten Sie den **primären Knoten** und warten Sie, bis er vollständig gestartet wurde.
2. Starten Sie den **sekundären Knoten**.

### Überprüfung

Bestätigen Sie die erfolgreiche Registrierung mithilfe der Host-Controller-Protokolle auf beiden Knoten.

## Zusammenfassung

* **Option 1** bietet eine schnelle Einrichtung mithilfe eines vorkonfigurierten Berechtigungsspeichers.
* **Option 2** ermöglicht eine höhere Sicherheit mithilfe eines benutzerdefinierten Kennworts für den Berechtigungsspeicher.
* Die Konfiguration muss abgeschlossen **nur auf sekundären Knoten**.
* Die Primäre Knotenkonfiguration wird automatisch in der gesamten Domain wiederverwendet.

