---
title: Aktuelle Versionshinweise für Adobe Experience Manager 6.5 LTS, SP1
description: Aktuelle Versionsinformationen zu Adobe Experience Manager 6.5 LTS, Service Pack 1 finden Sie.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 8c726951cbd99660d2cfd23abef8857a6f4fcf36
workflow-type: tm+mt
source-wordcount: '4939'
ht-degree: 31%

---

# Aktuelle Versionshinweise für Adobe Experience Manager 6.5 LTS, SP1 {#release-notes}

## Versionshinweise {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Version | Service Pack 1 (SP1) <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | &#x200B;21. August 2025 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://artifactory.corp.adobe.com/artifactory/maven-aem-release-local/com/adobe/aem/cq-quickstart/6.6.1/cq-quickstart-6.6.1.jar) |

<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

## Was in [!DNL Adobe Experience Manager] 6.5 LTS, SP1 enthalten ist {#what-is-new}

<!-- UPDATE EACH RELEASE -->

[!DNL Experience Manager] 6.5 LTS enthält SP1 neue Funktionen, wichtige von Kundschaft angeforderte Verbesserungen und Fehlerbehebungen. Dazu gehören auch Verbesserungen hinsichtlich Leistung, Stabilität und Sicherheit, die seit der ersten Verfügbarkeit von 6.5 LTS im März 2025 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install-update) auf 6.5 LTS.

## Wichtige Funktionen und Verbesserungen

<!-- 6.5 LTS REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE EACH RELEASE -->

## Es wurden Probleme in 6.5 LTS, Service Pack 1 behoben {#fixed-issues}

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

### [!DNL Sites]{#sites-65-LTS-SP1}

#### Barrierefreiheit {#sites-accessibility-65-lts-sp1}

* Es wurde ein Problem behoben, bei dem das Texteditorelement in Inhaltsfragmenten standardmäßig abgeschnitten wurde. Der Texteditor zeigt jetzt den gesamten Inhalt ohne Kürzung an. (SITES-33005)
* Es wurde ein Problem behoben, bei dem durch Klicken auf URL-Pfade die Startseite von Indigo anstelle der richtigen Ziel-URL geöffnet wurde. (SITES-33004)
* Es wurde ein Barrierefreiheitsproblem in einer benutzerdefinierten AEM-Komponente behoben, das während automatisierter Tests zu ADA-Kompatibilitätsfehlern führte. (SITES-30660)
* Fehlerkorrektur - Die ADA-Konformität im Warndialogfeld und in Workflow-Nachrichten wird nicht mehr hergestellt, da der Text auf hellem Hintergrund schwarz angezeigt wird und die WCAG 2.0-Kontrastanforderungen erfüllt. (SITES-30138)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem der Schaltfläche „Kategorie“ im AEM Sites-Editor eine bestimmte Beschriftung fehlte, was dazu führte, dass JAWS sie als „Menü für Bildschaltflächen“ ankündigte, anstatt eine beschreibende Beschriftung bereitzustellen. (SITES-27497)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem Häkchensymbole im Bildschirm Gültige Berechtigungen keinen Alternativtext hatten, sodass JAWS ihre Bedeutung nicht lesen und vermitteln konnte. (SITES-27272)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem die Seite Berechtigungen keine klare JAWS-Ankündigung zum Entfernen von Benutzer- oder Gruppenberechtigungen bereitstellte, was zu Verwirrung bei Benutzenden der Bildschirmlesehilfe führte. (SITES-27238)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem Fehlermeldungen nur als Symbole ohne beschreibenden Text angezeigt wurden, sodass JAWS die Fehler nicht ankündigen konnte, wenn sie auftraten. (SITES-27155)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem JAWS falsche und unklare Schaltflächenbeschreibungen in der AEM On-Premise-Umgebung las, einschließlich fehlendem Überschriftentext der Ebene 2 für den Modulabschnitt. (SITES-27152)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem JAWS die Anzahl der Ergebnisse nach dem Filtern von Werten auf der Registerkarte &quot;AEM Assets&quot; nicht ankündigte. (SITES-27150)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem beim Erstellen eines Ordners keine Bestätigung angezeigt wurde und JAWS sie nicht in der Assets-Benutzeroberfläche angekündigt hat. (SITES-27141)
* Es wurde ein Barrierefreiheitsproblem in AEM Sites behoben. JAWS meldete keine Formularfehler, der Fokus wurde auf nicht interaktive Fehlerelemente verschoben, und Fehler in Pflichtfeldern konnten nicht auf der Registerkarte angezeigt werden. (SITES-27138)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem dem Schaltflächenmenü Timelines eine bestimmte Beschriftung fehlte, was dazu führte, dass JAWS nur das „Schaltflächenmenü für Aktivitäten“ las, ohne eine klare Beschreibung bereitzustellen. (SITES-27134)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem JAWS die Aktion oder Rolle für Container-Elemente nicht ankündigte und nur „Breadcrumb v1“ und „Schaltfläche v2“ anstelle von beschreibenden Beschriftungen las. (SITES-27131)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem das Popup Quick Publish keine ordnungsgemäße Erfolgsmeldung lieferte, sodass Bildschirmlesehilfen kein Feedback zum Abschluss ankündigten. (SITES-26912)
* Es wurde ein Barrierefreiheitsproblem in der Korallenspaltenansicht behoben, bei dem Elemente mit ARIA-Rollen, für die untergeordnete Rollen erforderlich sind, sie nicht enthielten, was zur Nichteinhaltung von Barrierefreiheitsstandards führte. (SITES-26898)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem Texte für „Vorlagen“ und „Eigenschaften“ in der oberen Navigation der Erstellungsseite im Reflow-Modus nicht sichtbar waren, was den Zugriff für Benutzende von Tastatur und Bildschirmlesehilfe verhinderte. (SITES-26895)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem QuickInfos für die Symbole „Suche“, „Lösung“, „Hilfe“, „Posteingang“ und „Benutzer“ in der oberen Navigationsleiste nicht über die Tastaturnavigation zugänglich waren. (SITES-26889)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem Formularfelder auf der Registerkarte Allgemein keine Fehlervorschläge lieferten, sodass Benutzende keine Anleitung erhalten konnten, wenn erforderliche Eingabefelder leer gelassen wurden. (SITES-26885)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem NVDA- und Sprachausgaben keine Vorlagendateidetails auf der Seite Erstellen ankündigten, sodass Benutzer keine vollständigen Informationen programmgesteuert erhalten konnten. (SITES-26884)
* Es wurde ein Barrierefreiheitsproblem behoben, das einen falschen Namen für das Textfeld „Seitentitel“ auf der Registerkarte Allgemein verwendete, wodurch Bildschirmlesehilfen keine korrekten Informationen für Benutzende bereitstellten. (SITES-26879)
* Die Vorder- und Hintergrundfarben der Schaltfläche wurden aktualisiert, um die Anforderungen an das Mindestkontrastverhältnis von WCAG 2.2 AA zu erfüllen und die Lesbarkeit und Barrierefreiheit für alle Benutzer zu verbessern. (SITES-26877)
* Es wurde ein Problem behoben, das dazu führte, dass die Texte „Vorlage“ und „Eigenschaften“ in der oberen Navigation der Seite „Erstellen“ nach der Größenanpassung ausgeblendet wurden, um für Sehbehinderte Sichtbarkeit und Barrierefreiheit sicherzustellen. (SITES-26872)
* Es wurde ein Fehler behoben, der dazu führte, dass nach dem Anwenden eines Reflusses mehrere horizontale Bildlaufleisten auf der Hauptseite angezeigt wurden, um sicherzustellen, dass eine einzige Bildlaufleiste für ordnungsgemäße Barrierefreiheit und Sichtbarkeit des Inhalts angezeigt wurde. (SITES-26800)
* Es wurde ein Barrierefreiheitsproblem im AEM-Seiteneditor behoben, bei dem der Tastaturfokus nach dem Aktivieren von Schaltflächen wie „Persona“, „Warenkorb“ oder „Abgebrochen“ unerwartet auf den Anfang der demografischen Symbolleiste zurückgesetzt wurde. Der Fokus bleibt nun auf der aktivierten Schaltfläche, um eine konsistente Tastaturnavigation und Workflows für Bildschirmlesehilfen zu unterstützen. (SITES-25306)
* Es wurde ein Problem mit der Zuordnung von Barrierefreiheits-Labels für die Felder für Seitentitel und Tags behoben. Die Benutzeroberfläche von AEM ordnet Barrierefreiheits-Labels bei der Verwendung von Bildschirmlesehilfen wie JAWS nun den Feldern „Titel“ und „Seitentitel“ zu. Die Fehlerbehebung stellt das ordnungsgemäße Lesen von Labels sicher und verbessert die ADA-Konformität für Seitenerstellung, Eigenschaften und Verschiebungs-Workflows hinweg. (SITES-27149)
* Fehlende visuelle Labels für Felder zur Kommentareingabe in der Timeline wurden korrigiert. Fehlende visuelle Label für Eingabefelder vom Typ „Kommentar“ unter dem Abschnitt „Timeline“ wurden korrigiert, um die Barrierefreiheit zu verbessern. Durch die Aktualisierung wird sichergestellt, dass Bildschirmlesehilfen die Feld-Labels korrekt ausgeben können. Dieses Erlebnis verbessert die Navigation in und Übermittlung von Formularen für alle Benutzenden, insbesondere für diejenigen, die auf Hilfstechnologien angewiesen sind. (SITES-26903)
* Der Tastaturzugriff für die Schaltfläche mit den Auslassungspunkten in Timeline-Kommentaren wurde korrigiert. Die Tastaturnavigation für die Schaltfläche mit den Auslassungspunkten (drei Punkte) neben den Kommentaren im Abschnitt „Timeline“ wurde aktiviert. Benutzende können jetzt über die Tabulatortaste auf die Schaltfläche zugreifen und mit ihr interagieren, wodurch die Barrierefreiheit für Benutzende verbessert wird, die auf eine ausschließliche Tastaturnavigation angewiesen sind. (SITES-26891)
* NVDA-/Narrator-Ankündigungen für Suchergebnisse in Auswahldialogfeldern wurden verbessert. Das Feld „Auswahl-Dialogfeld öffnen“ wurde aktualisiert, um anzugeben, ob Suchergebnisse bei der Verwendung von Bildschirmlesehilfen wie NVDA oder Narrator gefunden werden oder nicht. Diese Verbesserung hilft Benutzenden, die auf Hilfstechnologien angewiesen sind, das Ergebnis ihrer Suchaktionen zu verstehen, ohne visuelle Bestätigung zu benötigen. (SITES-26883)
* Die ARIA-Rolle für das Symbol mit den Auslassungspunkten neben dem Feld zur Kommentareingabe wurde korrigiert. Das Symbol mit den Auslassungspunkten (drei Punkte) neben dem Feld zur Kommentareingabe wurde aktualisiert, damit es die richtige ARIA-Rolle verwendet. Dadurch wird sichergestellt, dass Bildschirmlesehilfen das Element genau identifizieren können. Diese Verbesserung optimiert die Compliance mit Barrierefreiheit und das Erlebnis für Benutzende, die auf Hilfstechnologien angewiesen sind. (SITES-26881)
* Ungültige ARIA-Attribute in Komponenten der Coral-Benutzeroberfläche wurden korrigiert. Die Komponenten der Coral-Benutzeroberfläche wurden aktualisiert, um sicherzustellen, dass alle ARIA-Attribute gültige Werte verwenden, wodurch die Compliance mit Barrierefreiheit verbessert wurde. Insbesondere wurden Fälle behandelt, in denen fälschlicherweise ungültige Werte wie `aria-modal="dialog"` zugewiesen wurden. Durch diese Verbesserung können Bildschirmlesehilfen Elemente von Dialogfeldern korrekt interpretieren, wodurch die Barrierefreiheit für Benutzende verbessert wird, die auf Hilfstechnologien angewiesen sind. (SITES-26873)
* Die Sichtbarkeit und QuickInfos für Symbole in Reflow-Szenarien wurde verbessert. Das Reflow-Verhalten wurde verbessert, um sicherzustellen, dass QuickInfos für die Symbole **Herunterladen**, **Assets erneut verarbeiten** und **Checkout** korrekt angezeigt werden. Der Fokus wurde auf ein Problem hinsichtlich der Barrierefreiheit gerichtet, bei dem Symbole und ihre Labels unsichtbar wurden, wenn die Viewport-Größe oder die Zoom-Einstellungen des Browsers geändert wurden. Diese Fehlerbehebung unterstützt Benutzende mit geringer Sehkraft, indem sie die Sichtbarkeit aufrechterhält und beim Reflow korrekte Symbolbeschreibungen bereitstellt. (SITES-26871)


#### Admin-Benutzeroberfläche{#sites-adminui-65-lts-sp1}

* Es wurde ein Barrierefreiheitsproblem behoben, bei dem JAWS keine Listenrollen ankündigte oder im Dialogfeld „Site erstellen“ keine Navigations- und Aktivierungsanweisungen bereitstellte. (SITES-30661)
* Die Unterstützung der Sprachausgabe für Statusmeldungen in der Sites-Filteransicht funktioniert erwartungsgemäß und stellt sicher, dass Benutzende beim Wechseln zwischen Ansichten ein klares und rechtzeitiges Feedback erhalten. (SITES-24992)
* Die Datumsauswahl in der Filterleiste wird vollständig in ihrem Container angezeigt, sodass eine angemessene Größe des Touch-Ziels gewährleistet ist und Probleme mit dem Beschneiden vermieden werden. (SITES-24988)
* Ausgewählte Filter-Tags verwenden jetzt semantische HTML- und ARIA-Labels, die der visuellen Darstellung entsprechen und so eine präzise Rollenunterstützung und klare Aktionen für Hilfstechnologien sicherstellen. (SITES-24980)
* Der Bereich Verweise-Leiste wurde ein aria-label-Attribut hinzugefügt, um Benutzenden von Bildschirmlesehilfen eine eindeutige, beschreibende Beschriftung zu bieten und eine konsistente Orientierungsidentifizierung über die gesamte Seite hinweg sicherzustellen. (SITES-24973)
* Die Leiste „Verweise“ wurde aktualisiert, um relative Einheiten für die Dimensionierung und Positionierung zu verwenden, sodass Inhalte skaliert werden können und voll funktionsfähig bleiben, wenn sie in einem 1280 x 1024-Darstellungsfeld auf 400 % gezoomt werden. (SITES-24972)
* Bestätigte Tabellenelemente in der Listenansicht der Sites-Startseite enthalten geeignete Spaltenkopfzeilen-Rollen, mit denen Bildschirmlesehilfen Kopfzeilen für jede Datenzelle ankündigen können. (SITES-24942)
* Die NVDA gibt jetzt das Änderungsdatum im Strukturverzeichnis bekannt, um sicherzustellen, dass Benutzende von Bildschirmlesehilfen vollständige Asset-Detailinformationen erhalten. (SITES-24782)
* Es wurde ein Problem behoben, bei dem die NVDA-Bildschirmlesehilfe angekündigt hat, dass der Text für Elemente in der Strukturverzeichniskomponente in AEM Sites unvollständig ist. Die NVDA liest jetzt den vollständigen Text für jedes Element, was die Barrierefreiheit und die Einhaltung verbessert. (SITES-24780)
* Es wurde ein Tastaturzugriff für den Window Splitter im Tree Directory hinzugefügt, sodass Benutzende die Größe der linken Seitenleiste nur mit einer Tastatur ändern können. (SITES-24779)
* Die Suchergebnisse des Hilfemenüs wurden aktualisiert, um korrekte ARIA-Rollen für Listenelemente einzuschließen und sicherzustellen, dass die Sprachausgabe Links ordnungsgemäß ankündigt, um die Barrierefreiheit zu verbessern. (SITES-24729)
* Es wurde ein Problem behoben, bei dem Bildschirmlesehilfen die Statusmeldung „X der Y Ergebnisse“ nicht ankündigten. Oder die Meldung „Keine Ergebnisse gefunden“, nachdem Filter im Sites-Filter-Bedienfeld angewendet wurden, um sicherzustellen, dass Benutzer eine ordnungsgemäße Bestätigung der Ergebnisse erhalten. (SITES-24720)
* Fehlende Rollenzuweisungen für Navigations-Links in der App-Navigation wurden korrigiert. Es wurden geeignete ARIA-Rollen hinzugefügt, um sicherzustellen, dass Bildschirmlesehilfen Navigationselemente korrekt identifizieren und ankündigen. (SITES-24719)
* Falsches Rasterrollen-Markup für ausgewählte Filter-Tags wurde durch Schaltflächenelemente ersetzt und barrierefreie Namen wurden hinzugefügt, um sicherzustellen, dass Bildschirmlesehilfen die Tags korrekt ankündigen und identifizieren. (SITES-24717)
* Es wurden Ankündigungen von Bildschirmlesehilfen für die Statusmeldung Verweise auf der Leiste hinzugefügt, wenn mehrere Auswahlen durchgeführt werden, um sicherzustellen, dass Benutzende eine Bestätigung von Änderungen erhalten. (SITES-24678)
* Das Suchfeldverhalten wurde korrigiert, sodass das erste Ergebnis nicht automatisch angekündigt wird. Die Sprachausgabe gibt jetzt die Anzahl der gefundenen Ergebnisse aus, sodass Benutzende ohne falsche Fokusankündigungen durch die Liste navigieren können. (SITES-24658)
* Falsche `aria-label` aus nicht interaktiven statischen Elementen in der Listenansicht entfernt, um zu verhindern, dass Bildschirmlesehilfen irreführende oder irrelevante Informationen angeben. (SITES-24515)
* Das Kontrollkästchen in der ersten Spalte der Listenansicht wurde so aktualisiert, dass der Text der Titelspalte als barrierefreier Name verwendet wird, sodass die Sprachausgabe den Zweck des Formularfelds genau wiedergibt. (SITES-24514)
* Es wurden geeignete ARIA-Attribute und Live-Regionsunterstützung hinzugefügt, um das Laden von Statusmeldungen für Benutzende von Sprachausgaben beim Navigieren durch Inhalte anzukündigen. (SITES-24481)
* Das responsive Design wurde aktualisiert, um horizontales Scrollen beim Zoomen von Inhalten auf 400 % mit einer Darstellungsfeldbreite von 1280 bis 1024 zu ×, sodass eine vollständige Sichtbarkeit ohne seitlichen Scrollen gewährleistet ist. (SITES-24308)
* Die Fokusnavigation in der Admin-Benutzeroberfläche von Sites wurde korrigiert, um einer logischen Reihenfolge zu folgen, wobei der Fokus nach dem Drücken von Esc auf die Schaltfläche „Alle auswählen“ zurückgesetzt und der Fokus nach dem Drücken der Tabulatortaste auf das nächste interaktive Element verschoben wurde. (SITES-24307)
* Die Fokusreihenfolge in der Admin-Benutzeroberfläche von Sites wurde aktualisiert, sodass die Breadcrumbs-Schaltfläche im `<betty-titlebar-title>`-Element während der Tastaturnavigation den Fokus in der richtigen Reihenfolge erhält. (SITES-24305)
* Es wurde eine Funktion zum Überspringen von Links überprüft, um sicherzustellen, dass der Tastaturfokus auf den Hauptinhaltsbereich verschoben wird, sodass Tastaturbenutzer Kopfzeilenelemente umgehen und effizient auf Inhalte zugreifen können. (SITES-24061)


#### Klassische Benutzeroberfläche{#sites-classicui-65-lts-sp1}

Es wurde ein Problem in der klassischen Benutzeroberfläche behoben, bei dem Kontrollkästchen-Bezeichnungen fehlten und HTML als kodierter Text in mehreren Benutzeroberflächenelementen, einschließlich Datumssuche und nicht standardmäßigen Benutzeroberflächen, angezeigt wurde. (SITES-31822)

#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp1}

AEM verhindert jetzt Leistungsbeeinträchtigungen durch falsch formatierte XMP-Metadaten in Bild-Assets. Assets, die ungültige oder nicht konforme XMP-Eigenschaftsnamen enthalten, z. B. solche mit numerischen Segmenten oder ungeeigneten Strukturen, lösen während der Verarbeitung keine wiederholten Warnprotokolle mehr aus. Das System filtert problematische Metadaten heraus, um sicherzustellen, dass Asset-Aufnahme und -Validierung fehlerfrei abgeschlossen werden. (SITES-30683)

<!--
#### [!DNL Content Fragments] - Admin{#sites-admin-65-lts-sp1} -->

#### [!DNL Content Fragments] – Fragmenteditor{#sites-fragments-editor-65-lts-sp1}

Andere Autorinnen und Autoren können Inhaltsfragmente selbst dann veröffentlichen, wenn sie von einer anderen Autorin oder einem anderen Autor ausgecheckt werden, was dem beabsichtigten Verhalten der Checkout-Funktion widerspricht. Diese Fehlerbehebung verhindert, dass andere Benutzende die Schaltflächen zum Veröffentlichen in der Authoring-Oberfläche sehen oder verwenden, wenn ein Inhaltsfragment ausgecheckt wird. (SITES-30578)

<!--
#### [!DNL Content Fragments] - GraphQL API {#sites-graphql-api-65-lts-sp1}

#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-65-lts-sp1}

#### [!DNL Content Fragments] - REST API{#sites-restapi-65-lts-sp1} -->

#### Komponentenkonsole{#sites-component-console-65-lts-sp1}

Es wurde ein Problem in der Produktlistenkomponente behoben, bei dem durch das Kontrollkästchen „Alle auswählen“ nur die ersten 20 SKUs von der ersten Seite hinzugefügt wurden, anstatt alle SKUs in den Suchergebnissen. (SITES-29191)

#### Core-Backend{#sites-core-backend-65-lts-sp1}

Falsch formatierte XMP-Metadaten haben bei der Verarbeitung von Bild-Assets im `ValidationDataServlet` einen Fehler ausgelöst. Die Fehlerbehebung stellt die konforme Verarbeitung von Metadaten sicher und vermeidet redundantes Parsen ungültiger Eigenschaften. (SITE-30683)

<!--
#### Core Components{#sites-core-components-65-lts-sp1}

#### Campaign integration{#sites-campaign-integration-65-lts-sp1}

#### Experience Fragments{#sites-experiencefragments-65-lts-sp1}

#### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp1}

#### Launches{#sites-launches-65-lts-sp1}

#### Link Checker{#sites-link-checker-65-lts-sp1} -->

#### MSM – Live Copies{#sites-msm-live-copies-65-lts-sp1}

* Fehlerkorrektur - Bei der erneuten Aktivierung der Vererbung von Ghost-Komponenten in AEM 6.5 On-Premise tritt jetzt kein JavaScript-`ns.ui.alert is not a function` mehr auf. (SITES-31993)
* Es wurde ein Problem behoben, bei dem die Option Rollout „Später“ es ermöglichte, ohne Auswahl eines Datums in AEM 6.5 fortzufahren. (SITES-31374)

#### Seiteneditor{#sites-pageeditor-65-lts-sp1}

* Es wurde ein Problem im Teaser-Modal behoben, bei dem auf der Registerkarte Link und Aktionen nach der gültigen Dateneingabe und Fehlerbehebung weiterhin Fehlerstile, Symbole und das Attribut „aria-invalid“ angezeigt wurden. (SITES-25527)
* Fehlerkorrektur - Im Teaser-Modal-Texteditor wird der erweiterte oder reduzierte Status der Listen- und Absatzschaltflächen nicht an Sprachausgaben weitergegeben, was eine genaue aria-erweiterte Attributaktualisierung gewährleistet. (SITES-25365)
* Es wurde ein Problem in der Demografie-Symbolleiste behoben, bei dem durch Anpassen des Warenkorb-Schiebereglers mit der Tastatureingabe der Fokus auf die Warenkorb-Schaltfläche verschoben wurde, anstatt den Fokus auf dem Schieberegler zu behalten, was die Navigationseffizienz für Tastaturbenutzer verbessert. (SITES-25324)
* Es wurde ein barrierefreier Name zum Warenkorb-Schieberegler in der Demografie-Symbolleiste hinzugefügt, indem dem zugehörigen `<label>` ein Wert zugewiesen wurde. Diese Fehlerbehebung verbessert die Kompatibilität mit Hilfstechnologien und verbessert die Benutzerfreundlichkeit für Benutzende von Bildschirmlesehilfen. (SITES-25322)
* ARIA-Rollen und barrierefreie Namen wurden zu den Schaltflächen in der Dropdown-Liste Demografie-Symbolleiste hinzugefügt. Diese Fehlerbehebung ermöglichte eine ordnungsgemäße Identifizierung durch Hilfstechnologien und eine verbesserte Navigation für Benutzende von Tastatur und Bildschirmlesehilfe. (SITES-25315)
* Das Layout der demografischen Symbolleiste wurde angepasst, um zu verhindern, dass Inhalte bei einem Browser-Zoom von 200 % über das Darstellungsfeld hinaus überlaufen. So wird sichergestellt, dass alle Steuerelemente ohne horizontales Scrollen zugänglich bleiben. (SITES-25309)
* Die Fokusverwaltung in der Demografie-Symbolleiste wurde korrigiert, damit der Tastaturfokus weiterhin auf der aktivierten Schaltfläche liegt, anstatt den Fokus auf die Startposition der Symbolleiste zurückzusetzen. (SITES-25306)
* Die Schaltflächenbeschriftung funktioniert wie vorgesehen und verwendet eine QuickInfo, um die Beschriftung anzuzeigen, wenn Modi mit ähnlichen Bildschirmbreiten aktiv sind. (SITES-25285)
* Das Anmerkungsmodal enthält eine sichtbare Senden-Schaltfläche, mit der Benutzende Anmerkungen senden können, ohne sich auf die Esc-Taste zu verlassen oder außerhalb des Modals zu klicken. (SITES-25281)
* Das Anmerkungsmodal enthält eine Stiftsymbol-Schaltfläche, mit der Benutzende Anmerkungen senden können, wodurch eine klare und zugängliche Übermittlungsmethode bereitgestellt wird. (SITES-25269)
* Die Ankündigungen der Bildschirmlesehilfen für die Schaltflächen Anmerken und Anmerken schließen wurden korrigiert, um genaues, relevantes Feedback zu geben und nicht verwandte oder verwirrende Informationen zu entfernen. (SITES-25268)
* Die Arbeitsflächen-Abschnitte auf den Seiten des AEM-Editors unterstützen jetzt den vollständigen Zugriff auf die Tastatur. Benutzende können Abschnittstitel und Schaltflächen zum Bearbeiten nur über die Tastatur aktivieren, ohne auf den Mauszeiger angewiesen zu sein. Diese Aktualisierung stellt die Einhaltung von WCAG 2.1.1 sicher und verbessert die Benutzerfreundlichkeit für Komponenten wie Teaser-, Bild-, Karussell-, Layout-, Timewarp- und Anmerkungsmodale hinweg. (SITES-25256)
* Unnötiges horizontales Scrollen im Karussell-Modal bei einer Breite von 320 Pixel entfernt, um sicherzustellen, dass alle Inhalte im Darstellungsfeld angezeigt werden, ohne dass eine seitliche Navigation erforderlich ist. (SITES-25254)
* Unnötiges horizontales Scrollen im Bild-Modal bei einer Breite von 320 Pixel entfernt, um sicherzustellen, dass alle Inhalte im Darstellungsfeld angezeigt werden, ohne dass eine seitliche Navigation erforderlich ist. (SITES-25244)
* Unnötiges horizontales Scrollen im Teaser-Modal bei einer Breite von 320 Pixel entfernt, um sicherzustellen, dass alle Inhalte im Ansichtsfenster angezeigt werden, ohne dass eine seitliche Navigation erforderlich ist. (SITES-25242)
* Die Tastaturnavigation für das `List`- und `Paragraph Format` Popup-Menü wurde sowohl im Teaser-Modal aktiviert. Mit dieser Fehlerbehebung können Benutzer mithilfe der Pfeiltasten auf diese Menüs zugreifen und darin navigieren. (SITES-25235)
* Die Ankündigungen der Sprachausgabe für die Schaltflächen Anmerken und Anmerken schließen wurden korrigiert, um ein genaues, relevantes Feedback zu erhalten, das auf die zugehörigen Aktionen abgestimmt ist. (SITES-25234)
* Die Beschriftung der Schaltfläche „Hilfe“ im Teaser-Modal wurde verbessert, um den Zweck klar zu beschreiben und einen aussagekräftigen Kontext für alle Benutzenden bereitzustellen, einschließlich Benutzender mit Hilfstechnologien. (SITES-25224)
* Der Emulator-Lineal für Benutzende von Bildschirmlesehilfen wurde verbessert, indem Linealmessungen mit ihren jeweiligen Geräten verknüpft wurden. Ersetzen Sie außerdem die QuickInfo durch ein aria-described by-Element. (SITES-24955)
* Es wurde keine Fehlerbehebung implementiert, da die Schaltfläche Bearbeiten wie vorgesehen funktioniert und einen informativen Kontext bietet, anstatt eine Aktion auszuführen. (SITES-24950)
* Die bestätigte Fokusreihenfolge auf der Editor-Seite folgt einer logischen Sequenz, sodass Benutzende durch alle interaktiven Elemente navigieren können, ohne unerwartet zu überspringen oder zurückzugehen. (SITES-24937)
* Bestätigte Arbeitsfläche im Vorschaumodus aktualisiert den Textabstand korrekt, wenn Benutzende benutzerdefinierte Textabstandseinstellungen anwenden, um eine konsistente Formatierung über alle Inhaltsbereiche hinweg sicherzustellen. (SITES-24936)
* Die überprüfte Vorschau-Schaltfläche ändert den Trigger-Kontext oder Status nicht mehr im Fokus, sodass Benutzer die Schaltfläche absichtlich aktivieren, bevor die Seitenansicht aktualisiert wird. (SITES-24784)
* Es wurden korrekte ARIA-Rollenzuweisungen zu App-Navigations-Links hinzugefügt, sodass Bildschirmlesehilfen Navigationselemente genau identifizieren und für bessere Barrierefreiheit ankündigen können. (SITES-24718)
* Die Schaltfläche Filter ändern wurde aktualisiert, um erweiterte und reduzierte Status für Bildschirmlesehilfen anzukündigen, redundante ARIA-Attribute zu entfernen und die Beschriftung anzupassen, um klare, nicht-duplizierende Beschreibungen bereitzustellen. (SITES-24713)
* Es wurden Ankündigungen der Sprachausgabe für Suchergebnisstatusmeldungen im Dialogfeld Linkauswahl hinzugefügt, um sicherzustellen, dass Benutzende eine Bestätigung erhalten, wenn Ergebnisse geladen werden oder keine Übereinstimmungen gefunden werden. (SITES-24700)
* Es wurden Ankündigungen der Bildschirmlesehilfe für den Ladestatus des Bild-Modals hinzugefügt, um sicherzustellen, dass Benutzende Feedback erhalten, wenn das Modal geladen wird und für die Interaktion bereit ist. (SITES-24697)
* Es wurde ein Barrierefreiheitsproblem behoben, bei dem der Sticky-Header den Teaser-Modal-Inhalt mit einem Zoom von 200 % und 400 % verdeckt hat, sodass eine vollständige Sichtbarkeit und Benutzerfreundlichkeit bei der Verwendung der Seitenvergrößerung gewährleistet ist. (SITES-24523)
* Dem Feld Suche/Filter wurde eine Statusmeldung mit der Anzahl der Suchergebnisse hinzugefügt, sodass die Sprachausgabe die Ergebnisse den Benutzern mitteilen kann. (SITES-24506)
* Es wurden Ankündigungen von Sprachausgaben für die Anzahl der Suchergebnisse im Feld Suche/Filter hinzugefügt, um sicherzustellen, dass Benutzer beim Laden der Ergebnisse sofort Feedback erhalten. (SITES-24505)
* Der Registerkartenliste im Seitenleisten-Bereich wurde ein barrierefreier Name hinzugefügt, damit die Sprachausgabe den Zweck in Übereinstimmung mit den WAI-ARIA-Richtlinien angeben kann. (SITES-24492)
* Mehrdeutigen Editor-Symbolen wurden beschreibende Beschriftungen hinzugefügt, um sicherzustellen, dass alle Benutzer die Funktion jeder Schaltfläche klar verstehen. (SITES-24480)
* Vollständige Tastaturbedienung für Abschnittstitel und Aktionsschaltflächen in der Arbeitsfläche aktiviert, um einen konsistenten Betrieb für Maus- und Tastaturbenutzer sicherzustellen. (SITES-24479)

<!--
#### Replication{#sites-replication-65-lts-sp1}

#### Rich Text Editor{#sites-rte-65-lts-sp1} -->

#### Universeller Editor {#sites-universal-editor-65-lts-sp1}

* Fehlerkorrektur - In QueryTokenService tritt jetzt keine Race-Bedingung mehr auf, die zu fehlerhaften Anmeldungen führt, wenn mehrere Anfragen mit Abfrageparametern ausgelöst werden, bevor der Anmelde-Token-Service ein Ergebnis zurückgibt. (SITES-30659)
* Es wurde ein Problem in UniversalEditorURLService behoben, bei dem beim Speichern eines Arrays von zugeordneten Pfaden in Felix ConfigMgr nur das erste Element beibehalten wurde. (SITES-30292)

### [!DNL Assets]{#assets-65-lts-sp1}

Es wurde ein Problem behoben, bei dem durch das Synchronisieren von Assets von Remote-DAM-Sites mit der lokalen AEM der Veröffentlichungsstatus und replikationsbezogene Eigenschaften aus Assets entfernt wurden. (Assets-48958)

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

Behobene OSGi-Abhängigkeitszyklen, die die Funktion der HTL Script Engine Factory blockierten, sodass eine ordnungsgemäße Service-Auflösung und Skriptausführung sichergestellt war. (GRANITE-58275)

#### Integrationen{#foundation-integrations-65-lts-sp1}

* Die Verwendung von commons-httpclient 3.x wurde aus dem `com.adobe.cq.cq-analytics-integration`-Bundle entfernt und durch `org.apache.httpcomponents.httpclient` 4.5.13.B0001 ersetzt, um sie an die neuesten AEM 6.5 LTS-Standards anzupassen. (CQ-4360586)
* Das veraltete Search&amp;Promote-Integrations-Bundle wurde aus AEM entfernt, um nicht verwendete Komponenten zu entfernen und den Wartungsaufwand zu reduzieren. (CQ-4358030)
* Es wurden neue Backend-Testfälle für die SiteCatalyst-Integration hinzugefügt, um die Analytics-Validierung zu verbessern und eine umfassendere Abdeckung sicherzustellen. (CQ-4359991)
* Es wurde ein Problem im Abschnitt Eigenschaften der Launch-Konfiguration behoben, bei dem die Dropdown-Listen Firma und Eigenschaft nicht angezeigt wurden. Außerdem lösten Speichern und schließen Fehler aus, obwohl alle Pflichtfelder ausgefüllt sind, und es wurden falsche Fehlermeldungen für „Unternehmen“ und „Eigenschaft“ angezeigt, wenn nur das Feld „Titel“ leer war. (CQ-4359853)
* Der Eintrag für den `searchpromote`-Servlet-Pfad wurde aus Version 6.6 entfernt, um ihn an die Entfernung des Search&amp;Promote-Bundles anzupassen. (CQ-4359523)
* Es wurden HTTP-Testfälle für das Ziel-Repository korrigiert, um eine genaue Validierung und verbesserte Testzuverlässigkeit zu gewährleisten. (CQ-4359022)
* Die Verwendung des Guava-Caching wurde aus dem Modul integration-adobeIMS-console entfernt, um Guava-Bibliotheksabhängigkeiten zu beseitigen. (CQ-4358710)
* Validierte Workflows zur DTM-Integration, Posteingangsaufgaben und Projektfunktionen in AEM 6.6, um einen ordnungsgemäßen Betrieb in AEM 6.5 sicherzustellen. (CQ-4358151)
* Validierte Insight-Funktionen für Inhalte in AEM 6.6, um Kompatibilität und ordnungsgemäßen Betrieb in AEM 6.5 sicherzustellen. (CQ-4357774)
* Validierte Cloud Services-Funktionen in AEM 6.6, um Kompatibilität und ordnungsgemäßen Betrieb in AEM 6.5 sicherzustellen. (CQ-4357773)
* Die Integration der Adobe IMS-Konsole in AEM 6.6 wurde validiert, um Kompatibilität und ordnungsgemäßen Betrieb in AEM 6.5 sicherzustellen. (CQ-4357772)
* Die Jenkins-Pipeline für die Test&amp;Target-Integration wurde aktualisiert, sodass sie auf Java 17 ausgeführt wird, fehlschlagende Selenium-Tests auflöst, ausgewählte Tests nach Playwright verschiebt und sicherstellt, dass alle Modultests erfolgreich sind. (CQ-4357770)
* DX-Integrationen, Workflow, Posteingang und Projekte wurden an die Verzweigung 6.6.0 angepasst, indem Build- und Test-Pipelines aktualisiert wurden. Beheben von Problemen mit der Upgrade-Kompatibilität und Überprüfen aller betroffenen Services auf Stabilität und Funktionalität. (CQ-4357767)

<!--
#### Jetty{#foundation-jetty-65-lts-sp1} -->

#### Lokalisierung{#foundation-localization-65-lts-sp1}

* Die Zeichenfolgen im Dialogfeld „Zugriffssteuerung entfernen“ von der Liste „Berechtigungen“ wurden lokalisiert, um die richtigen Übersetzungen anzuzeigen. (GRANITE-59427)
* Fehlerkorrektur - Im Dialogfeld zum Hinzufügen von Regeln im Modell-Editor für „ODER-Teilungs-Eigenschaften“ wurden mehrere Zeichenfolgen der Benutzeroberfläche, einschließlich Operatoren und Feldbezeichnungen, nicht lokalisiert angezeigt. Alle Zeichenfolgen werden jetzt mit korrekter Lokalisierung angezeigt. (CQ-4354014)
* Es wurde eine fehlende Übersetzung für die QuickInfo „Beschreibung anzeigen für“ im Dialogfeld zum Bearbeiten von Workflow-Modellen hinzugefügt. (CQ-4347996)

#### Oak {#foundation-oak-65-lts-sp1}

Es wurde ein Problem behoben, bei dem AEM vorhandene Konfigurationsdateien unter `/apps/system/config` während eines Upgrades neu erstellt oder umbenannt und `.cfg.json` durch `.config` Dateien ersetzt hat. (GRANITE-58899)

#### Omnisearch{#foundation-omnisearch-65-lts-sp1}

Es wurde ein Barrierefreiheitsproblem behoben, bei dem Platzhalter fälschlicherweise als Beschriftungen für Eingabefelder angezeigt wurden. Dieses Problem führt zu fehlenden Feldbeschriftungen in den Modellen Suche, AEM Experience Fragments, Inhaltsfragmente und Inhaltsfragmente. (GRANITE-61791)

<!--
#### Platform{#foundation-platform-65-lts-sp1} -->

#### Projekte{#foundation-projects-65-lts-sp1}

* Es wurde ein Problem behoben, bei dem beim Löschen eines Projekts in der Kalenderansicht trotz erfolgreicher Projektlöschung ein falsches Fehler-Popup angezeigt wurde. (CQ-4358890)
* Es wurde ein Problem in Firefox behoben, bei dem die Kartenfußzeile „Asset-Sammlung“ in der Projektansicht über den Kartenrahmen hinausging. Die Fußzeile wird nun korrekt ausgerichtet, ohne dass sie sich überschneidet. (CQ-4353317)

#### Schnellstart{#foundation-quickstart-65-lts-sp1}

* Das Deinstallationsskript wurde aktualisiert, um den Versionsbereich für das Guava-Bundle anzupassen, sodass es bei der Installation über den Package Manager nicht auf die Blockierungsliste gesetzt werden kann. (GRANITE-59559)
* Behebung eines mehrteiligen Konfigurationsfehlers, der beim Hochladen von AEMFD-Paketen auf Tomcat 11 mit JDK 17 aufgetreten ist, durch Aktualisieren der Server-Konfiguration zur Unterstützung großer Paketinstallationen, ohne Parsing-Fehler auszulösen. (GRANITE-58327)
* Fehlerkorrektur - In der Replikations-Benutzeroberfläche wird jetzt beim Bearbeiten von Replikationsagenten kein Fehler mehr angezeigt (`#1660`), indem die Handhabung von klassischen Kontrollkästchen in der Benutzeroberfläche korrigiert wird. (GRANITE-58302)
* Es wurden mehrere Startfehler für den S3-Datenspeicher beim Ausführen von AEM 6.5 LTS mit JDK 21 behoben, indem fehlende Service-Berechtigungen adressiert, die Konfigurationsverarbeitung aktualisiert und sichergestellt wurde, dass die erforderlichen Services korrekt initialisiert wurden. (GRANITE-57082)
* Definierte die Wartungs- und Instandhaltungsstrategie für AEM 6.5. Diese Fehlerbehebung umfasste Folgendes:
   * Service Pack-Kadenz.
   * Hotfix-Kadenz.
   * Parallele Unterstützung zu AEM 6.6.
   * Aktualisierte Support-Matrix.
   * Add-on-Verantwortlichkeiten für Eigentümer. (GRANITE-50459)

<!--
#### Security{#foundation-security-65-lts-sp1} -->

#### Sling{#foundation-sling-65-lts-sp1}

* Sling ResourceAccessSecurity wurde auf Version 1.1.2 aktualisiert, um ein `ClassCastException` zu beheben, das beim Initialisieren von `ResourceAccessGate` durch mehrere `ResourceAccessSecurityImpl` aufgetreten ist. (NPR-42750)
* Es wurde ein Problem bei der Adobe Stock-Integration behoben, bei dem das Lizenzdialogfeld ausgegraut erschien. Dieses Problem war auf das Entfernen erforderlicher Eingabefelder durch die `sunt:initList` zurückzuführen. Die Funktion wurde in den Client-Bibliotheken der Coral Foundation gefunden. Die Client-Bibliotheken wurden aktualisiert, um die erforderlichen Felder beizubehalten und eine ordnungsgemäße Funktion des Lizenzdialogfelds zu ermöglichen. (NPR-42748)
* Fehlerkorrektur - Die Fehlerbehebung für das Sling-Skripting, das während der Paketinstallation zu `DataTimeParseException`- und `String.length()`-Nullzeiger-Ausnahmen führte, wurde rückportiert. Sling Scripting wurde auf Version 2.8.3-1.0.10.6 aktualisiert, um Installationsfehler zu reduzieren und die Stabilität zu verbessern. (NPR-42640)

<!--
#### Translation{#foundation-translation-65-lts-sp1} -->

#### Benutzeroberfläche{#foundation-ui-65-lts-sp1}

* Es wurde ein Problem in der AEM Author-Benutzeroberfläche behoben, durch das die Anzeige von Benutzergruppen auf 41 beschränkt wurde. Dieses Problem war auf ein standardmäßiges Batch-Limit in der Gruppenauswahlkomponente der Granite-Benutzeroberfläche zurückzuführen. Die Komponente wurde so aktualisiert, dass alle Gruppen ohne Abschneiden angezeigt werden. (NPR-42749)
* Es wurde ein Problem im Assistenten zur On-Premise-Seitenerstellung behoben, bei dem erforderliche Felder in Komponenten mit mehreren Feldern beim Bearbeiten der Seiteneigenschaften nicht erneut überprüft wurden. Dieses Problem wiederum ermöglichte es Autoren, die Validierung zu umgehen und mit unvollständigen Daten fortzufahren. (GRANITE-58826)
* ARIA-Attribute für die Schaltfläche „Hilfe“ in AEM wurden korrigiert, um sicherzustellen, dass die JAWS-Bildschirmlesehilfen eine klare, benutzerfreundliche Beschriftung angeben, anstatt unübersetzte Symbol- und Textmetadaten anzuzeigen. (GRANITE-55360)

#### WCM{#foundation-wcm-65-lts-sp1}

* Es wurde Java 17-Unterstützung für AEM Translations hinzugefügt, indem Übersetzungspakete aktualisiert, die Kompatibilität mit Java-Paketen überprüft, veraltete Abhängigkeiten entfernt und durch umfassende Tests die volle Funktionalität sichergestellt wird. (CQ-4357525)
* Unzureichende Evergreen-`com.adobe.cq.platform.it.http.workflow.inbox.InboxOnOffTimeIT.testActivateLater` entfernt, um Fehlschläge während automatisierter Tests zu verhindern. (CQ-4298376)

#### Workflow{#foundation-workflow-65-lts-sp1}

* Das fehlende `data-detailsurl`-Attribut wurde in Posteingangselementen hinzugefügt, um zu verhindern, dass undefinierte Werte in URLs angezeigt werden, wenn AEM 6.5 LTS mit Java 21 verwendet wird. (GRANITE-60158)
* Fehlerkorrektur - Bei der Ausführung von AEM 6.5 LTS mit Java 21 kommt es jetzt nicht mehr zu einer NullPointerException in der `deactivate`-Methode des `WorkflowToPublishEventService`-Bundles, sodass ein ordnungsgemäßes Herunterfahren des Workflow-Services ohne Fehler gewährleistet ist. (GRANITE-58151)
* Der Workflow-Index wurde aktualisiert, um die Freigabe, Out-of-Office-Anpassung und Behebung von Zeitleisten-Abfrageproblemen zu unterstützen. (GRANITE-52640)
* Der Workflow-Index wurde aktualisiert, um die Freigabe, Abwesenheitsanpassungsfunktionen und die Behebung von Zeitleisten-Abfrageproblemen zu unterstützen. (GRANITE-52294)
* Fehlerkorrektur - Erhöhte Fehlerprotokollfehler während der Validierung von Protokollvergleichen wurden für ein Programm-Upgrade auf AEM Version 10912 behoben, wodurch eine stabile Ausführung des Workflows gewährleistet ist. (GRANITE-44268)
* Die URL-Bereinigungsmethode in Workflow-Repos wurde aktualisiert, um `url.searchParams` durch `url.search` zu ersetzen und so den XSS-Schutz für anfällige URLs zu verbessern. (CQ-4359585)
* Validierte Workflow-, Posteingang- und Projektfunktionen in AEM 6.6 Forms, um einen ordnungsgemäßen Betrieb und eine ordnungsgemäße Integration sicherzustellen. (CQ-4358777)
* Es wurde eine Automatisierung zur Freigabe von Workflow-Inhaltsartefakten über Jenkins implementiert, was optimierte und konsistente Bereitstellungsprozesse in AEM 6.5 ermöglicht. (CQ-4358472)
* Fehlerkorrektur - Im Workflow zum Erstellen einer Aufgabe im Posteingang wird das Dialogfeld „Aufgabe hinzufügen“ nicht geschlossen, nachdem auf „Senden“ geklickt wurde, obwohl die Aufgabe erstellt wurde. Dies ist auf einen JavaScript-Syntaxfehler zurückzuführen. (CQ-4355336)
* Es wurde ein Problem behoben, das das Speichern der Konfiguration der Ansicht des Posteingangs aufgrund einer fehlenden Eigenschaftsdefinition für `isEndUserConfigurationEnabled` verhinderte. (CQ-4287757)




## [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Die Plattform von [!DNL Adobe Experience Manager] 6.5 LTS basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java™ Content-Repository Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x wird als Servlet-Engine für den Schnellstart verwendet.

### Java™-Unterstützung  {#java-support}

* Unterstützung für Java™ 17 und Java™ 21.
* Um eine optimale Leistung zu erzielen, überschreiben Sie die GC-Standardwerte mit anderen Werten. Weitere Informationen finden Sie im Abschnitt [Installieren und Aktualisieren](/help/sites-deploying/custom-standalone-install.md).
* Adobe verteilt Wartungs-Updates für Java™ 17 und Java™ 21 für die Verwendung durch Kunden in AEM-bezogenen Projekten, sofern diese nicht über Oracle öffentlich verfügbar sind.

### UberJar-Verpackung {#uber-jar-packaging}

* Es gibt einen geringfügigen Unterschied beim Verpacken von Uber Jar in AEM 6.5 LTS. Weitere Informationen finden Sie unter [Aktualisieren der Uber Jar-Version von AEM](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Aktualisieren {#upgrade}

* Weitere Informationen zum Upgrade-Verfahren finden Sie unter [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md).

## Installieren und Aktualisieren {#install-update}

Informationen zu Setup-Anforderungen finden Sie unter [Installationsanweisungen](/help/sites-deploying/custom-standalone-install.md).

Detaillierte Anweisungen finden Sie unter [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> Für neue AEM 6.5 LTS-Installationen müssen Indexdefinitionen separat installiert werden. Weitere Informationen finden Sie in [diesem Artikel](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

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
|---|---|---|---|


### Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden die Funktionen aufgeführt, die aus AEM 6.5 LTS entfernt wurden. In früheren Versionen wurden diese Funktionen als veraltet gekennzeichnet.

| Bereich | Funktion | Ersatz | Version (SP) |
|--- |--- |--- |--- |



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

### Dispatcher-Verbindungsfehler mit Funktion nur SSL {#ssl-only-feature}

Bei der Aktivierung der Funktion „Nur SSL“ in AEM-Bereitstellungen gibt es ein bekanntes Problem, das die Verbindung zwischen dem Dispatcher und AEM-Instanzen beeinträchtigt. Nach Aktivierung dieser Funktion können Konsistenzprüfungen fehlschlagen und die Kommunikation zwischen dem Dispatcher und AEM-Instanzen kann unterbrochen werden. Dieses Problem tritt insbesondere auf, wenn Kundinnen und Kunden versuchen, eine Verbindung über `https + IP` von der Dispatcher zu AEM-Instanzen herzustellen. Dies steht im Zusammenhang mit SNI-Validierungsproblemen (Server Name Indication).

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

In den folgenden Textdokumenten sind die in dieser Version [!DNL Experience Manager] 6.5 LTS, Service Pack 1 enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt:

* [Liste der in Experience Manager 6.5 LTS, Service Pack 1 enthaltenen OSGi-Bundles](/help/release-notes/assets/65lts_sp1_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5 LTS enthaltenen Inhaltspakete, Service Pack 1](/help/release-notes/assets/65lts_sp1_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/de/docs/customer-one/using/home).

