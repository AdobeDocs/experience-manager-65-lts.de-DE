---
title: Zusammenstellen von verschlüsselten PDF-Dokumenten
description: Stellen Sie mithilfe der Java-API und der Webservice-API verschlüsselte PDF-Dokumente zusammen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
hide: true
hidefromtoc: true
exl-id: d9884c3e-47d2-400a-98c3-13cc37be6786
source-git-commit: 103250f3442cf7c2793c51a95b1bf4fbaff71463
workflow-type: tm+mt
source-wordcount: '1676'
ht-degree: 100%

---

# Zusammenstellen von verschlüsselten PDF-Dokumenten {#assembling-encrypted-pdf-documents}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Sie können ein PDF-Dokument mit einem Kennwort verschlüsseln, indem Sie den Assembler-Dienst verwenden. Nachdem ein PDF-Dokument mit einem Kennwort verschlüsselt wurde, müssen Sie das Kennwort angeben, damit das PDF-Dokument in Adobe Reader oder Acrobat angezeigt werden kann. Zum Verschlüsseln eines PDF-Dokuments mit einem Kennwort muss das DDX-Dokument Verschlüsselungselementwerte enthalten, die für die Verschlüsselung eines PDF-Dokuments erforderlich sind.

Nehmen Sie für dieses Thema bitte an, dass das folgende DDX-Dokument verwendet wird.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
        <PDF result="EncryptLoan.pdf" encryption="userProtect">
         <PDF source="inDoc" />
     </PDF>
     <PasswordEncryptionProfile name="userProtect" compatibilityLevel="Acrobat7">
         <OpenPassword>AdobeOpen</OpenPassword>
        </PasswordEncryptionProfile>
 </DDX>
```

Beachten Sie, dass in diesem DDX-Dokument dem Quellattribut der Wert `inDoc` zugewiesen ist. In Fällen, in denen nur ein Eingabedokument an den Assembler-Dienst übergeben und ein PDF-Dokument zurückgegeben wird, und Sie den `invokeOneDocument`-Vorgang aufrugen, weisen Sie dem PDF-Quellattribut den Wert `inDoc` zu. Beim Aufrufen des `invokeOneDocument`-Vorgangs, ist der `inDoc`-Wert ein vordefinierter Schlüssel, der im DDX-Dokument angegeben werden muss.

Wenn Sie dagegen zwei oder mehr PDF-Eingabedokumente an den Assembler-Dienst übergeben, können Sie den `invokeDDX`-Vorgang aufrufen. Weisen Sie in diesem Fall den Dateinamen des PDF-Eingabedokuments dem `source`-Attribut zu.

Der Verschlüsselungs-Service muss nicht Teil Ihrer AEM Forms-Installation sein, um ein PDF-Dokument mit einem Kennwort verschlüsseln zu können. Siehe [Verschlüsseln und Entschlüsseln von PDF-Dokumenten](/help/forms/developing/encrypting-decrypting-pdf-documents.md).

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie in der [Referenz für Assembler-Dienst und DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein verschlüsseltes PDF-Dokument zusammenzustellen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie ein unsicheres PDF-Dokument.
1. Legen Sie Laufzeitoptionen fest.
1. Verschlüsseln Sie das Dokument.
1. Speichern Sie das verschlüsselte PDF-Dokument.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien adobe-utilities.jar- und jbossall-client.jar-Dateien durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Assembler-Clients**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Betrachten Sie beispielsweise das DDX-Dokument, das in diesem Abschnitt eingeführt wurde. Um ein PDF-Dokument zu verschlüsseln, muss das DDX-Dokument das Element `PasswordEncryptionProfile` enthalten.

**Referenzieren eines ungesicherten PDF-Dokuments**

Ein ungesichertes PDF-Dokument muss referenziert und an den Assembler-Dienst übergeben werden, um es zu verschlüsseln. Wenn Sie auf ein bereits verschlüsseltes PDF-Dokument verweisen, wird eine Ausnahme ausgelöst.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt. Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie in der `AssemblerOptionSpec`-Klassenreferenz in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Verschlüsseln des Dokuments**

Nachdem Sie den Assembler-Dienst-Client erstellt haben, das DDX-Dokument referenziert haben, das Verschlüsselungsinformationen enthält, ein ungesichertes PDF-Dokument referenziert haben und Laufzeitoptionen festgelegt haben, können Sie den Vorgang `invokeOneDocument` aufrufen. Da nur ein Eingabedokument an den Assembler-Dienst übergeben wird (und ein PDF zurückgegeben wird), können Sie den Vorgang `invokeOneDocument` anstelle des Vorgangs `invokeDDX` verwenden.

**Speichern des verschlüsselten PDF-Dokuments**

Wenn nur ein einzelnes PDF-Dokument an den Assembler-Dienst übergeben wird, gibt der Assembler-Dienst ein einzelnes Dokument anstelle eines Sammlungsobjekts zurück. Das heißt, beim Aufrufen des Vorgangs `invokeOneDocument` wird ein einzelnes Dokument zurückgegeben. Da das in diesem Abschnitt referenzierte DDX-Dokument Verschlüsselungsinformationen enthält, gibt der Assembler-Dienst ein PDF-Dokument zurück, das mit einem Kennwort verschlüsselt ist.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmatisches Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenstellen eines verschlüsselten PDF-Dokuments mithilfe der Java-API {#assemble-an-encrypted-pdf-document-using-the-java-api}

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-assembler-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie ein unsicheres PDF-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort eines ungesicherten PDF-Dokuments übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält. Dieses `com.adobe.idp.Document`-Objekt wird der `invokeOneDocument`-Methode übergeben.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags im Falle eines Fehlers fortzusetzen, rufen Sie die Methode `setFailOnError` des Objekts `AssemblerOptionSpec` auf und geben Sie `false` weiter.

1. Verschlüsseln Sie das Dokument.

   Rufen Sie die Methode `invokeOneDocument` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das DDX-Dokument darstellt. Stellen Sie sicher, dass dieses DDX-Dokument den Wert `inDoc` für das PDF-Quellelement enthält.
   * Ein `com.adobe.idp.Document`-Objekt, das das ungesicherte PDF-Dokument enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt, einschließlich der standardmäßigen Schriftart und Auftragslog-Ebene.

   Die `invokeOneDocument`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf lautet.
   * Rufen Sie die Methode `copyToFile` des `Document`-Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das die Methode `invokeOneDocument` zurückgegeben hat.

**Siehe auch**

[Schnellstart (SOAP-Modus): Zusammenstellen eines verschlüsselten PDF-Dokuments mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-an-encrypted-pdf-document-using-the-java-api)

## Zusammenstellen eines verschlüsselten PDF-Dokuments mithilfe der Webservice-API {#assemble-an-encrypted-pdf-document-using-the-web-service-api}

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Service-Referenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen standardmäßigen Konstruktor verwenden.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address`-Objekt, indem Sie den `System.ServiceModel.EndpointAddress`-Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert mit der WSDL an den AEM Forms-Service (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie brauchen das Attribut `lc_version` nicht zu verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `AssemblerServiceClient.Endpoint.Binding`-Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` dem Feld `BasicHttpBindingSecurity.Security.Mode` zu.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein Objekt `System.IO.FileStream`, indem Sie den Konstruktor aufrufen und einen String-Wert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus, in dem die Datei geöffnet werden soll, repräsentiert.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekts gespeichert wird. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem Feld `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Referenzieren Sie ein unsicheres PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Dieses `BLOB`-Objekt wird an `invokeOneDocument` als Argument übergeben.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Eingabedokuments und den Modus zum Öffnen der Datei angibt.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekts gespeichert wird. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem Feld `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags im Falle eines Fehlers fortzusetzen, weisen Sie `false` dem Datenelement `failOnError` des Objekts `AssemblerOptionSpec` zu.

1. Verschlüsseln Sie das Dokument.

   Rufen Sie die Methode `invokeOneDocument` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * A `BLOB`-Objekt, das das DDX-Dokument darstellt
   * Ein `BLOB`-Objekt, das das ungesicherte PDF-Dokument darstellt
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die Methode `invokeOneDocument` gibt ein `BLOB`-Objekt zurück, das ein verschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das die Methode `invokeOneDocument` zurückgegeben hat. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `MTOM` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein Objekt vom Typ `System.IO.BinaryWriter`, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
