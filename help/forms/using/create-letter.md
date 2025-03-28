---
title: Erstellen eines Briefes
description: In diesem Thema werden die Schritte erläutert, die Sie zum Erstellen eines Briefes und zum Hinzufügen von Datenmodulen und Anhängen an diesen Brief und einer Vorschau des Briefes im Correspondence Management benötigen.
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: b866ff4a-251c-4402-b426-9c4d97fd181d
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '3982'
ht-degree: 100%

---

# Erstellen eines Briefes {#create-letter}

## Correspondence Management-Workflow {#correspondence-management-workflow}

Der Correspondence Management-Workflow besteht aus vier Phasen:

1. Vorlagenerstellung
1. Dokumentfragmenterstellung
1. Brieferstellung
1. Nachbearbeitung

### Vorlagenerstellung {#template-creation}

Die folgende Abbildung zeigt einen typischen Workflow zur Erstellung einer Korrespondenzvorlage.

![Arbeitsablauf für das Erstellen einer Korrespondenzvorlage](assets/01.png)

Die einzelnen Workflow-Schritte:

1. Formular-Designerinnen und -Designer erstellen Layouts und Fragment-Layouts mit Adobe Forms Designer und laden sie in ein CRX-Repository hoch. Die Layouts enthalten typische Formularfelder, Layout-Merkmale wie Kopf- und Fußzeilen sowie leere „Zielbereiche“ zur Platzierung von Inhalten. Zu einem späteren Zeitpunkt ordnen Anwendungsspezialistinnen und -spezialisten die entsprechenden Inhalte den jeweiligen Zielbereichen zu. Weitere Informationen finden Sie unter [Entwickeln eines Layouts](/help/forms/using/layout-design-details.md).
1. Fachleute aus Rechts-, Finanz- oder Marketing-Abteilungen erstellen Inhalte und laden sie hoch, etwa Textabschnitte, Haftungsausschlüsse, Nutzungsbedingungen und Bilder, z. B. Logos, die in verschiedenen Korrespondenzvorlagen wiederverwendet werden.
1. Anwendungsspezialistinnen und -spezialisten erstellen Korrespondenzvorlagen. Die Anwendungsfachkraft:

   * ordnet den Zielbereichen in den Layout-Vorlagen Textabschnitte und Bilder zu
   * legt Bedingungen/Regeln für die Einbeziehung von Inhalten fest
   * verknüpft Layout-Felder und Variablen mit zugrunde liegenden Datenmodellen

1. Verfasser zeigt den Brief in einer Vorschau an und reicht ihn zur Nachbearbeitung ein. Weitere Informationen finden Sie unter [Nachbearbeitung](/help/forms/using/submit-letter-topostprocess.md).

#### Verwenden der im Correspondence Management bereitgestellten Briefvorlagen {#using-letter-templates-provided-with-correspondence-management}

Anstatt eine völlig neue Layout-Vorlage zu erstellen, können Sie die vom Correspondence Management bereitgestellten Vorlagen ändern und wiederverwenden. Sie können mit Designer rasch das Branding sowie die Daten- und Inhaltsfelder in den Vorlagen an die Anforderungen Ihrer Organisation anpassen. Weitere Informationen zu Correspondence Management-Vorlagen finden Sie unter [Referenzieren von Briefvorlagen](/help/forms/using/reference-cm-layout-templates.md).

### Dokumentfragmenterstellung {#document-fragment-creation}

Dokumentfragmente sind wiederverwendbare Teile/Komponenten einer Korrespondenz, mit der Sie Briefe/Korrespondenz erstellen können.

Es gibt Dokumentfragmente der folgenden Typen:

#### Text {#text}

Ein Textelement ist eine Inhaltskomponente, die aus einem oder mehreren Textabsätzen besteht. Ein Absatz kann statisch oder dynamisch sein. Ein dynamischer Absatz enthält Verweise auf Datenelemente, deren Werte zur Laufzeit bereitgestellt werden.

#### Liste {#list}

Eine Liste ist eine Reihe von Dokumentenfragmenten, einschließlich Text, Listen (die gleiche Liste kann nicht zu sich selbst hinzugefügt werden), Bedingungen und Bildern. Die Reihenfolge der Listenelemente kann festgelegt sein oder bearbeitet werden. Beim Erstellen eines Briefs können Sie einige oder alle Listenelemente verwenden, um ein wiederverwendbares Muster von Elementen zu replizieren.

#### Bedingung {#condition}

Mithilfe von Bedingungen können Sie festlegen, welche Inhalte zum Zeitpunkt der Korrespondenzerstellung abhängig von den bereitgestellten Daten einbezogen werden sollen. Die Bedingung wird in Form von Steuerungsvariablen beschrieben. Bei den Variablen kann es sich entweder um ein Datenwörterbuchelement oder einen Platzhalter handeln. Beim Hinzufügen einer Bedingung haben Sie die Möglichkeit, ein Asset einzubeziehen, das auf dem Wert beruht, den die Steuerungsvariable hat. Bedingungen führen zu einer einzelnen Ausgabe, die von einem Ausdruck abhängt. Der erste Ausdruck gilt basierend auf der aktuellen Bedingungsvariable als „true“. Der entsprechende Wert wird zur Ausgabe der Bedingung.

#### Layout-Fragment {#layout-fragment}

Unter einem Layout-Fragment versteht man ein Layout, das mit einem oder mehreren Briefen verwendet werden kann. Ein Layout-Fragment wird verwendet, um wiederholbare Muster, insbesondere dynamische Tabellen, zu erstellen. Das Layout kann typische Formularfelder wie „Adresse“ und „Referenznummer“ enthalten. Es enthält auch leere Unterformulare, die Zielbereiche kennzeichnen. Die Layouts (XDP-Dateien) werden in Designer erstellt und können dann [in Formulare und Dokumente hochgeladen werden](/help/forms/using/get-xdp-pdf-documents-aem.md).

### Brieferstellung {#letter-creation}

Es gibt zwei Möglichkeiten, die Korrespondenz zu generieren, die an Ihre Kundschaft gesendet wird: benutzergesteuert und systemgesteuert.

#### Benutzergesteuert {#user-driven}

Kundschaftsorientierte Mitarbeitende (z. B. in der Schadensregulierung oder Sachbearbeitung) können angepasste Schriftstücke erstellen. Über eine einfache und intuitiv bedienbare Benutzeroberfläche zur Brieferstellung können Geschäftsbenutzende dem Schriftstück optionalen Text hinzufügen, bearbeitbaren Inhalt personalisieren und das Schriftstück in Echtzeit in der Vorschau anzeigen. Sie können die angepasste Korrespondenz dann an einen Backend-Prozess senden.

![Benutzergesteuerte, angepasste Korrespondenz](assets/02.png)

#### Systemgesteuert {#system-driven}

Die Erstellung von Schriftstücken wird durch sogenannte Ereignistrigger ausgelöst und erfolgt automatisch. Beispiel: Ein Mahnschreiben zur Erinnerung an eine Steuervorauszahlung wird durch Zusammenfügung der vorab definierten Vorlage mit den Kontaktdaten des Empfängers generiert. Der endgültige Brief kann per E-Mail gesendet, ausgedruckt, als Fax verschickt oder archiviert werden.

![Systemgesteuerte Korrespondenz](assets/us_cm_generate.png)

### Nachbearbeitung {#post-processing}

Die endgültige Korrespondenz kann zur Nachbearbeitung an einen Backend-Prozess gesendet werden. Der Status kann wie folgt lauten:

1. Für den Versand per E-Mail oder Fax oder für den Batch-Druck verarbeitet bzw. zwecks Druck oder E-Mail-Versand in einem Ordner abgelegt.
1. Zur Überprüfung und Genehmigung vorgelegt.
1. Durch Anwendung digitaler Signaturen, Zertifizierung, Verschlüsselung oder Rights Management gesichert.
1. Konvertiert in ein durchsuchbares PDF-Dokument, das alle für Archivierungs- und Auditing-Zwecke erforderlichen Metadaten enthält.
1. Eingebunden in ein PDF-Portfolio, das noch weitere Dokumente enthält, z. B. Marketing-Material. Das PDF-Portfolio kann dann als endgültiges Schriftstück gesendet werden.

### Architektur von Correspondence Management-Lösungen {#correspondence-management-solution-architecture}

Die folgende Grafik bietet eine Übersicht über eine Beispielarchitektur der Brieflösung.

![Architektur für Brieflösung](assets/us_cm_architecture_es3.png)

## Einzelkomponenten eines Briefs {#deconstructing-a-letter}

Dieses Dokument einer Kündigungsmitteilung ist ein Beispiel für eine typische Korrespondenz:

![Ein Beispielkündigungsbrief](assets/5_deconstructingaletter.png)

<table> 
 <tbody> 
  <tr> 
   <td><strong>Briefelemente</strong></td> 
   <td><strong>Beschreibung</strong></td> 
   <td><strong>Formuliert mit</strong></td> 
  </tr> 
  <tr> 
   <td>Daten aus Backend-Unternehmenssystemen</td> 
   <td>Daten, die aus Backend-Unternehmenssystemen bezogen werden. Die Daten werden dynamisch mit der Korrespondenzvorlage kombiniert.</td> 
   <td>Datendatei<br />, die basierend auf einem Datenwörterbuch erstellt wurde</td> 
  </tr> 
  <tr> 
   <td>Daten<br />, die von im Kundenkontakt stehenden Mitarbeiterinnen und Mitarbeitern eingegeben wurden</td> 
   <td>Daten, die von Kundenkontakt stehenden Mitarbeiterinnen und Mitarbeitern bereitgestellt werden können, die Briefe vor dem Versand einzeln anpassen.<br /> </td> 
   <td><p>Ungeschützte DD-Elemente<br /> Bearbeitbare Textabschnitte<br /> Variablen/Platzhalter<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Vorab genehmigte<br /> Textabschnitte</td> 
   <td>Vorab genehmigte Textinhalte. Der Textinhalt wird meist von Fachleuten aus den Bereichen Recht oder Finanzen oder aus einer Branche verfasst, in der man mit dem geschäftlichen Kontext eines Briefs vertraut ist. Dabei sind Inhalte wie Kopf- und Fußzeile, Haftungsausschlüsse und Grußformeln gängige Bestandteile der meisten Briefe. Andere Inhalte, wie z. B. der Grund für eine Kündigung, sind spezifisch für den jeweils zu erstellenden Brief.</td> 
   <td><p>Text\Listen\<br /> Bedingungen\Layout</p> <p> </p> </td> 
  </tr> 
  <tr> 
   <td>Daten<br /> basierend auf benutzerspezifischer Logik ?</td> 
   <td>Für einige Briefe, z. B. einen Brief, in dem weitere Informationen zu einem Schaden angefordert werden, können Benutzer wie etwa der Schadensregulierer benutzerdefinierte Textinhalte hinzufügen.</td> 
   <td>Dokument<br />-Fragment der Typenbedingung </td> 
  </tr> 
  <tr> 
   <td>Gespeicherte<br /> Bilder aus dem zentralen Repository</td> 
   <td>Bilder wie Logos und Signaturbilder. Bilder wie Unternehmenslogos sind wohl in den meisten oder in allen Anschreiben enthalten. Unterschriftsbilder sind spezifisch für den Brief und die Person, in deren Namen der Brief gesendet wird.</td> 
   <td><p>In AEM-Assets (DAM) gespeicherte Bilder<br /> </p> <p> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analyse eines Briefes vor der Erstellung {#analyze-a-letter-before-you-construct-it}

Analysieren Sie jeden Brief, um die verschiedenen Teile freizulegen, die den Brief bilden. Die Anwendungsfachkraft analysiert die generierten Anschreiben.

* Welche Teile der Korrespondenz sind statisch und welche dynamisch? Die aus Backend-Datenquellen oder von Endbenutzenden übernommenen Variablen.
* Die Reihenfolge, in der die verschiedenen Textabsätze in der Korrespondenz angezeigt werden, z. B. ob Business-Anwenderinnen und -Anwender Absätze während der Korrespondenzerstellung ändern können.
* Wird die Korrespondenz vom System generiert oder sind Endbenutzende erforderlich, um die Korrespondenz zu bearbeiten? Wie viele Korrespondenzen werden vom System generiert und wie viele erfordern ein Eingreifen auf Benutzerseite?
* Wie oft ändert sich die Korrespondenzvorlage? Wird sie jährlich, vierteljährlich oder nur bei einer Änderung bestimmter Rechtsvorschriften aktualisiert? Welche Änderungen werden erwartet? Erfolgt die Änderung, um Rechtschreibfehler zu beheben, das Layout zu ändern, weitere Felder hinzuzufügen, weitere Abschnitte hinzuzufügen, usw.
* Stellen Sie bei der Planung Ihrer Korrespondenzanforderungen die Liste der neuen Korrespondenzvorlagen zusammen. Für jede Korrespondenzvorlage benötigen Sie:

   * Textbausteine, Bilder und Tabellen
   * Datenwerte aus Backend-Systemen
   * Layout und Fragment-Layouts der Korrespondenz
   * Die Reihenfolge, in der die Inhalt im Brief angezeigt werden, und Regeln für die Einbeziehung und den Ausschluss von Inhalten

* Die Bedingungen, unter denen Business-Anwenderinnen und -Anwender, etwa bei der Schadensregulierung oder der Sachbearbeitung, Inhalte oder Teile davon im Brief ändern.
* Szenarien beschreiben das Benutzererlebnis, die Anforderungen und die Vorteile der Brieflösung.
* Szenarien bieten außerdem die erforderlichen Fertigkeiten und Tools, die Sie für Ihr Projekt benötigen.
* Empfohlene Vorgehensweisen für die Planung Ihrer Implementierung. ``Allgemeine Übersicht über die Implementierung.

## Vorteile der Analyse {#benefits-of-performing-the-analysis}

**Wiederverwendung von Inhalten**: Sie haben eine konsolidierte Liste mit neuen Inhalten, die für die Generierung von Korrespondenz erforderlich sind. Ein Großteil des Inhalts, wie etwa Kopf- und Fußzeilen, Haftungsausschlüsse und Einführungen, kommt in vielen Briefen vor und kann daher für zahlreiche Briefe wiederholt werden. All diese gemeinsamen Inhalte können von Fachleuten einmalig erstellt und genehmigt und dann in vielen Anschreiben wiederverwendet werden.

**Aufbau des Datenwörterbuchs**: Es gibt Datenwerte wie „Kundennummer“ und „Kundenname“, die in vielen Briefen verwendet werden. Sie können eine konsolidierte Liste aller dieser Datenwerte erstellen. Normalerweise wird bei der Strukturplanung jemand vom Middleware-Team des Unternehmens konsultiert. Dies bildet die Grundlage für die Erstellung des Datenwörterbuchs.

**Bezug von Daten aus Backend-Unternehmenssystemen**: Sie werden auch über alle erforderlichen Datenwerte und deren jeweilige Bezugsquelle im Unternehmenssystem Bescheid wissen. Sie können dann die Architektur so einrichten, dass die Daten aus dem Unternehmenssystem extrahiert und an die Brieflösung übermittelt werden.

**Schätzung der Komplexität von Briefen**: Es ist wichtig zu ermitteln, wie komplex die Erstellung einer bestimmten Korrespondenz sein wird. Anhand dieser Analyse kann bestimmt werden, wie viel Zeit und welche Fähigkeiten zur Erstellung der Briefvorlagen erforderlich sind. Dies wiederum erleichtert die Schätzung des Ressourcenbedarfs und der Kosten für die Implementierung der Brieflösung.

## Komplexität der Korrespondenz {#correspondence-complexity}

Die Komplexität der Korrespondenz kann durch die Analyse folgender Parameter bestimmt werden:

**Komplexität des Layouts** Wie komplex ist das Layout? Briefe wie etwa Kündigungsmitteilungen haben einfache Layouts. Briefe, wie z. B. Deckungsanspruchsbestätigungen, haben dagegen ein komplexes Layout mit mehreren Tabellen und mehr als 60 Formularfeldern. Das Erstellen komplexer Layouts nimmt mehr Zeit in Anspruch und erfordert umfangreichere Layout-Kenntnisse.

**Anzahl der Textabsätze und Bedingungen**: Ein Darlehensvertrag kann 10 Seiten lang sein und mehr als 40 Textbausteine enthalten. Viele dieser Textbausteine hängen von den Darlehensparametern ab. Je nach den genauen Vertragsbedingungen werden die einzelnen Bausteine in den Vertrag aufgenommen oder nicht. Die Erstellung solcher Briefe erfordert eine gründliche Planung und sorgfältige Definition der komplexen Bedingungen.

Diese Tabelle enthält einige Richtlinien, nach denen Sie Ihre Briefe klassifizieren können:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Komplexitätsstufe</strong></p> </td> 
   <td><p><strong>Komplexität des Layouts (subjektiv)</strong></p> </td> 
   <td><p><strong>Anzahl der Textabsätze</strong></p> </td> 
   <td><p><strong>Anzahl bedingter Textbausteine oder Bilder</strong></p> </td> 
   <td><p><strong>Erforderliche Kompetenz</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Geringe Komplexität</p> </td> 
   <td><p>Niedrig. Layout mit nur wenigen Formularfeldern (&lt;15).</p> <p>Normalerweise eine Seite<span class="acrolinxCursorMarker"></span>.</p> </td> 
   <td><p>8</p> </td> 
   <td><p>1</p> </td> 
   <td><p>Mittleres Kenntnisniveau in Designer.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Mittlere Komplexität</p> </td> 
   <td><p>Layout mit mittlerer Komplexität. Umfasst Strukturen wie Tabellen. In der Regel mehr als eine Seite lang.</p> </td> 
   <td><p>16</p> </td> 
   <td><p>2</p> </td> 
   <td><p>Mittleres Kenntnisniveau in Designer.</p> <p> </p> <p>Möglichkeit, komplexe Ausdrücke mithilfe von Benutzeroberflächen zu erstellen.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Hohe Komplexität</p> </td> 
   <td><p>Komplexes Layout. Kann mehr als drei Seiten umfassen. Enthält Tabellen und mehr als 60 Formularfelder.</p> </td> 
   <td><p>40</p> </td> 
   <td><p>8</p> </td> 
   <td><p>Professionelle Kenntnisse im Umgang mit Designer.</p> <p> </p> <p>Möglichkeit, komplexe Ausdrücke mithilfe von Benutzeroberflächen zu erstellen.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Übersicht über das Erstellen eines Briefs {#overview-of-creating-a-letter}

1. Wählen Sie das entsprechende Layout als Grundlage für den Brief aus und erstellen Sie einen Brief.
1. Fügen Sie dem Brief Datenmodule oder Layout-Fragmente hinzu und konfigurieren Sie sie.
1. Zeigen Sie eine Vorschau der Korrespondenz an.
1. Bearbeiten Sie die Felder, Variablen, Inhalte und Anlagen und richten Sie sie ein.

### Voraussetzungen {#prerequisites}

Zur Erstellung einer Korrespondenz müssen Sie zunächst Folgendes einrichten:

* [Kompatibilitätspaket](compatibility-package.md). Installieren Sie das Kompatibilitätspaket, um die Option **Briefe** auf der Seite **Formulare** anzuzeigen.
* Die XDP-Datei des Briefs ([Layout](/help/forms/using/document-fragments.md)).
* Andere XDP-Dateien ([Layoutfragmente](document-fragments.md#document-fragments)), die Bestandteile des Briefs bilden. Die XDP-Dateien/Layouts werden in [Designer](https://www.adobe.com/go/learn_aemforms_designer_65_de) erstellt.
* Das relevante [Datenwörterbuch](/help/forms/using/data-dictionary.md) (optional).
* Die [Datenmodule](/help/forms/using/document-fragments.md), die Sie in der Korrespondenz verwenden möchten.
* [Test-Daten](/help/forms/using/data-dictionary.md#p-working-with-test-data-p) bestehen aus der XML-Datei, in die die Testdaten portiert wurden. Testdaten sind erforderlich, wenn Sie ein Datenwörterbuch verwenden.

## Erstellen einer Briefvorlage {#create-a-letter-template}

### Wählen Sie ein Layout aus und geben Sie die Briefeigenschaften ein {#select-a-layout-and-enter-the-letter-properties}

1. Wählen Sie **Formulare** > **Briefe**.

1. Wählen Sie **Erstellen > Brief**. Correspondence Management zeigt die verfügbaren Layouts (XDPs) an. Diese Layouts stammen von Designer. Die Layouts umfassen auch die vorkonfigurierten Correspondence Management-Briefvorlagen. Weitere Informationen finden Sie unter [Referenzieren von Briefvorlagen](/help/forms/using/reference-cm-layout-templates.md). Um Ihre eigenen Layouts hinzuzufügen, erstellen Sie XDP-Dateien (Layout) in Designer und [laden Sie sie in AEM Forms hoch](/help/forms/using/get-xdp-pdf-documents-aem.md).

   ![create-letter](assets/create-letter.png)

1. Wählen Sie ein Layout durch Antippen und dann **Weiter** aus.

   ![Wählen eines Layouts, um einen Brief zu erstellen](assets/selectlayout.png)

1. Geben Sie die Eigenschaften für die Korrespondenz ein und wählen Sie **Speichern:** aus.

   * **Titel (optional)**: Geben Sie einen Titel für den Brief ein. Titel müssen nicht eindeutig sein und dürfen Sonderzeichen und nicht-englische Zeichen enthalten.
   * **Name**: Der eindeutige Name des Briefs. Es darf immer nur ein Brief mit einem bestimmten Namen in einem Status vorhanden sein. Im Feld „Name“ können Sie nur englische Zeichen, Zahlen und Bindestriche eingeben. Das Feld „Name“ wird automatisch auf der Grundlage des Titelfelds vorausgefüllt. Die Sonderzeichen, Leerzeichen, Zahlen und die nichtenglischen Zeichen im Feld „Titel“ werden im Feld „Name“ durch Bindestriche ersetzt. Obwohl der Wert im Feld „Titel“ automatisch in das Feld „Name“ kopiert wird, können Sie den Wert bearbeiten.
   * **Beschreibung (optional):** Geben Sie eine Beschreibung des Briefs als Referenz ein.
   * **Datenwörterbuch (optional)**: Das Datenwörterbuch kann mit der Korrespondenz verknüpft werden. Die Assets, die Sie später in diese Korrespondenz einfügen, sollten entweder dasselbe Datenwörterbuch wie Sie es für die Korrespondenz hier auswählen, oder gar kein Datenwörterbuch enthalten.
   * **Tags (optional)**: Wählen Sie die Tags aus, die auf die Korrespondenz angewendet werden sollen. Sie können auch einen neuen/benutzerdefinierten Tag-Namen eingeben und die Eingabetaste drücken, um ihn zu erstellen.
   * **Nachbearbeitungsprozess (optional)**: Wählen Sie den Nachbearbeitungsprozess aus, die auf die Briefvorlage angewendet werden soll. Es gibt sowohl standardmäßige Nachbearbeitungsprozesse als auch jene, die Sie mithilfe von AEM wie E-Mail und Druck erstellt haben.

   ![Eigenschaften der Korrespondenz](assets/createcorrespondenceproperties.png)

1. Das System zeigt eine Nachricht an: „Brief erfolgreich erstellt.“ Wählen Sie (in der Warnmeldung) **Öffnen** aus, um die darin enthaltenen Datenmodule und Layout-Fragmente zu konfigurieren. Oder wählen Sie **Fertig** aus, um zur vorherigen Seite zurückzukehren.

   ![Warnmeldung: Brief erfolgreich erstellt](assets/createcorrespondencecreated.png)

   **Weiter**: Wenn Sie **Öffnen** auswählen, zeigt das Correspondence Management eine Darstellung des Layouts an, in der alle Komponenten des Layouts (XDP) aufgeführt sind. Fahren Sie mit dem Einfügen und [Konfigurieren von Datenmodulen und Layout-Fragmenten](/help/forms/using/create-letter.md#p-insert-data-modules-and-layout-fragments-in-a-letter-and-configure-them-p) fort.

### Einfügen von Datenmodulen und Layout-Fragmenten in einen Brief mit anschließender Konfiguration {#insert-data-modules-and-layout-fragments-in-a-letter-and-configure-them}

Wenn Sie nach dem Erstellen einer Korrespondenz „Öffnen“ auswählen, zeigt das Correspondence Management eine Darstellung des Layouts an, in der alle Teilformulare/Zielbereiche des Layouts (XDP) aufgelistet sind. Sie können in jeden der Zielbereiche entweder ein Datenmodul oder ein Layout-Fragment (und dann Datenmodule in das Layout-Fragment) einfügen.

>[!NOTE]
>
>Auf der Seite „Briefe“ können Sie auch das Symbol „Bearbeiten“ für einen Brief auswählen, um Datenmodule und Layout-Fragmente in einen Brief einzufügen und sie zu konfigurieren.

1. Wählen Sie für jedes der Teilformulare **Einfügen** und dann Datenmodule oder ein Layout-Fragment zum Einfügen in jedes der Teilformulare aus.

   ![Fügen Sie Datenmodule und Layout-Fragmente ein](assets/insertdmandlf.png)

1. Wählen Sie für diese Optionen für jeweils jedes der Unterformulare „Datenmodul“ oder „Layout-Fragment“ aus und wählen Sie dann die einzufügenden Datenmodule oder Layout-Fragmente aus. Mit einem Layout-Fragment können Sie entsprechend seinem Design weitere Datenmodule oder Layout-Fragmente einfügen (bis zu vier Ebenen).

   ![nestedlf](assets/nestedlf.png)

1. Wenn Sie ein Layout-Fragment einfügen, wird der Name des Layout-Fragments im Teilformular angezeigt. Je nach ausgewähltem Fragment werden verschachtelte Teilformulare im Teilformular angezeigt.
1. Wenn die ausgewählten Datenmodule im Layout eingefügt wurden, können Sie nach dem Tippen auf das Symbol „Bearbeiten“ den Konfigurationsmodus auswählen und für jedes der Module folgende Optionen einstellen:

   1. **Bearbeitbar**: Wenn diese Option aktiviert ist, kann der Inhalt in der Benutzeroberfläche „Korrespondenz erstellen“ bearbeitet werden. Markieren Sie Inhalte nur dann als bearbeitbar, wenn Business-Anwenderinnen und -Anwender (z. B. bei der Schadenregulierung) sie ändern müssen.
   1. **Obligatorisch**: Wenn diese Option aktiviert ist, ist der Inhalt in der Benutzeroberfläche „Korrespondenz erstellen“ erforderlich.
   1. **Ausgewählt**: Wenn diese Option aktiviert ist, wird der Inhalt in der Benutzeroberfläche „Korrespondenz erstellen“ standardmäßig ausgewählt.
   1. **Einzug**: Vergrößern oder verkleinern Sie den Einzug des Moduls/Inhalts im Brief. Einzüge werden in Form von Ebenen angegeben, beginnend bei null. Jede Ebene um 36 Punkte einrücken. Weitere Informationen zum Anpassen von Formularen finden Sie unter **[!UICONTROL Correspondence Management-Konfigurationen]** in [Formular-Workflow](submit-letter-topostprocess.md#formsworkflow).
   1. **Seitenumbruch vor**: Wenn Sie die Option „Seitenumbruch vor“ aktivieren, werden die Inhalte DIESES Moduls immer auf einer neuen Seite angezeigt.
   1. **Seitenumbruch nach**: Wenn Sie für ein bestimmtes Modul die Option „Seitenumbruch nach“ aktivieren, werden die Inhalte des NÄCHSTEN Moduls immer auf einer neuen Seite angezeigt.

   ![Eingefügte Datenmodule und Layout-Fragmente](assets/insertdmandlf2.png)

1. Wählen Sie zum Bearbeiten eines Moduls das Symbol „Bearbeiten“ daneben aus. Wählen Sie nach dem Bearbeiten des Moduls die Option **Speichern** aus.

   Auf dieser Seite können Sie für die Unterformulare auch die folgenden Optionen einstellen:

   1. **Freien Text zulassen**: Wenn die Option „Freien Text zulassen“ aktiviert wird, dann kann der Benutzer in der CCR-Ansicht Inline-Text in einem Brief hinzufügen. In der CCR-Ansicht wird die Aktion „T“ für jene Zielbereiche aktiviert, für die „Freien Text zulassen“ aktiviert wurde. Bei Auswahl wird zur Eingabe des Namens und einer Beschreibung des Textes aufgefordert. Tippt die Person anschließend auf „OK“, wird dieser Text im Bearbeitungsmodus geöffnet, damit sich Text hinzufügen lässt. Das funktioniert wie bei anderen Textmodulen
   1. **Reihenfolge sperren**: Sperrt die Reihenfolge der Unterformulare im Brief. Die Autorin bzw. der Autor darf die Unterformulare/Komponenten beim Erstellen des Briefs nicht neu anordnen.

   Auf dieser Seite können Sie auch für jedes Asset in den Unterformularen folgende Schritte ausführen:

   1. **Reihenfolge der Assets ändern**: Ziehen Sie dazu das Symbol „Neu anordnen“ (![dragndrop](assets/dragndrop.png)) eines Assets per Drag-and-Drop an die gewünschte Stelle.
   1. **Assets löschen**: Wählen Sie neben einem Asset das Symbol „Löschen“ aus, um das Asset zu löschen.
   1. **Vorschau von Assets**: Wählen Sie das Symbol „Vorschau anzeigen“ (![showpreview](assets/showpreview.png)) neben einem Asset aus.

1. Wählen Sie **Weiter** aus.
1. Auf der Seite „Daten“ wird beschrieben, wie Datenfelder und Variablen in der Vorlage verwendet werden. Daten können mit Datenquellen, z. B. einem Datenwörterbuch oder einer Benutzereingabe, verknüpft werden. Jedes Feld definiert Eigenschaften, aus denen Datenwörterbücher Daten zuordnen oder entscheiden, welche Beschriftungen für Benutzereingabefelder angezeigt werden.

   Verknüpfung:

   * Die **Feld**-Elemente können mit einem Literal, einem Datenwörterbuchelement, einem Asset oder einem benutzerdefinierten Wert verknüpft werden. Sie können ein Feldelement auch ignorieren, indem Sie es an die Option „Ignorieren“ binden.
   * Die **Variablen**-Elemente können mit einem Literal, einem Datenwörterbuchelement, einem Feld, einer Variablen, einem Asset oder einem benutzerdefinierten Wert verknüpft werden.

   Nachfolgend finden Sie einige Hauptfelder in der Verknüpfung:

   * **Mehrzeilig**: Sie können angeben, ob die Dateneingabe für ein Feld oder eine Variable mehrzeilig ist. Wenn Sie diese Option auswählen, wird das Eingabefeld für das Feld oder die Variable in der Datenbearbeitungsansicht als mehrzeiliges Eingabefeld angezeigt. Das Feld oder die Variable wird auch in der Daten- und Inhaltsansicht der Benutzeroberfläche „Korrespondenz erstellen“ als mehrzeilige Ansicht angezeigt. Das mehrzeilige Eingabefeld ähnelt dem Feld zur Eingabe von Kommentaren in einem Textmodul. Die Option „Mehrzeilig“ ist nur für Felder und Variablen mit Verbindungstyp „Benutzer“ oder nicht geschützte Datenlexikonelemente verfügbar.
   * **Optional**: Sie können angeben, ob der Wert für Feld oder Variable optional ist oder nicht. Die Option „Optional“ ist für Felder und Variablen mit Verbindungstyp Benutzer oder nicht geschützte Datenlexikonelemente verfügbar.

   * **Validierung des Feldes/der Variablen**: Zur verbesserten Validierung des Werts eines Felds oder einer Variablen können Sie dem Feld bzw. der Variablen einen Validator zuweisen. Die Option ist nur für Felder und Variablen mit Verbindungstyp „Benutzer“ oder nicht geschützte Datenlexikonelemente verfügbar.
   * **Beschriftung** und **QuickInfo**: Beschriftung ist die Beschreibung des Feldes, das in der CCR-Benutzeroberfläche vor dem Feld angezeigt wird. Diese Option ist für Felder und Variablen mit dem Verbindungstyp „Benutzer“ oder ungeschützte Elemente des Datenwörterbuchs verfügbar.

   Für die Felder können folgende Validierungstypen verwendet werden:

   * **Zeichenfolgen-Validierer**: Verwenden Sie den Zeichenfolgen-Validierer, um eine Mindest- und Höchstlänge der in das Feld oder die Variable eingegebenen Zeichenfolge festzulegen. Achten Sie bei der Erstellung eines Zeichenfolgen-Validerers darauf, dass Sie gültige Validierungsparameter angeben. Geben Sie eine gültige Länge für den Mindest- und Höchstwert ein. Für den Zeichenfolgen-Validierer können Sie die Mindest- und Höchstlänge des eingegebenen Werts festlegen. Wenn der eingegebene Wert nicht der angegebenen Mindest- und Höchstlänge entspricht, wird das entsprechende Feld in der CCR-Benutzeroberfläche rot markiert.

   * **Zahlenvalidator:** Verwenden Sie den Zahlenvalidator, um den minimalen und maximalen in ein Feld oder eine Variable eingegebenen numerischen Wert festzulegen. Achten Sie beim Erstellen eines Zahlen-Validierers darauf, dass Sie gültige Validierungsparameter angeben. Geben Sie für Mindest- und Höchstwerte numerische Werte ein.

   * **Regelausdrucks-Validierer**: Verwenden Sie den Regelausdrucks-Validierer, um einen regulären Ausdruck zu definieren, mit dem der Wert eines Felds oder einer Variablen validiert wird. Darüber hinaus können Sie die Fehlermeldung anpassen. Achten Sie beim Erstellen eines Regelausdrucks-Validierers darauf, dass Sie einen gültigen regulären Ausdruck angeben.

   >[!NOTE]
   >
   >Die Feld- und Variablen-Validierer sind nur für Felder oder Variablen mit dem Verbindungstyp „Benutzer“ oder ungeschützte Datenwörterbuchelemente verfügbar.

   ![Verknüpfungen](assets/linkages.png)

1. Wählen Sie nach Angabe der Verknüpfung **Weiter** aus. Correspondence Management zeigt den Anhänge-Bildschirm an.

### Richten Sie die Anlagen ein {#set-up-the-attachments}

1. Wählen Sie **Medienelement hinzufügen**.
1. Wählen Sie im Bildschirm „Asset auswählen“ die Assets aus, die an den Brief angehängt werden sollen, und wählen Sie dann **Fertig** aus. Sie müssen die Anlagen zuerst in „Anlagen“ hochladen“. Es wird empfohlen, dass Sie nur PDF- und Microsoft Office-Dokumente anhängen. Sie können aber auch Bilder anhängen. Weitere Informationen über das Hochladen von Assets in DAM finden Sie unter [Assets hochladen](/help/assets/manage-assets.md).
1. Wenn Sie die Reihenfolge der Assets in der Liste festschreiben möchten, sodass der Schadensregulierer sie nicht ändern kann, wählen Sie **Sperrungsreihenfolge** aus. Wenn Sie diese Option nicht aktivieren, kann der Schadensregulierer die Reihenfolge der Listenelemente ändern.
1. Reihenfolge der Assets ändern: Ziehen Sie ein Assets per Drag and Drop, indem Sie das Symbol „Neu anordnen“ für ein Asset gedrückt halten (![dragndrop](assets/dragndrop.png)).
1. Wählen Sie **Bearbeiten** vor einem Anhang aus und geben Sie einen Anhang als „Obligatorisch“ an, wenn Sie nicht möchten, dass die Autorin oder der Autor diesen löschen kann. Geben Sie eine Anlage als „Ausgewählt“ an, wenn sie in der CCR-Benutzeroberfläche vorausgewählt werden soll.
1. Wählen Sie **Bibliothekszugriff** aus, um Zugriff auf die Bibliothek zu gewähren. Bei Aktivierung des Bibliothekszugriffs kann der Schadensregulierer beim Erstellen eines Briefes auf die Inhaltsbibliothek zugreifen und Anlagen einfügen.
1. Wählen Sie **Anlagenkonfiguration** aus und geben Sie die maximale Anzahl von Anlagen an.

1. Wählen Sie **Speichern** aus. Ihre Korrespondenz wird erstellt und auf der Seite „Briefe“ aufgeführt.

Nachdem in Correspondence Management eine Briefvorlage erstellt wurde, kann der Endbenutzer/Agent/Schadensregulierer den Brief in der CCR-Benutzeroberfläche öffnen und durch Eingabe von Daten, Einrichten von Inhalten und Verwalten von Anlagen eine Korrespondenz erstellen. Weitere Informationen finden Sie unter [Korrespondenz erstellen](/help/forms/using/create-correspondence.md).

## Verknüpfungsarten, die für jedes der Felder verfügbar sind {#types-of-linkage-available-for-each-of-the-fields}

Die folgende Tabelle beschreibt, welche Arten von Verknüpfung für verschiedene Arten von Feldern verfügbar sind.

Die folgenden Werte in der Tabelle

* **Ja:** Feldtyp in der Spalte ganz links unterstützt diesen Typ der Zuordnung
* **Nein:** Feldtyp in der Spalte ganz links unterstützt nicht diesen Typ der Zuordnung
* **Nicht zutreffend**: Feldtyp in der Spalte ganz links ist nicht zutreffend

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>Literal</strong></td> 
   <td><strong>Asset</strong></td> 
   <td><strong>Datenwörterbuch</strong></td> 
   <td><strong>Groß-/Kleinschreibung</strong></td> 
   <td><strong>User</strong></td> 
   <td><strong>Feld</strong></td> 
   <td><strong>Variable</strong></td> 
  </tr> 
  <tr> 
   <td><strong>date</strong></td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>Zeit </strong></td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>datetime</strong></td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>integer</strong></td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja<br /> </td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>float</strong></td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja<br /> </td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>richtext</strong></td> 
   <td>Ja</td> 
   <td>Nur Text</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>plain</strong> <strong>text</strong></td> 
   <td>Ja</td> 
   <td>Nur Text</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>image</strong></td> 
   <td>Nein</td> 
   <td>Nur Bild</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>Signature</strong></td> 
   <td>Nein</td> 
   <td>Nein</td> 
   <td>Nein<br /> </td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Erstellen einer Kopie einer Briefvorlage {#createcopylettertemplate}

Sie können eine Briefvorlage schnell anhand einer vorhandenen Briefvorlage mit ähnlichen Eigenschaften, Inhalten und vererbten Assets, wie Dokumentfragmenten und Datenwörterbüchern, erstellen. Kopieren Sie dazu einen Brief und fügen Sie ihn ein.

1. Wählen Sie auf der Seite „Briefe“ einen oder mehrere Briefe aus. Auf der Benutzeroberfläche wird das Symbol „Kopieren“ angezeigt.
1. Wählen Sie „Kopieren“. Auf der Benutzeroberfläche wird das Symbol „Einfügen“ angezeigt. Sie können vor dem Einfügen auch in einen Ordner wechseln. Verschiedene Ordner können Assets mit demselben Namen enthalten. Weitere Informationen zu Ordnern finden Sie unter [Ordner und Organisieren von Assets](/help/forms/using/import-export-forms-templates.md#folders-and-organizing-assets).
1. Wählen Sie „Einfügen“. Das Dialogfeld „Einfügen“ wird angezeigt. Wenn Sie die Dokumentfragmente kopieren und an derselben Stelle einfügen, weist das System den neuen Briefkopien automatisch Namen und Titel zu, die Sie jedoch ändern können.
1. Bearbeiten Sie ggf. den Titel und den Namen, unter dem Sie die Briefkopie speichern möchten.
1. Wählen Sie „Einfügen“. Die Kopie des Briefes wird erstellt. Jetzt können Sie die erforderlichen Änderungen an Ihrem neu erstellten Brief vornehmen.
