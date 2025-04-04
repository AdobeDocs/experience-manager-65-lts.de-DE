---
title: Übersetzen von Inhalten
description: Verwenden Sie den Übersetzungs-Connector und die Regeln, um Ihre Headless-Inhalte zu übersetzen.
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,Language Copy
role: Admin, Architect,Data Architect,Developer,User,Leader
exl-id: 13d11e2b-5a3f-4987-a653-14e0790fbbd0
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '2115'
ht-degree: 100%

---

# Übersetzen von Inhalten {#translate-content}

Verwenden Sie die Übersetzungsintegration und -regeln, um Ihre Headless-Inhalte zu übersetzen.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Headless-Übersetzungs-Tour, [Konfigurieren von Übersetzungsregeln](translation-rules.md), haben Sie gelernt, wie Sie die Übersetzungsregeln von AEM verwenden, um Ihre zu übersetzenden Inhalte zu bestimmen. Sie sollten jetzt:

* Verstehen, was die Übersetzungsregeln bewirken.
* Eigene Übersetzungsregeln definieren können.

Nachdem Sie nun Ihren Connector und Ihre Übersetzungsregeln eingerichtet haben, führt Sie dieser Artikel durch den nächsten Schritt der Übersetzung Ihrer Headless-Inhalte.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie AEM-Übersetzungsprojekte zusammen mit dem Connector und Ihren Übersetzungsregeln verwenden können, um Inhalte zu übersetzen. Nach dem Lesen dieses Dokuments sollten Sie zu Folgendem in der Lage sein:

* Verstehen, was ein Übersetzungsprojekt ist.
* Erstellen von Übersetzungsprojekten.
* Übersetzungsprojekte verwenden können, um Ihre Headless-Inhalte zu übersetzen.

## Erstellen eines Übersetzungsprojekts {#creating-translation-project}

Mithilfe von Übersetzungsprojekten können Sie die Übersetzung von AEM Headless-Inhalten verwalten. Ein Übersetzungsprojekt sammelt die Inhalte, die in andere Sprachen übersetzt werden sollen, an einem Ort, um einen zentralen Überblick über den Übersetzungsaufwand zu erhalten.

Wenn einem Übersetzungsprojekt Inhalte hinzugefügt werden, wird ein Übersetzungsauftrag für sie erstellt. Aufträge beinhalten Befehle und Statusinformationen, mit denen Sie die Workflows für menschliche und maschinelle Übersetzungen, die für die Ressourcen ausgeführt werden, verwalten.

Übersetzungsprojekte können auf zwei Arten erstellt werden:

1. Wählen Sie den Sprachstamm des Inhalts aus und lassen Sie AEM das Übersetzungsprojekt automatisch basierend auf dem Inhaltspfad erstellen.
1. Erstellen Sie ein leeres Projekt und wählen Sie manuell die Inhalte aus, die zum Übersetzungsprojekt hinzugefügt werden sollen.

Beide Ansätze sind zulässig und unterscheiden sich nur abhängig von der Rolle, die die Übersetzung durchführt:

* Der Übersetzungsprojekt-Manager (TPM) benötigt häufig die Flexibilität, die Inhalte manuell für das Übersetzungsprojekt auszuwählen.
* Wenn der Inhaltsverantwortliche auch für die Übersetzung verantwortlich ist, ist es oft einfacher, das Projekt anhand des ausgewählten Inhaltspfads automatisch von AEM erstellen zu lassen.

Auf beide Ansätze wird in den folgenden Abschnitten eingegangen.

### Automatisches Erstellen eines Übersetzungsprojekts basierend auf dem Inhaltspfad {#automatically-creating}

Für Inhaltsverantwortliche, die auch für die Übersetzung verantwortlich ist, ist es oft einfacher, das Projekt anhand des ausgewählten Inhaltspfads automatisch von AEM erstellen zu lassen. Gehen Sie wie folgt vor, um von AEM automatisch ein Übersetzungsprojekt auf der Grundlage Ihres Inhaltspfads erstellen zu lassen:

1. Gehen Sie zu **Navigation** > **Assets** > **Dateien**. Beachten Sie, dass Headless-Inhalte in AEM als Assets gespeichert werden. Diese werden auch als Inhaltsfragmente bezeichnet.
1. Wählen Sie den Sprachstamm Ihres Projekts aus. In diesem Fall wird `/content/dam/wknd/en` ausgewählt.
1. Klicken Sie auf die Leistenauswahl und zeigen Sie das Bedienfeld **Verweise** an.
1. Klicken Sie auf **Sprachkopien**.
1. Aktivieren Sie das Kontrollkästchen **Sprachkopien**.
1. Erweitern Sie den Abschnitt **Sprachkopien aktualisieren** unten im Bereich „Verweise“.
1. Wählen Sie in der Dropdown-Liste **Projekt** die Option **Übersetzungsprojekt(e) erstellen** aus.
1. Geben Sie einen passenden Titel für Ihr Übersetzungsprojekt an.
1. Klicken Sie auf **Starten**.

![Erstellen eines Übersetzungsprojekts](assets/create-translation-project.png)

Sie erhalten eine Nachricht, dass das Projekt erstellt wurde.

>[!NOTE]
>
>Es wird davon ausgegangen, dass die erforderliche Sprachstruktur für die Übersetzungssprachen bereits im Rahmen der [Definition Ihrer Inhaltsstruktur erstellt wurde.](getting-started.md#content-structure) Dies sollte in Zusammenarbeit mit dem Inhaltsarchitekten erfolgen.
>
>Wenn die Sprachordner nicht vorab erstellt werden, können Sie keine Sprachkopien, wie in den vorherigen Schritten beschrieben, erstellen.

### Manuelles Erstellen eines Übersetzungsprojekts durch Auswahl von Inhalten {#manually-creating}

Für Übersetzungsprojekt-Manager ist es oft erforderlich, bestimmte Inhalte, die in ein Übersetzungsprojekt aufgenommen werden sollen, manuell auszuwählen. Um ein solches manuelles Übersetzungsprojekt zu erstellen, müssen Sie zunächst ein leeres Projekt erstellen und dann die hinzuzufügenden Inhalte auswählen.

1. Navigieren Sie zu **Navigation** > **Projekte**.
1. Klicken Sie auf **Erstellen** > **Ordner**, um einen Ordner für Ihre Projekte zu erstellen.
   * Dies ist optional, aber hilfreich, um Ihre Übersetzungsarbeit zu organisieren.
1. Fügen Sie im Fenster **Ordner erstellen** einen **Titel** für den Ordner hinzu und klicken Sie dann auf **Erstellen**.

   ![Erstellen von Projektordnern](assets/create-project-folder.png)

1. Klicken Sie auf den Ordner, um ihn zu öffnen.
1. Klicken Sie in Ihrem neuen Projektordner auf **Erstellen** > **Projekt**.
1. Projekte basieren auf Vorlagen. Klicken Sie auf die Vorlage **Übersetzungsprojekt**, um diese auszuwählen, und dann auf **Weiter**.

   ![Übersetzungsprojektvorlage auswählen](assets/select-translation-project-template.png)

1. Geben Sie in der Registerkarte **Allgemein** einen Namen für Ihr neues Projekt ein.

   ![Registerkarte „Allgemein“ des Projekts](assets/project-basic-tab.png)

1. Verwenden Sie auf der Registerkarte **Erweitert** die Dropdown-Liste **Zielsprache**, um die Sprachen auszuwählen, in die der Inhalt übersetzt werden soll. Klicken Sie auf **Erstellen**.

   ![Registerkarte „Erweitert“ des Projekts](assets/project-advanced-tab.png)

1. Klicken Sie im Bestätigungsdialog auf **Öffnen**.

   ![Bestätigungsdialogfeld für das Projekt](assets/project-confirmation-dialog.png)

Das Projekt wurde erstellt, enthält jedoch keine zu übersetzenden Inhalte. Im nächsten Abschnitt wird beschrieben, wie das Projekt strukturiert ist und wie Inhalte hinzugefügt werden.

## Verwenden eines Übersetzungsprojekts {#using-translation-project}

Übersetzungsprojekte dienen dazu, alle Inhalte und Aufgaben im Zusammenhang mit einer Übersetzung zentral zu erfassen, damit die Übersetzung einfach verwaltet werden kann.

So zeigen Sie das Übersetzungsprojekt an:

1. Navigieren Sie zu **Navigation** > **Projekte**.
1. Klicken Sie auf das Projekt, das im vorherigen Abschnitt erstellt wurde.

![Übersetzungsprojekt](assets/translation-project.png)

Das Projekt ist in mehrere Karten unterteilt.

* **Zusammenfassung**: Diese Karte zeigt die grundlegenden Kopfzeileninformationen des Projekts, einschließlich des Verantwortlichen, der Sprache und des Übersetzungsdienstleisters.
* **Übersetzungsauftrag**: Diese Karte bzw. diese Karten bieten einen Überblick über den tatsächlichen Übersetzungsauftrag, einschließlich Status, Anzahl der Assets usw. Im Allgemeinen gibt es pro Sprache einen Auftrag, wobei der ISO-2-Sprach-Code an den Auftragsnamen angehängt wird.
* **Team**: Auf dieser Karte werden die Benutzer angezeigt, die an diesem Übersetzungsprojekt mitarbeiten. Diese Tour behandelt dieses Thema nicht.
* **Aufgaben**: Zusätzliche Aufgaben im Zusammenhang mit der Übersetzung der Inhalte, z. B. zum Erstellen von Elementen oder Workflow-Elementen. Diese Tour behandelt dieses Thema nicht.

Wie Sie ein Übersetzungsprojekt verwenden, hängt davon ab, wie es erstellt wurde: entweder automatisch durch AEM oder manuell.

### Verwenden eines automatisch erstellten Übersetzungsprojekts {#using-automatic-project}

Beim automatischen Erstellen des Übersetzungsprojekts bewertet AEM die Headless-Inhalte unter dem von Ihnen ausgewählten Pfad anhand der zuvor definierten Übersetzungsregeln. Basierend auf dieser Auswertung extrahiert es die Inhalte, die übersetzt werden müssen, in ein neues Übersetzungsprojekt.

So sehen Sie die Details der Headless-Inhalte in diesem Projekt:

1. Klicken Sie unten auf der Karte **Übersetzungsauftrag** auf die Schaltfläche mit den Auslassungspunkten.
1. Im Fenster **Übersetzungsauftrag** werden alle Elemente des Auftrags aufgelistet.
   ![Detail des Übersetzungsauftrags](assets/translation-job-detail.png)
1. Klicken Sie auf eine Zeile, um ihre Details anzuzeigen. Dabei ist zu beachten, dass eine Zeile mehrere zu übersetzende Inhaltselemente darstellen kann.
1. Aktivieren Sie das Kontrollkästchen für ein Zeilenelement, um weitere Optionen anzuzeigen, z. B. um das Element aus dem Auftrag zu löschen oder in der Inhaltsfragment- oder Assets-Konsole anzuzeigen.
   ![Optionen für Übersetzungsaufträge](assets/translation-job-options.png)

Normalerweise beginnt der Inhalt des Übersetzungsauftrags im Status **Entwurf**, wie in der Spalte **Status** im Fenster **Übersetzungsauftrag** angegeben.

Um den Übersetzungsauftrag zu starten, kehren Sie zur Übersicht des Übersetzungsprojekts zurück, klicken Sie auf die Pfeil-Schaltfläche oben auf der Karte **Übersetzungsauftrag** und wählen Sie **Starten** aus.

![Übersetzungsauftrag starten](assets/start-translation-job.png)

AEM kommuniziert nun mit Ihrer Übersetzungskonfiguration und dem Connector, um den Inhalt an den Übersetzungsdienstleister zu senden. Sie können den Fortschritt der Übersetzung verfolgen, indem Sie zum Fenster **Übersetzungsauftrag** zurückkehren und in der Spalte **Status** der Einträge nachsehen.

![Übersetzungsauftrag genehmigt](assets/translation-job-approved.png)

Maschinelle Übersetzungen werden automatisch mit dem Status **Genehmigt** zurückgegeben. Menschliche Übersetzung ermöglicht mehr Interaktion, sprengt aber den Rahmen dieser Tour.

### Verwenden eines manuell erstellten Übersetzungsprojekts {#using-manual-project}

Beim manuellen Erstellen eines Übersetzungsprojekts erstellt AEM die erforderlichen Aufträge, wählt jedoch nicht automatisch die einzuschließenden Inhalte aus. Dadurch kann der Übersetzungsprojekt-Manager flexibel entscheiden, welche Inhalte übersetzt werden sollen.

So fügen Sie einem Übersetzungsauftrag Inhalte hinzu:

1. Klicken Sie unten auf einer der Karten **Übersetzungsauftrag** auf die Schaltfläche mit den Auslassungspunkten.
1. Sie sehen, dass der Auftrag keinen Inhalt enthält. Klicken Sie oben im Fenster auf die Schaltfläche **Hinzufügen** und wählen Sie dann aus der Dropdown-Liste die Option **Assets/Seiten** aus.

   ![Leerer Übersetzungsauftrag](assets/empty-translation-job.png)

1. Ein Pfad-Browser wird geöffnet, in dem Sie auswählen können, welche Inhalte hinzugefügt werden sollen. Suchen Sie die gewünschten Inhalte und klicken Sie zur Auswahl darauf.

   ![Pfad-Browser](assets/path-browser.png)

1. Klicken Sie auf **Auswählen**, um die ausgewählten Inhalte zum Auftrag hinzuzufügen.
1. Geben Sie im Dialogfeld **Übersetzen** an, dass Sie eine **Sprachkopie erstellen** möchten.

   ![Sprachkopie erstellen](assets/translate-copy-master.png)

1. Der Inhalt ist jetzt im Auftrag enthalten.

   ![Zum Übersetzungsauftrag hinzugefügte Inhalte](assets/content-added.png)

1. Aktivieren Sie das Kontrollkästchen für ein Zeilenelement, um weitere Optionen anzuzeigen, z. B. um das Element aus dem Auftrag zu löschen oder in der Inhaltsfragment- oder Assets-Konsole anzuzeigen.
   ![Optionen für Übersetzungsaufträge](assets/translation-job-options-manual.png)

1. Wiederholen Sie diese Schritte, um alle erforderlichen Inhalte in den Auftrag einzuschließen.

>[!TIP]
>
>Der Pfad-Browser ist ein leistungsstarkes Tool, mit dem Sie Inhalte suchen, filtern und darin navigieren können. Klicken Sie auf die Schaltfläche **Nur Inhalt/Filter**, um das seitliche Bedienfeld ein-/auszuschalten und erweiterte Filter wie **Änderungsdatum** oder **Übersetzungsstatus** einzublenden.
>
>Weitere Informationen zum Pfad-Browser finden Sie im [Abschnitt mit zusätzlichen Ressourcen](#additional-resources).

Sie können die vorherigen Schritte verwenden, um die erforderlichen Inhalte zu allen Sprachen (Aufträgen) für das Projekt hinzuzufügen. Nachdem Sie alle Inhalte ausgewählt haben, können Sie mit der Übersetzung beginnen.

Normalerweise beginnt der Inhalt des Übersetzungsauftrags im Status **Entwurf**, wie in der Spalte **Status** im Fenster **Übersetzungsauftrag** angegeben.

Um den Übersetzungsauftrag zu starten, kehren Sie zur Übersicht des Übersetzungsprojekts zurück, klicken Sie auf die Pfeil-Schaltfläche oben auf der Karte **Übersetzungsauftrag** und wählen Sie **Starten** aus.

![Übersetzungsauftrag starten](assets/start-translation-job-manual.png)

AEM kommuniziert nun mit Ihrer Übersetzungskonfiguration und dem Connector, um den Inhalt an den Übersetzungsdienstleister zu senden. Sie können den Fortschritt der Übersetzung verfolgen, indem Sie zum Fenster **Übersetzungsauftrag** zurückkehren und in der Spalte **Status** der Einträge nachsehen.

![Übersetzungsauftrag genehmigt](assets/translation-job-approved-manual.png)

Maschinelle Übersetzungen werden automatisch mit dem Status **Genehmigt** zurückgegeben. Menschliche Übersetzung ermöglicht mehr Interaktion, sprengt aber den Rahmen dieser Tour.

## Überprüfen übersetzter Inhalte {#reviewing}

[Wie bereits erwähnt,](#using-translation-project) fließen maschinell übersetzte Inhalte mit dem Status **Genehmigt** zurück nach AEM, da davon ausgegangen wird, dass aufgrund der maschinellen Übersetzung kein menschliches Eingreifen erforderlich ist. Aber es ist noch möglich, die übersetzten Inhalte zu überprüfen.

Wechseln Sie einfach zum abgeschlossenen Übersetzungsauftrag und wählen Sie ein Zeilenelement aus, indem Sie auf das Kontrollkästchen tippen oder klicken. Das Symbol **In Inhaltsfragment anzeigen** wird in der Symbolleiste angezeigt.

![In Inhaltsfragment anzeigen](assets/reveal-in-content-fragment.png)

Klicken Sie auf dieses Symbol, um das übersetzte Inhaltsfragment in der Editorkonsole zu öffnen und die Details zu den übersetzten Inhalten anzuzeigen.

![Ein übersetztes Inhaltsfragment](assets/translated-content-fragment.png)

Sie können das Inhaltsfragment nach Bedarf weiter ändern, vorausgesetzt Sie verfügen über die entsprechenden Berechtigungen, aber die Bearbeitung von Inhaltsfragmenten sprengt den Rahmen dieser Tour. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments.

Ziel des Projekts ist es, alle Ressourcen, die mit einer Übersetzung verbunden sind, an einem Ort zu sammeln, um einen einfachen Zugriff und einen klaren Überblick zu erhalten. Wie Sie jedoch sehen können, indem Sie die Details eines übersetzten Elements anzeigen, fließen die Übersetzungen selbst in den Asset-Ordner der Übersetzungssprache zurück. In diesem Beispiel lautet der Ordner:

```text
/content/dam/wknd/es
```

Wenn Sie über **Navigation** > **Assets** > **Dateien** zu diesem Ordner navigieren, sehen Sie die übersetzten Inhalte.

![Struktur von Ordnern mit übersetzten Inhalten](assets/translated-file-content.png)

Das Übersetzungs-Framework von AEM erhält die Übersetzungen vom Übersetzungs-Connector und erstellt dann automatisch die Inhaltsstruktur, basierend auf dem Sprachstamm und unter Verwendung der vom Connector bereitgestellten Übersetzungen.

Es ist wichtig zu verstehen, dass diese Inhalte nicht veröffentlicht werden und daher nicht für Ihre Headless-Services verfügbar sind. Im nächsten Schritt der Übersetzungs-Tour lernen Sie diese Autoren- und Veröffentlichungstruktur kennen und erfahren, wie übersetzte Inhalte veröffentlicht werden.

## Menschliche Übersetzung {#human-translation}

Wenn Ihr Übersetzungsdienstleister menschliche Übersetzung bereitstellt, bietet der Überprüfungsprozess mehr Optionen. Übersetzungen gelangen beispielsweise mit dem Status **Entwurf** zurück in das Projekt und müssen manuell überprüft und genehmigt oder abgelehnt werden.

Die menschliche Übersetzung sprengt den Rahmen dieser Tour zur Lokalisierung. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments. Abgesehen von den zusätzlichen Genehmigungsoptionen ist der Workflow für menschliche Übersetzungen mit dem für maschinelle Übersetzungen identisch, wie in dieser Tour beschrieben.

## So geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der Headless-Übersetzungs-Tour abgeschlossen haben, sollten Sie zu Folgendem in der Lage sein:

* Verstehen, was ein Übersetzungsprojekt ist.
* Erstellen von Übersetzungsprojekten.
* Übersetzungsprojekte verwenden können, um Ihre Headless-Inhalte zu übersetzen.

Bauen Sie auf diesem Wissen auf und setzen Sie Ihre AEM Headless-Übersetzungs-Journey fort, indem Sie als Nächstes das Dokument [Übersetzte Inhalte veröffentlichen](publish-content.md) lesen. Dort lernen Sie, wie Sie übersetzte Inhalte veröffentlichen und wie Sie diese Übersetzungen aktualisieren, wenn sich die Inhalte Ihres Sprachstamms ändern.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, zum nächsten Teil der Headless-Übersetzungs-Tour voranzuschreiten, indem Sie das Dokument [Veröffentlichen übersetzter Inhalte](publish-content.md) lesen. Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige in diesem Dokument erwähnte Konzepte vertiefen. Aber sie sind nicht erforderlich, um mit der Headless-Tour fortzufahren.

* [Verwalten von Übersetzungsprojekten](/help/sites-administering/tc-manage.md) – Erfahren Sie mehr über die Einzelheiten von Übersetzungsprojekten und über zusätzliche Funktionen wie Workflows für menschliche Übersetzung und mehrsprachige Projekte.
* [Autorenumgebung und Tools](/help/sites-authoring/author-environment-tools.md#path-selection) – AEM bietet verschiedene Mechanismen für die Organisation und Bearbeitung von Inhalten, einschließlich eines robusten Pfad-Browsers.
