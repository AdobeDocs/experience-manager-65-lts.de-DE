---
title: Der Bulk Editor
description: Erfahren Sie, wie Sie den Bulk Editor für eine effiziente Bearbeitung verwenden können, wenn der visuelle Seitenkontext nicht benötigt wird.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Configuring
role: Admin
exl-id: 8028e74e-29df-4081-a567-5eb87ae362d4
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 97%

---

# Der Bulk Editor{#the-bulk-editor}

Der Bulk Editor ermöglicht eine äußerst effiziente Bearbeitung, wenn der visuelle Seitenkontext nicht benötigt wird. Sie können damit:

* Inhalte von mehreren Seiten suchen (und anzeigen), wozu GQL (Google Query Language) genutzt wird
* diese Inhalte direkt im Bulk Editor bearbeiten
* die Änderungen speichern (in den Originalseiten)
* diese Inhalte in eine tabulatorgetrennte Tabellendatei (.tsv) exportieren

>[!NOTE]
>
>Sie können auch Inhalte in das Repository importieren. Standardmäßig ist diese Option für den Bulk Editor aber deaktiviert, wie er in der **Tools**-Konsole verfügbar ist.

In diesem Abschnitt wird erläutert, wie Sie mit dem Bulk Editor in der **Tools**-Konsole arbeiten. Typischerweise nutzen Admins den Bulk Editor, um mehrere Elemente zu suchen und zu bearbeiten. Zu diesem Zweck wird die Tabelle mit einer GQL-Abfrage aufgefüllt, gefolgt von der Auswahl der zu bearbeitenden Inhaltselemente. Autorinnen und Autoren nutzen den Bulk Editor in der Regel als Teil einer benutzerdefinierten Bulk-Editor-Anwendung, die über die [Produktlisten](/help/sites-authoring/default-components.md#productlist)-Komponente zugänglich ist.

>[!CAUTION]
>
>Mit der Einstellung der klassischen Benutzeroberfläche in AEM 6.4 wird auch der Bulk Editor eingestellt. Daher plant Adobe keine weitere Verbesserung des Bulk Editors.

## Beispielhafter Anwendungsfall für den Bulk Editor {#example-use-case-for-the-bulk-editor}

Wenn Sie beispielsweise alle Namen und E-Mail-Adressen von Benutzenden benötigen, die an einer bestimmten Umfrage teilgenommen haben, kann Ihnen der Bulk Editor diese Daten zur Verfügung stellen, und Sie können sie in eine Tabelle exportieren.

Ein Beispiel, das einen solchen Anwendungsfall veranschaulicht, ist auf der Geometrixx-Website enthalten:

1. Navigieren Sie zur Seite **Support** und dann zur Umfrage zur **Zufriedenheit mit dem Kunden-Service**.
1. **Bearbeiten** Sie den Absatz **Beginn des Formulars**. Klicken Sie im Dialogfeld auf die Registerkarte **Erweitert**, erweitern Sie den Bereich **Aktionskonfiguration** und klicken Sie dann auf **Daten anzeigen**.

   ![Beispiel für eine Umfrage zur Kundenzufriedenheit](assets/custsatsurvey.png)

1. Der Bulk Editor ist vollständig anpassbar, auch wenn in diesem Beispiel die Benutzenden keine Inhalte bearbeiten, sondern nur die Daten in eine Tabelle exportieren können.

   ![Bulk Editor-Konsole](assets/bulkeditor.png)

## Arbeiten mit dem Bulk Editor {#how-to-use-the-bulk-editor}

Mit dem Bulk Editor können Sie:

* [basierend auf Abfrageparametern nach Inhalten suchen, festgelegte Eigenschaften der Ergebnisse in Spalten anzeigen, diese Inhalte bearbeiten und die Änderungen speichern](#searching-and-editing-content)
* [diese Inhalte in eine tabulatorgetrennte Tabelle exportieren](#exporting-content)

* [Inhalte aus einer tabulatorgetrennten Tabelle importieren](#importing-content)

### Suchen und Bearbeiten von Inhalten {#searching-and-editing-content}

So bearbeiten Sie mit dem Bulk Editor mehrere Elemente gleichzeitig:

1. Klicken Sie in der **Tools**-Konsole auf den Ordner für **Import-Tools**, um ihn zu erweitern.
1. Doppelklicken Sie auf den **Bulk Editor**.
1. Geben Sie die Auswahlanforderungen ein:

<table>
 <tbody>
  <tr>
   <td>Feld</td>
   <td>Eigenschaft</td>
  </tr>
  <tr>
   <td>Stammverzeichnis</td>
   <td>Hiermit wird das Stammverzeichnis angegeben, das der Bulk Editor durchsucht.<br /> Zum Beispiel <code>/content/geometrixx/en</code>. Der Bulk Editor durchsucht alle untergeordneten Knoten.</td>
  </tr>
  <tr>
   <td>Abfrageparameter</td>
   <td>Geben Sie mithilfe von GQL-Parametern die Suchzeichenfolge ein, nach der der Bulk Editor im Repository suchen soll. Beispielsweise wird mit <code>type:Page</code> nach allen Seiten im Stammverzeichnis gesucht, mit <code>text:professional</code> nach allen Seiten, die das Wort „professional“ enthalten, und mit <code>"jcr:title":English</code> nach allen Seiten, die „English“ als Titel aufweisen. Sie können nur nach Zeichenfolgen suchen.</td>
  </tr>
  <tr>
   <td>Kontrollkästchen „Inhaltsmodus“</td>
   <td>Aktivieren Sie dieses Kontrollkästchen, um die Eigenschaften im Unterknoten <code>jcr:content</code> der Suchergebnisse zu lesen, sofern vorhanden. Diese Option ist nur für Seiten nutzbar. Eigenschaftsnamen erhalten das Präfix <code>"jcr:content/"</code></td>
  </tr>
  <tr>
   <td>Eigenschaften/Spalten</td>
   <td>Aktivieren Sie die Kontrollkästchen für die Eigenschaften, die der Bulk Editor zurückgeben soll. Die ausgewählten Eigenschaften stellen die Spaltenüberschriften im Ergebnisbereich dar. Der Knotenpfad wird standardmäßig in den Ergebnissen angezeigt.</td>
  </tr>
  <tr>
   <td>Benutzerdefinierte Eigenschaften/Spalten</td>
   <td>Geben Sie alle anderen Eigenschaften ein, die nicht im Feld <strong>Eigenschaften/Spalten</strong> aufgeführt sind. Diese benutzerdefinierten Eigenschaften werden im Ergebnisbereich angezeigt.  Sie können mehrere Eigenschaften hinzufügen, indem Sie sie mit Kommas voneinander trennen.  <i>Hinweis:</i> Wenn Sie eine benutzerdefinierte Eigenschaft hinzufügen, die noch nicht vorhanden ist, zeigt AEM WCM eine leere Zelle an. Wenn Sie die leere Zelle bearbeiten und speichern, wird die Eigenschaft zum Knoten hinzugefügt.  Die neu erstellte Eigenschaft muss die Einschränkungen des Knotentyps und die Eigenschafts-Namespaces einhalten.</td>
  </tr>
 </tbody>
</table>

Beispiel:

![Filteroptionen für den Bulk Editor](assets/searchfilter.png)

1. Klicken Sie auf **Suchen**. Der Bulk Editor zeigt die Suchergebnisse an.
Im Beispiel oben werden alle Seiten, die Ihren Suchkriterien entsprechen, zurückgegeben und in den geforderten Spalten angezeigt.

   ![Ergebnisse des Bulk Editors](assets/chlimage_1-39.png)

1. Doppelklicken Sie auf eine Zelle, damit Sie Änderungen vornehmen können.

   ![Massenbearbeitung](assets/srchresultedit.png)

1. Klicken Sie auf **Speichern**, um die Änderungen zu speichern. (Die Schaltfläche **Speichern** wird aktiviert, wenn Sie eine Zelle bearbeitet haben.)

   >[!CAUTION]
   >
   >Die hier vorgenommenen Änderungen werden in den Repository-Inhalt geschrieben, z. B. die Seite, auf die unter **Pfad** verwiesen wird.

#### Weitere GQL-Abfrageparameter {#additional-gql-query-parameters}

* **path:** Durchsucht nur Knoten unter diesem Pfad. Wenn Sie mehr als einen Begriff mit einem Pfad-Präfix festlegen, wird nur das letzte berücksichtigt.
* **type:** Gibt nur Knoten des angegebenen Knotentyps zurück. Das schließt primäre und Mixin-Typen ein.  Sie können mehrere Knotentypen durch Kommas voneinander getrennt festlegen.  GQL gibt Knoten zurück, die einen der festgelegten Typen aufweisen.
* **order:** Sortiert das Ergebnis nach den bestimmten Eigenschaften. Sie können mehrere Eigenschaftsnamen durch Kommas voneinander getrennt festlegen.  Um das Ergebnis in absteigender Reihenfolge zu sortieren, setzen Sie einfach ein Minuszeichen als Präfix des Eigenschaftsnamens. Zum Beispiel: order:-name.  Ein Pluszeichen gibt das Ergebnis in aufsteigender Reihenfolge zurück. Dies ist auch die Standardeinstellung.
* **limit:** Begrenzt die Anzahl der Ergebnisse mithilfe eines Intervalls. Beispiel: limit:10..20. Das Intervall basiert auf null. Der Startwert ist ein-, der Endwert ausgeschlossen. Sie können auch ein offenes `interval:limit:10..` oder `limit:..20` angeben
Wenn Sie die Punkte weglassen und nur einen Wert angeben, gibt GQL höchstens diese Anzahl an Ergebnissen zurück. Beispiel: `limit:10` (gibt die ersten zehn Ergebnisse zurück).

### Exportieren von Inhalten {#exporting-content}

Exportieren Sie bei Bedarf Inhalte in eine Excel-Tabelle, um Änderungen vorzunehmen. Vielleicht möchten Sie z. B. eine Mailing-Liste exportieren und die Vorwahl aller aufgeführten Telefonnummern direkt in Excel ändern oder zusätzliche Zeilen hinzufügen.

So exportieren Sie Inhalte:

1. Suchen Sie wie in [Suchen und Bearbeiten von Inhalten](#searching-and-editing-content) beschrieben nach Inhalten.
1. Klicken Sie auf **Exportieren**, um die Änderungen in eine tabulatorgetrennte Excel-Tabelle zu exportieren. AEM WCM fragt Sie, in welches Verzeichnis Sie die Datei herunterladen möchten.

   >[!NOTE]
   >
   >Die Änderungen sind standardmäßig in [Windows-1252](https://de.wikipedia.org/wiki/Windows-1252) (auch als CP-1252 bekannt) kodiert. Sie können UTF-8 auswählen, um die Änderungen in UTF-8 zu exportieren.

   ![Exportieren von Ergebnissen](assets/srchrsesultexport.png)

1. Wählen Sie den Speicherort aus und bestätigen Sie, dass Sie die Datei herunterladen möchten.
1. Nach dem Herunterladen der Datei können Sie diese in einem Tabellenprogramm öffnen, z. B. in Microsoft® Excel. Das Tabellenprogramm importiert die Datei und konvertiert sie in ein Tabellenformat.

   ![Exportierte Ergebnisse in einer Tabelle](assets/exportinexcel.png)

### Importieren von Inhalten {#importing-content}

Standardmäßig ist die Importfunktion ausgeblendet, wenn Sie den Bulk Editor öffnen. Wenn Sie den Parameter `hib=false` zur URL hinzufügen, wird die Schaltfläche **Importieren** auf der Bulk Editor-Seite angezeigt. Sie können Inhalte aus jeder tabulatorgetrennten Datei (`.tsv`) importieren. Damit der Importvorgang ordnungsgemäß funktioniert, müssen die Spaltenüberschriften (die erste Reihe an Zellen) mit den Spaltenüberschriften der zu importierenden Tabelle übereinstimmen.

>[!NOTE]
>
>Wenn Sie Inhalte erneut importieren, löschen Sie alle vorherigen Inhalte dieser Knoten. Achten Sie darauf, keine wichtigen Daten zu überschreiben.

So importieren Sie Inhalte:

1. Öffnen Sie den Bulk Editor.
1. Fügen Sie `?hib=false` zur URL hinzu, z. B.:
   `https://localhost:4502/etc/importers/bulkeditor.html?hib=false`
1. Wählen Sie **Importieren** aus.
1. Wählen Sie die `.tsv`-Datei aus. Die Daten werden in das Repository importiert.
