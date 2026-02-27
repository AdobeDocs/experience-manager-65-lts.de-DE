---
title: Aktuelle Versionshinweise für Adobe Experience Manager 6.5 LTS, SP2
description: Hier finden Sie die aktuellen Versionsinformationen zu Adobe Experience Manager 6.5 LTS, Service Pack 2.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: f75f02c1e10deb6eef788d6584229c045b88880d
workflow-type: tm+mt
source-wordcount: '6062'
ht-degree: 21%

---

# Aktuelle Versionshinweise für Adobe Experience Manager 6.5 LTS, SP2 {#release-notes}

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Version | Service Pack 2 (SP2)-<!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | &#x200B;19. Februar 2026 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.2.jar) |


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

## Was in [!DNL Adobe Experience Manager] 6.5 LTS, SP2 enthalten ist {#what-is-new}

<!-- UPDATE EACH RELEASE -->

[!DNL Experience Manager] 6.5 LTS enthält SP2 neue Funktionen, wichtige von Kundschaft angeforderte Verbesserungen und Fehlerbehebungen. Diese Version enthält zudem Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von Version 6.5 LTS im März 2025 veröffentlicht wurden. [Installieren Sie dieses Service Pack](#install-update) auf 6.5 LTS.

## Wichtigste Funktionen und Verbesserungen

**AEM Sites**

AEM 6.5 LTS SP2 enthält jetzt OpenAPIs für [Inhaltsfragment- und Modellverwaltung](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/65lts/) und [Launches](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/launches/). Diese APIs bieten Zugriff auf Inhaltsfragmente und Launches für die Bearbeitung und Planung. Sie verwenden dieselben modernen OpenAPIs wie AEM as a Cloud Service.


<!-- UPDATE THE EACH RELEASE -->

## Behobene Probleme in 6.5 LTS, Service Pack 2 {#fixed-issues}

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

### [!DNL Sites]{#sites-65-LTS-SP2}

#### Barrierefreiheit {#sites-accessibility-65-lts-sp2}

* Die Textkomponente hat den Tastaturfokus verloren, wenn Autoren während der Bearbeitung im Komponenten-Browser Elemente über den Mauszeiger bewegen. Dadurch wurde die Eingabe unterbrochen und ein Barrierefreiheitsfehler unter WCAG 3.2.1 ausgelöst. Die Korrektur verhindert, dass der Fokus beim Hover-Stil verschoben wird, und hält die Textkomponente während der Interaktion mit dem Komponenten-Browser im Fokus. (SITES-35370)
* Die Fokusverwaltung im Rich-Text-Feld Beschreibung wurde korrigiert, sodass die Vorwärtsnavigation mit der Tabulatortaste blockiert wurde. Benutzende blieben im RTE stecken, weil die Komponente zum Verschieben des Fokus auf einen nicht standardmäßigen Tastaturbefehl angewiesen war, was die erwartete Dialogfeldnavigation beschädigte. Die Änderung erzwingt die standardmäßige Tastaturinteraktion und behält die logische Tab-Sequenzierung im gesamten Dialogfeld bei. (SITES-35228)
* Es wurde ein Problem im Sites-Editor behoben, das das erwartete Verhalten während der Seitenbearbeitung störte und zu inkonsistenter Komponenteninteraktion führte. Autoren erlebten unzuverlässige Benutzeroberflächenantworten, die mit standardmäßigen Bearbeitungsaufgaben interferierten und die Effizienz des Workflows verringerten. Die Aktualisierung verfeinert die zugrunde liegende Editor-Logik und stellt eine stabile, vorhersehbare Interaktion über die betroffenen Komponenten hinweg wieder her. (SITES-35227)
* Eine Regression, die den Asset-Wähler im Seiten-Editor unterbrochen und das Laden in bestimmten Seitenbearbeitungs-Szenarien verhindert hat. Autoren können den Asset-Wähler jetzt normal öffnen und verwenden, wenn sie beim Bearbeiten einer Seite Assets auswählen oder durchsuchen. Diese Änderung stellt den konsistenten Zugriff auf Asset-Auswahl-Workflows wieder her, durch die Ladefehler unterbrochen wurden. (SITES-35226)
* Es wurde ein Problem im Sites-Editor behoben, das zu inkonsistentem Verhalten während der Seiteninteraktion führte und standardmäßige Authoring-Workflows störte. Der Fehler führte zu unerwarteten Benutzeroberflächenantworten, die die Komponentenkonfiguration und Inhaltsaktualisierungen beeinträchtigten. Das Update stabilisiert die betroffenen Funktionen und stellt die zuverlässige Ausführung von Bearbeitungsaktionen über Seiten hinweg wieder her. (SITES-35225)
* Es wurde ein Fehler in der Sites-Authoring-Oberfläche behoben, der zu inkonsistentem Verhalten während der Seitenbearbeitung führte und normale Workflows störte. Autoren stießen auf unerwartete Benutzeroberflächenantworten, die die Komponenteninteraktion und Inhaltsaktualisierungen beeinträchtigten. Die Aktualisierung stabilisiert die betroffenen Funktionen und stellt ein zuverlässiges und vorhersehbares Verhalten in allen Bearbeitungsszenarien wieder her. (SITES-35224)
* AEM Sites bietet jetzt `alt` Textunterstützung für Bilder, um ADA- und WCAG-Anforderungen zu erfüllen. In der Seitenausgabe werden `alt` nicht mehr weggelassen, sodass die Sprachausgabe korrekten Alternativtext erhält. (SITES-27153)
* Das Layout der `Note Add`-Symbolleiste wurde korrigiert, sodass die Schaltfläche Hinzufügen sich nicht mehr mit dem Titel bei einer Breite des 320-Pixel-Darstellungsfelds überschneidet. Verbesserte Reflow-Funktion auf dem kleinen Bildschirm, sodass die Steuerelemente beim 400%igen Zoomen lesbar und verwendbar bleiben. (SITES-25376)
* Fehlerkorrektur - Fehlende Ankündigungen von Bildschirmlesehilfen für Fehler beim Auswählen von Links in Dialogfeldern wurden behoben. Die Benutzeroberfläche veröffentlicht jetzt Fehlertext über einen Statusmeldungs-Container, sodass die NVDA die Nachricht liest, sobald sie angezeigt wird. (SITES-25368)
* ARIA-Raster- und Rasterzellenrollen wurden aus der Seitenleisten-Asset-Liste entfernt. Die standardmäßige Listensemantik und die Tastaturfokusreihenfolge wurden wiederhergestellt, was die Navigation der Sprachausgabe verbessert und zusätzliche Tabstopps reduziert hat. (SITES-25361)
* Die Fokussequenzierung in der Seitenleisten-Assets wurde korrigiert. Tastaturbenutzer erreichen jetzt über einen konsistenten Registerkartenpfad alle Asset-Aktionen, einschließlich „Bearbeiten“. (SITES-25360)
* Layout-Überlauf im Assets-Modal „Suche“ bei einer Darstellungsfeldbreite von 320 Pixel behoben. Modale Inhalte fließen jetzt zurück und bleiben lesbar, sodass sich Steuerelemente nicht mehr überschneiden oder das Dialogfeld überlaufen wird. (SITES-25330)
* NVDA-Ausgabe für die Edit-Taste korrigiert. NVDA kündigt jetzt die Aktion „Bearbeiten“ an, nicht die Schaltfläche „Vorschau“. (SITES-25320)
* Es wurden unbenannte Texteingaben in der Demografie-Symbolleiste korrigiert, die eine stille oder generische Ausgabe der Bildschirmlesehilfe verursachten. Jede Eingabe zeigt jetzt einen klaren, auf Bezeichnungen basierenden barrierefreien Namen an, der die Tastaturnavigation und die Navigation mit Hilfstechnologien verbessert. (SITES-25316)
* Korrektur der Tastaturfokusreihenfolge für die Demografie-Symbolleiste während der Navigation in der Layout-Vorschau. Die Registerkartennavigation wechselt jetzt direkt von der Schaltfläche Demografisch zu den Symbolleistensteuerelementen, ohne zur sekundären Symbolleiste zu wechseln. (SITES-25305)
* Fehlerkorrektur - Die Ankündigungsreihenfolge für die Beschriftungen „Kleiner Screens&quot; und „Tablet“ auf dem Layout-Lineal „Bearbeiten“ ist jetzt korrekt. Die Sprachausgabe gibt diese Beschriftungen nun an den richtigen Linealmarken aus, die dem Seitenlayout entsprechen. (SITES-25291)
* Ein Überlauf der Symbolleiste „Layout bearbeiten“ wurde mit 200 % Zoom behoben. Inhalte bleiben jetzt im Darstellungsfeld und sind durch Scrollen erreichbar. (SITES-25288)
* Falsche Fokusreihenfolge in der Anmerkungsüberlagerung behoben. Die Tabulatortaste durchläuft jetzt Überlagerungssteuerelemente und Anmerkungselemente. Die übergeordnete Seite erhält nicht mehr den Fokus hinter der Überlagerung. (SITES-25282)
* Die Fokusbehandlung im Popover für Farbfelder wurde korrigiert. Das Dialogfeld verschiebt den Fokus jetzt auf eine leere Überschrift und startet die Ausgabe der Sprachausgabe an diesem Einstiegspunkt. NVDA liest den vollständigen Inhalt des Dialogfelds nicht mehr aus der Sequenz heraus. (SITES-25275)
* Die Behandlung des modalen Fokus von Timewarp nach dem Schließen der Datumsauswahl wurde korrigiert. `Escape` kehrt jetzt zur Schaltfläche zur Datumsauswahl zurück. Bei der Datumsauswahl wird jetzt der Fokus auf das Eingabefeld neben dem Datumsauswahl-Steuerelement gelegt, wodurch Fokusverlust und der Zugriff auf die Hintergrundseite verhindert werden. (SITES-25264)
* Fehlerkorrektur: Die Tastaturfokusbehandlung für das Dialogfeld Anmerkung löschen wurde korrigiert. Durch Abbrechen wird jetzt der Fokus auf das `Delete` Steuerelement zurückgesetzt, das das Dialogfeld geöffnet hat, nicht auf das Steuerelement zum Bestätigen des Hexadezimalwerts. Nach dem Abbrechen gibt die Sprachausgabe keinen nicht verwandten Dialogfeldinhalt mehr aus. (SITES-25258)
* Feste Fokusbehandlung für das modale Dialogfeld „Anmerkung“. Das Öffnen des Dialogfelds legt jetzt den Fokus auf die Dialogfeldüberschrift und verhindert, dass NVDA Canvas-Inhalte und nicht zugehörigen Dialogfeldtext liest. Die Tastaturnavigation bleibt jetzt bis zum Schließen im Dialogfeld. (SITES-25257)
* Es wurden Probleme mit dem Layout des Suchmodals bei einer Breite von 320 Pixel behoben. Modale Inhalte fließen jetzt sauber zurück und vermeiden Überschneidungen mit dem Baumverzeichnis. Benutzer können Ergebnisse anzeigen und ohne verdeckte Steuerelemente im Verzeichnis navigieren. (SITES-25246)
* Suchmodaltext wird nach Vergrößerung des Textabstands nicht mehr angeclipst. Das Strukturverzeichnis-Layout behält jetzt eine klare Trennung bei, sodass Bezeichnungen und Einträge lesbar bleiben. Benutzer können jetzt die Suche und Navigation ohne Überschneidung oder abgeschnittenen Text abschließen. (SITES-25245)
* Durch die Aktivierung der Anmerkung wird der Tastaturfokus jetzt in den Anmerkungsinhalt verschoben, nicht in die Schaltfläche Anmerkung beenden . Die Tabulatorreihenfolge folgt einer logischen Reihenfolge und hält die zugehörigen Steuerelemente ohne Rückwärtsnavigation erreichbar. (SITES-25241)
* Die Links „Datum festlegen“ und „Timewarp beenden“ hatten bei der Tastaturnavigation keinen sichtbaren Fokusindikator. Die Benutzeroberfläche rendert jetzt einen eigenen Stil mit kontrastreichem Fokus, sodass Benutzende den aktiven Link auf einen Blick erkennen können. (SITES-25232)
* Die modale Teaser-Kopfzeile blockiert nicht mehr Tastaturbenutzer darin, das Dialogfeld zu verschieben. Tastatursteuerelemente ermöglichen jetzt Aktionen zum Aufnehmen, Verschieben und Ablegen, was die Benutzerfreundlichkeit der Sprachausgabe und die allgemeine Bedienbarkeit verbessert. (SITES-25226)
* AEM verwendet jetzt eine aussagekräftige barrierefreie Bezeichnung für die Schaltfläche Teaser-Modalinformationen . Die Sprachausgabe gibt einen klaren Aktionsnamen anstelle der Standardsymbol-Alt-Text-Zeichenfolge aus. (SITES-25223)
* Die Sprachausgabe gibt jetzt die richtige Aktion aus, wenn Benutzende die Schaltfläche Bearbeiten aktivieren. Die NVDA meldet nicht mehr, dass die „Vorschau-Schaltfläche gedrückt“ wurde, was irreführendes Feedback und Verwirrung während der Tastaturnavigation verursachte. (SITES-25208)
* Durch Erweitern der linken Leiste wird der Tastaturfokus jetzt auf das erste Steuerelement der linken Leiste verschoben. Die Tabulatorsequenz springt nicht mehr zur sekundären Symbolleiste oder landet in der Mid-List, sodass Tastaturbenutzer Inhalte der linken Leiste ohne Rückwärtsnavigation erreichen können. (SITES-24998)
* Der Inhalt der Leiste des Geräteemulators bleibt jetzt bei einer Darstellungsfeldbreite von 320 Pixel vollständig sichtbar. Der Text und die Steuerelemente der Symbolleiste werden umgebrochen, anstatt sie zu kürzen, wodurch Überschneidungen reduziert und die Lesbarkeit verbessert werden. (SITES-24953)
* AEM zeigt jetzt die vollständige iPhone-Gerätebeschriftung in der Emulator-Symbolleiste an. Text wird nicht mehr mit der Standardbreite abgeschnitten, was die Lesbarkeit und die Klarheit der Geräteauswahl verbessert. (SITES-24952)
* Listenansicht - Tabellenüberschriften zeigen jetzt über ARIA den Sortierstatus an. Die Sprachausgabe gibt eine auf- oder absteigende Reihenfolge nach einer Spaltensortierungsaktion aus. (SITES-24943)
* AEM behält jetzt die Sichtbarkeit der Menübeschriftung Mehr Aktionen in der Kartenansicht bei Änderungen des Textabstands bei. Menüoptionen behalten den vollständigen Text, einschließlich Quick Publish, und das Menü bleibt bei allen WCAG-Textabstandseinstellungen lesbar. (SITES-24941)
* In der Menüleiste für Kartenaktionen wird jetzt ein barrierefreier Name in der Kartenansicht angezeigt. Bildschirmlesehilfen geben den Zweck der Menüleiste klar an, und die Sprachsteuerung kann das Steuerelement anhand des Namens auswählen. (SITES-24938)
* Die Kartenansicht verlässt sich nicht mehr auf die ARIA-Rastersemantik, die ein verwirrendes Verhalten von Bildschirmlesehilfen verursacht hat. Die Benutzeroberfläche bietet jetzt aussagekräftige Rollen und Beschriftungen für Karteninhalte und die Kartenaktionsleiste, wodurch die Anzahl der übersprungenen Steuerelemente bei der Verwendung der Tastatur reduziert wird. (SITES-24933)
* Die `Delete Modal` QuickInfo wird jetzt angezeigt, wenn Benutzer über das QuickInfo-Symbol fahren. Fokusaktionen zeigen jetzt denselben QuickInfo-Text an, was den Wiederholungszugriff für Maus- und Tastaturbenutzer verbessert. (SITES-24778)
* Die Navigation in der linken Leiste folgt jetzt der erwarteten Tastaturfokusreihenfolge, nachdem Benutzende die Leiste konfiguriert haben. Der Tabulatorfokus landet auf dem ausgewählten Bereich der linken Leiste anstelle des Umschalt-Displays, wodurch die Navigationsklarheit der Bildschirmlesehilfe verbessert wird. (SITES-24754)
* Fehlerkorrektur - Falsches NVDA-Feedback während der Farbfeld-Navigation im Modal „Benutzereinstellungen“ wird behoben. NVDA liest jetzt die Beschriftung für das Farbfeld, das den Fokus erhält, wodurch irreführende Farbausgaben entfernt werden. Das Farbfeldset unterstützt jetzt eine konsistente Tastaturnavigation und eine klare Auswahlerkennung. (SITES-24739)
* Reduzierte ausführliche NVDA-Ausgabe für die `Spin`. Redundante Gruppenbeschriftungen, die die Eingabebeschriftung dupliziert haben, wurden entfernt, sodass NVDA den Namen des Steuerelements nur einmal ankündigt. Die Navigation über Tastatur und Bildschirmlesehilfe bietet jetzt eine einzige, klare Ankündigung. (SITES-24725)
* Im Dialogfeld „Karussell“ wird der Fokus nun auf die Dialogfeldüberschrift anstelle der Registerkarte „Elemente“ gelegt. Abbrechen und Esc stellen den Fokus auf das Steuerelement wieder her, das das Dialogfeld gestartet hat, wodurch die ausführliche NVDA-Ausgabe reduziert wird. (SITES-24716)
* Das Dialogfeld für die Link-Auswahl richtet nun die programmgesteuerte Beschriftung an der Bildschirmbeschriftung für Baumstrukturelemente der letzten Ebene aus. Die Pfeiltasten-Navigation Trigger eine verlässliche Ankündigung der Bildschirmlesehilfe für jedes Element und entfernt irreführende Etikettenausgaben. (SITES-24710)
* Das Dialogfeld zum Öffnen der Link-Auswahl wird jetzt unter einem 320-Pixel-Viewport korrekt wiedergegeben. Der Inhalt wird nicht mehr über das Modal oder abgeschnitten und das Modal zeigt keine horizontale Bildlaufleiste mehr an. (SITES-24709)
* Das Dialogfeld zum Öffnen der Link-Auswahl stellt jetzt den Tastaturfokus nach Schließen oder Abbrechen wieder auf den Trigger des Dialogfelds her. Der Fokus springt nicht mehr zur Link-Eingabe, wodurch der Kontext der Sprachausgabe stabil bleibt und die zusätzliche Navigation reduziert wird. (SITES-24707)
* Das modale Dialogfeld „Bild“ folgt jetzt einer logischen Fokussequenz. Der Fokus überspringt nach dem Abbrechen nicht mehr frühere Steuerelemente oder Drops auf dem Orientierungspunkt der Seite, und Benutzende fokussieren nach dem Beenden wieder auf die Schaltfläche Konfigurieren . (SITES-24693)
* Das modale Dialogfeld „Leiste „Verweise“ hält jetzt den Tastaturfokus auf. Die Registerkarten und Umschalt+Tab bleiben innerhalb der Dialogfeldsteuerelemente, und der Fokus wird nicht mehr an den Seiteninhalt weitergegeben. Die Sprachausgabe gibt nur den Inhalt von Dialogfeldern aus. (SITES-24683)
* Das Modal „Hyperlink-Pfadauswahl“ legt jetzt den Fokus auf die Dialogfeldüberschrift beim Öffnen. Abbrechen schließt das Dialogfeld und stellt den Fokus auf die Schaltfläche Auswahl-Dialogfeld öffnen wieder her, wodurch Fokusverlust und redundante Bildschirmlesehilfen verhindert werden. (SITES-24672)
* Das Suchfeld verwendet jetzt eine beständige On-Screen-Beschriftung anstelle von Platzhaltertext. Die Beschriftung bleibt während der Eingabe sichtbar, wodurch die Klarheit für Benutzende von Tastatur, Bildschirmleser und Sprache verbessert wird. (SITES-24529)
* Das modale Dialogfeld „Teaser“ legt jetzt den Fokus auf die Dialogfeldüberschrift beim Öffnen. Beim Schließen des Dialogfelds wird der Fokus wieder auf das `Configure`-Steuerelement gesetzt, wodurch Fokusverlust und eine übermäßige Ausgabe der Sprachausgabe verhindert werden. (SITES-24522)
* Die Seitenleiste des Assets-Bedienfelds enthält jetzt ein Steuerelement zum Schließen. Durch Schließen wird der Tastaturfokus auf den Umschalter für die Seitenleiste zurückgesetzt und das erzwungene Durchblättern des Bereichsinhalts wird verhindert. (SITES-24489)
* Die Tabulatortaste auf der Tastatur greift jetzt auf Schaltflächen und Links in Admin-Tabellen zu. Benutzende verlassen sich nicht mehr auf die Pfeiltasten-Zellnavigation, um interaktive Steuerelemente zu finden. (SITES-24285)
* Das Dialogfeld Bildkomponente zeigt keine dekorativen Hilfs- und Vollbildsymbole mehr als Bilder an. Bildschirmlesehilfen überspringen jetzt diese Symbole, wobei der Fokus auf umsetzbaren Steuerelementen und Feldinhalten verbleibt. (SITES-2940)
* Sites Admin entfernt jetzt die Rolle Bild aus den Miniaturansichtssymbolen des Ordners. Die Hilfstechnologie überspringt diese dekorativen Elemente und behält den Fokus auf Ordnernamen und Aktionen. (SITES-2852)
* Die Inhaltsstruktur leitet jetzt den Tastaturfokus zum aktiven Baumstrukturelement oder ersten Baumstrukturelement weiter. Der Baum-Container fungiert nicht mehr als leerer Tabulatorstopp, was Umschalt- und Tabulatorfokusfallen verhindert. (SITES-1577)

#### Admin-Benutzeroberfläche{#sites-adminui-65-lts-sp2}

Die Listenansichtseinstellungen der Sites-Konsole spiegelten die in der Listenansicht angezeigten Spalten nicht wider. Das Dialogfeld wurde geöffnet, wobei die Kontrollkästchen deaktiviert und die Anzahl der ausgewählten Spalten falsch war. Das Dialogfeld Synchronisierung korrigieren stellt den Status mit den aktiven Rasterspalten her und aktualisiert den Zähler entsprechend der tatsächlichen Spaltensichtbarkeit. (SITES-38576)

#### Klassische Benutzeroberfläche{#sites-classicui-65-lts-sp2}

Bei der Bearbeitung der klassischen Textkomponente wurden nach einem Upgrade unformatierte HTML-Tags anstelle von Rich-Text angezeigt. Service Pack 2 korrigiert das Rendering des RTE der klassischen Benutzeroberfläche (Rich-Text-Editor), sodass der Editor formatierte Inhalte anzeigt und gespeichertes Markup beibehält. Die Korrektur stoppt auch die Markup-Erweiterung während wiederholter Bearbeitungen und speichert. (SITES-38709)

#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp2}

Der Unterstützung von Headless-Ereignissen fehlten die erforderlichen OSGi-Ereignisse für Inhaltsfragmente und -modelle in 6.5 LTS. Das Update fügt das Eventing-Bundle sowie die erforderlichen Abhängigkeiten hinzu und enthält einen 6.5 LTS-Build. Inhaltsfragment- und Modellereignisse werden jetzt korrekt ausgelöst und unterstützen Launches-API-Workflows. (SITES-35329)

#### [!DNL Content Fragments] – Admin{#sites-admin-65-lts-sp2}

* Die Komponentenverarbeitung in der Authoring-Oberfläche von Sites wurde angepasst, um unregelmäßiges Verhalten während Seitenaktualisierungen zu stoppen. Der Fehler führte zu unvorhersehbaren Editor-Antworten, die routinemäßige Inhaltsänderungen beeinträchtigten und die Workflow-Effizienz verringerten. Die Aktualisierung stimmt die Editor-Logik mit den erwarteten Interaktionsmustern ab und bietet eine zuverlässige Leistung bei Authoring-Aktivitäten. (SITES-35078) CRITICAL

* Eine Regression führte zu einer Unterbrechung der Assets-Konsolen-Listenansicht für Inhaltsfragmente und löste einen Fehler beim Rendern der Liste aus. Durch die Aktualisierung wird die Listenansichtslogik nach dem Entfernen der Vorschau-Info korrigiert und die stabile Listenausgabe wiederhergestellt. Die Konsole zeigt jetzt Inhaltsfragmente ohne Fehler an und hält Listeninteraktionen nutzbar. (SITES-38683)
* Der Inhaltsfragment-Editor lokalisiert jetzt die Tag-Kennzeichnung. Der Editor lokalisiert auch die Bezeichnung Sammlungen , sodass der Benutzeroberflächentext mit dem ausgewählten Gebietsschema übereinstimmt. (SITES-977)


#### [!DNL Content Fragments] – Fragmenteditor{#sites-fragments-editor-65-lts-sp2}

* Die Tags der Inhaltsfragmentvariante verschwanden, als der Umschalter für die Funktion nach der Umgestaltung deaktiviert blieb. Die Fehlerbehebung stellt die Unterstützung von Varianten-Tags wieder her, auch wenn dieser Umschalter deaktiviert bleibt. Autoren können im Inhaltsfragment-Editor wieder Varianten-Tags hinzufügen und anzeigen. (SITES-38682) CRITICAL
* Bearbeitete Inhaltsfragmente verschwanden aus der Assets-Konsolenliste, nachdem Autorinnen und Autoren zurück aus dem Inhaltsfragment-Editor navigiert waren. Die Browser-Zwischenspeicherung hat eine veraltete Liste zurückgegeben und das aktualisierte Fragment bis zu einer manuellen Aktualisierung ausgeblendet. Durch die Korrektur wird eine Cache-Steuerelementverarbeitung für den Rückgabepfad des Editors hinzugefügt, damit die Liste korrekt neu geladen wird und das bearbeitete Fragment sichtbar bleibt. (SITES-35374) CRITICAL

* Der Inhaltsfragment-RTE zeigte Layout- und visuelle Probleme nach den letzten Änderungen des Benutzeroberflächen-Stils. Service Pack 2 verfeinert die RTE-Formatierung, sodass die Symbolleiste und der bearbeitbare Bereich korrekt dargestellt werden und lesbar bleiben. Der Inhaltsfragment-Editor wird jetzt am Erscheinungsbild und Verhalten des Seiteneditors ausgerichtet. (SITES-38684)
* Durch das Entfernen von IMS-Bereichen vom Polaris-Asset-Selektor wurde die Integration von Inhaltsfragmenten mit dem Versand-Endpunkt unterbrochen. Autoren schlagen beim Öffnen des Remote-Asset-Wählers und beim Auswählen von Assets auf Fehler. Die Aktualisierung fügt die erforderlichen IMS-Bereiche erneut hinzu und stellt den stabilen Zugriff auf die Bereitstellungsebene wieder her. (SITES-35837)
* Das Bedienfeld „Zugehörige Inhalte“ rendert keinen hartcodierten Platzhalter „undefiniert“ mehr. Der Inhaltsfragment-Editor löst diesen Text jetzt durch Lokalisierungsressourcen auf, sodass Editoren übersetzten Text in der Benutzeroberfläche sehen. (SITES-33675)
  <!-- REMOVED FROM BUG LIST FEBRUARY 13, 2026 * Preview error messaging now uses localized strings instead of raw `Cannot print fragment's Json` text. The Content Fragment Editor now shows translated output across locales during GraphQL endpoint resolution failures. (SITES-33666)-->
* Im Inhaltsfragment-Editor wird jetzt eine übersetzte Registerkartenbeschriftung Allgemein für alle Gebietsschemata angezeigt. Der Editor ersetzt nicht lokalisierten Registerkartentext und entfernt interne IDs aus Registerkartentiteln. (SITES-30715)
* Der Inhaltsfragment-Editor zeigt jetzt übersetzte Namen für zulässige Asset-Typen an. In der Auswahlliste werden keine internen Zeichenfolgen und Nur-Englisch-Bezeichnungen mehr gemischt, wenn Autoren Inhaltsreferenz-Einschränkungen konfigurieren. (SITES-29699)

#### [!DNL Content Fragments] – GraphQL-API {#sites-graphql-api-65-lts-sp2}

* Die Validierung von GraphQL-Abfragen wurde verfeinert, um Bereitstellungsfehler zu stoppen, die durch Fehler bei der Filterausführung verursacht wurden. Der Fehler verursachte beim Anwendungsstart Ausnahmen und blockierte den erfolgreichen Rollout in betroffenen Umgebungen. Die Revision stellt ein konsistentes Validierungsverhalten sicher und ermöglicht eine reibungslose Bereitstellung ohne Unterbrechung der Abfragevalidierung zur Laufzeit. (SITES-34301) CRITICAL

* Das Dialogfeld GraphQL-Endpunkt bearbeiten zeigt jetzt lokalisierte Zeichenfolgen der Benutzeroberfläche an. Das Dialogfeld zeigt keinen reinen englischen Text mehr an, z. B. &quot;GraphQL schema is taken from configuration“ (Das-Schema wird aus der Konfiguration übernommen), und die zugehörigen Kennzeichnungen werden in allen Gebietsschemata korrekt dargestellt. (SITES-34018)

#### [!DNL Content Fragments] – GraphQL-Abfrage-Editor{#sites-graphql-query-editor-65-lts-sp2}

* Die Validierung von GraphQL-Abfragen wurde verfeinert, um Bereitstellungsfehler zu stoppen, die durch Fehler bei der Filterausführung verursacht wurden. Der Fehler verursachte beim Anwendungsstart Ausnahmen und blockierte den erfolgreichen Rollout in betroffenen Umgebungen. Die Revision stellt ein konsistentes Validierungsverhalten sicher und ermöglicht eine reibungslose Bereitstellung ohne Unterbrechung der Abfragevalidierung zur Laufzeit. (SITES-35529)
* GraphQL Explorer schlägt nicht mehr fehl, wenn ein Konfigurations-Browser-Name CJK-Zeichen enthält. Die Endpunkterstellung und der gespeicherte Abfragezugriff funktionieren normal und die GraphQL-Abfrage-Editor-Seite bleibt fehlerfrei. (SITES-31616)

#### [!DNL Content Fragments] - Modell-Editor{#sites-model-editor-65-lts-sp2}

* Verschachtelte Inhaltsfragmentmodelle funktionieren jetzt nicht mehr, wenn die Funktion durch einen deaktivierten Umschalter umstrukturiert wird. Die Fehlerbehebung stellt die Unterstützung verschachtelter Modelle wieder her, ohne dass Umschaltänderungen erforderlich sind. Autoren können im Modell-Editor wieder verschachtelte Modelle erstellen und verwenden. (SITES-38681) CRITICAL

* Der Filterbereich für Inhaltsfragmentmodelle stellt nicht mehr lokalisierte Zeichenfolgen bereit. AEM zeigt jetzt lokalisierte Filterbeschriftungen und lokalisierte Statuswerte für alle Gebietsschemata an. (SITES-30863)
* Der Inhaltsfragmentmodell-Editor rendert jetzt lokalisierte Zeichenfolgen für das Dialogfeld „Sperrwarnung“. Die Benutzeroberfläche ersetzt nicht lokalisierte englische Nachrichten durch Gebietsschema-Ressourcen in allen unterstützten Sprachen. (SITES-28592)

#### [!DNL Content Fragments] – REST-API{#sites-restapi-65-lts-sp2}

AEM Headless benötigte eine dedizierte Versionsverzweigung, um Abhängigkeiten und Paketversionskonflikte mit Mainline-Builds zu vermeiden. Die Aktualisierung fügt eine Headless-Verzweigung für Version/6.5lts hinzu und richtet Abhängigkeitssätze und Bundle-Versionen aus. Jenkins erstellt die Headless-Codebasis nun sauber und ohne Versionskollisionen. (SITES-36585)

<!-- #### Component console{#sites-component-console-65-lts-sp2} -->

#### Inhalts-API{#sites-content-api-65-lts-sp2}

Ein Feature-Toggle-Fehler meldet falsch den Status der Page Management-API. Die Aktualisierung fügt ein dediziertes Aktivierungs-Flag hinzu und bewertet es zusammen mit dem vorhandenen Umschalter. Die Seitenverwaltungs-API zeigt jetzt einen stabilen Status an. Die Site Management-API bleibt experimentell. (SITES-39284)

#### Core-Backend{#sites-core-backend-65-lts-sp2}

* Eine Änderung des Authoring-Erlebnisses in Sites, um inkonsistentes Verhalten zu beheben, das die standardmäßigen Seitenbearbeitungs-Workflows gestört hat. Autoren stießen bei der Komponenteninteraktion auf unerwartete Ergebnisse, die die Inhaltsaktualisierung beeinträchtigten und die Zuverlässigkeit beeinträchtigten. Durch die Änderung wird das stabile Editor-Verhalten wiederhergestellt und die konsistente Ausführung von Authoring-Aktionen in den betroffenen Szenarien sichergestellt. (SITES-35162) CRITICAL

* Das Authoring-Verhalten von Sites wurde verfeinert, um ein Problem zu beheben, das die Seitenbearbeitung unterbrochen und zu inkonsistenten Ergebnissen bei der Komponenteninteraktion geführt hat. Autoren erlebten unerwartete Benutzeroberflächenantworten, die die Inhaltsaktualisierung beeinträchtigten und die Zuverlässigkeit des Workflows verringerten. Die Änderung stellt eine stabile Verwaltung des Editor-Status wieder her und gewährleistet eine vorhersehbare Ausführung von Authoring-Aktionen in den betroffenen Szenarien. (SITES-34499)

<!--
#### Core Components{#sites-core-components-65-lts-sp2}

#### Campaign integration{#sites-campaign-integration-65-lts-sp2}

#### Experience Fragments{#sites-experiencefragments-65-lts-sp2}

#### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp2}
-->

#### Launches{#sites-launches-65-lts-sp2}

* Während der Launch-Promotion zeigte die Sites-Zeitleiste hartcodierten englischen Text: „Erstellte Version … vor der Launch-Promotion“. Die Aktualisierung ersetzt die hartcodierte Zeichenfolge durch die Behandlung lokalisierter Nachrichten. Die Zeitleiste zeigt jetzt lokalisierten Text an und stimmt den Eintrag mit dem standardmäßigen AEM-Lokalisierungsverhalten ab. (SITES-39157)
* Der Umfang der Launch-Promotion war unterschiedlich, wenn Autoren einen Unterabschnitt mit der Option Aktuelle Seite und Unterseiten hochstufen hochgestuft haben. AEM hat auch nicht verwandte Seiten hochgestuft und unerwartete Live-Site-Änderungen verursacht. Durch die Korrektur wird die Berechnung des Launch-Umfangs korrigiert, sodass nur die ausgewählte Unterstruktur höher stuft. (SITES-38315)
* Inhaltsfragmente in Launches waren nicht am `damAssetLucene`-Index beteiligt und haben die Suchergebnisse und die Abfrageeffizienz eingeschränkt. Durch diese Änderung werden Launch-Inhaltsfragmentpfade zur Indexdefinition hinzugefügt. Suchen und benutzerdefinierte Abfragen finden jetzt Inhaltsfragmente unter `/content/launches`. (SITES-35634)
* In der Launch-Benutzeroberfläche wurden die Launch-Steuerelemente für Inhaltsfragmente angezeigt, obwohl das Produkt keine Inhaltsfragment-Launches in der Touch-Benutzeroberfläche verfügbar macht. Durch diese Änderung werden die Codepfade für Inhaltsfragmentstarts von cq-launches-content entfernt und die Filterung der Launch-Liste angepasst. Autoren sehen jetzt konsistente Seiten-Launch-Optionen ohne Inhaltsfragment-Launch-Einträge. (SITES-35633)
* In AEM 6.5 LTS Quickstart fehlten erforderliche Launches-Bundles und Voraussetzungen, wodurch die OpenAPI-Aktivierung von Launches blockiert wurde. Die Aktualisierung fügt Launch-Bundles und erforderliche Abhängigkeiten hinzu, z. B. Unterstützung von Metriken, DAM-cfm-Aktualisierungen und Warteschlangenkonfiguration. Launches-APIs werden jetzt auf 6.5 LTS QuickStart ausgeführt, wobei die erforderlichen Laufzeitkomponenten vorhanden sind. (SITES-35297)
* Die CF Launches-Paketerstellung zog neuere Abhängigkeitsversionen und unnötige GraphQL-Bibliotheken hinzu, was die Integration von AEM 6.5 LTS erschwerte. Durch diese Änderung werden Abhängigkeitsversionen an der AEM 6.5 LTS-Baseline ausgerichtet und nicht verwendete GraphQL-Abhängigkeiten entfernt. Die Paketauflösung bleibt jetzt konsistent und der CF-Start bleibt stabil. (SITES-35295)
* AEM Launches führt jetzt eine dedizierte Jenkins-Pipeline für die 6.5-LTS-Verzweigung aus. Die Pipeline führt nächtliche Builds aus und sendet Fehlerwarnungen per E-Mail. Diese Konfiguration erhöht die Testabdeckung und erfasst Regressionen frühzeitig. (SITES-35293)
* AEM 6.5 LTS stellt jetzt ein aktualisiertes Launches-API-Bundle mit abgestimmten Artefaktversionen bereit. Das Bundle verfolgt die primäre Code-Zeile und behält dabei die korrekte Version der LTS-Version 6.5 bei. Dieses Update stabilisiert die Nutzung der Launches-API im gesamten 6.5 LTS-Stack. (SITES-35292)
* AEM 6.5 LTS enthält jetzt ein aktualisiertes Launches-Core-Bundle mit abgestimmten Abhängigkeitsversionen. Die Aktualisierung fügt die Core-Handhabung von Launches für die Datentypen „Fragment-UUID“ und „Referenz-UUID“ hinzu. Die Launch-Verarbeitung sorgt jetzt für ein konsistentes Verhalten in allen Launches und Inhaltsfragment-Workflows. (SITES-35290)
* Der Sites-Editor wurde verfeinert, um inkonsistentes Verhalten zu beheben, das normale Seitenerstellungs-Workflows gestört hat. Autoren stießen auf unerwartete Komponenteninteraktionen, die die Inhaltsaktualisierung behinderten und die Bearbeitungszuverlässigkeit beeinträchtigten. Die Änderung stellt eine konsistente Verwaltung des Benutzeroberflächenstatus wieder her und gewährleistet eine vorhersehbare Ausführung von Authoring-Aktionen in den betroffenen Szenarien. (SITES-35138)
* Beim Start von Bearbeiten wird nun lokalisierter Fehlertext anstelle der hartcodierten `Provided path is not a launch` angezeigt. Die Benutzeroberfläche rendert jetzt übersetzte Nachrichten sprachübergreifend, wenn Edit einen ungültigen Startpfad erhält. (SITES-33360)
* AEM 6.5 LTS enthält jetzt die Launches-OpenAPI-Side-Port-Arbeit. Durch die Aktualisierung werden Launches-API-Bundles, Inhaltspakete und erforderliche Schnellstart-Artefakte paritätisch zusammengeführt. Außerdem werden Inhaltsfragment-Launches und OpenAPI-Szenarien mit stabiler CI-Validierung ermöglicht. (SITES-32050)
* Die Launch-Benutzeroberfläche lokalisiert jetzt die überschriebene Vorlagenbeschriftung. Vorlagenüberschreibungsdetails zeigen jetzt übersetzten Text anstelle einer nur auf Englisch übersetzten Zeichenfolge an. (SITES-29525)
* AEM hat einen fehlenden Lokalisierungsschlüssel unter **Sites** > **Launches** > **Bearbeiten** behoben. Benutzern wird jetzt eine übersetzte Fehlermeldung anstelle der rohen Zeichenfolge „Quellliste kann nicht aktualisiert werden“ angezeigt. (SITES-21499)
* Die Benutzeroberfläche der Launch-Promotion zeigt jetzt lokalisierte Statusbeschriftungen und Aktionen an. Im Vorschaubereich werden übersetzte Texte für **Deleted**, **New** und **View** anstelle von rohen englischen Zeichenfolgen angezeigt. (SITES-13540)
* Die Launch-Erstellung zeigt jetzt lokalisierte Fehlermeldungen an. Die Benutzeroberfläche zeigt keine rohen englischen Zeichenfolgen mehr an, z. B. `Unable to create launch page`, `Source root resource is not a page` oder `Mandatory parameter is missing`. (SITES-13085)


<!-- #### Link Checker{#sites-link-checker-65-lts-sp2} -->


#### MSM – Live Copies{#sites-msm-live-copies-65-lts-sp2}

* Admins hatten während der Inhaltsänderungen nur eingeschränkte Einblicke in die MSM-Push-on-Modify-Verarbeitung. Die Fehlerbehebung fügt eine detaillierte Protokollierung zum Empfang von MSM-Ereignissen und zur Ausführung des Rollouts hinzu. Die Debug-Ausgabe zeigt jetzt an, welche Ereignisse ausgelöst wurden, welche Inhaltspfade sich geändert haben und wer die Änderung ausgelöst hat. (SITES-38029)
* AEM hat ein Lokalisierungs-Layout-Problem im Feld Rollout-Datum der Blueprint behoben. Die Datumsaufforderung passt nun zum Steuerelement und bleibt in allen unterstützten Sprachen lesbar, einschließlich `fr_FR`. (SITES-14961)

<!-- #### Page editor{#sites-pageeditor-65-lts-sp2} -->

#### Replikation{#sites-replication-65-lts-sp2}

Die Seiteneditor-Veröffentlichung verarbeitet jetzt URLs, die Selektoren oder Suffixe enthalten. Die veröffentlichte Anfrage sendet jetzt den JCR-Seitenpfad, keine Selektor- oder Suffix-URL-Zeichenfolge, sodass die Aktivierung abgeschlossen ist und der Inhalt live geschaltet wird. Die Replikation gibt jetzt bei einem Fehler den Fehlerstatus zurück, wodurch falsche „Veröffentlichung gestartet“-Meldungen verhindert werden. (NPR-43288)

<!-- #### Rich Text Editor{#sites-rte-65-lts-sp2} -->

#### Vorlageneditor{#sites-template-editor-65-lts-sp2}

Der Text zum Vorlagenstatus wird für einige Gebietsschemata vertikal unter **Tools** > **Allgemein** > **** angezeigt. Die Bezeichnung „veraltet“ unterbrach das Layout und las als Zeichenspalte. Durch die Korrektur wird der Stil des Vorlagenstatus korrigiert, sodass die Beschriftung auf einer einzigen horizontalen Linie gerendert wird. (SITES-36797)

#### Universeller Editor {#sites-universal-editor-65-lts-sp2}

* Eine OSGi-Standardkonfiguration wurde als `preview=true` festgelegt und zwang den universellen Editor, im Vorschaumodus zu starten. Durch diese Aktualisierung wird der Standardwert korrigiert und das standardmäßige Eingabeverhalten in der Produktion wiederhergestellt. Der universelle Editor wird jetzt im Produktionsmodus geöffnet, es sei denn, ein Administrator aktiviert ausdrücklich den Vorschaumodus. (SITES-37193)
* Der Befehl Öffnen im universellen Editor ist jetzt in Entwicklungs- und Staging-Umgebungen standardmäßig auf den Vorschaumodus eingestellt. Der Befehl fügt preview=true hinzu, wodurch Autorenprüfungen an den Vorschaukontext angepasst werden und versehentliche Produktionsöffnungen vermieden werden. (SITES-33839)

### [!DNL Assets]{#assets-65-lts-sp2}

Assets Relate funktioniert jetzt für Dateinamen, die Leerzeichen enthalten. Aktualisierte Relate Client-Logik verarbeitet jetzt Platzierungen enthaltende Pfade korrekt und vermeidet `undefined` Quellfehler bei der Beziehungsauswahl. Das Dialogfeld „Relation“ wird jetzt geöffnet und speichert Relationen ohne UI-Hänge oder Spinner. DAM-Benutzer können Assets verknüpfen, ableiten und die Verknüpfung aufheben, ohne Dateien umzubenennen. (Assets-56418)

#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp2}

* Neue Integration des Dynamic Media-Video-Players (begrenzter Rollout) - In AEM 6.6 QuickStart ist jetzt ein neues Dynamic Media-Video-Player-Erlebnis verfügbar. Diese Verbesserung ist derzeit nur für Erstkunden im Rahmen eines kontrollierten Rollouts aktiviert. (Assets-60165)
* Es wurde ein Problem behoben, bei dem die Option Miniaturansicht auswählen im Dialogfeld Videoeigenschaften die Asset-Auswahl nicht geöffnet hat und Benutzenden wieder benutzerdefinierte Miniaturansichten für Video-Assets auswählen konnte. (Assets-58926)
* In Dynamic Media wurde Unterstützung für die Auswahl von Arabisch in der Dropdown-Liste Untertitel und Audiospuren hinzugefügt, sodass Autorinnen und Autoren arabische Untertitel direkt in AEM verwalten können. (Assets-61771)

<!-- #### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp2} -->


<!--
### [!DNL Forms]{#forms-65-lts-sp2}

#### Forms Designer

#### Forms

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
* Die JMX-Konsole und die Web-Konsole senden jetzt eine `Content-Type: text/css header` für CSS-Ressourcen der Konsole. Die strikte MIME-Überprüfung blockiert nicht mehr das Laden von Stylesheets, sodass die `/system/console/jmx` Benutzeroberfläche mit normalem Stil gerendert wird. (GRANITE-63677)
* AEM vermeidet jetzt doppelte ACL-Einträge für die `contributor` im generierten `WEB-INF/resources/provisioning/model.txt`. Die WAR-Ausgabe enthält jetzt einen konsistenten ACL-Block, der verwirrende Berechtigungsunterschiede bei der Überprüfung verhindert. (GRANITE-63269)
* AEM löscht die Deserialisierungs-Firewall-Blockierungsliste auf die Zulassungsliste setzte und die Paketaktualisierungseinstellungen nicht mehr. Die aktualisierte Filterregistrierungslogik sorgt dafür, dass die aktive Firewall-Instanz mit der gespeicherten Konfiguration abgestimmt ist, sodass der Schutz ohne Neustart aktiviert bleibt. (GRANITE-61382)
* Die Felix-Web-Konsole gibt während des `NullPointerException`-Zugriffs keine zeitweiligen `/system/console` mehr aus. Die ServiceTracker-Handhabung verhindert einen Null-Tracker-Status. Konsolenanmeldung und -navigation bleiben bei wiederholten Anfragen und automatisierter Validierung stabil. (GRANITE-61042)

<!--
#### Campaign{#foundation-campaign-65-lts-sp2}

#### Cloud Services{#foundation-cloudservices-65-lts-sp2}

#### Communities {#foundation-communities-65-lts-sp2}

#### Content distribution{#foundation-content-distribution-65-lts-sp2}
-->

#### CRX {#foundation-crx-65-lts-sp2}

CRXDE Lite zeigt keine leere Registerkarte mehr an, wenn Sie nach einem Service Pack-Upgrade eine JSP-Datei öffnen. AEM bietet jetzt übereinstimmenden CodeMirror-Kern und Add-on-Code, wodurch der schwerwiegende Browser-Fehler verhindert und der Editor nutzbar bleibt. (GRANITE-64333)

#### Granite{#foundation-granite-65-lts-sp2}

Der Expression Security Validator verarbeitet jetzt leere oder null OSGi-Konfigurationswerte. Es wendet sichere Standardwerte an, ignoriert leere Arrays und zeichnet Protokolle auf, verhindert NullPointerException und unvorhersehbare Validierungsergebnisse. (NPR-43163)

<!-- #### HTL{#foundatoin-htl-5-lts-sp2} -->

#### Integrationen{#foundation-integrations-65-lts-sp2}

AEM synchronisiert jetzt Adobe Target-Aktivitäten, auch wenn Start- und Enddatum vorhanden sind. Die Target-Payload formatiert Aktivitätsdaten jetzt als vollständige ISO 8601-Zeitstempel, einschließlich Sekunden, Millisekunden und Zeitzone. Target lehnt die Anfrage nicht mehr mit `InvalidJson.Json` ab. Geplante Aktivitäten werden jetzt in einen synchronisierten Status versetzt, anstatt nicht synchronisiert zu bleiben. (CQ-4360733)

<!--
#### Jetty{#foundation-jetty-65-lts-sp2}

#### Localization{#foundation-localization-65-lts-sp2} 



#### Omnisearch{#foundation-omnisearch-65-lts-sp2}

#### Platform{#foundation-platform-65-lts-sp2}

#### Projects{#foundation-projects-65-lts-sp2}
-->

#### Oak {#foundation-oak-65-lts-sp2}

Für AEM 6.5 LTS Service Pack 2 ist der S3-Connector 1.60.10 oder höher erforderlich. Die S3-Datenspeicher-Konfiguration umfasst jetzt `crossRegionAccess` und `mode`, sodass Administratoren bei Bedarf den regionenübergreifenden Bucket-Zugriff aktivieren und den Speicher auf GCP umstellen können. `s3EndPoint` erwartet jetzt einen Bereich, der an `s3Region` ausgerichtet ist, oder er bleibt leer, sodass der Treiber den Endpunkt generiert. (GRANITE-64873)


#### Schnellstart{#foundation-quickstart-65-lts-sp2}

* Sling aktualisiert die administrativ-login-Zulassungsliste für die Verwendung von inklusiver Terminologie und neuen Konfigurations-PIDs. Diese Änderung entspricht Sling JCR Base 3.2.0. (GRANITE-63756)

  **Impact**

   * Sling verwirft diese PIDs und Sie sollten sie aus Ihren Konfigurationen entfernen:
      * Factory-PID: `org.apache.sling.jcr.base.internal.LoginAdminWhitelist.fragment`
      * Globale PID: `org.apache.sling.jcr.base.internal.LoginAdminWhitelist`
Diese älteren Konfigurationen verwenden Eigenschaften wie `whitelist.name` und `whitelist.bundles`.

   * Sling bietet weiterhin teilweise Abwärtskompatibilität für veraltete PIDs, verwendet sie jedoch nicht für neue Konfigurationen. Verwenden Sie stattdessen die neueren `LoginAdminAllowList.*` PIDs.
   * Auf die Zulassungsliste setzen Führen Sie nicht veraltete und neue Dateikonfigurationen gleichzeitig aus. Gemischte Konfigurationen können Unklarheiten verursachen und unbeabsichtigtes Verhalten hervorrufen. Wenn Sie zu AEM 6.5 LTS SP2 migrieren, entfernen Sie die veralteten PIDs vollständig.

  **Was sollten Sie tun**

   1. Suchen Sie nach Zulassungsliste-Konfigurationen, die `LoginAdminWhitelist*` PIDs verwenden.
   1. Ersetzen Sie sie durch die entsprechenden neuen PIDs:

      * Factory-PID: `org.apache.sling.jcr.base.LoginAdminAllowList.fragment`
      * Globale PID: `org.apache.sling.jcr.base.LoginAdminAllowList`

      Weitere Informationen finden Sie unter [Veralteter Ansatz zur Zulassungsliste von Bundles für die Administratoranmeldung](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html#deprecated-approach-to-allowlist-bundles-for-administrative-login).

* AEM 6.5 LTS SP2 aktualisiert den Foundation-Layer-Bundle-Satz für Sling, Oak und Felix. Diese Upgrades stärken die Kernlaufzeitstabilität und richten Abhängigkeitsversionen plattformübergreifend aus. (GRANITE-61874)

<!--
#### Security{#foundation-security-65-lts-sp2}

AEM now prevents NullPointerException errors when a logged-in user lacks read access for some groups and opens the Groups tab. The tab now hides groups without access and renders group membership details without a blank or unresponsive UI. (NPR-43311) -->

#### Sling{#foundation-sling-65-lts-sp2}

AEM enthält jetzt Sling Engine 2.16.6. Durch diese Änderung werden XSS-Verletzungen eliminiert, die von Sicherheits-Tools gekennzeichnet werden, und die Sicherheit und Stabilität des Core-Renderings verbessert. (NPR-43105)

<!--
#### Translation{#foundation-translation-65-lts-sp2}

#### User interface{#foundation-ui-65-lts-sp2}
-->

#### WCM{#foundation-wcm-65-lts-sp2}

AEM Translations schlägt auf Java 17 oder Java 21 aufgrund von Problemen mit dem XLIFF-Format nicht mehr fehl. Die Export-Pipeline erzeugt jetzt standardkonforme XLIFF-Dateien, die von Übersetzungsdienstleistern akzeptiert werden. Durch diese Änderung werden Unterbrechungen von Übersetzungsaufträgen entfernt und eine vorhersehbare Übergabe zwischen AEM und Übersetzungsdiensten wiederhergestellt. Übersetzungs-Workflows bleiben jetzt in allen unterstützten Java-Laufzeiten stabil. (CQ-4360217)

#### Workflow{#foundation-workflow-65-lts-sp2}

EmailNotificationService-Processor meldet keine Trigger mehr, die während der Verarbeitung von Workflow-Benachrichtigungen wiederholt Fehler des Typs „Segment nicht gefunden“ verursachen. Aktualisierte Ausnahmebehandlung erkennt SegmentNotFoundException und stoppt die Verarbeitungsschleife, anstatt mit ungültigen Lesevorgängen fortzufahren. Die Workflow-Ausführung bleibt stabil und das Protokollgeräusch sinkt beim Zugriff auf den Posteingang und die Arbeitselemente. (GRANITE-62635)




## Info [!DNL Experience Manager Foundation] {#experience-manager-foundation}

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
* Detaillierte Aktualisierungsanweisungen finden Sie im [Aktualisierungshandbuch für AEM Forms 6.5 LTS SP1 on JEE](https://experienceleague.adobe.com/en/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade)

#### Best Practices für AEM 6.5 LTS Service Pack-Upgrades

<!-- THE INFORMATION UNDER THIS HEADING CAME FROM CQDOC-23078 -->

**Umgebung**
Gilt für: AEM 6.5 LTS (On-Premise)-Kunden, die Service Pack 2 (SP2) installieren. SP2 wird als Schnellstart-JAR-Datei bereitgestellt.

**Warum ist das wichtig**
SP2 für AEM 6.5 LTS wird als Schnellstart-JAR und nicht als ZIP-Datei zur Installation über Package Manager bereitgestellt. On-Premise-Kundinnen und -Kunden führen ein Upgrade durch, indem sie die Schnellstart-JAR-Datei ersetzen, entpacken und neu starten. Diese Methode entspricht dem Upgrade-Verfahren von Adobe.

**Empfohlener Upgrade-Ablauf (Autoren- oder Veröffentlichungsinstanz)**

1. Stellen Sie sicher, dass Ihre AEM 6.5 LTS-Instanz fehlerfrei funktioniert und zugänglich ist.
1. Laden Sie die Schnellstart-JAR-Datei (z. B. `cq-quickstart-6.6.x.jar`) von Software Distribution herunter.
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
* Erstellen Sie ein vollständiges, wiederherstellbares Backup-Repository (plus alle externen Datenspeicher), bevor Sie beginnen.
* Lesen Sie die Anleitungen für das lokale Upgrade und die technischen Anforderungen von Adobe (Java 17/21 für LTS empfohlen).

>[!NOTE]
>
>Die oben aufgeführten Dateinamen (z. B. `cq-quickstart-6.6.x.jar`) spiegeln die für diese LTS-Version beobachtete Schnellstart-Artefaktbenennung wider. Verwenden Sie immer den genauen Dateinamen, den Sie von Software Distribution herunterladen.

## Installieren und Aktualisieren{#install-update}

Informationen zu Einrichtungsanforderungen finden Sie unter [Installationsanweisungen](/help/sites-deploying/custom-standalone-install.md).

>[!NOTE]
>
> Wenn Sie ein direktes Upgrade von alten 6.5 SPs auf LTS SP1 durchführen, befolgen Sie die Anweisungen für 6.5 bis 6.5 LTS GA [Upgrade](/help/sites-deploying/upgrade.md).


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

Adobe überprüft und entwickelt die Produktfunktionen kontinuierlich weiter, um durch die Modernisierung oder den Ersatz älterer Funktionen einen größeren Kundennutzen zu erzielen. Diese Änderungen werden unter sorgfältiger Berücksichtigung der Abwärtskompatibilität implementiert.

Um Transparenz zu gewährleisten und eine angemessene Planung zu ermöglichen, folgt Adobe diesem Prozess der Einstellung von Adobe Experience Manager (AEM):

* Die Einstellung wird zuerst angekündigt. Veraltete Funktionen bleiben weiterhin verfügbar, werden aber nicht mehr erweitert.
* Die Entfernung erfolgt nicht früher als bei der nächsten Hauptversion. Der geplante Zeitplan für die Entfernung wird separat mitgeteilt.
* Kunden, die auf unterstützte Alternativen umstellen möchten, erhalten mindestens einen Versionszyklus, bevor eine Funktion entfernt wird.

### Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden Funktionen aufgeführt, die Adobe in AEM 6.5 LTS nicht mehr unterstützt werden. In der Regel werden Funktionen von Adobe eingestellt, bevor sie aus einer zukünftigen Version entfernt werden, und es wird eine Alternative bereitgestellt.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung nutzen, und die Änderung ihrer Implementierung zu planen, um die bereitgestellte Alternative nutzen zu können.

| Bereich | Funktion | Ersatz | Version (SP) |
| --- | --- | --- | --- |
| Schnellstart | Mongo-APIs | Mongo-APIs werden nicht mehr unterstützt und sollen in zukünftigen Versionen entfernt werden. | 6.5 TS SP2 |
| Sites | Unterstützung von Inhaltsfragmenten in der AEM Assets-REST-API | AEM 6.5 LTS SP2 bietet moderne OpenAPIs für die Verwaltung von Inhaltsfragmenten und -modellen, sodass die älteren Endpunkte zur Unterstützung von Inhaltsfragmenten in der AEM Assets-REST-API jetzt nicht mehr unterstützt werden.<br>Adobe beabsichtigt, diese älteren Endpunkte bis zu einer Mitteilung über das Ende der Nutzungsdauer verfügbar zu halten. Adobe plant keine weiteren Verbesserungen an den veralteten Endpunkten. | 6.5 LTS SP2 |
| Sites | [SPA-Editor](/help/sites-developing/spa-overview.md) | Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind: <br>- der [universelle Editor](/help/sites-developing/universal-editor/introduction.md) zur visuellen Bearbeitung.<br>- der [Inhaltsfragment-Editor](/help/assets/content-fragments/content-fragments-managing.md) zur formularbasierten Bearbeitung. | 6.5 LTS GA |
| [!DNL Foundation] | Unterstützung für com.adobe.granite.oauth.server | Adobe IMS-Integration |  |

### Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden die Funktionen aufgeführt, die aus AEM 6.5 LTS entfernt wurden. In früheren Versionen wurden diese Funktionen als veraltet gekennzeichnet.

* Die Unterstützung für RDBMK für die Persistenz des CRX-Repositorys wurde entfernt.
* In Clusterumgebungen ist MongoMK jetzt die einzige unterstützte Option für die Repository-Persistenz.

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

### Installieren erforderlicher Oak-Indizes für Sites Headless-APIs{#site-headless-api}

Einige APIs, die zu Sites Headless verschoben wurden, erfordern zusätzliche Oak-Indizes, um die volle Funktionalität zu erhalten.

Installieren Sie das `cq-dam-cfm-indices`-Paket, um die folgenden Funktionen zu verwenden:

* Auflisten von Inhaltsfragmentmodellen
* Auflisten von Inhaltsfragmenten
* Such-API
* Workflows

Laden Sie das Indexpaket [cq-dam-cfm-](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/cq-dam-cfm-indices-1.1.2.zip)) vom Adobe Software Distribution-Portal herunter.

### Dispatcher-Verbindungsfehler mit Funktion „Nur SSL“ (behoben in AEM 6.5 LTS SP1 und höher){#ssl-only-feature}

>[!NOTE]
>
> Dieses Problem tritt nur in Version AEM 6.5 LTS GA auf.

Bei der Aktivierung der Funktion „Nur SSL“ in AEM-Bereitstellungen gibt es ein bekanntes Problem, das die Verbindung zwischen dem Dispatcher und AEM-Instanzen beeinträchtigt. Nach Aktivierung dieser Funktion können Konsistenzprüfungen fehlschlagen und die Kommunikation zwischen dem Dispatcher und AEM-Instanzen kann unterbrochen werden. Dieses Problem tritt insbesondere auf, wenn Kundinnen und Kunden versuchen, eine Verbindung über `https + IP` von Dispatcher zu AEM-Instanzen herzustellen. Dies steht im Zusammenhang mit SNI-Validierungsproblemen (Server Name Indication).

**Impact**

* Konsistenzprüfungsfehler mit HTTP 400-Antwort-Codes
* Unterbrochener Traffic zwischen Dispatcher und AEM-Instanzen
* Inhalte können nicht ordnungsgemäß über den Dispatcher bereitgestellt werden
* Verbindungsfehler bei Verwendung von HTTPS mit IP-Adressen in der Dispatcher-Konfiguration
* HTTP 400-Fehler vom Typ „Ungültige SNI“ bei der Verbindung über HTTPS + IP

**Betroffene Umgebungen**

* AEM-Bereitstellungen mit Dispatcher-Konfigurationen
* Systeme, in denen die Funktion „Nur SSL“ aktiviert wurde
* Dispatcher-Konfigurationen mit der Verbindungsmethode `https + IP` zu AEM-Instanzen

**Lösung**

Wenn dieses Problem auftritt, wenden Sie sich an den Adobe-Support. Zur Lösung dieses Problems ist Hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) verfügbar. Versuchen Sie nicht, „Nur SSL“-Funktionen zu aktivieren, bis Sie den erforderlichen Hotfix angewendet haben.

## Enthaltene OSGi- und Inhaltspakete{#osgi-bundles-and-content-packages-included}

In den nachfolgenden Textdokumenten sind die in [!DNL Experience Manager] 6.5 LTS, Service Pack 1 enthaltenen OSGi-Bundles und Inhaltspakete aufgeführt:

* [Liste der in Experience Manager 6.5 LTS, Service Pack 1 enthaltenen OSGi-Bundles](/help/release-notes/assets/65lts_sp1_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste der in Experience Manager 6.5 LTS, Service Pack 1 enthaltenen Inhaltspakete](/help/release-notes/assets/65lts_sp1_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-customer-support-experience).

