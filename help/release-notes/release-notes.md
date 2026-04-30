---
title: Aktuelle Versionshinweise zu Adobe Experience Manager 6.5 LTS, SP2
description: Hier finden Sie die aktuellen Versionsinformationen zu Adobe Experience Manager 6.5 LTS, Service Pack 2.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: f015c4fb30bbba2ec0de7290d37ee56e182d2ddc
workflow-type: tm+mt
source-wordcount: '7427'
ht-degree: 100%

---


# Aktuelle Versionshinweise zu Adobe Experience Manager 6.5 LTS, SP2 {#release-notes}

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Version | Service Pack 2 (SP2) <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | 19. Februar 2026 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.2.jar) |


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> **Obligatorischer Hotfix:** Um SNFE-Probleme (SegmentNotFoundException) mit der Offline-Komprimierung bei der Installation von SP2 zu vermeiden, installieren Sie den unter [Bekannte Probleme – Repository-Beschädigung während der Online-Komprimierung](#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146) beschriebenen Hotfix.

## Inhalt von [!DNL Adobe Experience Manager] 6.5 LTS, SP2 {#what-is-new}

<!-- UPDATE EACH RELEASE -->

[!DNL Experience Manager] 6.5 LTS, SP2 umfasst neue Funktionen, wichtige kundenseitig angeforderte Verbesserungen und Fehlerbehebungen. Diese Version enthält zudem Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von Version 6.5 LTS im März 2025 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install-update) auf 6.5 LTS.

## Wichtigste Funktionen und Verbesserungen

**AEM Sites**

AEM 6.5 LTS SP2 enthält jetzt OpenAPIs für [Inhaltsfragment- und Modellverwaltung](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/65lts/) und [Launches](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/launches/). Diese APIs bieten Zugriff auf Inhaltsfragmente und Launches zur Bearbeitung und Planung. Sie verwenden dieselben modernen OpenAPIs wie AEM as a Cloud Service.

**AEM Forms**

**Inhalt von AEM Forms 6.5 LTS SP2**

* Unterstützung für RDBMK mit JBoss® EAP 8.0 wurde hinzugefügt.

* Verbessertes Benutzererlebnis im visuellen Regeleditor. Dieses Update enthält:

   * Automatisches Neuladen der Zusammenfassungsansicht nach einem Speichervorgang, um den aktualisierten Regelstatus anzuzeigen

   * Anzeige der Schaltflächen „Hinzufügen“/„Löschen“ und Möglichkeit zum Umschalten statt Ausblenden

   * Eindeutiges Feedback, wenn ein Regelspeichervorgang nicht erfolgreich war (FORMS-21261)

* Laufzeit-API (Application Programming Interface) wurde hinzugefügt, um den alten Exportmodus der Extensible Markup Language (XML) in AEM Forms umzuschalten. Dies ersetzt den Parameter „`Dcom.adobe.fd.forms.export.legacy`“. Diese Verbesserung ermöglicht es Benutzenden, effizienter zwischen Exportmodi zu wechseln, was die Flexibilität des Workflows verbessert. (FORMS-23115)

* Unterstützung für JavaScript Object Notation (JSON) mit Namespace-Tags in adaptiven Formularen wurde hinzugefügt. Diese Verbesserung ermöglicht es Benutzenden, JSON-Datenstrukturen effektiver zu verarbeiten, wodurch die Datenintegration und -verarbeitung verbessert wird. (FORMS-22519)

* Option „Nachweis herunterladen“/„Formular übermitteln“ wurde im Regeleditor als vordefinierte Schaltfläche hinzugefügt. Diese Verbesserung ermöglicht es Kundinnen und Kunden, die Funktion „downloadDoR“ zu verwenden, ohne benutzerdefinierten Code zu schreiben, was die Benutzerfreundlichkeit und Effizienz verbessert. (FORMS-21263)

* Unterstützung für JavaScript Object Notation (JSON) mit Namespace-Tags in adaptiven Formularen wurde hinzugefügt. Diese Verbesserung ermöglicht es Benutzenden, Formulare genauer und effizienter vorzubefüllen, wodurch die Datenintegration verbessert und Fehler durch manuelle Eingaben reduziert werden. (FORMS-10883)

<!-- UPDATE THE EACH RELEASE -->

## Behobene Probleme in 6.5 LTS, Service Pack 2 {#fixed-issues}

### [!DNL Sites]{#sites-65-LTS-SP2}

#### Barrierefreiheit {#sites-accessibility-65-lts-sp2}

* Die Textkomponente verlor den Tastaturfokus, wenn Autorinnen und Autoren während der Bearbeitung im Komponenten-Browser den Mauszeiger über Elemente bewegten. Dadurch wurde die Eingabe unterbrochen und ein Barrierefreiheitsfehler gemäß WCAG 3.2.1 ausgelöst. Die Korrektur verhindert, dass beim Bewegen der Maus der Fokus verschoben wird, und hält die Textkomponente während der Interaktion mit dem Komponenten-Browser im Fokus. (SITES-35370)
* Die Fokusverwaltung im Rich-Text-Feld „Beschreibung“ wurde korrigiert, sodass die Vorwärtsnavigation mit der Tabulatortaste nicht mehr blockiert wird. Benutzende blieben im RTE stecken, weil die Komponente einen nicht standardmäßigen Tastaturbefehl zum Verschieben des Fokus verwendete, was die erwartete Dialogfeldnavigation blockierte. Die Änderung erzwingt die standardmäßige Tastaturinteraktion und behält die logische Tab-Sequenzierung im gesamten Dialogfeld bei. (SITES-35228)
* Ein Problem im Sites-Editor wurde behoben, das das erwartete Verhalten während der Seitenbearbeitung störte und zu inkonsistenter Komponenteninteraktion führte. Bei Autorinnen und Autoren traten unzuverlässige Benutzeroberflächenreaktionen auf, die mit standardmäßigen Bearbeitungsaufgaben interferierten und die Effizienz des Workflows verringerten. Die Aktualisierung optimiert die zugrunde liegende Editor-Logik und stellt eine stabile, vorhersehbare Interaktion über die betroffenen Komponenten hinweg wieder her. (SITES-35227)
* Eine Regression unterbrach den Asset-Wähler im Seiten-Editor und verhinderte das Laden in bestimmten Seitenbearbeitungs-Szenarien. Autorinnen und Autoren können den Asset-Wähler jetzt normal öffnen und verwenden, wenn sie beim Bearbeiten einer Seite Assets auswählen oder durchsuchen. Diese Änderung stellt den konsistenten Zugriff auf Asset-Auswahl-Workflows wieder her, durch die Ladefehler unterbrochen wurden. (SITES-35226)
* Ein Problem im Sites-Editor wurde behoben, das zu inkonsistentem Verhalten während der Seiteninteraktion führte und standardmäßige Authoring-Workflows störte. Der Fehler führte zu unerwarteten Benutzeroberflächenreaktionen, die die Komponentenkonfiguration und Inhaltsaktualisierungen beeinträchtigten. Das Update stabilisiert die betroffenen Funktionen und stellt die zuverlässige Ausführung von Bearbeitungsaktionen über Seiten hinweg wieder her. (SITES-35225)
* Ein Fehler in der Sites-Authoring-Oberfläche wurde behoben, der zu inkonsistentem Verhalten während der Seitenbearbeitung führte und normale Workflows störte. Bei Autorinnen und Autoren traten unerwartete Benutzeroberflächenreaktionen auf, die die Komponenteninteraktion und Inhaltsaktualisierungen beeinträchtigten. Die Aktualisierung stabilisiert die betroffenen Funktionen und stellt ein zuverlässiges und vorhersehbares Verhalten in allen Bearbeitungsszenarien wieder her. (SITES-35224)
* AEM Sites bietet jetzt `alt`-Textunterstützung für Bilder, um ADA- und WCAG-Anforderungen zu erfüllen. In der Seitenausgabe werden `alt`-Attribute nicht mehr ausgelassen, sodass Bildschirmlesehilfen korrekten Alternativtext erhalten. (SITES-27153)
* Das Layout der Symbolleiste „`Note Add`“ wurde korrigiert, sodass sich die Schaltfläche „Hinzufügen“ bei einer Viewport-Breite von 320 Pixeln nicht mehr mit dem Titel überschneidet. Reflow-Funktion auf kleinen Bildschirmen wurde verbessert, sodass die Steuerelemente bei 400 % Zoom lesbar und verwendbar bleiben. (SITES-25376)
* Fehlende Ansagen von Bildschirmlesehilfen bezüglich Fehler beim Auswählen von Links in Dialogfeldern wurden behoben. Die Benutzeroberfläche gibt Fehlertext jetzt über einen Statusmeldungs-Container aus, sodass die NVDA die Nachricht vorliest, sobald sie angezeigt wird. (SITES-25368)
* ARIA-Raster- und Rasterzellenrollen wurden aus der Asset-Liste in der Seitenleiste entfernt. Die standardmäßige Listensemantik und die Tastaturfokusreihenfolge wurden wiederhergestellt, was die Navigation der Bildschirmlesehilfen verbessert und zusätzliche Tabstopps reduziert hat. (SITES-25361)
* Die Fokussequenzierung in den Assets der Seitenleiste wurde korrigiert. Tastaturbenutzende erreichen jetzt alle Asset-Aktionen, einschließlich „Bearbeiten“, über einen konsistenten Registerkartenpfad. (SITES-25360)
* Layout-Überlauf im Assets-Modal „Suche“ bei einer Viewport-Breite von 320 Pixeln wurde behoben. Modal-Inhalte brechen jetzt korrekt um und bleiben lesbar, sodass sich Steuerelemente nicht mehr überschneiden oder das Dialogfeld überlaufen wird. (SITES-25330)
* NVDA-Ausgabe für die Schaltfläche „Bearbeiten“ wurde korrigiert. NVDA sagt jetzt die Aktion „Bearbeiten“ an, nicht „Vorschau-Schaltfläche gedrückt“. (SITES-25320)
* Unbenannte Texteingaben in der Symbolleiste „Demografie“ wurden korrigiert, die eine stumme oder generische Ausgabe von Bildschirmlesehilfen verursachten. Jede Eingabe hat jetzt einen klaren, Label-basierten barrierefreien Namen, der die Tastaturnavigation und die Navigation mit Hilfstechnologien verbessert. (SITES-25316)
* Tastaturfokusreihenfolge für die Symbolleiste „Demografie“ während der Navigation in der Layout-Vorschau wurde korrigiert. Die Registerkartennavigation wechselt jetzt direkt von der Schaltfläche „Demografie“ zu den Symbolleistensteuerelementen, ohne zur sekundären Symbolleiste zu springen. (SITES-25305)
* Falsche Ansagereihenfolge für die Label „Kleinere Bildschirme&quot; und „Tablet“ auf dem Lineal „Layout bearbeiten“ wurde korrigiert. Bildschirmlesehilfen geben diese Label nun an den richtigen Linealmarken aus, die dem Seitenlayout entsprechen. (SITES-25291)
* Ein Überlauf der Symbolleiste „Layout bearbeiten“ bei 200 % Zoom wurde behoben. Inhalte bleiben jetzt innerhalb des Viewports und sind durch Scrollen erreichbar. (SITES-25288)
* Falsche Fokusreihenfolge im Overlay „Anmerkungen“ wurde korrigiert. Die Tabulatortaste durchläuft jetzt Overlay-Steuerelemente und Anmerkungselemente. Die übergeordnete Seite erhält nicht mehr den Fokus hinter dem Overlay. (SITES-25282)
* Die Fokusbehandlung im Popover für Farbfelder wurde korrigiert. Das Dialogfeld verschiebt den Fokus jetzt auf einen klaren Titel und startet die Ausgabe der Bildschirmlesehilfe an diesem Einstiegspunkt. NVDA liest nicht mehr den vollständigen Inhalt des Dialogfelds außerhalb der Reihenfolge vor. (SITES-25275)
* Die Fokusbehandlung des Modals „Timewarp“ nach dem Schließen der Datumsauswahl wurde korrigiert. `Escape` legt den Fokus jetzt wieder auf die Schaltfläche „Datumsauswahl“. Bei der Auswahl eines Datums wird jetzt der Fokus auf das Eingabefeld neben dem Steuerelement „Datumsauswahl“ gelegt, wodurch der Verlust des Fokus und der Aufruf der Hintergrundseite verhindert werden. (SITES-25264)
* Tastaturfokusbehandlung für das Dialogfeld „Anmerkung löschen“ wurde korrigiert. Mit „Abbrechen“ wird jetzt der Fokus auf das Steuerelement „`Delete`“ zurückgesetzt, das das Dialogfeld geöffnet hat, und nicht mehr auf das Steuerelement „Hexadezimalwert bestätigen“. Nach dem Abbrechen sagen Bildschirmlesehilfen keinen irrelevanten Dialogfeldinhalt mehr an. (SITES-25258)
* Fokusbehandlung für das Modal „Anmerkung“ wurde korrigiert. Das Öffnen des Dialogfelds legt jetzt den Fokus auf den Dialogtitel und verhindert, dass NVDA Arbeitsflächeninhalte und irrelevanten Dialogfeldtext liest. Die Tastaturnavigation bleibt jetzt bis zum Schließen innerhalb des Dialogfelds. (SITES-25257)
* Layout-Probleme im Modal „Suchen“ bei einer Breite von 320 Pixeln wurden behoben. Modal-Inhalte brechen jetzt korrekt um und überlappen sich nicht mehr mit dem Baumverzeichnis. Benutzende können Ergebnisse anzeigen und im Verzeichnis navigieren, ohne dass Steuerelemente verdeckt werden. (SITES-25246)
* Text im Modal „Suchen“ wird nicht mehr abgeschnitten, wenn sich der Textabstand ändert. Das Baumverzeichnis-Layout bleibt jetzt stets klar getrennt, sodass Label und Einträge lesbar bleiben. Benutzende können jetzt die Suche und Navigation ohne überlappenden oder abgeschnittenen Text durchführen. (SITES-25245)
* Durch Aktivieren von „Kommentar einfügen“ wird der Tastaturfokus jetzt in den Anmerkungsinhalt verschoben, nicht auf die Schaltfläche „Anmerkungsmodus beenden“. Die Tabulatorreihenfolge folgt einer logischen Reihenfolge und hält die relevanten Steuerelemente ohne Rückwärtsnavigation erreichbar. (SITES-25241)
* Die Links „Datum einstellen“ und „Timewarp beenden“ hatten bei der Tastaturnavigation keinen sichtbaren Fokusindikator. Die Benutzeroberfläche rendert jetzt einen eigenen Stil mit kontrastreichem Fokus, sodass Benutzende den aktiven Link auf einen Blick erkennen können. (SITES-25232)
* Der Titel des Modals „Teaser“ hindert Tastaturbenutzende nicht mehr daran, das Dialogfeld zu verschieben. Tastatursteuerelemente ermöglichen jetzt Aktionen zum Aufnehmen, Verschieben und Ablegen, was die Benutzerfreundlichkeit von Bildschirmlesehilfen und die allgemeine Bedienbarkeit verbessert. (SITES-25226)
* AEM verwendet jetzt ein aussagekräftiges barrierefreies Label für die Schaltfläche „Info“ im Modal „Teaser“. Bildschirmlesehilfen sagen einen eindeutigen Aktionsnamen anstelle des Alt-Text-Strings für das Standardsymbol an. (SITES-25223)
* Bildschirmlesehilfen sagen jetzt die richtige Aktion an, wenn Benutzende die Schaltfläche „Bearbeiten“ aktivieren. Die NVDA meldet nicht mehr „Vorschau-Schaltfläche gedrückt“, was irreführendes Feedback war und Missverständnisse bei der Tastaturnavigation verursachte. (SITES-25208)
* Beim Erweitern der linken Leiste wird der Tastaturfokus jetzt auf das erste Steuerelement der linken Leiste verschoben. Die Tabulatorsequenz springt nicht mehr zur sekundären Symbolleiste oder landet mitten in der Liste, sodass Tastaturbenutzende Inhalte der linken Leiste ohne Rückwärtsnavigation erreichen können. (SITES-24998)
* Der Inhalt der Leiste für den Geräteemulator bleibt jetzt bei einer Viewport-Breite von 320 Pixeln vollständig sichtbar. Der Text und die Steuerelemente der Symbolleiste werden umbrochen statt abgeschnitten, wodurch Überlappungen reduziert und die Lesbarkeit verbessert werden. (SITES-24953)
* AEM zeigt jetzt das vollständige iPhone-Geräte-Label in der Symbolleiste „Emulator“ an. Text wird bei Standardbreite nicht mehr abgeschnitten, was die Lesbarkeit und die Klarheit der Geräteauswahl verbessert. (SITES-24952)
* Tabellenüberschriften der Listenansicht zeigen den Sortierstatus jetzt über ARIA an. Bildschirmlesehilfen sagen nach einer Spaltensortierung die auf- oder absteigende Reihenfolge an. (SITES-24943)
* AEM behält jetzt in der Kartenansicht die Sichtbarkeit des Menü-Labels „Weitere Aktionen“ bei, wenn sich der Textabstand ändert. Menüoptionen behalten den vollständigen Text, einschließlich „Quick Publish“, und das Menü bleibt bei allen WCAG-Textabstandseinstellungen lesbar. (SITES-24941)
* In der Kartenansicht wird jetzt in der Menüleiste für Kartenaktionen ein barrierefreier Name angezeigt. Bildschirmlesehilfen sagen den Zweck der Menüleiste klar an, und die Sprachsteuerung kann das Steuerelement anhand des Namens auswählen. (SITES-24938)
* Die Kartenansicht nutzt nicht länger die ARIA-Rastersemantik, die ein verwirrendes Verhalten von Bildschirmlesehilfen verursachte. Die Benutzeroberfläche bietet jetzt aussagekräftige Rollen und Label für Karteninhalte und die Kartenaktionsleiste, wodurch die Anzahl der übersprungenen Steuerelemente bei Verwendung der Tastatur reduziert wird. (SITES-24933)
* Die QuickInfo „`Delete Modal`“ wird jetzt jedes Mal angezeigt, wenn Benutzende mit der Maus auf das QuickInfo-Symbol zeigen. Fokusaktionen zeigen jetzt denselben QuickInfo-Text an, was den wiederholten Zugriff für Maus- und Tastaturbenutzende verbessert. (SITES-24778)
* Die Navigation in der linken Leiste folgt jetzt der erwarteten Tastaturfokusreihenfolge, nachdem Benutzende die Leiste konfiguriert haben. Der Tabulatorfokus wechselt zum ausgewählten Bereich der linken Leiste statt zu „Anzeige wechseln“, wodurch die Navigationsklarheit der Bildschirmlesehilfe verbessert wird. (SITES-24754)
* Falsches NVDA-Feedback während der Farbfeld-Navigation im Modal „Benutzereinstellungen“ wurde behoben. NVDA liest jetzt das Label des Farbfelds, das den Fokus erhält, wodurch irreführende Farbausgaben entfernt werden. Das Farbfeld-Set unterstützt jetzt eine konsistente Tastaturnavigation und eine klare Erkennung der Auswahl. (SITES-24739)
* Ausführliche NVDA-Ausgabe für das Steuerelement „`Spin`“ wurde reduziert. Redundante Gruppen-Label, die zu doppelten Eingabe-Labeln führten, wurden entfernt, sodass NVDA den Namen des Steuerelements nur einmal ansagt. Die Navigation mit der Tastatur und Bildschirmlesehilfen gibt jetzt eine einzige, klare Ansage aus. (SITES-24725)
* Im Dialogfeld „Karussell“ wird der Fokus nun auf den Dialogfeldtitel statt auf die Registerkarte „Elemente“ verschoben. „Abbrechen“ und „Esc“ geben den Fokus an das Steuerelement zurück, das das Dialogfeld gestartet hat, wodurch die ausführliche NVDA-Ausgabe reduziert wird. (SITES-24716)
* Das Dialogfeld für die Link-Auswahl richtet nun das programmgesteuerte Label am Bildschirm-Label für Baumstrukturelemente der letzten Ebene aus. Die Pfeiltasten-Navigation löst eine verlässliche Ansage der Bildschirmlesehilfe für jedes Element aus und entfernt irreführende Label-Ausgaben. (SITES-24710)
* Das Auswahldialogfeld zum Öffnen von Links wird jetzt bei einer Viewport-Breite von 320 Pixeln korrekt angezeigt. Der Inhalt überläuft das Modal nicht mehr und wird nicht abgeschnitten und das Modal zeigt keine horizontale Bildlaufleiste mehr an. (SITES-24709)
* Das Auswahldialogfeld zum Öffnen von Links legt den Tastaturfokus nach Schließen oder Abbrechen jetzt wieder auf den Auslöser des Dialogfelds. Der Fokus springt nicht mehr zur Link-Eingabe, wodurch der Kontext der Bildschirmlesehilfe stabil bleibt und die zusätzliche Navigation reduziert wird. (SITES-24707)
* Das modale Dialogfeld „Bild“ folgt jetzt einer logischen Fokussequenz. Der Fokus überspringt nach dem Abbrechen nicht mehr frühere Steuerelemente oder fällt auf den Orientierungspunkt der Seite zurück, und Benutzende haben nach dem Beenden wieder den Fokus auf der Schaltfläche „Konfigurieren“. (SITES-24693)
* Das modale Dialogfeld „Leiste „Verweise““ erhält jetzt den Tastaturfokus. Tab und Die Umschalt+Tab bleiben innerhalb der Dialogfeldsteuerelemente und der Fokus wechselt nicht mehr auf Seiteninhalte. Bildschirmlesehilfen sagen nur den Inhalt des Dialogfelds an. (SITES-24683)
* Das Modal „Hyperlink-Pfadauswahl“ legt jetzt beim Öffnen den Fokus auf den Dialogfeldtitel. „Abbrechen“ schließt das Dialogfeld und verschiebt den Fokus auf die Schaltfläche zum Öffnen des Auswahldialogfelds, wodurch Fokusverluste und redundante Ausgaben von Bildschirmlesehilfen verhindert werden. (SITES-24672)
* Das Suchfeld verwendet jetzt ein persistentes Label anstelle von Platzhaltertext. Das Label bleibt während der Eingabe sichtbar, wodurch die Klarheit für Benutzende von Tastatur, Bildschirmlesehilfen und Sprachsteuerung verbessert wird. (SITES-24529)
* Das modale Dialogfeld „Teaser“ legt den Fokus beim Öffnen jetzt auf den Dialogfeldtitel. Beim Schließen des Dialogfelds wird der Fokus wieder auf das Steuerelement „`Configure`“ gesetzt, wodurch Fokusverluste und übermäßig viele Ausgaben der Bildschirmlesehilfen verhindert werden. (SITES-24522)
* Das Seitenleisten-Panel „Assets“ enthält jetzt ein Steuerelement zum Schließen. Durch Schließen wird der Tastaturfokus auf den Umschalter für die Seitenleiste zurückgesetzt und das erzwungene Durchblättern des Bereichsinhalts wird verhindert. (SITES-24489)
* Die Tabulatortaste auf der Tastatur spricht jetzt Schaltflächen und Links in Admin-Tabellen an. Benutzende müssen sich bei der Suche nach interaktiven Steuerelementen nicht mehr auf die Zellennavigation mit den Pfeiltasten beschränken. (SITES-24285)
* Das Dialogfeld „Bildkomponente“ exponiert dekorative Hilfs- und Vollbildsymbole nicht mehr als Bilder. Bildschirmlesehilfen überspringen jetzt diese Symbole, sodass der Fokus auf ausführbaren Steuerelementen und Feldinhalten verbleibt. (SITES-2940)
* Sites Admin entfernt jetzt die Rolle „Bild“ aus den Miniatursymbolen für Ordner. Die Hilfstechnologie überspringt diese dekorativen Elemente und behält den Fokus auf Ordnernamen und Aktionen. (SITES-2852)
* Die Inhaltsstruktur leitet jetzt den Tastaturfokus zum aktiven Baumstrukturelement oder ersten Baumstrukturelement weiter. Der Baum-Container fungiert nicht mehr als leerer Tabstopp, was den Erhalt des Fokus bei Umschalt+Tab verhindert. (SITES-1577)

#### Admin-Benutzeroberfläche{#sites-adminui-65-lts-sp2}

Die Listenansichtseinstellungen der Sites-Konsole spiegelten nicht die in der Listenansicht angezeigten Spalten wider. Das Dialogfeld wurde mit deaktivierten Kontrollkästchen und der falschen Anzahl ausgewählter Spalten geöffnet. Die Korrektur synchronisiert den Dialogfeldstatus mit den aktiven Rasterspalten und aktualisiert den Zähler entsprechend der tatsächlichen Spaltensichtbarkeit. (SITES-38576)

#### Klassische Benutzeroberfläche{#sites-classicui-65-lts-sp2}

Bei der Bearbeitung der klassischen Textkomponente wurden nach einem Upgrade unformatierte HTML-Tags anstelle von Rich-Text angezeigt. Service Pack 2 korrigiert das Rendering des RTE (Rich-Text-Editor) in der klassischen Benutzeroberfläche, sodass der Editor formatierte Inhalte anzeigt und gespeichertes Markup beibehält. Die Korrektur stoppt auch die Markup-Erweiterung bei wiederholtem Bearbeitungen und Speichervorgängen. (SITES-38709)

#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp2}

Bei der Unterstützung für Headless-Eventing fehlten die erforderlichen OSGi-Ereignisse für Inhaltsfragmente und -modelle in 6.5 LTS. Das Update fügt das Eventing-Bundle sowie die erforderlichen Abhängigkeiten hinzu und enthält einen 6.5 LTS-Build. Inhaltsfragment- und Modellereignisse werden jetzt korrekt ausgelöst und unterstützen Launches-API-Workflows. (SITES-35329)

#### [!DNL Content Fragments] – Admin{#sites-admin-65-lts-sp2}

* Die Komponentenverarbeitung in der Authoring-Oberfläche von Sites wurde angepasst, um unregelmäßiges Verhalten während Seitenaktualisierungen zu stoppen. Der Fehler führte zu unvorhersehbaren Editor-Reaktionen, die routinemäßige Inhaltsänderungen beeinträchtigten und die Workflow-Effizienz verringerten. Die Aktualisierung stimmt die Editor-Logik mit den erwarteten Interaktionsmustern ab und bietet eine zuverlässige Leistung bei Authoring-Aktivitäten. (SITES-35078) KRITISCH

* Eine Regression führte zu einer Unterbrechung der Assets-Konsolen-Listenansicht für Inhaltsfragmente und löste einen Fehler beim Rendern der Liste aus. Durch die Aktualisierung wird die Listenansichtslogik nach dem Entfernen der Vorschau-Info korrigiert und die stabile Listenausgabe wiederhergestellt. Die Konsole zeigt jetzt Inhaltsfragmente ohne Fehler an und hält Listeninteraktionen nutzbar. (SITES-38683)
* Der Inhaltsfragment-Editor lokalisiert jetzt das Tag-Label. Der Editor lokalisiert auch das Label für Sammlungen, sodass der Benutzeroberflächentext mit dem ausgewählten Gebietsschema übereinstimmt. (SITES-977)


#### [!DNL Content Fragments] – Fragmenteditor{#sites-fragments-editor-65-lts-sp2}

* Die Tags von Inhaltsfragmentvarianten verschwanden, wenn der Funktionsumschalter nach der Refaktorierung deaktiviert blieb. Die Korrektur stellt die Unterstützung von Varianten-Tags wieder her, auch wenn dieser Umschalter deaktiviert bleibt. Autorinnen und Autoren können im Inhaltsfragment-Editor wieder Varianten-Tags hinzufügen und anzeigen. (SITES-38682) KRITISCH
* Bearbeitete Inhaltsfragmente verschwanden aus der Assets-Konsolenliste, nachdem Autorinnen und Autoren aus dem Inhaltsfragment-Editor zurückkehrten. Die Browser-Zwischenspeicherung gab eine veraltete Liste zurück und das aktualisierte Fragment blieb bis zu einer manuellen Aktualisierung ausgeblendet. Durch die Korrektur wird eine Cache-Steuerelementverarbeitung für den Rückkehrpfad des Editors hinzugefügt, damit die Liste korrekt neu geladen wird und das bearbeitete Fragment sichtbar bleibt. (SITES-35374) KRITISCH

* Der Inhaltsfragment-RTE zeigte Layout- und visuelle Probleme nach den letzten Änderungen des Benutzeroberflächensstils. Service Pack 2 optimiert die RTE-Formatierung, sodass die Symbolleiste und der bearbeitbare Bereich korrekt dargestellt werden und lesbar bleiben. Der Inhaltsfragment-Editor wird jetzt am Erscheinungsbild und Verhalten des Seiteneditors ausgerichtet. (SITES-38684)
* Das Entfernen von IMS-Bereichen aus dem Polaris-Asset-Wähler unterbrach die Integration von Inhaltsfragmenten mit dem Bereitstellungsendpunkt. Autorinnen und Autoren erfuhren Fehler beim Öffnen des Remote-Asset-Wählers und beim Auswählen von Assets. Die Aktualisierung fügt die erforderlichen IMS-Bereiche wieder hinzu und stellt den stabilen Zugriff auf die Bereitstellungsebene wieder her. (SITES-35837)
* Das Panel „Zugehörige Inhalte“ rendert keinen hart-codierten Platzhalter „undefiniert“ mehr. Der Inhaltsfragment-Editor löst diesen Text jetzt durch Lokalisierungsressourcen auf, sodass Bearbeitende übersetzten Text in der Benutzeroberfläche sehen. (SITES-33675)
  <!-- REMOVED FROM BUG LIST FEBRUARY 13, 2026 * Preview error messaging now uses localized strings instead of raw `Cannot print fragment's Json` text. The Content Fragment Editor now shows translated output across locales during GraphQL endpoint resolution failures. (SITES-33666)-->
* Im Inhaltsfragment-Editor wird jetzt ein übersetztes Label der Registerkarte „Allgemein“ für alle Gebietsschemata angezeigt. Der Editor ersetzt nicht lokalisierten Registerkartentext und entfernt interne IDs aus Registerkartentiteln. (SITES-30715)
* Der Inhaltsfragment-Editor zeigt jetzt übersetzte Namen für zulässige Asset-Typen an. In der Auswahlliste werden keine internen Zeichenfolgen und Nur-Englisch-Label mehr gemischt, wenn Autorinnen und Autoren Einschränkungen für Inhaltsreferenzen konfigurieren. (SITES-29699)

#### [!DNL Content Fragments] – GraphQL-API {#sites-graphql-api-65-lts-sp2}

* Die Validierung von GraphQL-Abfragen wurde optimiert, um Bereitstellungsfehler zu verhindern, die durch Fehler bei der Filterausführung verursacht wurden. Der Fehler verursachte Ausnahmen beim Anwendungsstart und blockierte den erfolgreichen Rollout in betroffenen Umgebungen. Die Revision stellt ein konsistentes Validierungsverhalten sicher und ermöglicht eine reibungslose Bereitstellung ohne Unterbrechung der Abfragevalidierung zur Laufzeit. (SITES-34301) KRITISCH

* Das Dialogfeld „GraphQL-Endpunkt bearbeiten“ zeigt jetzt lokalisierte Zeichenfolgen der Benutzeroberfläche an. Das Dialogfeld zeigt keinen reinen englischen Text mehr an, z. B. „GraphQL schema is taken from configuration“ (Das-Schema wird aus der Konfiguration übernommen), und die zugehörigen Label werden in allen Gebietsschemata korrekt dargestellt. (SITES-34018)

#### [!DNL Content Fragments] – GraphQL-Abfrage-Editor{#sites-graphql-query-editor-65-lts-sp2}

* Die Validierung von GraphQL-Abfragen wurde optimiert, um Bereitstellungsfehler zu verhindern, die durch Fehler bei der Filterausführung verursacht wurden. Der Fehler verursachte Ausnahmen beim Anwendungsstart und blockierte den erfolgreichen Rollout in betroffenen Umgebungen. Die Revision stellt ein konsistentes Validierungsverhalten sicher und ermöglicht eine reibungslose Bereitstellung ohne Unterbrechung der Abfragevalidierung zur Laufzeit. (SITES-35529)
* GraphQL Explorer schlägt nicht mehr fehl, wenn der Name eines Konfigurations-Browsers CJK-Zeichen enthält. Die Endpunkterstellung und der gespeicherte Abfragezugriff funktionieren normal und die Seite des GraphQL-Abfrage-Editors bleibt fehlerfrei. (SITES-31616)

#### [!DNL Content Fragments] – Modell-Editor{#sites-model-editor-65-lts-sp2}

* Verschachtelte Inhaltsfragmentmodelle funktionierten nicht mehr, wenn die Funktion durch Refaktorierung mit einem deaktivierten Umschalter verknüpft wurde. Die Korrektur stellt die Unterstützung verschachtelter Modelle wieder her, ohne dass Änderungen am Umschalter erforderlich sind. Autorinnen und Autoren können im Modell-Editor wieder verschachtelte Modelle erstellen und verwenden. (SITES-38681) KRITISCH

* Das Filter-Panel für Inhaltsfragmentmodelle exponiert keine nicht lokalisierten Zeichenfolgen mehr. AEM zeigt jetzt lokalisierte Filter-Label und lokalisierte Statuswerte für alle Gebietsschemata an. (SITES-30863)
* Der Inhaltsfragmentmodell-Editor rendert jetzt lokalisierte Zeichenfolgen für das Dialogfeld zum Sperren von Warnungen. Die Benutzeroberfläche ersetzt nicht lokalisierte englische Nachrichten durch Gebietsschema-Ressourcen in allen unterstützten Sprachen. (SITES-28592)

#### [!DNL Content Fragments] – REST-API{#sites-restapi-65-lts-sp2}

AEM Headless benötigte eine dedizierte Versionsverzweigung, um Abhängigkeiten und Paketversionskonflikte mit Mainline-Builds zu vermeiden. Das Update fügt eine Headless-Verzweigung „`release/6.5lts`“ hinzu und stimmt Abhängigkeitssätze und Paketversionen ab. Jenkins erstellt die Headless-Code-Basis jetzt sauber und ohne Versionskonflikte. (SITES-36585)

<!-- #### Component console{#sites-component-console-65-lts-sp2} -->

#### Inhalts-API{#sites-content-api-65-lts-sp2}

Durch einen Fehler beim Funktionsumschalter wurde ein falscher Status der Seitenverwaltungs-API gemeldet. Die Aktualisierung fügt ein dediziertes Aktivierungs-Flag hinzu und wertet es zusammen mit dem vorhandenen Umschalter aus. Die Seitenverwaltungs-API zeigt jetzt einen stabilen Status an. Die Site-Management-API bleibt experimentell. (SITES-39284)

#### Core-Backend{#sites-core-backend-65-lts-sp2}

* Eine Änderung des Authoring-Erlebnisses in Sites wurde eingeführt, um inkonsistentes Verhalten zu beheben, das die standardmäßigen Seitenbearbeitungs-Workflows störte. Autorinnen und Autoren stießen beim Interagieren mit Komponenten auf unerwartete Ergebnisse, die die Inhaltsaktualisierung beeinträchtigten und die Zuverlässigkeit reduzierten. Durch die Änderung wird das stabile Editor-Verhalten wiederhergestellt und die konsistente Ausführung von Authoring-Aktionen in den betroffenen Szenarien sichergestellt. (SITES-35162) KRITISCH

* Das Authoring-Verhalten von Sites wurde optimiert, um ein Problem zu beheben, das die Seitenbearbeitung unterbrach und zu inkonsistenten Ergebnissen beim Interagieren mit Komponenten führte. Bei Autorinnen und Autoren traten unerwartete Benutzeroberflächenreaktionen auf, die die Inhaltsaktualisierung beeinträchtigten und die Zuverlässigkeit des Workflows reduzierten. Die Änderung stellt eine stabile Verwaltung des Editor-Status wieder her und gewährleistet eine vorhersehbare Ausführung von Authoring-Aktionen in den betroffenen Szenarien. (SITES-34499)

<!--
#### Core Components{#sites-core-components-65-lts-sp2}

#### Campaign integration{#sites-campaign-integration-65-lts-sp2}

#### Experience Fragments{#sites-experiencefragments-65-lts-sp2}

#### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp2}
-->

#### Launches{#sites-launches-65-lts-sp2}

* Während der Launch-Promotion zeigte die Sites-Timeline hart-codierten englischen Text an: „Created version ... before promoting launch“. Die Aktualisierung ersetzt die hart-codierte Zeichenfolge durch Behandlung lokalisierter Nachrichten. Die Timeline zeigt jetzt lokalisierten Text an und stimmt den Eintrag mit dem standardmäßigen AEM-Lokalisierungsverhalten ab. (SITES-39157)
* Der Umfang der Launch-Promotion war unterschiedlich, wenn Autorinnen und Autoren einen Unterabschnitt mit der Option „Aktuelle Seite und Unterseiten bewerben“ bewarben. AEM bewarb auch irrelevante Seiten und verursachte unerwartete Änderungen an der Live-Site. Durch die Korrektur wird die Berechnung des Launch-Umfangs korrigiert, sodass nur die ausgewählte Unterstruktur beworben wird. (SITES-38315)
* Inhaltsfragmente in Launches waren nicht am `damAssetLucene`-Index beteiligt und schränkten die Suchergebnisse und die Abfrageeffizienz ein. Durch diese Änderung werden Launch-Inhaltsfragmentpfade zur Indexdefinition hinzugefügt. Suchvorgänge und benutzerdefinierte Abfragen finden jetzt Inhaltsfragmente unter „`/content/launches`“. (SITES-35634)
* In der Launches-Benutzeroberfläche wurden die Launch-Steuerelemente für Inhaltsfragmente angezeigt, obwohl das Produkt keine Inhaltsfragment-Launches in der Touch-optimierten Benutzeroberfläche exponiert. Durch diese Änderung werden die Code-Pfade für Inhaltsfragment-Launches aus cq-launches-content entfernt und die Filterung der Launch-Liste angepasst. Autorinnen und Autoren sehen jetzt konsistente Optionen für den Seiten-Launch ohne Inhaltsfragment-Launch-Einträge. (SITES-35633)
* Im AEM 6.5 LTS-Schnellstart fehlten erforderliche Launches-Pakete und Voraussetzungen, wodurch die OpenAPI-Aktivierung von Launches blockiert wurde. Die Aktualisierung fügt Launch-Pakete und erforderliche Abhängigkeiten hinzu, z. B. Unterstützung von Metriken, DAM-cfm-Aktualisierungen und Warteschlangenkonfiguration. Launches-APIs werden jetzt im 6.5 LTS-Schellstart ausgeführt und die erforderlichen Laufzeitkomponenten sind vorhanden. (SITES-35297)
* Die CF Launches-Paketerstellung lud neuere Abhängigkeitsversionen und unnötige GraphQL-Bibliotheken, was die Integration von AEM 6.5 LTS erschwerte. Durch diese Änderung werden Abhängigkeitsversionen an der AEM 6.5 LTS-Baseline ausgerichtet und nicht verwendete GraphQL-Abhängigkeiten entfernt. Die Paketauflösung bleibt jetzt konsistent und der Start von CF-Launches bleibt stabil. (SITES-35295)
* AEM Launches führt jetzt eine dedizierte Jenkins-Pipeline für die 6.5 LTS-Verzweigung aus. Die Pipeline führt nächtliche Builds aus und sendet Fehlerwarnungen per E-Mail. Diese Konfiguration erhöht die Testabdeckung und erfasst Regressionen frühzeitig. (SITES-35293)
* AEM 6.5 LTS stellt jetzt ein aktualisiertes Launches-API-Paket mit abgestimmten Artefaktversionen bereit. Das Paket verfolgt die primäre Code-Zeile nach und behält dabei die korrekte Version der LTS 6.5-Veröffentlichung bei. Dieses Update stabilisiert die Nutzung der Launches-API im gesamten 6.5 LTS-Stack. (SITES-35292)
* AEM 6.5 LTS enthält jetzt ein aktualisiertes Launches-Core-Paket mit abgestimmten Abhängigkeitsversionen. Die Aktualisierung fügt die Launches-Core-Handhabung für die Datentypen „Fragment-UUID“ und „Referenz-UUID“ hinzu. Die Launch-Verarbeitung sorgt jetzt für ein konsistentes Verhalten in allen Launches und Inhaltsfragment-Workflows. (SITES-35290)
* Der Sites-Editor wurde optimiert, um inkonsistentes Verhalten zu beheben, das normale Seitenerstellungs-Workflows störte. Bei Autorinnen und Autoren kam es zu unerwarteten Komponenteninteraktionen, die die Inhaltsaktualisierung behinderten und die Bearbeitungszuverlässigkeit beeinträchtigten. Die Änderung stellt eine konsistente Verwaltung des Benutzeroberflächenstatus wieder her und gewährleistet eine vorhersehbare Ausführung von Authoring-Aktionen in den betroffenen Szenarien. (SITES-35138)
* Beim Bearbeiten von Launches wird nun lokalisierter Fehlertext anstelle der hart-codierten Zeichenfolge „`Provided path is not a launch`“ angezeigt. Die Benutzeroberfläche rendert jetzt übersetzte Nachrichten sprachübergreifend, wenn ein ungültiger Launch-Pfad an die Bearbeitung übergeben wird. (SITES-33360)
* AEM 6.5 LTS enthält jetzt die Side-Port-Arbeit der Launches-OpenAPI. Durch die Aktualisierung werden Launches-API-Pakete, Inhaltspakete und erforderliche Schnellstart-Artefakte paritätisch zusammengeführt. Außerdem werden Inhaltsfragment-Launches und OpenAPI-Szenarien mit stabiler CI-Validierung ermöglicht. (SITES-32050)
* Die Launch-Benutzeroberfläche lokalisiert jetzt das Vorlagen-Label „Overridden“. In den Überschreibungsdetails der Vorlage wird jetzt übersetzter Text anstelle einer englischen Zeichenfolge angezeigt. (SITES-29525)
* AEM hat einen fehlenden Lokalisierungsschlüssel unter **Sites** > **Launches** > **Bearbeiten** behoben. Benutzenden wird jetzt eine übersetzte Fehlermeldung anstelle der rohen Zeichenfolge „Unable to update launch source list“ angezeigt. (SITES-21499)
* Die Benutzeroberfläche der Launch-Promotion zeigt jetzt lokalisierte Status-Label und Aktionen an. Im Vorschaubereich werden übersetzte Texte für **Deleted**, **New** und **View** anstelle von rohen englischen Zeichenfolgen angezeigt. (SITES-13540)
* Die Launch-Erstellung zeigt jetzt lokalisierte Fehlermeldungen an. Die Benutzeroberfläche zeigt keine rohen englischen Zeichenfolgen mehr an, z. B. „`Unable to create launch page`“, „`Source root resource is not a page`“ oder „`Mandatory parameter is missing`“. (SITES-13085)


<!-- #### Link Checker{#sites-link-checker-65-lts-sp2} -->


#### MSM – Live Copies{#sites-msm-live-copies-65-lts-sp2}

* Admins hatten während Inhaltsänderungen nur eingeschränkte Sichtbarkeit der MSM-Verarbeitung „Push-bei Verarbeitung“. Die Korrektur fügt eine detaillierte Protokollierung zum Empfang von MSM-Ereignissen und zur Ausführung des Rollouts hinzu. Die Debug-Ausgabe zeigt jetzt an, welche Ereignisse ausgelöst wurden, welche Inhaltspfade sich geändert haben und wer die Änderung ausgelöst hat. (SITES-38029)
* AEM hat ein Layout-Problem bei der Lokalisierung im Datumsfeld des Blueprint-Rollouts behoben. Die Eingabeaufforderung für das Datum passt nun zum Steuerelement und bleibt in allen unterstützten Sprachen lesbar, einschließlich `fr_FR`. (SITES-14961)

<!-- #### Page editor{#sites-pageeditor-65-lts-sp2} -->

#### Replikation{#sites-replication-65-lts-sp2}

Die Seiteneditor-Veröffentlichung verarbeitet jetzt URLs, die Selektoren oder Suffixe enthalten. Die veröffentlichte Anfrage sendet jetzt den JCR-Seitenpfad, keine Selektor- oder Suffix-URL-Zeichenfolge, sodass die Aktivierung abgeschlossen und der Inhalt live geschaltet wird. Die Replikation gibt jetzt bei einem Fehler den Fehlerstatus zurück, wodurch falsche „Veröffentlichung gestartet“-Meldungen verhindert werden. (NPR-43288)

<!-- #### Rich Text Editor{#sites-rte-65-lts-sp2} -->

#### Vorlageneditor{#sites-template-editor-65-lts-sp2}

Der Text zum Vorlagenstatus unter **Tools** > **Allgemein** > **** wurde für einige Gebietsschemata vertikal angezeigt. Das Label „veraltet“ unterbrach das Layout und wurde als Zeichenspalte gelesen. Durch die Korrektur wird der Stil des Vorlagenstatus korrigiert, sodass das Label in einer einzigen horizontalen Zeile ausgegeben wird. (SITES-36797)

#### Universeller Editor {#sites-universal-editor-65-lts-sp2}

* Eine OSGi-Standardkonfiguration wurde als „`preview=true`“ festgelegt und zwang den universellen Editor, im Vorschaumodus zu starten. Durch diese Aktualisierung wird der Standardwert korrigiert und das standardmäßige Eintrittsverhalten in die Produktion wiederhergestellt. Der universelle Editor wird jetzt im Produktionsmodus geöffnet, es sei denn, eine Administratorin oder ein Administrator aktiviert ausdrücklich den Vorschaumodus. (SITES-37193)
* Der Befehl „Öffnen“ im universellen Editor ist jetzt in Entwicklungs- und Staging-Umgebungen standardmäßig auf den Vorschaumodus eingestellt. Der Befehl fügt „`preview=true`“ hinzu, wodurch Autorenprüfungen am Vorschaukontext ausgerichtet bleiben und versehentliche Produktionsöffnungen vermieden werden. (SITES-33839)

### [!DNL Assets]{#assets-65-lts-sp2}

Assets-Korrelation funktioniert jetzt für Dateinamen mit Leerzeichen. Aktualisierte Korrelations-Client-Logik verarbeitet jetzt Pfade mit Leerzeichen korrekt und vermeidet „`undefined`“-Quellenfehler bei der Beziehungsauswahl. Das Dialogfeld „Korrelieren“ wird jetzt geöffnet und speichert Korrelationen, ohne dass die UI hängen bleibt oder das Ladesymbol angezeigt wird. DAM-Benutzende können Assets korrelieren, ableiten und die Korrelation aufheben, ohne Dateien umzubenennen. (Assets-56418)

#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp2}

* Neue Integration des Dynamic Media-Video-Players (begrenzter Rollout) – Im AEM 6.6-Schnellstart ist jetzt ein neues Dynamic Media-Video-Player-Erlebnis verfügbar. Diese Verbesserung ist derzeit nur für Erstkundschaft im Rahmen eines kontrollierten Rollouts aktiviert. (Assets-60165)
* Ein Problem wurde behoben, bei dem die Option „Miniatur auswählen“ im Dialogfeld mit den Videoeigenschaften die Asset-Auswahl nicht öffnete. Benutzende können nun wieder benutzerdefinierte Miniaturen für Video-Assets auswählen. (Assets-58926)
* In Dynamic Media-Videos wurde Unterstützung für die Auswahl von Arabisch in der Dropdown-Liste „Untertitel und Audiospuren“ hinzugefügt, sodass Autorinnen und Autoren arabische Untertitel direkt in AEM verwalten können. (Assets-61771)

<!-- #### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp2} -->

<!--
#### Forms Designer
-->

### [!DNL Forms]{#forms-65-lts-sp2}

* Benutzende hatten Probleme mit der Funktion „`Data Source / Enter Keyword`“ des Formulardatenmodell-Editors (FDM). Dieses Problem beeinträchtigte die Möglichkeit, Datenquellen zu suchen und auszuwählen. (FORMS-23971)
* Auf Mobilgeräten hat die Tabellenkomponente in adaptiven Formularen oben einen ausgeblendeten Titel gerendert, sodass Bildschirmlesehilfen den Inhalt falsch ansagten. Dies betraf Benutzende, die für die Navigation auf Bildschirmlesehilfen angewiesen waren. (FORMS-23754)
* Benutzende hatten Probleme mit auf Kernkomponenten basierenden adaptiven Formularen, die auf als „granite:InternalArea“ gekennzeichnete Ressourcentypen verwiesen. Dies wirkte sich auf die Funktionalität mehrerer Granite-Komponenten im lokalen Formular-Add-on aus. (FORMS-23632)
* Die Formularübermittlung schlägt nach dem Upgrade auf AEM 6.5 LTS SP1 fehl. Es traten fehlende com.adobe.cq.social.commons.CollabUtil auf, was zu JSP-Kompilierungsfehlern und E-Mail-Aktionsfehlern führte. (FORMS-23457)
* Benutzende hatten Probleme mit der nicht ordnungsgemäßen Übersetzung von hCAPTCHA in Foundation-Komponenten, die auf adaptivem Formularen basierten. Dadurch hatten nicht englischsprachige Benutzende Probleme, Formulare korrekt auszufüllen. (FORMS-23426)
* Bei Benutzenden trat ein Fehler bei der Formularübermittlung mit einer SAXParseException auf: „Inhalt ist in Prolog nicht zulässig“ (HTTP 500). Dieses Problem trat aufgrund eines Nullwerts in der XML zum Vorbefüllen von Daten auf, was dazu führte, dass das Server-seitige XML-Parsing fehlschlug. (FORMS-22633)
* Bei Benutzenden trat der Fehler auf, dass adaptive Formulare die WCAG-Audits (Web Content Accessibility Guidelines) nicht bestanden. Der Grund dafür war, dass das Markup für die Tabulatornavigation im Formular ungültig war. Das heißt, ein Nicht-Listenelement wird als direktes untergeordnetes Element einer Liste gerendert, in der nur Listenelemente zulässig sind. Dieses Problem verhinderte, dass das Formular Barrierefreiheitsprüfungen bestand, was Organisationen beeinträchtigte, die rechtliche oder interne Compliance-Anforderungen erfüllen mussten. (FORMS-22101)
* Benutzende hatten Probleme mit der Barrierefreiheit des Nachweises/der Übermittlungs-PDF, wenn leere Formularfelder nicht als Formularelemente getaggt waren. Dies führte zu Schwierigkeiten für Bildschirmlesehilfen und beeinträchtigte die Fähigkeit von Benutzenden mit Einschränkungen, effektiv zu navigieren und Formulare auszufüllen. (FORMS-21989)
* Benutzende hatten ein Problem, bei dem Fußnoten für Komponenten innerhalb eines Unter-Panels beim Laden des Formulars nicht angezeigt wurden. Dieses Problem trat auf, wenn das Element mit der Fußnote die letzte Komponente auf der Seite war. (FORMS-21925)
* Bei der Auswahl von Komponenten im AEM Forms-Editor traten Probleme auf. Beim Navigieren zwischen Registerkarten und beim Zurückkehren zur ersten Registerkarte konnten einige Container nicht mehr ausgewählt werden, was eine einfache Identifizierung und Interaktion verhinderte. (FORMS-21814)
* Bei Benutzenden trat eine Sicherheitslücke im Dashboard für adaptive Formulare auf. Insbesondere wurde ein Problem mit Cross-Site-Scripting (XSS) in der Datei „startpointcontrol.js“ erkannt, das die Ausführung bösartiger Skripte ermöglichen könnte. (FORMS-20679)
* In AEM Forms 6.5 LTS-Cluster-Bereitstellungen auf JBoss® EAP 8 enthalten die Dateien „`domain/configuration/domain_oracle.xml`“, „`domain_mysql.xml`“ und „`domain_mssql.xml`“ kein doppeltes Tag „`<security>`“ mehr, was zu ungültiger XML führte und den Start des Domain-Controllers verhinderte. (FORMS-24687)
* Im Turnkey-Modus wird die Aktualisierung des Datenbank-Ports bei Neuinstallationen und Upgrades jetzt korrekt durchgeführt. Im Neuinstallationsmodus können Benutzende aus allen verfügbaren Ports auswählen, und im Upgrade-Modus wird der in „lc_turnkey.xml“ aktualisierte Datenbank-Port während des Upgrade-Prozesses korrekt referenziert. (FORMS-24689)
* Beim Einrichten von JBoss® EAP 8.0 unter Linux® verursachen unter Windows geänderte Shell-Skripte keine Fehler „`/bin/sh^M: bad interpreter or $'\r': command not found`“ aufgrund von CRLF-Zeilenenden mehr. (FORMS-24688)

<!--
#### Forms JEE 

#### Forms Captcha {#forms-captcha-65-lts-sp2}

#### XMLFM {#forms-xmlfm-65-lts-sp2}

#### [!DNL Adaptive Forms] {#adaptive-forms-65-lts-sp2}

#### [!DNL Forms Designer] {#forms-designer-65-lts-sp2}

#### Forms Designer

#### AdaptIve Forms

#### Forms Captcha

#### Forms Management UI
-->


### Foundation {#foundation-65-lts-sp2}

#### Apache Felix {#foundation-apachefelix-65-lts-sp2}

* Sling Resource Access Security wird jetzt auf Version 1.1.2 ausgeführt. ResourceAccessSecurityImpl löst während der Initialisierung keine ClassCastException mehr aus, wenn sich mehrere ResourceAccessGateHandler-Dienste registrieren. Die Initialisierung wird jetzt zuverlässig abgeschlossen und vermeidet Startfehler in Umgebungen mit mehreren Handlern. (NPR-42750)
* Die JMX-Konsole und die Web-Konsole senden jetzt einen „`Content-Type: text/css header`“ für CSS-Ressourcen der Konsole. Die strikte MIME-Überprüfung blockiert nicht mehr das Laden von Stylesheets, sodass die Benutzeroberfläche von „`/system/console/jmx`“ im normalen Stil gerendert wird. (GRANITE-63677)
* AEM vermeidet jetzt doppelte ACL-Einträge für die Gruppe „`contributor`“ im generierten `WEB-INF/resources/provisioning/model.txt`. Die WAR-Ausgabe enthält jetzt einen konsistenten ACL-Block, der missverständliche Berechtigungsunterschiede bei der Überprüfung verhindert. (GRANITE-63269)
* AEM löscht die Einstellungen der Blockierungsliste und Zulassungsliste der Deserialisierungs-Firewall bei Paketaktualisierungsvorgängen nicht mehr. Durch eine aktualisierte Filterregistrierungslogik bleibt die Abstimmung zwischen aktiver Firewall-Instanz und gespeicherter Konfiguration erhalten, sodass der Schutz ohne Neustart aktiviert bleibt. (GRANITE-61382)
* Die Felix-Web-Konsole gibt während des Zugriffs auf „`/system/console`“ keine periodischen Fehler „`NullPointerException`“ mehr aus. Die ServiceTracker-Verarbeitung verhindert einen Null-Tracker-Status. Konsolenanmeldung und -navigation bleiben bei wiederholten Anfragen und automatisierter Validierung stabil. (GRANITE-61042)

<!--
#### Campaign{#foundation-campaign-65-lts-sp2}

#### Cloud Services{#foundation-cloudservices-65-lts-sp2}

#### Communities {#foundation-communities-65-lts-sp2}

#### Content distribution{#foundation-content-distribution-65-lts-sp2}
-->

#### CRX {#foundation-crx-65-lts-sp2}

CRXDE Lite zeigt keine leere Registerkarte mehr an, wenn Sie nach einem Upgrade des Service Packs eine JSP-Datei öffnen. AEM bietet jetzt übereinstimmenden CodeMirror-Kern und Add-on-Code, wodurch der schwerwiegende Browser-Fehler verhindert und der Editor nutzbar bleibt. (GRANITE-64333)

#### Granite{#foundation-granite-65-lts-sp2}

Der Validator für Ausdruckssicherheit verarbeitet jetzt Leer- oder Nullwerte in der OSGi-Konfiguration. Sichere Standardwerte werden angewendet, leere Arrays werden ignoriert und Protokolle werden aufgezeichnet, sodass NullPointerException und unvorhersehbare Validierungsergebnisse verhindert werden. (NPR-43163)

<!-- #### HTL{#foundatoin-htl-5-lts-sp2} -->

#### Integrationen{#foundation-integrations-65-lts-sp2}

AEM synchronisiert jetzt Adobe Target-Aktivitäten, auch wenn Start- und Enddatum vorhanden sind. Die Target-Payload formatiert Aktivitätsdaten jetzt als vollständige ISO 8601-Zeitstempel, einschließlich Sekunden, Millisekunden und Zeitzone. Target weist die Anfrage nicht mehr mit „`InvalidJson.Json`“ zurück. Geplante Aktivitäten werden jetzt in einen synchronisierten Status versetzt, anstatt nicht synchronisiert zu bleiben. (CQ-4360733)

<!--
#### Jetty{#foundation-jetty-65-lts-sp2}

#### Localization{#foundation-localization-65-lts-sp2} 

#### Omnisearch{#foundation-omnisearch-65-lts-sp2}

#### Platform{#foundation-platform-65-lts-sp2}

#### Projects{#foundation-projects-65-lts-sp2}
-->

#### Oak {#foundation-oak-65-lts-sp2}

Für AEM 6.5 LTS Service Pack 2 ist der S3-Connector 1.60.10 oder höher erforderlich. Die S3-Datenspeicherkonfiguration umfasst jetzt „`crossRegionAccess`“ und „`mode`“, sodass Admins bei Bedarf den regionsübergreifenden Bucket-Zugriff aktivieren und den Speicher auf GCP umstellen können. Der „`s3EndPoint`“ erwartet jetzt einen Bereich, der auf „`s3Region`“ abgestimmt ist, oder er bleibt leer, sodass der Treiber den Endpunkt generiert. (GRANITE-64873)


#### Schnellstart{#foundation-quickstart-65-lts-sp2}

* Sling aktualisiert die „administrativ-login“-Zulassungsliste für die Verwendung inklusiver Terminologie und neuer Konfigurations-PIDs. Diese Änderung entspricht Sling JCR Base 3.2.0. (GRANITE-63756)

  **Auswirkungen**

   * Sling verwirft folgende PIDs, die Sie aus Ihren Konfigurationen entfernen sollten:
      * Werkseitige PID: `org.apache.sling.jcr.base.internal.LoginAdminWhitelist.fragment`
      * Globale PID: `org.apache.sling.jcr.base.internal.LoginAdminWhitelist`
Diese älteren Konfigurationen verwenden Eigenschaften wie „`whitelist.name`“ und „`whitelist.bundles`“.

   * Sling bietet weiterhin partielle Abwärtskompatibilität für die veralteten PIDs. Verwenden Sie sie jedoch nicht für neue Konfigurationen. Verwenden Sie stattdessen die neueren „`LoginAdminAllowList.*`“-PIDs.
   * Führen Sie veraltete und neue Zulassungslistenkonfigurationen nicht gleichzeitig aus. Gemischte Konfigurationen können Mehrdeutigkeiten verursachen und zu unbeabsichtigtem Verhalten führen. Wenn Sie zu AEM 6.5 LTS SP2 migrieren, entfernen Sie die veralteten PIDs vollständig.

  **Vorgehensweise**

   1. Suchen Sie nach Zulassungslistenkonfigurationen, die „`LoginAdminWhitelist*`“-PIDs verwenden.
   1. Ersetzen Sie sie durch die entsprechenden neuen PIDs:

      * Werkseitige PID: `org.apache.sling.jcr.base.LoginAdminAllowList.fragment`
      * Globale PID: `org.apache.sling.jcr.base.LoginAdminAllowList`

      Weitere Informationen finden Sie unter [Veralteter Ansatz bei Paket-Zulassungslisten für die Administratoranmeldung](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html#deprecated-approach-to-allowlist-bundles-for-administrative-login).

* AEM 6.5 LTS SP2 aktualisiert das Paket-Set der Foundation-Ebene für Sling, Oak und Felix. Diese Upgrades verbessern die Kernlaufzeitstabilität und stimmen Abhängigkeitsversionen plattformübergreifend ab. (GRANITE-61874)

<!--
#### Security{#foundation-security-65-lts-sp2}

AEM now prevents NullPointerException errors when a logged-in user lacks read access for some groups and opens the Groups tab. The tab now hides groups without access and renders group membership details without a blank or unresponsive UI. (NPR-43311)
-->

#### Sling{#foundation-sling-65-lts-sp2}

AEM enthält jetzt Sling Engine 2.16.6. Durch diese Änderung werden XSS-Verletzungen eliminiert, die von Sicherheits-Tools gekennzeichnet werden, und Sicherheit und Stabilität des Core-Renderings werden verbessert. (NPR-43105)

<!--
#### Translation{#foundation-translation-65-lts-sp2}

#### User interface{#foundation-ui-65-lts-sp2}
-->

#### WCM{#foundation-wcm-65-lts-sp2}

AEM Translations schlägt auf Java 17 oder Java 21 nicht mehr aufgrund von Problemen mit dem XLIFF-Format fehl. Die Export-Pipeline erzeugt jetzt standardkonforme XLIFF-Dateien, die von Übersetzungsdienstleistern akzeptiert werden. Durch diese Änderung werden Unterbrechungen von Übersetzungsaufträgen vermieden und eine vorhersehbare Übergabe zwischen AEM und Übersetzungsdiensten wird wiederhergestellt. Übersetzungs-Workflows bleiben jetzt in allen unterstützten Java Runtimes stabil. (CQ-4360217)

#### Workflow{#foundation-workflow-65-lts-sp2}

EmailNotificationService-Processor löst keine wiederholten Fehler „Segment nicht gefunden“ während der Verarbeitung von Workflow-Benachrichtigungen mehr aus. Die aktualisierte Ausnahmebehandlung erkennt SegmentNotFoundException und stoppt die Verarbeitungsschleife, anstatt mit ungültigen Lesevorgängen fortzufahren. Die Workflow-Ausführung bleibt stabil und das Protokollrauschen beim Zugriff auf den Posteingang und die Arbeitselemente wird reduziert. (GRANITE-62635)




## Info [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Die Plattform von [!DNL Adobe Experience Manager] 6.5 LTS basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java™ Content-Repository Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x wird als Servlet-Engine für den Schnellstart verwendet.

### Java™-Unterstützung  {#java-support}

* Unterstützung für Java™ 17 und Java™ 21.
* Um eine optimale Leistung zu erzielen, überschreiben Sie die GC-Standardwerte mit anderen Werten. Weitere Informationen finden Sie im Abschnitt [Installieren und Aktualisieren](/help/sites-deploying/custom-standalone-install.md).
* Adobe verteilt Wartungs-Updates für Java™ 17 und Java™ 21 für die Verwendung durch Kunden in AEM-bezogenen Projekten, sofern diese nicht über Oracle öffentlich verfügbar sind.

### Uber-JAR-Verpackung {#uber-jar-packaging}

Das UberJar für AEM 6.5 LTS SP2 verwendet AEM 6.5 LTS UberJar 6.6.2. Sie können die entsprechenden UberJar-Artefakte aus dem Repository von Maven Central abrufen. Im Gegensatz zu AEM 6.5 unterteilt AEM 6.5 LTS öffentliche APIs und veraltete APIs in zwei verschiedene Artefakte.

Verwenden Sie Folgendes, um mit den öffentlichen APIs zu kompilieren:

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.2</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

Wenn Ihr Code auch von veralteten APIs abhängig ist, fügen Sie Folgendes hinzu:

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.2</version>
    <classifier>deprecated-apis</classifier>
    <scope>provided</scope>
</dependency>
```

Siehe auch [Aktualisieren der UberJar-Version von AEM](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Aktualisieren {#upgrade}

* Weitere Informationen zum Upgrade-Verfahren finden Sie unter [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md).
* Detaillierte Anweisungen finden Sie unter [Upgrade-Leitfaden für AEM Forms 6.5 LTS SP1 auf JEE](https://experienceleague.adobe.com/de/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade).

#### Best Practices für AEM 6.5 LTS Service Pack-Upgrades

<!-- THE INFORMATION UNDER THIS HEADING CAME FROM CQDOC-23078 -->

**Umgebung**
Gilt für: Kundinnen und Kunden mit AEM 6.5 LTS (On-Premise), die Service Pack 2 (SP2) installieren. SP2 wird als Schnellstart-JAR bereitgestellt.

**Darum ist dieses Upgrade-Verfahren wichtig**
SP2 für AEM 6.5 LTS wird als Schnellstart-JAR-Datei und nicht als ZIP-Datei zur Installation über den Paket-Manager bereitgestellt. On-Premise-Kundinnen und -Kunden führen ein Upgrade durch, indem sie die Schnellstart-JAR-Datei ersetzen, entpacken und neu starten. Diese Methode entspricht dem Upgrade-Verfahren von Adobe.

**Empfohlener Upgrade-Ablauf (Autoren- oder Veröffentlichungsinstanz)**

1. Stellen Sie sicher, dass Ihre AEM 6.5 LTS-Instanz fehlerfrei funktioniert und Sie darauf zugreifen können.
1. Laden Sie die Schnellstart-JAR-Datei (z. B. `cq-quickstart-6.6.x.jar`) von Software Distribution herunter.
1. Stoppen Sie die Instanz, die ausgeführt wird.
1. Ersetzen Sie im AEM-Installationsverzeichnis (außerhalb von `crx-quickstart/`) die vorherige Schnellstart-JAR-Datei durch die SP2-JAR-Datei.
1. Entpacken Sie die JAR-Datei:

   ```java
   java -jar cq-quickstart-6.6.x.jar -unpack
   ```

   (Passen Sie Heap-Flags nach Bedarf an.)

1. Benennen Sie die entpackte JAR-Datei so um, dass sie der Rolle und dem Port entspricht, z. B. `cq-author-4502.jar` oder `cq-publish-4503.jar`.
1. Starten Sie AEM und bestätigen Sie das Upgrade auf der Benutzeroberfläche („Hilfe“ > „Info“) und in den Protokollen.

**Gute Hygiene**

* Führen Sie das Upgrade in einer niedrigeren oder einer Testumgebung aus, bevor Sie es in der Produktionsumgebung ausführen.
* Erstellen ein vollständiges wiederherstellbares Backup (Repository plus alle externen Datenspeicher), bevor Sie beginnen.
* Lesen Sie die Anleitungen für das lokale Upgrade und die technischen Anforderungen von Adobe (Java 17/21 für LTS empfohlen).

>[!NOTE]
>
>Die oben gezeigten Dateinamen (z. B. `cq-quickstart-6.6.x.jar`) spiegeln die Schnellstart-Artefaktbenennung wider, die für diese LTS-Version beobachtet wird. Verwenden Sie immer exakt denselben Namen der Datei, die Sie von Software Distribution herunterladen.

## Installieren und Aktualisieren{#install-update}

Informationen zu Einrichtungsanforderungen finden Sie unter [Installationsanweisungen](/help/sites-deploying/custom-standalone-install.md).

>[!NOTE]
>
> Wenn Sie ein direktes Upgrade von alten 6.5 SPs auf LTS SP1 durchführen, folgen Sie den Anweisungen zum [Upgrade](/help/sites-deploying/upgrade.md) auf 6.5 bis 6.5 LTS GA.


Detaillierte Anweisungen finden Sie unter [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> Für neue AEM 6.5 LTS-Installationen müssen Indexdefinitionen separat installiert werden. Weitere Informationen finden Sie in [diesem Artikel](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Installieren und Aktualisieren des AEM Forms-Add-ons {#install-update-aem-forms-add-on}

Detaillierte Anweisungen finden Sie unter [Durchführen einer ersetzenden Aktualisierung](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/release-notes/aem-forms-current-service-pack-installation-instructions).


## Unterstützte Plattformen {#supported-platforms}

Die vollständige Matrix der unterstützten Plattformen, einschließlich der Support-Ebene, finden Sie unter [AEM 6.5 LTS – Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java™ 17/Java™ 21 sind die empfohlenen Versionen für AEM 6.5 LTS.


## Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

<!-- CARRY OVER EACH RELEASE -->

Adobe prüft kontinuierlich die Produktfunktionen und entwickelt sie weiter, um den Kundenwert zu verbessern, indem ältere Funktionen modernisiert oder ersetzt werden. Diese Änderungen werden unter sorgfältiger Berücksichtigung der Abwärtskompatibilität implementiert.

Um Transparenz zu gewährleisten und eine angemessene Planung zu ermöglichen, folgt Adobe bei Adobe Experience Manager (AEM) folgendem Einstellungsprozess:

* Die Einstellung wird zuerst angekündigt. Veraltete Funktionen bleiben weiterhin verfügbar, werden aber nicht mehr weiterentwickelt.
* Die Entfernung erfolgt frühestens mit Einführung der nächsten Hauptversion. Der vorgesehene Zeitplan für die Entfernung wird separat mitgeteilt.
* Kundinnen und Kunden, die auf unterstützte Alternativen umstellen möchten, erhalten mindestens einen Versionszyklus, bevor eine Funktion entfernt wird.

### Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden Funktionen aufgeführt, die Adobe in AEM 6.5 LTS nicht mehr unterstützt werden. In der Regel werden Funktionen von Adobe eingestellt, bevor sie aus einer zukünftigen Version entfernt werden, und es wird eine Alternative bereitgestellt.

Kundinnen und Kunden werden aufgefordert zu prüfen, ob sie die Funktion in ihrer aktuellen Bereitstellung verwenden. Planen Sie Änderungen an deren Implementierung, damit die bereitgestellte Alternative genutzt werden kann.

| Bereich | Funktion | Ersatz | Version (SP) |
| --- | --- | --- | --- |
| Schnellstart | Mongo-APIs | Mongo-APIs werden nicht mehr unterstützt und sollen in zukünftigen Versionen entfernt werden. | 6.5 TS SP2 |
| Sites | Unterstützung von Inhaltsfragmenten in der AEM Assets-REST-API | AEM 6.5 LTS SP2 bietet moderne OpenAPIs für die Verwaltung von Inhaltsfragmenten und -modellen. Daher wurden die älteren Endpunkte zur Unterstützung von Inhaltsfragmenten in der AEM Assets-REST-API jetzt eingestellt.<br>Adobe beabsichtigt, diese älteren Endpunkte bis zu einer Ankündigung zum Ende der Nutzungsdauer verfügbar zu halten. Adobe plant keine weiteren Verbesserungen an den veralteten Endpunkten. | 6.5 LTS SP2 |
| Sites | [SPA-Editor](/help/sites-developing/spa-overview.md) | Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind:<br>– [Der universelle Editor](/help/sites-developing/universal-editor/introduction.md) für visuelle Bearbeitung.<br>– [Der Inhaltsfragment-Editor](/help/assets/content-fragments/content-fragments-managing.md) für formularbasierte Bearbeitung. | 6.5 LTS GA |
| [!DNL Foundation] | Unterstützung für com.adobe.granite.oauth.server | Adobe IMS-Integration |  |

### Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden die Funktionen aufgeführt, die aus AEM 6.5 LTS entfernt wurden. In früheren Versionen wurden diese Funktionen als veraltet gekennzeichnet.

* Die Unterstützung für RDBMK für die Persistenz des CRX-Repositorys wurde entfernt.
* In Cluster-Umgebungen ist MongoMK jetzt die einzige unterstützte Option für Repository-Persistenz.

| Bereich | Funktion | Ersatz | Version (SP) |
| --- | --- | --- | --- |
| Commerce | AEM CIF Classic wird nicht unterstützt. | Migrieren Sie zu [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
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

### AEM Forms

* Im Configuration Manager schlägt die Datenbankinitialisierung beim Bootstrap im benutzerdefinierten Turnkey-Modus von AEM Forms 6.5 LTS JEE fehl, wenn keine Module oder nur eingeschränkte Komponenten ausgewählt sind. Das Problem ist auf eine fehlende Abhängigkeit (xalan-2.7.2.jar) zurückzuführen, die zu einem Fehler führt. Durch Hinzufügen der JAR-Datei zu „adobe-livecycle-jboss.ear\lib“ wird das Problem behoben. (FORMS-24690)
* Bei Bereitstellungen von Forms JEE LTS, die auf JBoss® EAP 8 ausgeführt werden, kann die Reader Extensions-Benutzeroberfläche mit einem internen Server-Fehler fehlschlagen. (FORMS-24894)
* Bei Forms JEE LTS, das auf JBoss® ausgeführt wird, können E-Mail-bezogene Funktionen fehlschlagen. Beim Versuch, E-Mail-Funktionen zu verwenden, protokolliert der Server möglicherweise einen Fehler ähnlich wie „`Error IMAPProvider not a subtype`“. (FORMS-24892)
* Auf Linux®-Plattformen muss für Forms JEE LTS in „`LFS_Foundation.properties`“ die Eigenschaft „`OSFileSetIntendedFor`“ korrekt eingestellt sein, bevor der Configuration Manager ausgeführt werden kann. Wenn sie nicht aktualisiert wird, ist die Konfiguration möglicherweise nicht richtig auf Linux® zugeschnitten, was zu Problemen bei der Laufzeit oder der Bereitstellung führen kann. Um das Problem zu beheben, navigieren Sie nach dem Ausführen des Installationsprogramms und vor dem Ausführen von Configuration Manager zu „`configurationManager/config/solcomp/`“, öffnen Sie „`LFS_Foundation.properties`“, stellen Sie „`OSFileSetIntendedFor=Linux`“ ein, speichern Sie die Datei und führen Sie dann den Configuration Manager aus. (FORMS-24741)

### Repository-Beschädigung bei Online-Komprimierung nach Offline-Komprimierung (GRANITE-65146) {#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146}

Bei Benutzenden kann während der Online-Komprimierung eine Beschädigung des Repositorys auftreten, wenn sie zuvor die Offline-Komprimierung auf dem JCR-Repository ausgeführt haben. In diesem Szenario kann eine `SegmentNotFoundException` (SNFE) auftreten, die zu einer Beschädigung des Repositorys führen kann.

Um das Problem zu beheben, installieren Sie den Hotfix von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.2-hotfix-GRANITE-65388-1.0.zip). Da der Hotfix ein `oak-segment-tar`-Paket auf niedriger Ebene enthält, wird die Instanz nach der Installation neu gestartet.

Planen Sie die Ausfallzeiten der Instanz bei der Hotfix-Anwendung ein. Verwenden Sie für die Offline-Komprimierung die entsprechende [`oak-run`-JAR](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar), die auch auf Software Distribution verfügbar ist.

>[!NOTE]
>
> * Verwenden Sie für alle „`oak-run`“-Vorgänge die Datei „[`oak-run` 1.88.1-B006 jar](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar)“.
>
> * Starten Sie AEM, indem Sie die Systemeigenschaft „`oak.compaction.legacy=true`“ einstellen.

### Installieren erforderlicher Oak-Indizes für Sites Headless-APIs{#site-headless-api}

Einige APIs, die zu Sites Headless verschoben wurden, erfordern zusätzliche Oak-Indizes, damit die volle Funktionalität genutzt werden kann.

Installieren Sie das Paket „`cq-dam-cfm-indices`“, um die folgenden Funktionen zu verwenden:

* Auflisten von Inhaltsfragmentmodellen
* Auflisten von Inhaltsfragmenten
* Such-API
* Workflows

Laden Sie das Indexpaket [cq-dam-cfm-](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/cq-dam-cfm-indices-1.1.2.zip) im Adobe Software Distribution-Portal herunter.

### Dispatcher-Verbindungsfehler mit Funktion „Nur SSL“ (behoben in AEM 6.5 LTS SP1 und höher){#ssl-only-feature}

>[!NOTE]
>
> Dieses Problem tritt nur in Version AEM 6.5 LTS GA auf.

Bei der Aktivierung der Funktion „Nur SSL“ in AEM-Bereitstellungen gibt es ein bekanntes Problem, das die Verbindung zwischen dem Dispatcher und AEM-Instanzen beeinträchtigt. Nach Aktivierung dieser Funktion können Konsistenzprüfungen fehlschlagen und die Kommunikation zwischen dem Dispatcher und AEM-Instanzen kann unterbrochen werden. Dieses Problem tritt insbesondere auf, wenn Kundinnen und Kunden versuchen, eine Verbindung über `https + IP` von Dispatcher zu AEM-Instanzen herzustellen. Dies steht im Zusammenhang mit SNI-Validierungsproblemen (Server Name Indication).

**Auswirkungen**

* Konsistenzprüfungsfehler mit HTTP 400-Antwort-Codes
* Unterbrochener Traffic zwischen Dispatcher und AEM-Instanzen
* Inhalte können nicht ordnungsgemäß über den Dispatcher bereitgestellt werden.
* Verbindungsfehler bei Verwendung von HTTPS mit IP-Adressen in der Dispatcher-Konfiguration.
* HTTP 400-Fehler „Ungültige SNI“ bei der Verbindung über HTTPS + IP.

**Betroffene Umgebungen**

* AEM-Bereitstellungen mit Dispatcher-Konfigurationen.
* Systeme, in denen die Funktion „Nur SSL“ aktiviert wurde.
* Dispatcher-Konfigurationen mit der Verbindungsmethode „`https + IP`“ zu AEM-Instanzen.

**Lösung**

Wenn dieses Problem auftritt, wenden Sie sich an den Adobe-Kunden-Support. Zur Lösung dieses Problems ist Hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) verfügbar. Versuchen Sie nicht, „Nur SSL“-Funktionen zu aktivieren, bis Sie den erforderlichen Hotfix angewendet haben.

## Enthaltene OSGi- und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in dieser [!DNL Experience Manager] 6.5. LTS, Service Pack 2 enthaltenen OSGi-Pakete und Inhaltspakete aufgeführt: <!-- UPDATE FOR EACH NEW RELEASE -->

* [Liste der in Experience Manager 6.5 LTS, Service Pack 2 enthaltenen OSGi-Pakete](/help/release-notes/assets/65lts_sp2_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5 LTS, Service Pack 2 enthaltenen Inhaltspakete](/help/release-notes/assets/65lts_sp2_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produkt-Download unter „licensing.adobe.com“](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/de/docs/support-resources/adobe-support-tools-guide/adobe-customer-support-experience).

