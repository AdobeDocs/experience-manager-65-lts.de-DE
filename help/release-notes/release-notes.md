---
title: Aktuelle Versionshinweise zu Adobe Experience Manager 6.5 LTS, SP1
description: Hier finden Sie die aktuellen Versionsinformationen zu Adobe Experience Manager 6.5 LTS, Service Pack 1.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 12e2966754fe317c2a20951ee29b401425de486b
workflow-type: tm+mt
source-wordcount: '7223'
ht-degree: 82%

---

# Aktuelle Versionshinweise für Adobe Experience Manager 6.5 LTS, SP1 {#release-notes}

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Version | Service Pack 1 (SP1), Hotfix für GRANITE-61551 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | &#x200B;9. September 2025 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq660%2Fhotfixes%2Fcq-6.5.lts.1-hotfix-GRANITE-61551-1.2.zip) |

<!-- OLD URL TO JAR
(https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.1.jar) | -->


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

## Was in [!DNL Adobe Experience Manager] 6.5 LTS, SP1 enthalten ist {#what-is-new}

<!-- UPDATE EACH RELEASE -->

[!DNL Experience Manager] 6.5 LTS, SP1 umfasst neue Funktionen, wichtige kundenseitig angeforderte Verbesserungen und Fehlerbehebungen. Diese Version enthält zudem Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von Version 6.5 LTS im März 2025 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install-update) auf 6.5 LTS.

<!-- ## Key features and enhancements -->

<!-- 6.5 LTS REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE EACH RELEASE -->

## Behobene Probleme in 6.5 LTS, Service Pack 1 {#fixed-issues}

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

### [!DNL Sites]{#sites-65-LTS-SP1}

#### Barrierefreiheit {#sites-accessibility-65-lts-sp1}

* Es wurde ein Problem behoben, bei dem das Texteditorelement in Inhaltsfragmenten standardmäßig abgeschnitten wurde. Der Texteditor zeigt jetzt den gesamten Inhalt ohne Kürzung an. (SITES-33005)
* Es wurde ein Problem behoben, bei dem durch Klicken auf URL-Pfade die Startseite von Indigo anstelle der richtigen Ziel-URL geöffnet wurde. (SITES-33004)
* Es wurde ein Barrierefreiheitsproblem in einer benutzerdefinierten AEM-Komponente behoben, das während automatisierter Tests zu ADA-Compliance-Fehlern führte. (SITES-30660)
* Die ADA-Compliance-Fehler im Warndialogfeld und in Workflow-Nachrichten wurden behoben, indem sichergestellt wird, dass der Text auf hellem Hintergrund schwarz angezeigt wird und die WCAG 2.0-Kontrastanforderungen erfüllt werden. (SITES-30138)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem der Schaltfläche „Kategorie“ im AEM Sites-Editor ein bestimmtes Label fehlte, was dazu führte, dass JAWS sie als „Images button menu“ ankündigte, anstatt einen beschreibenden Titel bereitzustellen. (SITES-27497)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem Häkchensymbole im Bildschirm „Gültige Berechtigungen“ keinen Alternativtext hatten, sodass JAWS ihre Bedeutung nicht lesen und vermitteln konnte. (SITES-27272)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem die Seite „Berechtigungen“ keine klare JAWS-Ankündigung zum Entfernen von Benutzer- oder Gruppenberechtigungen bereitstellte, was zu Verwirrung bei Benutzenden von Bildschirmlesehilfen führte. (SITES-27238)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem Fehlermeldungen nur als Symbole ohne beschreibenden Text angezeigt wurden, sodass JAWS die Fehler nicht ankündigen konnte, wenn sie auftraten. (SITES-27155)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem JAWS falsche und unklare Schaltflächenbeschreibungen in der AEM-On-Premise-Umgebung las, einschließlich fehlendem Überschriftentext der Ebene 2 für den Abschnitt „Module“. (SITES-27152)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem JAWS die Anzahl der Ergebnisse nach dem Filtern von Werten auf der Registerkarte „AEM Assets“ nicht ankündigte. (SITES-27150)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem beim Erstellen eines Ordners keine Bestätigung angezeigt wurde und JAWS sie nicht in der Assets-Benutzeroberfläche ankündigte. (SITES-27141)
* Es wurde ein Barrierefreiheitsproblem in AEM Sites behoben. JAWS meldete keine Formularfehler, der Fokus wurde auf nicht interaktive Fehlerelemente verschoben, und Pflichtfeld-Fehler wurden beim Drücken der Tab-Taste nicht angezeigt. (SITES-27138)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem dem Timeline-Schaltflächenmenü ein bestimmtes Label fehlte, was dazu führte, dass JAWS nur „Menü der Aktivitäten-Schaltfläche“ las, ohne eine klare Beschreibung bereitzustellen. (SITES-27134)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem JAWS die Aktion oder Rolle für Container-Elemente nicht ankündigte und nur „Breadcrumb v1“ und „Schaltfläche v2“ anstelle von beschreibenden Labels las. (SITES-27131)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem das Popup „Quick Publish“ keine ordnungsgemäße Erfolgsmeldung lieferte, sodass Bildschirmlesehilfen kein Feedback zum Abschluss ankündigten. (SITES-26912)
* Es wurde ein Barrierefreiheitsproblem in der Coral-Spaltenansicht behoben, bei dem Elemente mit ARIA-Rollen, für die untergeordnete Rollen erforderlich sind, sie nicht enthielten, was zur Nichteinhaltung von Barrierefreiheitsstandards führte. (SITES-26898)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem Texte für „Vorlagen“ und „Eigenschaften“ in der oberen Navigation der Erstellungsseite im Reflow-Modus nicht sichtbar waren, was den Zugriff für Benutzende der Tastaturnavigation und von Bildschirmlesehilfen verhinderte. (SITES-26895)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem QuickInfos für die Symbole „Suche“, „Lösung“, „Hilfe“, „Posteingang“ und „Benutzer“ in der oberen Navigationsleiste nicht über die Tastaturnavigation zugänglich waren. (SITES-26889)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem Formularfelder auf der Registerkarte „Allgemein“ keine Fehlervorschläge lieferten, sodass Benutzende keine Anleitung erhalten konnten, wenn erforderliche Eingabefelder leer gelassen wurden. (SITES-26885)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem NVDA und Sprachausgaben keine Vorlagendateidetails auf der Seite „Erstellen“ ankündigten, sodass Benutzende programmgesteuert keine vollständigen Informationen erhalten konnten. (SITES-26884)
* Es wurde ein Barrierefreiheitsproblem behoben, das einen falschen Namen für das Textfeld „Seitentitel“ auf der Registerkarte „Allgemein“ verwendete, wodurch Bildschirmlesehilfen keine korrekten Informationen für Benutzende bereitstellten. (SITES-26879)
* Die Vorder- und Hintergrundfarben der Schaltfläche wurden aktualisiert, um die Anforderungen an das Mindestkontrastverhältnis gemäß WCAG 2.2 AA zu erfüllen, was die Lesbarkeit und Barrierefreiheit für alle Benutzenden verbessert. (SITES-26877)
* Das Problem, das dazu führte, dass die Texte für „Vorlage“ und „Eigenschaften“ in der oberen Navigation der Seite „Erstellen“ nach der Größenanpassung ausgeblendet wurden, wurde behoben. So wird für Menschen mit Seheinschränkungen die Sichtbarkeit und Barrierefreiheit sichergestellt. (SITES-26872)
* Das Problem, das dazu führte, dass nach dem Anwenden eines Reflow mehrere horizontale Bildlaufleisten auf der Hauptseite angezeigt wurden, wurde behoben. So wird sichergestellt, dass eine einzige Bildlaufleiste für ordnungsgemäße Barrierefreiheit und Sichtbarkeit des Inhalts angezeigt wird. (SITES-26800)
* Es wurde ein Problem mit der Barrierefreiheit im AEM-Seiteneditor behoben, bei dem der Tastaturfokus nach dem Aktivieren von Schaltflächen wie „Persona“, „Warenkorb“ oder „Verworfen“ unerwartet auf den Anfang der Demografie-Symbolleiste zurückgesetzt wurde. Der Fokus bleibt nun auf der aktivierten Schaltfläche, um eine konsistente Tastaturnavigation und Workflows für Bildschirmlesehilfen zu unterstützen. (SITES-25306)
* Es wurde ein Problem mit der Zuordnung von Barrierefreiheits-Labels für die Felder für Seitentitel und Tags behoben. Die Benutzeroberfläche von AEM ordnet Barrierefreiheits-Labels bei der Verwendung von Bildschirmlesehilfen wie JAWS nun den Feldern „Titel“ und „Seitentitel“ zu. Die Fehlerbehebung stellt das ordnungsgemäße Lesen von Labels sicher und verbessert die ADA-Konformität für Seitenerstellung, Eigenschaften und Verschiebungs-Workflows hinweg. (SITES-27149)
* Fehlende visuelle Labels für Felder zur Kommentareingabe in der Timeline wurden korrigiert. Fehlende visuelle Label für Eingabefelder vom Typ „Kommentar“ unter dem Abschnitt „Timeline“ wurden korrigiert, um die Barrierefreiheit zu verbessern. Durch die Aktualisierung wird sichergestellt, dass Bildschirmlesehilfen die Feld-Labels korrekt ausgeben können. Dieses Erlebnis verbessert die Navigation in und Übermittlung von Formularen für alle Benutzenden, insbesondere für diejenigen, die auf Hilfstechnologien angewiesen sind. (SITES-26903)
* Der Tastaturzugriff für die Schaltfläche mit den Auslassungspunkten in Timeline-Kommentaren wurde korrigiert. Die Tastaturnavigation für die Schaltfläche mit den Auslassungspunkten (drei Punkte) neben den Kommentaren im Abschnitt „Timeline“ wurde aktiviert. Benutzende können jetzt über die Tabulatortaste auf die Schaltfläche zugreifen und mit ihr interagieren, wodurch die Barrierefreiheit für Benutzende verbessert wird, die auf eine ausschließliche Tastaturnavigation angewiesen sind. (SITES-26891)
* NVDA-/Narrator-Ankündigungen für Suchergebnisse in Auswahldialogfeldern wurden verbessert. Das Feld „Auswahl-Dialogfeld öffnen“ wurde aktualisiert, um anzugeben, ob Suchergebnisse bei der Verwendung von Bildschirmlesehilfen wie NVDA oder Narrator gefunden werden oder nicht. Diese Verbesserung hilft Benutzenden, die auf Hilfstechnologien angewiesen sind, das Ergebnis ihrer Suchaktionen zu verstehen, ohne visuelle Bestätigung zu benötigen. (SITES-26883)
* Die ARIA-Rolle für das Symbol mit den Auslassungspunkten neben dem Feld zur Kommentareingabe wurde korrigiert. Das Symbol mit den Auslassungspunkten (drei Punkte) neben dem Feld zur Kommentareingabe wurde aktualisiert, damit es die richtige ARIA-Rolle verwendet. Dadurch wird sichergestellt, dass Bildschirmlesehilfen das Element genau identifizieren können. Diese Verbesserung optimiert die Compliance mit Barrierefreiheit und das Erlebnis für Benutzende, die auf Hilfstechnologien angewiesen sind. (SITES-26881)
* Ungültige ARIA-Attribute in Komponenten der Coral-Benutzeroberfläche wurden korrigiert. Die Komponenten der Coral-Benutzeroberfläche wurden aktualisiert, um sicherzustellen, dass alle ARIA-Attribute gültige Werte verwenden, wodurch die Compliance mit Barrierefreiheit verbessert wurde. Insbesondere wurden Fälle behandelt, in denen fälschlicherweise ungültige Werte wie `aria-modal="dialog"` zugewiesen wurden. Durch diese Verbesserung können Bildschirmlesehilfen Elemente von Dialogfeldern korrekt interpretieren, wodurch die Barrierefreiheit für Benutzende verbessert wird, die auf Hilfstechnologien angewiesen sind. (SITES-26873)
* Die Sichtbarkeit und QuickInfos für Symbole in Reflow-Szenarien wurde verbessert. Das Reflow-Verhalten wurde verbessert, um sicherzustellen, dass QuickInfos für die Symbole **Herunterladen**, **Assets erneut verarbeiten** und **Checkout** korrekt angezeigt werden. Der Fokus wurde auf ein Problem hinsichtlich der Barrierefreiheit gerichtet, bei dem Symbole und ihre Labels unsichtbar wurden, wenn die Viewport-Größe oder die Zoom-Einstellungen des Browsers geändert wurden. Diese Fehlerbehebung unterstützt Benutzende mit geringer Sehkraft, indem sie die Sichtbarkeit aufrechterhält und beim Reflow korrekte Symbolbeschreibungen bereitstellt. (SITES-26871)


#### Admin-Benutzeroberfläche{#sites-adminui-65-lts-sp1}

* Es wurde ein Barrierefreiheitsproblem behoben, bei dem JAWS keine Listenrollen ankündigte oder im Dialogfeld „Website erstellen“ keine Navigations- und Aktivierungsanweisungen bereitstellte. (SITES-30661)
* Die Unterstützung der Bildschirmlesehilfe für Statusmeldungen in der Sites-Filteransicht funktioniert erwartungsgemäß und stellt sicher, dass Benutzende beim Wechseln zwischen Ansichten ein klares und rechtzeitiges Feedback erhalten. (SITES-24992)
* Die Datumsauswahl in der Filterleiste wird vollständig in ihrem Container angezeigt, sodass eine angemessene Größe des Touch-Ziels gewährleistet ist und Probleme mit dem Beschneiden vermieden werden. (SITES-24988)
* Ausgewählte Filter-Tags verwenden jetzt semantische HTML- und ARIA-Labels, die der visuellen Darstellung entsprechen, was eine präzise Rollenunterstützung und klare Aktionen für Hilfstechnologien sicherstellt. (SITES-24980)
* Dem Bereich der Leiste „Verweise“ wurde ein „aria-label“-Attribut hinzugefügt, um Benutzenden von Bildschirmlesehilfen ein eindeutiges, beschreibendes Label bereitzustellen und eine konsistente Identifizierung von Orientierungspunkten über die gesamte Seite hinweg sicherzustellen. (SITES-24973)
* Die Leiste „Verweise“ wurde aktualisiert, um relative Einheiten für die Dimensionierung und Positionierung zu verwenden, sodass Inhalte skaliert werden können und voll funktionsfähig bleiben, wenn sie in einem Viewport mit 1280 x 1024 auf 400 % vergrößert werden. (SITES-24972)
* Bestätigte Tabellenelemente in der Listenansicht der Sites-Startseite enthalten richtige Spaltenkopfzeilen-Rollen, mit denen Bildschirmlesehilfen Kopfzeilen für jede Datenzelle ankündigen können. (SITES-24942)
* NVDA gibt jetzt das Änderungsdatum im Strukturverzeichnis bekannt, um sicherzustellen, dass Benutzende von Bildschirmlesehilfen vollständige Asset-Detailinformationen erhalten. (SITES-24782)
* Es wurde ein Problem behoben, bei dem die NVDA-Bildschirmlesehilfe ankündigte, dass der Text für Elemente in der Strukturverzeichniskomponente in AEM Sites unvollständig ist. NVDA liest jetzt den vollständigen Text für jedes Element, was die Barrierefreiheit und die Compliance verbessert. (SITES-24780)
* Es wurde ein Tastaturzugriff für den Fenster-Splitter im Strukturverzeichnis hinzugefügt, sodass Benutzende die Größe der linken Seitenleiste nur mit der Tastatur ändern können. (SITES-24779)
* Die Suchergebnisse des Hilfemenüs wurden aktualisiert, um korrekte ARIA-Rollen für Listenelemente einzuschließen, was sicherstellt, dass Bildschirmlesehilfen Links ordnungsgemäß ankündigen, um die Barrierefreiheit zu verbessern. (SITES-24729)
* Es wurde ein Problem behoben, bei dem Bildschirmlesehilfen die Statusmeldung „X von Y Ergebnissen“ nicht ankündigten. Auch die Meldung „Keine Ergebnisse gefunden“ wurde nicht angekündigt, nachdem Filter im Sites-Filter-Bedienfeld angewendet wurden. Durch die Behebung dieses Problems wird sichergestellt, dass Benutzende eine ordnungsgemäße Bestätigung der Ergebnisse erhalten. (SITES-24720)
* Fehlende Rollenzuweisungen für Navigations-Links in der App-Navigation wurden korrigiert. Es wurden geeignete ARIA-Rollen hinzugefügt, um sicherzustellen, dass Bildschirmlesehilfen Navigationselemente korrekt identifizieren und ankündigen. (SITES-24719)
* Falsches Rasterrollen-Markup für ausgewählte Filter-Tags wurde durch Schaltflächenelemente ersetzt und barrierefreie Namen wurden hinzugefügt, um sicherzustellen, dass Bildschirmlesehilfen die Tags korrekt ankündigen und identifizieren. (SITES-24717)
* Es wurden Ankündigungen der Bildschirmlesehilfen für die Statusmeldung auf der Leiste „Verweise“ hinzugefügt, die angezeigt wird, wenn mehrere Auswahlen erfolgen, um sicherzustellen, dass Benutzende eine Bestätigung der Änderungen erhalten. (SITES-24678)
* Das Suchfeldverhalten wurde korrigiert, sodass das erste Ergebnis nicht automatisch angekündigt wird. Bildschirmlesehilfen geben jetzt die Anzahl der gefundenen Ergebnisse aus, sodass Benutzende ohne falsche Fokusankündigungen durch die Liste navigieren können. (SITES-24658)
* Falsche `aria-label`-Attribute wurden aus nicht interaktiven statischen Elementen in der Listenansicht entfernt, um zu verhindern, dass Bildschirmlesehilfen irreführende oder irrelevante Informationen ankündigen. (SITES-24515)
* Das Kontrollkästchen in der ersten Spalte der Listenansicht wurde so aktualisiert, dass der Text der Titelspalte als barrierefreier Name verwendet wird, sodass Bildschirmlesehilfen den Zweck des Formularfelds genau wiedergeben. (SITES-24514)
* Es wurden korrekte ARIA-Attribute und die Live-Regionsunterstützung hinzugefügt, um das Laden von Statusmeldungen für Benutzende von Bildschirmlesehilfen beim Navigieren durch Inhalte anzukündigen. (SITES-24481)
* Das responsive Design wurde aktualisiert, um auf Viewports mit einer Breite von 1280 x 1024 beim Vergrößern von Inhalten auf 400 % horizontales Scrollen zu beseitigen, sodass die vollständige Sichtbarkeit ohne seitliches Scrollen gewährleistet ist. (SITES-24308)
* Die Fokusnavigation in der Admin-Benutzeroberfläche von Sites wurde korrigiert, um einer logischen Reihenfolge zu folgen, wobei der Fokus nach dem Drücken von Esc auf die Schaltfläche „Alle auswählen“ zurückgesetzt und der Fokus nach dem Drücken der Tabulatortaste auf das nächste interaktive Element verschoben wird. (SITES-24307)
* Die Fokusreihenfolge in der Admin-Benutzeroberfläche von Sites wurde aktualisiert, sodass die Breadcrumbs-Schaltfläche im `<betty-titlebar-title>`-Element während der Tastaturnavigation den Fokus in der richtigen Reihenfolge erhält. (SITES-24305)
* Die Funktion zum Überspringen von Links wurde überprüft, um sicherzustellen, dass sie den Tastaturfokus auf den Hauptinhaltsbereich verschiebt, sodass Tastaturbenutzende Kopfzeilenelemente umgehen und effizient auf Inhalte zugreifen können. (SITES-24061)


#### Klassische Benutzeroberfläche{#sites-classicui-65-lts-sp1}

Es wurde ein Problem in der klassischen Benutzeroberfläche behoben, bei dem Kontrollkästchen-Labels fehlten und HTML in mehreren Benutzeroberflächenelementen als kodierter Text angezeigt wurde, darunter bei der Datumssuche und nicht standardmäßigen Benutzeroberflächen. (SITES-31822)

#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp1}

AEM verhindert jetzt Leistungsbeeinträchtigungen durch falsch formatierte XMP-Metadaten in Bild-Assets. Assets, die ungültige oder nicht konforme XMP-Eigenschaftsnamen enthalten, z. B. solche mit numerischen Segmenten oder ungeeigneten Strukturen, lösen während der Verarbeitung keine wiederholten Warnprotokolle mehr aus. Das System filtert problematische Metadaten heraus, um sicherzustellen, dass Asset-Aufnahme und -Validierung fehlerfrei abgeschlossen werden. (SITES-30683)

<!--
#### [!DNL Content Fragments] - Admin{#sites-admin-65-lts-sp1} -->

#### [!DNL Content Fragments] - Editor für Fragmente{#sites-fragments-editor-65-lts-sp1}

Andere Autorinnen und Autoren können Inhaltsfragmente selbst dann veröffentlichen, wenn sie von einer anderen Autorin oder einem anderen Autor ausgecheckt werden, was dem beabsichtigten Verhalten der Checkout-Funktion widerspricht. Diese Fehlerbehebung verhindert, dass andere Benutzende die Schaltflächen zum Veröffentlichen in der Authoring-Oberfläche sehen oder verwenden, wenn ein Inhaltsfragment ausgecheckt wird. (SITES-30578)

<!--
#### [!DNL Content Fragments] - GraphQL API {#sites-graphql-api-65-lts-sp1}

#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-65-lts-sp1}

#### [!DNL Content Fragments] - REST API{#sites-restapi-65-lts-sp1} -->

#### Komponentenkonsole{#sites-component-console-65-lts-sp1}

Es wurde ein Problem in der Produktlistenkomponente behoben, bei dem durch das Kontrollkästchen „Alle auswählen“ nur die ersten 20 SKUs von der ersten Seite hinzugefügt wurden anstatt alle SKUs in den Suchergebnissen. (SITES-29191)

#### Kern-Backend{#sites-core-backend-65-lts-sp1}

Falsch formatierte XMP-Metadaten haben bei der Verarbeitung von Bild-Assets im `ValidationDataServlet` einen Fehler ausgelöst. Die Fehlerbehebung stellt die konforme Verarbeitung von Metadaten sicher und vermeidet redundantes Parsen ungültiger Eigenschaften. (SITE-30683)

<!--
#### Core Components{#sites-core-components-65-lts-sp1}

#### Campaign integration{#sites-campaign-integration-65-lts-sp1}

#### Experience Fragments{#sites-experiencefragments-65-lts-sp1}

#### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp1}

#### Launches{#sites-launches-65-lts-sp1}

#### Link Checker{#sites-link-checker-65-lts-sp1} -->

#### MSM – Live Copies{#sites-msm-live-copies-65-lts-sp1}

* Es wurde ein JavaScript-Fehler `ns.ui.alert is not a function` behoben, der bei der erneuten Aktivierung der Vererbung von Ghost-Komponenten in AEM 6.5 On-Premise auftrat. (SITES-31993)
* Es wurde ein Problem behoben, bei dem die Rollout-Option „Später“ es ermöglichte, ohne Auswahl eines Datums in AEM 6.5 fortzufahren. (SITES-31374)

#### Seiteneditor{#sites-pageeditor-65-lts-sp1}

* Es wurde ein Problem im Teaser-Modal behoben, bei dem auf der Registerkarte „Verknüpfung und Aktionen“ nach der gültigen Dateneingabe und Fehlerbehebung weiterhin Fehlerstile, Symbole und das Attribut „aria-invalid“ angezeigt wurden. (SITES-25527)
* Es wurde ein Problem im Texteditor des Teaser-Modals behoben, bei dem die Listen- und Absatz-Schaltflächen ihren erweiterten oder ausgeblendeten Status nicht an Bildschirmlesehilfen weitergaben. Durch die Behebung des Problems wird sichergestellt, dass das „aria-expanded“-Attribut korrekt aktualisiert wird. (SITES-25365)
* Das Problem in der Demografie-Symbolleiste, bei dem durch Anpassen des Warenkorb-Reglers mit der Tastatureingabe der Fokus auf die Warenkorb-Schaltfläche verschoben und nicht auf dem Regler belassen wurde, wurde behoben, was die Navigationseffizienz für Tastaturbenutzende verbessert. (SITES-25324)
* Es wurde ein barrierefreier Name zum Warenkorb-Regler in der Demografie-Symbolleiste hinzugefügt, indem dem zugehörigen `<label>`-Element ein Wert zugewiesen wurde. Diese Fehlerbehebung verbessert die Kompatibilität mit Hilfstechnologien und verbessert die Benutzerfreundlichkeit für Benutzende von Bildschirmlesehilfen. (SITES-25322)
* ARIA-Rollen und barrierefreie Namen wurden zu den Schaltflächen im Dropdown der Demografie-Symbolleiste hinzugefügt. Diese Fehlerbehebung ermöglichte eine ordnungsgemäße Identifizierung durch Unterstützungstechnologien und eine verbesserte Navigation für Benutzende von Tastatur und Bildschirmlesehilfen. (SITES-25315)
* Das Layout der Demografie-Symbolleiste wurde angepasst, um zu verhindern, dass Inhalte bei einem Browser-Zoom von 200 % über den Viewport hinaus überlaufen und nicht mehr auf den angezeigten Bereich passen. Durch die Anpassung wird sichergestellt, dass alle Steuerelemente ohne horizontales Scrollen zugänglich bleiben. (SITES-25309)
* Die Fokusverwaltung in der Demografie-Symbolleiste wurde korrigiert, damit der Tastaturfokus weiterhin auf der aktivierten Schaltfläche liegt, anstatt den Fokus auf die Startposition der Symbolleiste zurückzusetzen. (SITES-25306)
* Die Überschneidung von Schaltflächen-Labels funktioniert wie vorgesehen und verwendet eine QuickInfo, um das Label anzuzeigen, wenn Modi mit ähnlichen Bildschirmbreiten aktiv sind. (SITES-25285)
* Das Anmerkungsmodal enthält eine sichtbare Senden-Schaltfläche, mit der Benutzende Anmerkungen senden können, ohne die Esc-Taste zu nutzen oder außerhalb des Modals zu klicken. (SITES-25281)
* Das Anmerkungsmodal enthält eine Stiftsymbol-Schaltfläche, mit der Benutzende Anmerkungen senden können, wodurch eine klare und zugängliche Übermittlungsmethode bereitgestellt wird. (SITES-25269)
* Die Ankündigungen der Bildschirmlesehilfen für die Schaltflächen „Anmerken“ und „Schließen“ wurden korrigiert, um genaue, relevante Rückmeldung zu geben und zusammenhanglose oder verwirrende Informationen zu entfernen. (SITES-25268)
* Die Arbeitsflächen-Abschnitte auf den Seiten des AEM-Editors unterstützen jetzt den vollständigen Zugriff auf die Tastatur. Benutzende können Abschnittstitel und Schaltflächen zum Bearbeiten nur über die Tastatur aktivieren, ohne auf den Mauszeiger angewiesen zu sein. Diese Aktualisierung stellt die Einhaltung von WCAG 2.1.1 sicher und verbessert die Benutzerfreundlichkeit für Komponenten wie Teaser-, Bild-, Karussell-, Layout-, Timewarp- und Anmerkungsmodale hinweg. (SITES-25256)
* Unnötiges horizontales Scrollen im Karussell-Modal bei einer Breite von 320 Pixel wurde entfernt, um sicherzustellen, dass alle Inhalte im Viewport angezeigt werden, ohne dass eine seitliche Navigation erforderlich ist. (SITES-25254)
* Unnötiges horizontales Scrollen im Bild-Modal bei einer Breite von 320 Pixel wurde entfernt, um sicherzustellen, dass alle Inhalte im Viewport angezeigt werden, ohne dass eine seitliche Navigation erforderlich ist. (SITES-25244)
* Unnötiges horizontales Scrollen im Teaser-Modal bei einer Breite von 320 Pixel wurde entfernt, um sicherzustellen, dass alle Inhalte im Viewport angezeigt werden, ohne dass eine seitliche Navigation erforderlich ist. (SITES-25242)
* Die Tastaturnavigation für das Popup-Menü `List` und `Paragraph Format` im Teaser-Modal wurde aktiviert. Mit dieser Fehlerbehebung können Benutzende mithilfe der Pfeiltasten auf diese Menüs zugreifen und darin navigieren. (SITES-25235)
* Die Ankündigungen der Bildschirmlesehilfen für die Schaltflächen „Anmerken“ und „Schließen“ wurden korrigiert, um genaue, relevante Rückmeldung entsprechend den zugehörigen Aktionen zu geben. (SITES-25234)
* Das Label der Schaltfläche „Hilfe“ im Teaser-Modal wurde verbessert, um den Zweck klar zu beschreiben und einen aussagekräftigen Kontext für alle Benutzenden bereitzustellen, einschließlich derjenigen, die Hilfstechnologien verwenden. (SITES-25224)
* Der Emulator-Lineal für Benutzende von Bildschirmlesehilfen wurde verbessert, indem die Linealmaße mit ihren jeweiligen Geräten verknüpft wurden. Außerdem wurde die QuickInfo durch ein „aria-describedby“-Element ersetzt. (SITES-24955)
* Es wurde keine Fehlerbehebung implementiert, da die Schaltfläche „Bearbeiten“ wie vorgesehen funktioniert und einen informativen Kontext bietet, anstatt eine Aktion auszuführen. (SITES-24950)
* Die bestätigte Fokusreihenfolge auf der Editor-Seite folgt einer logischen Sequenz, sodass Benutzende durch alle interaktiven Elemente navigieren können, ohne unerwartet Elemente zu überspringen oder zurückzugehen. (SITES-24937)
* Die bestätigte Arbeitsfläche im Vorschaumodus aktualisiert den Textabstand korrekt, wenn Benutzende benutzerdefinierte Textabstandseinstellungen anwenden, was eine konsistente Formatierung über alle Inhaltsbereiche hinweg sicherstellt. (SITES-24936)
* Die überprüfte Vorschau-Schaltfläche löst keine Kontext- oder Statusänderungen im Fokus mehr aus, was sicherstellt, dass Benutzende die Schaltfläche absichtlich aktivieren, bevor die Seitenansicht aktualisiert wird. (SITES-24784)
* Es wurden korrekte ARIA-Rollenzuweisungen zu App-Navigations-Links hinzugefügt, sodass Bildschirmlesehilfen Navigationselemente genau identifizieren und ankündigen können, was die Barrierefreiheit verbessert. (SITES-24718)
* Die Schaltfläche „Filter ändern“ wurde aktualisiert, um die Status „erweitert“ und „ausgeblendet“ für Bildschirmlesehilfen anzukündigen. Redundante ARIA-Attribute wurden entfernt, und die Labels wurden angepasst, um klare, sich nicht überschneidende Beschreibungen bereitzustellen. (SITES-24713)
* Es wurden Ankündigungen der Bildschirmlesehilfen für Statusmeldungen zu Suchergebnissen im Dialogfeld für die Linkauswahl hinzugefügt, um sicherzustellen, dass Benutzende eine Bestätigung erhalten, wenn Ergebnisse geladen werden oder keine Ergebnisse gefunden wurden. (SITES-24700)
* Es wurden Ankündigungen der Bildschirmlesehilfe für den Ladestatus des Bild-Modals hinzugefügt, um sicherzustellen, dass Benutzende eine Rückmeldung erhalten, wenn das Modal geladen wird und für die Interaktion bereit ist. (SITES-24697)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem der Sticky-Header bei einem Zoom von 200 % und 400 % den Inhalt des Teaser-Modal verdeckte. Durch diese Behebung ist nun die vollständige Sichtbarkeit und Benutzerfreundlichkeit bei der Verwendung der Seitenvergrößerung gewährleistet. (SITES-24523)
* Dem Feld „Suchen/Filtern“ wurde eine Statusmeldung mit der Anzahl der Suchergebnisse hinzugefügt, sodass Bildschirmlesehilfen den Benutzenden die Ergebnisse mitteilen können. (SITES-24506)
* Es wurden Ankündigungen der Bildschirmlesehilfen für die Anzahl der Suchergebnisse im Feld „Suchen/Filtern“ hinzugefügt, was sicherstellt, dass Benutzende sofort eine Rückmeldung erhalten, wenn die Ergebnisse geladen werden. (SITES-24505)
* Der Registerkartenliste im Seitenleisten-Bereich wurde ein barrierefreier Name hinzugefügt, damit Bildschirmlesehilfen den Zweck in Übereinstimmung mit den WAI-ARIA-Richtlinien ankündigen können. (SITES-24492)
* Mehrdeutigen Editor-Symbolen wurden beschreibende Labels hinzugefügt, um sicherzustellen, dass alle Benutzenden die Funktion jeder Schaltfläche klar verstehen. (SITES-24480)
* De vollständige Tastaturbedienung für Abschnittstitel und Aktionsschaltflächen in der Arbeitsflächen-Ansicht wurde aktiviert, um einen konsistenten Betrieb für Maus- und Tastaturbenutzende sicherzustellen. (SITES-24479)

<!--
#### Replication{#sites-replication-65-lts-sp1}

#### Rich Text Editor{#sites-rte-65-lts-sp1} -->

#### Universeller Editor {#sites-universal-editor-65-lts-sp1}

* Eine Race-Bedingung in QueryTokenService wurde behoben, die zu fehlerhaften Anmeldungen führt, wenn mehrere Anfragen mit Abfrageparametern ausgelöst werden, bevor der login-token-Dienst ein Ergebnis zurückgibt. (SITES-30659)
* Es wurde ein Problem in UniversalEditorURLService behoben, bei dem beim Speichern eines Arrays von zugeordneten Pfaden in Felix ConfigMgr nur das erste Element beibehalten wurde. (SITES-30292)

### [!DNL Assets]{#assets-65-lts-sp1}

Es wurde ein Problem behoben, bei dem durch das Synchronisieren von Assets von Remote-DAM mit lokalen Sites-AEM der Veröffentlichungsstatus und replikationsbezogene Eigenschaften aus Assets entfernt wurden. (Assets-48958)

<!--
#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp1}

#### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp1}



### [!DNL Forms]{#forms-65-lts-sp1}


#### Forms Designer 

#### Forms

#### Forms JEE 
 
#### Forms Captcha {#forms-captcha-65-lts-sp1} 

#### XMLFM {#forms-xmlfm-65-lts-sp1}

#### [!DNL Adaptive Forms] {#adaptive-forms-65-lts-sp1}

#### [!DNL Forms Designer] {#forms-designer-65-lts-sp1} -->



### Foundation {#foundation-65-lts-sp1}

<!--
#### Apache Felix {#foundation-apachefelix-65-lts-sp1}

#### Campaign{#foundation-campaign-65-lts-sp1}

#### Cloud Services{#foundation-cloudservices-65-lts-sp1}



#### Communities {#foundation-communities-65-lts-sp1}

#### Content distribution{#foundation-content-distribution-65-lts-sp1}

#### CRX {#foundation-crx-65-lts-sp1}

#### Granite{#foundation-granite-65-lts-sp1} -->

#### HTL{#foundatoin-htl-5-lts-sp1}

OSGi-Abhängigkeitszyklen, die verhinderten, dass die HTL Script Engine-Factory funktionierte, wurden behoben, sodass eine ordnungsgemäße Service-Auflösung und Skriptausführung sichergestellt ist. (Granite-58275)

#### Integrationen{#foundation-integrations-65-lts-sp1}

* Zur Anpassung an die neuesten AEM 6.5 LTS-Standards wurde die Verwendung von commons-httpclient 3.x aus dem `com.adobe.cq.cq-analytics-integration`-Bundle entfernt und durch `org.apache.httpcomponents.httpclient` 4.5.13.B0001 ersetzt. (CQ-4360586)
* Das veraltete Search&amp;Promote-Integrations-Bundle wurde aus AEM entfernt, um nicht verwendete Komponenten zu entfernen und den Wartungsaufwand zu reduzieren. (CQ-4358030)
* Es wurden neue Backend-Testfälle für die SiteCatalyst-Integration hinzugefügt, um die Analyse-Validierung zu verbessern und eine umfassendere Abdeckung sicherzustellen. (CQ-4359991)
* Es wurde ein Problem im Abschnitt „Eigenschaften“ der Launch-Konfiguration behoben, bei dem die Dropdown-Listen „Unternehmen“ und „Eigenschaft“ nicht angezeigt wurden. Außerdem löste „Speichern und schließen“ Fehler aus, obwohl alle Pflichtfelder ausgefüllt waren, und es wurden falsche Fehlermeldungen für „Unternehmen“ und „Eigenschaft“ angezeigt, wenn nur das Feld „Titel“ leer war. (CQ-4359853)
* Zur Anpassung an die Entfernung des Search&amp;Promote-Bundles wurde der Eintrag für den `searchpromote`-Servlet-Pfad aus Version 6.6 entfernt. (CQ-4359523)
* Es wurden HTTP-Testfälle für das Ziel-Repository korrigiert, um eine genaue Validierung und verbesserte Testzuverlässigkeit zu gewährleisten. (CQ-4359022)
* Die Verwendung des Guava-Caching wurde aus dem Modul integration-adobeIMS-console entfernt, um Guava-Bibliotheksabhängigkeiten zu beseitigen. (CQ-4358710)
* DTM-Integrations-Workflows, Posteingangsaufgaben und Projektfunktionen in AEM 6.6 wurden validiert, um einen ordnungsgemäßen Betrieb in AEM 6.5 sicherzustellen. (CQ-4358151)
* Die Inhaltseinblick-Funktionalität in AEM 6.6 wurde validiert, um die Kompatibilität und den ordnungsgemäßen Betrieb in AEM 6.5 sicherzustellen. (CQ-4357774)
* Die Cloud Services-Funktionalität in AEM 6.6 wurde validiert, um die Kompatibilität und den ordnungsgemäßen Betrieb in AEM 6.5 sicherzustellen. (CQ-4357773)
* Die Integration der Adobe IMS-Konsole in AEM 6.6 wurde validiert, um die Kompatibilität und den ordnungsgemäßen Betrieb in AEM 6.5 sicherzustellen. (CQ-4357772)
* Die Jenkins-Pipeline für die Test&amp;Target-Integration wurde aktualisiert, sodass sie auf Java 17 ausgeführt werden kann, fehlgeschlagene Selenium-Tests auflöst, ausgewählte Tests nach Playwright verschiebt und sicherstellt, dass alle Unit-Tests erfolgreich sind. (CQ-4357770)
* DX-Integrationen, Workflow, Posteingang und Projekte wurden an die 6.6.0-Verzweigung angepasst, indem Build- und Test-Pipelines aktualisiert wurden. Außerdem wurden Probleme mit der Upgrade-Kompatibilität behoben und alle betroffenen Services auf Stabilität und Funktionalität überprüft. (CQ-4357767)

<!--
#### Jetty{#foundation-jetty-65-lts-sp1} -->

#### Lokalisierung{#foundation-localization-65-lts-sp1}

* Die Zeichenfolgen im Dialogfeld „Zugriffskontrolle entfernen“ der Liste „Berechtigungen“ wurden lokalisiert, um die richtigen Übersetzungen anzuzeigen. (GRANITE-59427)
* Im Modell-Editor wurde im Dialogfeld zum Hinzufügen von Regeln für „ODER-Verzweigungs-Eigenschaften“ ein Problem behoben, bei dem mehrere Zeichenfolgen der Benutzeroberfläche, einschließlich Operatoren und Feldbezeichnungen, nicht lokalisiert angezeigt wurden. Alle Zeichenfolgen werden jetzt mit korrekter Lokalisierung angezeigt. (CQ-4354014)
* Es wurde eine fehlende Übersetzung für die QuickInfo „Beschreibung anzeigen für“ im Dialogfeld zum Bearbeiten von Workflow-Modellen hinzugefügt. (CQ-4347996)

#### Oak {#foundation-oak-65-lts-sp1}

Es wurde ein Problem behoben, bei dem AEM vorhandene Konfigurationsdateien unter `/apps/system/config` bei Upgrades neu erstellt oder umbenannt und `.cfg.json`-Dateien durch `.config`-Dateien ersetzt hat. (GRANITE-58899)

#### OmniSearch{#foundation-omnisearch-65-lts-sp1}

Es wurde ein Barrierefreiheitsproblem behoben, bei dem Platzhalter fälschlicherweise als Labels für Eingabefelder angezeigt wurden. Dieses Problem führt zu fehlenden Feldbezeichnungen bei der Suche, bei AEM Experience Fragments, Inhaltsfragmenten und Inhaltsfragmentmodellen. (Granite-61791)

<!--
#### Platform{#foundation-platform-65-lts-sp1} -->

#### Projekte{#foundation-projects-65-lts-sp1}

* Es wurde ein Problem behoben, bei dem beim Löschen eines Projekts in der Kalenderansicht trotz erfolgreicher Projektlöschung ein falsches Fehler-Popup angezeigt wurde. (CQ-4358890)
* Es wurde ein Problem in Firefox behoben, bei dem die Kartenfußzeile „Asset-Sammlung“ in der Projektansicht über den Kartenrahmen hinausging. Die Fußzeile wird nun korrekt ausgerichtet, ohne dass sie sich mit dem Rahmen überschneidet. (CQ-4353317)

#### Schnellstart{#foundation-quickstart-65-lts-sp1}

* Das Deinstallationsskript wurde aktualisiert, um den Versionsbereich für das Guava-Bundle anzupassen, sodass es bei der Installation über den Paket-Manager nicht auf die Blockierungsliste gesetzt wird. (GRANITE-59559)
* Ein Problem in der Replikations-Benutzeroberfläche, das beim Bearbeiten von Replikationsagenten einen Fehler (`#1660`) anzeigte, wurde behoben, indem die Handhabung von klassischen Kontrollkästchen in der Benutzeroberfläche korrigiert wurde. (GRANITE-58302)
* Es wurden mehrere Startfehler für den S3-Datenspeicher beim Ausführen von AEM 6.5 LTS mit JDK 21 behoben, indem fehlende Dienstberechtigungen korrigiert, die Konfigurationsverarbeitung aktualisiert und sichergestellt wurde, dass die erforderlichen Dienste korrekt initialisiert werden. (GRANITE-57082)
* Die Wartungs- und Instandhaltungsstrategie für AEM 6.5 wurde definiert. Diese Fehlerbehebung umfasste Folgendes:
   * Service Pack-Intervalle.
   * Hotfix-Intervall.
   * Parallele Unterstützung zu AEM 6.6.
   * Aktualisierte Support-Matrix.
   * Verantwortlichkeiten bei Add-on-Inhaberschaft. (GRANITE-50459)

<!--
#### Security{#foundation-security-65-lts-sp1} -->

#### Sling{#foundation-sling-65-lts-sp1}

* Sling ResourceAccessSecurity wurde auf Version 1.1.2 aktualisiert, um eine `ClassCastException` zu beheben, die auftrat, wenn mehrere `ResourceAccessGate`-Referenzen `ResourceAccessSecurityImpl` initialisierten. (NPR-42750)
* Es wurde ein Problem bei der Adobe Stock-Integration behoben, bei dem das Lizenzdialogfeld ausgegraut angezeigt wurde. Dieses Problem war auf das Entfernen erforderlicher Eingabefelder durch die Funktion `sunt:initList` zurückzuführen. Die Funktion wurde in den Client-Bibliotheken der Coral Foundation gefunden. Die Client-Bibliotheken wurden aktualisiert, um die erforderlichen Felder beizubehalten, was die ordnungsgemäße Funktion des Lizenzdialogfelds ermöglicht. (NPR-42748)
* Die Fehlerbehebung für das Sling Scripting-Problem, das während der Paketinstallation zu den Null Pointer-Ausnahmen `DataTimeParseException` und `String.length()` führte, ist als Backport verfügbar. Sling Scripting wurde auf Version 2.8.3-1.0.10.6 aktualisiert, um Installationsfehler zu reduzieren und die Stabilität zu verbessern. (NPR-42640)

<!--
#### Translation{#foundation-translation-65-lts-sp1} -->

#### Benutzeroberfläche{#foundation-ui-65-lts-sp1}

* Es wurde ein Problem in der AEM Author-Benutzeroberfläche behoben, durch das die Anzeige von Benutzergruppen auf 41 beschränkt wurde. Dieses Problem war auf ein standardmäßiges Batch-Limit in der Gruppenauswahl-Komponente der Granite-Benutzeroberfläche zurückzuführen. Die Komponente wurde so aktualisiert, dass alle Gruppen ohne Abschneiden angezeigt werden. (NPR-42749)
* Es wurde ein Problem im Assistenten zur On-Premise-Seitenerstellung behoben, bei dem Pflichtfelder in Komponenten mit mehreren Feldern beim Bearbeiten der Seiteneigenschaften nicht erneut überprüft wurden. Dieses Problem wiederum ermöglichte es Autoren und Autorinnen, die Validierung zu umgehen und mit unvollständigen Daten fortzufahren. (GRANITE-58826)
* ARIA-Attribute für die Schaltfläche „Hilfe“ in AEM wurden korrigiert, um sicherzustellen, dass die JAWS-Bildschirmlesehilfen ein klares, benutzerfreundliches Label ankündigen, anstatt unübersetzte Symbol- und Textmetadaten anzuzeigen. (GRANITE-55360)

#### WCM{#foundation-wcm-65-lts-sp1}

* Die Java 17-Unterstützung für AEM-Übersetzungen wurde hinzugefügt. Dazu wurden Übersetzungspakete aktualisiert, die Kompatibilität mit Java-Paketen wurde überprüft, veraltete Abhängigkeiten wurden entfernt und durch umfassende Tests wurde die volle Funktionalität sichergestellt. (CQ-4357525)
* Unzureichende Evergreen-Test-`com.adobe.cq.platform.it.http.workflow.inbox.InboxOnOffTimeIT.testActivateLater` entfernt, um falsche Fehler bei Tests zu verhindern. (CQ-4298376)

#### Workflow{#foundation-workflow-65-lts-sp1}

* Das fehlende `data-detailsurl`-Attribut wurde in Posteingangselementen hinzugefügt, um zu verhindern, dass undefinierte Werte in URLs angezeigt werden, wenn AEM 6.5 LTS mit Java 21 verwendet wird. (GRANITE-60158)
* Die NullPointerException in der Methode `deactivate` des `WorkflowToPublishEventService`-Bundles, die bei der Ausführung von AEM 6.5 LTS mit Java 21 auftrat, wurde behoben, sodass ein ordnungsgemäßes Herunterfahren des Workflow-Services ohne Fehler gewährleistet ist. (GRANITE-58151)
* Der Workflow-Index wurde aktualisiert, um die Freigabe, die Abwesenheitsanpassung und die Behebung von Timeline-Abfrageproblemen zu unterstützen. (GRANITE-52640)
* Der Workflow-Index wurde aktualisiert, um die Freigabe, die Abwesenheitsanpassungs-Funktionen und die Behebung von Timeline-Abfrageproblemen zu unterstützen. (GRANITE-52294)
* Die erhöhte Anzahl an Fehlerprotokollfehlern bei der Validierung von Protokollvergleichen wurde für ein Programm-Upgrade auf AEM Version 10912 behoben, wodurch eine stabile Ausführung des Workflows gewährleistet ist. (GRANITE-44268)
* Die URL-Bereinigungsmethode in Workflow-Repos wurde aktualisiert, sodass `url.searchParams` durch `url.search` ersetzt wird, was den XSS-Schutz für anfällige URLs verbessert. (CQ-4359585)
* Die Workflow-, Posteingangs- und Projektfunktionen in AEM 6.6 Forms wurden validiert, um einen ordnungsgemäßen Betrieb und eine ordnungsgemäße Integration sicherzustellen. (CQ-4358777)
* Die Automatisierung für die Freigabe von Workflow-Inhaltsartefakten über Jenkins wurde implementiert, was optimierte und konsistente Bereitstellungsprozesse in AEM 6.5 ermöglicht. (CQ-4358472)
* Ein Problem im Workflow zum Erstellen einer Aufgabe im Posteingang wurde behoben, bei dem das Dialogfeld „Aufgabe hinzufügen“ nicht geschlossen wurde, nachdem auf „Senden“ geklickt wurde, obwohl die Aufgabe erstellt wurde. Dies ist auf einen JavaScript-Syntaxfehler zurückzuführen. (CQ-4355336)
* Es wurde ein Problem behoben, das das Speichern der Konfiguration der Posteingang-Ansicht aufgrund einer fehlenden Eigenschaftsdefinition für `isEndUserConfigurationEnabled` verhinderte. (CQ-4287757)

## Forms

### Forms Designer

* Wenn Benutzende die Daten für eine XFA-basierte PDF mit dem exportDataAPI exportieren, weist die resultierende XML Diskrepanzen im Vergleich zu den XML-Daten auf, die manuell mit Acrobat Reader exportiert wurden. In der Ausgabe fehlten Werte einiger Felder im Vergleich zu der von Acrobat Reader generierten Ausgabe. (LC-3922791)
* Beim Generieren einer getaggten PDF mit dem Ausgabe-Service in Workbench wird ein unerwartetes Beschriftungs-Tag unter dem Referenz-Tag in einem Inhaltsverzeichniselement hinzugefügt. (LC-3922756)
* Beim Reduzieren dynamischer, ausfüllbarer PDF-Dateien mithilfe des Output-Service auf das PDF/A-Format wird der dynamische Status nicht beibehalten. Dies führt zu Datenverlust und potenziellen Compliance-Problemen, insbesondere wenn das Tagging aktiviert ist. (LC-3922708)
* Wenn Benutzende Feldbeschriftungen mit Ausrichtung nach unten oder rechts in AEM Forms Designer platzieren, enthält die Tag-Baumstruktur nur die Beschriftung ohne den entsprechenden Wert, was zu unvollständigem Tagging für die Barrierefreiheit führt. (LC-3922619)
* Die QR-Codes in generierten PDFs werden unlesbar. Der Alternativtext für die QR-Codes besteht die Prüfung der Barrierefreiheit ebenfalls nicht, was sich auf die Kompatibilität der Bildschirmlesehilfen auswirkt. (LC-3922551)
* Wenn ein Benutzer einen Brief in der Benutzeroberfläche für Agenten rendert, wird der Inhalt aufgrund der FormService-Render()-API nicht korrekt angezeigt. (LC-3922461)
* Wenn ein(e) Benutzende(r) versucht, PDF/A-Dateien aus XDPs im Sunken-Square-Stil in AEM Forms zu erstellen, führt dies zu Problemen beim Rendering von Rahmen. (LC-3922180)
* Das Reduzieren dynamischer Formulare, die an ein XSD-Schema gebunden sind, verursacht einen teilweisen Datenverlust, da einige gebundene Formulardaten nicht in der endgültigen PDF beibehalten werden. (LC-3922008)
* Wenn ein(e) Benutzende(r) versucht, Daten aus interaktiven PDFs mithilfe der extractData-API in AEM Forms 6.5.13 und höheren Versionen zu exportieren, fehlen im Vergleich zum manuellen Export Daten. (LC-3921983)
* Benutzende sehen sich dem Problem der Barrierefreiheit gegenüber, wenn beim Konvertieren von XDP-Formularen in statische PDFs mit AEM Forms Designer oder Output Service mehrere Link-OBJR-Tags erstellt werden, anstatt ein einziges einheitliches Link-Tag zu erstellen. (LC-3921977)

### Adaptive Formulare

* Wenn Sie in AEM Forms im Stammbedienfeld die Option „Rich-Text für Titel zulassen“ aktivieren, wird durch die Option „Titel aus Nachweis ausschließen“ in einem verschachtelten Bedienfeld der Titel des Stammbedienfelds fälschlicherweise ausgeblendet. Dies erfolgt im generierten Nachweis. (FORMS-19696)
* Das System ignoriert das benutzerdefinierte Sling:resourceType das über AEM in :afProperties JSON-Schema zugewiesen wurde. Der benutzerdefinierte Ressourcentyp wird beim Rendern ignoriert. (FORMS-19691)
* Wenn Benutzende ein adaptives Formular mit vorausgefüllten Anhängen unter Verwendung von URIs senden, schlägt die Formularübermittlung mit einer NullPointerException aufgrund fehlender Binärdaten fehl. (FORMS-19371), (FORMS-19486)
* Wenn ein(e) Benutzende(r) eine PDF unter dem Abschnitt &quot;Forms und Dokumente“ hochlädt, funktioniert die Zeitleisten-Funktion nicht mehr. (FORMS-19407), (FORMS-19234)
* Wenn Benutzende Dateien mit der vordefinierten Dateianhangskomponente in AEM Forms hochladen, werden Sicherheitslücken identifiziert. Dieses Problem führt zu einem möglichen Abfangen des Übermittlungsprozesses durch nicht autorisierte Entitäten. (FORMS-19271)
* Wenn Benutzende in AEM Forms ein standardmäßiges adaptives Formular so konfigurieren, dass automatisch ein Nachweis (DoR) generiert wird, wird im Feld „Titel“ der Dokumenteigenschaften von Acrobat Reader nicht der erfasste DoR-Titel angezeigt. Standardmäßig wird der Formulartitel nicht anstelle des Dateinamens angezeigt. (FORMS-19263)
* Wenn Benutzende eine interaktive Kommunikation in der Agent-Benutzeroberfläche öffnen, können die vorausgefüllten Daten nicht vollständig gelöscht werden. Nach dem Entfernen werden sie automatisch mit denselben Daten erneut ausgefüllt. (FORMS-19151)
* Wenn Benutzende in der Agent-Benutzeroberfläche eine Vorschau eines Datumsfeldes anzeigen, ändert sich das Datum unerwartet. Dieses Problem tritt aufgrund von Zeitzonendiskrepanzen zwischen der UTC-Einstellung der VM und der Datumsinterpretation des Systems auf. (FORMS-19115)
* Wenn Benutzende ein Formular senden, können Dateianhänge dupliziert werden, was zu mehreren Uploads derselben Datei führt. (FORMS-19045), (FORMS-19051)
* Das Hinzufügen von Koordinatoren zu Richtliniensätzen in Document Security schlägt sowohl in Produktions- als auch in niedrigeren Umgebungen fehl. (FORMS-18603, FORMS-18212, FORMS-19697)
* Wenn ein(e) Benutzende(r) im Desktop-Modus mit einem leeren Feld auf das „Datumsauswahl-Kalender-Symbol“ klickt, tritt aufgrund der nicht definierten Variablen _$focusDate ein Fehler auf, der die zugehörigen benutzerdefinierten Skripte stört. (FORMS-18483), (FORMS-18268)
* Wenn ein Kunde einen Brief in der Vorschau anzeigt, kann das Feld „Betrag in Wörtern“ Zahlenwerte nicht korrekt anzeigen oder aktualisieren, was zu einer falschen Ausrichtung und fehlenden Leerzeichen im Inhalt führt. (FORMS-18437, FORMS-17330, FORMS-18209, FORMS-18557, CTG-4150848,FORMS-19614, LC-3922004)
* Wenn ein Kunde einen gespeicherten Brief in RHEL in der Vorschau anzeigt, werden der Inhalt falsch ausgerichtet, Leerzeichen fehlen und unerwartete Zeichen wie „x“ angezeigt. (FORMS-18422), (FORMS-17641)
* Wenn Benutzende in AEM Forms zwischen Registerkarten navigieren, reagiert die Auswahl von Komponenten auf der ersten Registerkarte nicht mehr. (FORMS-18345)
* Wenn ein(e) Benutzende(r) eine HTML-Datei mithilfe der Option WebToPDF in PDF konvertiert, fehlt der Ausgabe-PDF der Kopfzeilenabschnitt einschließlich der Metadaten- und Titel-Tags. (FORMS-18223, FORMS-17835, FORMS-19642, FORMS-18224)
* Wenn Benutzende im AEM JEE Process Manager-SDK die Methode „retryAction(long actionOid)“ aufrufen, versucht das System fälschlicherweise, die erste Aktion in der Tabelle „tb_action_instance“ erneut auszuführen. Dieser Workflow tritt auch dann auf, wenn eine bestimmte Aktions-ID angegeben wird oder die ID null ist, was zu ungewolltem Verhalten führt. (FORMS-18187)
* Ein Benutzer stößt auf Probleme, bei denen die gespeicherten Entwurfs- und Übermittlungsfunktionen fehlschlagen, ohne eine Fehlermeldung anzuzeigen. (FORMS-18069)
* Der Übergang von XSD-basierten Foundation-Komponenten zu Kernkomponenten verhindert die Implementierung dateiübergreifender Verweise in JSON-Schemas, was sich auf die Migration von adaptiven Forms auswirkt. (FORMS-18065)
* Wenn Benutzende in der Agent-Benutzeroberfläche die Vorschau eines US-Letters anzeigen, wird im Datumsfeld aufgrund von Problemen mit der IC-Zeitkonvertierung ein falscher Wert angezeigt. Diese Diskrepanzen ergeben sich aus Zeitzonenunterschieden zwischen der VM-Umgebung und der Zeitinterpretation des Systems (UTC vs. lokale Zeit). (FORMS-17988), (FORMS-17248)
* Wenn Benutzende US-Letter mithilfe von Benachrichtigungs-IC-Vorlagen in AEM Forms anzeigen, variieren die Generierungszeiten der PDF-Dateien selbst auf demselben Server erheblich: von 1,5 Sekunden bis mehr als 10 Sekunden. Diese Inkonsistenz wirkt sich auf geschäftskritische Workflows aus. (FORMS-17951)
* Wenn eine Benutzerin bzw. ein Benutzer ein Scribble-Signaturobjekt in einem adaptiven Formular über die Option „Datenquellen“ mit einer XDP-Datei verknüpft, können Änderungen nicht gespeichert werden. Der Grund dafür sind anhaltende Fehler bei der Validierung des Seitenverhältnisses, selbst bei Verwendung gültiger Werte. (FORMS-17587)
* Wenn ein(e) Benutzende(r) eine bestimmte XDP-Datei mit vielen ausgeblendeten Feldern für Dokumentfragmente verwendet, erstellt AEM CRX-Knoten mit der cm:optional-Eigenschaft, die auf „false“ gesetzt ist, was dazu führt, dass die Übermittlung der interaktiven Kommunikation (IC) fehlschlägt. (FORMS-17538)
* Wenn eine Kundin oder ein Kunde einen Brief in der Vorschau anzeigt, kann das numerische Feld negative Werte nicht korrekt verarbeiten, wenn Ziffernlimits für Lead und Frac definiert sind. Dieses Problem tritt aufgrund der Verwendung von parseFloat auf, das das Minuszeichen als Teil der Zahl behandelt. (FORMS-17451)
* Wenn ein Brief in der Vorschau angezeigt wird, wird die Verwendung des Platzhalters &quot;*&quot; in der Datei &quot;Adobe.json“ bemerkt, was Bedenken hinsichtlich seines Zwecks und seiner möglichen Änderung aufwirft. (FORMS-17317)
* Wenn ein(e) Benutzende(r) im gemeinsamen Konto Apply for a Fixed Rate Saver eine Bildschirmlesehilfe verwendet, werden die Überschriften fälschlicherweise als anklickbar angekündigt, was zu Problemen bei der Barrierefreiheit führt. (FORMS-17038)
* Wenn ein Formular eingebettet ist, fehlt im generierten iframe ein Titelattribut, was zu einem Problem hinsichtlich der Barrierefreiheit führt. (FORMS-17010)
* Das Herunterladen eines Formulars über die Forms Manager-Benutzeroberfläche umfasst immer verknüpfte Abhängigkeiten wie Designs und Fragmente. (FORMS-15811)
* Wenn Benutzende über mobile Geräte (iOS und Android™) auf das Formular zugreifen, sind die Schaltflächen „Weiter“ und „Zurück“ auf der ersten Seite deaktiviert. Die Bildschirmlesehilfe erkennt sie jedoch nicht als deaktiviert. (FORMS-15773)
* Wenn Benutzende ein großes Formular mit aktivierten Fragmenten und verzögertem Laden speichern, können keine Entwürfe abgerufen werden, wodurch der Workflow unterbrochen wird. (FORMS-19890, FORMS-19808)
* Beim Speichern von Formulareigenschaften für adaptive Formulare basierend auf Kernkomponenten sind Probleme aufgetreten. Dies trat auf, weil redundante Skripte aus dem auf Foundation-Komponenten basierenden adaptiven Formular enthalten sind, was zu Konflikten in dem auf Kernkomponenten basierenden adaptiven Formular führt. Editor. (FORMS-17474)
* Benutzende hatten Probleme damit, dass die Adobe Sign-GovCloud-Signaturseite nicht in einem iFrame gerendert wurde. (FORMS-16803)
* Benutzende erhalten Fehler bei der Auswahl von Verweisen für Kernkomponenten-Fragmente des adaptiven Forms (AF). Die Fehlermeldung „Verweis kann nicht gerendert werden: Kein absoluter Pfad“ wurde angezeigt, wodurch das korrekte Rendern von Verweisen verhindert wurde. (FORMS-19678)
* Multi-Thread-Konvertierungen mit Acrobat DC werden jetzt unterstützt, sodass Benutzer Word-, Excel- und PowerPoint-Dokumente gleichzeitig effizienter in PDF-Dokumente konvertieren können. (FORMS-21310)
* Es wurde die Aufnahme `com.adobe.granite.toggle.impl.dev` Bundles in AEM Service Pack 24 hinzugefügt, was optimierte Entwicklungsprozesse ermöglicht, indem es aus dem Forms-Add-on entfernt wird. (FORMS-20139)
* Das FeatureToggleRenderConditionServlet wurde aus dem forms-foundation-Paket und das com.adobe.granite.toggle.impl.dev-Paket aus dem Forms-Add-on entfernt. Diese Aktualisierung stellt sicher, dass die Render-Bedingung nach der Installation des Forms-Add-ons korrekt aufgelöst wird, wodurch die Komponentenfunktionalität für Kunden verbessert wird. (FORMS-20138)
* Benutzende erlebten eine langsame Leistung aufgrund von langwierigen Abfragen in Adaptive Forms. Diese Aktualisierung rückportiert Abfrageänderungen, um die Effizienz zu verbessern. Kunden können jetzt einen Index mit dem Tag-Namen aemformsAFReferences erstellen. (FORMS-21411)
* Beim Konvertieren von HTML in das Portable Document Format (PDF) mithilfe von WebToPDF sind falsch ausgerichtete Kopfzeilenpositionen aufgetreten. Dieses Problem wirkte sich auf die Konsistenz des Dokumentlayouts und die Lesbarkeit der Ausgabe aus. (FORMS-21502, FORMS-21540)
* Bei den Benutzenden traten trotz erfolgreicher PreFlight-Verifizierung PDF/A-1b-Validierungsfehler auf. Dieses Problem wirkte sich auf die Dokumentenkonformitätsprüfungen für Unternehmenskunden mit PDF-Validierungstools aus. (FORMS-20196)
* Benutzende erlebten unübersetzte Zeichenfolgen auf der Benutzeroberfläche, was Verwirrung und Schwierigkeiten beim Verständnis der Benutzeroberfläche verursachte. (FORMS-6542)
* Benutzende hatten Probleme mit E-Mail-Benachrichtigungen. Der Workflow-Schritt „E-Mail senden“ konnte keine E-Mails senden, was sich auf die automatisierten Kommunikationsprozesse auswirkte. (FORMS-17961)
* Benutzende erlebten fehlgeschlagene Tests für Formular-Workflows, was sich auf ihre Fähigkeit auswirkte, Workflow-Prozesse effizient abzuschließen. (FORMS-16231)
* Benutzende konnten die Zeitleisten-Funktion von PDF-Dateien in AEM Forms nicht verwenden. Dieses Problem beeinträchtigte die Fähigkeit von Benutzern, Dokumentänderungen und -revisionen effektiv zu verfolgen. Beim Hochladen von PDF unter dem Abschnitt &quot;Forms und Dokumente“ im Bereich &quot;AEM Forms“ funktioniert die Zeitleisten-Ansicht nicht mehr. (FORMS-19408)
* Bei der Interaktion mit OData kommt es zu einer Null Pointer-Ausnahme. Dies führt zu Unterbrechungen bei Datenabrufprozessen. (FORMS-20348)
* Die Bibliothek „google.common.collect“ wurde entfernt, nachdem Guava, eine Open-Source-Java-Bibliothek, entfernt wurde. Dieses Update sorgt für bessere Kompatibilität und Leistung für Unternehmenskunden, die Adaptive Forms verwenden. (FORMS-17031)

### Formular-Captcha

* Es wurde HCAPTCHA- und Drehkreuz-Unterstützung für adaptive Forms auf der Grundlage von Foundation-Komponenten hinzugefügt. (FORMS-16562)
* Bei Benutzenden traten im Dialogfeld „CAPTCHA-Konfiguration erstellen“ Probleme mit Symbolüberschneidungen auf. Beim Ausfüllen von Pflichtfeldern überlagerte sich das Informationssymbol mit dem Fehlersymbol, was bei der Einrichtung der Konfiguration zu Verwirrung führte. (FORMS-16916)
* Benutzende haben erfahren, dass für reCAPTCHA in adaptiven Forms basierend auf Foundation-Komponenten eine falsche Konfiguration abgerufen wurde. Wenn der Konfigurations-Container für ein Formular nicht ausgewählt wurde, verursachten mehrere Konfigurationen im `conf/global` das Problem. (FORMS-19237)
* Bei Benutzenden traten Probleme auf, bei denen reCAPTCHA nicht gerendert wurde. Dies wirkte sich auf Formularübermittlungen und die Sicherheitsüberprüfung für Unternehmenskunden aus. (FORMS-17136, FORMS-19596)
* Bei Benutzenden tritt ein Problem auf, bei dem die Größe des reCAPTCHA-Unternehmens nicht in der Benutzeroberfläche angezeigt wird. (FORMS-16574)
* Benutzende hatten Probleme mit der reCAPTCHA-Funktion aufgrund eines nicht geschlossenen ResourceResolver in „reCAPTCHAconfigurationServiceImpl“, was zu zeitweiligen Validierungsfehlern während der Formularübermittlung führte. (FORMS-19241)
* Benutzende hatten Probleme mit der reCAPTCHA-Validierung, wenn Formulare in Sites verfasst wurden. AEM Forms erkannte den Formularnamen nicht richtig, was zu Validierungsfehlern führte. (FORMS-20486)
* Bei Benutzenden traten Formularübermittlungen auf, obwohl der reCAPTCHA-Wert für das Unternehmen bei 1,0 lag, was zu potenziellen Sicherheitsrisiken führte. (FORMS-16766){{$include }}
* reCAPTCHA-Warnungen in adaptiven Formularen wurden durch Aktualisierung der Übermittlungsfehler-Codes auf 400 verbessert. Außerdem wurden Protokollwarnungen verfeinert, um zwischen Timeouts, Abläufen und Fehlern bei der Bot-Erkennung zu unterscheiden und so die Genauigkeit bei der Fehlerbehebung und Systembeobachtung zu verbessern. (FORMS-19240)
* Eine nicht geschlossene ResourceResolver-Instanz in ReCAPTCHAconfigurationServiceImpl wurde geschlossen, um potenzielle Ressourcenlecks zu verhindern und die Systemstabilität bei der Verwendung von reCAPTCHA-Integrationen in AEM Forms zu verbessern. (FORMS-19242)
* Die CAPTCHA-Konfigurationsverarbeitung für AEM Forms wurde verbessert, indem sichergestellt wurde, dass die richtige Konfiguration an jedes Formular gebunden ist, wenn mehrere Einträge im Ordner &quot;/conf/global“ vorhanden sind. Verhindert die unbeabsichtigte Verwendung falscher CAPTCHA-Einstellungen, wenn der Konfigurations-Container nicht explizit ausgewählt ist. (FORMS-19239)

### Benutzeroberfläche für die Formularverwaltung

* Nicht lokalisierte Zeichenfolgen traten im Erstellungsprozess von Forms > Watchfolder erstellen > Watchfolder auf. Beim Erstellen eines überwachten Ordners wurden Zeichenfolgen wie „Erstellung des überwachten Ordners“ und „Überwachter Ordner erfolgreich erstellt“ nicht gefunden, was sich auf die Benutzeroberfläche auswirkte. (FORMS-15234)

## [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Die Plattform von [!DNL Adobe Experience Manager] 6.5 LTS basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java™ Content-Repository Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x wird als Servlet-Engine für den Schnellstart verwendet.

### Java™-Unterstützung  {#java-support}

* Unterstützung für Java™ 17 und Java™ 21.
* Um eine optimale Leistung zu erzielen, überschreiben Sie die GC-Standardwerte mit anderen Werten. Weitere Informationen finden Sie im Abschnitt [Installieren und Aktualisieren](/help/sites-deploying/custom-standalone-install.md).
* Adobe verteilt Wartungs-Updates für Java™ 17 und Java™ 21 für die Verwendung durch Kunden in AEM-bezogenen Projekten, sofern diese nicht über Oracle öffentlich verfügbar sind.

### Uber-JAR-Verpackung {#uber-jar-packaging}

* Es gibt einen geringfügigen Unterschied beim Verpacken von Uber Jar in AEM 6.5 LTS. Weitere Informationen finden Sie unter [Aktualisieren der Uber Jar-Version von AEM](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Aktualisieren {#upgrade}

* Weitere Informationen zum Upgrade-Verfahren finden Sie unter [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md).

## Installieren und Aktualisieren {#install-update}

Informationen zu Einrichtungsanforderungen finden Sie unter [Installationsanweisungen](/help/sites-deploying/custom-standalone-install.md).

>[!NOTE]
>
> Wenn Sie ein direktes Upgrade von alten 6.5 SPs auf LTS SP1 durchführen, befolgen Sie bitte die Anweisungen für 6.5 bis 6.5 LTS GA [Upgrade](/help/sites-deploying/upgrade.md).


Detaillierte Anweisungen finden Sie unter [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> Für neue AEM 6.5 LTS-Installationen müssen Indexdefinitionen separat installiert werden. Weitere Informationen finden Sie in [diesem Artikel](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Installieren und Aktualisieren des AEM Forms-Add-ons {#install-update-aem-forms-add-on}

Detaillierte Anweisungen finden Sie unter [Durchführen eines In-Place-Upgrades](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/release-notes/aem-forms-current-service-pack-installation-instructions).



## Unterstützte Plattformen {#supported-platforms}

Die vollständige Matrix der unterstützten Plattformen, einschließlich der Support-Ebene, finden Sie unter [AEM 6.5 LTS – Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java™ 17/Java™ 21 sind die empfohlenen Versionen für AEM 6.5 LTS.


## Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

<!-- CARRY OVER EACH RELEASE -->

Adobe überprüft kontinuierlich die Produktfunktionen, um den Kundenwert zu verbessern, indem ältere Funktionen modernisiert oder ersetzt werden. Diese Änderungen werden mit größter Sorgfalt vorgenommen, um Abwärtskompatibilität zu gewährleisten.

Für die Bekanntgabe der bevorstehenden Entfernung oder Ersetzung von Adobe Experience Manager (AEM)-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Obwohl diese Funktionen veraltet sind, sind sie weiterhin verfügbar, sie werden jedoch nicht weiter verbessert.
1. Das Entfernen veralteter Funktionen erfolgt frühestens mit Einführung der nächsten Hauptversion. Das tatsächliche Zieldatum für die Entfernung wird später bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

### Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden Funktionen aufgeführt, die Adobe in AEM 6.5 LTS nicht mehr unterstützt werden. In der Regel werden Funktionen von Adobe eingestellt, bevor sie aus einer zukünftigen Version entfernt werden, und es wird eine Alternative bereitgestellt.


Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung nutzen, und die Änderung ihrer Implementierung zu planen, um die bereitgestellte Alternative nutzen zu können.

| Bereich | Funktion | Ersatz | Version (SP) |
| --- | --- | --- | --- |
| Sites | [SPA-Editor](/help/sites-developing/spa-overview.md) | Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind: <br>- der [universelle Editor](/help/sites-developing/universal-editor/introduction.md) zur visuellen Bearbeitung.<br>- der [Inhaltsfragment-Editor](/help/assets/content-fragments/content-fragments-managing.md) zur formularbasierten Bearbeitung. | 6.5 LTS GA |

### Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden die Funktionen aufgeführt, die aus AEM 6.5 LTS entfernt wurden. In früheren Versionen wurden diese Funktionen als veraltet gekennzeichnet.

| Bereich | Funktion | Ersatz | Version (SP) |
| --- | --- | --- | --- |
| Commerce  | AEM CIF Classic wird nicht unterstützt. | Migrieren Sie zu [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Lösungen | Social/Communities wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Screens | Screens werden nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Assets | `dam-pim` und `dam-rating` werden nicht unterstützt, da Bundles von Social abhängig sind. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Assets | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` wurde entfernt. | Verwenden Sie die hinzugefügte alternative API `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()`. | 6.5 LTS GA |
| Portal | AEM Portal Director wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Granite | Bundle `com.adobe.granite.socketio` wird entfernt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Granite | `com.adobe.granite.crx-explorer` wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Granite | `crx2oak` wird nicht unterstützt. | Wählen Sie die relevante Version von [Oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) aus. | 6.5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Guava | Alle Guava-Abhängigkeiten sind jetzt aus AEM entfernt und daher ist das Bundle `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` nicht Teil von AEM. | Kunden können Guava selbst hinzufügen, wenn sie von Guava abhängig sind, oder Guava-Code durch Java-Sammlungen oder andere Alternativen ersetzen, sofern möglich. | 6.5 LTS GA |
| `We.Retail` | Die Beispiel-Site `We-retail` wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Open Source | Bundle `oak-solr-osgi` wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Open Source | `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` und `org.apache.sling.atom.taglib` werden nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Open Source | `org.apache.commons.io`-Pakete werden jetzt aus `org.apache.commons.commons-io` exportiert. | Keine Änderung erforderlich. | 6.5 LTS GA |
| Open Source | `javax.mail`-Pakete werden aus dem Bundle `com.sun.javax.mail` exportiert. | Keine Änderung erforderlich. | 6.5 LTS GA |
| Open Source | `org.apache.jackrabbit.api`-Pakete werden jetzt aus dem Bundle `org.apache.jackrabbit.oak-jackrabbit-api` exportiert. | Keine Änderung erforderlich. | 6.5 LTS GA |
| Open Source | `com.github.jknack.handlebars` wird nicht unterstützt | Wählen Sie die relevante [Version](https://mvnrepository.com/artifact/com.github.jknack/handlebars) aus | 6.5 LTS GA |


## Bekannte Probleme {#known-issues}

<!-- DO THESE KNOWN ISSUES CARRY OVER EACH RELEASE? THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST. -->

### Problem mit dem JSP-Scripting-Bundle in AEM 6.5.21–6.5.23 und AEM 6.5 LTS GA

AEM 6.5.21, 6.5.22, 6.5.23 und AEM 6.5 LTS GA werden mit dem Bundle `org.apache.sling.scripting.jsp:2.6.0` ausgeliefert, das ein bekanntes Problem enthält. Das Problem tritt in der Regel bei hoher Auslastung auf, wenn die AEM-Instanz viele Anfragen gleichzeitig verarbeitet.

Wenn dieses Problem auftritt, kann eine der folgenden Ausnahmen in den Fehlerprotokollen neben Verweisen auf `org.apache.sling.scripting.jsp:2.6.0` angezeigt werden:

* `java.io.IOException: classFile.delete() failed`
* `java.io.IOException: tmpFile.renameTo(classFile) failed`
* `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
* `java.io.FileNotFoundException`

Zur Lösung dieses Problems ist Hotfix [cq-6.5.lts.0-hotfix-NPR-42640](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-NPR-42640-1.2.zip) verfügbar.

### Dispatcher-Verbindungsfehler mit Nur-SSL-Funktion (behoben in AEM 6.5 LTS SP1 und höher){#ssl-only-feature}

>[!NOTE]
>
> Dieses Problem tritt nur in AEM 6.5 LTS GA auf.

Bei der Aktivierung der Funktion „Nur SSL“ in AEM-Bereitstellungen gibt es ein bekanntes Problem, das die Verbindung zwischen dem Dispatcher und AEM-Instanzen beeinträchtigt. Nach Aktivierung dieser Funktion können Konsistenzprüfungen fehlschlagen und die Kommunikation zwischen dem Dispatcher und AEM-Instanzen kann unterbrochen werden. Dieses Problem tritt insbesondere auf, wenn Kundinnen und Kunden versuchen, eine Verbindung über `https + IP` von Dispatcher zu AEM-Instanzen herzustellen. Dies steht im Zusammenhang mit SNI-Validierungsproblemen (Server Name Indication).

**Auswirkungen:**

* Konsistenzprüfungsfehler mit HTTP 400-Antwort-Codes
* Unterbrochener Traffic zwischen Dispatcher und AEM-Instanzen
* Inhalte können nicht ordnungsgemäß über den Dispatcher bereitgestellt werden
* Verbindungsfehler bei Verwendung von HTTPS mit IP-Adressen in der Dispatcher-Konfiguration
* HTTP 400-Fehler vom Typ „Ungültige SNI“ bei der Verbindung über HTTPS + IP

**Betroffene Umgebungen:**

* AEM-Bereitstellungen mit Dispatcher-Konfigurationen
* Systeme, in denen die Funktion „Nur SSL“ aktiviert wurde
* Dispatcher-Konfigurationen mit der Verbindungsmethode `https + IP` zu AEM-Instanzen

**Lösung:**
Wenn dieses Problem auftritt, wenden Sie sich an den Adobe-Kundensupport. Zur Lösung dieses Problems ist Hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) verfügbar. Versuchen Sie nicht, „Nur SSL“-Funktionen zu aktivieren, bis Sie den erforderlichen Hotfix angewendet haben.

## Enthaltene OSGi- und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in [!DNL Experience Manager] 6.5 LTS, Service Pack 1 enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt:

* [Liste der in Experience Manager 6.5 LTS, Service Pack 1 enthaltenen OSGi-Bundles](/help/release-notes/assets/65lts_sp1_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5 LTS, Service Pack 1 enthaltenen Inhaltspakete](/help/release-notes/assets/65lts_sp1_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/de/docs/customer-one/using/home).

