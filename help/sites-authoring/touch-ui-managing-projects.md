---
title: Verwalten von Projekten
description: In „Projekte“ können Sie ein Projekt organisieren, indem Sie Ressourcen zu einer Einheit gruppieren. Der Zugriff und die Verwaltung erfolgen über die Projektekonsole.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: projects
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
exl-id: 53400e3d-542f-4abc-9909-45eb11b0cfcc
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 100%

---

# Verwalten von Projekten {#managing-projects}

In der **Projektekonsole** können Sie Ihre auf Projekte zugreifen und sie verwalten.

![Die Projektekonsole](assets/projects-console.png)

Unter Verwendung der Konsole können Sie ein Projekt erstellen, Ressourcen mit Ihrem Projekt verknüpfen sowie Projekte oder Ressourcenlinks löschen.

## Zugriffsanforderungen {#access-requirements}

„Projekte“ ist eine standardmäßige AEM-Funktion und erfordert keine zusätzliche Einrichtung.

Damit Benutzer in „Projekte“ andere Benutzer/Gruppen sehen können, während sie mit Projektfunktionen wie Erstellen von Projekten, Erstellen von Aufgaben/Workflows, Anzeigen und Verwalten des Teams arbeiten, benötigen sie Lesezugriff auf `/home/users` und `/home/groups`.

Um dies umzusetzen, erteilen Sie am besten der Gruppe **projects-users** Lesezugriff auf `/home/users` und `/home/groups`.

## Erstellen eines Projekts {#creating-a-project}

Gehen Sie wie folgt vor, um ein Projekt zu erstellen.

1. Klicken Sie in der **Projektekonsole** auf **Erstellen**, um den Assistenten zur **Projekterstellung** zu öffnen.
1. Wählen Sie eine Vorlage aus und klicken Sie auf **Weiter**. Weitere Informationen zu den standardmäßigen Projektvorlagen finden Sie [hier](/help/sites-authoring/projects.md#project-templates).

   ![Assistent zur Projekterstellung](assets/create-project-wizard.png)

1. Definieren Sie den **Titel** und die **Beschreibung** und fügen Sie ggf. eine **Miniaturansicht** hinzu. Hier können Sie auch Benutzer und deren Gruppenzugehörigkeit hinzufügen oder löschen.

   ![Schritt „Eigenschaften“ des Assistenten](assets/create-project-wizard-properties.png)

1. Klicken Sie auf **Erstellen**. Daraufhin werden Sie gefragt, ob Sie ein neues Projekt öffnen oder zur Konsole zurückkehren möchten.

Die Vorgehensweise zum Erstellen eines Projekts ist für alle Projektvorlagen identisch. Unterschiede zwischen den Projekttypen gibt es in Bezug auf verfügbare [Benutzerrollen](/help/sites-authoring/projects.md) und [Workflows](/help/sites-authoring/projects-with-workflows.md).

### Zuordnen von Ressourcen zum Projekt {#associating-resources-with-your-project}

„Projekte“ ermöglicht es Ihnen, Ressourcen zu einer Einheit zu gruppieren, um sie insgesamt zu verwalten. Daher müssen Sie Ressourcen mit dem Projekt verknüpfen. Diese Ressourcen werden innerhalb des Projekts als **Kacheln** gruppiert. Die Ressourcentypen, die Sie mit einem Projekt verknüpfen können, werden unter [Projektkacheln](/help/sites-authoring/projects.md#project-tiles) beschrieben.

So ordnen Sie Ihrem Projekt Ressourcen zu:

1. Öffnen Sie das Projekt in der **Projektekonsole**.
1. Klicken Sie auf **Kachel hinzufügen** und wählen Sie die Kachel aus, die mit Ihrem Projekt verknüpft werden soll. Sie können mehrere Arten von Kacheln auswählen.

   ![Kachel hinzufügen](assets/project-add-tile.png)

1. Klicken Sie auf **Erstellen**. Die Ressource wird mit Ihrem Projekt verknüpft und danach können Sie über Ihr Projekt auf sie zugreifen.

### Hinzufügen von Elementen zu einer Kachel {#adding-items-to-a-tile}

In einigen Kacheln benötigen Sie möglicherweise mehr als ein Element. Dies ist zum Beispiel der Fall, wenn Sie mehr als einen gleichzeitig ausgeführten Workflow oder mehr als ein Erlebnis haben.

So fügen Sie einer Kachel Elemente hinzu:

1. Navigieren Sie in **Projekte** zum Projekt, klicken Sie oben rechts in der Kachel, der Sie ein Element hinzufügen möchten, auf das Pfeilsymbol nach unten und wählen Sie die entsprechende Option aus.

   * Die Option hängt vom Typ der Kachel ab. Zum Beispiel kann dies **Aufgabe erstellen** für die Kachel **Aufgaben** oder **Workflow starten** für die Kachel **Workflows** sein.

   ![Kachel-Chevron](assets/project-tile-create-task.png)

1. Fügen Sie der Kachel auf dieselbe Weise ein Element hinzu wie bei der Erstellung einer Kachel. Projektkacheln werden [hier](/help/sites-authoring/projects.md#project-tiles) beschrieben.

## Anzeigen von Projektinformationen {#viewing-project-info}

Der Hauptzweck von Projekten besteht darin, verknüpfte Informationen an einem Ort zu gruppieren, um sie leichter zugänglich und umsetzbar zu machen. Sie haben verschiedene Möglichkeiten, auf diese Informationen zuzugreifen.

### Öffnen einer Kachel {#opening-a-tile}

Manchmal kann es nötig sein zu wissen, welche Elemente in einer aktuellen Kachel enthalten sind, oder die Elemente in einer Kachel zu ändern oder zu löschen.

Dazu öffnen Sie die Kachel, sodass Sie ihre Elemente anzeigen und ändern können:

1. Klicken Sie unten rechts auf der Kachel auf das Symbol mit den Auslassungspunkten.

   ![Aufgabenkachel](assets/project-tile-tasks.png)

1. AEM öffnet die Konsole für die Typen von Elementen, die mit der Kachel verknüpft sind, und Filtern, die auf dem ausgewählten Projekt basieren.

   ![Projektaufgaben](assets/project-tasks.png)

### Anzeigen einer Projekt-Zeitleiste {#viewing-a-project-timeline}

Die Projekt-Zeitleiste enthält Informationen dazu, wann Assets des Projekts zuletzt verwendet wurden. Gehen Sie wie folgt vor, um die Projekt-Zeitleiste anzuzeigen.

1. Klicken Sie in der **Projektekonsole** in der Leistenauswahl oben links auf **Timeline**.
   ![Auswahl des Zeitleisten-Modus](assets/projects-timeline-rail.png)
2. Wählen Sie in der Konsole das Projekt aus, dessen Zeitleiste Sie anzeigen möchten.
   ![Projekt-Zeitleisten-Ansicht](assets/project-timeline-view.png)

Assets werden in der Leiste angezeigt. Verwenden Sie die Leistenauswahl, um nach Abschluss zur normalen Ansicht zurückzukehren.

### Anzeigen inaktiver Projekte {#viewing-active-inactive-projects}

Um zwischen aktiven und [inaktiven Projekten](#making-projects-inactive-or-active) zu wechseln, klicken Sie in der **Projektekonsole** auf das Symbol **Aktive Projekte ein/aus.** In der Symbolleiste,

![Symbol „Aktive Projekte ein/aus“](assets/projects-toggle-active.png)

Standardmäßig zeigt die Konsole aktive Projekte an. Klicken Sie auf das Symbol **Aktive Projekte ein/aus**, um zur Ansicht inaktiver Projekte zu wechseln. Klicken Sie erneut darauf, um zu aktiven Projekten zurückzukehren.

## Organisieren von Projekten {#organizing-projects}

Es stehen mehrere Optionen zur Verfügung, um Ihre Projekte zu organisieren und die **Projektekonsole** übersichtlich zu halten.

### Projektordner {#project-folders}

In der **Projektekonsole** können Sie Ordner erstellen, um ähnliche Projekte zu gruppieren und zu organisieren.

1. Klicken in der **Projektekonsole** auf **Erstellen** und anschließend auf **Ordner erstellen**.

   ![Ordner erstellen](assets/project-create-folder.png)

1. Geben Sie dem Ordner einen Titel und klicken Sie auf **Erstellen**.

1. Der Ordner wird der Konsole hinzugefügt.

Sie können jetzt Projekte im Ordner erstellen. Sie können mehrere Ordner erstellen und sie auch verschachteln.

### Inaktivieren von Projekten {#making-projects-inactive-or-active}

Sie können ein Projekt als inaktiv markieren, wenn Sie es abgeschlossen haben, aber die Informationen über das Projekt beibehalten möchten. [Inaktive Projekte werden jetzt](#viewing-active-inactive-projects) standardmäßig in der **Projektekonsole** angezeigt.

Gehen Sie wie folgt vor, um ein Projekt inaktiv zu machen.

1. Öffnen Sie das Fenster **Projekteigenschaften** des Projekts.
   * Sie können dies über die Konsole tun, indem Sie das Projekt auswählen oder innerhalb des Projekts über die Kachel **Projektinformationen**.
1. Bewegen sie im Fenster **Projekteigenschaften** den Schieberegler **Projektstatus** von **Aktiv** zu **Inaktiv**.

   ![Projektstatusauswahl im Fenster „Eigenschaften“](assets/project-status.png)

1. Klicken Sie auf **Speichern und schließen**, um die Änderungen zu speichern.

### Löschen von Projekten {#deleting-a-project}

Gehen Sie wie folgt vor, um ein Projekt zu löschen.

1. Gehen Sie zur obersten Ebene der **Projektekonsole**.
1. Wählen Sie Ihr Projekt in der Konsole aus.
1. Klicken Sie in der Symbolleiste auf **Löschen**.
1. AEM kann die zugehörigen Projektdaten beim Löschen des Projekts entfernen/ändern. Wählen Sie die gewünschten Optionen im Dialogfenster **Projekt löschen** aus.
   * Projektgruppen und -rollen entfernen
   * Projekt-Asset-Ordner löschen
   * Projekt-Workflows beenden

   ![Optionen zum Löschen von Projekten](assets/project-delete-options.png)
1. Klicken Sie auf **Löschen**, um das Projekt mit den ausgewählten Optionen zu löschen.

Weitere Einzelheiten zu automatisch von Projekten erstellten Gruppen finden Sie unter [Automatische Gruppenerstellung](/help/sites-authoring/projects.md#auto-group-creation).
