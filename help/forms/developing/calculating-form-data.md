---
title: Berechnen von Formulardaten
description: Verwenden Sie den Forms-Service, um die Werte zu berechnen, die ein Benutzer in ein Formular eingibt, und die Ergebnisse anzuzeigen. Der Forms-Service berechnet die Werte mithilfe der Java-API und der Webservice-API.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromtoc: true
exl-id: 071a6ccb-8204-4cbc-a39b-143da52c16f7
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '1858'
ht-degree: 100%

---

# Berechnen von Formulardaten {#calculating-form-data}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Der Forms-Service kann die Werte berechnen, die ein Benutzer in ein Formular eingibt, und die Ergebnisse anzeigen. Zur Berechnung von Formulardaten müssen Sie zwei Aufgaben ausführen. Erstellen Sie zunächst ein Formularentwurfsskript, das Formulardaten berechnet. Ein Formularentwurf unterstützt drei Arten von Skripten. Ein Skripttyp wird auf dem Client ausgeführt, ein anderer auf dem Server und der dritte sowohl auf dem Server als auch auf dem Client. Der in diesem Thema beschriebene Skripttyp wird auf dem Server ausgeführt. Server-seitige Berechnungen werden für HTML-, PDF- und Formularhandbuchtransformationen (veraltet) unterstützt.

Im Rahmen des Formularentwurfsprozesses können Sie Berechnungen und Skripte verwenden, um ein besseres Benutzererlebnis zu bieten. Berechnungen und Skripte können zu den meisten Formularfeldern und -objekten hinzugefügt werden. Erstellen Sie ein Formularentwurfsskript, um Berechnungsvorgänge für Daten durchführen zu können, die Benutzende in ein interaktives Formular eingeben.

Der Benutzer gibt Werte in das Formular ein und klickt auf die Schaltfläche „Berechnen“, um die Ergebnisse anzuzeigen. Im folgenden Prozess wird ein Beispiel-Programm beschrieben, mit dem ein Benutzer Daten berechnen kann:

* Benutzende greifen auf eine HTML-Seite mit dem Namen „StartLoan.html“ zu, die als Startseite der Web-Anwendung fungiert. Diese Seite ruft ein Java-Servlet mit dem Namen `GetLoanForm` auf.
* Die `GetLoanForm`-Servlet rendert ein Darlehensformular. Dieses Formular enthält ein Skript, interaktive Felder, eine Berechnungsschaltfläche und eine Senden-Schaltfläche.
* Benutzende geben Werte in die Felder des Formulars ein und klicken auf die Schaltfläche „Berechnen“. Das Formular wird an das Java-Servlet `CalculateData` gesendet, wo das Skript ausgeführt wird. Das Formular wird mit den im Formular angezeigten Berechnungsergebnissen an den Benutzer zurückgesendet.
* Der Benutzer gibt weitere Werte ein und lässt sie berechnen, bis ein zufriedenstellendes Ergebnis angezeigt wird. Wenn der Benutzer zufrieden ist, klickt er auf die Senden-Schaltfläche, damit das Formular verarbeitet wird. Das Formular wird an ein anderes Java-Servlet mit dem Namen `ProcessForm` gesendet, das für das Abrufen der gesendeten Daten verantwortlich ist. (Siehe [Umgang mit übermittelten Formularen](/help/forms/developing/rendering-forms.md#handling-submitted-forms).)


Das folgende Diagramm zeigt den logischen Fluss der Anwendung.

![cf_cf_finsrv_loancalcapp_v1](assets/cf_cf_finsrv_loancalcapp_v1.png)

Die folgende Tabelle beschreibt die Schritte in diesem Diagramm.

<table>
 <thead>
  <tr>
   <th><p>Schritt</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>1</p></td>
   <td><p>Das Java-Servlet <code>GetLoanForm</code> wird von der HTML-Startseite aus aufgerufen. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>Das Java-Servlet <code>GetLoanForm</code> verwendet die Client-API des Forms-Services, um das Darlehensformular an den Client-Webbrowser zu rendern. Der Unterschied zwischen der Wiedergabe eines Formulars, das ein für die Ausführung auf dem Server konfiguriertes Skript enthält, und der Wiedergabe eines Formulars, das kein Skript enthält, besteht darin, dass Sie den Zielspeicherort angeben müssen, der zum Ausführen des Skripts verwendet wird. Wenn kein Zielspeicherort angegeben ist, wird ein Skript, das für die Ausführung auf dem Server konfiguriert ist, nicht ausgeführt. Betrachten Sie beispielsweise das in diesem Abschnitt eingeführte Programm. Das Java-Servlet <code>CalculateData</code> ist der Zielspeicherort, an dem das Skript ausgeführt wird.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Der Benutzer gibt Daten in interaktive Felder ein und klickt auf die Schaltfläche „Berechnen“. Das Formular wird an das Java-Servlet <code>CalculateData</code> gesendet, wo das Skript ausgeführt wird. </p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Das Formular wird im Webbrowser wiedergegeben, wobei die Berechnungsergebnisse im Formular angezeigt werden. </p></td>
  </tr>
  <tr>
   <td><p>5</p></td>
   <td><p>Der Benutzer klickt auf die Senden-Schaltfläche, wenn die Werte zufriedenstellend sind. Das Formular wird an ein anderes Java-Servlet mit dem Namen <code>ProcessForm</code> gesendet.</p></td>
  </tr>
 </tbody>
</table>

Normalerweise enthält ein Formular, das als PDF-Inhalt gesendet wird, Skripte, die auf dem Client ausgeführt werden. Es können aber auch Server-seitige Berechnungen durchgeführt werden. Eine Senden-Schaltfläche kann nicht zur Berechnung von Skripten verwendet werden. In diesem Fall werden keine Berechnungen ausgeführt, da der Forms-Service die Interaktion für abgeschlossen hält.

Um die Verwendung eines Formularentwurfsskripts zu veranschaulichen, wird in diesem Abschnitt ein einfaches interaktives Formular untersucht, das ein Skript enthält, das für die Ausführung auf dem Server konfiguriert ist. Das folgende Diagramm zeigt einen Formularentwurf mit einem Skript, das Werte hinzufügt, die ein Benutzer in die ersten beiden Felder eingibt, und das Ergebnis im dritten Feld anzeigt.

![cf_cf_caldata](assets/cf_cf_caldata.png)

**A.** Ein Feld namens NumericField1 **B.** Ein Feld namens NumericField2 **C.** Ein Feld namens NumericField3

Die Syntax des Skripts in diesem Formularentwurf lautet wie folgt:

```javascript
     NumericField3 = NumericField2 + NumericField1
```

In diesem Formularentwurf ist die Schaltfläche „Berechnen“ eine Befehlsschaltfläche, und das Skript befindet sich im Ereignis `Click` dieser Schaltfläche. Wenn ein Benutzer Werte in die ersten beiden Felder (NumericField1 und NumericField2) eingibt und auf die Schaltfläche „Berechnen“ klickt, wird das Formular an den Forms-Service gesendet, wo das Skript ausgeführt wird. Der Forms-Service rendert das Formular zurück auf den Client-Computer und zeigt die Ergebnisse der Berechnung im Feld NumericField3 an.

>[!NOTE]
>
>Informationen zum Erstellen eines Formularentwurfsskripts finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_de).

>[!NOTE]
>
>Weitere Informationen über den Forms-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um Formulardaten zu berechnen, führen Sie die folgenden Aufgaben aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms-Client-API-Objekt.
1. Rufen Sie ein Formular ab, das ein Berechnungsskript enthält.
1. Schreiben Sie den Formulardaten-Stream zurück in den Client-Webbrowser

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms-Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Service programmgesteuert durchführen können, müssen Sie einen Client für den Forms-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `FormsServiceClient`-Objekt. Wenn Sie die Forms-Webservice-API verwenden, erstellen Sie ein `FormsServiceService`-Objekt.

**Abrufen eines Formulars, das ein Berechnungsskript enthält**

Sie verwenden die Client-API des Forms-Services, um eine Anwendungslogik zu erstellen, die ein Formular verarbeitet, welches ein Skript enthält, das für die Ausführung auf dem Server konfiguriert ist. Der Prozess ähnelt der Verarbeitung eines gesendeten Formulars. (Siehe [Umgang mit übermittelten Formularen](/help/forms/developing/handling-submitted-forms.md).)

Überprüfen Sie, ob der mit dem gesendeten Formular verknüpfte Verarbeitungsstatus `1` `(Calculate)` ist, was bedeutet, dass der Forms-Service einen Berechnungsvorgang für die Formulardaten durchführt und die Ergebnisse für den Benutzer zurückgeschrieben werden müssen. In diesem Fall wird automatisch ein Skript ausgeführt, das für die Ausführung auf dem Server konfiguriert wurde.

**Zurückschreiben des Formulardaten-Streams in den Client-Webbrowser**

Nachdem Sie überprüft haben, dass der mit einem gesendeten Formular verknüpfte Verarbeitungsstatus `1` ist, müssen Sie die Ergebnisse zurück in den Client-Webbrowser schreiben. Wenn das Formular angezeigt wird, erscheint der berechnete Wert in den entsprechenden Feldern.

**Siehe auch**

[Einbeziehen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
[Berechnen von Formulardaten mit der Java-API](/help/forms/developing/calculating-form-data.md#calculate-form-data-using-the-java-api)
[Berechnen von Formulardaten mit der Webservice-API](/help/forms/developing/calculating-form-data.md#calculate-form-data-using-the-web-service-api)
[Festlegen von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
[Kurzanleitungen zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)
[Rendern interaktiver PDF-Formulare](/help/forms/developing/rendering-interactive-pdf-forms.md)
[Erstellen von Web-Anwendungen, die PDF-Formulare rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

## Berechnen von Formulardaten mithilfe der Java-API {#calculate-form-data-using-the-java-api}

So berechnen Sie die Formulardaten mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-forms-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen eines Formulars, das ein Berechnungsskript enthält

   * Um Formulardaten abzurufen, die ein Berechnungsskript enthalten, erstellen Sie ein Objekt vom Typ `com.adobe.idp.Document`, indem Sie dessen Konstruktor verwenden und die Methode `getInputStream` des `javax.servlet.http.HttpServletResponse`-Objekts über den Konstruktor aufrufen.
   * Rufen Sie die Methode `processFormSubmission` des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

      * Das `com.adobe.idp.Document`-Objekt, das die Formulardaten enthält.
      * Ein Zeichenfolgenwert, der Umgebungsvariablen einschließlich aller relevanten HTTP-Kopfzeilen angibt. Geben Sie den zu verarbeitenden Content-Typ an, indem Sie einen oder mehrere Werte für die Umgebungsvariable `CONTENT_TYPE` angeben. Um beispielsweise XML- und PDF-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=application/xml&CONTENT_TYPE=application/pdf`
      * Ein Zeichenfolgenwert, der den Wert der `HTTP_USER_AGENT`-Kopfzeile angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen speichert.

     Die `processFormSubmission`-Methode gibt ein `FormsResult`-Objekt aus, das die Ergebnisse der Formularübermittlung enthält.

   * Überprüfen Sie, ob der Verarbeitungsstatus eines übermittelten Formulars `1` ist, indem Sie die Methode `getAction` des `FormsResult`-Objekts aufrufen. Wenn diese Methode den Wert `1` zurückgibt, wurde die Berechnung durchgeführt und die Daten können in den Client-Webbrowser zurückgeschrieben werden.

1. Schreiben Sie den Formulardaten-Stream zurück in den Client-Webbrowser

   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Senden eines Formulardaten-Streams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie ein Objekt vom Typ `com.adobe.idp.Document`, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen.
   * Erstellen Sie ein Objekt vom Typ `java.io.InputStream`, indem Sie die Methode `getInputStream` des `com.adobe.idp.Document`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstrom, indem Sie die Methode `read` des `InputStream`-Objekts aufrufen und das Byte-Array als Argument übergeben.
   * Rufen Sie die Methode `write` des `javax.servlet.ServletOutputStream`-Objekts auf, um den Formulardatenstrom an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die Methode `write`.

**Siehe auch**


[Einbeziehen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
[Festlegen von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Berechnen von Formulardaten mithilfe der Webservice-API {#calculate-form-data-using-the-web-service-api}

So berechnen Sie Formulardaten mithilfe der Forms API (Webservice):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxy-Klassen, welche die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Abrufen eines Formulars, das ein Berechnungsskript enthält

   * Um Formulardaten abzurufen, die an ein Java-Servlet gesendet wurden, erstellen Sie ein `BLOB`-Objekt, indem Sie seinen Konstruktor verwenden.
   * Erstellen Sie ein Objekt vom Typ `java.io.InputStream` mithilfe der Methode `getInputStream` des `javax.servlet.http.HttpServletResponse`-Objekts.
   * Erstellen Sie ein `java.io.ByteArrayOutputStream`-Objekt, indem Sie seinen Konstruktor verwenden und die Länge des `java.io.InputStream`-Objekts übergeben.
   * Kopieren Sie den Inhalt des `java.io.InputStream`-Objekts in das `java.io.ByteArrayOutputStream`-Objekt.
   * Erstellen Sie ein Byte-Array, indem Sie die Methode `toByteArray` des `java.io.ByteArrayOutputStream`-Objekts aufrufen.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `setBinaryData`-Methode aufrufen und das Byte-Array als Argument übergeben.
   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden. Legen Sie den Gebietsschemawert fest, indem Sie die Methode `setLocale` des `RenderOptionsSpec`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt.
   * Rufen Sie die Methode `processFormSubmission` des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

      * Das `BLOB`-Objekt, das die Formulardaten enthält.
      * Ein Zeichenfolgenwert, der Umgebungsvariablen angibt, die alle relevanten HTTP-Kopfzeilen enthalten. Sie können beispielsweise den folgenden Zeichenfolgenwert angeben: `HTTP_REFERER=referrer&HTTP_CONNECTION=keep-alive&CONTENT_TYPE=application/xml`
      * Ein Zeichenfolgenwert, der den Wert der `HTTP_USER_AGENT`-Kopfzeile angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen speichert. Für weitere Informationen, .
      * Ein leeres `BLOBHolder`-Objekt, das von der Methode aufgefüllt wird.
      * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `BLOBHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `BLOBHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `javax.xml.rpc.holders.ShortHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `MyArrayOf_xsd_anyTypeHolder`-Objekt, das von der Methode gefüllt wird. Dieser Parameter wird zum Speichern von Dateianhängen verwendet, die zusammen mit dem Formular gesendet werden.
      * Ein leeres `FormsResultHolder`-Objekt, das von der Methode mit dem gesendeten Formular gefüllt wird.

     Die Methode `processFormSubmission` füllt den Parameter `FormsResultHolder` mit den Ergebnissen der Formularübermittlung. Die Methode `processFormSubmission` gibt ein `FormsResult`-Objekt zurück, das die Ergebnisse der Formularübermittlung enthält.

   * Überprüfen Sie, ob der Verarbeitungsstatus eines übermittelten Formulars `1` ist, indem Sie die Methode `getAction` des `FormsResult`-Objekts aufrufen. Wenn diese Methode den Wert `1` zurückgibt, wurde die Berechnung durchgeführt und die Daten können in den Client-Webbrowser zurückgeschrieben werden.

1. Schreiben Sie den Formulardaten-Stream zurück in den Client-Webbrowser

   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Senden eines Formulardaten-Streams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie ein Objekt vom Typ `BLOB`, das Formulardaten enthält, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es auf, indem Sie die Methode `getBinaryData` des `BLOB`-Objekts aufrufen. Mit dieser Aufgabe wird dem Byte-Array der Inhalt des `FormsResult`-Objekts zugewiesen.
   * Rufen Sie die Methode `write` des `javax.servlet.http.HttpServletResponse`-Objekts auf, um den Formulardatenstrom an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die Methode `write`.

**Siehe auch**
[Aufrufen von AEM Forms mithilfe von Base64-Codierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
