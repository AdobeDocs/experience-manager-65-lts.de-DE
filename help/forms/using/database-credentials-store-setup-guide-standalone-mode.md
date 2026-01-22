---
title: Handbuch zum Einrichten des Speichers für Datenbankberechtigungen (eigenständiger Modus)
description: Suchen Sie die Einrichtung des Speichers für Datenbankberechtigungen für AEM Forms JEE unter JBoss/Red Hat EAP im eigenständigen Modus.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
hide: true
index: false
hidefromtoc: true
source-git-commit: 5d020671efaa4527a5f6dbb4b779c7a3351888a4
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 2%

---


# Handbuch zum Einrichten des Speichers für Datenbankberechtigungen (eigenständiger Modus)

## Überblick

Dieses Handbuch behandelt die **Einrichtung des Speichers für Datenbankberechtigungen** für AEM Forms JEE unter JBoss/Red Hat EAP **eigenständiger Modus**. Dies ist bei der manuellen Installation erforderlich.

**Dieses Handbuch behandelt:**

- Erstellen des Speichers für Datenbankberechtigungen (`cred-store.p12`)
- Sicheres Hinzufügen von Datenbankkennwort-Aliassen
- Konfigurieren von JBoss zur Verwendung des Berechtigungsspeichers

**KRITISCH:** Diese Skripte werden nur im **-Modus**. JBoss muss vor Ausführung dieser Skripte angehalten werden. Die Skripte verwenden `embed-server` Modus, bei dem der Server angehalten werden muss.

**Hinweis:** Dies ist **kein** Installationshandbuch. Dieses Dokument setzt Folgendes voraus:

- JBoss ist bereits installiert
- Eigenständige Konfigurationsdateien (`lc_oracle.xml`, `lc_mysql.xml` oder `lc_mssql.xml`) sind bereits konfiguriert
- Datenbank ist eingerichtet und zugänglich

Wenn Sie vollständige eigenständige Installationsanweisungen benötigen, lesen Sie bitte das Haupt-Installationshandbuch.

## Voraussetzungen

Bevor Sie diese Skripte ausführen, stellen Sie Folgendes sicher:

1. **JBoss MUSS angehalten werden**
   - Diese Skripte funktionieren **NUR OFFLINE-MODUS**
   - Die Skripte verwenden `embed-server` , wodurch der Server angehalten werden muss
   - Wenn JBoss ausgeführt wird, schlagen die Skripte fehl
   - Überprüfen, ob JBoss ausgeführt wird:
      - Windows: Überprüfen des Task-Managers auf `java.exe` Prozess
      - Linux: `ps aux | grep jboss` oder `ps aux | grep java`
   - JBoss bei Ausführung stoppen:
      - Drücken Sie `Ctrl+C` im Terminal, auf dem JBoss ausgeführt wird
      - Oder beenden Sie den Prozess manuell

2. **Sie haben das Datenbankkennwort bereit**

3. **Sie haben sich für ein sicheres Kennwort für den Berechtigungsspeicher entschieden**

4. **Sie wissen, welche Datenbankkonfigurationsdatei Sie verwenden:**
   - `lc_oracle.xml` (für Oracle-Datenbank)
   - `lc_mysql.xml` (für MySQL-Datenbank)
   - `lc_mssql.xml` (für Microsoft SQL Server-Datenbank)

## Einrichtungsschritte

### Schritt 1: Erstellen eines Speichers für Datenbankberechtigungen

Verwenden Sie die bereitgestellten Skripte, um den Datenbank-Berechtigungsspeicher zu erstellen und alle erforderlichen Passwort-Aliase hinzuzufügen.

#### Unter Windows:

**Skript-Speicherort:** `create-elytron-cred-standalone.bat`

`batch cd path\to\script\location create-elytron-cred-standalone.bat`

**Das Skript fordert Sie auf:**
1. **JBOSS_HOME-Pfad** (z. B. `C:\Adobe\Adobe_Experience_Manager_Forms\jboss`)
2. **Konfigurationsdateiname** (z. B. `lc_oracle.xml`, `lc_mysql.xml` oder `lc_mssql.xml`)
3. **Kennwort für Berechtigungsspeicher** (schützt die KeyStore-Datei - merken Sie sich dieses Kennwort)
4. **Datenbankkennwort** (Ihr tatsächliches Datenbankkennwort)

**Funktion des Skripts:**

- Erstellt einen Berechtigungsspeicher unter: `JBOSS_HOME\standalone\configuration\cred-store.p12`
- Ändert vorübergehend die Konfigurationsdatei, um die Erstellung des Berechtigungsspeichers zu aktivieren
- Fügt die folgenden Aliase mit Ihrem Datenbankkennwort hinzu:
   - `EncryptDBPassword`
   - `EncryptDBPassword_IDP_DS`
   - `EncryptDBPassword_EDC_DS`
   - `EncryptDBPassword_AEM_DS`
- Stellt die Konfigurationsdatei im Originalzustand wieder her
- Prüft, ob alle Aliase erfolgreich hinzugefügt wurden

#### Unter Linux:

**Skript-Speicherort:** `create-elytron-cred-standalone.sh`

`bash cd /path/to/script/location chmod +x create-elytron-cred-standalone.sh./create-elytron-cred-standalone.sh`

**Das Skript fordert Sie auf:**

1. **JBOSS_HOME-Pfad** (z. B. `/opt/Adobe/Adobe_Experience_Manager_Forms/jboss`)
2. **Konfigurationsdateiname** (z. B. `lc_oracle.xml`, `lc_mysql.xml` oder `lc_mssql.xml`)
3. **Kennwort für Berechtigungsspeicher** (schützt die KeyStore-Datei - merken Sie sich dieses Kennwort)
4. **Datenbankkennwort** (Ihr tatsächliches Datenbankkennwort)

**Funktion des Skripts:**

- Erstellt einen Berechtigungsspeicher unter: `JBOSS_HOME/standalone/configuration/cred-store.p12`
- Ändert vorübergehend die Konfigurationsdatei, um die Erstellung des Berechtigungsspeichers zu aktivieren
- Fügt die folgenden Aliase mit Ihrem Datenbankkennwort hinzu:
   - `EncryptDBPassword`
   - `EncryptDBPassword_IDP_DS`
   - `EncryptDBPassword_EDC_DS`
   - `EncryptDBPassword_AEM_DS`
- Stellt die Konfigurationsdatei im Originalzustand wieder her
- Prüft, ob alle Aliase erfolgreich hinzugefügt wurden

**Erwartete Ausgabe:**

```
=== JBoss Elytron Credential Store Setup ===
Enter JBOSS_HOME path (e.g. /opt/jboss): /opt/Adobe/Adobe_Experience_Manager_Forms/jboss
Enter configuration file name (e.g. lc_oracle.xml): lc_oracle.xml
Enter credential store password: ********
Confirm credential store password: ********
Enter database password: ********
Creating credential store using JBoss CLI...
Adding aliases to credential store...
Verifying credential store aliases...

All 4 aliases verified successfully!
- EncryptDBPassword
- EncryptDBPassword_IDP_DS
- EncryptDBPassword_EDC_DS
- EncryptDBPassword_AEM_DS

Credential store setup completed successfully!
```

### Schritt 2: Aktualisieren der eigenständigen Konfigurationsdatei

Nachdem Sie das Skript ausgeführt haben, müssen Sie JBoss so konfigurieren, dass das Kennwort für den Berechtigungsspeicher beim Start gelesen wird.

#### Unter Windows:

**Dateispeicherort:** `<JBOSS_HOME>\bin\standalone.conf.bat`

Beispiel: `C:\Adobe\Adobe_Experience_Manager_Forms\jboss\bin\standalone.conf.bat`

Fügen Sie die folgende Zeile hinzu oder aktualisieren Sie sie:

```batch
set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=YourActualPassword123"
```

Ersetzen Sie `YourActualPassword123` durch das **Kennwort für Berechtigungsspeicher**, das Sie in Schritt 1 verwendet haben.

#### Unter Linux:

**Dateispeicherort:** `<JBOSS_HOME>/bin/standalone.conf`

Beispiel: `/opt/Adobe/Adobe_Experience_Manager_Forms/jboss/bin/standalone.conf`

Fügen Sie die folgende Zeile hinzu oder aktualisieren Sie sie:

```bash
JAVA_OPTS="$JAVA_OPTS -DCS_PASS=YourActualPassword123"
```

Ersetzen Sie `YourActualPassword123` durch das **Kennwort für Berechtigungsspeicher**, das Sie in Schritt 1 verwendet haben.

### Schritt 3: JBoss starten

Starten Sie JBoss nach Abschluss der Einrichtung des Berechtigungsspeichers mit der entsprechenden Konfigurationsdatei.

**Hinweis:** Die genauen Startbefehle und -verfahren zum Starten von JBoss im eigenständigen Modus finden Sie im **Haupt-Installationshandbuch**. Die Startbefehle können je nach Konfiguration und Datenbanktyp (`lc_oracle.xml`, `lc_mysql.xml` oder `lc_mssql.xml`) variieren.

## Überprüfung

### Serverprotokolle überprüfen

**Protokollspeicherort:**

- Windows: `<JBOSS_HOME>\standalone\log\server.log`
- Linux: `<JBOSS_HOME>/standalone/log/server.log`

**Suchen Sie nach erfolgreichen Startmeldungen:**

```
INFO  [org.jboss.as.server] WFLYSRV0025: JBoss EAP started
INFO  [org.jboss.as.connector.deployers.jdbc] Bound data source [java:/AdobeDataSource]
```

**Keine Fehler im Zusammenhang mit:**

- Laden des Berechtigungsspeichers
- Datenbankverbindung
- Fehlende Aliase

## Fehlerbehebung

### Problem 1: Berechtigungsspeicher nicht gefunden

**Fehlermeldung:**

```
ERROR Unable to load credential store
```

**Lösung:**

1. Überprüfen, ob die Datei für den Berechtigungsspeicher vorhanden ist:
   - Windows: `dir <JBOSS_HOME>\standalone\configuration\cred-store.p12`
   - Linux: `ls -l <JBOSS_HOME>/standalone/configuration/cred-store.p12`
2. Wenn sie fehlt, führen Sie das Erstellungsskript des Berechtigungsspeichers erneut aus (Schritt 1)

### Problem 2: Falsches Kennwort für Berechtigungsspeicher

**Fehlermeldung:**

```
ERROR Unable to load credential store - Invalid password
```

**Lösung:**
Überprüfen Sie, ob das Kennwort in `standalone.conf.bat` / `standalone.conf` (Schritt 2) mit dem Kennwort übereinstimmt, das beim Erstellen des Speichers für die Berechtigung verwendet wurde (Schritt 1).

**Zu beheben:**
Bearbeiten Sie `standalone.conf.bat`/`standalone.conf` und aktualisieren Sie das Kennwort:

```
set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=CorrectPassword"
```

### Problem 3: Datenbankverbindung fehlgeschlagen

**Fehlermeldung:**

```
ERROR Failed to obtain connection
```

**Lösung:**

1. Überprüfen, ob das im Berechtigungsspeicher verwendete Datenbankkennwort korrekt ist
2. Überprüfen Sie, ob die Datenquellenkonfiguration auf den richtigen Alias verweist.
3. Überprüfen der Netzwerkverbindung zum Datenbankserver

**So erstellen Sie einen Berechtigungsspeicher:**

1. JBoss stoppen
2. Löschen Sie den vorhandenen Berechtigungsspeicher:
   - Windows: `del <JBOSS_HOME>\standalone\configuration\cred-store.p12`
   - Linux: `rm <JBOSS_HOME>/standalone/configuration/cred-store.p12`
3. Führen Sie das Erstellungsskript des Berechtigungsspeichers mit dem richtigen Datenbankkennwort erneut aus.

### Problem 4: Skript schlägt während der Ausführung fehl

**Fehlermeldung:**

```
ERROR: jboss-cli.bat is not found
```

**Lösung:**
Stellen Sie sicher, dass der Pfad JBOSS_HOME korrekt ist und auf das JBoss-Installationsverzeichnis verweist.

**Fehlermeldung:**

```
ERROR: Configuration file not found
```

**Lösung:**

1. Überprüfen Sie, ob der Konfigurationsdateiname korrekt ist.
2. Überprüfen, ob die Datei in `JBOSS_HOME\standalone\configuration\` Verzeichnis vorhanden ist
3. Stellen Sie sicher, dass Sie die richtige datenbankspezifische Konfigurationsdatei verwenden

## Kurzübersicht

### Datenbank-Zugangsdaten-Store (eigenständiger Modus)

**Zweck:** Sicheres Speichern von Datenbankkennwörtern

**script:**

- Windows: `create-elytron-cred-standalone.bat`
- Linux: `create-elytron-cred-standalone.sh`

**Erstellt:**

- Datei: `standalone/configuration/cred-store.p12`
- Aliase: `EncryptDBPassword`, `EncryptDBPassword_IDP_DS`, `EncryptDBPassword_EDC_DS`, `EncryptDBPassword_AEM_DS`

**Konfiguration:**

- Variable: `-DCS_PASS=password`
- Datei: `standalone.conf.bat` (Windows) oder `standalone.conf` (Linux)

