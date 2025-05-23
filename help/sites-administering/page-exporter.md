---
title: Das Seiten-Export-Tool
description: Erfahren Sie, wie Sie das Seiten-Export-Tool von Adobe Experience Manager (AEM) verwenden.
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
exl-id: 997637d5-1627-4102-8b7c-a0cfd871a7b2
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 99%

---

# Das Seiten-Export-Tool{#the-page-exporter}

Adobe Experience Manager (AEM) bietet Ihnen die Möglichkeit, eine Seite als vollständige Web-Seite einschließlich aller Grafiken, `.js`- und `.css`-Dateien zu exportieren.

Nach der Konfiguration fordern Sie einen Seitenexport über Ihren Browser an, indem Sie in der URL `html` durch `export.zip` ersetzen. Dadurch wird eine Archivdatei (ZIP) generiert, die die gerenderte Seite im HTML-Format zusammen mit den referenzierten Assets enthält. Alle in der Seite enthaltenen Pfade (z. B. Pfade zu Grafiken) werden umgeschrieben und verweisen entweder auf die im Archiv enthaltenen Dateien oder auf die Ressourcen auf dem Server. Die Archivdatei (ZIP) kann dann von Ihrem Browser heruntergeladen werden.

>[!NOTE]
>
>Abhängig von Ihrem Browser und den Einstellungen erhalten Sie beim Download eine der folgenden Optionen:
>
>* eine Archivdatei (`<page-name>.export.zip`)
>* ein Ordner (`<page-name>`); die Archivdatei wurde effektiv bereits erweitert

## Exportieren einer Seite {#exporting-a-page}

Die folgenden Schritte beschreiben, wie Sie eine Seite exportieren können. Vorausgesetzt wird, dass für Ihre Website eine Vorlage für die Exportkonfiguration vorliegt: Eine Exportvorlage legt fest, wie eine Seite exportiert wird, und gilt speziell für Ihre Site. Informationen zum Erstellen einer Exportvorlage finden Sie unter [Erstellen einer Seiten-Export-Tool-Konfiguration für Ihre Site](#creating-a-page-exporter-configuration-for-your-site).

So exportieren Sie eine Seite:

1. Gehen Sie zur gewünschten Seite in der **Sites**-Konsole.

1. Wählen Sie die Seite aus und öffnen Sie dann das Dialogfeld **Eigenschaften**.

1. Wählen Sie die Registerkarte **Erweitert**.

1. Erweitern Sie das Feld **Export**, um eine Exportvorlage auszuwählen.
Wählen Sie die erforderliche Vorlage für Ihre Website aus und bestätigen Sie dann mit **OK**.

1. Klicken Sie auf **Speichern und schließen**, um das Dialogfeld „Seiteneigenschaften“ zu schließen.

1. Fragen Sie die Seite für den Export an und ersetzen Sie dabei in der URL das Suffix `html` durch `export.zip`.

   Beispiel:
   * localhost:4502/content/we-retail/language-masters/de.html

   Zugriff über:
   * localhost:4502/content/we-retail/language-masters/de.export.zip

1. Laden Sie die Archivdatei auf Ihr Dateisystem herunter.

1. Entpacken Sie ggfs. die Datei in Ihrem Dateisystem. Nach dem Erweitern wird ein Ordner mit demselben Namen wie die ausgewählte Seite angezeigt. Dieser Ordner enthält:

   * den Unterordner `content`, der das Stammverzeichnis einer Reihe von Unterordnern ist, die den Pfad zur Seite im Repository widerspiegeln

      * innerhalb dieser Struktur befindet sich die HTML-Datei für die ausgewählte Seite (`<page-name>.html`)

   * die anderen Ressourcen (`.js`- und `.css`-Dateien, Grafiken usw.) befinden sich in den in der Exportvorlage festgelegten Verzeichnissen

1. Öffnen Sie die HTML-Datei der Seite (`<unzip-dir>/<path>/<to>/<page>/<page-path>.html`) im Browser, um das Rendering zu überprüfen.

## Erstellen einer Seiten-Export-Tool-Konfiguration für Ihre Website {#creating-a-page-exporter-configuration-for-your-site}

Das Seiten-Export-Tool basiert auf dem [Inhaltssynchronisierungs-Framework](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/contentsync/package-summary.html). Die Konfigurationen, die im Dialogfeld **Seiteneigenschaften** verfügbar sind, sind Exportvorlagen, die die erforderlichen Abhängigkeiten für eine Seite definieren.

Wenn ein Seitenexport ausgelöst wird, wird auf die Exportvorlage verwiesen. Der Seitenpfad und der Designpfad werden dynamisch angewendet. Anschließend wird die ZIP-Datei erstellt, indem die Standardfunktion zur Inhaltssynchronisierung genutzt wird.

Eine vorkonfigurierte AEM-Installation enthält unter `/etc/contentsync/templates/default` eine Standardvorlage.

* Diese Vorlage dient als Fallback-Vorlage, wenn keine Exportvorlage im Repository gefunden wird.

* Die `default`-Vorlage zeigt Ihnen, wie ein Seitenexport konfiguriert werden kann, sodass er als Grundlage für eine neue Exportvorlage dienen kann.

* Um die Knotenstruktur der Vorlage in Ihrem Browser im JSON-Format anzuzeigen, fragen Sie die folgenden URL an:
  `http://localhost:4502/etc/contentsync/templates/default.json`

Die einfachste Methode zum Erstellen einer Seiten-Export-Tool-Vorlage besteht darin, Folgendes zu tun:

* kopieren Sie die `default`-Vorlage,

* Weisen Sie einen neuen Namen zu, der Ihrer Website entspricht,

* Nehmen Sie dann die erforderlichen Änderungen vor.

So erstellen Sie eine völlig neue Vorlage:

1. Erstellen Sie in **CRXDE Lite** einen Knoten unter `/etc/contentsync/templates`:

   * `Name`: ein Name, der Ihrer Website entspricht; Beispiel: `<mysite>`. Dieser Name wird im Dialogfeld „Seiteneigenschaften“ angezeigt, wenn Sie die Seiten-Export-Toolvorlage auswählen.

   * `Type`: `nt:unstructured`

2. Erstellen Sie unter dem Vorlagenknoten (in diesem Beispiel: `mysite`) eine Knotenstruktur mit den unten beschriebenen Konfigurationsknoten.

## Aktivieren einer Seiten-Export-Tool-Vorlage für Ihre Seiten {#activating-a-page-exporter-configuration-for-your-pages}

Wenn Ihre Vorlage konfiguriert ist, stellen Sie sie zur Verfügung:

1. Gehen Sie in CRXDE zur gewünschten Seite in der `/content`-Verzweigung. Dies kann eine einzelne Seite oder die Stammseite einer Unterstruktur sein.

1. Erstellen Sie im `jcr:content`-Knoten der Seite die Eigenschaft:
   * `Name`: `cq:exportTemplate`
   * `Type`: `String`
   * `Value`: Pfad zur Vorlage; Beispiel: `/etc/contentsync/templates/mysite`

### Konfigurationsknoten für das Seiten-Export-Tool {#page-exporter-configuration-nodes}

Die Vorlage besteht aus einer Knotenstruktur, da sie das [Content Sync-Framework](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/contentsync/package-summary.html) verwendet. Jeder Knoten verfügt über die Eigenschaft `type`, die eine spezifische Aktion beim Erstellungsprozess der ZIP-Datei definiert.

<!-- For more details about the type property, see the Overview of configuration types section in the Content Sync framework page.
-->

Mit den folgenden Knoten können Sie eine Export-Vorlage erstellen:

* `page`
Mit dem Knoten page wird die HTML-Seite in die ZIP-Datei kopiert. Er weist die folgenden Eigenschaften auf:

   * Ein obligatorischer Knoten.
   * Befindet sich unter `/etc/contentsync/templates/<mysite>`.
   * Er wird mit der `Name`-Eigenschaft definiert, die auf `page` gesetzt wird.
   * Knotentyp ist `nt:unstructured`

  Der Knoten `page` hat folgende Eigenschaften:

   * Die Eigenschaft `type` mit dem Wert `pages`.

   * Er verfügt nicht über die Eigenschaft `path`, da der aktuelle Seitenpfad dynamisch in die Konfiguration kopiert wird.
  <!--
  * The other properties are described in the Overview of configuration types section of the Content Sync framework.
  -->

* `rewrite`
Der Knoten rewrite definiert, wie die Links in der exportierten Seite neu geschrieben werden. Die neu geschriebenen Links können entweder auf die Dateien in der ZIP-Datei oder auf die Ressourcen auf dem Server verweisen.
  <!-- See the Content Sync page for a complete description of the `rewrite` node. -->

* `design`
Mit dem Knoten design wird das für die exportierte Seite genutzte Design kopiert. Er weist die folgenden Eigenschaften auf:

   * Optional.
   * Befindet sich unter `/etc/contentsync/templates/<mysite>`.
   * Er wird mit der `Name`-Eigenschaft definiert, die auf `design` gesetzt wird.
   * Knotentyp ist `nt:unstructured`.

  Der Knoten `design` hat folgende Eigenschaften:

   * Die Eigenschaft `type` mit dem Wert `copy`.

   * Er verfügt nicht über die Eigenschaft `path`, da der aktuelle Seitenpfad dynamisch in die Konfiguration kopiert wird.

* `generic`
Mit einem generischen Knoten werden Ressourcen wie die `.js`- oder `.css`-Dateien der Client-Bibliotheken in die ZIP-Datei kopiert. Er weist die folgenden Eigenschaften auf:

   * Optional.
   * Befindet sich unter `/etc/contentsync/templates/<mysite>`.
   * Kein spezifischer Name.
   * Knotentyp ist `nt:unstructured`.
   * Er hat eine `type`-Eigenschaft und mit `type` verwandte Eigenschaften. <!--Has a `type` property and any `type` related properties as defined in the Overview of configuration types section of the Content Sync framework.-->

  Beispielsweise kopiert der folgende Konfigurationsknoten die Dateien `mysite.clientlibs.js` in die ZIP-Datei:

  ```xml
  "mysite.clientlibs.js": {
      "extension": "js",
      "type": "clientlib",
      "path": "/etc/designs/mysite/clientlibs",
      "jcr:primaryType": "nt:unstructured"
  }
  ```

**Implementieren einer benutzerdefinierten Konfiguration**

Benutzerdefinierte Konfigurationen sind ebenfalls möglich.

<!--
As you may have noticed in the node structure, the **Geometrixx** page export template has a `logo` node with a `type` property set to `image`. This is a special configuration type that has been created to copy the image logo to the zip file. 
-->

Um bestimmte Anforderungen zu erfüllen, implementieren Sie einen [benutzerdefinierten Update-Handler](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/contentsync/handler/package-summary.html).

<!-- To meet some specific requirements, you may need to implement a custom `type` property. To do so, see the Implementing a custom update handler section in the Content Sync page.
-->

## Programmatisches Exportieren einer Seite {#programmatically-exporting-a-page}

Um eine Seite programmatisch zu exportieren, können Sie den OSGi-Dienst [PageExporter](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) nutzen. Mit diesem Dienst können Sie:

* eine Seite exportieren und in die HTTP-Servlet-Antwort schreiben
* eine Seite exportieren und die ZIP-Datei an einem bestimmten Ort speichern

Das Servlet, das an den Selektor `export` und die Erweiterung `zip` gebunden ist, nutzt den PageExporter-Service.

## Fehlerbehebung {#troubleshooting}

Wenn beim Herunterladen der ZIP-Datei ein Fehler auftritt, können Sie den Knoten `/var/contentsync` im Repository löschen und die Exportanfrage erneut senden.
