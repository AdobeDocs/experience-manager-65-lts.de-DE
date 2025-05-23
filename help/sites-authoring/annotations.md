---
title: Anmerkungen beim Bearbeiten einer Inhaltsseite
description: Viele direkt auf den Inhalt bezogene Komponenten erlauben die Hinzufügung von Anmerkungen.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
exl-id: 5e0e7d8e-4da2-4304-ac21-7500ca2ba9c6
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 100%

---

# Anmerkungen beim Bearbeiten einer Seite{#annotations-when-editing-a-page}

Oft muss das Hinzufügen von Inhalten zu den Seiten Ihrer Website vor der tatsächlichen Veröffentlichung besprochen werden. Um diesen Vorgang zu erleichtern, können Sie in vielen Komponenten, die direkt mit Inhalt (und nicht mit dem Layout) in Verbindung stehen, Anmerkungen hinzufügen.

Bei einer Anmerkung wird eine farbige Markierung/Haftnotiz auf der Seite platziert. Mit einer Anmerkung können Sie (oder andere Benutzer) Kommentare und/oder Fragen für andere Autoren/Prüfer hinterlassen.

>[!NOTE]
>
>Die Definition einer einzelnen Komponente bestimmt, ob Anmerkungen in Instanzen dieser Komponente möglich sind oder nicht.

>[!NOTE]
>
>In der klassischen Benutzeroberfläche erstellte Anmerkungen werden in der Touch-optimierten Benutzeroberfläche angezeigt. Skizzen sind jedoch benutzeroberflächenspezifisch und werden nur in der Benutzeroberfläche angezeigt, in der sie erstellt wurden.

>[!CAUTION]
>
>Durch Löschen einer Ressource (z. B. eines Absatzes) werden alle Anmerkungen und Zeichnungen gelöscht, die mit dieser Ressource verbunden sind (unabhängig von ihrer Position auf der Seite als Ganzes).

>[!NOTE]
>
>Je nach Ihren Anforderungen können Sie auch einen Workflow erstellen, damit Benachrichtigungen gesendet werden, wenn Anmerkungen hinzugefügt, aktualisiert oder gelöscht werden.

## Anmerkungen {#annotations}

Zum Erstellen und Ansehen von Anmerkungen wird ein spezieller [Modus](/help/sites-authoring/author-environment-tools.md#page-modes) verwendet.

>[!NOTE]
>
>Denken Sie daran, dass Sie auch mithilfe von [Kommentaren](/help/sites-authoring/basic-handling.md#timeline) Feedback zu einer Seite geben können.

>[!NOTE]
>
>Sie können Anmerkungen zu einer Vielzahl von Ressourcen anfügen: 
>
>* [Anmerkungen zu Assets](/help/assets/manage-assets.md#annotating)
>* [Kommentieren von Video-Assets](/help/assets/managing-video-assets.md#annotate-video-assets)
>

### Hinzufügen von Anmerkungen zu Komponenten {#annotating-a-component}

Im Anmerkungsmodus können Sie Anmerkungen für Ihre Inhalte erstellen, bearbeiten, verschieben oder löschen:

1. Sie können den Anmerkungsmodus über das Symbol in der Symbolleiste (rechts oben) aufrufen, wenn Sie eine Seite bearbeiten:

   ![Anmerken](do-not-localize/screen_shot_2018-03-22at110414.png)

   Sie können nun vorhandene Anmerkungen anzeigen.

   >[!NOTE]
   >
   >Um den Anmerkungsmodus zu beenden, klicken Sie oben rechts in der Symbolleiste auf das Anmerken-Symbol (x-Symbol).

1. Klicken Sie auf das Symbol „Anmerkung hinzufügen“ (Plussymbol links in der Symbolleiste), um mit dem Hinzufügen von Anmerkungen zu beginnen.

   >[!NOTE]
   >
   >Um das Hinzufügen von Anmerkungen zu beenden (und zur Anzeige zurückzukehren), klicken Sie links in der oberen Symbolleiste auf das Abbrechen-Symbol (x-Symbol in einem weißen Kreis).

1. Klicken Sie auf die erforderliche Komponente (Komponenten, denen eine Anmerkung hinzugefügt werden kann, sind mit einem blauen Rahmen gekennzeichnet), um die Anmerkung hinzuzufügen und das Dialogfeld zu öffnen:

   ![screen_shot_2018-03-22at110606](assets/screen_shot_2018-03-22at110606.png)

   Hier können Sie das entsprechende Feld und/oder Symbol verwenden, um:

   * den Anmerkungstext einzugeben.
   * Eine Zeichnung (Linien und Formen) erstellen, um den Bereich der Komponente hervorzuheben.

     Der Mauszeiger ändert sich in ein Fadenkreuz, wenn Sie eine Zeichnung erstellen. Sie können mehrere separate Linien zeichnen. Die Zeichnungslinie hat dieselbe Farbe wie die Anmerkung und kann ein Pfeil, ein Kreis oder ein Oval sein.

     ![Skizze](do-not-localize/screen_shot_2018-03-22at110640.png)

   * Farbe wählen/ändern:

     ![Farbe wählen/ändern](do-not-localize/chlimage_1-19.png)

   * Die Anmerkung löschen.

     ![Anmerkung löschen](do-not-localize/screen_shot_2018-03-22at110647.png)

1. Sie können das Dialogfeld für die Anmerkungen schließen, indem Sie außerhalb des Dialogfelds. Es wird eine gekürzte Ansicht der Anmerkung zusammen mit sämtlichen Zeichnungen angezeigt:

   ![screen_shot_2018-03-22at110850](assets/screen_shot_2018-03-22at110850.png)

1. Wenn Sie mit dem Bearbeiten einer bestimmten Anmerkung fertig sind, können Sie Folgendes tun:

   * Klicken Sie auf die Textmarkierung, um die Anmerkung zu öffnen. Sobald sie geöffnet ist, können Sie den vollständigen Text sehen, Änderungen vornehmen oder die Anmerkung löschen.

      * Zeichnungen können nicht unabhängig von der Anmerkung gelöscht werden.

   * Positionieren Sie die Textmarkierung neu.
   * Klicken Sie auf eine Skizze, um diese Skizze auszuwählen und sie auf die gewünschte Position zu ziehen.
   * Eine Komponente zu verschieben oder zu kopieren.

      * Alle damit verbundenen Anmerkungen und deren Zeichnungen werden ebenfalls verschoben oder kopiert und ihre Position in Relation zum Absatz bleibt gleich.

1. Um den Anmerkungsmodus zu beenden und zum vorher verwendeten Modus zurückzukehren, klicken Sie auf die Schaltfläche (x-Symbol) oben rechts in der Symbolleiste.

>[!NOTE]
>
>Anmerkungen können nicht zu einer Seite hinzugefügt werden, die von einer anderen Person gesperrt wurde.

### Kennzeichnung von Anmerkungen {#annotation-indicator}

Anmerkungen werden nicht im Bearbeitungsmodus angezeigt, doch die Kennzeichnung oben rechts in der Symbolleiste gibt an, wie viele Anmerkungen auf der aktuellen Seite vorhanden sind. Die Kennzeichnung ersetzt das standardmäßige Anmerkungssymbol, dient jedoch ebenfalls als schneller Link, mit dem Sie den Anmerkungsmodus aktivieren/deaktivieren können:

![Anmerkungsanzeige](assets/chlimage_1-242.png)
