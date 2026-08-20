---
title: Aktuelle Versionshinweise für Adobe Experience Manager 6.5 LTS, SP3
description: Aktuelle Versionsinformationen zu Adobe Experience Manager 6.5 LTS, Service Pack 3 finden Sie.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 0ce890503d43af340b6ee3c85b1b563613627c78
workflow-type: tm+mt
source-wordcount: '6749'
ht-degree: 26%

---


# Aktuelle Versionshinweise für Adobe Experience Manager 6.5 LTS, SP3 {#release-notes}

## Versionsinformationen {#release-information}

| Produkt | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Version | Service Pack 3 (SP3) <!-- UPDATE FOR EACH NEW RELEASE --> |
| Typ | Service Pack-Version |
| Datum | &#x200B;20. August 2026 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.3.jar) |


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

<!-- **Mandatory Hotfix** – To avoid SNFE (SegmentNotFoundException) issues with offline compaction when installing SP2, install the hotfix described in [Known issues – Repository corruption during online compaction](#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146). -->

## Was in [!DNL Adobe Experience Manager] 6.5 LTS, SP3 enthalten ist {#what-is-new}

<!-- UPDATE EACH RELEASE -->

[!DNL Experience Manager] 6.5 LTS enthält SP3 neue Funktionen, wichtige von Kundschaft angeforderte Verbesserungen und Fehlerbehebungen. Seit der ersten Verfügbarkeit von 6.5 LTS im März 2025 werden Leistung, Sicherheit und Lokalisierung auf der gesamten Plattform verbessert. [Installieren Sie dieses Service Pack](#install-update) auf 6.5 LTS.

### Überblick über behobene Probleme {#fixed-issues-overview}

[!DNL Adobe Experience Manager] 6.5 LTS löst SP3 Probleme in [!DNL Sites] und [!DNL Experience Manager Foundation]. Die Korrekturen verbessern die Barrierefreiheit, die Zuverlässigkeit der Bearbeitung, die Bereitstellung von Headless-Inhalten, die Verwaltung mehrerer Sites und die Plattformstabilität. In den folgenden Abschnitten werden alle Fehlerbehebungen mit ihrer Referenznummer aufgeführt.

Die meisten Änderungen gelten für [!DNL Sites]:

* Verbesserte Barrierefreiheit in der größten -Gruppe. Die Aktualisierungen verbessern die Tastaturnavigation, das Feedback für Bildschirmlesehilfen, die Fokusverwaltung, das semantische Markup, den Textkontrast und die Touch-Target-Größe im Seiteneditor, in der Assets-Seitenleiste, in Filtern und auf den zugehörigen Authoring-Oberflächen.
* Fehlerbehebungen in [!DNL Content Fragments] umfassen den Fragment-Editor, den Modell-Editor, die REST-API und die GraphQL-API. Der aktualisiert die korrekte Lokalisierung, Feldüberprüfung, Bearbeitungsverhalten und Antwortverarbeitung.
* Mit den MSM Live Copies-Fehlerbehebungen können Autoren Änderungen zuverlässig von Blueprint-Seiten aus bereitstellen und die vorhandene Rollout-Konfiguration beibehalten.
* Crosswalk-Unterstützung ist auf Adobe Managed Services verfügbar, einschließlich der erforderlichen Bundles, Systembenutzenden und Konfiguration.
* Weitere Fehlerbehebungen betreffen die Admin- und klassischen Benutzeroberflächen, Kernkomponenten, die Komponentenkonsole, die Campaign-Integration, Experience Fragments und Launches.

Die übrigen Änderungen gelten für [!DNL Experience Manager Foundation]:

* Durch Lokalisierungsaktualisierungen wird bereits früher nur englischer Text in Konsistenzberichten, der Betriebskonsole und mehreren Authoring-Oberflächen übersetzt.
* Stabilitätskorrekturen stellen den Endpunkt für die Systemüberwachung wieder her, sorgen dafür, dass der E-Mail-Service nach zeitweise auftretenden Konfigurationsfehlern ausgeführt wird, und korrigieren die Bearbeitung von Workflow-Variablen und Workflow-Paketen.
* Die Version fügt außerdem die Unterstützung des AEM Context Service hinzu und löst Probleme mit der Sicherheit, Übersetzung und Benutzeroberfläche.

Die vollständige Liste finden Sie unter [Behobene Probleme in 6.5 LTS, Service Pack 3](#fixed-issues).


<!-- ## Key features and enhancements -->



<!-- UPDATE THE EACH RELEASE -->

## Es wurden Probleme in 6.5 LTS, Service Pack 3 behoben {#fixed-issues}

### [!DNL Sites]{#sites-65-LTS-SP3}

* AEM 6.5 LTS, Service Pack 3 enthält die Crosswalk-Bundles, das Inhaltspaket, Systembenutzer, Service-Benutzerzuordnungen, Funktions-Umschalter und die erforderliche OSGi-Konfiguration. Neuinstallationen liefern die Crosswalk-Voraussetzungen automatisch und erfordern nur eine kundenspezifische Laufzeitkonfiguration. (SITES-41596)
* AEM 6.5 LTS, Service Pack 3-Updates `cq-wcm-core` zur Unterstützung von Crosswalk auf Adobe Managed Services. Die Aktualisierung fügt die Vorlagenerstellung und den universellen Editor-Zugriff hinzu, während veralteter benutzerdefinierter Code und Feature-Umschalter entfernt werden. (SITES-37657)


#### Barrierefreiheit {#sites-accessibility-65-lts-sp3}

* Die Arbeitsfläche des Seiteneditors unterstützt jetzt die Komponentenverwaltung nur über die Tastatur. Autoren können Komponenten einfügen, ausschneiden, einfügen und löschen verwenden, um Komponenten hinzuzufügen, neu anzuordnen und zu entfernen. (SITES-25359) KRITISCH
* Tastaturbenutzer können jetzt Tabellenzeilen in der Sites-Listenansicht neu anordnen, ohne Drag-and-Drop-Gesten zu verwenden. Mit Tastatursteuerelementen können Benutzer eine Zeile auswählen, an eine andere Position verschieben und die Platzierung abschließen. (SITES-24946) KRITISCH

* Der Editor für benutzerdefinierte Eigenschaften unterstützt jetzt die Tastaturinteraktion mit seinen Formatierungssteuerelementen. Autoren können den Fokus zwischen Symbolleistenoptionen verschieben, einen Textstil auswählen und Eigenschaftswerte nur mit der Tastatur formatieren. (SITES-40333) WICHTIG

* Der Tastaturfokus überspringt jetzt die Komponentenliste des seitlichen Bedienfelds, wenn die verfügbare Interaktion Drag-and-Drop erfordert. Diese Änderung verhindert, dass Tastaturbenutzer in einen nicht verwendbaren Komponentenauswahl-Workflow eintreten. (SITES-40752)
* Durch Schließen einer Überlagerung wird der Fokus nun auf die auslösende Steuerung zurückgesetzt. Benutzer von Tastatur und Bildschirmlesehilfe kehren nicht mehr zur Überlagerung zurück oder verlieren ihre Position in der Benutzeroberfläche. (SITES-40819)
* Die Tastaturnavigation verschiebt den Fokus nicht mehr auf ausgeblendeten Seiteninhalt. Diese Änderung sorgt für eine vorhersehbare Fokussequenz und verhindert Navigationsstörungen. (SITES-41430)
* Die Schaltfläche „Sperren“ bietet jetzt basierend auf dem Titel eine präzise Rückmeldung der Bildschirmlesehilfe. Benutzer hören eine klare Aktionsbeschriftung anstelle einer langen Beschreibung. (SITES-41431)
* Ein visueller Indikator identifiziert nun die ausgewählte Option im Listenfeld Datei oder Ordner ändern . Die Anzeige hilft Benutzenden, den Breadcrumb-Pfad zu verstehen und den aktuellen Ordner zu erkennen. (SITES-25532)
* Die Sprachausgabe gibt jetzt einmal die aufsteigende oder absteigende Sortierrichtung aus. Eine beschreibende Beschriftung identifiziert die Schaltflächenaktion klar und entfernt doppeltes Feedback. (SITES-25534)
* AEM Sites bietet jetzt eine breitere Unterstützung der Barrierefreiheit in gängigen Authoring-Workflows. Aktualisierungen verbessern die Tastaturinteraktion, die Beschriftungen der Benutzeroberfläche, die Fokusverwaltung und das Feedback zur Hilfstechnologie. (SITES-38239)
* In Symbolleistenelementen werden jetzt sichtbare Beschriftungen angezeigt, wenn sie den Tastaturfokus erhalten. Tastaturbenutzer können jedes Steuerelement identifizieren, bevor sie es aktivieren. (SITES-40751)
* Benutzer von Tastatur und Bildschirmlesehilfe können jetzt das Menü „Posteingang“ verlassen, ohne es offen zu lassen. Das Menü wird automatisch geschlossen und behält einen klaren Navigationspfad bei. (SITES-25518)
* Farbfelder zeigen jetzt ein Symbol mit ausgewähltem Status mit ausreichendem Kontrast an. Der klarere Indikator hilft Benutzenden, das aktive Farb-/Bildmuster über verschiedene Hintergrundfarben hinweg zu erkennen. (SITES-25523)
* Die Symbolleiste Layout bearbeiten meldet jetzt das aktuelle Gerät genau an die Hilfstechnologie. Die Geräteschaltflächen bieten nicht mehr die Möglichkeit, dass Benutzende jede Schaltfläche ein- und ausschalten können. (SITES-25524)
* Das Suchmodal zeigt jetzt die Beschriftung **Sortieren nach** mit ausreichendem Textkontrast an. Der aktualisierte Stil verbessert die Lesbarkeit für Benutzende mit Sehschwäche. (SITES-25531)
* Die Sortierschaltflächen für die Sites-Listenansicht erfüllen jetzt die minimalen Kontrastanforderungen. Benutzende können jedes Sortiersteuerelement und dessen Status anhand des Tabellenhintergrunds leichter identifizieren. (SITES-25372)
* Die Assets-Liste der Seitenleiste wird nicht mehr neu geladen, wenn das Filterfeld den Tastaturfokus erhält. Benutzer können das Feld ohne unerwartete Inhaltsverschiebung oder wiederholte Ankündigungen zum Laden der Bildschirmlesehilfe betreten. (SITES-25377)
* Die Seitenleisten-Registerkarten für Inhaltsfragmente bieten jetzt konsistente barrierefreie Beschriftungen. NVDA gibt den Namen der Registerkarte aus, anstatt das ausgewählte Element der Unternavigation anzukündigen. (SITES-25509)
* Das Menü Hilfe wird nun geschlossen, wenn der Fokus der Tastatur oder Bildschirmlesehilfe sich außerhalb von ihr bewegt. Benutzer können weiterhin in Kopfzeilensteuerelementen oder Seiteninhalten navigieren, ohne das Menü geöffnet zu lassen. (SITES-25517)
* Text, der in die Felder der Demografie-Symbolleiste eingegeben wird, erfüllt jetzt die Kontrastanforderungen. Benutzerinnen und Benutzer können Profilwerte vor dem Hintergrund der Textfelder besser lesen. (SITES-25318)
* Das Menü Seiteninformationen zeigt jetzt fokussierte Optionen mit ausreichendem Textkontrast an. Der klarere Stil hilft Benutzern, den Tastaturfokus im gesamten Menü zu verfolgen. (SITES-25321)
* Kontrollkästchen in den Dialogfeldern „Teaser“, „Bild“ und „Karussell“ machen nun die zugehörigen Anweisungen für Bildschirmlesehilfen verfügbar. Benutzende hören die unterstützende Beschreibung, wenn der Tastaturfokus jedes Kontrollkästchen erreicht. (SITES-25364)
* Steuerelemente des Texteditors kommunizieren jetzt ihren aktuellen Status an Hilfstechnologien. Bildschirmlesehilfen identifizieren das aktive Absatzformat und die ausgewählte Hyperlink-Zieloption. (SITES-25367)
* Die Sprachausgabe gibt jetzt die Schaltfläche **Gerät drehen** und die aktuelle Geräteausrichtung klar aus. Beim Aktivieren des Steuerelements wird die neue Ausrichtung angezeigt, ohne dass ein Titel verwendet wird, der die entgegengesetzte Aktion beschreibt. (SITES-25292)
* Bei der Tastaturnavigation werden jetzt die in der reduzierten Symbolleiste „Demografie“ ausgeblendeten Steuerelemente übersprungen. Benutzer können durch die Layout-Vorschau navigieren, ohne auf nicht verfügbare Symbolleistenoptionen stoßen zu müssen. (SITES-25304)
* Textbeschriftungen in der Demografie-Symbolleiste erfüllen jetzt während der Layout-Vorschau die Mindestanforderungen an den Kontrast. Benutzende können Beschriftungen wie „Empfohlen“ vor dem Symbolleistenhintergrund besser lesen. (SITES-25307)
* In der Demografie-Symbolleiste werden jetzt Fokusindikatoren für Schaltflächen mit ausreichendem Kontrast angezeigt. Benutzende können die aktive Commerce-, Persona- oder Gerätesteuerung während der Tastaturnavigation identifizieren. (SITES-25308)
* Die Symbolleiste „Layout bearbeiten“ verwendet eine Anzeige für den gruppierten Fokus für den Geräteselektor. Die Gliederung enthält die zugehörigen Steuerelemente **Gerät auswählen** und **Gerät drehen** als Teil des beabsichtigten Symbolleistenverhaltens. (SITES-25283)
* Die Symbolleiste „Layout bearbeiten“ schneidet die Beschriftung **iPhone 8 Plus** nicht mehr ab, wenn Benutzende ein anderes Gerät auswählen. Der vollständige Gerätename bleibt für alle Schaltflächenstatus sichtbar. (SITES-25284)
* Das Layout-Lineal bearbeiten bietet jetzt für Bildschirmlesehilfen Messkontext. Benutzer hören ein beschreibendes Etikett und das Messformat anstelle einer unerklärten Zahlenreihe. (SITES-25287)
* In der Symbolleiste Layout bearbeiten ist jetzt die Schaltfläche **Desktop** hervorgehoben, wenn die Desktop-Ansicht aktiv ist. Die optische Anzeige macht die aktuelle Geräteauswahl übersichtlich. (SITES-25290)
* Der Tastaturfokus bleibt jetzt auf der Musterschaltfläche für alle verfügbaren Farben sichtbar. Durch den hinzugefügten Abstand wird verhindert, dass der Fokusindikator an das ausgewählte Farb-/Bildmuster angepasst wird. (SITES-25253)
* Die Sprachausgabe erkennt das Timewarp-Datumsfeld jetzt korrekt. Das Feld bietet keine irreführende Rückmeldung mehr, die darauf hindeutet, dass ein Dialogfeld geöffnet wird. (SITES-25263)
* Die Beschriftung der Schaltfläche „Anmerkung“ erfüllt jetzt die minimalen Kontrastanforderungen im Standard- und Hover-Status. Benutzende können die Beschriftung deutlich vor dem Hintergrund der Schaltfläche lesen. (SITES-25267)
* Die Sprachausgabe gibt jetzt aussagekräftige Bezeichnungen für Steuerelemente im Dialogfeld Anmerkung aus. Jede Schaltfläche kommuniziert ihre Aktion ohne unnötiges Anmerkungspräfix. (SITES-25277)
* Die Schaltfläche Bearbeiten in der Assets-Seitenleiste bietet jetzt ein größeres Touch-Ziel. Benutzer können das Steuerelement zuverlässiger aktivieren, ohne ein nahegelegenes Element auszuwählen. (SITES-25221)
* Der Seiteneditor verwendet jetzt eine logische Überschriftenhierarchie. Bildschirmlesehilfen identifizieren den Seitentitel als primäre Überschrift und Seitenleisten-Titel als untergeordnete Überschriften. (SITES-25222)
* Das Dialogfeld Anmerkung stellt nun seinen Titel als semantische Überschrift bereit. Benutzende von Bildschirmlesehilfen können den Titel identifizieren und durch Überschriftenbefehle in der Dialogfeldstruktur navigieren. (SITES-25248)
* Benutzende, die eine Bildschirmlesehilfe nutzen, erhalten jetzt Feedback, wenn sie die Liste Neue Komponente einfügen filtern. Im Suchfeld wird das Filterverhalten beschrieben, und eine Statusmeldung meldet die Anzahl der Ergebnisse. (SITES-25251)
* Das Bedienfeld „Seitliche Leistenkomponenten“ verwendet jetzt semantisches Listen-Markup. Bildschirmlesehilfen können die Elementanzahl ausgeben und eine effiziente Listennavigation unterstützen. (SITES-25214)
* Info-Schaltflächen verwenden jetzt größere Symbole im Bedienfeld „Komponenten“. Benutzer können jedes Steuerelement leichter finden und erkennen. (SITES-25217)
* Komponententitel bleiben jetzt sichtbar, wenn Benutzer den Textabstand vergrößern. Lange Titel werden umgebrochen, anstatt nahegelegene Inhalte zu kürzen oder zu überlappen. (SITES-25219)
* Die Schaltfläche **Bearbeiten** in der Assets-Seitenleiste zeigt jetzt an, dass eine neue Browser-Registerkarte geöffnet wird. Visuelle Hinweise und Hinweise für Bildschirmlesehilfen bereiten Benutzer vor der Navigation vor. (SITES-25220)
* Im Anmerkungsmodus wird jetzt der Tastaturfokus auf der Anmerkungssymbolleiste platziert, wenn die Symbolleiste geöffnet wird. Benutzer von Tastatur und Bildschirmlesehilfe können die Steuerelemente in einer logischen Reihenfolge durchlaufen, ohne rückwärts von der Schaltfläche **Schließen** zu navigieren. (SITES-24996)
* Die Auswahlschaltflächen für die Felder Pfad und Tags verwenden kein Kontrollkästchensymbol mehr. Das aktualisierte Symbol zeigt an, dass das Steuerelement ein Auswahldialogfeld öffnet, anstatt einen aktivierten Status zu ändern. (SITES-25210)
* Das Feld Filter im Bedienfeld Komponenten der Seitenleiste verfügt jetzt über eine gültige barrierefreie Beschriftung. Die Sprachausgabe gibt den Zweck des Felds an, anstatt sich auf ein Symbol oder einen Platzhaltertext zu verlassen. (SITES-25212)
* Die Assets-Seitenleiste blendet jetzt dekorative Miniaturansichten aus Bildschirmlesehilfen aus. Benutzende hören den Asset-Namen nicht mehr zweimal, wenn sie durch das Asset-Raster navigieren. (SITES-25213)
* Akkordeon-Schaltflächen in der Leiste Filter zeigen jetzt Fokusindikatoren mit ausreichendem Kontrast an. Tastaturbenutzer können den Fokus beim Navigieren in Filterkategorien verfolgen. (SITES-24986)
* Die Leiste „Filter“ zeigt jetzt einen klaren Tastaturfokus um Optionsfelder an. Ein erhöhter Kontrast hilft Benutzenden, ihre Position über Filteroptionen hinweg zu verfolgen. (SITES-24987)
* Das Laden von Statusmeldungen auf der Seite „Filter“ erfüllt jetzt die Mindestanforderungen an den Textkontrast. Benutzer können beim Wechseln zwischen Karten- und Listenansicht das Fortschrittsfeedback lesen. (SITES-24991)
* Der Seitentitel auf der Arbeitsfläche des Editors verwendet jetzt semantisches Überschriften-Markup. Hilfstechnologien können den Titel ankündigen und in die Navigation für Überschriften einschließen. (SITES-24993)
* Durch Erweitern des Emulator-Menüs wird der Tastaturfokus jetzt auf das erste Menüelement verschoben. Durch das Reduzieren des Menüs bleibt der Fokus auf der logischen sekundären Symbolleistensequenz. (SITES-24954)
* Der Text in der Live View-Tabelle erfüllt nun die Kontrastanforderungen. Benutzer können Live Copy-Details beim normalen Status und beim Bewegen des Mauszeigers deutlich lesen. (SITES-24956)
* Die Leiste „Verweise“ verwendet jetzt für ihren Titel semantisches Überschriften-Markup. Die Sprachausgabe gibt die Überschrift beim ersten Laden und beim Durchsuchen von Ordnern aus. (SITES-24967)
* Kartenlinks beschreiben nun ihre Ziele klar. Benutzende von Bildschirmlesehilfen können jeden Link identifizieren, ohne die vollständigen Metadaten der Karte zu hören. (SITES-24975)
* Schaltflächen im Kopfzeilenmenü teilen Sprachausgaben nicht mehr mit, dass Dialogfelder geöffnet werden. Die Sprachausgabe gibt stattdessen den erweiterten oder reduzierten Status jeder Schaltfläche aus, wodurch das Menüverhalten genau beschrieben wird. (SITES-24742)
* Text auf der Schaltfläche Löschen bietet nun einen ausreichenden Kontrast zu seinem roten Hintergrund. Benutzer können die Aktion leichter identifizieren, bevor sie den Löschvorgang bestätigen. (SITES-24772)
* Arbeitsflächenkarten legen keine separaten Bild- und Überschriftenlinks mehr offen, die zum selben Ziel führen. Durch einen einzigen Link werden doppelte Tastaturstopps und wiederholte Ankündigungen der Sprachausgabe reduziert. (SITES-24947)
* Die Listenansicht zeigt jetzt die Drag-and-Drop-Schaltfläche mit größerer visueller Hervorhebung an. Aktualisierte Symbolgröße, -stärke und -kontrast erleichtern die Suche und Verwendung des Steuerelements. (SITES-24951)
* Kopfzeilen-Schaltflächen bieten jetzt knappe barrierefreie Namen: Suche, Apps, Hilfe, Posteingang und Benutzer. Die Sprachausgabe gibt bei der Tastaturnavigation keine redundanten Begriffe wie „klickbar“ oder „Grafik“ mehr aus. (SITES-24715)
* Links in der App-Navigation weisen jetzt eine stärkere visuelle Hervorhebung auf. Erhöhte Textgröße und -stärke verbessern die Lesbarkeit für Benutzende mit Sehschwäche oder Farbunterschieden. (SITES-24723)
* Für Posteingangslinks wird jetzt semantisches Listen-Markup verwendet. Bildschirmlesehilfen können die Links als verwandte Gruppe identifizieren, die Elementanzahl ausgeben und eine effizientere Navigation unterstützen. (SITES-24730)
* QuickInfo-Steuerelemente im Dialogfeld Benutzereinstellungen zeigen jetzt beschreibende barrierefreie Namen an. Bildschirmlesehilfen geben den Zweck jedes Steuerelements an, anstatt vor dem Lesen des QuickInfo-Inhalts „leer“ zu sagen. (SITES-24732)
* Jedes Wahrzeichen der Filterleiste enthält jetzt eine eindeutige barrierefreie Beschriftung. Bildschirmlesehilfen können die Filterleiste von anderen Seitenbereichen unterscheiden und sie während der Navigation identifizieren. (SITES-24686)
* Editor-Dialogfelder trennen jetzt die Schaltflächen Hilfe und Vollbild ein/aus vom Überschriftenelement. Bildschirmlesehilfen identifizieren diese interaktiven Steuerelemente genau und geben sie nicht mehr als Überschriften an. (SITES-24696)
* Die Schaltfläche CSV-Bericht warnt Benutzende jetzt, bevor eine neue Browser-Registerkarte geöffnet wird. Die barrierefreie Kennzeichnung informiert Sprachausgaben und Tastaturbenutzer vor der Aktivierung über das Verhalten. (SITES-24704)
* Die Filterleiste lädt jetzt Beschriftungen für gespeicherte Suchen und wählt Suchordner einheitlich aus. Mit der Schaltfläche Filter werden keine Beschriftungselemente mehr während Fokus-, Tastatur- oder Mausinteraktionen eingefügt. (SITES-24706)
* Die Schaltflächen „Standort schließen“ und „Standort entfernen“ bieten jetzt größere Touch-Ziele. Benutzer können beide Steuerelemente zuverlässiger aktivieren, ohne benachbarte Elemente auszuwählen. (SITES-24530)
* Die Schaltfläche Standort entfernen und ihre Fokusanzeige erfüllen jetzt die minimalen Kontrastanforderungen. Ein stärkerer Kontrast hilft Benutzenden, das Steuerelement zu identifizieren und den Tastaturfokus zu verfolgen. (SITES-24531)
* Editor-iFrames enthalten jetzt beschreibende Titel auf der Arbeitsfläche, Seitenleisten, Komponentendialogfelder und Layout-Vorschauen. Bildschirmlesehilfen können jeden Frame identifizieren, wenn der Fokus darauf eingeht. (SITES-24650)
* Der verbesserte Textkontrast erleichtert die Lesbarkeit der Meldungen in der Verweisleiste. Durch die Änderung werden Eingabeaufforderungen verdeutlicht, die eine Auswahl oder einen Bericht mit nicht verfügbaren Verweisen anfordern. (SITES-24666)
* Das Bedienfeld Komponenten bietet für jedes Informationssymbol eine aussagekräftige, barrierefreie Beschriftung. Bildschirmlesehilfen identifizieren das Steuerelement, das eine Komponentenbeschreibung anzeigt. (SITES-24500)
* Der Tastaturfokus umgibt jetzt die gesamte Schaltfläche Beschreibung anzeigen für die Autorenzeile. Der sichtbare Umriss hilft Benutzern, ihre Position zu verfolgen und die Aktivierung eines anderen Steuerelements zu vermeiden. (SITES-24503)
* Das Dialogfeld Teaser-Komponente zeigt die Schaltflächen Hilfe und Umschalten im Vollbildmodus nicht mehr als Überschriften an. Bildschirmlesehilfen geben beide Steuerelemente als Schaltflächen an und behalten die korrekte Überschriftenstruktur bei. (SITES-24525)
* Das Adobe Experience Manager-Header-Steuerelement meldet den erweiterten oder reduzierten Status korrekt. Das Steuerelement öffnet und schließt den Navigationsinhalt, sodass die Sprachausgabe gültige Statusinformationen erhält. (SITES-24528)
* Filterergebnisse kennzeichnen Globussymbole als dekorativ und entfernen ihre barrierefreien Namen. Bildschirmlesehilfen ignorieren die Symbole, anstatt irreführende Beschreibungen anzukündigen. (SITES-3057)
* Im Dialogfeld „Zeitsprung“ werden jetzt Zeiteingabefehler mit dem entsprechenden Feld Stunden oder Minuten verknüpft. Die Sprachausgabe gibt das betroffene Feld zusammen mit der Validierungsmeldung aus. (SITES-10980)
* Das ausgewählte Inhaltsstrukturelement wird nicht mehr Teil der Beschriftung Datei ändern oder Ordnersteuerelement. Bildschirmlesehilfen hören einen klaren Steuerelementnamen ohne zusätzlichen Statustext. (SITES-24496)
* Orientierungspunkte für Regionen in der Assets-Seitenleiste zeigen jetzt unterschiedliche barrierefreie Namen an. Benutzende von Bildschirmlesehilfen können jede Region eindeutig identifizieren und darin navigieren. (SITES-24497)
* Die Sprachausgabe ignoriert jetzt die dekorativen Hilfesymbole und Vollbildsymbole im Karusselldialogfeld. Die Tastaturnavigation Trigger keine unnötigen Symbolankündigungen mehr. (SITES-2912)
* Die Sprachausgabe überspringt jetzt dekorative Symbolleistensymbole im Teaser-Dialogfeld. Die Steuerelemente Hilfe, Vollbild, Formatierung und Link erzeugen keine redundanten Ankündigungen mehr. (SITES-2934)


#### Admin-Benutzeroberfläche{#sites-adminui-65-lts-sp3}

* Mit AEM können Mitglieder der Administratorgruppe jetzt Seiten entsperren und Benutzende verkörpern. Gruppenmitglieder können über ihren vorhandenen Zugriff beide Verwaltungsaufgaben ausführen. (SITES-14732)
* Die Admin-Ansicht von Assets aktualisiert jetzt eine Asset-Karte, nachdem **Autoren in der Zeitleiste auf „Auf diese Version**&quot; geklickt haben. Die Miniaturansicht zeigt die wiederhergestellte Version sofort an und zeigt keinen veralteten Vorschauinhalt mehr an. (SITES-46590)


#### Klassische Benutzeroberfläche{#sites-classicui-65-lts-sp3}

Die Eigenschaften der indonesischen Sprachkopie zeigen den richtigen ID-Sprachcode an. Die Leiste Verweise ersetzt NICHT mehr IN, wenn Autoren eine indonesische Sprachkopie erstellen oder überprüfen. (SITES-44918)


#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp3}

Die Assets-Konsole reagiert jetzt, wenn Benutzende Suchfilter anwenden. Beim Ändern eines Filters des Inhaltsfragmentmodells werden die Ergebnisse aktualisiert, anstatt die aktuelle Asset-Liste unverändert zu lassen. (SITES-38686) WICHTIG


#### [!DNL Content Fragments] – Admin{#sites-admin-65-lts-sp3}

* Die Assets-Seite lokalisiert jetzt die QuickInfo für ein gesperrtes Inhaltsfragment. Benutzer sehen die übersetzte Beschriftung **Ausgecheckt von**, wenn sie den Mauszeiger über die Sperranzeige bewegen. (SITES-42531) WICHTIG

* AEM lokalisiert den ungültigen Namen, der bei der Erstellung des Inhaltsfragments als Überprüfungsmeldung angegeben wurde. Nicht unterstützte Titelzeichen enthalten keinen Trigger mehr zwischen englischem Text und nicht-englischen Benutzeroberflächen. (SITES-19796)
* AEM übersetzt die Zeichenfolge der Inhaltsfragmentmodelle bei der Erstellung von Inhaltsfragmenten. Auf der Assets-Benutzeroberfläche wird für diese Beschriftung in lokalisierten Umgebungen kein englischer Text mehr angezeigt. (SITES-22336)
* Inhaltsfragment-Services verlassen sich nicht mehr auf die veraltete Umschalter-Logik für Funktionen. Die optimierte Implementierung entfernt toggle-abhängige Verzweigungen und sorgt für ein konsistentes Service Pack-Verhalten. (SITES-38688)
* AEM übersetzt die Option Später während der geplanten Veröffentlichung von Inhaltsfragmenten. Der Veröffentlichungs-Workflow entspricht der Sprache der aktiven Benutzeroberfläche. (SITES-42532)
* AEM übersetzt die Hauptzeichenfolge im Dialogfeld zum Herunterladen von Inhaltsfragmenten. Der Abschnitt Elemente entspricht der Sprache der aktiven Benutzeroberfläche. (SITES-42534)


#### [!DNL Content Fragments] - Fragment-Editor{#sites-fragments-editor-65-lts-sp3}

* Der Inhaltsfragment-Editor positioniert die Dropdown-Menüs im Rich-Text-Editor jetzt korrekt. Jedes Menü bleibt mit seinem Symbolleistensteuerelement ausgerichtet und die angrenzenden Formatierungssteuerelemente bleiben sichtbar. (SITES-44005) KRITISCH

* Die Schaltfläche Inhaltsfragment bearbeiten wird jetzt angezeigt und funktioniert sofort für Multifield-Referenzeinträge. Autoren müssen das übergeordnete Inhaltsfragment nicht mehr speichern, schließen und erneut öffnen, bevor sie ein eingebettetes Fragment bearbeiten können. (SITES-43733) WICHTIG

* Der Inhaltsfragment-Editor zeigt einen Fokusumriss an, wenn Autoren ein mehrzeiliges Textfeld auswählen. Der Umriss dupliziert nicht mehr Steuerelemente in der Nähe oder überschneidet sie. (SITES-39253)
* Bei der Erstellung von Inhaltsfragmenten wird CJK-Platzhaltertext ohne kursiven Stil angezeigt. Japanisch, Koreanisch, Chinesisch (vereinfacht) und Chinesisch (traditionell) haben ihre ursprüngliche Form beibehalten. (SITES-43548)
* Der Inhaltsfragment-Editor aktualisiert das Statusbanner, nachdem Autoren ein Fragment gespeichert oder veröffentlicht haben. Autoren können den Status Geändert, Gespeichert oder Veröffentlicht bestätigen, ohne die Browser-Registerkarte neu laden zu müssen. (SITES-45897)
* Der Inhaltsfragment-Editor validiert Felder konsistent nach Änderungen an der Granite-Benutzeroberfläche. Aktualisierte Client-Bibliotheken stellen das erwartete Validierungsverhalten wieder her. (SITES-46650)


#### [!DNL Content Fragments] – GraphQL-API {#sites-graphql-api-65-lts-sp3}

* GraphQL-JSON-Antworten enthalten jetzt eingebettete Bildverweise, wenn DAM-Dateinamen Leerzeichen oder Nicht-ASCII-Zeichen enthalten. Client-Programme können diese Bilder abrufen und rendern, ohne die Assets umzubenennen. (SITES-42191) WICHTIG
* Die GraphQL-API für Inhaltsfragmente enthält jetzt mehrere Aktualisierungen der Abfrageverarbeitung und Antwortverarbeitung. Die Änderungen verhindern doppelte Cache-Kopfzeilen und -Werte, verbessern die Codierung, bewahren Statusinformationen über persistierte Abfragen auf, behandeln leere Kopfzeilen und geben geeignete Endpunktfehler zurück. (SITES-40159) WICHTIG
* Das PersistedQueryServlet verarbeitet jetzt kodierte Variablen in gültigen persistierten GraphQL-Abfragen, ohne Fehler oder Warnungen aufzuzeichnen. Abfragen geben weiterhin erfolgreiche Antworten zurück, während die Protokolle ihren tatsächlichen Ausführungsstatus widerspiegeln. (SITES-39354) WICHTIG

* Beim Neuladen der Seite &quot;GraphQL-Endpunkte“ bleibt die lokalisierte Nachricht mit leerem Status erhalten. Die Seite wird nicht mehr auf Englisch zurückgesetzt, wenn keine Endpunkte vorhanden sind. (SITES-43586)


<!--#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-65-lts-sp3}-->


#### [!DNL Content Fragments] – Modell-Editor{#sites-model-editor-65-lts-sp3}

* Die Inhaltsfragmentmodelle -Konsole zeigt jetzt hochgeladene Miniaturansichten für Konfigurationen an, deren Namen lokalisierte Zeichen enthalten. Autoren verlieren keine Miniaturansichten mehr, wenn Konfigurationsnamen nicht-englischen Text verwenden. (SITES-39242) WICHTIG

* Der Inhaltsfragmentmodell-Editor zeigt lokalisierten Text **Feldbezeichnung** an, sobald Autoren eine Komponente zur Arbeitsfläche hinzufügen. Autoren müssen das Modell nicht mehr speichern und erneut öffnen, um die Übersetzung anzuzeigen. (SITES-45383)
* Der Inhaltsfragmentmodell-Editor lokalisiert die Validierungsmeldung, die angezeigt wird, wenn Autoren einen ungültigen Modelltyp für eine zusammengesetzte Komponente auswählen. Die Meldung stimmt nun mit dem aktiven Gebietsschema überein, anstatt nur in Englisch angezeigt zu werden. (SITES-41117)
* Der Inhaltsfragmentmodell-Editor lokalisiert den gesamten Text im Dialogfeld Modell ist gesperrt . Im Dialogfeld werden englische Schaltflächenbeschriftungen und Anweisungen nicht mehr mit übersetztem Benutzeroberflächentext gemischt. (SITES-28592)



#### [!DNL Content Fragments] – REST-API{#sites-restapi-65-lts-sp3}

Das Bundle mit der REST-API für Headless-Inhaltsfragmente entfernt veraltete Funktionsumschalter und den zugehörigen bedingten Code. Das unterstützte API-Verhalten bleibt unverändert, während das Bundle nur die für aktive Funktionen erforderlichen Umschalter beibehält. (SITES-39113)



#### Komponentenkonsole{#sites-component-console-65-lts-sp3}

Der Content Finder listet jetzt Assets auf, deren Namen nicht kodierbare Zeichen enthalten, ohne dass Fehler auftreten oder Ausnahmen generiert werden. Auf der Seite „Live-Nutzung der Komponenten“ werden auch große Ergebnismengen kontinuierlich geladen, ohne dass beim Scrollen leere Zeilen angezeigt werden. (SITES-44672) WICHTIG

<!--
#### Content API{#sites-content-api-65-lts-sp3}

#### Core backend{#sites-core-backend-65-lts-sp3}
-->

#### Kernkomponenten{#sites-core-components-65-lts-sp3}

* Mehrfeld-Komponenten speichern jetzt für jeden Eintrag eine separate Remote-Asset-Auswahl. Autoren können Remote-Bilder auswählen, ändern und speichern, ohne ein Bild über jedes Mehrfachfeld-Element hinweg zu duplizieren. (SITES-42376) WICHTIG
* „ThumbnailServlet“ stoppt jetzt die Verarbeitung, nachdem es eine Anforderung für eine fehlende Ressource umleitet. Durch diese Änderung werden wiederholte Nullzeiger-Ausnahmen und übermäßige Fehlerprotokollierung beim DAM- und Konsolenbrowsen verhindert. (SITES-41238) WICHTIG


#### Campaign-Integration{#sites-campaign-integration-65-lts-sp3}

Das Content-Servlet von Campaign behält jetzt den Content-Typ der JSON-Antwort bei Inhaltsanfragen bei. Durch diese Änderung werden die wiederholten `WARN`- und `ERROR`-Protokolleinträge gestoppt, die nach einem Upgrade von AEM 6.5.24 aufgetreten sind. (SITES-46902) WICHTIG


#### Experience Fragments{#sites-experiencefragments-65-lts-sp3}

Autoren können jetzt mehr als 40 Vorlagen durchsuchen, während sie eine Experience Fragment-Variante erstellen. Jede zusätzliche Seite behält den ursprünglichen Ordnerfilter bei und zeigt die nächsten übereinstimmenden Vorlagen an. (SITES-41531) WICHTIG


<!-- #### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp3} -->


#### Launches{#sites-launches-65-lts-sp3}

Der Launch-Promotion-Verlauf zeigt jetzt lokalisierten Text in der Sites-Zeitleiste an. Die Zeitleiste übersetzt die Nachrichten „Erstellte Version von“ und „Vor dem Hochstufen des Launches“ in unterstützte Gebietsschemata. (SITES-13389)


<!-- #### Link Checker{#sites-link-checker-65-lts-sp3} -->



#### MSM – Live Copies{#sites-msm-live-copies-65-lts-sp3}

* Inhaltsfragment-Live Copy-Ordner behalten jetzt cq:rolloutConfigs bei, wenn Autoren unveränderte Eigenschaften speichern. Autoren können die Rollout-Einstellungen später aktualisieren, ohne die vorhandene Konfiguration zu verlieren. (SITES-43729) KRITISCH

* Autoren können jetzt über die bearbeitbare Symbolleiste Komponentenänderungen auf einer Blueprint-Seite einführen. Der Rollout wird ohne JavaScript-Fehler abgeschlossen und die Änderungen werden an die Live Copy übertragen. (SITES-46052) WICHTIG
* Autoren können jetzt nach einem Upgrade MSM-Rollouts von Blueprint-Seiten abschließen. Das Dialogfeld „Rollout“ lädt die verfügbaren Live Copies und aktiviert ihre Rollout-Steuerelemente, anstatt im permanenten Ladezustand zu bleiben. (SITES-43116) WICHTIG

* Die Live Copy-Übersicht wendet jetzt lokalisierte Datumsformate im gesamten Beziehungsstatus an. Die Felder **Live Copy Source Zuletzt geändert**, **Live Copy Zuletzt geändert** und **Zuletzt ausgerollt** entsprechen dem Gebietsschema des Benutzers. (SITES-40756)
* Wenn Sie einen übergeordneten Blueprint und dessen untergeordnete Seiten in einer Anfrage deaktivieren, wird jetzt pro Pfad ein Rollout-Ereignis erzeugt. Der Rollout-Manager führt keine doppelten Aktionen mehr für dieselbe untergeordnete Seite aus. (SITES-44987)


#### Seiteneditor{#sites-pageeditor-65-lts-sp3}

* Autoren können jetzt während des Speicherns der Seiteneigenschaften Tags mit Großbuchstaben oder Leerzeichen erstellen und anwenden. AEM speichert den normalisierten Tag-Wert sofort und behält die Seitenzuweisung bei. (SITES-42550) KRITISCH

* Beim Scrollen durch das Stilmenü wird die Hervorhebung aus dem ausgewählten Stil nicht mehr entfernt. Autoren können ihre aktuelle Auswahl bestätigen, während sie andere verfügbare Optionen überprüfen. (SITES-30874) WICHTIG

* Die Schaltfläche Rich-Text-Editor-Link wird jetzt geöffnet, wenn Autorinnen und Autoren über HTTP auf AEM zugreifen. Bei der Link-Erstellung tritt kein `crypto.randomUUID` mehr auf. (SITES-39467)
* Autoren können jetzt konfigurierte Inhaltsfragmentkomponenten kopieren und in leere Layout-Container einfügen. Die eingefügte Komponente behält ihren ursprünglichen Inhaltsfragmentverweis bei und zeigt den Fehler *Erlebnisvariante auswählen* nicht mehr an. (SITES-41586)
* Der Bildeditor berücksichtigt jetzt benutzerdefinierte Zuschnittverhältnisse bei der hybriden Inline-Bearbeitung. Jedes Bild-Ablageziel verwendet eine eigene Konfiguration, sodass die Zuschnittsauswahl außerhalb des Vollbildmodus korrekt angewendet wird. (SITES-45771)

<!--
#### Replication{#sites-replication-65-lts-sp3}

#### Rich Text Editor{#sites-rte-65-lts-sp3}

#### Template Editor{#sites-template-editor-65-lts-sp3}

#### Universal editor {#sites-universal-editor-65-lts-sp3}

### [!DNL Assets]{#assets-65-lts-sp3}

#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp3}

#### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp3}
-->



<!--
### [!DNL Forms]{#forms-65-lts-sp3}
-->



### Fundament {#foundation-65-lts-sp3}

#### AEM Context Service {#foundation-aem-context-service-65-lts-sp3}

AEM 6.5 LTS führt die Unterstützung des AEM Context Service ein. Mit dem Rollout werden Service-APIs, Agentenintegration, AMS-Bereitstellung, Experience Cloud-Integration, Produktionsüberwachung, operative Runbooks und Nutzungsberichte hinzugefügt. (GRANITE-65148)

#### Apache Felix {#foundation-apachefelix-65-lts-sp3}

Der AEM-E-Mail-Service sendet jetzt weiterhin E-Mails, wenn gelegentlich Konfigurationsfehler auftreten. Administratoren müssen das Day Communique 5 Mailer Bundle nicht mehr neu starten, um den E-Mail-Versand wiederherzustellen. (GRANITE-66817) MAJOR

<!--
#### Campaign{#foundation-campaign-65-lts-sp3}

#### Cloud Services{#foundation-cloudservices-65-lts-sp3}

#### Communities {#foundation-communities-65-lts-sp3}

#### Content distribution{#foundation-content-distribution-65-lts-sp3}

#### CRX {#foundation-crx-65-lts-sp3}

#### Granite{#foundation-granite-65-lts-sp3}

#### HTL{#foundation-htl-5-lts-sp3}

#### Integrations{#foundation-integrations-65-lts-sp3}

#### Jetty{#foundation-jetty-65-lts-sp3}
-->

#### Lokalisierung{#foundation-localization-65-lts-sp3}

* Die Betriebskonsole lokalisiert jetzt nicht übersetzten Text in Konsistenzberichten. Benutzer können übersetzte Statusmeldungen, Warnungen, Wartungsergebnisse und Leistungsinformationen anzeigen. (NPR-44280) SCHWERWIEGEND

* Die Wartungsaufgabe Auditprotokoll zeigt jetzt einen lokalisierten Haftungsausschluss an. Admins sehen die Compliance und rechtlichen Hinweise in der von ihnen gewählten Sprache, bevor sie die automatische Bereinigung der Auditprotokolle konfigurieren. (NPR-44188)
* Auf der Seite „Benutzer bearbeiten“ wird jetzt ein lokalisierter Fehler angezeigt, wenn Benutzer geänderte Profile neu anordnen. In der Meldung wird klar erläutert, dass geänderte Profile erst verschoben werden können, wenn Benutzer ihre Änderungen speichern. (NPR-44282)
* AEM lokalisiert jetzt QuickInfos in allen Eigenschaften der Inhaltsfragmentliste. Die übersetzten Anleitungen erläutern die Modellauswahl, Tag-Filter, Inhaltspfade, Elementbeschränkungen und Sortiereinstellungen. (SITES-14969)
* Mithilfe von Komponenten-Links im Vorlageneditor kann jetzt die lokalisierte Dokumentation geöffnet werden. Autoren erhalten Anleitungen, die ihrer ausgewählten Sprache entsprechen, anstatt nur englischsprachige Komponentenseiten zu verwenden. (SITES-15058)
* Der Komponentenrichtlinien-Editor lokalisiert jetzt Fehler, die eine unveränderliche Ressource oder eine fehlgeschlagene Knotenerstellung melden. Vorlagenautoren erhalten diese Nachrichten in der ausgewählten Sprache. (SITES-17475)

<!-- #### Omnisearch{#foundation-omnisearch-65-lts-sp3} -->

#### Vorgangs-Dashboard{#foundation-operations-dashboard-65-lts-sp3}

Der `/system/health/systemalive.json`-Endpunkt bleibt jetzt verfügbar, nachdem Kunden ein Upgrade von AEM LTS durchgeführt haben. Eine korrigierte Servlet-Kontextkonfiguration verhindert HTTP 404-Antworten und unterstützt Systemüberwachungssysteme, die auf dem Endpunkt basieren. (GRANITE-69457) KRITISCH

#### Plattform{#foundation-platform-65-lts-sp3}

Die standardmäßige HTL-Ausdrucksoptionen-Zulassungsliste erkennt jetzt `decorationTagName` und `cssClassName`. Das Rendern des standardmäßigen responsiven Rasters füllt `error.log` nicht mehr mit wiederholten Warnungen für unbekannte Optionen. (GRANITE-67152)

<!--
#### Projects{#foundation-projects-65-lts-sp3}

#### Oak {#foundation-oak-65-lts-sp3}

#### Quickstart{#foundation-quickstart-65-lts-sp3} 
-->


#### Sicherheit{#foundation-security-65-lts-sp3}

Die **Gruppe kopieren** Aktion öffnet jetzt das erwartete Formular, anstatt eine leere Seite anzuzeigen. Administratoren können eine neue Gruppen-ID und Beschreibung eingeben und dann eine vorhandene Sicherheitsgruppe duplizieren. (NPR-44302) SCHWERWIEGEND


<!-- #### Sling{#foundation-sling-65-lts-sp3} -->


#### Übersetzung{#foundation-translation-65-lts-sp3}

Übersetzungsprojekte behalten jetzt den genauen Status während des Workflows bei. Die Erstellung von Launches und die Statusübertragung folgen dem erwarteten Workflow-Verhalten, wodurch inkonsistente Projektmetadaten entfernt werden. (NPR-43420)


#### Benutzeroberfläche{#foundation-ui-65-lts-sp3}

* Die Bezeichnung Land/Region wird jetzt in der ausgewählten Sprache der Benutzeroberfläche angezeigt. Lokalisierte Schnittstellen zeigen die englische Beschriftung nicht mehr an. (NPR-43883)
* Wenn Sie eine gleichrangige Seite auswählen, wird **Auswählen** in der Pfadauswahl für zusammengesetzte Mehrfachfelder aktiviert. Autoren können den neuen Pfad bestätigen, ohne das Browser-Fenster zu vergrößern oder die Auswahl zu wiederholen. (GRANITE-69323)


<!-- #### WCM{#foundation-wcm-65-lts-sp3} -->


#### Workflow{#foundation-workflow-65-lts-sp3}

* Workflow-Paketseiten unterstützen jetzt die Komponenten Inhaltsstruktur und bearbeitbare Ressourcendefinition im Seiteneditor für die Touch-optimierte Benutzeroberfläche. Autorinnen und Autoren können ohne die klassische Benutzeroberfläche durch Paketinhalte navigieren und die Komponenten überprüfen oder aktualisieren. (GRANITE-67348) MAJOR
* Der Seiteneditor der Touch-optimierten Benutzeroberfläche rendert jetzt die Inhaltsstruktur für Workflow-Paketseiten. Autoren können über denselben Editor die Paketstruktur überprüfen und Ressourcendefinitionskomponenten bearbeiten. (GRANITE-67186) MAJOR

* Das Dialogfeld „Workflow-Variable“ zeigt jetzt die richtigen Steuerelemente für Formulardatenmodell-, JSON-, XML- und Dokumentvariablen an. Autorinnen und Autoren sehen beim Erstellen dieser nicht primitiven Variablen kein unformatiertes HTML-Markup mehr. (GRANITE-67915)



## Info [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Die Plattform von [!DNL Adobe Experience Manager] 6.5 LTS basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java™ Content-Repository Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x wird als Servlet-Engine für den Schnellstart verwendet.

### Java™-Unterstützung  {#java-support}

* Unterstützung für Java™ 17 und Java™ 21.
* Um eine optimale Leistung zu erzielen, überschreiben Sie die GC-Standardwerte mit anderen Werten. Weitere Informationen finden Sie im Abschnitt [Installieren und Aktualisieren](/help/sites-deploying/custom-standalone-install.md).
* Adobe verteilt Wartungs-Updates für Java™ 17 und Java™ 21 für die Verwendung durch Kunden in AEM-bezogenen Projekten, sofern diese nicht über Oracle öffentlich verfügbar sind.

### Uber-JAR-Verpackung {#uber-jar-packaging}

UberJar für AEM 6.5 LTS SP3 verwendet AEM 6.5 LTS UberJar 6.6.3. Sie können die entsprechenden UberJar-Artefakte aus dem Repository von Maven Central abrufen. Im Gegensatz zu AEM 6.5 unterteilt AEM 6.5 LTS öffentliche APIs und veraltete APIs in zwei verschiedene Artefakte.

Verwenden Sie Folgendes, um mit den öffentlichen APIs zu kompilieren:

    „xml
    &lt;dependence>
    &lt;groupId>com.adobe.aem&lt;/groupId>
    &lt;artifactId>uber-jar&lt;/artifactId>
    &lt;version>6.6.3&lt;/version>
    &lt;classifier>apis&lt;/classifier>
    &lt;scope>Bereitgestellter&lt;/scope>
    &lt;/dependence>
    &quot;

Wenn Ihr Code auch von veralteten APIs abhängig ist, fügen Sie Folgendes hinzu:

    „xml
    &lt;dependence>
    &lt;groupId>com.adobe.aem&lt;/groupId>
    &lt;artifactId>uber-jar&lt;/artifactId>
    &lt;version>6.6.3&lt;/version>
    &lt;classifier>deprecated-apis&lt;/classifier>
    &lt;scope>provided&lt;/scope>
    &lt;/dependence>
    &quot;

Siehe auch [Aktualisieren der UberJar-Version von AEM](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Aktualisieren {#upgrade}

* Weitere Informationen zum Upgrade-Verfahren finden Sie unter [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md).
* Detaillierte Anweisungen finden Sie unter [Upgrade-Leitfaden für AEM Forms 6.5 LTS SP1 auf JEE](https://experienceleague.adobe.com/de/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade).

## Best Practices für AEM 6.5 LTS Service Pack-Upgrades

<!-- THE INFORMATION UNDER THIS HEADING CAME FROM CQDOC-23078 -->

Gilt für: AEM 6.5 LTS (On-Premise)-Kunden, die Service Pack 3 (SP3) installieren. SP3 wird als Schnellstart-JAR-Datei bereitgestellt.

**Darum ist dieses Upgrade-Verfahren wichtig**
SP2 für AEM 6.5 LTS wird als Schnellstart-JAR-Datei und nicht als ZIP-Datei zur Installation über den Paket-Manager bereitgestellt. On-Premise-Kunden führen ein Upgrade durch, indem sie die Schnellstart-JAR-Datei ersetzen, entpacken und neu starten. Diese Methode entspricht dem standardmäßigen Upgrade-Verfahren von Adobe.


**Empfohlener Upgrade-Ablauf (Autoren- oder Veröffentlichungsinstanz)**

1. Stellen Sie sicher, dass Ihre AEM 6.5 LTS-Instanz fehlerfrei funktioniert und Sie darauf zugreifen können.
1. Laden Sie die Schnellstart-JAR-Datei (z. B. `cq-quickstart-6.6.x.jar`) von Software Distribution herunter.
1. Stoppen Sie die Instanz, die ausgeführt wird.
1. Ersetzen Sie im AEM-Installationsverzeichnis (außerhalb von `crx-quickstart/`) die vorherige Schnellstart-JAR-Datei durch die SP3-JAR-Datei.
1. Entpacken Sie die JAR-Datei:

       „java
     java -jar cq-quickstart-6.6.x.jar -unpack
     &quot;
   
   (Passen Sie Heap-Flags nach Bedarf an.)

1. Benennen Sie die entpackte JAR-Datei so um, dass sie der Rolle und dem Port entspricht, z. B. `cq-author-4502.jar` oder `cq-publish-4503.jar`.
1. Starten Sie AEM und bestätigen Sie das Upgrade auf der Benutzeroberfläche („Hilfe“ > „Info“) und in den Protokollen.

**Best Practices**

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


Detaillierte Anweisungen finden Sie in der [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md), da für LTS Service Pack-Aktualisierungen dieselbe Dokumentation gilt.

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

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Bereitstellung verwenden. Planen Sie Änderungen an Ihrer Implementierung, um die bereitgestellte Alternative zu verwenden.

| Bereich | Funktion | Ersatz | Version (SP) |
| --- | --- | --- | --- |
| Sites | Zusammenfassung des Inhaltsfragmenttextes | Es steht kein Ersatz zur Verfügung. | |
| Schnellstart | Mongo-APIs | Mongo-APIs werden nicht mehr unterstützt und sollen in zukünftigen Versionen entfernt werden. | 6.5 TS SP2 |
| Sites | Unterstützung von Inhaltsfragmenten in der AEM Assets-REST-API | AEM 6.5 LTS SP2 bietet moderne OpenAPIs für die Verwaltung von Inhaltsfragmenten und -modellen. Daher wurden die älteren Endpunkte zur Unterstützung von Inhaltsfragmenten in der AEM Assets-REST-API jetzt eingestellt.<br>Adobe beabsichtigt, diese älteren Endpunkte bis zu einer Ankündigung zum Ende der Nutzungsdauer verfügbar zu halten. Adobe plant keine weiteren Verbesserungen an den veralteten Endpunkten. | 6.5 LTS SP2 |
| Sites | [SPA-Editor](/help/sites-developing/spa-overview.md) | Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind:<br>– [Der universelle Editor](/help/sites-developing/universal-editor/introduction.md) für visuelle Bearbeitung.<br>– [Der Inhaltsfragment-Editor](/help/assets/content-fragments/content-fragments-managing.md) für formularbasierte Bearbeitung. | 6.5 LTS GA |
| [!DNL Foundation] | Unterstützung für com.adobe.granite.oauth.server | Adobe IMS-Integration | |

### Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden die Funktionen aufgeführt, die aus AEM 6.5 LTS entfernt wurden. In früheren Versionen wurden diese Funktionen als veraltet gekennzeichnet.

* Die Unterstützung für RDBMK für die Persistenz des Adobe CRX-Repositorys wurde entfernt.
* In Cluster-Umgebungen ist MongoMK jetzt die einzige unterstützte Option für Repository-Persistenz.

| Bereich | Funktion | Ersatz | Version (SP) |
| --- | --- | --- | --- |
| Commerce | AEM CIF Classic wird nicht unterstützt. | Migrieren Sie zu [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Lösungen | Social/Communities wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Screens | Screens werden nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Assets | `dam-pim` und `dam-rating` werden nicht unterstützt, da Pakete von Social abhängig sind. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Assets | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` wurde entfernt. | Verwenden Sie die hinzugefügte alternative API `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()`. | 6.5 LTS GA |
| Portal | AEM Portal Director wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Granite | Paket `com.adobe.granite.socketio` wird entfernt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Granite | `com.adobe.granite.crx-explorer` wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Granite | `crx2oak` wird nicht unterstützt. | Wählen Sie die relevante Version von [Oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) aus. | 6.5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Guava | Alle Guava-Abhängigkeiten sind jetzt aus AEM entfernt und daher ist das Paket `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` nicht Teil von AEM. | Kunden können Guava selbst hinzufügen, wenn sie von Guava abhängig sind, oder Guava-Code durch Java-Sammlungen oder andere Alternativen ersetzen, sofern möglich. | 6.5 LTS GA |
| `We.Retail` | Die Beispiel-Site `We-retail` wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Open Source | Paket `oak-solr-osgi` wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Open Source | `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` und `org.apache.sling.atom.taglib` werden nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Open Source | `org.apache.commons.io`-Pakete werden jetzt aus `org.apache.commons.commons-io` exportiert. | Keine Änderung erforderlich. | 6.5 LTS GA |
| Open Source | `javax.mail`-Pakete werden aus dem Bundle `com.sun.javax.mail` exportiert. | Keine Änderung erforderlich. | 6.5 LTS GA |
| Open Source | `org.apache.jackrabbit.api`-Pakete werden jetzt aus dem Bundle `org.apache.jackrabbit.oak-jackrabbit-api` exportiert. | Keine Änderung erforderlich. | 6.5 LTS GA |
| Open Source | `com.github.jknack.handlebars` wird nicht unterstützt | Wählen Sie die relevante [Version](https://mvnrepository.com/artifact/com.github.jknack/handlebars) aus | 6.5 LTS GA |

## Bekannte Probleme {#known-issues}

### AEM Forms

* Im Configuration Manager schlägt die Datenbankinitialisierung beim Bootstrap im benutzerdefinierten Turnkey-Modus von AEM Forms 6.5 LTS JEE fehl, wenn keine Module oder nur eingeschränkte Komponenten ausgewählt sind. Das Problem ist auf eine fehlende Abhängigkeit (xalan-2.7.2.jar) zurückzuführen, die zu einem Fehler führt. Durch Hinzufügen der JAR-Datei zu Adobe-livecycle-jboss.ear\lib wird das Problem behoben. (FORMS-24690)
* Bei Forms JEE LTS Service Pack 2-Bereitstellungen, die auf dem WebSphere® Liberty-Profil ausgeführt werden, schlägt die E-Mail-Funktion fehl. Beim Versuch, E-Mail-Funktionen zu verwenden, protokolliert der Server einen Fehler: `Could not convert socket to TLS`. (FORMS-24692)
* Bei Forms JEE LTS, das auf JBoss® ausgeführt wird, schlägt die E-Mail-bezogene Funktion fehl. Beim Versuch, E-Mail-Funktionen zu verwenden, protokolliert der Server einen Fehler: `Error IMAPProvider not a subtype`. Um dieses Problem zu beheben, installieren Sie den Hotfix von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-core-jboss.ear). (FORMS-24892)

### Repository-Beschädigung bei Online-Komprimierung nach Offline-Komprimierung (GRANITE-65146) {#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146}

Bei Benutzenden kann während der Online-Komprimierung eine Beschädigung des Repositorys auftreten, wenn sie zuvor die Offline-Komprimierung auf dem JCR-Repository ausgeführt haben. In diesem Szenario kann eine `SegmentNotFoundException` (SNFE) auftreten, die zu einer Beschädigung des Repositorys führen kann.

Um das Problem zu beheben, installieren Sie den Hotfix von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.2-hotfix-GRANITE-65388-1.0.zip). Da der Hotfix ein `oak-segment-tar`-Paket auf niedriger Ebene enthält, wird die Instanz nach der Installation neu gestartet.

Planen Sie die Ausfallzeiten der Instanz bei der Hotfix-Anwendung ein. Verwenden Sie für die Offline-Komprimierung die entsprechende [`oak-run`-JAR](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar), die auch auf Software Distribution verfügbar ist.

>[!NOTE]
>
> * Verwenden Sie für alle „`oak-run`“-Vorgänge die Datei „[`oak-run` 1.88.1-B006 jar](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar)“.
>
> * Starten Sie AEM, indem Sie die Systemeigenschaft „`oak.compaction.legacy=true`“ einstellen.

### Fehlendes `com.adobe.granite.apicontroller`-Bundle in AEM 6.5 LTS SP2 (GRANITE-67640) {#missing-apicontroller-bundle-granite-67640}

Das `com.adobe.granite.apicontroller`-Bundle fehlt in AEM 6.5 LTS SP2. Dieses Bundle steuert, wie OSGi-Bundles aufgelöst werden, und kann verhindern, dass Bundles in andere Bundles aufgelöst werden. Dies ist nützlich, um die Anzahl der verfügbar gemachten APIs zu begrenzen.

Um diese Funktion zu verwenden, installieren Sie den Hotfix von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.2-hotfix-GRANITE-67640-1.0.zip).

>[!NOTE]
>
> Um sicherzustellen, dass die Standardkonfiguration von `com.adobe.granite.apicontroller` keine unbeabsichtigten Auflösungsbeschränkungen einführt, die sich auf bestehende benutzerdefinierte Implementierungen auswirken, überprüfen Sie den Bundle-Status aller installierten Bundles nach der Installation des Hotfixes.

### JSON-Kommentare werden in Sling-Initial-Content (SP2) nicht mehr unterstützt {#json-comments-no-longer-supported-in-sling-initial-content}

Dieses Problem betrifft Entwicklerinnen und Entwickler von OSGi-Paketen und Admins, die Pakete bereitstellen, die `Sling-Initial-Content` mit JSON-Dateien verwenden.

Ab AEM 6.5 LTS SP2 akzeptieren JSON-Dateien, die in `Sling-Initial-Content` Paketen verwendet werden, keine Kommentare mehr (`//` oder `/* */`). Frühere AEM-Versionen akzeptierten Kommentare, da der `javax.json`-Anbieter diesbezüglich kulant war. AEM 6.5 LTS SP2 aktualisierte `org.apache.sling.jcr.contentloader` auf Version 2.6.0, wodurch der JSON-Parser auf `jakarta.json` umgestellt wurde. Während die [JSON-Spezifikation (RFC 8259)](https://datatracker.ietf.org/doc/html/rfc8259) keine Syntax für Kommentare definiert, wurden diese in früheren AEM-Versionen akzeptiert, da der `javax.json`-Anbieter diesbezüglich kulant war. Der `jakarta.json`-Anbieter bietet diese Erweiterung nicht an.

Der Ausfall erfolgt still: Inhaltsknoten werden bei der Paket-Aktivierung nicht geladen, wobei im Installationsprogramm kein Fehler ausgegeben wird. Wenn nach dem Upgrade auf SP2 unerwartet Inhalte fehlen, suchen Sie im Protokoll des OSGi-Installationsprogramms nach JSON-Parsing-Fehlern. Zur Identifizierung betroffener Pakete suchen Sie in den JSON-Dateien, die unter den `Sling-Initial-Content`-Manifest-Headern aufgeführt sind, nach „`//`“ oder „`/* */`“.

>[!CAUTION]
>
> Um Fehler beim Laden von Inhalten nach dem Upgrade auf AEM 6.5 LTS SP2 zu vermeiden, entfernen Sie alle Kommentare aus JSON-Dateien in Ihren `Sling-Initial-Content`.

### Die Aktualisierung des Jackson-Bundles wirkt sich auf den GlobalLink-Connector aus {#jackson-upgrade-globallink-connector}

AEM 6.5 LTS SP3 aktualisiert das `jackson`. Diese Änderung betrifft Bereitstellungen, die den GlobalLink-Übersetzungs-Connector verwenden.

Wenn Sie das `gs4tr-globallink-adaptors-aem.core`-Bundle mit einer älteren Version als 3.4.0 verwenden, aktualisieren Sie das Bundle auf eine kompatible Version. Version 3.4.0 oder höher funktioniert mit dem aktualisierten `jackson`-Bundle in SP3.

>[!NOTE]
>
> Aktualisieren Sie das `gs4tr-globallink-adaptors-aem.core`-Bundle vor oder während des SP3-Updates auf 3.4.0 oder höher, um Kompatibilitätsprobleme mit dem GlobalLink-Connector zu vermeiden.


### Installieren erforderlicher Oak-Indizes für Sites Headless-APIs{#site-headless-api}

Einige APIs, die zu Sites Headless verschoben wurden, erfordern zusätzliche Oak-Indizes, damit die volle Funktionalität genutzt werden kann.

Installieren Sie das `cq-dam-cfm-indices`-Paket, um die folgenden Funktionen zu verwenden:

* Auflisten von Inhaltsfragmentmodellen
* Auflisten von Inhaltsfragmenten
* Such-API
* Workflows

Laden Sie das Indexpaket [cq-dam-cfm-](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fcq-dam-cfm-indices-1.1.5.zip) im Adobe Software Distribution-Portal herunter.

### Dispatcher-Verbindungsfehler mit Funktion „Nur SSL“ (behoben in AEM 6.5 LTS SP1 und höher){#ssl-only-feature}

>[!NOTE]
>
> Dieses Problem tritt nur in Version AEM 6.5 LTS GA auf.

Bei der Aktivierung der Funktion „Nur SSL“ in AEM-Bereitstellungen gibt es ein bekanntes Problem, das die Verbindung zwischen dem Dispatcher und AEM-Instanzen beeinträchtigt. Nach Aktivierung dieser Funktion schlagen Konsistenzprüfungen fehl und die Kommunikation zwischen Dispatcher- und AEM-Instanzen wird unterbrochen. Dieses Problem tritt insbesondere auf, wenn Kundinnen und Kunden versuchen, eine Verbindung über `https + IP` von Dispatcher zu AEM-Instanzen herzustellen. Dies steht im Zusammenhang mit SNI-Validierungsproblemen (Server Name Indication).

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

Wenn dieses Problem auftritt, wenden Sie sich an den Adobe-Support. Zur Lösung dieses Problems ist Hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) verfügbar. Versuchen Sie nicht, „Nur SSL“-Funktionen zu aktivieren, bis Sie den erforderlichen Hotfix angewendet haben.

## Enthaltene OSGi- und Inhaltspakete{#osgi-bundles-and-content-packages-included}

Die folgenden ZIP-Dateien enthalten die Textdokumente, die die in dieser Experience Manager 6.5 LTS Service Pack-Version enthaltenen OSGi-Bundles und Inhaltspakete auflisten:

* [OSGi-Bundles](/help/release-notes/assets/65lts_sp3_bundles.zip)
* [Inhaltspakete](/help/release-notes/assets/65lts_sp3_packages.zip)

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produkt-Download unter „licensing.adobe.com“](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/de/docs/support-resources/adobe-support-tools-guide/adobe-customer-support-experience).

