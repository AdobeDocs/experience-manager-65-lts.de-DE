---
title: Verwalten von Übersetzungsprojekten
description: Erfahren Sie, wie Sie Übersetzungsprojekte in Adobe Experience Manager verwalten.
solution: Experience Manager, Experience Manager Sites
feature: Language Copy
role: Admin
exl-id: 901bd212-3daf-4b1e-a7c3-afb832959913
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '3519'
ht-degree: 100%

---

# Verwalten von Übersetzungsprojekten{#managing-translation-projects}

Nachdem Sie den Inhalt für die Übersetzung vorbereitet haben, müssen Sie die Sprachstruktur vervollständigen, indem Sie fehlende Sprachkopien sowie Übersetzungsprojekte erstellen.

Mithilfe von Übersetzungsprojekten können Sie die Übersetzung von AEM-Inhalten verwalten. Ein Übersetzungsprojekt ist ein Typ eines AEM-[Projekts](/help/sites-authoring/projects.md), das Ressourcen beinhaltet, die in andere Sprachen übersetzt werden sollen. Bei diesen Ressourcen handelt es sich um Seiten und Assets der [Sprachkopien](/help/sites-administering/tc-prep.md), die vom Sprachstamm erstellt werden.

Wenn einem Übersetzungsprojekt Ressourcen hinzugefügt werden, wird ein Übersetzungsauftrag für sie erstellt. Aufträge beinhalten Befehle und Statusinformationen, mit denen Sie die Workflows für menschliche und maschinelle Übersetzungen, die für die Ressourcen ausgeführt werden, verwalten.

>[!NOTE]
>
>Ein Übersetzungsprojekt kann mehrere Übersetzungsaufträge enthalten.

Übersetzungsprojekte sind langfristige Elemente, die durch Sprache und Übersetzungsmethode/-anbieter definiert werden, um sie an die Governance der Organisation für die Globalisierung anzupassen. Sie sollten einmal während der Erstübersetzung oder manuell initiiert werden und so lange gültig bleiben, wie Aktivitäten der Inhalts- und Übersetzungsaktualisierung ausgeführt werden.

Übersetzungsprojekte und -vorgänge werden mit Übersetzungsvorbereitungs-Workflows erstellt. Diese Workflows umfassen drei Optionen für die Erstübersetzung (Erstellen und übersetzen) und für Aktualisierungen (Übersetzung aktualisieren):

1. [Neues Projekt erstellen](#creating-translation-projects-using-the-references-panel)
1. [Zu vorhandenem Projekt hinzufügen](#adding-pages-to-a-translation-project)
1. [Nur Inhaltsstruktur](#creating-the-structure-of-a-language-copy)

>[!NOTE]
>
>Die Option 3 bezieht sich nicht auf einen Übersetzungsauftrag/ein Übersetzungsprojekt. Sie können Inhalte und strukturelle Änderungen in der Sprachmustervorlage in (nicht übersetzte) Sprachkopien kopieren. Sie können diese Option verwenden, um Ihren Sprachstamm auch ohne Übersetzung zu synchronisieren.

## Durchführen von Erstübersetzungen und Aktualisieren vorhandener Übersetzungen {#performing-initial-translations-and-updating-existing-translations}

AEM erkennt, ob ein Übersetzungsprojekt für die Erstübersetzung von Inhalten oder für die Aktualisierung bereits übersetzter Sprachkopien erstellt wird. Wenn Sie ein Übersetzungsprojekt für eine Seite erstellen und die Sprachkopien angeben, die übersetzt werden sollen, erkennt AEM, ob die Quellseite bereits in den Zielsprachkopien vorhanden ist:

* **Die Sprachkopie enthält die Seite nicht:** AEM geht in diesem Fall von einer Erstübersetzung aus. Die Seite wird sofort in die Sprachkopie kopiert und in das Projekt aufgenommen. Wenn die übersetzte Seite in AEM importiert wird, kopiert AEM sie direkt in die Sprachkopie.
* **Die Sprachkopie enthält bereits die Seite:** AEM geht in diesem Fall davon aus, dass die Übersetzung aktualisiert wird. Ein Launch wird erstellt und eine Kopie der Seite zum Launch hinzugefügt und in das Projekt aufgenommen. Mithilfe von Launches können Sie aktualisierte Übersetzungen vor dem Einfügen in die Sprachkopie überprüfen:

   * Wenn die übersetzte Seite in AEM importiert wird, wird die Seite im Launch überschrieben.
   * Die übersetzte Seite überschreibt die Sprachkopie nur, wenn der Launch weitergeleitet (beworben) wird.

Beispiel: Der Sprachstamm „/content/geometrixx/fr“ wurde für die französische Übersetzung der Primärsprache „/content/geometrixx/en“ erstellt. Es gibt keine anderen Seiten in der französischen Sprachkopie.

* Es wird ein Übersetzungsprojekt für die Seite /content/geometrixx/en/products und alle untergeordneten Seiten erstellt, das mit der französischen Sprachkopie verknüpft ist. Da die Sprachkopie die Seite /content/geometrixx/fr/products nicht enthält, kopiert AEM die Seite /content/geometrixx/en/products und alle untergeordneten Seiten sofort in die französische Sprachkopie. Die Kopien werden auch in das Übersetzungsprojekt eingefügt.
* Es wird ein Übersetzungsprojekt für die Seite /content/geometrixx/en/ und alle untergeordneten Seiten erstellt, das als Ziel die französische Sprachkopie hat. Da die Sprachkopie die Seite enthält, die der Seite /content/geometrixx/en (dem Sprach-Stamm) entspricht, kopiert AEM die Seite /content/geometrixx/en und alle untergeordneten Seiten und fügt sie einem Launch hinzu. Die Kopien werden auch in das Übersetzungsprojekt eingefügt.

## Erstellen von Übersetzungsprojekten mithilfe des Bedienfelds „Verweise“ {#creating-translation-projects-using-the-references-panel}

Erstellen Sie Übersetzungsprojekte so, dass Sie den Workflow zur Übersetzung der Ressourcen Ihres Sprachstamms ausführen und verwalten können. Wenn Sie Projekte erstellen, legen Sie die Seite im Sprachstamm, die Sie übersetzen wollen, und die Sprachkopien, für die Sie die Übersetzung durchführen wollen, fest:

* Die Cloud-Konfiguration des Frameworks für die Übersetzungsintegration, das mit der ausgewählten Seite verknüpft ist, bestimmt viele Eigenschaften der Übersetzungsprojekte, z. B. die zu verwendenden Übersetzungs-Workflows.
* Es wird ein Projekt für jede ausgewählte Sprachkopie erstellt.
* Es wird eine Kopie der ausgewählten Seite und der zugehörigen Assets erstellt und jedem Projekt hinzugefügt. Diese Kopien werden später zum Übersetzen an den Übersetzungsanbieter gesendet.

Sie können festlegen, dass die untergeordneten Seiten der ausgewählten Seite ebenfalls ausgewählt werden sollen. In diesem Fall werden jedem Projekt auch die Kopien der untergeordneten Seiten hinzugefügt, sodass sie übersetzt werden. Wenn alle untergeordneten Seiten mit unterschiedlichen Übersetzungsintegrations-Framework-Konfigurationen verknüpft sind, erstellt AEM weitere Projekte.

Sie können [Übersetzungsprojekte auch manuell erstellen](#creating-a-translation-project-using-the-projects-console).

>[!NOTE]
>
>Um ein Projekt zu erstellen, muss Ihr Konto Mitglied der Gruppe `project-administrators` sein.

**Erstübersetzungen und Aktualisieren von Übersetzungen**

Im Bedienfeld „Verweise“ wird angezeigt, ob Sie vorhandene Sprachkopien aktualisieren oder die erste Version der Sprachkopien erstellen. Falls eine Sprachkopie für die ausgewählte Seite vorhanden ist, wird die Registerkarte „Sprachkopien aktualisieren“ angezeigt, mit der Sie auf projektspezifische Befehle zugreifen können.

![chlimage_1-239](assets/chlimage_1-239.png)

Nach dem Übersetzen können Sie die [Übersetzung überprüfen](#reviewing-and-promoting-updated-content), bevor Sie die Sprachkopie damit überschreiben. Wenn keine Sprachkopie für die ausgewählte Seite vorhanden ist, wird die Registerkarte „Erstellen und Übersetzen“ angezeigt, auf der Sie auf projektspezifische Befehle zugreifen können.

![chlimage_1-240](assets/chlimage_1-240.png)

### Erstellen von Übersetzungsprojekten für eine neue Sprachkopie {#create-translation-projects-for-a-new-language-copy}

1. Verwenden Sie die Sites-Konsole, um die Seite auszuwählen, die Sie den Übersetzungsprojekten hinzufügen.

   Wählen Sie beispielsweise „Geometrixx Demo Site“ > „Englisch“ aus, um die englischen Seiten der Geometrixx-Demo-Site zu übersetzen.

1. Klicken Sie in der Symbolleiste auf „Verweise“.

   ![chlimage_1-241](assets/chlimage_1-241.png)

1. Wählen Sie die Option Sprachkopien und dann die Sprachkopien aus, für die Sie die Quellseiten übersetzen.
1. Klicken Sie auf „Erstellen und übersetzen“ und konfigurieren Sie dann den Übersetzungsauftrag:

   * Wählen Sie mithilfe des Dropdown-Menüs Sprache eine Sprachkopie aus, für die Sie eine Übersetzung durchführen möchten. Wählen Sie bei Bedarf weitere Sprachen aus. Die in der Liste angezeigten Sprachen entsprechen den [von Ihnen erstellten Sprachstämmen](/help/sites-administering/tc-prep.md#creating-a-language-root).
   * Wählen Sie zur Übersetzung der von Ihnen ausgewählten Seite und allen untergeordneten Seiten die Option „Alle Unterseiten auswählen“ aus. Um nur die von Ihnen ausgewählten Seiten zu übersetzen, wählen Sie diese Option ab.
   * Wählen Sie für das Projekt die Option „Neues Übersetzungsprojekt erstellen“ aus.
   * Geben Sie einen Namen für das Projekt ein.

   ![chlimage_1-242](assets/chlimage_1-242.png)

1. Klicken Sie auf „Erstellen“.

### Erstellen von Übersetzungsprojekten für vorhandene Sprachkopien {#create-translation-projects-for-an-existing-language-copy}

1. Verwenden Sie die Sites-Konsole, um die Seite auszuwählen, die Sie den Übersetzungsprojekten hinzufügen.

   Wählen Sie beispielsweise „Geometrixx Demo Site“ > „Englisch“ aus, um die englischen Seiten der Geometrixx-Demo-Site zu übersetzen.

1. Klicken Sie in der Symbolleiste auf „Verweise“.

   ![chlimage_1-243](assets/chlimage_1-243.png)

1. Wählen Sie die Option Sprachkopien und dann die Sprachkopien aus, für die Sie die Quellseiten übersetzen.
1. Klicken Sie auf „Sprachkopien aktualisieren“ und konfigurieren Sie dann den Übersetzungsauftrag:

   * Wählen Sie zur Übersetzung der von Ihnen ausgewählten Seite und allen untergeordneten Seiten die Option „Alle Unterseiten auswählen“ aus. Um nur die von Ihnen ausgewählten Seiten zu übersetzen, wählen Sie diese Option ab.
   * Wählen Sie für das Projekt die Option „Neues Übersetzungsprojekt erstellen“ aus.
   * Geben Sie einen Namen für das Projekt ein.

   ![chlimage_1-244](assets/chlimage_1-244.png)

1. Klicken Sie auf „Starten“.

## Hinzufügen von Seiten zu einem Übersetzungsprojekt {#adding-pages-to-a-translation-project}

Nachdem Sie ein Übersetzungsprojekt erstellt haben, können Sie das Bedienfeld „Ressourcen“ verwenden, um Seiten zum Projekt hinzuzufügen. Das Hinzufügen von Seiten ist dann hilfreich, wenn Sie Seiten von verschiedenen Verzweigungen in dasselbe Projekt einfügen.

Wenn Sie einem Übersetzungsprojekt Seiten hinzufügen, werden die Seiten in einen neuen Übersetzungsauftrag einbezogen. Sie können auch [Seiten zu einem vorhandenen Vorgang hinzufügen](#adding-pages-assets-to-a-translation-job).

So wie beim Erstellen eines Projekts werden beim Hinzufügen von Seiten bei Bedarf Kopien der Seiten zu einem Launch hinzugefügt, um zu verhindern, dass vorhandene Sprachkopien überschrieben werden. (Siehe [Erstellen von Übersetzungsprojekten für bestehende Sprachkopien](#performing-initial-translations-and-updating-existing-translations).)

1. Verwenden Sie die Sites-Konsole, um die Seite auszuwählen, die Sie zum Übersetzungsprojekt hinzufügen.

   Wählen Sie beispielsweise „Geometrixx Demo Site“ > „Englisch“ aus, um die englischen Seiten der Geometrixx-Demo-Site zu übersetzen.

1. Klicken Sie in der Symbolleiste auf „Verweise“.

   ![chlimage_1-245](assets/chlimage_1-245.png)

1. Wählen Sie die Option Sprachkopien und dann die Sprachkopien aus, für die Sie die Quellseiten übersetzen.

   ![chlimage_1-35](assets/chlimage_1-35.jpeg)

1. Klicken Sie auf „Sprachkopien aktualisieren“ und konfigurieren Sie dann die Eigenschaften:

   * Wählen Sie zur Übersetzung der von Ihnen ausgewählten Seite und allen untergeordneten Seiten die Option „Alle Unterseiten auswählen“ aus. Um nur die von Ihnen ausgewählten Seiten zu übersetzen, wählen Sie diese Option ab.
   * Wählen Sie für das Projekt die Option „Zu vorhandenem Übersetzungsprojekt hinzufügen“ aus.
   * Wählen Sie das Projekt aus.

   >[!NOTE]
   >
   >Die im Übersetzungsprojekt festgelegte Sprache muss dem Pfad der Sprachkopie entsprechen, der im Bedienfeld „Verweise“ angezeigt wird.

   ![chlimage_1-36](assets/chlimage_1-36.jpeg)

1. Klicken Sie auf „Starten“.

## Hinzufügen von Seiten/Assets zu einem Übersetzungsauftrag {#adding-pages-assets-to-a-translation-job}

Sie können Seiten, Assets, Tags oder i18n-Wörterbücher dem Übersetzungsauftrag Ihres Übersetzungsprojektes hinzufügen. So fügen Sie Seiten oder Assets hinzu:

1. Klicken Sie unten im Übersetzungsprojekt auf der Kachel „Übersetzungsauftrag“ auf die Auslassungspunkte.

   ![chlimage_1-246](assets/chlimage_1-246.png)

1. Klicken Sie auf „Hinzufügen“ und anschließend auf „Seiten/Assets“.

   ![chlimage_1-247](assets/chlimage_1-247.png)

1. Wählen Sie das oberste Element der Verzweigung aus, die Sie hinzufügen möchten, und klicken Sie dann auf das Häkchen-Symbol.  Sie können mehrere Objekte auswählen.

   ![chlimage_1-248](assets/chlimage_1-248.png)

1. Alternativ können Sie das Symbol „Suchen“ auswählen, um schnell und einfach nach Seiten oder Assets zu suchen, die Sie Ihrem Übersetzungsauftrag hinzufügen möchten.

   ![chlimage_1-249](assets/chlimage_1-249.png)

Die Seiten und/oder Assets werden dem Übersetzungsauftrag hinzugefügt.

## Hinzufügen von i18n-Wörterbüchern zu einem Übersetzungsauftrag {#adding-i-n-dictionaries-to-a-translation-job}

Sie können Seiten, Assets, Tags oder i18n-Wörterbücher dem Übersetzungsauftrag Ihres Übersetzungsprojektes hinzufügen. Hinzufügen eines i18n-Wörterbuchs:

1. Klicken Sie unten im Übersetzungsprojekt auf der Kachel „Übersetzungsauftrag“ auf die Auslassungspunkte.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Klicken Sie auf „Hinzufügen“ und „I18N-Wörterbuch“.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Wählen Sie **Stammverzeichnis** und das Wörterbuch (falls erforderlich), das Sie hinzufügen möchten, und wählen Sie dann **Hinzufügen**.

   ![I18N-Wörterbuch](assets/tc-manage-i18n-dictionary.png)

1. Wählen Sie ggf. die Art der Aktualisierung aus:

   ![Übersetzen](assets/tc-manage-translate.png)

Ihr Wörterbuch befindet sich nun in Ihrem Übersetzungsauftrag.

![chlimage_1-253](assets/chlimage_1-253.png)

>[!NOTE]
>
>Weitere Informationen zu i18n-Wörterbüchern finden Sie im Abschnitt [Verwenden des Übersetzers zur Verwaltung von Wörterbüchern](/help/sites-developing/i18n-translator.md).

## Hinzufügen von Tags zu einem Übersetzungsauftrag {#adding-tags-to-a-translation-job}

Sie können Seiten, Assets, Tags oder i18n-Wörterbücher dem Übersetzungsauftrag Ihres Übersetzungsprojektes hinzufügen. Hinzufügen von Tags:

1. Klicken Sie unten im Übersetzungsprojekt auf der Kachel „Übersetzungsauftrag“ auf die Auslassungspunkte.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Klicken Sie auf „Hinzufügen“ und dann auf „Tags“.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Wählen Sie die Tags aus, die Sie hinzufügen möchten, und klicken Sie dann auf das Häkchen-Symbol. Sie können mehrere Objekte auswählen.

   ![chlimage_1-256](assets/chlimage_1-256.png)

Ihre Tags werden nun in Ihrem Übersetzungsauftrag hinzugefügt.

![chlimage_1-257](assets/chlimage_1-257.png)

## Anzeigen von Details eines Übersetzungsprojekts {#seeing-translation-project-details}

Die Kachel „Zusammenfassung der Übersetzung“ enthält die Eigenschaften, die für ein Übersetzungsprojekt konfiguriert sind.  Auf der Registerkarte „Übersetzung“ finden Sie zusätzlich zu den allgemeinen [Projektinformationen](/help/sites-authoring/projects.md#project-info) übersetzungsspezifische Eigenschaften:

* Ausgangssprache: Die Sprache der Seiten, die übersetzt werden.
* Zielsprache: Die Sprache, in die die Seiten übersetzt werden.
* Übersetzungsmethode: Der Übersetzungs-Workflow. Es wird „Menschliche Übersetzung“ oder „Maschinelle Übersetzung“ unterstützt.
* Übersetzungsanbieter: Der Übersetzungsdienstleister, der die Übersetzung ausführt.
* Inhaltskategorie: (Maschinelle Übersetzung) Die Inhaltskategorie, die für die Übersetzung verwendet wird.
* Cloud-Konfiguration: Die Cloud-Konfiguration für den Übersetzungsdienst-Connector, der für das Projekt verwendet wird.

Wenn ein Projekt unter Verwendung des Bedienfelds „Ressourcen“ einer Seite erstellt wurde, werden diese Eigenschaften automatisch basierend auf den Eigenschaften der Quellseite konfiguriert.

![chlimage_1-258](assets/chlimage_1-258.png)

## Überwachen des Status von Übersetzungsaufträgen {#monitoring-the-status-of-a-translation-job}

Die Kachel „Übersetzungsauftrag“ eines Übersetzungsprojekts zeigt den Status eines Übersetzungsauftrags sowie die Anzahl der Seiten und Assets im Auftrag an.

![chlimage_1-259](assets/chlimage_1-259.png)

Die folgende Tabelle beschreibt die einzelnen Status, die ein Auftrag oder ein Element im Auftrag haben kann:

| Status | Beschreibung |
|---|---|
| Entwurf | Der Übersetzungsauftrag wurde noch nicht gestartet. Übersetzungsaufträge haben den Status ENTWURF, wenn sie erstellt werden. |
| Übermittelt | Dateien im Übersetzungsauftrag erhalten diesen Status, wenn sie erfolgreich an den Übersetzungs-Service gesendet wurden. Dieser Status kann nach dem Befehl „Request Scope“ oder dem Befehl „Start“ auftreten. |
| Berechnung angefragt | Für den Workflow für die menschliche Übersetzung wurden die Dateien des Auftrags zum Berechnen des Umfangs an den Übersetzungsdienstleister gesendet. Er wird nach Ausgabe des Befehls Berechnung anfordern angezeigt. |
| Berechnung abgeschlossen | Der Anbieter hat die Berechnung des Übersetzungsauftrag abgeschlossen. |
| Übersetzung beauftragt | Der Projektinhaber hat die Berechnung akzeptiert. Dieser Status zeigt an, dass der Übersetzungsanbieter mit der Übersetzung der Dateien im Auftrag beginnen soll. |
| Übersetzung läuft | Bei einem Auftrag ist die Übersetzung einer oder mehrerer Dateien im Auftrag noch nicht abgeschlossen. Hinsichtlich eines Elements im Auftrag besagt der Status, dass das Element übersetzt wird. |
| Übersetzt | Bei einem Auftrag ist die Übersetzung aller Dateien im Auftrag abgeschlossen. Hinsichtlich eines Elements im Auftrag besagt der Status, dass das Element übersetzt ist. |
| Bereit für Überprüfung | Das Element im Auftrag ist übersetzt und die Datei wurde in AEM importiert. |
| Fertig stellen | Der Projektinhaber hat mitgeteilt, dass der Übersetzungsvertrag abgeschlossen ist. |
| Abbrechen | Gibt an, dass der Übersetzungsanbieter die Arbeit an einem Übersetzungsauftrag anhalten soll. |
| Fehler beim Update | Beim Übertragen von Dateien zwischen AEM und dem Übersetzungs-Service ist ein Fehler aufgetreten. |
| Unbekannter Status | Ein unbekannter Fehler ist aufgetreten. |

Klicken Sie auf die Auslassungspunkte am unteren Rand der Kachel, um den Status der einzelnen Dateien im Auftrag anzuzeigen.

## Festlegen des Fälligkeitsdatums von Übersetzungsaufträgen {#setting-the-due-date-of-translation-jobs}

Geben Sie das Datum an, bis zu dem Ihr Übersetzungsanbieter die übersetzten Dateien zurückgeben muss. Sie können das Fälligkeitsdatum für ein Projekt oder für einen bestimmten Auftrag festlegen:

* **Projekt:** Die Übersetzungsaufträge im Projekt übernehmen das Fälligkeitsdatum.
* **Auftrag:** Das von Ihnen für den Auftrag festgelegte Fälligkeitsdatum überschreibt das Fälligkeitsdatum, das für das Projekt festgelegt wurde.

Die Festlegung eines Fälligkeitsdatums funktioniert nur dann richtig, wenn der Übersetzungsanbieter diese Funktion unterstützt.

Mit dem folgenden Verfahren wird das Fälligkeitsdatum für ein Projekt festgelegt.

1. Klicken Sie auf die Auslassungspunkte am unteren Rand der Kachel „Zusammenfassung der Übersetzung“. 

   ![chlimage_1-260](assets/chlimage_1-260.png)

1. Wählen Sie auf der Registerkarte Allgemein mithilfe der Datumsauswahl der Eigenschaft Fälligkeitsdatum das Fälligkeitsdatum aus.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. Klicken Sie auf „Fertig“.

Mit dem folgenden Verfahren wird das Fälligkeitsdatum für einen Übersetzungsauftrag festgelegt.

1. Klicken Sie auf der Kachel „Übersetzungsauftrag“ auf das Befehlsmenü und dann auf „Fälligkeitsdatum“.

   ![chlimage_1-262](assets/chlimage_1-262.png)

1. Klicken Sie im Dialogfeld auf das Kalendersymbol, wählen Sie dann das Datum und die Uhrzeit für das Fälligkeitsdatum aus und klicken Sie abschließend auf „Speichern“.

   ![chlimage_1-263](assets/chlimage_1-263.png)

## Berechnen des Umfangs eines Übersetzungsauftrags {#scoping-a-translation-job}

Berechnen Sie den Umfang eines Übersetzungsauftrags, um eine Kostenschätzung für die Übersetzung von Ihrem Übersetzungsdienstleister zu erhalten. Bei der Umfangsberechnung eines Auftrags werden Quelldateien an den Übersetzungsanbieter gesendet, der den Text mit seinem Pool an gespeicherten Übersetzungen (dem sogenannten Translation Memory) vergleicht. In der Regel handelt es sich beim Umfang um die Anzahl der zu übersetzenden Wörter.

Wenden Sie sich an Ihren Übersetzungsanbieter, um weitere Informationen zu den Ergebnissen der Umfangsberechnung zu erhalten.

>[!NOTE]
>
>Die Berechnung des Umfangs ist optional. Sie können einen Übersetzungsauftrag auch ohne Berechnung des Umfangs starten.

Wenn Sie den Umfang eines Übersetzungsauftrags berechnen, lautet der Status des Auftrags `Scope Requested`. Wenn der Übersetzungsanbieter die Berechnung des Umfangs übermittelt, wechselt der Status zu `Scope Completed`. Ist die Berechnung des Umfangs abgeschlossen, können Sie den Befehl Berechnung anzeigen zur Überprüfung der Ergebnisse der Umfangsberechnung verwenden.

Die Umfangsberechnung funktioniert nur dann richtig, wenn der Übersetzungsanbieter diese Funktion unterstützt.

1. Öffnen Sie in der Projektkonsole das Übersetzungsprojekt.
1. Klicken Sie auf der Kachel „Übersetzungsauftrag“ auf das Befehlsmenü und dann auf „Berechnung anfordern“.

   ![chlimage_1-264](assets/chlimage_1-264.png)

1. Wenn der Auftragsstatus zu BERECHNUNG_ABGESCHLOSSEN wechselt, klicken Sie auf der Kachel „Übersetzungsauftrag“ auf das Befehlsmenü und dann auf „Berechnung anzeigen“.

## Starten von Übersetzungsaufträgen {#starting-a-translation-job}

Starten Sie einen Übersetzungsauftrag, um die Quellseiten in die Zielsprache zu übersetzen. Die Übersetzung wird gemäß den Eigenschaftswerten der Kachel „Zusammenfassung der Übersetzung“ durchgeführt.

Nachdem Sie den Übersetzungsauftrag gestartet haben, wird auf der Kachel „Übersetzungsauftrag“ der Status „Übersetzung läuft“ angezeigt.

![chlimage_1-265](assets/chlimage_1-265.png)

1. Öffnen Sie in der Projektkonsole das Übersetzungsprojekt.
1. Klicken Sie auf der Kachel „Übersetzungsauftrag“ auf das Befehlsmenü und dann auf „Starten“. 

   ![chlimage_1-266](assets/chlimage_1-266.png)

1. Klicken Sie im Dialogfeld „Aktion“, das den Start der Übersetzung bestätigt, auf „Schließen“.

## Abbrechen von Übersetzungsaufträgen {#canceling-a-translation-job}

Sie können einen Übersetzungsauftrag abbrechen, um den Übersetzungsprozess zu stoppen und den Übersetzungsanbieter daran zu hindern, weitere Übersetzungen durchzuführen. Sie können einen Auftrag abbrechen, wenn der Auftrag den Status `Committed For Translation` oder `Translation In Progress` hat.

1. Öffnen Sie in der Projektkonsole das Übersetzungsprojekt.
1. Klicken Sie auf der Kachel „Übersetzungsauftrag“ auf das Befehlsmenü und dann auf „Abbrechen“.
1. Klicken Sie im Dialogfeld „Aktion“, das den Abbruch der Übersetzung bestätigt, auf „OK“.

## Workflow zum Akzeptieren/Ablehnen {#accept-reject-workflow}

Wenn die Inhalte nach der Übersetzung zurückgegeben werden und den Status Bereit für Überprüfung aufweisen, können Sie den Übersetzungsauftrag aufrufen und die Inhalte akzeptieren bzw. ablehnen.

![chlimage_1-267](assets/chlimage_1-267.png)

Falls Sie die Option Übersetzung ablehnen auswählen, haben Sie die Möglichkeit, einen Kommentar hinzuzufügen.

![chlimage_1-268](assets/chlimage_1-268.png)

Bei Ablehnung der Inhalte werden diese an den Übersetzungsanbieter zurückgesendet, der dann den Kommentar einsehen kann.

## Überprüfen und Bewerben aktualisierter Inhalte {#reviewing-and-promoting-updated-content}

Wenn Inhalte für eine vorhandene Sprachkopie übersetzt werden, überprüfen Sie die Übersetzungen, nehmen Sie bei Bedarf Änderungen vor und leiten Sie dann die Übersetzungen weiter, um die Übersetzungen in die Sprachkopie zu verschieben. Sie können übersetzte Dateien überprüfen, wenn der Übersetzungsauftrag den Status Bereit für Überprüfung aufweist.

![chlimage_1-269](assets/chlimage_1-269.png)

1. Wählen Sie die Seite zunächst in der Sprachmustervorlage aus, klicken Sie auf „Verweise“ und abschließend auf „Sprachkopien“.
1. Klicken Sie auf die zu überprüfende Sprachkopie.

   ![chlimage_1-270](assets/chlimage_1-270.png)

1. Klicken Sie auf „Launch“, um die Launch-Befehle anzuzeigen.

   ![chlimage_1-271](assets/chlimage_1-271.png)

1. Klicken Sie auf Seite öffnen, um die Launch Copy der zu überprüfenden Seite zu öffnen und die Inhalte zu bearbeiten.
1. Nachdem Sie die Inhalte überprüft und alle notwendigen Änderungen vorgenommen haben, klicken Sie auf Bewerben, um die Launch Copy zu bewerben.
1. Legen Sie auf der Seite „Launch bewerben“ fest, welche Seiten beworben werden sollen, und klicken Sie dann auf „Bewerben“.

## Vergleichen von Sprachkopien {#comparing-language-copies}

So vergleichen Sie Sprachkopien mit der Sprachmustervorlage:

1. Navigieren Sie in der **Sites**-Konsole zur Sprachkopie, die verglichen werden soll.
1. Öffnen Sie das Bedienfeld **[Verweise](/help/sites-authoring/basic-handling.md#references)**.
1. Wählen Sie unter der Überschrift **Kopien** die Option **Sprachkopien** aus.
1. Wählen Sie Ihre spezifische Sprachkopie aus und klicken Sie dann entweder auf **Mit Stamm vergleichen** oder auf **Mit vorherigen vergleichen**, falls zutreffend.

   ![chlimage_1-37](assets/chlimage_1-37.jpeg)

1. Die beiden Seiten (Start und Quelle) werden nebeneinander geöffnet.

   Vollständige Informationen zur Verwendung der Vergleichsfunktion finden Sie unter [Seitenvergleich](/help/sites-authoring/page-diff.md).

## Abschließen und Archivieren von Übersetzungsaufträgen {#completing-and-archiving-translation-jobs}

Schließen Sie einen Übersetzungsauftrag ab, nachdem Sie die übersetzten Dateien vom Anbieter überprüft haben. Beim Workflow „Menschliche Übersetzung“ signalisiert der Abschluss einer Übersetzung dem Übersetzungsanbieter, dass der Übersetzungsauftrag erfüllt wurde und die Übersetzung in seinem Translation Memory gespeichert werden sollte.

Nachdem Sie den Auftrag abgeschlossen haben, hat der Auftrag den Status „Abgeschlossen“.

![chlimage_1-272](assets/chlimage_1-272.png)

Archivieren Sie einen Übersetzungsauftrag, nachdem er abgeschlossen ist und Sie die Auftragsstatusdetails nicht länger einsehen müssen. Wenn Sie den Auftrag archivieren, wird die Kachel „Übersetzungsauftrag“ aus dem Projekt entfernt.

## Erstellen der Struktur einer Sprachkopie {#creating-the-structure-of-a-language-copy}

Füllen Sie Ihre Sprachkopie so, dass sie Inhalte aus der Stammsprache enthält, die Sie übersetzen. Bevor Sie Ihre Sprachkopie füllen, müssen Sie [den Sprachstamm der Sprachkopie erstellt haben](/help/sites-administering/tc-prep.md#creating-a-language-root).

1. Wählen Sie über die Sites-Konsole den Sprachstamm der Primärsprache aus, die Sie als Quelle verwenden. Wählen Sie beispielsweise „Inhalt“ > „Geometrixx Demo Site“ > „Englisch“ aus, um die englischen Seiten der Geometrixx-Demo-Site zu übersetzen.
1. Klicken Sie in der Symbolleiste auf „Verweise“.

   ![chlimage_1-273](assets/chlimage_1-273.png)

1. Wählen Sie die Option Sprachkopien und dann die Sprachkopien aus, die Sie füllen möchten.

   ![chlimage_1-38](assets/chlimage_1-38.jpeg)

1. Klicken Sie auf „Sprachkopien aktualisieren“, um die Übersetzungs-Tools anzuzeigen, und konfigurieren Sie die Eigenschaften:

   * Wählen Sie die Option „Alle Unterseiten auswählen“ aus.
   * Wählen Sie für das Projekt die Option Nur Struktur erstellen aus.

   ![chlimage_1-39](assets/chlimage_1-39.jpeg)

1. Klicken Sie auf „Starten“.

## Verschieben oder Umbenennen einer Quellseite {#move-source}

Wenn eine bereits übersetzte Quellseite [umbenannt oder verschoben](/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page) werden muss, wird beim erneuten Übersetzen der Seite nach der Verschiebung eine Sprachkopie auf Grundlage des neuen Seitennamens/Speicherorts erstellt. Die alte Sprachkopie mit dem vorherigen Namen/Speicherort bleibt bestehen. Um dies zu verhindern, können Sie nach dem Verschieben die Funktion zum Aktualisieren der Sprachkopie verwenden:

1. Verschieben Sie eine Seite mit einer Sprachkopie.
1. Wählen Sie den Sprachkopiestamm aus.
1. Öffnen Sie das Bedienfeld **Verweise**.
1. Wählen Sie **Sprachkopien** aus.
1. Wählen Sie die zu aktualisierenden Zielsprachen aus.
1. Wählen Sie **Sprachkopien aktualisieren** aus.

   ![Aktualisieren der Sprachkopie](assets/translation-move-to.png)

1. Klicken Sie auf **Aktualisieren**. Es wird ein [Launch](/help/sites-authoring/launches-promoting.md) erstellt.
1. Navigieren Sie zum erforderlichen Sprachstamm und wählen Sie ihn aus.
1. Wählen Sie über das Bedienfeld **Verweise** **Launches** aus.

   ![Launch bewerben – Übersetzung](assets/promote-launch-translation.png)

1. Klicken Sie auf den erstellten Launch und dann auf **Launch bewerben**.

Die Quellseite und die zugehörige Sprachkopie wurden nun verschoben.

## Erstellen von Übersetzungsprojekten mithilfe der Projektkonsole {#creating-a-translation-project-using-the-projects-console}

Sie können ein Übersetzungsprojekt manuell erstellen, wenn Sie die Verwendung der Projektkonsole bevorzugen

>[!NOTE]
>
>Um ein Projekt zu erstellen, muss Ihr Konto Mitglied der Gruppe `projects-administrators` sein.

Wenn Sie ein Übersetzungsprojekt manuell erstellen, müssen Sie neben den [grundlegenden Eigenschaften](/help/sites-authoring/touch-ui-managing-projects.md#creating-a-project) Werte für die folgenden übersetzungsspezifischen Eigenschaften angeben:

* **Name:** Dies ist der Projektname.
* **Ausgangssprache:** Die Sprache der Quellinhalte.
* **Zielsprache:** Die Sprache, in die die Inhalte übersetzt werden.
* **Übersetzungsmethode:** Wählen Sie Menschliche Übersetzung aus, um anzugeben, dass die Übersetzung manuell durchgeführt werden soll.

1. Klicken Sie in der Symbolleiste der Projektkonsole auf „Erstellen“.
1. Wählen Sie zunächst die Vorlage „Übersetzungsprojekt“ aus und klicken Sie dann auf „Weiter“.
1. Geben Sie Werte für die grundlegenden Eigenschaften ein.
1. Klicken Sie auf „Erweitert“ und geben Sie Werte für die übersetzungsbezogenen Eigenschaften an.
1. Klicken Sie auf „Erstellen“. Klicken Sie im Bestätigungsfeld auf „Fertig“, um zur Projektkonsole zurückzukehren, oder klicken Sie auf „Projekt öffnen“, um das Projekt zu öffnen und zu verwalten.

## Exportieren von Übersetzungsaufträgen {#exporting-a-translation-job}

Sie können die Inhalte eines Übersetzungsauftrags herunterladen, um sie z. B. an einen Übersetzungsanbieter zu senden, der nicht über einen Connector in AEM integriert ist, oder um die Inhalte zu überprüfen.

1. Klicken Sie im Dropdown-Menü der Kachel „Übersetzungsauftrag“ auf „Exportieren“.
1. Klicken Sie im Dialogfeld „Exportieren“ auf „Exportierte Datei herunterladen“ und speichern Sie die Datei ggf. über das Dialogfeld des Webbrowsers.
1. Klicken Sie im Dialogfeld „Exportieren“ auf „Schließen“.

## Importieren von Übersetzungsaufträgen {#importing-a-translation-job}

Sie können übersetzte Inhalte in AEM importieren, zum Beispiel wenn Ihr Übersetzungsanbieter die Inhalte an Sie sendet, da er nicht über einen Connector in AEM integriert ist.

1. Klicken Sie im Dropdown-Menü der Kachel „Übersetzungsauftrag“ auf „Importieren“.
1. Wählen Sie im Dialogfeld des Webbrowsers die zu importierende Datei aus.
1. Klicken Sie im Dialogfeld „Importieren“ auf „Schließen“.
