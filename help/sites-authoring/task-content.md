---
title: Arbeiten mit Aufgaben
description: Aufgaben stellen zu erledigende Arbeiten am Inhalt dar und werden in Projekten verwendet, um den Grad der Vollständigkeit der laufenden Aufgaben zu bestimmen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: projects
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
exl-id: 852aaf6e-acf3-4224-bf4c-c0913110abd4
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 100%

---

# Arbeiten mit Aufgaben {#working-with-tasks}

Aufgaben stellen inhaltlich zu erledigende Arbeiten dar. Wenn Ihnen eine Aufgabe zugewiesen wird, wird diese in Ihrem Workflow-Posteingang angezeigt. Aufgabenelemente können von Workflow-Elementen durch den Wert der Spalte **Typ** unterschieden werden.

Aufgaben werden auch in Projekten verwendet, um den Grad der Vollständigkeit des Projekts zu bestimmen.

## Verfolgen des Projektfortschritts {#tracking-project-progress}

Sie können den Projektfortschritt verfolgen, indem Sie sich die aktiven/abgeschlossenen Aufgaben innerhalb eines Projekts ansehen, das durch die Kachel **Aufgaben** dargestellt wird. Der Projektfortschritt kann durch Folgendes bestimmt werden:

* **Aufgabenkachel:** Ein Gesamtfortschritt des Projekts wird in der Aufgabenkachel dargestellt, die auf der Seite „Projektdetails“ zu sehen ist.

* **Aufgabenliste:** Beim Klicken auf die Aufgabenkachel wird eine Liste von Aufgaben angezeigt. Diese Liste enthält detaillierte Informationen zu allen Aufgaben in Zusammenhang mit dem Projekt.

Bei beiden Optionen werden sowohl Workflow-Aufgaben als auch Aufgaben, die Sie direkt auf der Aufgabenkachel erstellen, aufgelistet.

### Aufgabenkachel {#task-tile}

Wenn ein Projekt zugehörige Aufgaben hat, wird eine Aufgabenkachel innerhalb des Projekts angezeigt. Die Aufgabenkachel zeigt den aktuellen Status des Projekts an. Die Anzeige basiert auf den vorhandenen Aufgaben innerhalb des Workflows und beinhaltet keine Aufgaben, die in der Zukunft erzeugt werden, während der Workflow fortgesetzt wird. Die folgenden Informationen sind in der Aufgabenkachel sichtbar:

* Prozentsatz der abgeschlossenen Aufgaben
* Prozentsatz der aktiven Aufgaben
* Prozentsatz der überfälligen Aufgaben

![Aufgabenkachel](assets/project-tile-tasks.png) 

### Anzeigen oder Ändern von Aufgaben in einem Projekt {#viewing-or-modifying-the-tasks-in-a-project}

Zusätzlich zur Verfolgung des Fortschritts möchten Sie vielleicht auch Informationen über das Projekt anzeigen oder es ändern.

#### Aufgabenliste {#task-list}

Klicken Sie unten rechts in der Aufgabenkachel auf die Schaltfläche mit Auslassungspunkten, um den Posteingang anzuzeigen, der nach den mit dem Projekt verbundenen Aufgaben gefiltert wurde. Die Aufgabendetails werden zusammen mit Metadaten wie Fälligkeitsdatum, Verantwortlicher, Priorität und Status angezeigt.

![Posteingang für Projektaufgaben](assets/project-tasks.png)

#### Aufgabendetails {#task-details}

Um weitere Informationen zu einer bestimmten Aufgabe zu erhalten, klicken Sie im Posteingang auf die Aufgabe, um sie auszuwählen, oder klicken Sie in der Symbolleiste auf **Öffnen**.

![Aufgabendetails](assets/project-task-detail.png)

Über verschiedene Registerkarten können Sie Details der Aufgabe anzeigen, bearbeiten oder hinzufügen.

* **Aufgabe**: Allgemeine Informationen zu Aufgaben
* **Projektinformationen**:Zusammenfassung des Projekts, mit dem die Aufgabe verknüpft ist
* **Workflow-Info**:- Zusammenfassung des Workflows, mit dem die Aufgabe verknüpft ist (falls zutreffend)
* **Kommentare**: Allgemeine Anmerkungen zur Aufgabe selbst

### Hinzufügen von Aufgaben {#adding-tasks}

Sie können neue Aufgaben zu Projekten hinzufügen. Diese Aufgaben werden dann in der Aufgabenkachel angezeigt und stehen im Benachrichtigungs-Posteingang zur Verfügung, damit Sie über Ihre noch ausstehenden Aufgaben informiert sind.

So fügen Sie eine Aufgabe hinzu:

1. Suchen Sie im Projekt die Kachel **Aufgaben**.
1. Klicken Sie oben rechts auf der Kachel auf den nach unten gerichteten Pfeil und wählen Sie **Aufgabe erstellen** aus.
1. Geben Sie im Fester **Aufgabe hinzufügen** Aufgabendetails wie Priorität, Beauftragter und Fälligkeitsdatum an.

   ![Hinzufügen einer Aufgabe](assets/project-add-task.png)

1. Klicken Sie auf **Absenden**.

## Arbeiten mit Aufgaben im Posteingang {#working-with-tasks-in-the-inbox}

Anstatt über das Projekt selbst auf Ihre Projektaufgaben zuzugreifen, können Sie direkt über Ihren Posteingang darauf zugreifen. Ihr Posteingang gibt Ihnen einen Überblick über Ihre Aufgaben in allen Projekten, damit Sie Ihren gesamten Workflow verstehen können.

Im Posteingang können Sie die Aufgaben öffnen und den Aufgabenstatus festlegen. Aufgaben werden auch in Ihrem Posteingang angezeigt, wenn sie einer Benutzergruppe zugewiesen werden, der Sie angehören. In diesem Fall kann jedes Mitglied der Gruppe die Arbeit durchführen und die Aufgabe abschließen.

![Posteingang](assets/project-inbox.png)

Um eine Aufgabe abzuschließen, wählen Sie die Aufgabe aus und klicken Sie in der Symbolleiste auf **Abschließen**. Fügen Sie Informationen zur Aufgabe hinzu und klicken Sie auf **Fertig**. In Ihrem [Posteingang](/help/sites-authoring/inbox.md) finden Sie weitere Informationen.
