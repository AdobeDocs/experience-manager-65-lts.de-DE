---
title: Upgrade auf AEM 6.5 Forms LTS unter OSGi
description: Sie können direkt von AEM 6.5.22.0 Forms auf AEM 6.5 Forms LTS aktualisieren.
content-type: reference
role: Admin, User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, AEM Forms on OSGi, AEM Forms Upgrade
exl-id: 9233d4b7-441c-4cbd-86f8-2c52b99c3330
source-git-commit: b7aa877f9e782b0568adc7baa440dc630c690454
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 47%

---

# Upgrade auf AEM 6.5 Forms LTS unter OSGi {#upgrade-to-aem-forms-osgi}

Um [von AEM 6.5 auf AEM 6.5 LTS](/help/sites-deploying/upgrade.md) zu aktualisieren, führen Sie ein Upgrade auf AEM 6.5.22.0 Forms oder höher durch. Ein direktes Upgrade von AEM 6.5.22.0 auf AEM 6.5 Forms LTS wird unterstützt.

Wenn Sie AEM 6.0 Forms, AEM 6.1 Forms, AEM 6.2 Forms, AEM 6.3 Forms, AEM 6.4 Forms oder AEM 6.5 Forms verwenden, ist kein direktes Upgrade auf AEM 6.5 Forms LTS verfügbar. Ausführliche Informationen zu Upgrade-Pfaden finden Sie in der [Upgrade-Pfade](/help/forms/using/upgrade.md).

Führen Sie nach dem Upgrade auf das Service Pack AEM Forms 6.5.22.0 die folgenden Schritte aus, um auf AEM 6.5 LTS Forms zu aktualisieren:

1. Installieren des AEM Forms-Add-on-Pakets. Die Schritte sind hier aufgeführt:

   1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
   1. Wählen Sie im Kopfzeilenmenü **[!UICONTROL Adobe Experience Manager]** aus.
   1. Im Abschnitt **[!UICONTROL Filter]**:
      1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** aus.
      1. Wählen Sie die Version aus und geben Sie sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
   1. Wählen Sie den für Ihr Betriebssystem zutreffenden Paketnamen, dann **[!UICONTROL EULA-Bedingungen akzeptieren]** und dann **[!UICONTROL Herunterladen]** aus.
   1. Öffnen Sie den [Paket-Manager](/help/sites-administering/package-manager.md) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
   1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

      Sie können das Paket auch über den direkten Link herunterladen, der im Artikel [AEM Forms-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) aufgeführt ist.

      Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Halten Sie den Server nicht sofort an.** Warten Sie vor dem Anhalten des AEM Forms-Servers, bis die Meldungen „ServiceEvent REGISTERED“ und „ServiceEvent UNREGISTERED“ nicht mehr in der Datei &lt;crx-repository>/error.log angezeigt werden und das Protokoll stabil ist. Beachten Sie außerdem, dass einige Pakete im installierten Zustand verbleiben können. Sie können den Status dieser Pakete ignorieren.


      **Starten Sie die AEM-Instanz mit den folgenden zusätzlichen JVM-Befehlszeilenparametern neu**:
      `--add-opens java.base/java.util=ALL-UNNAMED --add-exports=java.xml/com.sun.org.apache.xml.internal.serialize=ALL-UNNAMED`

      Wenn der Server über ein Skript oder einen Service gestartet wird, aktualisieren Sie ihn entsprechend, um die oben genannten einzuschließen, damit diese auch nach nachfolgenden Neustarts wirksam werden.

      >[!NOTE]
      >
      > Es wird empfohlen, den Befehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

1. Führen Sie nach der Installation folgende Aktivitäten durch.

   * **Ausführen des Migrationsdienstprogramms**

     Das Migrationsdienstprogramm macht die adaptiven Formulare und Korrespondenzmanagement-Assets aus früheren Versionen kompatibel mit AEM 6.5 Forms. Sie können das Dienstprogramm von der AEM Software Distribution herunterladen. Informationen in Einzelschritten zur Konfiguration und Verwendung des Migrationsdienstprogramms finden Sie in der Dokumentation zum [Migrationsdienstprogramm](../../forms/using/migration-utility.md).

     Wenn Sie [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) mit der Datenbank verwenden und von einer früheren Version aktualisieren, führen Sie nach der Aktualisierung die folgenden SQL-Abfragen aus:

     ```sql
     UPDATE metadata m, additionalmetadatatable am
     SET m.dataType = am.value
     WHERE m.id = am.id
     AND am.key = 'dataType'
     ```

     ```sql
     DELETE from additionalmetadatatable
     WHERE `key` = 'dataType'
     ```

   * **(Nur wenn Sie von AEM 6.2 Forms oder früheren Versionen aktualisieren) Konfigurieren Sie Adobe Sign neu**

     Wenn Sie Adobe Sign in der vorherigen Version von AEM Forms konfiguriert haben, konfigurieren Sie Adobe Sign über AEM Cloud Services neu. Weitere Informationen finden Sie unter [Adobe Sign mit AEM Forms integrieren](../../forms/using/adobe-sign-integration-adaptive-forms.md).

   * **Unterstützung für jQuery**

     In AEM 6.5 Forms wird die jQuery-Version auf 3.2.1 aktualisiert und die jQuery-UI-Version wird auf 1.12.1 aktualisiert. AEM Form verwendet JQuery im **noConflict**-Modus. Wenn Sie also eine andere jQuery-Version verwenden, werden bei der Durchführung eines Upgrades keine Probleme angezeigt. Wenn Sie jedoch auf AEM 6.5 Forms aktualisieren:

      * Stellen Sie sicher, dass Ihre benutzerdefinierten Komponenten, falls vorhanden, mit unterstützten jQuery-Versionen kompatibel sind.
      * Entfernen Sie nicht unterstützte APIs aus den benutzerdefinierten Komponenten. Siehe [Upgrade-Handbuch](https://jquery.com/upgrade-guide/3.0/) für die Liste der entfernten APIs. Beispielsweise wird die Unterstützung für die APIs load(), .unload() und .error() entfernt. Verwenden Sie die Methode .on() anstelle der oben genannten APIs. Ändern Sie beispielsweise $(&quot;img&quot;).load(fn) to $(&quot;img&quot;).on(&quot;load&quot;, fn).

   * **(Nur wenn Sie von AEM 6.2 Forms oder früheren Versionen aktualisieren) Konfigurieren Sie Analysen und Berichte neu**

     In AEM 6.4 Forms sind keine Traffic-Variablen für Quelle und Erfolgsereignis für Impressionen verfügbar. Wenn Sie von AEM 6.2 Forms oder vorherigen Versionen aktualisieren, sendet AEM Forms daher keine Daten mehr an den Adobe Analytics-Server und es stehen keine Analyseberichte für adaptive Formulare zur Verfügung. Darüber hinaus führt AEM 6.4 Forms Traffic-Variablen für die Version der Formularanalyse und das Erfolgsereignis für die auf einem Feld verbrachte Zeit ein. Konfigurieren Sie daher die Analyse und die Berichte für Ihre AEM Forms-Umgebung neu. Ausführliche Anweisungen finden Sie unter [Konfigurieren von Analysen und Berichten](../../forms/using/configure-analytics-forms-documents.md).

1. Vergewissern Sie sich, dass der Server erfolgreich aktualisiert und alle Daten migriert wurden und dass der Server einwandfrei funktioniert.

   * **Überprüfen Sie den Status der Pakete:** Stellen Sie sicher, dass alle Pakete sich im aktiven Status befinden.
   * **Überprüfen Sie die Replikation und Rückwärtsreplikation:** Veröffentlichen Sie einige migrierte Formulare, füllen Sie sie aus und senden Sie sie. Überprüfen Sie auch die gesendeten Daten.
   * **Überprüfen Sie den Zugriff auf die Administrator- und Entwicklerbenutzeroberflächen:** Melden Sie sich über ein Administratorkonto bei der AEM-Instanz an und stellen Sie sicher, dass Sie Zugriff auf die folgenden URLs haben:

      * `https://'[server]:[port]'/crx/packmgr`
      * `https://'[server]:[port]'/crx/de`
      * `https://'[server]:[port]'/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   >
   >In AEM 6.4 Forms hat sich die Struktur des crx-Repository geändert. Verwenden Sie nach dem Upgrade auf AEM 6.5 Forms die geänderten Pfade für die Anpassung, die Sie neu erstellen. Sie finden die vollständige Liste der geänderten Pfade unter [Forms Repository-Restrukturierung in AEM](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/deploying/restructuring/forms-repository-restructuring-in-aem-6-5).


## Bereitstellen von AEM unter JBoss EAP 8 (Windows)

### Übersicht

Dieses Handbuch enthält schrittweise Anweisungen zur Bereitstellung von Adobe Experience Manager (AEM) als eigenständige OSGi-WAR-Datei auf JBoss Enterprise Application Platform (EAP) 8 in einer Windows-Umgebung mit JDK 21.

### Systemanforderungen

Stellen Sie vor Beginn des Bereitstellungsprozesses sicher, dass Ihre Umgebung die folgenden Anforderungen erfüllt:

| Komponente | Anforderung |
|-----------|-------------|
| Betriebssystem | Windows Server 2016 oder höher (64-Bit) |
| Java Development Kit | JDK 21 (Oracle oder OpenJDK) |
| Anwendungs-Server | JBoss EAP 8.x |
| AEM-Verteilung | AEM WAR-Datei (bezogen von Adobe) |

>[!NOTE]
>
> Stellen Sie sicher, dass die Umgebungsvariable `JAVA_HOME` auf Ihr JDK 21-Installationsverzeichnis verweist.

### Schritt 1: Installieren von JBoss EAP 8

#### JBoss EAP herunterladen

1. Navigieren Sie zum Red Hat Developer Portal:\
   [https://developers.redhat.com/products/eap/download](https://developers.redhat.com/products/eap/download)

2. Laden Sie die JBoss EAP 8 ZIP-Distribution für Windows herunter.

#### JBoss-EAP extrahieren

1. Extrahieren Sie die heruntergeladene ZIP-Datei in das bevorzugte Installationsverzeichnis.

2. Notieren Sie sich diesen Ordnerpfad, der in diesem Handbuch `<JBOSS_HOME>` wird.

   **Beispiel:**\
   ```C:\jboss-eap-8.0```

### Schritt 2: AEM-WAR-Datei vorbereiten

#### AEM WAR erhalten

Erwerben Sie die AEM WAR-Datei von Adobe Software Distribution oder Ihrem Adobe-Support-Mitarbeiter.

#### WAR-Datei umbenennen

Benennen Sie die WAR-Datei um, damit ihr gewünschter URL-Kontextpfad widergespiegelt wird:

```
cq-quickstart.war
```

>[!IMPORTANT]
>
> Der WAR-Dateiname bestimmt den URL-Kontext der Anwendung. Beispielsweise ist `cq-quickstart.war` unter `/cq-quickstart` zugänglich.


### Schritt 3: AEM WAR konfigurieren

Alle Konfigurationsänderungen müssen vor der Bereitstellung **JBoss** werden.

#### Arbeitsverzeichnis erstellen

1. Erstellen Sie ein temporäres Arbeitsverzeichnis:

   ```
   C:\aem\war-config
   ```

2. Kopieren Sie `cq-quickstart.war` in diesen Ordner.

#### WAR-Inhalte extrahieren

1. Öffnen Sie **Eingabeaufforderung** und navigieren Sie zum Arbeitsverzeichnis:

   ```cmd
   cd C:\aem\war-config
   ```

2. Extrahieren Sie die WAR-Datei:

   ```cmd
   jar -xvf cq-quickstart.war
   ```

   Dadurch wird eine Verzeichnisstruktur mit `WEB-INF` und anderen Anwendungsdateien erstellt.

### Schritt 4: Konfigurieren des JBoss-Bereitstellungsdeskriptors

#### Erstellen einer Bereitstellungsstrukturdatei

1. Navigieren Sie zum `WEB-INF`-Verzeichnis in Ihrem extrahierten WAR:

   ```cmd
   cd WEB-INF
   ```

2. Erstellen Sie eine neue Datei mit dem Namen `jboss-deployment-structure.xml`.

3. Fügen Sie den folgenden XML-Inhalt hinzu:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jboss-deployment-structure xmlns="urn:jboss:deployment-structure:1.2">
       <deployment>
           <dependencies>
               <module name="jdk.unsupported" />
           </dependencies>
       </deployment>
   </jboss-deployment-structure>
   ```

4. Speichern und schließen Sie die Datei.

**Zweck:** Diese Konfiguration bietet Zugriff auf JDK-interne Module, die von AEM benötigt werden.

### Schritt 5: Konfigurieren der Einstellungen für den mehrteiligen Upload

>[!NOTE]
>
> Schritt 5 gilt nur für **AEM Forms**. Wenn Sie **nur AEM einrichten** können Sie diesen Schritt überspringen.


#### Ändern von web.xml

1. Öffnen Sie `WEB-INF\web.xml` in einem Texteditor.

2. Suchen Sie den `<servlet>` Abschnitt, der die Ausführungsmodus-Konfiguration enthält:

   ```xml
   <!-- Set the runmode per default to author -->
   <init-param>
       <param-name>sling.run.modes</param-name>
       <param-value>author</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

3. Ersetzen Sie das schließende `</servlet>`-Tag und die vorangehende Zeile durch:

   ```xml
   <init-param>
       <param-name>sling.run.modes</param-name>
       <param-value>author</param-value>
   </init-param>
   <multipart-config>
       <max-file-size>1048576000</max-file-size>
       <max-request-size>1048576000</max-request-size>
       <file-size-threshold>0</file-size-threshold>
   </multipart-config>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

4. Speichern und schließen Sie `web.xml`.

**Zweck:** Diese Einstellungen ermöglichen große Datei-Uploads (bis zu 1 GB) für die Verwaltung von AEM Forms und digitalen Assets.

### Schritt 6: Komprimieren Sie die WAR-Datei neu

Komprimieren Sie nach Abschluss aller Konfigurationsänderungen die WAR-Datei neu.

1. Navigieren Sie zurück zum Arbeitsverzeichnis, das den extrahierten Inhalt enthält:

   ```cmd
   cd C:\aem\war-config
   ```

2. Erstellen Sie die neue WAR-Datei:

   ```cmd
   jar -cvf cq-quickstart.war *
   ```

>[!IMPORTANT]
>
> Führen Sie diesen Schritt nur einmal aus, nachdem alle Konfigurationen abgeschlossen sind.

### Schritt 7: AEM bereitstellen und starten

#### Bereitstellen von WAR für JBoss

1. Kopieren Sie die neu gepackten `cq-quickstart.war` in das JBoss-Bereitstellungsverzeichnis:

   ```
   <JBOSS_HOME>\standalone\deployments
   ```

   **Beispiel:**
   ```C:\jboss-eap-8.0\standalone\deployments```

#### JVM-Einstellungen konfigurieren (optional, aber empfohlen)

Bevor Sie JBoss starten, konfigurieren Sie JVM-Speichereinstellungen:

1. Öffnen Sie `<JBOSS_HOME>\bin\standalone.conf.bat` in einem Texteditor.

1. Ändern Sie die folgende Zeile, um den Heap-Speicher festzulegen, oder fügen Sie sie hinzu:

   ```batch
   set "JAVA_OPTS=-Xms4096m -Xmx4096m -XX:MaxMetaspaceSize=512m"
   ```

>[!NOTE]
>
> Passen Sie die Speicherwerte an Ihre Serverkapazität und AEM-Anforderungen an.

1. Speichern und schließen Sie die Datei.

#### JBoss EAP starten

1. Öffnen Sie **Eingabeaufforderung** als **Administrator**.

1. Navigieren Sie zum Ordner JBoss bin :

   ```cmd
   cd <JBOSS_HOME>\bin
   ```

   **Beispiel:**
   ```cmd cd C:\jboss-eap-8.0\bin```

1. Starten Sie den JBoss-Server:

   ```cmd
   standalone.bat -b 0.0.0.0 -bmanagement 0.0.0.0
   ```

   **Parameter:**
   * `-b 0.0.0.0` - Bindet den Server an alle Netzwerkschnittstellen
   * `-bmanagement 0.0.0.0` - Bindet die Verwaltungsschnittstelle an alle Netzwerkschnittstellen

#### Überwachen der Bereitstellung

Überwachen Sie die Konsolenausgabe auf Bereitstellungsmeldungen. Eine erfolgreiche Bereitstellung wird durch Folgendes angezeigt:

```
Deployed "cq-quickstart.war" (runtime-name : "cq-quickstart.war")
```

### Schritt 8: Zugriff auf AEM

Sobald die Bereitstellung abgeschlossen ist und AEM vollständig gestartet wurde:

**AEM-Autoren-URL:**
```http://<server-ip>:8080/cq-quickstart```

**Standardanmeldeinformationen:**

* Benutzername: `admin`
* Passwort: `admin`

**Wichtig:** Ändern Sie das Standardkennwort sofort nach der ersten Anmeldung.

### Fehlerbehebung

#### Gängige Probleme

| Problem | Lösung |
|-------|----------|
| Die Bereitstellung schlägt mit ClassNotFoundException fehl | Überprüfen, ob `jboss-deployment-structure.xml` ordnungsgemäß konfiguriert ist |
| OutOfMemoryError beim Start | Heap-Speicher in `standalone.conf.bat` erhöhen |
| AEM startet nicht nach der Bereitstellung | Überprüfen der JBoss-Protokolle in `<JBOSS_HOME>\standalone\log\server.log` |
| Zugriff auf AEM im Browser nicht möglich | Firewall-Einstellungen auf Port 8080 überprüfen |

#### Protokolldateien

* **JBoss-Serverprotokoll:** `<JBOSS_HOME>\standalone\log\server.log`
* **AEM-Fehlerprotokoll:** nach dem Start über die AEM-Web-Konsole verfügbar unter\
  `http://<server-ip>:8080/cq-quickstart/system/console`

### Zusätzliche Konfiguration

#### Konfigurieren von Ausführungsmodi

Um die AEM-Ausführungsmodi (author/publish) zu ändern, ändern Sie den `sling.run.modes` in `WEB-INF\web.xml`, bevor Sie WAR neu verpacken:

```xml
<init-param>
    <param-name>sling.run.modes</param-name>
    <param-value>publish</param-value>
</init-param>
```

#### Produktions-Recommendations

Für Produktionsumgebungen:

* Konfigurieren von SSL-/TLS-Zertifikaten in JBoss
* Einrichten von AEM-Replikationsagenten
* Konfigurieren des Dispatchers für den Lastenausgleich
* Automatisierte Sicherungen aktivieren
* Implementieren von Überwachung und Warnhinweisen

### Verwandte Dokumentation

* [JBoss EAP 8-Dokumentation](https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/8.0)
* [Dokumentation zu Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de)
* [Installations- und Bereitstellungshandbuch für AEM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=de)

### Dokumentinformation

| Feld | Wert |
|-------|-------|
| Zuletzt aktualisiert | Februar 2026 |
| AEM-Version | 6.5+ (LTS) |
| JBoss-Version | EAP 8.x |
| JDK-Version | 21 |
| Platform | Windows |


