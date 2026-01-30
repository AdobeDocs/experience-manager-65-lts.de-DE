---
title: We.Retail-Referenzimplementierung
description: We.Retail ist eine Technologievorschau einer Referenzimplementierung, die die empfohlene Vorgehensweise zum Einrichten einer Online-Präsenz mit AEM veranschaulicht.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 71a49353-5273-46ee-a1ff-5bbfe5b6b0b4
source-git-commit: c0bf6864bb344e582c4f88371c892d401ce2827c
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 56%

---

# `We.Retail` Referenzimplementierung{#we-retail-reference-implementation}

## Einführung {#introduction}

Die `We.Retail` Seiten sind eine Referenzimplementierung und Beispielinhalte, die die empfohlene Methode zum Einrichten einer Online-Präsenz mit Adobe Experience Manager veranschaulichen.

Die `We.Retail`-Site verwendet die neuesten Adobe Experience Manager (AEM)-Technologien wie HTL, responsive Layouts, bearbeitbare Vorlagen, Kernkomponenten und vieles mehr.

Die Vorgehensweisen werden zwar an Beispielen aus dem Einzelhandel erläutert, aber die Art und Weise, wie die Site eingerichtet ist, lässt sich auch auf jede andere Branche anwenden. Lediglich die Produktkatalog- und Warenkorbfunktionen sind spezifisch für den Einzelhandel.

## Funktionen {#features}

Als standardmäßige Referenzimplementierung von AEM präsentiert `We.Retail` einige der leistungsfähigsten Funktionen von AEM.

| **Funktion** | **Beschreibung** | **Interessiert?** |
|---|---|---|
| [Globalisierte Site-Struktur](/help/sites-administering/tc-bp.md) | `We.Retail` umfasst primäre Sprachseiten, die live in länderspezifische Sites kopiert werden. | [Jetzt testen!](/help/sites-developing/we-retail-globalized-site-structure.md) |
| [Responsives Layout](/help/sites-authoring/responsive-layout.md) | Alle Seiten verfügen über ein responsives Layout, das sich dynamisch an die Bildschirm- und Gerätegröße anpasst. | [Jetzt testen!](/help/sites-developing/we-retail-responsive-layout.md) |
| [Bearbeitbare Vorlagen](/help/sites-developing/page-templates-editable.md) | Alle Seiten basieren auf bearbeitbaren Vorlagen, sodass auch Benutzende ohne Entwicklerkenntnisse die Vorlagen anpassen können. | [Jetzt testen!](/help/sites-developing/we-retail-editable-templates.md) |
| [HTML-Vorlagensprache](https://experienceleague.adobe.com/de/docs/experience-manager-htl/content/overview) | Alle Komponenten basieren auf HTL. |  |
| [Kernkomponenten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/introduction) | Alle Komponenten basieren auf den neuen Kernkomponenten und sind standardmäßig noch benutzerfreundlicher und einfacher konfigurierbar. | [Jetzt testen!](/help/sites-developing/we-retail-core-components.md) |
| [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md) | Der Abschnitt `We.Retail` Erlebnisse zeigt die Möglichkeiten der Wiederverwendung von Inhalten mithilfe von Inhaltsfragmenten. | [Jetzt testen!](/help/sites-developing/we-retail-content-fragments.md) |
| [Experience Fragments](/help/sites-authoring/experience-fragments.md) | Ein Experience Fragment ist eine Gruppe aus einer oder mehreren Komponenten (einschließlich Inhalt und Layout), die innerhalb von Seiten referenziert werden können. | [Jetzt testen!](/help/sites-developing/we-retail-experience-fragments.md) |

## Erste Schritte {#getting-started}

Die `We.Retail`-Site wird als Beispielinhalt von AEM bereitgestellt. Um den Inhalt zu verwenden, [starten Sie AEM einfach wie gewohnt](/help/sites-deploying/deploy.md#getting-started). Stellen Sie dabei sicher, dass die Beispielinhalte nicht deaktiviert sind.

>[!CAUTION]
>
>Installieren Sie `We.Retail` nicht auf Produktionsinstanzen. Produktionsinstanzen sollten im [Ausführungsmodus](/help/sites-deploying/configure-runmodes.md) `nosamplecontent` gestartet werden.

>[!CAUTION]
>
>Die `We.Retail`-Site basiert auf der neuesten AEM-Technologie und bietet daher keine Unterstützung für [klassische Benutzeroberflächenerstellung](/help/sites-classic-ui-authoring/classic-page-author-first-steps.md).

### Neueste Version {#latest-version}

Obwohl `We.Retail` mit der AEM-Version verteilt wird, können nach der Veröffentlichung Aktualisierungen am Inhalt und seinen Funktionen vorgenommen werden. Daher können Sie die [ Version von GitHub herunterladen ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases) sie dann [hochladen](/help/sites-administering/package-manager.md#uploading-packages-from-your-file-system) und [als ](/help/sites-administering/package-manager.md#installing-packages) auf Ihrer AEM-Instanz installieren.

### Erste Schritte {#first-steps}

1. Sobald AEM gestartet (und/oder `We.Retail` installiert ist) ist der Site-**`We.Retail`** in der [Sites-Konsole](/help/sites-authoring/basic-handling.md#global-navigation) verfügbar.
1. Beispielsweise kann die folgende Seite geöffnet werden und sollte so aussehen, wie sie unten im [Anhang](#appendix) angezeigt wird:

   `https://<server name>:<port number>/editor.html/content/we-retail/language-masters/en.html`

## `We.Retail` und Geometrixx {#we-retail-geometrixx}

Geometrixx und seine vielen Varianten dienten als Beispielinhalte in früheren Versionen von AEM. Seit Version 6.3 ist `We.Retail` der Beispielinhalt, der mit AEM bereitgestellt wird und als neue standardmäßige Referenzimplementierung dient.

Die `We.Retail` Site ist technisch robuster und nutzt die neueste AEM-Technologie, um flexibler und skalierbarer zu sein, während gleichzeitig die neuesten Funktionen des Produkts gezeigt werden.

### Funktionsvergleich {#feature-comparison}

In der folgenden Tabelle finden Sie einen Überblick über die wichtigsten Funktionen, die in `We.Retail` im Vergleich zu Geometrixx verfügbar sind.

* **Verfügbar** bedeutet, dass Beispiele der Funktion in den Beispielinhalten zu finden sind.
* **Nicht verfügbar** bedeutet, dass der Beispielinhalt keine Funktionsbeispiele enthält, die Funktion jedoch möglicherweise weiterhin verfügbar ist.


| **Funktion** | **`We.Retail`** | **Geometrixx** |
|---|---|---|
| Globalisierte Site-Struktur | Primäre Sprachseiten werden live in länderspezifische Sites kopiert | Nicht verfügbar |
| Inhaltsfragmente | Verfügbar | Nicht verfügbar |
| Experience Fragments | Verfügbar | Nicht verfügbar |
| Responsives Layout | Für alle Seiten | Nur Geometrixx Media |
| Bearbeitbare Vorlagen | Für alle Seiten | Nicht verfügbar |
| HTL | Alle Komponenten | Limited |
| Targeting | Für alle Seiten | Nur Geometrixx Outdoors |
| Manuskripte | Nicht verfügbar | Verfügbar |
| Karussell-Viewer, Downloads und Diagrammkomponenten | Nicht verfügbar | Verfügbar |
| Spalten-Steuerung | Ersetzt durch Layout-Container | Verfügbar |
| Formulare | Nicht verfügbar | Verfügbar |
| Campaign | Keine E-Mail-Beispiele | Verfügbar |

>[!NOTE]
>
>Diese Liste erhebt keinen Anspruch auf Vollständigkeit.

## Beitragen {#contribute}

Die `We.Retail`-Site wird als Open-Source-Projekt veröffentlicht und die neueste Version des Quell-Codes kann von GitHub heruntergeladen werden.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen des Projekts aem-sample-we-retail auf GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail)
* Laden Sie das Projekt als [ZIP-Datei](https://codeload.github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/zip/refs/heads/master) herunter.

Die neueste Version kann auch [direkt als installierbares Paket heruntergeladen](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases/tag/we.retail.reactor-4.0.0) werden.

Wenn Sie auf Probleme stoßen, öffnen Sie ein [GitHub-Ticket](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/issues).

Mit [Pull-Requests](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/pulls) können Sie weiter ins Detail gehen und eigene Beiträge veröffentlichen.

## Vorschau {#preview}

Vorschau der `We.Retail` Begrüßungsseite:

![screenCapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32](assets/screencapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32.png)
