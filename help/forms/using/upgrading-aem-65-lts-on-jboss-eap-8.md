---
title: Aktualisieren von AEM 6.5 LTS auf JBoss EAP 8 (Windows)
description: Dieses Handbuch enthält schrittweise Anleitungen zum Aktualisieren einer bestehenden Adobe Experience Manager (AEM) 6.5 LTS-Installation unter Windows von JBoss EAP 7.4 auf JBoss EAP 8 unter Verwendung von JDK 21.
source-git-commit: 835530039678bc16a6de87b8d580be91a2026f94
workflow-type: tm+mt
source-wordcount: '1374'
ht-degree: 4%

---

# Aktualisieren von AEM 6.5 LTS auf JBoss EAP 8 (Windows)

## Übersicht

Dieses Handbuch enthält schrittweise Anleitungen zum Aktualisieren einer bestehenden Adobe Experience Manager (AEM) 6.5 LTS-Installation unter Windows von JBoss EAP 7.4 auf JBoss EAP 8 unter Verwendung von JDK 21.

**Aktualisierungspfad:** JBoss EAP 7.4 (JDK 11) → JBoss EAP 8 (JDK 21)

## Wichtige Hinweise

>[!NOTE]
>
>Dies ist ein wichtiger Upgrade-Vorgang. Führen Sie dieses Upgrade immer zuerst in einer Nicht-Produktionsumgebung durch und bewahren Sie vollständige Backups auf.
>
> **&#x200B; VORAUSSETZUNGEN: &#x200B;** Sie eine vollständige Systemsicherung und einen dokumentierten Rollback-Plan vor dem Fortfahren.

## Anforderungen vor einem Upgrade

### Systemanforderungen

| Komponente | Anforderung |
|-----------|-------------|
| Betriebssystem | Windows Server 2016 oder höher (64-Bit) |
| Source-Umgebung | JBoss EAP 7.4 mit AEM 6.5 LTS |
| Zielumgebung  | JBoss EAP 8.x |
| Java Development Kit | JDK 21 (Oracle oder OpenJDK) |
| AEM-Version | AEM 6.5 Service Pack (zuletzt empfohlen) |
| Festplattenspeicher | Mindestens 50 GB freier Speicherplatz für den Upgrade-Prozess |

### Erforderliche Downloads

Bevor Sie mit dem Upgrade beginnen, informieren Sie sich über Folgendes:

1. **JBoss EAP 8.0-Verteilung**\
   Download von: [https://developers.redhat.com/products/eap/download](https://developers.redhat.com/products/eap/download)

2. **JDK 21-Installationsprogramm**\
   Herunterladen von Oracle JDK 21 oder OpenJDK 21 für Windows (64-Bit)

3. **AEM 6.5 LTS-WAR-Datei**\
   Erhalten Sie das neueste AEM 6.5 Service Pack WAR von Adobe Software Distribution

## Schritt 1: Erstellen eines vollständigen Backups

>[!IMPORTANT]
>
> Führen Sie umfassende Sicherungen durch, bevor Sie fortfahren.

### Sicherungs-Checkliste

- [ ] Vollständige Sicherung des vorhandenen JBoss EAP 7.4-Installationsverzeichnisses
- [ ] Sicherung `crx-repository` Ordners
- [ ] Sicherung `crx-quickstart` Ordners
- [ ] Export aller benutzerdefinierten Konfigurationen
- [ ] Datenbank-Backup (bei Verwendung einer externen Datenbank)
- [ ] des aktuellen Systemstatus und der aktuellen Konfigurationen

### Backup erstellen

```cmd
# Example backup location
C:\AEM-Backups\Pre-Upgrade-<date>

# Copy entire JBoss 7.4 directory
xcopy "C:\jboss-eap-7.4" "C:\AEM-Backups\Pre-Upgrade-<date>\jboss-eap-7.4" /E /I /H
```

**Empfohlen:** Speichern Sie Sicherungskopien auf einem separaten Laufwerk oder an einem separaten Netzwerkspeicherort.

## Schritt 2: Installieren von JBoss EAP 8

### Extrahieren von JBoss EAP 8

1. Extrahieren Sie die JBoss EAP 8 ZIP-Distribution in Ihr Zielinstallationsverzeichnis:

   ```
   C:\jboss-eap-8.0
   ```

2. Notieren Sie sich diesen Ordnerpfad, der in diesem Handbuch `<JBOSS_HOME>` wird.

### Verzeichnisstruktur replizieren

Stellen Sie sicher, dass die neue JBoss EAP 8-Installation dieselbe benutzerdefinierte Verzeichnisstruktur aufweist wie das vorherige JBoss EAP 7.4-Setup, insbesondere:

- Benutzerdefinierte Bereitstellungsordner
- Externe Konfigurationsordner
- Speicherorte der Protokolldateien
- Alle benutzerdefinierten Module oder Bibliotheken

## Schritt 3: Migrieren von Repository-Daten

### CRX-Repository kopieren

1. Navigieren Sie zu Ihrer vorhandenen JBoss EAP 7.4-Installation:

   ```
   <OLD_JBOSS_HOME>\bin\crx-repository
   ```

2. Kopieren Sie den gesamten `crx-repository`-Ordner in die neue JBoss EAP 8-Installation:

   ```cmd
   xcopy "C:\jboss-eap-7.4\bin\crx-repository" "C:\jboss-eap-8.0\bin\crx-repository" /E /I /H
   ```

**Wichtig:** Dieser Ordner enthält Ihr Inhalts-Repository und muss vollständig übertragen werden.

### Repository-Kopie überprüfen

Überprüfen Sie nach dem Kopieren, ob Größe und Struktur des Repositorys mit der Quelle übereinstimmen:

```cmd
dir "C:\jboss-eap-8.0\bin\crx-repository" /s
```

## Schritt 4: AEM-Instanz stoppen

Bevor Sie Änderungen vornehmen, stellen Sie sicher, dass AEM vollständig angehalten wurde.

### Beenden über Windows-Dienste

1. Öffnen Sie **Dienste** (Ausführung: `services.msc`)
2. Suchen des AEM-/JBoss-Service
3. Klicken Sie mit der rechten Maustaste und wählen Sie **Beenden**
4. Warten Sie, bis der Dienst vollständig beendet wurde

### Über die Befehlszeile anhalten

Wenn AEM manuell gestartet wurde:

1. Zum Fenster der JBoss-Konsole wechseln
2. `Ctrl+C`
3. Auf ordnungsgemäßes Herunterfahren warten

### Herunterfahren überprüfen

Stellen Sie sicher, dass der Java-Prozess nicht mehr ausgeführt wird:

```cmd
tasklist | findstr java
```

## Schritt 5: Alte AEM-Dateien bereinigen

Entfernen Sie veraltete Dateien aus dem `crx-quickstart`, um ein sauberes Upgrade sicherzustellen.

>[!CAUTION]
>
> Löschen Sie nur die unten aufgeführten Dateien und Ordner. Entfernen Sie keine anderen Konfigurationsdateien, benutzerdefinierten Code oder Repository-Daten.

### 5.1 Entfernen des Launchpad-Startordners

**Speicherort:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\startup
```

**Aktion:**

```cmd
rd /s /q "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\startup"
```

**Zweck:** Dieser Ordner enthält alte OSGi-Bundles, die während des Upgrades neu generiert werden.

### 5.2 JAR-Basisdatei entfernen

**Speicherort:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\org.apache.sling.launchpad.base.jar
```

**Aktion:**

```cmd
del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\org.apache.sling.launchpad.base.jar"
```

**Zweck:** Diese JAR-Datei wird durch die Version aus der neuen WAR-Datei ersetzt.

### 5.3 Bootstrap-Befehlsdatei entfernen

**Speicherort:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\felix\bundle0\BootstrapCommandFile_*.txt
```

**Aktion:**

```cmd
del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\felix\bundle0\BootstrapCommandFile_*.txt"
```

**Zweck:** Bootstrap-Befehle werden für die neue Umgebung neu generiert.

### 5.4 Entfernen der Datei „sling.options“

**Speicherort:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\felix\sling.options.file
```

**Aktion:**

```cmd
del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\felix\sling.options.file"
```

### 5.5 Entfernen der Datei sling_bootstrap.txt

**Speicherort:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\sling_bootstrap.txt
```

**Aktion:**

```cmd
del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\sling_bootstrap.txt"
```

### 5.6 Sichern und Entfernen der Datei sling.properties

Diese Datei enthält umgebungsspezifische Konfigurationen, die möglicherweise später zusammengeführt werden müssen.

**Speicherort:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\conf\sling.properties
```

**Aktion:**

1. **Backup erstellen:**

   ```cmd
   copy "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\conf\sling.properties" "C:\AEM-Backups\sling.properties.backup"
   ```

2. **Original löschen:**

   ```cmd
   del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\conf\sling.properties"
   ```

**Zweck:** Es wird eine neue `sling.properties` generiert. Überprüfen Sie die Sicherung, um alle benutzerdefinierten Konfigurationen nach dem Upgrade wiederherzustellen.

## Schritt 6: Installieren und Konfigurieren von JDK 21

### Installieren von JDK 21

1. Ausführen des JDK 21-Installationsprogramms für Windows
2. Installation an einem Standardspeicherort (z. B. `C:\Program Files\Java\jdk-21`)
3. Abschließen des Installationsassistenten

### Konfigurieren von Umgebungsvariablen

#### JAVA_HOME festlegen

1. Öffnen Sie **Systemeigenschaften** → **Erweitert** → **Umgebungsvariablen**
2. Klicken **unter &quot;**&quot; auf **Neu**
3. Satz:
   - Variablenname: `JAVA_HOME`
   - Variablenwert: `C:\Program Files\Java\jdk-21`
4. Klicken Sie auf **OK**

#### PATH-Variable aktualisieren

1. Wählen **unter &quot;**&quot; die Option `Path` aus und klicken Sie auf **Bearbeiten**
2. Neuen Eintrag hinzufügen:

   ```
   %JAVA_HOME%\bin
   ```

3. Verschieben Sie diesen Eintrag an den Anfang der Liste, um sicherzustellen, dass JDK 21 Vorrang hat
4. Klicken **in** Dialogfeldern auf OK

### Java-Installation überprüfen

1. Öffnen Sie eine **neue** Eingabeaufforderung (zum Laden aktualisierter Umgebungsvariablen)
2. Java-Version überprüfen:

   ```cmd
   java -version
   ```

   Erwartete Ausgabe:

   ```
   java version "21.0.x"
   Java(TM) SE Runtime Environment (build 21.0.x+...)
   Java HotSpot(TM) 64-Bit Server VM (build 21.0.x+..., mixed mode, sharing)
   ```

3. Überprüfen Sie JAVA_HOME:

   ```cmd
   echo %JAVA_HOME%
   ```

## Schritt 7: JVM-Einstellungen konfigurieren

Konfigurieren Sie vor der Bereitstellung von AEM die entsprechenden JVM-Speichereinstellungen für die Verwendung in der Produktion.

### Standalone.conf.bat bearbeiten

1. Gehen Sie zu:

   ```
   <JBOSS_HOME>\bin
   ```

2. `standalone.conf.bat` in einem Texteditor öffnen (als Administrator)

3. Suchen Sie die `JAVA_OPTS`-Konfiguration oder fügen Sie sie hinzu:

   ```batch
   rem # AEM Production JVM Settings
   set "JAVA_OPTS=-Xms4096m -Xmx4096m -XX:MaxMetaspaceSize=768m"
   set "JAVA_OPTS=%JAVA_OPTS% -Djava.net.preferIPv4Stack=true"
   set "JAVA_OPTS=%JAVA_OPTS% -Dfile.encoding=UTF-8"
   set "JAVA_OPTS=%JAVA_OPTS% -server"
   ```

4. Speichern und schließen Sie die Datei

**Empfohlene Einstellungen:**

| Parameter | Empfohlener Wert | Beschreibung |
|-----------|-------------------|-------------|
| `-Xms` | 4096 - 8192 MB | Anfängliche Heap-Größe |
| `-Xmx` | 4096 - 8192 MB | Maximale Heap-Größe |
| `-XX:MaxMetaspaceSize` | 768 - 1024 MB | Metaspace-Limit |

**Hinweis:** Passen Sie die Werte entsprechend den verfügbaren Speicher- und Arbeitslastanforderungen Ihres Servers an.

## Schritt 8: Bereitstellen von AEM 6.5 LTS WAR

### WAR-Datei vorbereiten

Stellen Sie sicher, dass Ihre AEM-WAR-Datei gemäß Bereitstellungshandbuch ordnungsgemäß konfiguriert ist:

- `jboss-deployment-structure.xml` ist vorhanden
- `web.xml` enthält Einstellungen für multipart-config
- WAR wird neu verpackt, wenn Änderungen vorgenommen wurden

### Bereitstellen für JBoss

1. Kopieren Sie die AEM 6.5 LTS WAR-Datei in das Bereitstellungsverzeichnis :

   ```cmd
   copy "C:\AEM-Downloads\cq-quickstart-6.5.xx.war" "C:\jboss-eap-8.0\standalone\deployments\cq-quickstart.war"
   ```

**Wichtig:** Stellen Sie sicher, dass der WAR-Dateiname mit dem gewünschten URL-Kontextpfad übereinstimmt.

## Schritt 9: JBoss EAP 8 mit AEM starten

### Server starten

1. Öffnen Sie **Eingabeaufforderung** als **Administrator**

2. Navigieren Sie zum JBoss-Bin-Verzeichnis:

   ```cmd
   cd C:\jboss-eap-8.0\bin
   ```

3. JBoss EAP 8 starten:

   ```cmd
   standalone.bat -b 0.0.0.0 -bmanagement 0.0.0.0
   ```

### Erststart überwachen

Konsolenausgabe beobachten für:

1. **WAR-Bereitstellung:**

   ```
   Deployed "cq-quickstart.war" (runtime-name : "cq-quickstart.war")
   ```

2. **AEM-Initialisierungsnachrichten:**

   ```
   Apache Sling Application Launcher
   Sling Home: crx-repository/crx-quickstart
   ```

3. **Repository-Upgrade (falls zutreffend):**

   ```
   Performing repository migration...
   ```

**Erwartete Startzeit:** 5-15 Minuten, je nach Repository-Größe und Systemressourcen.

## Schritt 10: Überprüfen, ob das Upgrade erfolgreich war

### AEM-Start überprüfen

Überwachen Sie die JBoss-Konsole auf die endgültige Startmeldung:

```
**** AEM started successfully ****
```

### Zugriff auf die AEM-Benutzeroberfläche

1. Öffnen eines Webbrowsers
2. Gehen Sie zu:

   ```
   http://localhost:8080/cq-quickstart
   ```

3. Melden Sie sich mit Administratorberechtigungen an:
   - Benutzername: `admin`
   - Kennwort: `admin` (oder Ihr benutzerdefiniertes Kennwort)

### Überprüfen der Systeminformationen

1. Navigieren Sie zu **Tools** → **Vorgänge** → **Web-Konsole**

   ```
   http://localhost:8080/cq-quickstart/system/console
   ```

2. Klicken Sie **Systeminformationen**

3. Überprüfen Sie:

   - **JVM-Version:** sollte Java 21 anzeigen
   - **JBoss-Version:** sollte EAP 8.x anzeigen
   - **AEM-Version:** sollte 6.5.xx anzeigen

### Systemzustand überprüfen

Navigieren Sie zu **Tools** → **Vorgänge** → **Diagnose**, um Konsistenzprüfungen durchzuführen:

- Bundle-Status: Alle Bundles sollten „Aktiv“ sein
- Ressourcenauflösung: Sollte einen gesunden Status anzeigen
- Abfrageleistung: Überprüfung auf Beeinträchtigung

## Aufgaben nach einem Upgrade

### Benutzerdefinierte Konfigurationen wiederherstellen

1. Überprüfen der gesicherten `sling.properties`
2. Stellen Sie alle benutzerdefinierten Ausführungsmodi oder Konfigurationen in der neuen Datei wieder her:

   ```
   <JBOSS_HOME>\bin\crx-repository\crx-quickstart\conf\sling.properties
   ```

3. AEM neu starten, wenn Konfigurationen geändert wurden

### Aktualisieren von Replikationsagenten

1. Navigieren Sie zu **Tools** → **Bereitstellung** → **Replikation** → **Agenten für Autor**
2. Überprüfen und Testen aller Replikationsagenten
3. Aktualisieren Sie alle hartcodierten Verweise auf alte Serverpfade

### Testen der kritischen Funktionalität

- [ ] Inhaltserstellung und -veröffentlichung
- [ Hochladen und Verarbeiten von ] Assets
- [ Workflow-Ausführung ]
- [ ] Benutzerauthentifizierung
- [ ] Integrationsendpunkte
- [ Benutzerdefinierte Komponenten und Vorlagen ]

### Leistungsoptimierung

1. Überprüfen und löschen Sie alle temporären Caches
2. Überwachen der Systemleistung bei der ersten Verwendung
3. JVM-Einstellungen bei Bedarf basierend auf tatsächlichen Nutzungsmustern anpassen

## Fehlerbehebung

### Gängige Probleme

| Problem | Mögliche Ursache | Lösung |
|-------|---------------|----------|
| AEM kann nicht gestartet werden | Falsche Java-Version | Überprüfen, ob `JAVA_HOME` auf JDK 21 verweist |
| Repository-Beschädigungsfehler | Unvollständige Repository-Kopie | Wiederherstellen aus einem Backup und erneutes Kopieren des Repositorys |
| OutOfMemoryError | Nicht genügend Heap-Speicher | `-Xmx` in `standalone.conf.bat` erhöhen |
| Pakete im Status „Installiert“ | Fehlende Abhängigkeiten | Überprüfen der Bundle-Abhängigkeiten in der Web-Konsole |
| Port 8080 wird bereits verwendet | Ein weiterer Dienst, der Port verwendet | Konflikt beim Dienst beenden oder JBoss-Port ändern |

### Speicherorte der Protokolldateien

- **JBoss-Serverprotokoll:**\
  `<JBOSS_HOME>\standalone\log\server.log`

- **AEM-Fehlerprotokoll:**\
  `<JBOSS_HOME>\bin\crx-repository\crx-quickstart\logs\error.log`

- **AEM-Zugriffsprotokoll:**\
  `<JBOSS_HOME>\bin\crx-repository\crx-quickstart\logs\access.log`

### Rollback

Wenn das Upgrade fehlschlägt und nicht behoben werden kann:

1. JBoss EAP 8 anhalten
2. Wiederherstellen des vollständigen Backups von JBoss EAP 7.4
3. Wiederherstellen des `crx-repository` Ordners
4. Überprüfen, ob `JAVA_HOME` auf JDK 11 verweist (bei Rollback)
5. Vorherige Umgebung starten

## Best Practices

### Vor der Produktionsbereitstellung

- [ ] Testen des vollständigen Upgrade-Prozesses in einer Entwicklungsumgebung
- [ ] in einer Staging-Umgebung mit produktionsähnlichen Daten
- [ Alle benutzerdefinierten Konfigurationen und Integrationen ] dokumentieren
- [ ] Erstellen eines detaillierten Rollback-Plans
- [ ] Planung des Upgrades während des Wartungsfensters
- [ ] Alle Stakeholder über geplante Ausfallzeiten informieren

### Nach erfolgreicher Aktualisierung

- [ Systemprotokolle für 48-72 Stunden ] überwachen
- [ ] Führen Sie Belastungstests durch, um Leistungsprobleme zu identifizieren
- [ ] Systemdokumentation aktualisieren
- [ ] Trainieren des Teams bei allen JBoss EAP 8-Unterschieden
- [ ] Archivieren der gesamten Upgrade-Dokumentation und -Backups

## Verwandte Dokumentation

- [JBoss EAP 8-Migrationshandbuch](https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/8.0/html/migration_guide/)
- [Aktualisierungshandbuch für Adobe Experience Manager 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html?lang=de)
- [Installieren von Service Packs durch AEM](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=de)

## Dokumentinformation

| Feld | Wert |
|-------|-------|
| Dokumentversion | 1.0 |
| Zuletzt aktualisiert | Februar 2026 |
| AEM-Version | 6.5 LTS |
| Source Platform | JBoss EAP 7.4/JDK 11 |
| Zielplattform | JBoss EAP 8.x / JDK 21 |
| Betriebssystem | Windows Server |

**Rechtlicher Hinweis:** Adobe, Adobe Experience Manager und AEM sind eingetragene Marken von Adobe Inc. JBoss und Red Hat sind eingetragene Marken von Red Hat, Inc.
