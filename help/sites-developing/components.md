---
title: Komponentenübersicht
description: Bei Komponenten handelt es sich um modulare Einheiten, mit denen spezifische Funktionalität zum Darstellen von Inhalten auf Ihrer Website realisiert wird.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 364eebca-b4cf-470b-994e-9e56ec68597b
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 100%

---

# Komponentenübersicht{#components-overview}

Diese Seite enthält einen Überblick über die Komponenten von Adobe Experience Manager (AEM), z. B. für die [Seitenbearbeitung](/help/sites-authoring/default-components-foundation.md).

## Was sind Komponenten? {#what-exactly-is-a-component}

* Es sind modulare Einheiten, mit denen eine spezifische Funktionalität zum Darstellen von Inhalten auf Ihrer Website realisiert wird.
* Sind wiederverwendbar.
* Werden als eigenständige Einheiten innerhalb eines Ordners des Repositorys entwickelt.
* Verfügen nicht über ausgeblendete Konfigurationsdateien.
* Sie können andere Komponenten enthalten.
* Sie können überall in einem AEM-System ausgeführt werden. Sie können auch auf die Ausführung unter bestimmten Komponenten beschränkt werden.
* Verfügen über eine standardisierte Benutzeroberfläche.
* Verfügen über ein konfigurierbares Bearbeitungsverhalten.
* Verwenden Dialogfelder, die basierend auf Granite-UI-Komponenten mit Unterelementen erstellt werden
* Werden per [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de) (empfohlen) oder JSP entwickelt.
* Sie können für die Erstellung von angepassten Komponenten entwickelt werden, mit denen die Standardfunktionalität erweitert wird.

Da die Komponenten modular sind, haben Sie folgende Möglichkeiten:

* Entwickeln einer neuen Komponente auf Ihrer lokalen Instanz
* Bereitstellen dieser Komponente in Ihrer Testumgebung
* Bereitstellen in Ihrer Live-Authoring-Umgebung, in der Autoren bzw. Administratoren Inhalt hinzufügen und konfigurieren können
* Bereitstellen in Ihren Live-Veröffentlichungsumgebungen, in denen sie zum Rendern von Inhalten für Besucher Ihrer Website verwenden können Bestimmte Komponenten, z. B. für Communities, akzeptieren auch Eingaben von Ihren Benutzenden.

Für jede AEM-Komponente gilt Folgendes:

* Ist ein Ressourcentyp.
* Ist eine Sammlung mit Skripten, mit denen eine bestimmte Funktion vollständig realisiert wird.
* Funktioniert auch *isoliert* (also in AEM oder einem Portal).

## Vorkonfigurierte Komponenten in AEM {#out-of-the-box-components-within-aem}

AEM verfügt über verschiedene [vorkonfigurierte Komponenten](/help/sites-authoring/default-components.md) mit umfassender Funktionalität, z. B.:

* Absatzsystem ( `parsys`)
* Seite ( `responsivegrid` – nur für Touch-optimierte Benutzeroberfläche)
* Text
* Bild mit Begleittext
* Symbolleiste

Mit den bereitgestellten Komponenten und deren Nutzung auf den bereitgestellten [We.Retail-Beispiel-Websites](/help/sites-developing/we-retail.md) wird veranschaulicht, wie Sie sie implementieren und verwenden können. Die Komponenten werden mit dem gesamten Quell-Code bereitgestellt und können unverändert oder als Ausgangspunkte für geänderte oder erweiterte Komponenten genutzt werden.

### Kernkomponenten und Foundation-Komponenten {#core-components-and-foundation-components}

Von Adobe werden zwei Sätze AEM-Komponenten bereitgestellt:

* [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)
* [Foundation-Komponenten](/help/sites-authoring/default-components-foundation.md)

Die **Kernkomponenten** wurden mit AEM 6.3 eingeführt und bieten flexible und umfangreiche Bearbeitungsfunktionen. Auf der [We.Retail-Referenzsite](/help/sites-developing/we-retail.md) ist dargestellt, wie die Kernkomponenten verwendet werden. Dies entspricht derzeit den Best Practices für die Komponentenentwicklung.

**Foundation-Komponenten** gehören in vielen Versionen von AEM zur Grundausstattung und sind direkt nach einer Standardinstallation verfügbar. Die meisten sind veraltet, werden zwar noch unterstützt, aber nicht mehr erweitert. Sie basieren auf früheren Technologieversionen.

>[!NOTE]
>
>[Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) sind die derzeit beste Vorgehensweise für den Entwurf und die Entwicklung von Komponenten und dienen als Referenzimplementierungen.
>
>[AEM-Modernisierungs-Tools](modernization-tools.md) können die Migration zu Kernkomponenten unterstützen.

### Anzeigen der verfügbaren Komponenten {#viewing-available-components}

Einen Überblick über alle verfügbaren Komponenten Ihrer AEM-Instanz finden Sie in der [Komponentenkonsole](/help/sites-authoring/default-components-console.md).

Alternativ hierzu können Sie auch CRXDE Lite verwenden, um eine Liste mit allen Komponenten abzurufen, die im Repository verfügbar sind.

1. Wählen Sie in **[!UICONTROL CRXDE Lite]** in der Symbolleiste die Option **[!UICONTROL Tools]** und dann **[!UICONTROL Abfrage]**, um die Registerkarte **[!UICONTROL Abfrage]** zu öffnen.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Abfrage]** die Option `XPath` als **[!UICONTROL Typ]**.

1. Geben Sie in das Feld **[!UICONTROL Abfrage]** folgende Zeichenfolge ein:

   `//element(*, cq:Component)`

1. Wenn Sie auf **[!UICONTROL Ausführen]** klicken, werden die Komponenten aufgelistet.

## Zusätzliche Ressourcen {#further-reading}

Die folgenden Seiten enthalten detailliertere Informationen zur Entwicklung dieser – und anderer – Komponenten:

* [AEM-Komponenten – Grundlagen](/help/sites-developing/components-basics.md)
* [Entwickeln von AEM-Komponenten](/help/sites-developing/developing-components.md)
* [Entwickeln von AEM-Komponenten – Code-Beispiele](/help/sites-developing/developing-components-samples.md)
* [Konfigurieren mehrerer Editoren für Bearbeitung im Kontext](/help/sites-developing/multiple-inplace-editors.md)
* [Entwicklermodus](/help/sites-developing/developer-mode.md)
* [Testen der Benutzeroberfläche](/help/sites-developing/hobbes.md)
* [Komponenten für Inhaltsfragmente](/help/sites-developing/components-content-fragments.md)
* [Ermitteln von Seiteninformationen im JSON-Format](/help/sites-developing/pageinfo.md)
* [Internationalisieren von Komponenten](/help/sites-developing/i18n.md)
* [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)
* [Verwenden von Bedingungen zum Ausblenden](/help/sites-developing/hide-conditions.md)
* Klassische Benutzeroberfläche

   * [AEM-Komponenten (klassische Benutzeroberfläche)](/help/sites-developing/developing-components-classic.md)
   * [Verwenden und Erweitern von Widgets (klassische Benutzeroberfläche)](/help/sites-developing/widgets.md)
   * [Verwenden von xtypes (klassische Benutzeroberfläche)](/help/sites-developing/xtypes.md)
   * [Entwicklung von Formularen (klassische Benutzeroberfläche)](/help/sites-developing/developing-forms.md)
