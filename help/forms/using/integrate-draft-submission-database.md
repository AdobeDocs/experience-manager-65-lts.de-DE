---
title: Beispiel zur Integrierung der Komponente „Entwürfe und Sendungen“ in die Datenbank
description: Referenzimplementierung von benutzerdefinierten Daten- und Metadatendiensten zur Integration der Komponente „Entwürfe und Sendungen“ in eine Datenbank.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
solution: Experience Manager, Experience Manager Forms
feature: Forms Portal
role: Admin, User, Developer
exl-id: b9b989e3-f204-4929-a03a-857cbb786185
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1502'
ht-degree: 100%

---

# Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank {#sample-for-integrating-drafts-submissions-component-with-database}

## Überblick zum Beispiel {#sample-overview}

Mit der Komponente „Entwürfe und Sendungen“ des AEM Forms-Portals können Benutzende ihre Formulare als Entwürfe speichern und zu einem späteren Zeitpunkt von jedem beliebigen Gerät senden. Zudem können die Benutzenden ihre übermittelten Formulare im Portal anzeigen. Um diese Funktion zu aktivieren, bietet AEM Forms Daten- und Metadatendienste an, um die von Benutzenden im Formular eingegebenen Daten sowie die mit Entwürfen und gesendeten Formularen verknüpften Metadaten zu speichern. Diese Daten werden standardmäßig im CRX-Repository gespeichert. Da die Benutzenden mit den Formularen jedoch über eine AEM-Veröffentlichunginstanz interagieren, die in der Regel außerhalb der Unternehmens-Firewall liegt, sollten Sie die Datenspeicherung so anpassen, dass sie sicherer und zuverlässiger ist.

Bei dem in diesem Dokument gezeigten Beispiel handelt es sich um eine Referenzimplementierung benutzerdefinierter Daten- und Metadatendienste zur Integration der Komponente „Entwürfe und Sendungen“ in eine Datenbank. In der Beispielimplementierung wird die Datenbank **MySQL 5.6.24** verwendet. Sie können die Komponente „Entwürfe und Sendungen“ jedoch in eine Datenbank Ihrer Wahl integrieren.

>[!NOTE]
>
>* Die Beispiele und Konfigurationen in diesem Dokument entsprechen MySQL 5.6.24. Sie müssen sie für Ihr Datenbanksystem entsprechend anpassen.
>* Stellen Sie sicher, dass Sie die neueste Version des AEM Forms-Add-On-Pakets installiert haben. Eine Liste der verfügbaren Pakete finden Sie im Artikel [AEM Forms-Versionen](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html).
>* Das Beispielpaket funktioniert nur mit Übermittlungsaktionen für adaptive Formulare.

## Beispiel installieren und konfigurieren {#set-up-and-configure-the-sample}

Führen Sie die folgenden Schritte für alle Autoren- und Veröffentlichungsinstanzen durch, um das Beispiel zu installieren und zu konfigurieren :

1. Laden Sie das folgende **aem-fp-db-integration-sample-pkg-6.1.2.zip**-Paket auf Ihr Dateisystem herunter.

   Beispielpaket zur Datenbankintegration:

[Datei laden](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. Gehen Sie zu AEM Package Manager unter https://[*host*]:[*port*]/crx/packmgr/.
1. Klicken Sie auf **[!UICONTROL Paket hochladen]**.

1. Navigieren Sie zum Paket **aem-fp-db-integration-sample-pkg-6.1.2.zip**, wählen Sie es aus und klicken Sie auf **[!UICONTROL OK]**.
1. Klicken Sie neben dem Paket auf **[!UICONTROL Installieren]**, um das Paket zu installieren.
1. Gehen Sie zur Seite **[!UICONTROL Konfiguration der AEM-Webkonsole]**
unter https://[*host*]:[*port*]/system/console/configMgr.
1. Klicken Sie, um die **[!UICONTROL Konfiguration des Forms Portals für Entwurf und Übermittlung]** im Bearbeitungsmodus zu öffnen.

1. Geben Sie die Werte für die Eigenschaften an, wie in der folgenden Tabelle beschrieben:

   | **Eigenschaft** | **Beschreibung** | **Wert** |
   |---|---|---|
   | Entwurfs-Datendienst des Formularportals | Kennung für Entwurfs-Datendienst | formsportal.sampledataservice |
   | Entwurfs-Metadatendienst des Formularportals | Bezeichner für den Dienst für Entwurfs-Metadaten | formsportal.samplemetadataservice |
   | Übermittlungs-Datendienst des Formularportals | Bezeichner für den Dienst zur Datenübermittlung | formsportal.sampledataservice |
   | Übermittlungs-Metadatendienst des Formularportals | Bezeichner für den Dienst Metadatenübermittlung | formsportal.samplemetadataservice |
   | Datendienst für ausstehende Signaturen des Formularportals | Bezeichner für den Dienst für Daten zu ausstehende Signaturen | formsportal.sampledataservice |
   | Metadatendienst für ausstehende Signaturen des Formularportals | Bezeichner für den Dienst für Metadaten zu ausstehende Signaturen | formsportal.samplemetadataservice |

   >[!NOTE]
   >
   >Die Dienste werden nach ihren Namen aufgelöst, die als Wert für den `aem.formsportal.impl.prop`-Schlüssel wie folgt erwähnt werden:

   ```java
   @Service(value = {SubmitDataService.class, DraftDataService.class})
   @Property(name = "aem.formsportal.impl.prop", value = "formsportal.sampledataservice")
   @Service(value = { SubmitMetadataService.class, DraftMetadataService.class })
   @Property(name = "aem.formsportal.impl.prop", value = "formsportal.samplemetadataservice")
   ```

   Sie können die Namen der Daten- und Metadatentabellen ändern.

   So geben Sie einen anderen Namen für die Metadatentabelle an:

   * Klicken Sie auf der Seite zur Web-Konsolenkonfiguration auf die Beispielimplementierung des Formularportal-Metadatendienstes. Sie können die Werte der Datenquelle, Metadaten/zusätzlichen Metadatentabellennamen ändern.

   So geben Sie einen anderen Namen für die Datentabelle an:

   * Klicken Sie auf der Seite zur Web-Konsolenkonfiguration auf die Beispielimplementierung des Formularportal-Datendienstes. Sie können die Werte der Datenquelle und Datentabellennamen ändern.

   >[!NOTE]
   >
   >Wenn Sie die Tabellennamen ändern, geben Sie sie in der Formularportal-Konfiguration an.

1. Belassen Sie die anderen Konfigurationen und klicken Sie auf **[!UICONTROL Speichern]**.

1. Die Datenbankverbindung kann über die Apache Sling Connection Pooled Datenquelle erfolgen.
1. Klicken Sie für die Apache Sling-Verbindung in der Konfiguration der Web-Konsole im Bearbeitungsmodus auf **[!UICONTROL Apache Sling Connection Pooled DataSource]**. Geben Sie die Werte für die Eigenschaften an, wie in der folgenden Tabelle beschrieben:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Wert</strong></td>
  </tr>
  <tr>
   <td>Datenquellenname</td>
   <td><p>Ein Datenquellenname für das Filtern der Treiber aus dem Datenquellen-Pool</p> <p><strong>Hinweis: </strong><em>In der Beispielimplementierung wird „FormsPortal“ als Datenquellenname verwendet.</em></p> </td>
  </tr>
  <tr>
   <td>JDBC-Treiberklasse</td>
   <td>com.mysql.jdbc.Driver</td>
  </tr>
  <tr>
   <td>JDBC-Verbindungs-URI<br /> </td>
   <td>jdbc:mysql://[<em>host</em>]:[<em>port</em>]/[<em>schema_name</em>]</td>
  </tr>
  <tr>
   <td>Benutzername</td>
   <td>Benutzername zur Authentifizierung und Durchführung von Aktionen für Datenbanktabellen</td>
  </tr>
  <tr>
   <td>Kennwort</td>
   <td>Passwort für den Benutzernamen</td>
  </tr>
  <tr>
   <td>Transaktions-Isolierung</td>
   <td>READ_COMMITTED</td>
  </tr>
  <tr>
   <td>Max. aktive Verbindungen</td>
   <td>1.000</td>
  </tr>
  <tr>
   <td>Max. inaktive Verbindungen</td>
   <td>100</td>
  </tr>
  <tr>
   <td>Min. inaktive Verbindungen</td>
   <td>10</td>
  </tr>
  <tr>
   <td>Anfangsgröße</td>
   <td>10</td>
  </tr>
  <tr>
   <td>Max. Wartezeit</td>
   <td>100000</td>
  </tr>
  <tr>
   <td>Test zu Leihung</td>
   <td>Aktiviert</td>
  </tr>
  <tr>
   <td>Test bei Inaktivität</td>
   <td>Aktiviert</td>
  </tr>
  <tr>
   <td>Validierungsabfrage</td>
   <td>Beispielwerte sind SELECT 1(mysql), select 1 from dual(oracle), SELECT 1(MS Sql Server) (validationQuery)</td>
  </tr>
  <tr>
   <td>Maximale Wartezeit der Validierungsabfrage</td>
   <td>10000</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Der JDBC-Treiber für MySQL wird nicht mit dem Beispiel geliefert.  Stellen Sie sicher, dass Sie ihn bereitgestellt haben, und geben Sie die erforderlichen Informationen ein, um den JDBC-Verbindungs-Pool zu konfigurieren.
>* Lassen Sie Ihre Autoren- und Veröffentlichungsinstanzen auf dieselbe Datenbank verweisen.  Der Wert des URI-Feldes für die JDBC-Verbindung muss für alle Autoren- und Veröffentlichungsinstanzen gleich sein.

1. Belassen Sie die anderen Konfigurationen und klicken Sie auf **[!UICONTROL Speichern]**.

1. Wenn bereits eine Tabelle im Datenbankschema vorhanden ist, fahren Sie mit dem nächsten Schritt fort.

   Wenn Sie noch keine Tabelle im Datenbankschema haben, führen Sie die folgenden SQL-Anweisungen aus, um separate Tabellen für Daten, Metadaten und weitere Metadaten im Datenbankschema zu erstellen:

   >[!NOTE]
   >
   >Sie benötigen nicht verschiedene Datenbanken für Autoren- und Veröffentlichungsinstanzen. Verwenden Sie dieselbe Datenbank für alle Autor- und Veröffentlichungsinstanzen. 

   **SQL-Anweisung für Datentabelle**

   ```sql
   CREATE TABLE `data` (
   `owner` varchar(255) DEFAULT NULL,
   `data` longblob,
   `metadataId` varchar(45) DEFAULT NULL,
   `id` varchar(45) NOT NULL,
   PRIMARY KEY (`id`)
   ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

   **SQL-Anweisung für Metadatentabelle**

   ```sql
   CREATE TABLE `metadata` (
   `formPath` varchar(1000) DEFAULT NULL,
   `formType` varchar(100) DEFAULT NULL,
   `description` text,
   `formName` varchar(255) DEFAULT NULL,
   `owner` varchar(255) DEFAULT NULL,
   `enableAnonymousSave` varchar(45) DEFAULT NULL,
   `renderPath` varchar(1000) DEFAULT NULL,
   `nodeType` varchar(45) DEFAULT NULL,
   `charset` varchar(45) DEFAULT NULL,
   `userdataID` varchar(45) DEFAULT NULL,
   `status` varchar(45) DEFAULT NULL,
   `formmodel` varchar(45) DEFAULT NULL,
   `markedForDeletion` varchar(45) DEFAULT NULL,
   `showDorClass` varchar(255) DEFAULT NULL,
   `sling:resourceType` varchar(1000) DEFAULT NULL,
   `attachmentList` longtext,
   `draftID` varchar(45) DEFAULT NULL,
   `submitID` varchar(45) DEFAULT NULL,
   `id` varchar(60) NOT NULL,
   `profile` varchar(255) DEFAULT NULL,
   `submitUrl` varchar(1000) DEFAULT NULL,
   `xdpRef` varchar(1000) DEFAULT NULL,
   `agreementId` varchar(255) DEFAULT NULL,
   `nextSigners` varchar(255) DEFAULT NULL,
   `eSignStatus` varchar(45) DEFAULT NULL,
   `pendingSignID` varchar(45) DEFAULT NULL,
   `agreementDataId` varchar(255) DEFAULT NULL,
   `enablePortalSubmit` varchar(45) DEFAULT NULL,
   `submitType` varchar(45) DEFAULT NULL,
   `dataType` varchar(45) DEFAULT NULL,
   `jcr:lastModified` varchar(45) DEFAULT NULL,
   PRIMARY KEY (`id`),
   UNIQUE KEY `ID_UNIQUE` (`id`)
   ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

   **SQL-Anweisung für additionalmetadatatable**

   ```sql
   CREATE TABLE `additionalmetadatatable` (
   `value` text,
   `key` varchar(255) NOT NULL,
   `id` varchar(60) NOT NULL,
   PRIMARY KEY (`id`,`key`),
   CONSTRAINT 'additionalmetadatatable_fk' FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
   ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

   **SQL-Anweisung für Kommentartabelle**

   ```sql
   CREATE TABLE `commenttable` (
   `commentId` varchar(255) DEFAULT NULL,
   `comment` text DEFAULT NULL,
   `ID` varchar(255) DEFAULT NULL,
   `commentowner` varchar(255) DEFAULT NULL,
   `time` varchar(255) DEFAULT NULL);
   ```

1. Wenn die Tabellen („data“, „metadata“ und „additionalmetadatatable“) bereits im Datenbankschema vorhanden sind, führen Sie folgende Abfragen zum Ändern von Tabellen aus:

   **SQL-Anweisung zum Ändern der Tabelle „data“**

   ```sql
   ALTER TABLE `data` CHANGE `owner` `owner` VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL;
   ```

   **SQL-Anweisung zum Ändern der Tabelle „metadata“**

   ```sql
   ALTER TABLE metadata add markedForDeletion varchar(45) DEFAULT NULL
   ```

   >[!NOTE]
   >
   >Die Metadatenanfrage „Tabelle ändern“ schlägt fehl, wenn Sie diese bereits ausführen und die Spalte „markedfordeletion“ ist in der Tabelle vorhanden.

   ```sql
   ALTER TABLE metadata add agreementId varchar(255) DEFAULT NULL,
   add nextSigners varchar(255) DEFAULT NULL,
   add eSignStatus varchar(45) DEFAULT NULL,
   add pendingSignID varchar(45) DEFAULT NULL,
   add agreementDataId varchar(255) DEFAULT NULL,
   add enablePortalSubmit varchar(45) DEFAULT NULL,
   add submitType varchar(45) DEFAULT NULL,
   add dataType varchar(45) DEFAULT NULL;
   ```

   ```sql
   ALTER TABLE `metadata` CHANGE `formPath` `formPath` VARCHAR(1000) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `formType` `formType` VARCHAR(100) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `description` `description` TEXT CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `formName` `formName` VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `owner` `owner` VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `renderPath` `renderPath` VARCHAR(1000) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `showDorClass` `showDorClass` VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `sling:resourceType` `sling:resourceType` VARCHAR(1000) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `profile` `profile` VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `submitUrl` `submitUrl` VARCHAR(1000) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `xdpRef` `xdpRef` VARCHAR(1000) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL;
   ```

   **SQL-Anweisung zum Ändern der Tabelle „additionalmetadatatable“**

   ```sql
   ALTER TABLE `additionalmetadatatable` CHANGE `value` `value` TEXT CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL, CHANGE `key` `key` VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL;
   ```

Die Beispielimplementierung ist jetzt konfiguriert. Sie können sie verwenden, um Ihre Entwürfe und Sendungen aufzulisten, während Sie alle Daten und Metadaten in einer Datenbank speichern. Als Nächstes geht es darum, wie im Beispiel die Daten- und Metadatendienste konfiguriert werden.

## Installieren der Datei mysql-connector-java-5.1.39-bin.jar {#install-mysql-connector-java-bin-jar-file}

Führen Sie die folgenden Schritte auf allen Autoren- und Veröffentlichungsinstanzen aus, um die Datei mysql-connector-java-5.1.39-bin.jar zu installieren:

1. Navigieren Sie zu `https://'[server]:[port]'/system/console/depfinder` und suchen Sie nach dem com.mysql.jdbc-Paket.
1. Überprüfen Sie in der Spalte „Exportiert von“, ob das Paket von einem Paket exportiert wird.

   Fahren Sie fort, wenn das Paket nicht von einem Paket exportiert wird.

1. Navigieren Sie zu `https://'[server]:[port]'/system/console/bundles` und klicken Sie auf **[!UICONTROL Installieren/Aktualisieren]**.
1. Klicken Sie auf **[!UICONTROL Datei auswählen]** und wählen Sie die Datei mysql-connector-java-5.1.39-bin.jar. Aktivieren Sie außerdem die Kontrollkästchen **[!UICONTROL Paket starten]** und **[!UICONTROL Paket aktualisieren]**.
1. Klicken Sie auf **[!UICONTROL Installieren oder Aktualisieren]**. Wenn dies abgeschlossen ist, starten Sie den Server neu.
1. (*Nur Windows*) Deaktivieren Sie die System-Firewall für Ihr Betriebssystem.

>[!NOTE]
>
> Es wird empfohlen, den Befehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

## Beispielcode für Formularportaldaten und Metadatendienst {#sample-code-for-forms-portal-data-and-metadata-service}

Die folgende Zip enthält`FormsPortalSampleDataServiceImpl` und`FormsPortalSampleMetadataServiceImpl` (Implementierungsklassen) für Benutzeroberflächen für Daten- und Metadatendienste. Zusätzlich enthält es alle Klassen, die für die Kompilierung der oben genannten Implementierungsklassen benötigt werden.

[Datei laden](assets/sample_package.zip)

## Überprüfen der Länge des Dateinamens  {#verify-length-of-the-file-name}

Die Datenbankimplementierung des Formularportals verwendet eine zusätzliche Metadatentabelle. Die Tabelle hat einen zusammengesetzten Primärschlüssel, der auf den Schlüssel- und ID-Spalten der Tabelle basiert. MySQL ermöglicht Primärschlüssel bis zu einer Länge von 255 Zeichen. Sie können das folgende Client-seitige Validierungsskript verwenden, um die Länge des Dateinamens zu überprüfen, der an das Datei-Widget angehängt ist. Die Überprüfung wird ausgeführt, wenn eine Datei angehängt ist. Das Skript, das im folgenden Verfahren bereitgestellt wird, zeigt eine Meldung an, wenn der Dateiname (einschließlich Erweiterung) mehr als 150 Zeichen hat. Sie können das Skript modifizieren, um es auf eine andere Anzahl von Zeichen zu überprüfen. 

Führen Sie die folgenden Schritte aus, um eine [Client-Bibliothek](/help/sites-developing/clientlibs.md) zu erstellen und das Skript zu verwenden:

1. Melden Sie sich bei CRXDE an und navigieren Sie zu „/etc/clientlibs/“.
1. Erstellen Sie einen Knoten vom Typ **cq:ClientLibraryFolder** und geben Sie einen Knotennamen an. Beispiel: `validation`.

   Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Klicken Sie mit der rechten Maustaste auf den Knoten **[!UICONTROL Neue Datei erstellen]** und legen Sie eine Datei mit der Erweiterung .txt an. Beispiel: `js.txt` Fügen Sie den folgenden Code zur neu erstellten .txt-Datei hinzu und klicken Sie auf **[!UICONTROL Alle speichern]**.

   ```javascript
   #base=util
    util.js
   ```

   Im vorstehenden Code ist `util` der Name des Ordners und`util.js` der Name der Datei im `util`-Ordner. Der Ordner `util` und die Datei `util.js` werden in aufeinanderfolgenden Schritten erstellt.

1. Klicken Sie mit der rechten Maustaste auf den Knoten `cq:ClientLibraryFolder`, der in Schritt 2 erstellt wurde, wählen Sie „Erstellen“ > „Ordner erstellen“. Erstellen Sie einen Ordner mit dem Namen `util`. Klicken Sie auf **[!UICONTROL Alle speichern]**. Klicken Sie mit der rechten Maustaste auf den Ordner `util` und wählen Sie „Erstelle“ > „Ordner erstellen“. Erstellen Sie eine Datei mit dem Namen `util.js`. Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Fügen Sie der Datei „POST.jsp“ folgenden Code hinzu und klicken Sie auf **[!UICONTROL Alle speichern]**. Die Code-Validierungslänge des Dateinamens.

   ```javascript
   /*
    * ADOBE CONFIDENTIAL
    * ___________________
    *
    * Copyright 2016 Adobe Systems Incorporated
    * All Rights Reserved.
    *
    * NOTICE:  All information contained herein is, and remains
    * the property of Adobe Systems Incorporated and its suppliers,
    * if any.  The intellectual and technical concepts contained
    * herein are proprietary to Adobe Systems Incorporated and its
    * suppliers and may be covered by U.S. and Foreign Patents,
    * patents in process, and are protected by trade secret or copyright law.
    * Dissemination of this information or reproduction of this material
    * is strictly forbidden unless prior written permission is obtained
    * from Adobe Systems Incorporated.
    *
    */
   (function () {
       var connectWithGuideBridge = function (gb) {
           gb.connect(function () {
               //For first time load
               window.guideBridge.on("elementValueChanged" , function(event, payload) {
           var component = payload.target; // Field whose value has changed
                   if(component.name == 'fileAttachment' && component.parent) {
                       var fileItems = $('#'+payload.target.parent.id).find(".guide-fu-fileItem");
                       for (i = 0;i<fileItems.length;i++) {
                           var filename = $(fileItems[i]).find(".guide-fu-fileName").text();
                           //check whether it is previously attached file or a newly  attached one
                           if(filename.length > 150 && filename.indexOf("fp.attach.jsp") < 0) {
                               window.alert("filename is larger than 150 : "+filename);
                                $(fileItems[i]).find(".guide-fu-fileClose.close").click();
                           }
                       }
                   }
   
      });
           });
       };
   
       if (window.guideBridge) {
           connectWithGuideBridge(window.guideBridge);
       } else {
           window.addEventListener("bridgeInitializeStart", function (event) {
               connectWithGuideBridge(event.detail.guideBridge);
           });
       }
   })();
   ```

   >[!NOTE]
   >
   >Das Skript ist für eine vorkonfigurierte Anlagen-Widget-Komponente. Wenn Sie das vorkonfigurierte Anlagen-Widget angepasst haben, ändern Sie das obige Skript, um entsprechende Änderungen zu implementieren.

1. Fügen Sie dem in Schritt 2 erstellten Ordner die folgende Eigenschaft hinzu und klicken Sie auf **[!UICONTROL Alle speichern]**.

   * **[!UICONTROL Name:]** categories

   * **[!UICONTROL Typ:]** String

   * **[!UICONTROL Wert:]** fp.validation

   * **[!UICONTROL Multi-Option:]** Aktiviert

1. Navigieren Sie zu `/libs/fd/af/runtime/clientlibs/guideRuntime`und fügen Sie den Wert `fp.validation` an die Eigenschaft embed an.

1. Navigieren Sie zu /libs/fd/af/runtime/clientlibs/guideRuntimeWithXFA und hängen Sie den Wert `fp.validation` an die Eigenschaft embed an.

   >[!NOTE]
   >
   >Wenn Sie anstelle der Client-Bibliotheken guideRuntime und guideRuntimeWithXfa benutzerdefinierte Client-Bibliotheken verwenden, verwenden Sie den Kategorienamen, um die in diesem Verfahren erstellte Client-Bibliothek in Ihre zur Laufzeit geladenen benutzerdefinierten Bibliotheken einzubetten.

1. Klicken Sie auf **[!UICONTROL Alle speichern.]** Wenn der Dateiname größer als 150 (einschließlich Erweiterung) Zeichen ist, wird eine Meldung angezeigt. 
