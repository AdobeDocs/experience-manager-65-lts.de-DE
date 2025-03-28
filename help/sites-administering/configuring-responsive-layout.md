---
title: Konfigurieren von Layout-Container und Layout-Modus
description: Erfahren Sie, wie Sie Layout-Container und den Layout-Modus konfigurieren.
topic-tags: operations
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Operations
role: Admin
exl-id: 413f15c9-5b51-4d8d-8cf0-3e98608b9d9e
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1389'
ht-degree: 100%

---

# Konfigurieren von Layout-Container und Layout-Modus{#configuring-layout-container-and-layout-mode}

Erfahren Sie, wie Sie Layout-Container und den Layout-Modus konfigurieren.

>[!TIP]
>
>Dieses Dokument bietet einen Überblick über das responsive Design für Site-Admins und Entwickelnde, die beschreiben, wie Funktionen in AEM umgesetzt werden.
>
>Informationen zur Verwendung responsiver Design-Funktionen auf einer Inhaltsseite für Inhaltsautorinnen und -autoren finden Sie im Dokument [Responsives Layout für Ihre Inhaltsseiten](/help/sites-authoring/responsive-layout.md).

## Überblick {#overview}

Ein [responsives Layout](/help/sites-authoring/responsive-layout.md) ist eine Methode, um ein [responsives Webdesign](https://de.wikipedia.org/wiki/Responsive_Webdesign) zu realisieren. Damit lassen sich Web-Seiten erstellen, deren Layout und Abmessungen von dem Gerät des Benutzers abhängen.

Das responsive Layout für Ihre Seiten wird von AEM durch eine Kombination von Mechanismen ermöglicht:

* [**Layout-Container-Komponente**](/help/sites-authoring/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode)

  Diese Komponente stellt ein Rasterabsatzsystem zur Verfügung, mit dem Sie Komponenten in einem responsiven Raster hinzufügen und positionieren können. Sie können sie als Standard-ParSys für Ihre Seite nutzen und/oder sie anderen Autoren im Komponenten-Browser zur Verfügung stellen.

   * Die standardmäßige **Layout-Container**-Komponente ist definiert unter:

     /libs/wcm/foundation/components/responsivegrid

   * Sie können Layout-Container definieren:

      * als Komponente, die Benutzerinnen und Benutzer einer Seite hinzufügen können.
      * als Standard-Absatzsystem für die Seite.
      * Beide.

        Sie können den Layout-Container als Standard für die Seite festlegen und es den Benutzern gleichzeitig erlauben, weitere Layout-Container darin hinzuzufügen, z. B. für die Spaltensteuerung.

* **[Layout-Modus](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)**
Sobald der Layout-Container auf der Seite positioniert ist, können Sie im **Layout**-Modus Inhalte im responsiven Raster positionieren.

* [**Emulator**](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate)
Auf diese Weise können Sie responsive Websites erstellen und bearbeiten, deren Layout sich durch interaktive Größenanpassung der Komponenten an die Geräte-/Fenstergröße anpasst. Die Benutzerin bzw. der Benutzer kann dann mit dem Emulator sehen, wie der Inhalt wiedergegeben wird.

Mit diesen responsiven Rastermechanismen können Sie:

* Breakpoints verwenden (die die Gerätegruppierung angeben), um je nach Geräte-Layout ein unterschiedliches Inhaltsverhalten zu definieren.
* Komponenten basierend auf Gerätegruppen ausblenden (d. h. definieren, an welchem Breakpoint eine Komponente ausgeblendet wird).
* Horizontales Einrasten am Raster verwenden (Komponenten im Raster platzieren, die Größe nach Bedarf ändern oder definieren, wann ein Reduzieren/Umfließen erfolgen soll, damit sie nebeneinander oder über-/untereinander angeordnet werden).
* Realisieren einer Spaltensteuerung.

>[!TIP]
>
>Adobe stellt eine [GitHub-Dokumentation](https://adobe-marketing-cloud.github.io/aem-responsivegrid/) zum responsiven Layout als Referenz bereit. Diese kann Frontend-Entwickelnden zur Verfügung gestellt werden, damit sie das AEM-Raster außerhalb von AEM verwenden können, um beispielsweise statische HTML-Modelle für künftige AEM-Sites zu erstellen.

>[!NOTE]
>
>Bei einer vorab konfigurierten Installation wurde das responsive Layout für die [We.Retail-Referenzwebsite](/help/sites-developing/we-retail.md) konfiguriert. [Aktivieren Sie die Layout-Container-Komponente](#enable-the-layout-container-component-for-page) für andere Seiten.

>[!CAUTION]
>
>Auch wenn die **Layout-Container**-Komponente in der klassischen Benutzeroberfläche verfügbar ist, steht der vollständige Funktionsumfang nur in der Touch-optimierten Benutzeroberfläche zur Verfügung.

## Aktivieren des Layout-Modus für die Website {#activate-layout-mode-for-your-site}

Mit diesen Vorgängen wird der **Layout-Modus** auf Ihrer Website aktiviert.

### Konfigurieren der Haltepunkte {#configure-the-breakpoints}

[Haltepunkte](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate):

* Werden im responsiven Design verwendet.
* Können definiert werden:

   * auf der Seitenvorlage, von der aus die Einstellungen auf alle Seiten kopiert werden, die mit dieser Vorlage erstellt wurden
   * auf dem Seitenknoten, von dem aus die Einstellungen von allen untergeordneten Seiten übernommen werden.

* Legen Sie einen Titel und eine Breite fest:

   * Der Titel beschreibt die generische Gerätegruppierung, gegebenenfalls mit Ausrichtung, z. B. Smartphone, Tablet, Tablet-horizontal.
   * Die Breite definiert die maximale Breite in Pixeln für diese generische Gerätegruppierung. Wenn der Telefon-Breakpoint beispielsweise eine Breite von 768 hat, dann ist dies die maximale Breite des Layouts, das für ein Telefongerät verwendet wird.

* Sind als Markierungen am oberen Rand des Seiten-Editors sichtbar, wenn Sie den Emulator verwenden.
* Werden von der Hierarchie des übergeordneten Knotens übernommen und können beliebig überschrieben werden.
* Es gibt einen standardmäßigen (nativen) Breakpoint, der alles oberhalb des letzten *konfigurierten* Breakpoints abdeckt.

Haltepunkte können Sie mit CRXDE Lite oder XML definieren.

>[!NOTE]
>
>Wenn Sie ein neues Projekt einrichten:
>
>* Fügen Sie Breakpoints zu den Vorlagen hinzu.
>
>Wenn Sie ein vorhandenes Projekt (mit vorhandenem Inhalt) migrieren, müssen Sie:
>
>* Breakpoints zu Vorlagen hinzufügen
>* dieselben Haltepunkte zu vorhandenen Seiten hinzufügen
>
>  Da die Vererbung im Einsatz ist, können Sie dies auf die Stammseite Ihrer Inhalte beschränken.

#### Konfigurieren von Breakpoints mithilfe von CRXDE Lite {#configuring-breakpoints-using-crxde-lite}

1. Navigieren Sie mit CRXDE Lite (o. ä.) zu einem der folgenden:

   * Ihrer Vorlagendefinition.
   * dem Knoten `jcr:content` Ihrer Seite

1. Erstellen Sie unter `jcr:content` den Knoten:

   * Name: `cq:responsive`
   * Typ: `nt:unstructured`

1. Erstellen Sie darunter den Knoten:

   * Name: `breakpoints`
   * Typ: `nt:unstructured`

1. Unter dem Breakpoints-Knoten können Sie eine beliebige Anzahl von Breakpoints erstellen. Jede Definition ist ein einzelner Knoten mit den folgenden Eigenschaften:

   * Name: `<descriptive name>`
   * Typ: `nt:unstructured`
   * Titel: `String` * `<descriptive title seen in Emulator>`*
   * Breite: `Decimal` * `<value of breakpoint>`*

#### Konfigurieren von Haltepunkten mit XML {#configuring-breakpoints-using-xml}

Haltepunkte befinden sich im Abschnitt `<jcr:content>` der Datei `.context.html` im entsprechenden Vorlagenorder (bzw. Inhaltsordner).

Eine Beispieldefinition:

```xml
<cq:responsive jcr:primaryType="nt:unstructured">
  <breakpoints jcr:primaryType="nt:unstructured">
    <phone jcr:primaryType="nt:unstructured" title="{String}Phone" width="{Decimal}768"/>
    <tablet jcr:primaryType="nt:unstructured" title="{String}Tablet" width="{Decimal}1200"/>
  </breakpoints>
</cq:responsive>
```

### Hinzufügen eines responsiven Informationsanbieters {#add-a-responsive-information-provider}

>[!NOTE]
>
>Dies ist nur erforderlich, wenn die Seitenkomponente nicht auf der Foundation-Seitenkomponente basiert.

Kopieren Sie die folgende `cq:infoProviders`-Knotenstruktur in die übergeordnete Seitenkomponente:

`/libs/foundation/components/page/cq:infoProviders/responsive`

## Aktivieren der Größenänderung von Komponenten für die Seite {#enable-component-resizing-for-the-page}

Sie müssen diese Vorgänge durchführen, um die Größe von Komponenten im **Layout-Modus** zu ändern.

### Festlegen des Layout-Containers als Haupt-Absatzsystem {#set-layout-container-as-main-parsys}

Um festzulegen, dass das Haupt-Absatzsystem Ihrer Seite ein Layout-Container sein sollen, definieren Sie die Absatzsysteme wie folgt:

`wcm/foundation/components/responsivegrid`

In entweder der:

* Seitenkomponente
* Seitenvorlage (zur zukünftigen Verwendung)

Die folgenden beiden Beispiele veranschaulichen die Definition:

* **HTL:**

  ```html
  <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
  ```

* **JSP:**

  ```html
  <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
  ```

### Einschließen von responsivem CSS {#include-the-responsive-css}

#### CSS für Breakpoints mit LESS {#css-for-breakpoints-using-less}

AEM verwendet LESS, um Teile des erforderlichen CSS zu generieren. Diese müssen für Ihre Projekte einbezogen werden.

Sie müssen auch eine [Client-Bibliothek](https://experienceleague.adobe.com/docs/?lang=de) erstellen, um zusätzliche Konfigurations- und Funktionsaufrufe bereitzustellen. Der folgende LESS-Extrakt ist ein Beispiel für das Minimum, das Sie zum Projekt hinzufügen müssen:

```css
@import (once) "/libs/wcm/foundation/clientlibs/grid/grid_base.less";

/* maximum amount of grid cells to be provided */
@max_col: 12;

/* default breakpoint */
.aem-Grid {
  .generate-grid(default, @max_col);
}

/* phone breakpoint */
@media (max-width: 768px) {
  .aem-Grid {
    .generate-grid(phone, @max_col);
  }
}

/* tablet breakpoint */
@media (min-width: 769px) and (max-width: 1200px) {
  .aem-Grid {
    .generate-grid(tablet, @max_col);
  }
}
```

Die Basisrasterdefinition finden Sie unter:

`/libs/wcm/foundation/clientlibs/grid/grid_base.less`

#### Überlegungen zur Gestaltung {#styling-considerations}

Die Größe von Komponenten in einem responsiven Container wird (zusammen mit den entsprechenden HTML-DOM-Elementen) entsprechend der Größe des responsiven Rasters geändert. Daher empfehlen wir in diesen Fällen, Definitionen von (enthaltenen) DOM-Elementen mit fester Breite zu vermeiden (oder zu aktualisieren).

Zum Beispiel:

* Vorher:

   * `width=100px`

* Nachher:

   * `max-width=100px`

#### Größenanpassung und adaptive Bildkompatibilität {#resizing-and-adaptive-image-compliance}

Jede Änderung der Größe einer Komponente innerhalb des Rasters löst mindestens einen der folgende Listener aus:

* `beforeedit`
* `beforechildedit`
* `afteredit`

* `afterchildedit`

Um die Größe eines adaptiven Bildes in einem responsiven Raster ordnungsgemäß zu ändern und die Inhalte des Bildes zu aktualisieren, müssen Sie den Listener `afterEdit`, dessen Wert auf `REFRESH_PAGE` festgelegt ist, zur `EditConfig`-Datei aller enthaltenen Komponenten hinzufügen.

Zum Beispiel:

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

Der Mechanismus für adaptive Bilder wird über ein Skript zur Verfügung gestellt, das die Auswahl des richtigen Bildes für die aktuelle Fenstergröße steuert. Es wird aktiviert, wenn das DOM bereit ist oder ein dediziertes Ereignis empfangen wird. Derzeit muss die Seite aktualisiert werden, um das Ergebnis der Benutzeraktion korrekt widerzuspiegeln.

>[!CAUTION]
>
>Benutzerdefinierte Stylesheet-ClientLibs müssen als Teil der Kopfzeile geladen werden, damit sie in der Autoren- und Veröffentlichungsumgebung ordnungsgemäß funktionieren.

## Aktivieren der Layout-Container-Komponente für die Seite {#enable-the-layout-container-component-for-page}

Mit diesen Aufgaben können Autorinnen und Autoren Instanzen der **Layout-Container**-Komponente auf die Seite verschieben.

### Aktivieren der Layout-Container-Komponente für die Seitenbearbeitung {#enable-the-layout-container-component-for-page-editing}

Damit Autorinnen und Autoren weitere responsive Raster zu den Inhaltsseiten hinzufügen können, müssen Sie die Layout-Container-Komponente für Ihre Seite aktivieren. Möglich ist dies über folgende Optionen:

* **Autorenumgebung**

  Verwenden Sie den [Design-Modus](/help/sites-authoring/default-components-designmode.md), um die **Layout-Container**-Komponente für eine Seite zu aktivieren.

* **Komponentendefinition**

  Nutzen Sie beim Definieren der Komponente `allowedComponent` oder ein Static Include.

### Konfigurieren des Rasters des Layout-Containers {#configure-the-grid-of-the-layout-container}

Sie können die Anzahl der verfügbaren Spalten für jede spezifische Instanz des Layout-Containers konfigurieren:

1. **Autorenumgebung**

   Sie können die Anzahl der verfügbaren Spalten für jede spezifische Instanz des Layout-Containers konfigurieren.

   Öffnen Sie dazu im [Design-Modus](/help/sites-authoring/default-components-designmode.md) das Design-Dialogfeld für den betroffenen Container. Hier können Sie festlegen, wie viele Spalten für die Positionierung und Größenanpassung verfügbar sein sollen. Der Standardwert lautet 12.

1. **XML**

   Definitionen für das responsive Raster finden Sie unter:

   `etc/design/<*your-project-name*>/.content.xml`

   Die folgenden Parameter können definiert werden:

   * Anzahl der verfügbaren Spalten:

      * `columns="{String}8"`

   * Komponenten, die zur aktuellen Komponente hinzugefügt werden können:

      * `components="[/libs/wcm/foundation/components/responsivegrid, ...`

## Verschachtelte responsive Raster {#nested-responsive-grids}

Gelegentlich ist es erforderlich, responsive Raster zu verschachteln, um die Anforderungen Ihres Projekts zu erfüllen. Beachten Sie jedoch, dass Adobe als Best Practice empfiehlt, die Struktur so flach wie möglich zu halten.

Wenn Sie die Verwendung verschachtelter responsiver Raster nicht vermeiden können, stellen Sie Folgendes sicher:

* Alle Container (Container, Registerkarten, Akkordeons usw.) haben die Eigenschaft `layout = responsiveGrid`.
* Mischen Sie nicht die Eigenschaft `layout = simple` in der Container-Hierarchie.

Dies betrifft alle strukturellen Container aus der Seitenvorlage.

Die Spaltenanzahl des inneren Containers darf nie größer sein als die des äußeren Containers. Das folgende Beispiel erfüllt diese Bedingung. Die Spaltenanzahl des äußeren Containers für den Standardbildschirm (Desktop) beträgt 8 und die des inneren Containers 4.

>[!BEGINTABS]

>[!TAB Beispiel einer Knoten-Struktur]

```text
container
  @layout = responsiveGrid
  cq:responsive
    default
      @offset = 0
      @width = 8
  container
  @layout = responsiveGrid
    cq:responsive
      default
        @offset = 0
        @width = 4
    text
      @text =" Text Column 1"
```

>[!TAB Beispiel des HTML-Ergebnisses]

```html
<div class="container responsivegrid aem-GridColumn--default--none aem-GridColumn aem-GridColumn--default--8 aem-GridColumn--offset--default--0">
  <div id="container-c9955c233c" class="cmp-container">
    <div class="aem-Grid aem-Grid--8 aem-Grid--default--8 ">
      <div class="container responsivegrid aem-GridColumn--default--none aem-GridColumn aem-GridColumn--offset--default--0 aem-GridColumn--default--4">
        <div id="container-8414e95866" class="cmp-container">
          <div class="aem-Grid aem-Grid--4 aem-Grid--default--4 ">
            <div class="text aem-GridColumn aem-GridColumn--default--4">
              <div data-cmp-data-layer="..." id="text-1234567890" class="cmp-text">
                <p>Text Column 1</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

>[!ENDTABS]
