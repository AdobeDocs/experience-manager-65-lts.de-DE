---
title: Verwenden von xtypes (klassische Benutzeroberfläche)
description: Erfahren Sie mehr über alle xtypes, die mit Adobe Experience Manager verfügbar sind.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 4a78de53-33bf-4999-ba3c-7d0bc33196a4
source-git-commit: 24bd1f57da3f9ce613ee28276d1ae9465b6dfba6
workflow-type: tm+mt
source-wordcount: '3668'
ht-degree: 59%

---

# Verwenden von xtypes (klassische Benutzeroberfläche){#using-xtypes-classic-ui}

Auf dieser Seite werden alle xtypes beschrieben, die in Adobe Experience Manager (AEM) verfügbar sind.

In der ExtJS-Sprache ist ein xtype ein symbolischer Name, der einer Klasse zugewiesen wird. Eine ausführliche Erläuterung der Funktionsweise und Einsatzmöglichkeiten von xtypes finden Sie im Abschnitt zu „Komponenten-xtypes“ unter [Übersicht zu ExtJS 2](https://docs.sencha.com/).

Weitere Informationen zu allen in AEM verfügbaren Widgets finden Sie in der [Widget-API-Dokumentation](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

Um herauszufinden, in welchen Komponenten ein bestimmter xtype in AEM verwendet wird, können Sie die folgende `Xpath` in CRXDE verwenden. Ersetzen Sie einfach „checkbox“ durch den xtype, an dem Sie interessiert sind:

`//element(*, cq:Widget)[@xtype='checkbox']`

>[!NOTE]
>
>Diese Seite beschreibt die Verwendung von ExtJS-xtypes in der klassischen Benutzeroberfläche.
>
>Adobe empfiehlt die Verwendung der standardmäßigen, modernen [Touch-optimierten Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md), die auf der [Coral](/help/sites-developing/touch-ui-concepts.md#coral-ui)- und [Granite-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components) basiert.

## xtypes {#xtypes}

Im Folgenden sind die verfügbaren xtypes in Adobe Experience Manager aufgeführt:

* `annotation`

  [CQ.wcm.Annotation](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Das `Annotation` ist ein spezielles Fenster. Es hat ein Formular im Hauptteil und eine Schaltflächengruppe in der Fußzeile. Es wird in der Regel zum Bearbeiten von Inhalten verwendet, kann aber auch nur zur Anzeige von Informationen genutzt werden.

* `arraystore`

  [CQ.Ext.data.ArrayStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Zuvor als &quot;`SimpleStore`&quot; bezeichnet.

  Eine kleine Hilfsklasse, um das Erstellen von [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) aus Array-Daten zu vereinfachen. Eine `ArrayStore` wird automatisch mit einem [CQ.Ext.data.ArrayReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) konfiguriert.

* `asseteditor`

  [CQ.dam.AssetEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die `Asset Editor` wird in DAM Admin verwendet.

* `assetreferencesearchdialog`

  [CQ.wcm.AssetReferenceSearchDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Der `AssetReferenceSearchDialog` ist ein Dialogfeld, das angezeigt wird, wenn eine Seite auf Assets oder Tags verweist.

* `blueprintconfig`

  [CQ.wcm.msm.BlueprintConfig](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Der `BlueprintConfig` bietet ein Bedienfeld, in dem Sie die Live Copies eines Blueprints anzeigen und diese Blueprint-Eigenschaften bearbeiten können ( Synchronisierungs-Trigger und Synchronisierungsaktionen ).

* `blueprintstatus`

  [CQ.wcm.msm.BlueprintStatus](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  BlueprintStatus stellt ein Feld bereit, in dem Sie einen Blueprint und dessen Live Copies-Beziehungen anzeigen und bearbeiten können. Das Durchsuchen erfolgt über [CQ.wcm.msm.BlueprintStatus.Tree](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), die Bearbeitung über [CQ.wcm.msm.BlueprintConfig](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) und [CQ.wcm.msm.LiveCopyProperties](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `box`

  [CQ.Ext.BoxComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine allgemeine Klasse für eine beliebige [Komponente](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), die anhand von Breite und Höhe als Feld formatiert werden soll.

  BoxComponent passt das Feldmodell automatisch an die Größen- und Platzierungsdefinition an und funktioniert auch im Rendering-Modell der Komponente ordnungsgemäß.

* `browsedialog`

  [CQ.BrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit BrowseDialog können Benutzende das Repository durchsuchen und einen Pfad auswählen. Die Klasse wird in der Regel in einem [BrowseField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) verwendet.

* `browsefield`

  [CQ.form.BrowseField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Veraltet: Verwenden Sie stattdessen [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).**

* `bulkeditor`

  [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die `BulkEditor` bietet eine Suchmaschine und ein Raster zum Bearbeiten von Suchergebnissen.

  Die `BulkEditor` muss in ein HTML-Formular eingefügt werden (erforderlich für die Importfunktion). Dies funktioniert ausgezeichnet mit einem [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `bulkeditorform`

  [CQ.wcm.BulkEditorForm](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  BulkEditorForm stellt [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) umgeben von einem HTML-Formular bereit. Die eigenständige Version von &quot;[.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Für die Importschaltfläche ist ein HTML-Formular erforderlich.

* `button`

  [CQ.Ext.Button](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine einfache Schaltflächenklasse.

* `buttongroup`

  [CQ.Ext.ButtonGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein Container für eine Schaltflächengruppe.

* `chart`

  [CQ.Ext.chart.Chart](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Das Paket CQ.Ext.chart stellt die Funktion zum Visualisieren von Daten anhand von Flash-basierten Diagrammen bereit. Jedes Diagramm wird direkt an einen CQ.Ext.data.Store gebunden, was automatische Aktualisierungen des Diagramms ermöglicht. Sie können das Erscheinungsbild eines Diagramms anhand der Konfigurationsoptionen [chartStyle](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) und [extraStyle](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) ändern.

* `checkbox`

  [CQ.Ext.form.Checkbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein einzelnes Kontrollkästchen. Kann als direkter Ersatz für herkömmliche Kontrollkästchen verwendet werden.

* `checkboxgroup`

  [CQ.Ext.form.CheckboxGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein Gruppierungs-Container für [CQ.Ext.form.Checkbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Steuerelemente.

* `clearcombo`

  [CQ.form.ClearableComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ClearableComboBox ist ein nicht bearbeitbares Kombinationsfeld mit einem Auslöser zum Löschen des darin enthaltenen Werts.

* `colorfield`

  [CQ.form.ColorField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit ColorField können Benutzer einen Hex-Farbwert direkt oder über das [CQ.Ext.ColorMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) eingeben.

* `colorlist`

  [CQ.form.ColorList](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit ColorList kann der Benutzer eine Farbe aus einer bearbeitbaren Liste auswählen.

* `colormenu`

  [CQ.Ext.menu.ColorMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein Menü, das eine [CQ.Ext.ColorPalette](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Komponente enthält.

* `colorpalette`

  [CQ.Ext.ColorPalette](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine einfache Farbpalettenklasse zum Auswählen von Farben. Die Palette kann in einem beliebigen Container gerendert werden.

* `combo`

  [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein Kombinationsfeld-Steuerelement mit Unterstützung für das automatische Ausfüllen, Remote-Laden, Paging und viele andere Funktionen.

  Eine ComboBox funktioniert ähnlich wie ein herkömmliches &lt;select>-Feld in HTML. Der Unterschied besteht darin, dass für das [valueField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) ein [hiddenName](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) angegeben werden muss, um eine ausgeblendete Eingabe zu erstellen.

* `component`

  [CQ.Ext.Component](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basisklasse für alle `Ext`. Alle Unterklassen von „Component“ können am Lebenszyklus der automatisierten `Ext`-Komponente von Erstellung, Rendering und Zerstörung teilnehmen, der von der Klasse [Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) bereitgestellt wird. Komponenten können einem Container über die Konfigurationsoption [items](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) hinzugefügt werden, wenn der Container erstellt wird.

* `componentextractor`

  [CQ.wcm.ComponentExtractor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit ComponentExtractor können Benutzer Komponenten aus einer Website bzw. Seite extrahieren.

* `componentselector`

  [CQ.form.ComponentSelector](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine gruppierte, sortierte Auswahl der verfügbaren Komponenten.

* `componentstyles`

  [CQ.form.ComponentStyles](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `compositefield`

  [CQ.form.CompositeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine allgemeine Klasse für feldbasierte, komplexe Formularfelder, einschließlich einzelner Formularfelder oder Formularfeldgruppen.

* `container`

  [CQ.Ext.Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine allgemeine Klasse für eine beliebige [CQ.Ext.BoxComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), die andere Komponenten enthalten kann. Container behandeln das grundlegende Verhalten von enthaltenen Elementen, d. h. das Hinzufügen, Einfügen und Entfernen von Elementen.

  Die am häufigsten verwendeten Container-Klassen sind [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) und [CQ.Ext.TabPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `contentfinder`

  [CQ.wcm.ContentFinder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ContentFinder ist ein spezieller, zweispaltiger [Viewport](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) mit der Inhaltssuche auf der linken und dem Inhalts-Frame auf der rechten Seite.

* `contentfindertab`

  [CQ.wcm.ContentFinderTab](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ContentFinderTab ist ein spezialisiertes Bedienfeld mit Funktionen, die in den Registerkartenfeldern in [CQ.wcm.ContentFinder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) verwendet werden. In der Regel verfügt sie über ein Suchformular - das Abfragefeld - und eine Datenansicht, um die Suche anzuzeigen.

* `cq.workflow.model.combo`

  [CQ.wcm.WorkflowModelCombo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  WorkflowModelCombo ist ein benutzerdefiniertes [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), in dem eine Liste der verfügbaren Workflow-Modelle angezeigt wird.

* `cq.workflow.model.selector`

  [CQ.wcm.WorkflowModelSelector](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  WorkflowModelSelector ist eine Kombination aus WorkflowModelCombo und Workflow-Miniaturbild und enthält auch Schaltflächen zum Erstellen und Bearbeiten von Workflow-Modellen.

* `createsitewizard`

  [CQ.wcm.CreateSiteWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CreateSiteWizard ist ein schrittweiser Assistent zum Erstellen von (MSM-)Sites.

* `createversiondialog`

  [CQ.wcm.CreateVersionDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CreateVersionDialog ist ein Dialogfeld, in dem eine neue Version einer Seite erstellt werden kann.

* `customcontentpanel`

  [CQ.CustomContentPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CustomContentPanel ist ein spezielles Bedienfeld für die Verwendung in [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html): Die darin enthaltenen Inhalte werden von einer anderen URL abgerufen bzw. zu einer anderen URL gesendet als die anderen Felder im Dialogfeld.

* `cycle`

  [CQ.Ext.CycleButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein spezieller SplitButton, der ein Menü mit [CQ.Ext.menu.CheckItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Elementen enthält. Bei jedem Klick durchblättert die Schaltfläche automatisch alle Menüelemente und löst für das aktive Menüelement das [change](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Ereignis aus (bzw. ruft die [changeHandler](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Funktion, falls vorhanden).

* `dataview`

  [CQ.Ext.DataView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein Mechanismus für die Datenanzeige mithilfe von benutzerdefinierten Layout-Vorlagen und Formatierungen. DataView verwendet ein [CQ.Ext.XTemplate](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) als internen Vorlagenmechanismus und ist mit einem [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) verbunden, sodass beim Ändern von Daten im Speicher die Ansicht automatisch mit diesen Änderungen aktualisiert wird.

* `datefield`

  [CQ.Ext.form.DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Es stellt ein Datumseingabefeld mit einer [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Dropdown-Liste und automatischer Datumsvalidierung bereit.

* `datemenu`

  [CQ.Ext.menu.DateMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein Menü, das eine [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Komponente enthält.

* `datepicker`

  [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein Popup-Datumsauswahl. Diese Klasse wird von der Klasse [DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) verwendet, um das Durchsuchen und Auswählen von gültigen Daten zu ermöglichen.

* `datetime`

  [CQ.form.DateTime](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit DateTime können Benutzer ein Datum und eine Uhrzeit eingeben, indem sie [CQ.Ext.form.DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) und [CQ.Ext.form.TimeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) miteinander kombinieren.

* `dialog`

  [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Das Dialogfeld ist ein spezielles Fenster. Es hat ein Formular im Hauptteil und eine Schaltflächengruppe in der Fußzeile. Es wird in der Regel zum Bearbeiten von Inhalten verwendet, kann aber auch nur zur Anzeige von Informationen genutzt werden.

* `dialogfieldset`

  [CQ.form.DialogFieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  DialogFieldSet ist ein [FieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) zur Verwendung in [Dialogfeldern](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `directstore`

  [CQ.Ext.data.DirectStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine kleine Helper-Klasse zum Erstellen eines [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), konfiguriert mit einem [CQ.Ext.data.DirectProxy](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) und [CQ.Ext.data.JsonReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), um die Interaktion mit einem [CQ.Ext.Direct](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) Server-seitigen [Provider](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) zu erleichtern.

* `displayfield`

  [CQ.Ext.form.DisplayField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein nur für die Anzeige bestimmtes Textfeld, das nicht validiert und gesendet wird.

* `editbar`

  [CQ.wcm.EditBar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit EditBar können Benutzer mithilfe von Schaltflächen in einer Leiste Inhalte bearbeiten.

  Obwohl hier nicht aufgeführt, enthält EditBar alle Mitglieder von [CQ.wcm.EditBase](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `editor`

  [CQ.Ext.Editor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein allgemeines Editor-Feld für die Anzeige bzw. das Ausblenden nach Bedarf, mit integrierter Logik für Größenänderung und Ereignisbehandlung.

* `editorgrid`

  [CQ.Ext.grid.EditorGridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Diese Klasse erweitert die [GridPanel-Klasse](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), um die Bearbeitung von Zellen in ausgewählten [Spalten](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) zu ermöglichen. Die bearbeitbaren Spalten werden durch Angabe eines [Editors](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) in der [Spaltenkonfiguration](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) festgelegt.

* `editrollover`

  [CQ.wcm.EditRollover](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit EditRollover können Benutzende Inhalte durch Doppelklick bearbeiten und über ein Kontextmenü weitere Bearbeitungsaktionen durchführen. Der bearbeitbare Bereich wird durch einen Rahmen gekennzeichnet, wenn die Maus über den Inhalt bewegt wird.

* `feedimporter`

  [CQ.wcm.FeedImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit FeedImporter können Benutzer RSS- oder Atom-Feeds importieren und Seiten für jeden Feed-Eintrag erstellen.

* `field`

  [CQ.Ext.form.Field](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine allgemeine Klasse für Formularfelder, die Standardfunktionen für die Ereignisbehandlung, Größenänderung, Werteverarbeitung und anderes bereitstellt.

* `fieldset`

  [CQ.Ext.form.FieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein Standard-Container zum Gruppieren von Elementen in einem [Formular](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `fileuploaddialogbutton`

  [CQ.form.FileUploadDialogButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  FileUploadDialogButton erstellt eine Schaltfläche, die ein neues Dialogfeld zum Hochladen einer Datei über FileUploadField öffnet. Kann in Bearbeitungsdialogfeldern verwendet werden, in denen der Upload in einem separaten Formular erfolgen muss.

* `fileuploadfield`

  [CQ.form.FileUploadField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit FileUploadField können Benutzer eine einzelne Datei zum Hochladen auswählen.

* `findreplacedialog`

  [CQ.wcm.FindReplaceDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  FindReplaceDialog ist ein Dialogfeld zum Suchen nach und Ersetzen von Token auf einer Seite und deren untergeordneten Seiten.

* `flash`

  [CQ.Ext.FlashComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `grid`

  [CQ.Ext.grid.GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Diese Klasse stellt die primäre Oberfläche eines komponentenbasierten Raster-Steuerelements dar, um Daten im Tabellenformat in Zeilen und Spalten darzustellen.

* `groupingstore`

  [CQ.Ext.data.GroupingStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine spezielle Speicherimplementierung zum Gruppieren von Einträgen nach einem der verfügbaren Felder. Wird mit einem [CQ.Ext.grid.GroupingView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) zum Testen des Datenmodells für ein gruppiertes GridPanel verwendet.

* `heavymovedialog`

  [CQ.wcm.HeavyMoveDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  HeavyMoveDialog ist ein Dialogfeld zum Verschieben einer Seite und ihrer untergeordneten Seiten, einschließlich der Reaktivierung zuvor aktivierter Seiten („große“ Verschiebung).

* `hidden`

  [CQ.Ext.form.Hidden](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein allgemeines verborgenes Feld zum Speichern ausgeblendeter Werte in Formularen, die beim Senden des Formulars weitergegeben werden müssen.

* `historybutton`

  [CQ.HistoryButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  HistoryButton ist eine kleine Hilfsklasse zur einfachen Bereitstellung der Schaltflächen „Vorwärts“ und „Zurück“. Normalerweise sind zwei verwandte Instanzen erforderlich: Die Instanz für die Schaltfläche „Vorwärts“ ist eine einfache Schaltfläche, die mit der Instanz für die Schaltfläche „Zurück“ verknüpft ist, die den Verlauf handhabt.

* `htmleditor`

  [CQ.Ext.form.HtmlEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Es bietet eine einfache HTML-Editor-Komponente. Safari unterstützt einige Symbolleistenfunktionen nicht, sodass sie vom System bei Bedarf automatisch ausgeblendet werden. Wird bei Bedarf in den Konfigurationsoptionen erwähnt.

  Für die Schaltflächen in der Editor-Symbolleiste sind in der [buttonTips](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Eigenschaft QuickInfos definiert.

* `iframedialog`

  [CQ.IframeDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein einfaches Dialogfeld, das den Inhalt eines iframe anzeigt und Formulare in iframes zulässt.

* `iframepanel`

  [CQ.IframePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein Feld mit einem iFrame. Es bietet einfache Erstellung von iFrames, ein iFrame-Ladeereignis und einfachen Zugriff auf den Inhalt des iFrames.

* `inlinetextfield`

  [CQ.form.InlineTextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  InlineField ist ein Textfeld, das als Beschriftung angezeigt wird, wenn es sich nicht im Fokus befindet.

* `jsonstore`

  [CQ.Ext.data.JsonStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine kleine Helper-Klasse, um das Erstellen [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) aus JSON-Daten zu vereinfachen. Ein JsonStore wird automatisch mit einem [CQ.Ext.data.JsonReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) konfiguriert.

* `label`

  [CQ.Ext.form.Label](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein einfaches Beschriftungsfeld.

* `languagecopydialog`

  [CQ.wcm.LanguageCopyDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  LanguageCopyDialog ist ein Dialogfeld zum Kopieren von Sprachstrukturen.

* `linkchecker`

  [CQ.wcm.LinkChecker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  LinkChecker ist ein Tool zum Überprüfen externer Links in einer Site.

* `listview`

  [CQ.Ext.list.ListView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CQ.Ext.list.ListView ist eine schnelle, einfache Implementierung einer [rasterähnlichen](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) Ansicht.

* `livecopyproperties`

  [CQ.wcm.msm.LiveCopyProperties](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  LiveCopyProperties stellt ein Bedienfeld zum Anzeigen und Bearbeiten von Live Copy-Eigenschaften („Beziehungsvererbung“, „Synchronisierungsauslöser“ und „Aktionen synchronisieren“) bereit.

* `lvbooleancolumn`

  [CQ.Ext.list.BooleanColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine Spaltendefinitionsklasse, die boolesche Datenfelder rendert. Weitere Informationen finden Sie unter [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Konfigurationsoptionen von [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `lvcolumn`

  [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Diese Klasse kapselt Konfigurationsdaten von Spalten, die bei der Initialisierung von [ListView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) verwendet werden sollen.

* `lvdatecolumn`

  [CQ.Ext.list.DateColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine Spaltendefinitionsklasse, die ein übergebenes Datum gemäß dem Standardgebietsschema oder einem konfigurierten [Format](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) rendert. Weitere Informationen finden Sie unter [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Konfigurationsoptionen von [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `lvnumbercolumn`

  [CQ.Ext.list.NumberColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine Spaltendefinitionsklasse, die ein numerisches Datenfeld gemäß einer [Format](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Zeichenfolge rendert. Weitere Informationen finden Sie unter [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Konfigurationsoptionen von [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `mediabrowsedialog`

  [CQ.MediaBrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Veraltet: Verwenden Sie stattdessen [Content Finder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), um Medien zu durchsuchen.**

  MediaBrowseDialog ist ein Dialogfeld zum Durchsuchen der Medienbibliothek.

* `menu`

  [CQ.Ext.menu.Menu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein Menüobjekt. Der Container, dem Menüelemente hinzugefügt werden können. Das Menü kann auch als allgemeine Klasse dienen, wenn Sie ein spezielles Menü basierend auf einer anderen Komponente (wie z. B. [CQ.Ext.menu.DateMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)) benötigen.

  Menüs können entweder [Menüelemente](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) oder allgemeine [Komponenten](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) enthalten.

* `menubaseitem`

  [CQ.Ext.menu.BaseItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die allgemeine Klasse für alle in Menüs gerenderten Elemente. „BaseItem“ stellt Optionen für das Standard-Rendering, die Verwaltung in aktiviertem Zustand und die Basiskonfiguration bereit, die von allen Menükomponenten gemeinsam verwendet werden.

* `menucheckitem`

  [CQ.Ext.menu.CheckItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Dadurch wird ein Menüelement hinzugefügt, das standardmäßig ein Kontrollkästchen enthält, aber auch Teil einer Optionsfeldgruppe sein kann.

* `menuitem`

  [CQ.Ext.menu.Item](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine Basisklasse für alle Menüelemente, für die menübezogene Funktionen (wie Untermenüs) erforderlich sind und bei denen es sich nicht um statische Anzeigeelemente handelt. „Item“ erweitert die allgemeinen Funktionen von [CQ.Ext.menu.BaseItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) und fügt die menüspezifische Bearbeitung von Aktivierungs- und Klickaktionen hinzu.

* `menuseparator`

  [CQ.Ext.menu.Separator](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Einem Menü wird eine Trennleiste hinzugefügt, mit der logische Gruppen von Menüelementen geteilt werden. Im Allgemeinen fügen Sie sie mit &quot;-&quot; in Ihrem Aufruf von add() oder in Ihrer Konfiguration „items“ hinzu, anstatt sie direkt zu erstellen.

* `menutextitem`

  [CQ.Ext.menu.TextItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Dadurch wird einem Menü eine statische Textzeichenfolge hinzugefügt, die entweder als Überschrift oder als Gruppentrennzeichen verwendet wird.

* `metadata`

  [CQ.dam.form.Metadata](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Metadata` stellt einen Satz von Feldern bereit, mit denen bestimmt wird, welche Informationen für ein Metadatenfeld erforderlich sind, das z. B. auf Asset-Editor-Seiten verwendet wird.

  Die Klasse enthält die folgenden Felder:

* `multifield`

  [CQ.form.MultiField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Der `MultiField` ist eine bearbeitbare Liste von Formularfeldern zum Bearbeiten von Eigenschaften mit mehreren Werten.

* `mvt`

  [CQ.form.MVT](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die Komponente „Multivariate Testing“ kann verwendet werden, um eine Reihe von Bildern zu definieren und zu bearbeiten, die als alternierende Banner dargestellt werden. Klickratenstatistiken werden pro Banner erfasst.

* `notificationinbox`

  [CQ.wcm.NotificationInbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit der `NotificationInbox` kann der Benutzer WCM-Aktionen abonnieren und Benachrichtigungen verwalten.

* `numberfield`

  [CQ.Ext.form.NumberField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein numerisches Textfeld, das automatisch Tastenanschläge filtert und numerische Werte validiert.

* `offlineimporter`

  [CQ.wcm.OfflineImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Der `OfflineImporter` ist ein Tool zum Importieren und Konvertieren von Microsoft® Word-Dokumenten in AEM-Seiten. Mit dieser Funktion können Inhalte mithilfe eines Textverarbeitungsgeräts offline bearbeitet werden.

* `ownerdraw`

  [CQ.form.OwnerDraw](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die `OwnerDraw` kann benutzerdefinierten HTML-Code enthalten (der entweder direkt eingegeben oder von einer URL abgerufen wurde).

* `paging`

  [CQ.Ext.PagingToolbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit einer steigenden Anzahl von Einträgen steigt auch die vom Browser zum Rendern benötigte Zeit. Paging wird verwendet, um die Datenmenge zu reduzieren, die mit dem Client ausgetauscht wird.

* `panel`

  [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein `panel` ist ein Container mit spezifischen Funktionen und Strukturkomponenten, die ihn zum perfekten Baustein für anwendungsorientierte Benutzeroberflächen machen.

  Panels werden aufgrund ihrer Vererbung von &quot;[.Ext.Container“ &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `paragraphreference`

  [CQ.form.ParagraphReference](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Das Feld „ParagraphReference“ ermöglicht es, Seiten zu durchsuchen und einen der darin enthaltenen Absätze auszuwählen. Es beinhaltet ein Auslöserfeld und ein damit verknüpftes Dialogfeld zum Durchsuchen von Absätzen.

* `password`

  [CQ.form.Password](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Der `Password` ähnelt einem [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) behält jedoch seinen Wert privat, sodass Benutzer vertrauliche Daten eingeben können.

* `pathcompletion`

  [CQ.form.PathCompletion](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Veraltet: Verwenden Sie stattdessen [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).**

* `pathfield`

  [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Das `PathField` ist ein Eingabefeld für Pfade mit Pfadvervollständigung und einer Schaltfläche zum Öffnen eines [CQ.BrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) zum Durchsuchen des Server-Repositorys. Damit können auch Seitenabsätze zur erweiterten Link-Erzeugung durchsucht werden.

* `progress`

  [CQ.Ext.ProgressBar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine Komponente mit einer Fortschrittsleiste, die aktualisiert werden kann. Die Fortschrittsleiste unterstützt zwei verschiedene Modi: manuell und automatisch.

  Im manuellen Modus sind Sie für das Anzeigen, Aktualisieren (über [updateProgress](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)) und Löschen der Fortschrittsleiste nach Bedarf über Ihren eigenen Code verantwortlich. Diese Methode eignet sich am besten, wenn Sie den Fortschritt anzeigen möchten.

* `propertygrid`

  [CQ.Ext.grid.PropertyGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine spezielle Rasterimplementierung, die das herkömmliche Eigenschaftenraster nachahmen soll, das normalerweise in Entwicklungs-IDEs verwendet wird. Jede Zeile im Raster steht für eine Eigenschaft eines Objekts; die Daten werden in Namen-Wert-Paaren in [CQ.Ext.grid.PropertyRecord](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) gespeichert.

* `propgrid`

  [CQ.PropertyGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die `PropertyGrid` ist ein generisches Raster, das zum Anzeigen und Bearbeiten von Eigenschaften von Objekten verwendet wird.

* `quicktip`

  [CQ.Ext.QuickTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `@xtype quicktip` : Eine spezielle QuickInfo-Klasse für QuickInfos, die im Markup angegeben und automatisch von der globalen [CQ.Ext.QuickTips](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Instanz verwaltet werden können. Zusätzliche Informationen zur Verwendung und Beispiele finden Sie unter dem Header „QuickTips-Klasse“.

* `radio`

  [CQ.Ext.form.Radio](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Einzelnes `radio`. Ähnlich wie das Kontrollkästchen, der Eingabetyp kann jedoch für die einfache Verwendung automatisch festgelegt werden. Optionsschaltflächen werden im Browser automatisch gruppiert, wenn jede Optionsschaltfläche in der Gruppe denselben Namen verwendet.


* `radiogroup`

  [CQ.Ext.form.RadioGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein Gruppierungscontainer für [CQ.Ext.form.Radio](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Steuerelemente.

* `referencesdialog`

  [CQ.wcm.ReferencesDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Das `ReferencesDialog` ist ein Dialogfeld zum Anzeigen von Verweisen auf einer Seite.

* `restoretreedialog`

  [CQ.wcm.RestoreTreeDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Das `RestoreTreeDialog` ist ein Dialogfeld zum Wiederherstellen einer früheren Version eines Baums.

* `restoreversiondialog`

  [CQ.wcm.RestoreVersionDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  RestoreVersionDialog ist ein Dialogfeld zum Wiederherstellen einer früheren Version einer Seite.

* `richtext`

  [CQ.form.RichText](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die `RichText` bietet ein Formularfeld zum Bearbeiten von formatierten Textinformationen (Rich-Text).

  Die `RichText`-Komponente bietet derzeit die folgenden Funktionen:

* `rolloutplan`

  [CQ.wcm.msm.RolloutPlan](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  RolloutPlan stellt ein Dialogfeld zum Überwachen des Rollout-Fortschritts einer Seite bereit. Ein [CQ.wcm.msm.RolloutWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) startet den RolloutPlan.

* `rolloutwizard`

  [CQ.wcm.msm.RolloutWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die `RolloutWizard` bietet einen Assistenten für das Rollout einer Seite. „RolloutWizard“ startet einen [CQ.wcm.msm.RolloutPlan](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `searchfield`

  [CQ.form.SearchField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Der `SearchField` bietet ein Suchfeld , das die Ergebnisse in einer Dropdown-Liste bereitstellt, die für die Suche im Repository verwendet werden kann.

* `selection`

  [CQ.form.Selection](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit dem `Selection` können Benutzende zwischen mehreren Optionen wählen. Die Optionen können Teil der Konfiguration sein oder aus einer JSON-Antwort geladen werden. Die Auswahl kann entweder als Dropdown-Liste (Auswahl) oder als Kombinationsfeld (Auswahl plus freie Texteingabe) gerendert werden.

* `sidekick`

  [CQ.wcm.Sidekick](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Der `Sidekick` ist ein unverankerter Helfer, der den Benutzenden allgemeine Tools zur Seitenbearbeitung bereitstellt.

* `siteadmin`

  [CQ.wcm.SiteAdmin](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Der `SiteAdmin` ist eine Konsole mit WCM-Verwaltungsfunktionen.

* `siteimporter`

  [CQ.wcm.SiteImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit dem `SiteImporter` können Benutzer komplette Websites importieren und erste Projekte erstellen.

* `sizefield`

  [CQ.form.SizeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit der `SizeField` können Benutzende die Breite und Höhe (z. B. für ein Bild) eingeben.

* `slider`

  [CQ.Ext.Slider](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein Regler für die vertikale und horizontale Ausrichtung, Tastaturanpassungen, konfigurierbare Ausrichtungen, Achsenklicks und Animationen. Sie kann als Element zu einem beliebigen Container hinzugefügt werden. Beispielsweise die Verwendung: …

* `slideshow`

  [CQ.form.Slideshow](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit der Slideshow-Komponente können Sie eine Reihe von Bildern und Bildtiteln definieren und bearbeiten. Benutzer können das Set als Diashow anzeigen.

  Die Komponente für die Bildschirmpräsentation basiert auf der Komponente [CQ.form.SmartImage](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `smartfile`

  [CQ.form.SmartFile](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  „SmartFile“ ist ein intelligenter Datei-Uploader.

  Wenn ein Flash-Plug-in (Version 9 oder höher) installiert ist, werden Uploads mit der SWFupload-Bibliothek durchgeführt, was eine benutzerfreundliche Upload-Methode darstellt.

* `smartimage`

  [CQ.form.SmartImage](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  SmartImage ist ein intelligenter Bild-Uploader, der Tools zum Verarbeiten von hochgeladenen Bildern bereitstellt, beispielsweise ein Definitions-Tool für Imagemaps und einen Bildzuschneider.

  Die Komponente ist für die Verwendung in einer separaten Dialogfeldregisterkarte konzipiert.

* `spacer`

  [CQ.Ext.Spacer](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Wird verwendet, um einen anpassbaren Bereich in einem Layout bereitzustellen.

* `spinner`

  [CQ.form.Spinner](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Das `Spinner` ist ein Trigger-Feld für numerische, Datums- oder Zeitwerte. Der Wert kann mithilfe der bereitgestellten Auf- und Ab-Trigger, des Scrollrads oder der Tasten erhöht und verringert werden.

* `splitbutton`

  [CQ.Ext.SplitButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein `splitbutton`, das einen integrierten Dropdownpfeil bereitstellt, der ein Ereignis separat vom Standardklickereignis der Schaltfläche auslösen kann. Normalerweise wird sie zum Anzeigen eines Dropdown-Menüs verwendet, das zusätzliche Optionen zur primären Schaltflächenaktion bereitstellt. Jeder benutzerdefinierte Handler kann jedoch die `arrowclick` Implementierung bereitstellen.

* `static`

  [CQ.Static](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die `Static` kann verwendet werden, um beliebigen Text oder HTML anzuzeigen.

* `statistics`

  [CQ.wcm.Statistics](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die `Statistics` zeigt die Seitenimpressionen als Diagramm an. Das Widget ermöglicht die Auswahl eines Zeitraums, für den die Statistiken angezeigt werden sollen.

* `store`

  [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die `Store`-Klasse kapselt einen Client-seitigen Cache von [Record](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Objekten, die Eingabedaten für Komponenten wie [GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), [ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) oder [DataView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `suggestfield`

  [CQ.form.SuggestField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die `SuggestField` bietet Benutzenden Vorschläge auf Grundlage ihrer Eingabe.

* `switcher`

  [CQ.Switcher](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Der `Switcher` bietet eine Schaltflächengruppe für die Kopfzeilenleiste in einer Konsole, mit der Sie zwischen Websites, Digital Assets, Tools, Workflows und Sicherheit wechseln können.

* `tableedit`

  [CQ.form.TableEdit](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Veraltet: Verwenden Sie stattdessen [CQ.form.TableEdit2.](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)**

* `tableedit2`

  [CQ.form.TableEdit2](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die `TableEdit2` bietet ein Widget zum Erstellen von Tabellen.

* `tabpanel`

  [CQ.Ext.TabPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein allgemeiner Container für Registerkarten. TabPanels kann zu Layout-Zwecken genauso wie ein standardmäßiges [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) verwendet werden, verfügt aber auch über spezielle Unterstützung für darin enthaltene untergeordnete Komponenten ([`items` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)).

* `tags`

  [CQ.tagging.TagInputField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ```
  CQ.tagging.TagInputField
  ```

  ist ein Formular-Widget zum Eingeben von Tags. Es verfügt über ein Popup-Menü zur Auswahl vorhandener Tags, einschließlich der automatischen Vervollständigung und vieler anderer Funktionen.

* `textarea`

  [CQ.Ext.form.TextArea](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein mehrere Zeilen umspannendes Textfeld. Kann als direkter Ersatz für herkömmliche `textarea` verwendet werden und unterstützt zusätzlich die automatische Größenanpassung.

* `textbutton`

  [CQ.TextButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die `TextButton` enthält einen Textlink mit den Funktionen einer [CQ.Ext.Button](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `textfield`

  [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein einfaches Textfeld. Kann als direkter Ersatz für herkömmliche Texteingaben oder als allgemeine Klasse für komplexere Eingabeelemente (wie [CQ.Ext.form.TextArea](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) und [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)) verwendet werden.

* `thumbnail`

  [CQ.form.Thumbnail](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `timefield`

  [CQ.Ext.form.TimeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Es bietet ein Zeiteingabefeld mit einer Zeitauswahl und automatischer Zeitvalidierung. Anwendungsbeispiel: ...

* `tip`

  [CQ.Ext.Tip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  @xtype tip. Dieses ist die allgemeine Klasse für [CQ.Ext.QuickTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) und [CQ.Ext.Tooltip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), die das grundlegende Layout und die Platzierung bereitstellt, die für alle Klassen mit QuickInfo erforderlich sind. Diese Klasse kann direkt für einfache, statisch platzierte QuickInfos verwendet werden.

* `titleseparator`

  [CQ.menu.TitleSeparator](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Einem Menü wird eine Trennleiste hinzugefügt, mit der logische Gruppen von Menüelementen geteilt werden. Das Trennzeichen kann auch einen Titel aufweisen.

* `toolbar`

  [CQ.Ext.Toolbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Toolbar`. Obwohl die [`defaultType`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) für Toolbar [`button`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) ist, können Toolbar-Elemente (untergeordnete Elemente für den toolbar-Container) praktisch jeden Komponententyp umfassen. Symbolleistenelemente können explizit über ihre Konstruktoren erstellt werden.

* `tooltip`

  [CQ.Ext.ToolTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine standardmäßige `tooltip`-Implementierung, die zusätzliche Informationen bereitstellt, wenn Sie den Mauszeiger über ein Zielelement bewegen. @xtype tooltip.

* `treegrid`

  [CQ.tree.TreeGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  @xtype `treegrid`

* `treepanel`

  [CQ.Ext.tree.TreePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Die `TreePanel` bietet eine baumstrukturierte Benutzeroberflächendarstellung von baumstrukturierten Daten.

  [TreeNode](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s, die der `TreePanel` hinzugefügt wurden, können jeweils Metadaten enthalten, die von der Anwendung in der [attributes](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)-Eigenschaft verwendet werden.

* `trigger`

  [CQ.Ext.form.TriggerField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Er bietet einen praktischen Wrapper für `TextFields`, der eine anklickbare Trigger-Schaltfläche hinzufügt (die standardmäßig wie ein Kombinationsfeld aussieht). Für den Auslöser gibt es keine Standardaktion. Sie müssen eine Funktion zuweisen, um den Klick-Handler für den Auslöser durch Überschreiben von [onTriggerClick](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) zu implementieren. Sie können ein `TriggerField` direkt erstellen, da es genau wie ein Kombinationsfeld gerendert wird.

* `uploaddialog`

  [CQ.UploadDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mit dem `UploadDialog` können Benutzer Dateien in das Repository hochladen. Erstellt einen neuen UploadDialog.

* `userinfo`

  [CQ.UserInfo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein Element der Symbolleiste, das den aktuellen Benutzernamen anzeigt und Benutzeraktionen wie das Bearbeiten von Benutzereigenschaften und die Personifikation ermöglicht.

* `viewport`

  [CQ.Ext.Viewport](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein spezieller Container, der den sichtbaren Anwendungsbereich (das Browser-Darstellungsfeld) darstellt.

  Der `Viewport` rendert sich selbst im Dokumenthauptteil und passt sich automatisch der Größe des Browser-Ansichtsfensters an und verwaltet die Größenanpassung des Fensters. Es kann nur ein Viewport erstellt werden.

* `window`

  [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ein spezielles Bedienfeld, das als Anwendungsfenster verwendet werden soll. Fenster sind standardmäßig nicht verankert, [anpassbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) und per Maus [ziehbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Fenster können auf die Größe des Darstellungsfelds [maximiert](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), auf die ursprüngliche Größe zurückgesetzt oder [minimiert](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) werden.

* `xmlstore`

  [CQ.Ext.data.XmlStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eine kleine Hilfsklasse, die das Erstellen von [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) aus XML-Daten erleichtert. Eine `XmlStore` wird automatisch mit einem [CQ.Ext.data.XmlReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) konfiguriert.

  `cqinclude` - Ein Pseudo-xtype, das Widget-Definitionen aus einem anderen Pfad im Repository enthält. Sie wird am häufigsten in Dialogfeldern für Seiten verwendet. Für diesen xtype gibt es keine tatsächliche JavaScript-Widget-Klasse. Die `CQ.Util`-Klasse verarbeitet sie mithilfe der `formatData()`.
