---
source-git-commit: 0deac9cb7fb13c6fec515739168eb2dbfd9a58c7
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 69%

---
# Richtlinien für Beiträge zur Adobe Experience Manager-Dokumentation

## Dokumentationsphilosophie

Adobe Experience Manager-Anwender arbeiten in einem hart umkämpften Umfeld und sind bestrebt, digitale Erlebnisse zu schaffen, die sie von ihren Mitbewerbern abheben. Deshalb ist es wichtig, wenn Adobe erweiterte neue Tools in AEM bereitstellt, dass diese Werkzeuge durch eine genaue und klare Dokumentation ergänzt werden, damit die Kundinnen und Kunden sofort ihre AEM-Investition nutzen und den ROI maximieren können.

Das Ziel der AEM-Dokumentation besteht darin, AEM-Benutzende schnellstmöglich mit der Dokumentation vertraut zu machen. Daher legt das AEM-Dokumentations-Team Wert auf genaue, verwendbare Dokumentationen und ist bestrebt, diese kontinuierlich zu aktualisieren und zu verbessern.

## Beiträge zur Dokumentation

Zur stetigen Verbesserung der AEM-Dokumentation ist die gesamte Community von AEM-Benutzern herzlich eingeladen, zur Dokumentation beizutragen. Sei es durch Pull-Anfragen oder Probleme, bei den Verbesserungen der Dokumentation kann es sich um Korrekturen, Klarstellungen, Erweiterungen und weitere Beispiele handeln.

## Dokumentationsstandards

Während das Dokumentationsteam von Experience Manager Beiträge zur Dokumentation von Adobe begrüßt, sollten alle Beiträge zur Dokumentation von AEM - entweder in Form einer Pull-Anfrage oder eines Problems - mit den Beitrags- und Dokumentationsstandards des Teams übereinstimmen.

Beiträge, die diesen Standards nicht entsprechen, können abgelehnt werden.

### Experience Manager-Dokumentations-Team dokumentiert Standardanwendungsfälle.

Die AEM-Dokumentation umfasst Standard-Anwendungsfälle. Anwendungsfälle, die über den Umfang der standardmäßigen Installation und Nutzung des Produkts hinausgehen, sind nicht Teil der AEM-Dokumentation.

### Das Experience Manager-Dokumentations-Team dokumentiert im Allgemeinen keine Fehler oder Problemumgehungen.

Die AEM-Dokumentation umfasst Standard-Anwendungsfälle. Aus diesem Grund werden Fehler, durch Bugs verursachte Auswirkungen und Problemumgehungen für Bugs nicht dokumentiert.

Ausnahmen gelten für die Versionshinweise, in denen bekannte Probleme mit möglichen Lösungen aufgelistet werden können, die vom AEM Product Management genehmigt wurden.

### Dokumentationsbeiträge sind nicht zur Beantwortung technischer Fragen gedacht.

Alle Ideen, die Sie möglicherweise zur Verbesserung der AEM-Dokumentation haben, sind als Beiträge willkommen. Kommentare, Probleme und Pull-Anfragen sind jedoch nur für *Beiträge* vorgesehen. Sie sind nicht zur Beantwortung Ihrer Fragen über die Verwendung von AEM, Implementierung Ihres AEM-Projekts oder zur Lösung technischer Probleme gedacht.

Fragen zur Verwendung von AEM oder zu technischen Fehlern, die möglicherweise bei Ihnen auftreten, sollten entsprechend dem herkömmlichen Support-Prozess über das [Support-Portal für Experience Manager](https://experienceleague.adobe.com/de?support-solution=Experience+Manager&lang=de#home) gemeldet oder in der [Experience Manager-Community](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community?profile.language=de&lang=de) diskutiert werden.

***AEM-Dokumentationsbeiträge sind kein Ersatz für den Adobe-Support*** und Beiträge, die um Antwort auf Support-Fragen bitten, werden abgelehnt.

### Die Beiträge müssen sich eindeutig auf die betroffenen Dokumentationsseiten beziehen.

Wenn Sie ein Problem erstellen, um Verbesserungen an der Dokumentation vorzuschlagen, müssen Sie Links zu den betroffenen Seiten angeben. Wenn Sie ein Problem mithilfe des Links **Diese Seite bearbeiten** auf einer Dokumentationsseite erstellen, wird das Problem automatisch mit einem Link zur Seite erstellt.

Dies gilt nicht für Pull-Anforderungen, da Pull-Anforderungen naturgemäß auf die betroffenen Seiten verweisen.

## Dokumentationsrichtlinien

Alle Beiträge zur AEM-Dokumentation müssen bestimmten Stilrichtlinien entsprechen.

Die Befolgung dieser Richtlinien erleichtert die Überprüfung Ihres Beitrags und beschleunigt somit die Integration in die AEM-Dokumentation.

### Sprache und Stil

#### Sprache

* Die AEM-Dokumentation wird in englischer Sprache verfasst und verwaltet.
* Ausdrücke sollten so einfach wie möglich sein.
* Drücken Sie sich klar und bündig aus.

Denken Sie daran, dass die Leser der AEM-Dokumentation auf der ganzen Welt zu finden sind und von ihnen nicht erwartet werden kann, dass sie fließend Englisch beherrschen oder Muttersprachler sind. Vermeiden Sie umgangssprachliche Wendungen und verwenden Sie eine klare und einfache Sprache wie möglich.

#### Befolgen des „Manual of Style von Microsoft®“

Das [Manual of Style von Microsoft®](https://learn.microsoft.com/de-de/style-guide/welcome/) ist ein kostenloses Dokumentationshandbuch, das sich auf Software-Dokumentation konzentriert. Die AEM-Dokumentation folgt diesem Handbuch, soweit möglich.

### Formatierung

| Element | Stil |
|---|---|
| Element oder Option der Benutzeroberfläche | **fett** |
| Dateiname, Pfad, Benutzereingabe, Parameterwerte | `monospaced` |
| Code, Befehlszeile | ```Code Block``` |

### Screenshots

Screenshots sind mit Bedacht und nur dann zu verwenden, wenn eine Textbeschreibung nicht ausreicht.

Verwenden Sie keine Markierungen oder anderen Anmerkungen in Screenshots (z. B. rote Rahmen, Pfeile oder Text). Auf diese Weise können die Screenshots in lokalisierten Versionen der Dokumentation einfacher wiederverwendet oder repliziert werden.

### Versionsspezifische Verweise

Versuchen Sie nach Möglichkeit direkte Verweise auf eine bestimmte Version im gesamten Dokumentationsinhalt zu vermeiden. Dadurch wird die Dokumentation für künftige Versionen flexibler und erweiterbarer.

### Verwendung von Day, AEM, CQ, CRX

Das Produkt sollte in einem Artikel zum ersten Mal immer mit dem vollständigen Namen **Adobe Experience Manager** bezeichnet und anschließend als **AEM** bezeichnet werden.

Verwenden Sie nicht die Begriffe „Day“, „Day Software“, „CQ“ oder „CRX“, außer wo dies unvermeidbar ist, weil es z. B. um Klassennamen oder frühere Versionen von AEM geht.