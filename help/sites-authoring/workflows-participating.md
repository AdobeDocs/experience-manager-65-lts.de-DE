---
title: Workflow-Beteiligung
description: Workflows enthalten normalerweise Schritte, bei denen eine Person eine Aktivität auf einer Seite oder in einem Asset ausführen muss.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Workflow
role: User,Admin,Architect,Developer
exl-id: 2680e967-ec04-4ae6-b379-f1f0e7c6606b
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1521'
ht-degree: 100%

---

# Teilnehmen an Workflows{#participating-in-workflows}

Workflows enthalten normalerweise Schritte, bei denen eine Person eine Aktivität auf einer Seite oder in einem Asset ausführen muss. Der Workflow wählt eine Benutzerin bzw. einen Benutzer oder eine Gruppe aus, um die Aktivität auszuführen, und weist dieser Person oder Gruppe ein Arbeitselement zu. Die Person erhält eine Benachrichtigung und kann dann die entsprechenden Aktionen ausführen:

* [Ansehen der Benachrichtigungen](#notifications-of-available-workflow-actions)
* [Fertigstellen eines Teilnehmerschritts](#completing-a-participant-step)
* [Delegieren eines Teilnehmerschritts](#delegating-a-participant-step)
* [Wechseln zu einem vorherigen Teilnehmerschritt](#performing-step-back-on-a-participant-step)
* [Öffnen eines Workflow-Elements, um Details anzuzeigen (und Maßnahmen zu ergreifen)](#opening-a-workflow-item-to-view-details-and-take-actions)
* [Anzeigen der Workflow-Payload (mehrere Ressourcen)](#viewing-the-workflow-payload-multiple-resources)

## Benachrichtigungen über verfügbare Workflow-Aktionen {#notifications-of-available-workflow-actions}

Wenn Ihnen ein Arbeitselement zugewiesen wird (z. B. **Inhalte genehmigen**), werden verschiedene Warnhinweise und/oder Benachrichtigungen angezeigt:

* In der [Benachrichtigungsanzeige](/help/sites-authoring/inbox.md) (Symbolleiste) werden weitere Elemente angezeigt:

  ![Benachrichtigungsanzeige](do-not-localize/wf-57.png)

* Das Element wird in Ihrem Benachrichtigungs-[Posteingang](/help/sites-authoring/inbox.md) aufgeführt:

  ![wf-58](assets/wf-58.png)

* Wenn Sie den Seiteneditor verwenden, wird in der Statusleiste Folgendes angezeigt:

   * Die Namen der Workflows, die auf die Seite angewendet werden, z. B. „Aktivierungsanfrage“.
   * Alle Aktionen, die dem momentanen Benutzer bzw. der Benutzerin für den aktuellen Workflow-Schritt zur Verfügung stehen, z. B. „Fertigstellen“, „Delegieren“ oder „Details anzeigen“.
   * Die Anzahl der Workflows, denen die Seite unterliegt. Sie haben folgende Möglichkeiten:

      * Die Pfeiltasten links/rechts verwenden, um durch die Statusinformationen der verschiedenen Workflows zu navigieren.
      * Auf die tatsächliche Zahl klicken, um eine Dropdown-Liste aller anwendbaren Workflows zu öffnen, und dann den Workflow auswählen, der in der Statusleiste angezeigt werden soll.

  ![wf-59](assets/wf-59.png)

  >[!NOTE]
  >
  >ie Statusleiste ist nur für Benutzer mit Workflow-Privilegien sichtbar, z. B. Mitglieder der Gruppe `workflow-users`.
  >
  >
  >Aktionen werden dann angezeigt, wenn der aktuelle Benutzer bzw. die Benutzerin direkt am aktuellen Workflow-Schritt beteiligt sind.

* Wenn die **Timeline** für die Ressource geöffnet ist, wird der Workflow-Schritt angezeigt. Wenn Sie auf das Warnbanner klicken, werden die verfügbaren Aktionen ebenfalls angezeigt:

  ![screen-shot_2019-03-05at120453](assets/screen-shot_2019-03-05at120453.png)

### Fertigstellen eines Teilnehmerschritts {#completing-a-participant-step}

Sie können ein Element abschließen, damit der Workflow mit dem nächsten Schritt fortfahren kann.

Bei dieser Aktion können Sie Folgendes angeben:

* **Nächster Schritt**: der nächste Schritt, der ausgeführt werden soll (Sie können aus einer vorgegebenen Liste auswählen)
* **Kommentar**: falls erforderlich

Sie können einen Teilnehmerschritt wie folgt abschließen:

* [im Posteingang](#completing-a-participant-step-inbox)
* [im Seiten-Editor](#completing-a-participant-step-page-editor)
* [Zeitleiste](#completing-a-participant-step-timeline)
* beim [Öffnen eines Workflow-Elements zur Ansicht von Details](#opening-a-workflow-item-to-view-details-and-take-actions)

#### Durchführen eines Teilnehmerschritts: Posteingang {#completing-a-participant-step-inbox}

Führen Sie die folgenden Schritte aus, um das Arbeitselement abzuschließen:

1. Öffnen Sie den **[AEM-Posteingang](/help/sites-authoring/inbox.md)**.
1. Wählen Sie das Workflow-Element aus, das Sie bearbeiten möchten (klicken Sie auf die Miniaturansicht).
1. Wählen Sie in der Symbolleiste die Option **Fertigstellen** aus.
1. Das Dialogfeld **Arbeitselement fertigstellen** wird geöffnet. Gehen Sie in der Dropdown-Auswahl zu **Nächster Schritt** und fügen Sie bei Bedarf einen **Kommentar** hinzu.
1. Verwenden Sie **OK**, um den Schritt abzuschließen (oder **Abbrechen**, um den Vorgang abzubrechen).

#### Durchführen eines Teilnehmerschritts: Seiten-Editor {#completing-a-participant-step-page-editor}

Führen Sie die folgenden Schritte aus, um das Arbeitselement abzuschließen:

1. Öffnen Sie die [Seite zur Bearbeitung](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing).
1. Wählen Sie in der Statusleiste oben im Bild **Fertig stellen** aus.
1. Das Dialogfeld **Arbeitselement fertigstellen** wird geöffnet. Gehen Sie in der Dropdown-Auswahl zu **Nächster Schritt** und fügen Sie bei Bedarf einen **Kommentar** hinzu.
1. Verwenden Sie **OK**, um den Schritt abzuschließen (oder **Abbrechen**, um den Vorgang abzubrechen).

#### Durchführen eines Teilnehmerschritts: Zeitleiste {#completing-a-participant-step-timeline}

Sie können auch die Zeitleiste verwenden, um einen Schritt abzuschließen und zum nächsten Schritt zu gelangen:

1. Wählen Sie die entsprechende Seite aus und öffnen Sie die **Zeitleiste** (oder öffnen Sie die **Zeitleiste** und wählen Sie die Seite aus):

   ![screen-shot_2019-03-05at120744](assets/screen-shot_2019-03-05at120744.png)

1. Klicken Sie auf das Warnbanner, um die verfügbaren Aktionen anzuzeigen. Wählen Sie **Voranbringen**:

   ![screen-shot_2019-03-05at120453-1](assets/screen-shot_2019-03-05at120453-1.png)

1. Je nach Workflow können Sie den nächsten Schritt auswählen:

   ![screen-shot_2019-03-05at120905](assets/screen-shot_2019-03-05at120905.png)

1. Wählen Sie **Voranbringen**, um die Aktion zu bestätigen.

### Delegieren eines Teilnehmerschritts {#delegating-a-participant-step}

Wenn Ihnen ein Schritt zugewiesen wurde, Sie jedoch aus irgendeinem Grund die Aktion nicht ausführen können, können Sie den Schritt an eine andere Person oder Gruppe delegieren.

An welche Benutzenden delegiert werden kann, hängt davon ab, wem das Arbeitselement zugewiesen wurde:

* Wenn das Arbeitselement einer Gruppe zugewiesen wurde, sind die Gruppenmitglieder verfügbar.
* Wenn das Arbeitselement einer Gruppe zugewiesen und dann an einen Benutzer delegiert wurde, sind die Gruppenmitglieder und die Gruppe verfügbar.
* Wenn das Arbeitselement einem einzelnen Benutzer zugewiesen wurde, kann es nicht delegiert werden.

Bei dieser Aktion können Sie Folgendes angeben:

* **Benutzerin bzw. Benutzer**: die Person, an die Sie delegieren möchten (Sie können aus einer bereitgestellten Liste auswählen)
* **Kommentar**: falls erforderlich

Das Delegieren eines Teilnehmerschritts ist möglich:

* [im Posteingang](#delegating-a-participant-step-inbox)
* [im Seiten-Editor](#delegating-a-participant-step-page-editor)
* [Zeitleiste](#delegating-a-participant-step-timeline)
* beim [Öffnen eines Workflow-Elements zur Ansicht von Details](#opening-a-workflow-item-to-view-details-and-take-actions)

#### Delegieren eines Teilnehmerschritts: Posteingang {#delegating-a-participant-step-inbox}

Gehen Sie folgendermaßen vor, um ein Arbeitselement zu delegieren:

1. Öffnen Sie den **[AEM-Posteingang](/help/sites-authoring/inbox.md)**.
1. Wählen Sie das Workflow-Element aus, das Sie bearbeiten möchten (klicken Sie auf die Miniaturansicht).
1. Wählen Sie in der Symbolleiste die Option **Delegieren** aus.
1. Ein Dialogfeld wird angezeigt. Wählen Sie in der Dropdown-Auswahl die Option **Benutzer** aus (dabei kann es sich auch um eine Gruppe handeln) und fügen Sie bei Bedarf einen **Kommentar** hinzu.
1. Verwenden Sie **OK**, um den Schritt abzuschließen (oder **Abbrechen**, um den Vorgang abzubrechen).

#### Delegieren eines Teilnehmerschritts: Seiten-Editor {#delegating-a-participant-step-page-editor}

Gehen Sie folgendermaßen vor, um ein Arbeitselement zu delegieren:

1. Öffnen Sie die [Seite zur Bearbeitung](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing).
1. Wählen Sie in der Statusleiste oben im Bild **Delegieren** aus.
1. Ein Dialogfeld wird angezeigt. Wählen Sie in der Dropdown-Auswahl die Option **Benutzer** aus (dabei kann es sich auch um eine Gruppe handeln) und fügen Sie bei Bedarf einen **Kommentar** hinzu.
1. Verwenden Sie **OK**, um den Schritt abzuschließen (oder **Abbrechen**, um den Vorgang abzubrechen).

#### Delegieren eines Teilnehmerschritts: Zeitleiste {#delegating-a-participant-step-timeline}

Sie können auch die Zeitleiste verwenden, um einen Schritt zu delegieren und/oder zuzuweisen:

1. Wählen Sie die entsprechende Seite aus und öffnen Sie die **Zeitleiste** (oder öffnen Sie die **Zeitleiste** und wählen Sie die Seite aus).
1. Klicken Sie auf das Warnbanner, um die verfügbaren Aktionen anzuzeigen. Wählen Sie **Bevollmächtigten ändern**:

   ![screen-shot_2019-03-05at120453-2](assets/screen-shot_2019-03-05at120453-2.png)

1. Legen Sie einen neuen Bevollmächtigten fest:

   ![screen-shot_2019-03-05at121025](assets/screen-shot_2019-03-05at121025.png)

1. Wählen Sie **Zuweisen** aus, um die Aktion zu bestätigen.

### Wechseln zu einem vorherigen Teilnehmerschritt {#performing-step-back-on-a-participant-step}

Wenn Sie erkennen, dass ein Schritt oder eine Reihe von Schritten wiederholt werden muss, können Sie zu einem vorherigen Schritt zurückkehren. Auf diese Weise können Sie einen früheren Schritt im Workflow zur erneuten Verarbeitung auswählen. Der Workflow kehrt zu dem von Ihnen angegebenen Schritt zurück und fährt dann dort fort.

Bei dieser Aktion können Sie Folgendes angeben:

* **Vorheriger Schritt**: der Schritt, zu dem zurückgekehrt werden soll; Sie können hier aus einer Liste auswählen
* **Kommentar**: falls erforderlich

Das Wechseln zu einem vorherigen Teilnehmerschritt ist möglich:

* [im Posteingang](#performing-step-back-on-a-participant-step-inbox)
* [im Seiten-Editor](#performing-step-back-on-a-participant-step-page-editor)
* [Zeitleiste](#performing-step-back-on-a-participant-step-timeline)
* beim [Öffnen eines Workflow-Elements zur Ansicht von Details](#opening-a-workflow-item-to-view-details-and-take-actions)

#### Wechseln zu einem vorherigen Teilnehmerschritt: Posteingang {#performing-step-back-on-a-participant-step-inbox}

Gehen Sie dazu folgendermaßen vor:

1. Öffnen Sie den **[AEM-Posteingang](/help/sites-authoring/inbox.md)**.
1. Wählen Sie das Workflow-Element aus, das Sie bearbeiten möchten (klicken Sie auf die Miniaturansicht).
1. Wählen Sie **Schritt zurück** aus, um das Dialogfeld zu öffnen.

1. Wählen Sie die Option **Vorheriger Schritt** aus und fügen Sie bei Bedarf einen **Kommentar** hinzu.
1. Verwenden Sie **OK**, um den Schritt abzuschließen (oder **Abbrechen**, um den Vorgang abzubrechen).

#### Wechseln zu einem vorherigen Teilnehmerschritt: Seiten-Editor {#performing-step-back-on-a-participant-step-page-editor}

Gehen Sie dazu folgendermaßen vor:

1. Öffnen Sie die [Seite zur Bearbeitung](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing).
1. Wählen Sie in der Symbolleiste oben im Bild **Schritt zurück** aus.
1. Wählen Sie die Option **Vorheriger Schritt** aus und fügen Sie bei Bedarf einen **Kommentar** hinzu.
1. Verwenden Sie **OK**, um den Schritt abzuschließen (oder **Abbrechen**, um den Vorgang abzubrechen).

#### Wechseln zu einem vorherigen Teilnehmerschritt: Zeitleiste {#performing-step-back-on-a-participant-step-timeline}

Sie können auch die Zeitleiste verwenden, um zu einem vorherigen Schritt zurückzukehren:

1. Wählen Sie die entsprechende Seite aus und öffnen Sie die **Zeitleiste** (oder öffnen Sie die **Zeitleiste** und wählen Sie die Seite aus).
1. Klicken Sie auf das Warnbanner, um die verfügbaren Aktionen anzuzeigen. Wählen Sie **Zurücksetzen**:

   ![screen-shot_2019-03-05at121131](assets/screen-shot_2019-03-05at121131.png)

1. Geben Sie den Schritt an, an den der Workflow zurückkehren soll:

   ![screen-shot_2019-03-05at121158](assets/screen-shot_2019-03-05at121158.png)

1. Wählen Sie **Zurücksetzen** aus, um die Aktion zu bestätigen.

### Öffnen eines Workflow-Elements, um Details anzuzeigen (und Maßnahmen zu ergreifen) {#opening-a-workflow-item-to-view-details-and-take-actions}

Zeigen Sie Details zum Workflow-Element an und führen Sie entsprechende Aktionen aus.

Die Workflow-Details werden in Registerkarten angezeigt und die entsprechenden Aktionen können in der Symbolleiste ausgewählt werden:

* Registerkarte **ARBEITSELEMENT**:

  ![wf-72](assets/wf-72.png)

* Registerkarte **WORKFLOW-INFORMATIONEN**:

  ![wf-73](assets/wf-73.png)

  Wenn für das Modell die Option [Workflow-Status](/help/sites-developing/workflows.md#workflow-stages) konfiguriert wurde, können Sie den Fortschritt entsprechend dem Status anzeigen:

  ![wf-107](assets/wf-107.png)

* Registerkarte **KOMMENTARE**:

  ![wf-75](assets/wf-75.png)

Das Öffnen der Details der Arbeitselemente ist möglich:

* [im Posteingang](#performing-step-back-on-a-participant-step-inbox)
* [im Seiten-Editor](#performing-step-back-on-a-participant-step-page-editor)

#### Öffnen der Workflow-Details: Posteingang {#opening-workflow-details-inbox}

Gehen Sie folgendermaßen vor, um ein Workflow-Element zu öffnen und die Details anzusehen:

1. Öffnen Sie den **[AEM-Posteingang](/help/sites-authoring/inbox.md)**.
1. Wählen Sie das Workflow-Element aus, das Sie bearbeiten möchten (klicken Sie auf die Miniaturansicht).
1. Wählen Sie **Öffnen** aus, um die Informationsregisterkarten zu öffnen.

1. Wählen Sie bei Bedarf die geeignete Aktion aus, geben Sie etwaige Details ein und bestätigen Sie mit **OK** (oder **Abbrechen**).
1. Mit **Speichern** oder **Abbrechen** schließen Sie das Dialogfeld.

#### Öffnen von Workflow-Details: Seiten-Editor {#opening-workflow-details-page-editor}

Gehen Sie folgendermaßen vor, um ein Workflow-Element zu öffnen und die Details anzusehen:

1. Öffnen Sie die [Seite zur Bearbeitung](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing).
1. Wählen Sie aus der Statusleiste **Details anzeigen** aus, um die Informationsregisterkarten zu öffnen.

1. Wählen Sie bei Bedarf die geeignete Aktion aus, geben Sie etwaige Details ein und bestätigen Sie mit **OK** (oder **Abbrechen**).
1. Mit **Speichern** oder **Abbrechen** schließen Sie das Dialogfeld.

### Ansicht der Workflow-Payload (mehrere Ressourcen) {#viewing-the-workflow-payload-multiple-resources}

Sie können sich Details zur Payload anzeigen lassen, die mit der Workflow-Instanz verbunden ist. Zunächst werden die Ressourcen im Paket gezeigt, Sie können diese aber weiter aufschlüsseln und die einzelnen Seiten anzeigen.

Gehen Sie folgendermaßen vor, um die Payload und Ressourcen der Workflow-Instanz anzuzeigen:

1. Öffnen Sie den **[AEM-Posteingang](/help/sites-authoring/inbox.md)**.
1. Wählen Sie das Workflow-Element aus, das Sie bearbeiten möchten (klicken Sie auf die Miniaturansicht).
1. Wählen Sie in der Symbolleiste **Nutzdaten anzeigen** aus, um den Dialog zu öffnen.

   Da ein Workflow-Paket lediglich eine Sammlung von Referenzen auf Pfade innerhalb des Repositorys ist, können Sie die Einträge hier hinzuzufügen, entfernen oder anpassen, um zu ändern, was vom Workflow-Paket referenziert werden soll. Verwenden Sie die Komponente **Ressourcendefinition**, um neue Einträge hinzuzufügen.

   ![wf-78](assets/wf-78.png)

1. Mit den Links können die einzelnen Seiten geöffnet werden.
