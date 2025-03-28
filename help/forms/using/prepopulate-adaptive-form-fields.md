---
title: Vorbefüllen von Feldern in adaptiven Formularen
description: Verwenden Sie bestehende Daten, um die Felder eines adaptiven Formulars zu befüllen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
feature: Adaptive Forms,Foundation Components
discoiquuid: 7139a0e6-0e37-477c-9e0b-aa356991d040
docset: aem65
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: 69734a2b-7f9d-4661-a1e9-3bf6e362c272
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '2203'
ht-degree: 100%

---

# Vorbefüllen von Feldern in adaptiven Formularen{#prefill-adaptive-form-fields}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/prepopulate-adaptive-form-fields.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

## Einführung {#introduction}

Sie können die Felder eines adaptiven Formulars mit vorhandenen Daten vorbefüllen. Wenn ein Benutzer ein Formular öffnet, werden die Werte für diese Felder vorbefüllt. Um ein adaptives Formular mit Daten vorzufüllen, stellen Sie die Benutzerdaten als vorbefüllte XML/JSON in dem Format bereit, das der Datenstruktur zum Vorbefüllen von adaptiven Formularen entspricht.

## Struktur der Vorbefüllungsdaten {#the-prefill-structure}

Ein adaptives Formular kann eine Mischung aus gebundenen und ungebundenen Feldern enthalten. Gebundene Felder sind diejenigen, die aus der Registerkarte für die Inhaltssuche gezogen werden und einen nicht leeren Wert für die `bindRef`-Eigenschaft im Dialogfeld zum Bearbeiten von Feldern enthalten. Ungebundene Felder werden direkt aus dem Sidekick gezogen und haben einen leeren `bindRef`-Wert.

Sie können sowohl gebundene als auch ungebundene Felder eines adaptiven Formulars vorbefüllen. Die Vorbefüllungsdaten enthalten die Abschnitte „afBoundData“ und „afUnBoundData“, um sowohl gebundene als auch ungebundene Felder eines adaptiven Formulars vorzubefüllen. Der Abschnitt `afBoundData` enthält die Daten zum Vorbefüllen für gebundene Felder und Bereiche. Diese Daten müssen mit dem verknüpften Formularmodellschema konform sein:

* Bei adaptiven Formularen mit der [XFA-Formularvorlage](../../forms/using/prepopulate-adaptive-form-fields.md) muss die XML zum Vorbefüllen mit dem Datenschema der XFA-Vorlage konform sein.
* Bei adaptiven Formularen mit [XML-Schema](#xml-schema-af) muss die XML zum Vorbefüllen mit der XML-Schemastruktur konform sein.
* Bei adaptiven Formularen mit dem [JSON-Schema](#json-schema-based-adaptive-forms) muss die JSON zum Vorbefüllen mit dem JSON-Schema konform sein.
* Bei adaptiven Formularen mit dem FDM-Schema muss die JSON zum Vorbefüllen mit dem FDM-Schema konform sein.
* Bei adaptiven Formularen [ohne Formularmodell](#adaptive-form-with-no-form-model) gibt es keine gebundenen Daten. Jedes Feld ist ein ungebundenes Feld und wird anhand der ungebundenen XML vorausgefüllt.

### XML-Beispielstruktur zum Vorbefüllen {#sample-prefill-xml-structure}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<afData>
  <afBoundData>
     <employeeData>
        .
     </employeeData>
  </afBoundData>

  <afUnboundData>
    <data>
      <textbox>Hello World</textbox>
         .
         .
      <numericbox>12</numericbox>
         . 
         .              
    </data>
  </afUnboundData>
</afData>
```

### JSON-Beispielstruktur zum Vorbefüllen {#sample-prefill-json-structure}

```javascript
{
   "afBoundData": {
      "employeeData": { }
   },
   "afUnboundData": {
      "data": {
         "textbox": "Hello World",
         "numericbox": "12"
      }
   }
}
```

Im Fall von gebundenen Feldern mit demselben „bindref“ oder ungebundenen Feldern mit demselben Namen, werden die im XML-Tag oder JSON-Objekt angegebenen Daten in alle Felder eingefügt. Beispiel: Zwei Felder in einem Formular sind dem Namen `textbox` in den Vorbefüllungsdaten zugeordnet. Wenn das erste Feld für das Textfeld „A“ enthält, wird zur Laufzeit im zweiten Textfeld automatisch „A“ ausgefüllt. Diese Verknüpfung wird als Live-Verknüpfung von Feldern adaptiver Formulare bezeichnet.

### Adaptives Formular mit XFA-Formularvorlage {#xfa-based-af}

Die Struktur der vorausgefüllten XML-Datei und der übermittelten XML-Datei für XFA-basierte adaptive Formulare ist wie folgt:

* **XML-Struktur zum Vorbefüllen**: Die XML zum Vorausfüllen für XFA-basierte adaptive Formulare muss mit dem Datenschema der XFA-Formularvorlage konform sein. Um ungebundene Felder vorzubefüllen, umschließen Sie die XML-Struktur zum Vorbefüllen in das Tag `/afData/afBoundData`.

* **Übermittelte XML-Struktur**: Wenn keine XML zum Vorbefüllen verwendet wird, enthält die übermittelte XML Daten für gebundene und ungebundene Felder im `afData`-Wrapper-Tag. Wenn XML zum Vorbefüllen verwendet wird, enthält die übermittelte XML dieselbe Struktur wie die XML zum Vorbefüllen. Wenn die XML zum Vorbefüllen mit dem `afData`-Stamm-Tag beginnt, hat die Ausgabe-XML ebenfalls dasselbe Format. Wenn die XML zum Vorbefüllen den `afData/afBoundData`-Wrapper nicht enthält und stattdessen direkt aus dem Schema-Root-Tag beginnt wie `employeeData`, beginnt die übermittelte XML ebenfalls mit dem `employeeData`-Tag.

Prefill-Submit-Data-ContentPackage.zip

[Datei laden](assets/prefill-submit-data-contentpackage.zip)
Beispiel mit vorbefüllten und übermittelten Daten

### XML-Schema-basierte adaptive Formulare  {#xml-schema-af}

Die Struktur von Prefill-XML und von eingereichten XML für adaptive Formulare, die auf XML-Schemata basieren, ist wie folgt:

* **XML-Struktur zum Vorbefüllen**: Die XML zum Vorbefüllen muss mit dem verknüpften XML-Schema konform sein. Um ungebundene Felder vorzubefüllen, umschließen Sie die XML-Struktur zum Vorbefüllen in das Tag „/afData/afBoundData“.
* **Übermittelte XML-Struktur**: Wenn keine XML zum Vorbefüllen verwendet wird, enthält die übermittelte XML Daten für gebundene und ungebundene Felder im `afData`-Wrapper-Tag. Wenn die XML zum Vorbefüllen verwendet wird, enthält die übermittelte XML dieselbe Struktur wie die XML zum Vorbefüllen. Wenn die XML zum Vorbefüllen mit dem `afData`-Stamm-Tag beginnt, hat die Ausgabe-XML dasselbe Format. Wenn die XML zum Vorbefüllen nicht den `afData/afBoundData`-Wrapper aufweist und stattdessen direkt aus dem Schemastamm-Tag beginnt wie `employeeData`, beginnt die übermittelte XML ebenfalls mit dem `employeeData`-Tag.

```xml
<?xml version="1.0" encoding="utf-8" ?> 
<xs:schema targetNamespace="https://adobe.com/sample.xsd"
            xmlns="https://adobe.com/sample.xsd"
            xmlns:xs="https://www.w3.org/2001/XMLSchema">
 
    <xs:element name="sample" type="SampleType"/>
         
    <xs:complexType name="SampleType">
        <xs:sequence>
            <xs:element name="noOfProjectsAssigned" type="xs:string"/>
        </xs:sequence>
    </xs:complexType>
</xs:schema>
```

Bei Feldern, deren Modell das XML-Schema ist, werden die Daten im `afBoundData`-Tag wie im XML-Beispielschema unten dargestellt vorbefüllt. Es kann zum Vorfüllen eines adaptiven Formulars mit einem oder mehreren ungebundenen Textfeldern verwendet werden.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <textbox>Ignorance is bliss :) </textbox>
    </data>
  </afUnboundData>
  <afBoundData>
    <data>
      <noOfProjectsAssigned>twelve</noOfProjectsAssigned>
    </data>
  </afBoundData>
</afData>
```

>[!NOTE]
>
>Es wird empfohlen, keine ungebundenen Felder in gebundenen Bereichen zu verwenden (Bereiche mit nicht leerem `bindRef`-Wert, der durch Ziehen von Komponenten aus dem Sidekick oder der Registerkarte „Datenquellenr“ erstellt wurde). Dies kann zu Datenverlust bei diesen ungebundenen Feldern führen. Darüber hinaus wird empfohlen, dass die Namen der Felder im gesamten Formular eindeutig sind, insbesondere für ungebundene Felder.

#### Beispiel ohne „afData“- und „afBoundData“-Wrapper {#an-example-without-afdata-and-afbounddata-wrapper}

```xml
<?xml version="1.0" encoding="UTF-8"?><config>
 <assignmentDetails descriptionOfAssignment="Some Science Project" durationOfAssignment="34" financeRelatedProject="1" name="Lisa" numberOfMentees="1"/>
 <assignmentDetails descriptionOfAssignment="Kidding, right?" durationOfAssignment="4" financeRelatedProject="1" name="House" numberOfMentees="3"/>
</config>
```

### JSON-Schema-basierte adaptive Formulare {#json-schema-based-adaptive-forms}

Für adaptive Formulare, die auf dem JSON-Schema basieren, wird im Folgenden die Struktur von JSONs zum Vorbefüllen und vom übermittelten JSONs beschrieben. Weitere Informationen finden Sie unter [Erstellen von adaptiven Formularen mit dem JSON-Schema](../../forms/using/adaptive-form-json-schema-form-model.md).

* **Struktur von JSON zum Vorbefüllen**: Das JSON zum Vorbefüllen muss mit dem verknüpften JSON-Schema konform sein. Optional kann es in das „/afData/afBoundData“-Objekt eingeschlossen werden, wenn Sie auch ungebundene Felder vorbefüllen möchten.
* **Übermittelte JSON-Struktur**: Wenn kein JSON zum Vorbefüllen verwendet wird, enthält das übermittelte JSON im „afData-Wrapper“-Tag Daten für gebundene und ungebundene Felder. Wenn das JSON zum Vorbefüllen verwendet wird, enthält das übermittelte JSON dieselbe Struktur wie das JSON zum Vorbefüllen. Wenn das JSON zum Vorbefüllen mit dem „afData“-Stamm-Objekt beginnt, hat das Ausgabe-JSON dasselbe Format. Wenn das JSON zum Vorbefüllen keinen „afData/afBoundData“-Wrapper hat und stattdessen direkt vom Schemastammobjekt startet, z. B. Benutzer, dann startet das übermittelte JSON ebenfalls mit dem Objekt „Benutzer“.

```json
{
    "id": "https://some.site.somewhere/entry-schema#",
    "$schema": "https://json-schema.org/draft-04/schema#",
    "type": "object",
    "properties": {
        "address": {
            "type": "object",
            "properties": { 
    "name": {
     "type": "string"
    },
    "age": {
     "type": "integer"
}}}}}
```

Bei Feldern, die das JSON-Schemamodell verwenden, sind die Daten im „afBoundData“-Objekt bereits vorbefüllt, wie im folgenden Beispiel-JSON gezeigt. Es kann zum Vorfüllen eines adaptiven Formulars mit einem oder mehreren ungebundenen Textfeldern verwendet werden. Im Folgenden finden Sie ein Beispiel für die Daten mit `afData/afBoundData`-Wrapper:

```json
{
  "afData": {
    "afUnboundData": {
      "data": { "textbox": "Ignorance is bliss :) " }
    },
    "afBoundData": {
      "data": { {
   "user": {
    "address": {
     "city": "Noida",
     "country": "India"
}}}}}}}
```

Im Folgenden finden Sie ein Beispiel ohne `afData/afBoundData`-Wrapper:

```json
{
 "user": {
  "address": {
   "city": "Noida",
   "country": "India"
}}}
```

>[!NOTE]
>
>Die Verwendung von ungebundenen Feldern in gebundenen Bedienfeldern (Bedienfelder mit nicht leerer bindRef, die durch Ziehen von Komponenten aus der Registerkarte „Sidekick“ oder „Datenquellen“ erstellt wurden) wird **nicht** empfohlen, da dies zum Verlust von Daten der ungebundenen Felder führen kann. Es wird empfohlen, eindeutige Feldnamen im gesamten Formular zu verwenden, insbesondere für ungebundene Felder.

### Adaptives Formular ohne Formularmodell {#adaptive-form-with-no-form-model}

Bei adaptiven Formularen ohne Formularmodell befinden sich die Daten für alle Felder unter dem Tag `<data>` von `<afUnboundData> tag`.

Beachten Sie außerdem Folgendes:

Die XML-Tags für die Benutzerdaten, die für verschiedene Felder übermittelt werden, werden mit dem Namen der Felder generiert. Daher müssen die Feldnamen eindeutig sein.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <radiobutton>2</radiobutton>
      <repeatable_panel_no_form_model>
        <numericbox>12</numericbox>
      </repeatable_panel_no_form_model>
      <repeatable_panel_no_form_model>
        <numericbox>21</numericbox>
      </repeatable_panel_no_form_model>
      <checkbox>2</checkbox>
      <textbox>Nopes</textbox>
    </data>
  </afUnboundData>
  <afBoundData/>
</afData>
```

## Konfigurieren des Vorbefüllungs-Service mithilfe von Configuration Manager {#configuring-prefill-service-using-configuration-manager}

Um den Vorbefüllungs-Service zu aktivieren, müssen Sie die standardmäßige Vorbefüllungs-Service-Konfiguration in der AEM Web Console-Konfiguration angeben. Führen Sie folgende Schritte aus, um den Vorbefüllungs-Service zu konfigurieren:

>[!NOTE]
>
>Die Vorbefüllungs-Dienstkonfiguration ist auf adaptive Formulare, HTML5-Formulare und HTML5-Formularsätze anwendbar.

1. Öffnen Sie die **[!UICONTROL Adobe Experience Manager Web-Konsolenkonfiguration]** über die URL:\
   https://&lt;server>:&lt;port>/system/console/configMgr
1. Suchen und öffnen Sie die **[!UICONTROL standardmäßige Vorbefüllungs-Service-Konfiguration]**.

   ![Vobefüllungskonfiguration](assets/prefill_config_new.png)

1. Geben Sie den Datenspeicherort oder einen Regex (regulärer Ausdruck) für die **Datendateispeicherorte** ein. Beispiele für gültige Datendateispeicherorte:

   * file:///C:/Users/public/Document/Prefill/.&#42;
   * https://localhost:8000/somesamplexmlfile.xml

   >[!NOTE]
   >
   >Standardmäßig wird das Vorbefüllen durch CRX-Dateien für alle Typen adaptiver Formulare ermöglicht (XSD-, XDP-, JSON-, FDM-basierte und nicht formularmodellbasierte). Vorbefüllen ist nur mit JSON- und XML-Dateien zulässig.

1. Der Vorbefüllungs-Service ist jetzt für Ihr Formular konfiguriert.

   >[!NOTE]
   >
   >Das CRX-Protokoll verwaltet die Sicherheit der vorbefüllten Daten, daher ist es standardmäßig zulässig. Beim Vorbefüllen über andere Protokolle mit dem generischen Regex kann es zu Sicherheitslücken kommen. Geben Sie in der Konfiguration eine sichere URL-Konfiguration zum Schutz Ihrer Daten an.

## Die Besonderheit wiederholbarer Bereiche {#the-curious-case-of-repeatable-panels}

Im Allgemeinen werden gebundene (Formular-Schema) und ungebundene Felder oder Teilformulare in demselben adaptiven Formular erstellt. Im Folgenden werden allerdings einige Ausnahmen genannt, die gelten, falls die Gebundenen wiederholbar sind:

* Ungebundene wiederholbare Bereiche werden bei adaptiven Formularen mit der XFA-Formularvorlage, XSD, JSON-Schema oder dem FDM-Schema nicht unterstützt.
* Verwenden Sie keine ungebundenen Felder in gebundenen, wiederholbaren Bedienfeldern.

>[!NOTE]
>
>Generell sollten Sie keine gebundenen und ungebundenen Felder mischen, wenn sich diese in Daten überschneiden, die vom Benutzer in ungebundenen Feldern eingegeben werden. Wenn möglich, sollten Sie das XML-Schema oder die XFA-Formularvorlage ändern und einen Eintrag für ungebundene Felder hinzufügen, sodass diese auch gebunden werden und ihre Daten wie andere Felder in den übermittelten Daten verfügbar sind.

## Unterstützte Protokolle zum Vorbefüllen von Benutzerdaten {#supported-protocols-for-prefilling-user-data}

Adaptive Formulare können mit Benutzerdaten im Vorbefülldatenformat über die folgenden Protokolle vorbefüllt werden, wenn sie mit gültigem Regex konfiguriert sind:

### „crx://“-Protokoll  {#the-crx-protocol}

```http
https://localhost:4502/content/forms/af/xml.html?wcmmode=disabled&dataRef=crx:///tmp/fd/af/myassets/sample.xml
```

Der angegebene Knoten muss die Eigenschaft `jcr:data` aufweisen und die Daten enthalten.

### „file://“-Protokoll  {#the-file-protocol-nbsp}

```http
https://localhost:4502/content/forms/af/someAF.html?wcmmode=disabled&dataRef=file:///C:/Users/form-user/Downloads/somesamplexml.xml
```

Die referenzierte Datei muss sich auf demselben Server befinden.

### „https://“-Protokoll  {#the-http-protocol}

```http
https://localhost:4502/content/forms/af/xml.html?wcmmode=disabled&dataRef=https://localhost:8000/somesamplexmlfile.xml
```

### „service://“-Protokoll  {#the-service-protocol}

```http
https://localhost:4502/content/forms/af/abc.html?wcmmode=disabled&dataRef=service://[SERVICE_NAME]/[IDENTIFIER]
```

* SERVICE_NAME verweist auf den Namen des OSGI-Vorbefüllungs-Service. Lesen Sie [Erstellen und Ausführen eines Vorbefüllungs-Service](../../forms/using/prepopulate-adaptive-form-fields.md#create-and-run-a-prefill-service).
* IDENTIFIER bezieht sich auf alle Metadaten, die vom OSGI-Vorbefüllungs-Service erforderlich sind, um die Daten zum Vorbefüllen aufzurufen. Eine Kennung für die angemeldete Benutzerin bzw. den angemeldeten Benutzer ist ein Beispiel für Metadaten, die verwendet werden können.

>[!NOTE]
>
>Die Übergabe von Authentifizierungsparametern wird nicht unterstützt.

### Festlegen des Datenattributs in „slingRequest“ {#setting-data-attribute-in-slingrequest}

Sie können auch das `data`-Attribut in `slingRequest` festlegen, wo das `data`-Attribut eine Zeichenfolge mit XML oder JSON ist, wie in folgendem Beispiel-Code dargestellt (Beispiel ist für XML):

```javascript
<%
           String dataXML="<afData>" +
                            "<afUnboundData>" +
                                "<data>" +
                                    "<first_name>"+ "Tyler" + "</first_name>" +
                                    "<last_name>"+ "Durden " + "</last_name>" +
                                    "<gender>"+ "Male" + "</gender>" +
                                    "<location>"+ "Texas" + "</location>" +
                                    "</data>" +
                            "</afUnboundData>" +
                        "</afData>";
        slingRequest.setAttribute("data", dataXML);
%>
```

Sie können eine einfache XML- oder JSON-Zeichenfolge schreiben, die alle Ihre Daten enthält, und sie in slingRequest festlegen. Sie können dies einfach in der Renderer-JSP für jede Komponente durchführen, die Sie auf der Seite aufnehmen möchten, auf der Sie das „slingRequest“-Datenattribut festlegen können.

Beispiel: Sie wünschen ein spezifisches Design für Ihre Seite mit einem bestimmten Kopfzeilentyp. Um dies zu erreichen, können Sie eine eigene `header.jsp` schreiben, die Sie in Ihre Seitenkomponente aufnehmen, und das `data`-Attribut festlegen.

Ein weiteres gutes Beispiel ist ein Szenario, bei dem Sie Daten bei der Anmeldung über Social Madia-Konten wie Facebook, Twitter oder LinkedIn vorbefüllen möchten. In diesem Fall können Sie eine einfache JSP in `header.jsp` aufnehmen, die Daten aus dem Benutzerkonto abruft und den Datenparameter festlegt.

prefill-page component.zip

[Datei abrufen](assets/prefill-page-component.zip)
Beispieldatei „prefill.jsp“ in der Seitenkomponente

## Benutzerdefinierter AEM Forms-Vorbefüllungsdienst {#aem-forms-custom-prefill-service}

Sie können den benutzerdefinierten Vorbefüllungs-Service für die Szenarien verwenden, in denen Sie permanent Daten aus einer vordefinierten Quelle lesen. Der Vorbefüllungsdienst liest Daten aus definierten Datenquellen und befüllt die Felder des adaptiven Formulars mit dem Inhalt der Vorbefüllungsdatendatei vor. Außerdem können Sie dauerhaft vorgefüllte Daten mit einem adaptiven Formular verknüpfen.

### Erstellen und Ausführen eines Vorbefüllungs-Service {#create-and-run-a-prefill-service}

Der Vorbefüllungsdienst ist ein OSGi-Dienst und wird über das OSGi-Paket bereitgestellt. Sie erstellen das OSGi-Bundle, laden es hoch und installieren es in die AEM Forms-Pakete. Bevor Sie mit der Erstellung des Pakets beginnen:

* [Laden Sie das AEM Forms Client SDK herunter](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html)
* Laden Sie das Textbausteinpaket herunter

* Platzieren Sie die Datendatei (Vorbefüllungsdaten) in das CRX-Repository. Sie können die Datei an einem beliebigen Ort in den \contents des CRX-Repositorys platzieren.

[Datei laden](assets/prefill-sumbit-xmlsandcontentpackage.zip)

#### Erstellen eines Vorbefüllungs-Service {#create-a-prefill-service}

Das Textbausteinpaket (Vorbefüllungsdienst-Beispielpaket) enthält folgende Beispielimplementierung des AEM Forms-Vorbefüllungsdiensts. Öffnen Sie das Textbausteinpaket in einem Codeeditor. Öffnen Sie beispielsweise das Textbausteinprojekt zur Bearbeitung in Eclipse. Nachdem Sie das Textbausteinpaket in einem Code-Editor geöffnet haben, führen Sie folgende Schritte aus, um den Service zu erstellen.

1. Öffnen Sie die Datei „src\main\java\com\adobe\test\Prefill.java“ zur Bearbeitung.
1. Legen Sie im Code folgenden Wert fest:

   * `nodePath:` Die Knotenpfadvariable, die auf den CRX-Repository-Speicherort verweist, enthält den Pfad der Daten-(Vorbefüllungs)-Datei. Beispiel: /content/prefilldata.xml
   * `label:` Der Parameter „label“ gibt den Anzeigenamen des Service an. Beispiel: Standardvorbefüllungs-Service

1. Speichern und schließen Sie die Datei `Prefill.java`.
1. Fügen Sie das Paket `AEM Forms Client SDK` zum Erstellungspfad des Textbausteinprojektes hinzu.
1. Kompilieren Sie das Projekt und erstellen Sie die .jar-Datei für das Paket.

#### Starten und Verwenden des Vorbefüllungs-Service {#start-and-use-the-prefill-service}

Um den Vorbefüllungsdienst zu starten, laden Sie die JAR-Datei in die AEM Forms Web Console hoch und aktivieren Sie den Dienst. Jetzt wird der Dienst im Editor für adaptive Formulare angezeigt. Verknüpfen eines Vorbefüllungs-Dienstes mit einem adaptiven Formular:

1. Öffnen Sie das adaptive Formular im Editor für Formulare und öffnen Sie den Bereich „Eigenschaften“ für den Formular-Container.
1. In der Eigenschaftenkonsole gehen Sie zu „AEM Forms-Container“ > „Standard“ > „Vorbefüllungsdienst“.
1. Wählen Sie den Vorbefüllungsdienst und klicken Sie auf **[!UICONTROL Speichern]**. Dieser Service ist mit dem Formular verknüpft.

## Vorbefüllen von Daten auf dem Client {#prefill-at-client}

Wenn Sie ein adaptives Formular vorbefüllen lassen, führt der AEM Forms-Server Daten mit einem adaptiven Formular zusammen und stellt das ausgefüllte Formular für Sie bereit. Standardmäßig erfolgt die Datenzusammenführung auf dem Server.

Sie können den AEM Forms-Server so konfigurieren, dass die Datenzusammenführung auf dem Client statt auf dem Server durchgeführt wird. Dadurch wird der Zeitaufwand für das Vorbefüllen und Rendern von adaptiven Formularen erheblich verringert. Standardmäßig ist die Funktion deaktiviert. Sie können sie über den Configuration Manager oder die Befehlszeile aktivieren.

* Aktivieren oder Deaktivieren der Funktion über den Configuration Manager:
   1. Öffnen Sie AEM Configuration Manager.
   1. Suchen und Öffnen der Webkanalkonfiguration für adaptive Formulare und interaktive Kommunikation
   1. Aktivieren der Option „Configuration.af.clientside.datamerge.enabled.name“
* Aktivieren oder Deaktivieren der Funktion über die Befehlszeile:
   * Zum Aktivieren führen Sie folgenden cURL-Befehl aus:
     `curl -u admin:admin -X POST -d apply=true \ -d propertylist=af.clientside.datamerge.enabled \ -d af.clientside.datamerge.enabled=true \ http://${crx.host}:${crx.port}/system/console/configMgr/Adaptive%20Form%20and%20Interactive%20Communication%20Web%20Channel%20Configuration`

   * Zum Deaktivieren führen Sie folgenden cURL-Befehl aus:
     `curl -u admin:admin -X POST -d apply=true \ -d propertylist=af.clientside.datamerge.enabled \ -d af.clientside.datamerge.enabled=false \ http://${crx.host}:${crx.port}/system/console/configMgr/Adaptive%20Form%20and%20Interactive%20Communication%20Web%20Channel%20Configuration`

  Um die Option zum Vorbefüllen der Daten auf dem Client vollständig nutzen zu können, aktualisieren Sie den Vorbefüllungs-Service, um [FileAttachmentMap](https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/forms/common/service/PrefillData.html) und [CustomContext](https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/forms/common/service/PrefillData.html) zurückzugeben.
