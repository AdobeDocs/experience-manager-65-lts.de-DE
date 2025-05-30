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
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '3865'
ht-degree: 93%

---

# Verwenden von xtypes (klassische Benutzeroberfläche){#using-xtypes-classic-ui}

Auf dieser Seite werden alle xtypes beschrieben, die in Adobe Experience Manager (AEM) verfügbar sind.

In der ExtJS-Sprache ist ein xtype ein symbolischer Name, der einer Klasse zugewiesen wird. Eine ausführliche Erläuterung der Funktionsweise und Einsatzmöglichkeiten von xtypes finden Sie im Abschnitt zu „Komponenten-xtypes“ unter [Übersicht zu ExtJS 2](https://www.sencha.com/learn/overview-of-extjs-2).

Informationen zu allen in AEM verfügbaren Widgets finden Sie in der [Dokumentation zur Widgets-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

Sie können die folgende Xpath-Abfrage in CRXDE verwenden, um herausfinden, in welchen Komponenten ein bestimmter xtype in AEM verwendet wird. Ersetzen Sie dazu „checkbox“ durch den gewünschten xtype:

`//element(*, cq:Widget)[@xtype='checkbox']`

>[!NOTE]
>
>Diese Seite beschreibt die Verwendung von ExtJS-xtypes in der klassischen Benutzeroberfläche.
>
>Adobe empfiehlt die Verwendung der standardmäßigen, modernen [Touch-optimierten Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md), die auf der [Coral](/help/sites-developing/touch-ui-concepts.md#coral-ui)- und [Granite-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components) basiert.

## xtypes {#xtypes}

Im Folgenden sind die verfügbaren xtypes in Adobe Experience Manager aufgeführt:

* annotation

  [CQ.wcm.Annotation](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.Annotation)

   Ein spezielles Fenster mit einem Formular im Hauptteil und einer Schaltflächengruppe in der Fußzeile. Es wird in der Regel zum Bearbeiten von Inhalten verwendet, kann aber auch nur zur Anzeige von Informationen genutzt werden.

* arraystore

  [CQ.Ext.data.ArrayStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.ArrayStore)

  Zuvor als „SimpleStore“ bezeichnet.

  Kleine Helferklasse die das Erstellen von [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Store)s aus Array-Daten erleichtert. Ein ArrayStore wird automatisch mit einem [CQ.Ext.data.ArrayReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.ArrayReader) konfiguriert.

* asseteditor

  [CQ.dam.AssetEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.dam.AssetEditor)

  Der in DAM Admin verwendete Asset-Editor.

* assetreferencesearchdialog

  [CQ.wcm.AssetReferenceSearchDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.AssetReferenceSearchDialog)

  AssetReferenceSearchDialog ist ein Dialogfeld, das angezeigt wird, wenn eine Seite auf Assets oder Tags verweist.

* blueprintconfig

  [CQ.wcm.msm.BlueprintConfig](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.BlueprintConfig)

   BlueprintConfig stellt ein Feld bereit, in dem Sie die Live Copies eines Blueprint anzeigen und die Blueprint-Eigenschaften („Synchronisierungsauslöser“ und „Aktionen synchronisieren“) bearbeiten können.

* blueprintstatus

  [CQ.wcm.msm.BlueprintStatus](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.BlueprintStatus)

  BlueprintStatus stellt ein Feld bereit, in dem Sie einen Blueprint und dessen Live Copies-Beziehungen anzeigen und bearbeiten können. Das Durchsuchen erfolgt über [CQ.wcm.msm.BlueprintStatus.Tree](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.BlueprintStatus.Tree), die Bearbeitung über [CQ.wcm.msm.BlueprintConfig](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.BlueprintConfig) und [CQ.wcm.msm.LiveCopyProperties](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.LiveCopyProperties).

* box

  [CQ.Ext.BoxComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.BoxComponent)

  Eine allgemeine Klasse für eine beliebige [Komponente](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Component), die anhand von Breite und Höhe als Feld formatiert werden soll.

  BoxComponent passt das Feldmodell automatisch an die Größen- und Platzierungsdefinition an und funktioniert auch im Rendering-Modell der Komponente ordnungsgemäß.

* browsedialog

  [CQ.BrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.BrowseDialog)

  Mit BrowseDialog können Benutzende das Repository durchsuchen und einen Pfad auswählen. Die Klasse wird in der Regel in einem [BrowseField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.BrowseField) verwendet.

* browsefield

  [CQ.form.BrowseField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.BrowseField)

  **Veraltet: Verwenden Sie stattdessen [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.PathField).**

* bulkeditor

  [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.BulkEditor)

  BulkEditor stellt eine Suchmaschine und ein Raster zum Bearbeiten von Suchergebnissen bereit.

  Der BulkEditor muss in ein HTML-Formular eingefügt werden (für die Importfunktion erforderlich). Dies funktioniert ausgezeichnet mit einem [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Dialog).

* bulkeditorform

  [CQ.wcm.BulkEditorForm](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.BulkEditorForm)

  BulkEditorForm stellt [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.BulkEditor) umgeben von einem HTML-Formular bereit. Dies ist die eigenständige Version von [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.BulkEditor). Daher ist das HTML-Formular für die Import-Schaltfläche erforderlich.

* Schaltfläche

  [CQ.Ext.Button](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Button)

  Eine einfache Schaltflächenklasse.

* buttongroup

  [CQ.Ext.ButtonGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ButtonGroup)

  Ein Container für eine Schaltflächengruppe.

* chart

  [CQ.Ext.chart.Chart](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.chart.Chart)

  Das Paket CQ.Ext.chart stellt die Funktion zum Visualisieren von Daten anhand von Flash-basierten Diagrammen bereit. Jedes Diagramm wird direkt an einen CQ.Ext.data.Store gebunden, was automatische Aktualisierungen des Diagramms ermöglicht. Sie können das Erscheinungsbild eines Diagramms anhand der Konfigurationsoptionen [chartStyle](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.chart.Chart) und [extraStyle](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.chart.Chart) ändern.

* checkbox

  [CQ.Ext.form.Checkbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Checkbox)

  Ein einzelnes Kontrollkästchen. Kann als direkter Ersatz für herkömmliche Kontrollkästchen verwendet werden.

* checkboxgroup

  [CQ.Ext.form.CheckboxGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.CheckboxGroup)

  Ein Gruppierungs-Container für [CQ.Ext.form.Checkbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Checkbox)-Steuerelemente.

* clearcombo

  [CQ.form.ClearableComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.ClearableComboBox)

  ClearableComboBox ist ein nicht bearbeitbares Kombinationsfeld mit einem Auslöser zum Löschen des darin enthaltenen Werts.

* colorfield

  [CQ.form.ColorField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.ColorField)

  Mit ColorField können Benutzer einen Hex-Farbwert direkt oder über das [CQ.Ext.ColorMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ColorMenu) eingeben.

* colorlist

  [CQ.form.ColorList](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.ColorList)

  Mit ColorList kann der Benutzer eine Farbe aus einer bearbeitbaren Liste auswählen.

* colormenu

  [CQ.Ext.menu.ColorMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.ColorMenu)

  Ein Menü, das eine [CQ.Ext.ColorPalette](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ColorPalette)-Komponente enthält.

* colorpalette

  [CQ.Ext.ColorPalette](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ColorPalette)

  Eine einfache Farbpalettenklasse zum Auswählen von Farben. Die Palette kann in einem beliebigen Container gerendert werden.

* combo

  [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.ComboBox)

  Ein Kombinationsfeld-Steuerelement mit Unterstützung für das automatische Ausfüllen, Remote-Laden, Paging und viele andere Funktionen.

  Eine ComboBox funktioniert ähnlich wie ein herkömmliches &lt;select>-Feld in HTML. Der Unterschied besteht darin, dass für das [valueField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.ComboBox) ein [hiddenName](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.ComboBox) angegeben werden muss, um eine ausgeblendete Eingabe zu erstellen.

* Komponente

  [CQ.Ext.Component](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Component)

  Eine allgemeine Klasse für alle Ext-Komponenten. Alle Unterklassen von „Component“ können am automatischen Lebenszyklus zum Erstellen, Rendern und Zerstören von Ext-Komponenten beteiligt sein, der von der [Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Container)-Klasse definiert wird. Komponenten können einem Container über die Konfigurationsoption [items](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Container) hinzugefügt werden, wenn der Container erstellt wird.

* componentextractor

  [CQ.wcm.ComponentExtractor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.ComponentExtractor)

  Mit ComponentExtractor können Benutzer Komponenten aus einer Website bzw. Seite extrahieren.

* componentselector

  [CQ.form.ComponentSelector](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.ComponentSelector)

  Eine gruppierte, sortierte Auswahl der verfügbaren Komponenten.

* componentstyles

  [CQ.form.ComponentStyles](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.ComponentStyles)

* compositefield

  [CQ.form.CompositeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.CompositeField)

  Eine allgemeine Klasse für feldbasierte, komplexe Formularfelder, einschließlich einzelner Formularfelder oder Formularfeldgruppen.

* container

  [CQ.Ext.Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Container)

  Eine allgemeine Klasse für eine beliebige [CQ.Ext.BoxComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.BoxComponent), die andere Komponenten enthalten kann. Container behandeln das grundlegende Verhalten von enthaltenen Elementen, d. h. das Hinzufügen, Einfügen und Entfernen von Elementen.

  Die am häufigsten verwendeten Container-Klassen sind [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Panel), [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window) und [CQ.Ext.TabPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.TabPanel).

* contentfinder

  [CQ.wcm.ContentFinder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.ContentFinder)

  ContentFinder ist ein spezieller, zweispaltiger [Viewport](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Viewport) mit der Inhaltssuche auf der linken und dem Inhalts-Frame auf der rechten Seite.

* contentfindertab

  [CQ.wcm.ContentFinderTab](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.ContentFinderTab)

  ContentFinderTab ist ein spezialisiertes Bedienfeld mit Funktionen, die in den Registerkartenfeldern in [CQ.wcm.ContentFinder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.ContentFinder) verwendet werden. Normalerweise enthält es ein Suchformular – das Abfragefeld – und eine Datenansicht zum Anzeigen der Suche.

* cq.workflow.model.combo

  [CQ.wcm.WorkflowModelCombo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.WorkflowModelCombo)

  WorkflowModelCombo ist ein benutzerdefiniertes [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.ComboBox), in dem eine Liste der verfügbaren Workflow-Modelle angezeigt wird.

* cq.workflow.model.selector

  [CQ.wcm.WorkflowModelSelector](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.WorkflowModelSelector)

  WorkflowModelSelector ist eine Kombination aus WorkflowModelCombo und Workflow-Miniaturbild und enthält auch Schaltflächen zum Erstellen und Bearbeiten von Workflow-Modellen.

* createsitewizard

  [CQ.wcm.CreateSiteWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.CreateSiteWizard)

  CreateSiteWizard ist ein schrittweiser Assistent zum Erstellen von (MSM-)Sites.

* createversiondialog

  [CQ.wcm.CreateVersionDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.CreateVersionDialog)

  CreateVersionDialog ist ein Dialogfeld, in dem eine neue Version einer Seite erstellt werden kann.

* customcontentpanel

  [CQ.CustomContentPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.CustomContentPanel)

  CustomContentPanel ist ein spezielles Feld für die Verwendung in [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Dialog): Die darin enthaltenen Inhalte werden von einer anderen URL abgerufen und an eine andere URL gesendet als die übrigen Felder im Dialogfeld.

* cycle

  [CQ.Ext.CycleButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.CycleButton)

  Ein spezieller SplitButton, der ein Menü mit [CQ.Ext.menu.CheckItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.CheckItem)-Elementen enthält. Beim Klicken durchblättert die Schaltfläche automatisch alle Menüelemente und löst für das aktive Menüelement das [change](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.CycleButton)-Ereignis aus (bzw. ruft die Funktion [changeHandler](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.CycleButton) der Schaltfläche ab, falls vorhanden).

* dataview

  [CQ.Ext.DataView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.DataView)

  Ein Mechanismus für die Datenanzeige mithilfe von benutzerdefinierten Layout-Vorlagen und Formatierungen. DataView verwendet ein [CQ.Ext.XTemplate](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.XTemplate) als internen Vorlagenmechanismus und ist mit einem [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Store) verbunden, sodass beim Ändern von Daten im Speicher die Ansicht automatisch mit diesen Änderungen aktualisiert wird.

* datefield

  [CQ.Ext.form.DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.DateField)

  Stellt ein Datumseingabefeld mit einem [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.DatePicker)-Dropdown-Menü und automatischer Datumsvalidierung bereit.

* datemenu

  [CQ.Ext.menu.DateMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.DateMenu)

  Ein Menü, das eine [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.DatePicker)-Komponente enthält.

* datepicker

  [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.DatePicker)

  Ein Popup für die Datumsauswahl. Diese Klasse wird von der Klasse [DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.DateField) verwendet, um das Durchsuchen und Auswählen von gültigen Daten zu ermöglichen.

* datetime

  [CQ.form.DateTime](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.DateTime)

  Mit DateTime können Benutzer ein Datum und eine Uhrzeit eingeben, indem sie [CQ.Ext.form.DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.DateField) und [CQ.Ext.form.TimeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TimeField) miteinander kombinieren.

* Dialogfeld

  [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Dialog)

  Ein spezielles Dialogfeld mit einem Formular im Hauptteil und einer Schaltflächengruppe in der Fußzeile. Es wird in der Regel zum Bearbeiten von Inhalten verwendet, kann aber auch nur zur Anzeige von Informationen genutzt werden.

* dialogfieldset

  [CQ.form.DialogFieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.DialogFieldSet)

  DialogFieldSet ist ein [FieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.FieldSet) zur Verwendung in [Dialogfeldern](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Dialog).

* directstore

  [CQ.Ext.data.DirectStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.DirectStore)

  Eine kleine Helper-Klasse zum Erstellen von [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Store), konfiguriert mit einem [CQ.Ext.data.DirectProxy](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.DirectProxy) und [CQ.Ext.data.JsonReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.JsonReader), um die Interaktion mit einem Server-seitigen [CQ.Ext.Direct](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Direct)-[Provider](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.direct.Provider) zu erleichtern.

* displayField

  [CQ.Ext.form.DisplayField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.DisplayField)

  Ein nur für die Anzeige bestimmtes Textfeld, das nicht validiert und gesendet wird.

* editbar

  [CQ.wcm.EditBar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.EditBar)

  Mit EditBar können Benutzer mithilfe von Schaltflächen in einer Leiste Inhalte bearbeiten.

  Obwohl hier nicht aufgeführt, enthält EditBar alle Mitglieder von [CQ.wcm.EditBase](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.EditBase).

* editor

  [CQ.Ext.Editor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Editor)

  Ein allgemeines Editor-Feld für die Anzeige bzw. das Ausblenden nach Bedarf, mit integrierter Logik für Größenänderung und Ereignisbehandlung.

* editorgrid

  [CQ.Ext.grid.EditorGridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.EditorGridPanel)

  Diese Klasse erweitert die [GridPanel-Klasse](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GridPanel), um die Bearbeitung von Zellen in ausgewählten [Spalten](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.Column) zu ermöglichen. Die bearbeitbaren Spalten werden durch Angabe eines [Editors](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.ColumnModel) in der [Spaltenkonfiguration](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.Column) festgelegt.

* editrollover

  [CQ.wcm.EditRollover](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.EditRollover)

  Mit EditRollover können Benutzende Inhalte durch Doppelklick bearbeiten und über ein Kontextmenü weitere Bearbeitungsaktionen durchführen. Der bearbeitbare Bereich wird durch einen Rahmen gekennzeichnet, wenn die Maus über den Inhalt bewegt wird.

* feedimporter

  [CQ.wcm.FeedImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.FeedImporter)

  Mit FeedImporter können Benutzer RSS- oder Atom-Feeds importieren und Seiten für jeden Feed-Eintrag erstellen.

* field

  [CQ.Ext.form.Field](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Field)

  Eine allgemeine Klasse für Formularfelder, die Standardfunktionen für die Ereignisbehandlung, Größenänderung, Werteverarbeitung und anderes bereitstellt.

* fieldset

  [CQ.Ext.form.FieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.FieldSet)

  Ein Standard-Container zum Gruppieren von Elementen in einem [Formular](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.FormPanel).

* fileuploaddialogbutton

  [CQ.form.FileUploadDialogButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.FileUploadDialogButton)

  FileUploadDialogButton erstellt eine Schaltfläche, die ein neues Dialogfeld zum Hochladen einer Datei über das FileUploadField öffnet. Kann in Bearbeitungsdialogfeldern verwendet werden, in denen der Upload in einem separaten Formular erfolgen muss.

* fileuploadfield

  [CQ.form.FileUploadField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.FileUploadField)

  Mit FileUploadField können Benutzer eine einzelne Datei zum Hochladen auswählen.

* findreplacedialog

  [CQ.wcm.FindReplaceDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.FindReplaceDialog)

  FindReplaceDialog ist ein Dialogfeld zum Suchen nach und Ersetzen von Tokens in einer Seite und deren untergeordneten Seiten.

* flash

  [CQ.Ext.FlashComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.FlashComponent)

* grid

  [CQ.Ext.grid.GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)

  Diese Klasse stellt die primäre Oberfläche eines komponentenbasierten Raster-Steuerelements dar, um Daten im Tabellenformat in Zeilen und Spalten darzustellen.

* groupingstore

  [CQ.Ext.data.GroupingStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.GroupingStore)

  Eine spezielle Speicherimplementierung zum Gruppieren von Datensätzen nach einem der verfügbaren Felder. Dies wird mit einer [CQ.Ext.grid.GroupingView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GroupingView) verwendet, um das Datenmodell für ein gruppiertes GridPanel zu bestätigen.

* heavymovedialog

  [CQ.wcm.HeavyMoveDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.HeavyMoveDialog)

  HeavyMoveDialog ist ein Dialogfenster zum Verschieben einer Seite und der untergeordneten Seiten, einschließlich erneuter Aktivierung zuvor aktivierter Seiten („große“ Verschiebung).

* hidden

  [CQ.Ext.form.Hidden](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Hidden)

  Ein allgemeines verborgenes Feld zum Speichern ausgeblendeter Werte in Formularen, die beim Senden des Formulars weitergegeben werden müssen.

* historybutton

  [CQ.HistoryButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.HistoryButton)

  HistoryButton ist eine kleine Helper-Klasse für die einfache Bereitstellung der Schaltflächen „Vorwärts“ und „Zurück“. Normalerweise sind zwei verwandte Instanzen erforderlich: Die Instanz für die Schaltfläche „Vorwärts“ ist eine einfache Schaltfläche, die mit der Instanz für die Schaltfläche „Zurück“ verknüpft ist, die den Verlauf handhabt.

* htleditor

  [CQ.Ext.form.HtmlEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor)

  Stellt eine einfache HTML-Editor-Komponente bereit. Einige Symbolleistenfunktionen werden von Safari nicht unterstützt und bei Bedarf automatisch ausgeblendet. Diese werden gegebenenfalls in den Konfigurationsoptionen angegeben.

  Für die Schaltflächen in der Editor-Symbolleiste sind in der [buttonTips](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor)-Eigenschaft QuickInfos definiert.

* iframedialog

  [CQ.IframeDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.IframeDialog)

  Ein einfaches Dialogfeld, das die Inhalte eines iFrame anzeigt und Formulare in iFrames zulässt.

* iframepanel

  [CQ.IframePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.IframePanel)

  Ein Feld mit einem iFrame. Es ermöglicht die einfache Erstellung von iFrames, ein iFrame-Ladeereignis und einfachen Zugriff auf den iFrame-Inhalt.

* inlinetextfield

  [CQ.form.InlineTextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.InlineTextField)

  InlineField ist ein Textfeld, das als Beschriftung angezeigt wird, wenn es sich nicht im Fokus befindet.

* jsonstore

  [CQ.Ext.data.JsonStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.JsonStore)

  Eine kleine Helferklasse, die das Erstellen von [CQ.Ext.data.Stores](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Store) aus JSON-Daten erleichtert. Ein JsonStore wird automatisch mit einem [CQ.Ext.data.JsonReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.JsonReader) konfiguriert.

* label

  [CQ.Ext.form.Label](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Label)

  Ein einfaches Beschriftungsfeld.

* languagecopydialog

  [CQ.wcm.LanguageCopyDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.LanguageCopyDialog)

  LanguageCopyDialog ist ein Dialogfeld zum Kopieren von Sprachstrukturen.

* linkchecker

  [CQ.wcm.LinkChecker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.LinkChecker)

  LinkChecker ist ein Tool zum Überprüfen externer Links in einer Site.

* listview

  [CQ.Ext.list.ListView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.ListView)

  CQ.Ext.list.ListView ist eine schnelle, einfache Implementierung einer [rasterähnlichen](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) Ansicht.

* livecopyproperties

  [CQ.wcm.msm.LiveCopyProperties](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.LiveCopyProperties)

  LiveCopyProperties stellt ein Bedienfeld zum Anzeigen und Bearbeiten von Live Copy-Eigenschaften („Beziehungsvererbung“, „Synchronisierungsauslöser“ und „Aktionen synchronisieren“) bereit.

* lvbooleancolumn

  [CQ.Ext.list.BooleanColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.BooleanColumn)

  Eine Spaltendefinitionsklasse, die boolesche Datenfelder rendert. Weitere Informationen finden Sie unter [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column)-Konfigurationsoptionen von [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column).

* lvcolumn

  [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column)

  Diese Klasse kapselt Konfigurationsdaten von Spalten, die bei der Initialisierung von [ListView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.ListView) verwendet werden sollen.

* lvdatecolumn

  [CQ.Ext.list.DateColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.DateColumn)

  Eine Spaltendefinitionsklasse, die ein übergebenes Datum gemäß dem Standardgebietsschema oder einem konfigurierten [Format](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.DateColumn) rendert. Weitere Informationen finden Sie unter [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column)-Konfigurationsoptionen von [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column).

* lvnumbercolumn

  [CQ.Ext.list.NumberColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.NumberColumn)

  Eine Spaltendefinitionsklasse, die ein numerisches Datenfeld gemäß einer [Format](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.NumberColumn)-Zeichenfolge rendert. Weitere Informationen finden Sie unter [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column)-Konfigurationsoptionen von [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column).

* mediabrowsedialog

  [CQ.MediaBrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.MediaBrowseDialog)

  **Veraltet: Verwenden Sie stattdessen [Content Finder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.ContentFinder), um Medien zu durchsuchen.**

  MediaBrowseDialog ist ein Dialogfeld zum Durchsuchen der Medienbibliothek.

* menu

  [CQ.Ext.menu.Menu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.Menu)

  Ein Menüobjekt. Dies ist der Container, dem Sie Menüelemente hinzufügen können. „Menu“ kann auch als Basisklasse dienen, wenn Sie ein spezielles Menü benötigen, das auf einer anderen Komponente (z. B. [CQ.Ext.menu.DateMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.DateMenu)) basiert.

  Menüs können entweder [Menu-Elemente](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.Item) oder allgemeine [Komponenten](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Component) enthalten.

* menubaseitem

  [CQ.Ext.menu.BaseItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.BaseItem)

  Die allgemeine Klasse für alle in Menüs gerenderten Elemente. „BaseItem“ stellt Optionen für das Standard-Rendering, die Verwaltung in aktiviertem Zustand und die Basiskonfiguration bereit, die von allen Menükomponenten gemeinsam verwendet werden.

* menucheckitem

  [CQ.Ext.menu.CheckItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.CheckItem)

  Fügt ein Menüelement hinzu, das standardmäßig ein Kontrollkästchen enthält, aber auch Teil einer Optionsfeldgruppe sein kann.

* menuitem

  [CQ.Ext.menu.Item](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.Item)

  Eine Basisklasse für alle Menüelemente, für die menübezogene Funktionen (wie Untermenüs) erforderlich sind und bei denen es sich nicht um statische Anzeigeelemente handelt. „Item“ erweitert die allgemeinen Funktionen von [CQ.Ext.menu.BaseItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.BaseItem) und fügt die menüspezifische Bearbeitung von Aktivierungs- und Klickaktionen hinzu.

* menuseparator

  [CQ.Ext.menu.Separator](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.Separator)

  Fügt eine Leiste mit Trennzeichen zu einem Menü hinzu, die zum Trennen logischer Gruppen von Menüelementen verwendet werden. Normalerweise fügen Sie eines dieser Zeichen mit „-“ im Aufruf von add() oder der Elementkonfiguration hinzu, anstatt das Zeichen direkt zu erstellen.

* menutextitem

  [CQ.Ext.menu.TextItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.TextItem)

  Fügt eine statische Textzeichenfolge zu einem Menü hinzu und wird entweder als Überschrift oder als Gruppentrennzeichen verwendet.

* Metadaten

  [CQ.dam.form.Metadata](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.dam.form.Metadata)

  MetaData stellt Felder zum Bestimmen der für ein Metadatenfeld erforderlichen Informationen bereit (z. B. auf Asset-Editor-Seiten).

  Die Klasse enthält die folgenden Felder:

* multifield

  [CQ.form.MultiField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.MultiField)

  MultiField ist eine bearbeitbare Liste von Formularfeldern zum Bearbeiten von Eigenschaften mit mehreren Werten.

* mvt

  [CQ.form.MVT](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.MVT)

  Die Komponente „Multivariate Testing“ kann verwendet werden, um eine Reihe von Bildern zu definieren und zu bearbeiten, die als alternierende Banner dargestellt werden. Klickratenstatistiken werden pro Banner erfasst.

* notificationinbox

  [CQ.wcm.NotificationInbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.NotificationInbox)

  Mit NotificationInbox können Benutzer WCM-Aktionen abonnieren und Benachrichtigungen verwalten.

* numberfield

  [CQ.Ext.form.NumberField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.NumberField)

  Ein numerisches Textfeld, das automatisch Tastenanschläge filtert und numerische Werte validiert.

* offlineimporter

  [CQ.wcm.OfflineImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.OfflineImporter)

  OfflineImporter ist ein Tool zum Importieren und Konvertieren von Microsoft® Word-Dokumenten in AEM-Seiten. Mit dieser Funktion können Inhalte mithilfe eines Textverarbeitungsgeräts offline bearbeitet werden.

* ownerdraw

  [CQ.form.OwnerDraw](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.OwnerDraw)

  OwnerDraw kann benutzerdefinierten HTML-Code enthalten (der entweder direkt eingegeben oder von einer URL abgerufen wurde).

* paging

  [CQ.Ext.PagingToolbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.PagingToolbar)

  Mit einer steigenden Anzahl von Einträgen steigt auch die vom Browser zum Rendern benötigte Zeit. Paging wird verwendet, um die Datenmenge zu reduzieren, die mit dem Client ausgetauscht wird.

* panel

  [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Panel)

  „Panel“ ist ein Container mit spezifischen Funktionen und Strukturkomponenten und ist ideal als Baustein für anwendungsorientierte Benutzeroberflächen geeignet.

  Felder werden vom [CQ.Ext.Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Container) vererbt.

* paragraphreference

  [CQ.form.ParagraphReference](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.ParagraphReference)

  Das Feld „ParagraphReference“ ermöglicht es, Seiten zu durchsuchen und einen der darin enthaltenen Absätze auszuwählen. Es beinhaltet ein Auslöserfeld und ein damit verknüpftes Dialogfeld zum Durchsuchen von Absätzen.

* Kennwort

  [CQ.form.Password](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.Password)

   „Password“ ist einem [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TextField) ähnlich, die darin enthaltenen Werte bleiben jedoch privat, sodass Benutzer vertrauliche Daten eingeben können.

* pathcompletion

  [CQ.form.PathCompletion](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.PathCompletion)

  **Veraltet: Verwenden Sie stattdessen [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.PathField).**

* pathfield

  [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.PathField)

  „PathField“ ist ein Eingabefeld für Pfade mit Pfadvervollständigung und einer Schaltfläche zum Öffnen eines [CQ.BrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.BrowseDialog) zum Durchsuchen des Server-Repositorys. Damit können auch Seitenabsätze zur erweiterten Link-Erzeugung durchsucht werden.

* Fortschritt

  [CQ.Ext.ProgressBar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ProgressBar)

  Eine Komponente mit einer Fortschrittsleiste, die aktualisiert werden kann. Die Fortschrittsleiste unterstützt zwei verschiedene Modi: manuell und automatisch.

  Im manuellen Modus sind Sie für das Anzeigen, Aktualisieren (über [updateProgress](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ProgressBar)) und Löschen der Fortschrittsleiste nach Bedarf über Ihren eigenen Code verantwortlich. Diese Methode eignet sich am besten, wenn Sie den Fortschritt anzeigen möchten.

* propertygrid

  [CQ.Ext.grid.PropertyGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.PropertyGrid)

  Eine spezielle Rasterimplementierung, die das herkömmliche Eigenschaftenraster nachahmen soll, das normalerweise in Entwicklungs-IDEs verwendet wird. Jede Zeile im Raster steht für eine Eigenschaft eines Objekts; die Daten werden in Namen-Wert-Paaren in [CQ.Ext.grid.PropertyRecord](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.PropertyRecord) gespeichert.

* propgrid

  [CQ.PropertyGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.PropertyGrid)

  PropertyGrid ist ein generisches Raster, das zum Anzeigen und Bearbeiten von Objekteigenschaften verwendet wird.

* quicktip

  [CQ.Ext.QuickTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.QuickTip)

  @xtype quicktip. Eine spezielle QuickInfo-Klasse für QuickInfos, die im Markup angegeben und automatisch von der globalen [CQ.Ext.QuickTips](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.QuickTips)-Instanz verwaltet werden können. Zusätzliche Informationen zur Verwendung und Beispiele finden Sie unter dem Header „QuickTips-Klasse“.

* radio

  [CQ.Ext.form.Radio](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Radio)

  Ein einzelnes Optionsfeld Ähnlich wie das Kontrollkästchen, der Eingabetyp kann jedoch für die einfache Verwendung automatisch festgelegt werden. Die Gruppierung von Optionsfeldern erfolgt automatisch im Browser, falls alle Optionsfelder einer Gruppe gleich benannt werden.

* radiogroup

  [CQ.Ext.form.RadioGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.RadioGroup)

  Ein Gruppierungscontainer für [CQ.Ext.form.Radio](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Radio)-Steuerelemente.

* referencesdialog

  [CQ.wcm.ReferencesDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.ReferencesDialog)

  ReferencesDialog ist ein Dialogfeld zum Anzeigen von Verweisen auf einer Seite.

* restoretreedialog

  [CQ.wcm.RestoreTreeDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.RestoreTreeDialog)

  RestoreTreeDialog ist ein Dialogfeld zum Wiederherstellen einer vorherigen Version einer Struktur.

* restoreversiondialog

  [CQ.wcm.RestoreVersionDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.RestoreVersionDialog)

  RestoreVersionDialog ist ein Dialogfeld zum Wiederherstellen einer vorherigen Version einer Seite.

* richtext

  [CQ.form.RichText](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.RichText)

  „RichText“ stellt ein Formularfeld zum Bearbeiten von formatierten Textinformationen (Rich Text) zur Verfügung.

  Die RichText-Komponente bietet derzeit die folgenden Funktionen:

* rolloutplan

  [CQ.wcm.msm.RolloutPlan](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan)

  RolloutPlan stellt ein Dialogfeld zum Überwachen des Rollout-Fortschritts einer Seite bereit. „RolloutPlan“ wird von einem [CQ.wcm.msm.RolloutWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard) gestartet.

* rolloutwizard

  [CQ.wcm.msm.RolloutWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard)

  RolloutWizard stellt einen Assistenten für das Rollout einer Seite bereit. „RolloutWizard“ startet einen [CQ.wcm.msm.RolloutPlan](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan).

* searchfield

  [CQ.form.SearchField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.SearchField)

  SearchField ist ein Suchfeld, das die Ergebnisse in einer Dropdown-Liste bereitstellt, die zum Durchsuchen des Repositorys verwendet werden kann.

* selection

  [CQ.form.Selection](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.Selection)

  Mit „Selection“ können Benutzer aus mehreren Optionen auswählen. Die Optionen können Teil der Konfiguration sein oder aus einer JSON-Antwort geladen werden. „Selection“ kann entweder als Dropdown-Menü (Auswahl) oder als Kombinationsfeld (Auswahl plus freie Texteingabe) gerendert werden.

* sidekick

  [CQ.wcm.Sidekick](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.Sidekick)

  Der „Sidekick“ ist ein unverankerter Hilfsdienst, in dem gängige Tools zur Seitenbearbeitung bereitgestellt werden.

* siteadmin

  [CQ.wcm.SiteAdmin](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.SiteAdmin)

  SiteAdmin ist eine Konsole mit WCM-Administrationsfunktionen.

* siteimporter

  [CQ.wcm.SiteImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.SiteImporter)

  Mit SiteImporter können Benutzer komplette Websites importieren und erste Projekte erstellen.

* sizefield

  [CQ.form.SizeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.SizeField)

  Mit SizeField können Benutzende die Breite und Höhe (z. B. eines Bildes) eingeben.

* slider

  [CQ.Ext.Slider](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Slider)

  Ein Regler für die vertikale und horizontale Ausrichtung, Tastaturanpassungen, konfigurierbare Ausrichtungen, Achsenklicks und Animationen. Kann als Element zu jedem Container hinzugefügt werden. Anwendungsbeispiel: ...

* slideshow

  [CQ.form.Slideshow](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.Slideshow)

  „Slideshow“ stellt eine Komponente bereit, die zum Definieren und Bearbeiten von Bildern und Bildtiteln verwendet werden kann, die möglicherweise in einer Bildschirmpräsentation angezeigt werden.

  Die Komponente für die Bildschirmpräsentation basiert auf der Komponente [CQ.form.SmartImage](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.SmartImage).

* smartfile

  [CQ.form.SmartFile](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.SmartFile)

  „SmartFile“ ist ein intelligenter Datei-Uploader.

  Wenn ein Flash-Plug-in (Version 9 oder höher) installiert ist, werden Uploads mit der SWFupload-Bibliothek durchgeführt, was eine benutzerfreundliche Upload-Methode darstellt.

* smartimage

  [CQ.form.SmartImage](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.SmartImage)

  SmartImage ist ein intelligenter Bild-Uploader, der Tools zum Verarbeiten von hochgeladenen Bildern bereitstellt, beispielsweise ein Definitions-Tool für Bildzuordnungen und einen Bildzuschneider.

  Die Komponente ist für die Verwendung auf einer separaten Dialogfeld-Registerkarte bestimmt.

* spacer

  [CQ.Ext.Spacer](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Spacer)

  Wird verwendet, um einen anpassbaren Bereich in einem Layout bereitzustellen.

* spinner

  [CQ.form.Spinner](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.Spinner)

  „Spinner“ ist ein Auslöserfeld für numerische, Daten- oder Zeitwerte. Der Wert kann mit den bereitgestellten Aufwärts- und Abwärts-Auslösern, dem Scroll-Rad oder den Tasten erhöht und verringert werden.

* splitbutton

  [CQ.Ext.SplitButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.SplitButton)

   Eine unterteilte Schaltfläche, die einen integrierten Abwärtspfeil bereitstellt, der ein Ereignis separat zu einem Standard-Klick-Ereignis der Schaltfläche auslösen kann. Sie wird in der Regel verwendet, um ein Dropdown-Menü anzuzeigen, das zusätzliche Optionen zur Hauptaktion der Schaltfläche bereitstellt. Jeder benutzerdefinierte Handler kann jedoch den Pfeilklick implementieren.

* static

  [CQ.Static](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Static)

  Mit „Static“ kann beliebiger Text oder HTML angezeigt werden.

* Statistiken

  [CQ.wcm.Statistics](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.Statistics)

   „Statistics“ zeigt die Seitenimpressionen als Diagramm an. Das Widget ermöglicht die Auswahl eines Zeitraums, für den die Statistiken angezeigt werden sollen.

* store

  [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Store)

  Die Store-Klasse kapselt einen Client-seitigen Cache der [Datensatz](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Record)-Objekte, die Eingabedaten für die Komponenten [GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GridPanel), [ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.ComboBox) oder [DataView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.DataView) liefern.

* suggestfield

  [CQ.form.SuggestField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.SuggestField)

  SuggestField macht Benutzenden Vorschläge auf Basis ihrer Eingaben.

* switcher

  [CQ.Switcher](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Switcher)

   „Switcher“ stellt eine Gruppe von Schaltflächen für die Kopfzeilenleiste in einer Konsole bereit, mit denen Benutzer zwischen Websites, digitalen Assets, Tools, Workflows und Sicherheit wechseln können.

* tableedit

  [CQ.form.TableEdit](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.TableEdit)

  **Veraltet: Verwenden Sie stattdessen [CQ.form.TableEdit2.](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.TableEdit2)**

* tableedit2

  [CQ.form.TableEdit2](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.TableEdit2)

  „TableEdit2“ stellt ein Widget zum Erstellen von Tabellen bereit.

* tabpanel

  [CQ.Ext.TabPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.TabPanel)

  Ein allgemeiner Container für Registerkarten. TabPanels kann zu Layout-Zwecken genauso wie ein standardmäßiges [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Panel) verwendet werden, verfügt aber auch über spezielle Unterstützung für darin enthaltene untergeordnete Komponenten ([`items` ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Container)).

* tags

  [CQ.tagging.TagInputField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.tagging.TagInputField)

  ```
  CQ.tagging.TagInputField
  ```

  ist ein Formular-Widget zum Eingeben von Tags. Es beinhaltet ein Popup-Menü für die Auswahl vorhandener Tags, einschließlich Autovervollständigen und vieler anderer Funktionen.

* textarea

  [CQ.Ext.form.TextArea](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TextArea)

  Ein mehrere Zeilen umspannendes Textfeld. Kann als direkter Ersatz für herkömmliche textarea-Felder verwendet werden und unterstützt auch die automatische Größenänderung.

* textbutton

  [CQ.TextButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.TextButton)

  TextButton stellt einen Textlink mit den Funktionen einer [CQ.Ext.Button](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Button) bereit.

* textfield

  [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TextField)

  Ein einfaches Textfeld. Kann als direkter Ersatz für herkömmliche Texteingaben oder als allgemeine Klasse für komplexere Eingabeelemente (wie [CQ.Ext.form.TextArea](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TextArea) und [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.ComboBox)) verwendet werden.

* thumbnail

  [CQ.form.Thumbnail](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.Thumbnail)

* timefield

  [CQ.Ext.form.TimeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TimeField)

  Stellt ein Zeiteingabefeld mit einem Zeit-Dropdown-Menü und automatischer Zeitvalidierung bereit. Anwendungsbeispiel: ...

* tip

  [CQ.Ext.Tip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Tip)

  @xtype tip. Dieses ist die allgemeine Klasse für [CQ.Ext.QuickTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.QuickTip) und [CQ.Ext.Tooltip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Tooltip), die das grundlegende Layout und die Platzierung bereitstellt, die für alle Klassen mit QuickInfo erforderlich sind. Diese Klasse kann direkt für einfache, statisch platzierte QuickInfos verwendet werden.

* titleseparator

  [CQ.menu.TitleSeparator](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.menu.TitleSeparator)

  Fügt eine Leiste mit Trennzeichen zu einem Menü hinzu, die zum Trennen logischer Gruppen von Menüelementen verwendet werden. Das Trennzeichen kann auch einen Titel aufweisen.

* toolbar

  [CQ.Ext.Toolbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Toolbar)

  Eine allgemeine Klasse für Symbolleisten. Der [`defaultType`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Container) für die Toolbar-Klasse ist zwar [`button`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Button), Toolbar-Elemente (untergeordnete Elemente für den toolbar-Container) können jedoch praktisch jeden Komponententyp umfassen. Symbolleistenelemente können explizit über ihre Konstruktoren erstellt werden.

* QuickInfo

  [CQ.Ext.ToolTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ToolTip)

  Eine Standardimplementierung für QuickInfos, die zusätzliche Informationen beim Zeigen auf ein Zielelement bereitstellt. @xtype tooltip.

* treegrid

  [CQ.tree.TreeGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.tree.TreeGrid)

  @xtype-Treegrid

* treepanel

  [CQ.Ext.tree.TreePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)

  „TreePanel“ ermöglicht das Anzeigen von Baumstruktur-Daten in einer Baumstruktur-Benutzeroberfläche.

  Zu TreePanel hinzugefügte [TreeNode](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.tree.TreeNode)s können Metadaten enthalten, die von der Anwendung in der Eigenschaft [attributes](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.tree.TreeNode) verwendet werden.

* trigger

  [CQ.Ext.form.TriggerField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TriggerField)

  Stellt einen benutzerfreundlichen Wrapper für TextFields bereit, der eine klickbare Auslöserschaltfläche hinzufügt (ähnelt einem Standard-Kombinationsfeld). Für den Auslöser gibt es keine Standardaktion. Sie müssen eine Funktion zuweisen, um den Klick-Handler für den Auslöser durch Überschreiben von [onTriggerClick](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TriggerField) zu implementieren. Sie können ein TriggerField direkt erstellen, da es genauso wie ein Kombinationsfeld gerendert wird.

* uploaddialog

  [CQ.UploadDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.UploadDialog)

  Mit UploadDialog können Benutzer Dateien ins Repository hochladen. Erstellt einen neuen UploadDialog.

* userinfo

  [CQ.UserInfo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.UserInfo)

  Ein Element der Symbolleiste, das den aktuellen Benutzernamen anzeigt und Benutzeraktionen wie das Bearbeiten von Benutzereigenschaften und die Personifikation ermöglicht.

* viewport

  [CQ.Ext.Viewport](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Viewport)

  Ein spezieller Container, der den sichtbaren Anwendungsbereich (das Browser-Darstellungsfeld) darstellt.

  „Viewport“ wird automatisch im Hauptteil des Dokuments gerendert. Die Größe wird automatisch an das Browser-Darstellungsfeld angepasst und die Größenänderung des Fensters verwaltet. Es kann nur ein Viewport erstellt werden.

* window

  [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window)

  Ein spezielles Bedienfeld, das als Anwendungsfenster verwendet werden soll. Fenster sind standardmäßig nicht verankert, [anpassbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window) und per Maus [ziehbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window). Fenster können auf die Größe des Darstellungsfelds [maximiert](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window), auf die ursprüngliche Größe zurückgesetzt oder [minimiert](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window) werden.

* xmlstore

  [CQ.Ext.data.XmlStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.XmlStore)

  Eine kleine Helferklasse, die das Erstellen von [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Store)aus XML-Daten erleichtert. XmlStore wird automatisch mit einem [CQ.Ext.data.XmlReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.XmlReader) konfiguriert.

  **Cqinclude>**: Ein Pseudo-xtype, das Widget-Definitionen aus unterschiedlichen Pfaden im Repository enthält. Es wird in der Regel in Seitendialogfeldern verwendet. Für diesen xtype gibt es keine tatsächliche JavaScript-Widget-Klasse. Es wird durch die formatData()-Funktion der CQ.Util-Klasse verarbeitet. Weitere Informationen finden Sie in diesem Knowledge Base-Artikel.
