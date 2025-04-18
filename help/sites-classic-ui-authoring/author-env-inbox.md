---
title: Ihr Posteingang
description: Sie können Benachrichtigungen aus verschiedenen Bereichen von AEM erhalten, beispielsweise Benachrichtigungen zu Arbeitselementen oder Aufgaben bezüglich Aktionen, die Sie für Seiteninhalte durchführen müssen.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
exl-id: 2f760a0e-bee3-4803-b0db-6e1137396600
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 100%

---

# Ihr Posteingang{#your-inbox}

Sie können Benachrichtigungen aus verschiedenen Bereichen von AEM erhalten, beispielsweise Benachrichtigungen zu Arbeitselementen oder Aufgaben bezüglich Aktionen, die Sie für Seiteninhalte durchführen müssen.

Diese Benachrichtigungen werden je nach Benachrichtigungstyp in zwei verschiedene Posteingänge zugestellt:

* Ein Posteingang, in dem die Benachrichtigungen empfangen werden, die Sie im Rahmen von Abonnements erhalten. Dieser wird im folgenden Abschnitt beschrieben.
* Ein spezieller Posteingang für Workflow-Elemente wird im Dokument [Teilnehmen an Workflows](/help/sites-classic-ui-authoring/classic-workflows-participating.md) beschrieben.

## Anzeigen Ihrer Benachrichtigungen {#viewing-your-notifications}

So zeigen Sie Ihre Benachrichtigungen an:

1. Öffnen Sie den Benachrichtigungs-Posteingang, indem Sie in der Konsole **Websites** auf die Benutzerschaltfläche oben rechts klicken und **Benachrichtigungs-Posteingang** auswählen.

   ![screen_shot_2012-02-08at105226am](assets/screen_shot_2012-02-08at105226am.png)

   >[!NOTE]
   >
   >Sie können auch direkt im Browser auf die Konsole zugreifen. Beispiel:
   >
   >
   >` https://<host>:<port>/libs/wcm/core/content/inbox.html`

1. Ihre Benachrichtigungen werden aufgelistet. Sie können nach Bedarf Aktionen durchführen:

   * [Abonnieren von Benachrichtigungen](#subscribing-to-notifications)
   * [Verarbeiten von Benachrichtigungen](#processing-your-notifications)

   ![chlimage_1-4](assets/chlimage_1-4.jpeg)

## Abonnieren von Benachrichtigungen {#subscribing-to-notifications}

So abonnieren Sie Benachrichtigungen:

1. Öffnen Sie den Benachrichtigungs-Posteingang, indem Sie in der Konsole **Websites** auf die Benutzerschaltfläche oben rechts klicken und **Benachrichtigungs-Posteingang** auswählen.

   ![screen_shot_2012-02-08at105226am-1](assets/screen_shot_2012-02-08at105226am-1.png)

   >[!NOTE]
   >
   >Sie können auch direkt im Browser auf die Konsole zugreifen. Beispiel:
   >
   >
   >`https://<host>:<port>/libs/wcm/core/content/inbox.html`

1. Klicken Sie oben links auf **Konfigurieren...**, um das Konfigurationsdialogfeld zu öffnen.

   ![screen_shot_2012-02-08at111056am](assets/screen_shot_2012-02-08at111056am.png)

1. Wählen Sie den Benachrichtigungskanal aus:

   * **Posteingang**: Die Benachrichtigungen werden in Ihrem AEM Posteingang angezeigt.
   * **E-Mail**: Die Benachrichtigungen werden an die in Ihrem Benutzerprofil angegebene E-Mail-Adresse gesendet.

   >[!NOTE]
   >
   >Einige Einstellungen müssen konfiguriert werden, um eine Benachrichtigung per E-Mail zu ermöglichen. Außerdem können Sie die E-Mail-Vorlage anpassen oder eine E-Mail-Vorlage für eine neue Sprache hinzufügen. Informationen zum Konfigurieren von E-Mail-Benachrichtigungen in AEM finden Sie unter [Konfigurieren von E-Mail-Benachrichtigungen](/help/sites-administering/notification.md#configuringemailnotification).

1. Wählen Sie die Seitenaktionen aus, für die Sie eine Benachrichtigung erhalten möchten:

   * Aktiviert: wenn eine Seite aktiviert wurde.
   * Deaktiviert: wenn eine Seite deaktiviert wurde.
   * Gelöscht (Syndication): wenn eine Seite gelöscht und repliziert wurde, d. h., wenn eine Löschaktion auf einer Seite repliziert wird.
Wenn eine Seite gelöscht oder verschoben wird, wird automatisch eine Löschaktion repliziert: Die Seite wird in der Quellinstanz, in der die Löschaktion durchgeführt wurde, und in der von den Replikationsagenten definierten Zielinstanz gelöscht.

   * Geändert: wenn eine Seite geändert wurde.
   * Erstellt: wenn eine Seite erstellt wurde.
   * Gelöscht: wenn eine Seite durch eine Seitenlöschaktion gelöscht wurde.
   * Ausgerollt: wenn ein Rollout einer Seite durchgeführt wurde.

1. Definieren Sie die Pfade der Seiten, für die Sie benachrichtigt werden wollen:

   * Klicken Sie auf **Hinzufügen**, um der Tabelle eine neue Zeile hinzuzufügen.
   * Klicken Sie auf die Tabellenzelle **Pfad**, und geben Sie den Pfad ein, z. B. `/content/docs`.

   * Um für alle Seiten, die zur Unterstruktur gehören, benachrichtigt zu werden, setzen Sie **Exakt?** auf **Nein**.
Um über nur über die angegebene Seite Benachrichtigungen zu erhalten, setzen Sie **Exakt?** auf **Ja**.

   * Um die Regel zuzulassen, legen Sie **Regel** auf **Zulassen** fest. Wenn dies auf **Ablehnen** festgelegt ist, wird die Regel deaktiviert, aber nicht entfernt und kann später zugelassen werden.

   Um eine Definition zu entfernen, wählen Sie die Zeile aus, indem Sie auf eine Tabellenzelle klicken, und klicken Sie auf **Löschen**.

1. Klicken Sie auf **OK**, um die Konfiguration zu speichern.

## Verarbeiten von Benachrichtigungen {#processing-your-notifications}

Wenn Sie ausgewählt haben, dass Sie Benachrichtigungen in Ihrem AEM-Posteingang erhalten, werden die Benachrichtigungen an das Postfach versendet. Sie können [Ihre Benachrichtigungen anzeigen](#viewing-your-notifications) und dann die erforderlichen Benachrichtigungen auswählen, um Folgendes zu tun:

* Genehmigen durch Klicken auf **Genehmigen**, woraufhin der Wert in der Spalte **Lesen** auf **wahr** gesetzt wird.

* Entfernen durch Klicken auf **Löschen**.

![chlimage_1-5](assets/chlimage_1-5.jpeg)
