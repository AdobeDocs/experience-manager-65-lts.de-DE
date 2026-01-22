---
title: Setup für den Datenbank-Berechtigungsspeicher (auf Elytron-Basis)
description: JBoss EAP 8 unterstützt Elytron-Berechtigungsspeicher für eine sichere Datenbankkennwortverwaltung in AEM Forms mit automatisierten Skripten für die Einrichtung des Domain-Modus.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
hide: true
index: false
hidefromtoc: true
source-git-commit: 5d020671efaa4527a5f6dbb4b779c7a3351888a4
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 2%

---


# Setup für den Datenbank-Berechtigungsspeicher (auf Elytron-Basis)

## Konfigurieren des Speichers für Datenbankberechtigungen mit Elytron

JBoss EAP 8 verwendet **Elytron-Berechtigungsspeicher** um Datenbankkennwörter für AEM Forms-Bereitstellungen sicher zu verwalten. Adobe bietet **automatisierte Skripte** um die Erstellung und Konfiguration des Elytron-basierten Berechtigungsspeichers im Domain-Modus zu vereinfachen.

Diese Einrichtung muss abgeschlossen sein **vor dem Starten des JBoss-Domänencontrollers**.

### Voraussetzungen

* Der **JBoss-Server muss vollständig angehalten werden** bevor das Skript zur Erstellung des Berechtigungsspeichers ausgeführt wird.
* Die Erstellung des Speichers für Anmeldeinformationen darf nur im **-Modus**.

So stoppen Sie JBoss, wenn es ausgeführt wird:

* **Windows**

  ```
  <JBOSS_HOME>\bin\jboss-cli.bat --connect command=:shutdown
  ```

* **Linux/UNIX**

  ```
  <JBOSS_HOME>/bin/jboss-cli.sh --connect command=:shutdown
  ```

### Herunterladen von Skripten

Laden Sie das entsprechende Skript für Ihr Betriebssystem herunter:

| Skriptname | Betriebssystem |
| -------------------------------- | ---------------- |
| `create-elytron-cred-domain.bat` | Windows |
| `create-elytron-cred-domain.sh` | Linux/UNIX |

Machen Sie unter Linux das Skript ausführbar:

```
chmod +x create-elytron-cred-domain.sh
```

### Konfigurationsschritte

#### Schritt 1: Herunterladen und Platzieren des Skripts

Laden Sie das entsprechende Skript herunter und platzieren Sie es im folgenden Verzeichnis:

```
<JBOSS_HOME>/bin
```

#### Schritt 2: Skript ausführen

* **Windows**

  ```
  cd <JBOSS_HOME>\bin
  create-elytron-cred-domain.bat
  ```

* **Linux/UNIX**

  ```
  cd <JBOSS_HOME>/bin
  ./create-elytron-cred-domain.sh
  ```

#### Schritt 3: Bereitstellen der erforderlichen Informationen

Während der Ausführung fordert das Skript die folgenden Eingaben an:

1. **JBOSS_HOME-Pfad**
Geben Sie den vollständigen Pfad zum JBoss-Installationsverzeichnis ein.

2. **Name der Datenbankkonfigurationsdatei**
Geben Sie je nach Datenbank einen der folgenden Werte ein:

   * `domain_oracle.xml`
   * `domain_mysql.xml`
   * `domain_mssql.xml`

3. **Zugangsdaten-Store-Kennwort**
Geben Sie ein sicheres Kennwort ein, um den Berechtigungsspeicher zu schützen.

   > Dieses Kennwort wird bei der Eingabe ausgeblendet und muss für spätere Schritte gespeichert werden.

4. **Datenbankkennwort**
Geben Sie das tatsächliche Kennwort für die Datenbankverbindung ein.

#### Schritt 4: Skriptausführung und -validierung

Das Skript führt die folgenden Aktionen automatisch aus:

* Erstellt `cred-store.p12` in:

  ```
  <JBOSS_HOME>/domain/configuration/
  ```

* Erstellt die folgenden Berechtigungsalias:

   * `EncryptDBPassword`
   * `EncryptDBPassword_IDP_DS`
   * `EncryptDBPassword_EDC_DS`
   * `EncryptDBPassword_AEM_DS`
* Prüft, ob alle Aliase erfolgreich hinzugefügt wurden

Bei erfolgreicher Ausführung wird die Erstellung des Berechtigungsspeichers und die Alias-Überprüfung bestätigt.

#### Schritt 5: JVM-Optionen konfigurieren

Aktualisieren Sie die JBoss-Domain-Startkonfiguration, um das Kennwort für den Berechtigungsspeicher anzugeben.

* **Linux**
Bearbeiten:

  ```
  <JBOSS_HOME>/bin/domain.conf
  ```

  Hinzufügen:

  ```
  JAVA_OPTS="$JAVA_OPTS -DCS_PASS=YourCredStorePassword"
  ```

* **Windows**
Bearbeiten:

  ```
  <JBOSS_HOME>/bin/domain.conf.bat
  ```

  Hinzufügen:

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=YourCredStorePassword"
  ```

Ersetzen Sie `YourCredStorePassword` durch das Kennwort, das bei der Erstellung des Berechtigungsspeichers eingegeben wurde.

Die Domain-Konfigurationsdateien verweisen mithilfe der `${CS_PASS}`-Variablen auf diesen Wert.


#### Schritt 6: Domain-Konfiguration überprüfen

Öffnen Sie die Konfigurationsdatei der Datenbank-Domain:

```
<JBOSS_HOME>/domain/configuration/<domain_*.xml>
```

Stellen Sie sicher, dass Datenquellen auf den Berechtigungsspeicher von Elytron verweisen:

```xml
<security>
    <user-name>your_database_username</user-name>
    <credential-reference store="db-creds" alias="EncryptDBPassword_IDP_DS"/>
</security>
```

Jede Datenquelle verwendet einen bestimmten Alias:

* **IDP_DS:** `EncryptDBPassword_IDP_DS`
* **EDC_DS:** `EncryptDBPassword_EDC_DS`
* **AEM_DS:** `EncryptDBPassword_AEM_DS`
* **DefaultDS / ExampleDS:** `EncryptDBPassword`

Alle Aliase verweisen auf dasselbe im Berechtigungsspeicher gespeicherte Datenbankkennwort.

>[!NOTE]
>
>* Konfigurieren Sie den Berechtigungsspeicher nur auf dem primären Knoten.
>* Sekundäre Knoten verwenden automatisch die Domain-Konfiguration, die mit dem Primärknoten synchronisiert wurde.
