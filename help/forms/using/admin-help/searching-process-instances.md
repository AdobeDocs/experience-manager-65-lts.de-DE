---
title: Nach Prozessinstanzen suchen
description: Verwenden Sie die Seite „Prozesssuche“, um Suchkriterien zum Auffinden einer Prozessinstanz einzugeben.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: e358ee51-c23f-4737-9dcf-3193ed541bbb
source-git-commit: 51342861dd01e659999c19fbe0274e8d3cbcf8c4
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 66%

---

# Nach Prozessinstanzen suchen{#searching-for-process-instances}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Verwenden Sie die Seite „Prozesssuche“, um Suchkriterien zum Auffinden einer Prozessinstanz einzugeben. Sie können über die Forms Workflow-Seite auf die Seite „Prozesssuche“ zugreifen. Oder klicken Sie auf **Seite „Prozessinstanz** auf „Suchen“.

Sie können grundlegende Kriterien zur Durchführung einer allgemeinen Suche eingeben, spezifische Attribute zur Durchführung einer Detailsuche oder eine Kombination aus grundlegenden Kriterien und spezifischen Attributen zur Durchführung einer kombinierten Suche.

## Durchführen einer allgemeinen Suche {#perform-a-general-search}

Eine allgemeine Suche nach einem Prozess ist am besten geeignet, wenn Sie die Prozess-ID der Prozessinstanz kennen. Oder wenn Sie nach einer Gruppe verwandter Prozessinstanzen suchen oder wenn nur wenige Prozessinstanzen ausgeführt werden.

Geben Sie die grundlegenden Kriterien ein, um eine allgemeine Suche durchzuführen. Wenn Sie mehrere Kriterien eingeben, wird die Suche mit einer impliziten UND-Bedingung ausgeführt.

1. Klicken Sie in Administration Console auf „Services“ > &quot;Forms Workflow&quot; > „Prozesssuche“.
1. Geben Sie auf der Seite „Prozesssuche“ unter „Allgemeine Suche“ die folgenden Kriterien ein:

   * **Prozess-ID:** Die positive Ganzzahl, die jede eindeutige Prozessinstanz identifiziert.
   * **Prozessstatus:** Wählen Sie den gewünschten Status in der Liste.
   * **Programm:** Wählen Sie das gewünschte Programm in der Liste. Nur bereitgestellte Programme werden angezeigt.
   * **Prozessname/-version:** Wählen Sie einen Prozessnamen im Menü. Nur bereitgestellte Prozesse werden angezeigt.

1. Klicken Sie auf **Suchen**. Die Seite Prozessinstanz wird mit den gefundenen Instanzen angezeigt.

## Durchführen einer Detailsuche nach einem Prozess {#perform-a-detailed-search-for-a-process}

Zum Durchführen einer Detailsuche geben Sie spezifische Attribute ein. Eine Detailsuche eignet sich am besten, wenn zahlreiche Prozessinstanzen ausgeführt werden und Sie die möglichen Suchergebnisse durch bestimmte Kriterien einschränken müssen.

1. Klicken Sie in Administration Console auf „Services“ > &quot;Forms Workflow&quot; > „Prozesssuche“.
1. Geben Sie auf der Seite „Prozesssuche“ unter „Detailsuche“ den ersten Kriteriensatz an:

   * Wählen Sie in der Liste „Attribut“ ein Attribut aus.
   * Wählen Sie in der Liste „Filter“ einen Operator aus.
   * Geben Sie in das Feld „Wert“ einen dem ausgewählten Attribut entsprechenden Wert ein.

1. Wählen Sie zum Hinzufügen einer weiteren Zeile „Mehr Filter“ aus. Ein weiterer Satz von „Attribut“-, „Filter“- sowie „Wert“-Listen und die Liste „Bedingung“ werden angezeigt.
1. Wählen Sie unter „Bedingung“ UND oder ODER. Wiederholen Sie die Schritte 1 bis 3 nach Bedarf, um die Suche weiter einzuschränken.
1. Klicken Sie zum Hinzufügen oder Löschen von Zeilen auf „Mehr Filter“ oder „Weniger Filter“. Es können eine bis vier Zeilen verwendet werden.
1. Klicken Sie auf **Suchen**. Die Seite Prozessinstanz wird mit den gefundenen Instanzen angezeigt.

Siehe auch [Über Prozessinstanzstatus](/help/forms/using/admin-help/processes.md#about-process-instance-statuses).

## Durchführen einer kombinierten Suche nach einem Prozess {#perform-a-combined-search-for-a-process}

Um eine Suche zu erstellen, die sowohl allgemeine als auch detaillierte Kriterien verwendet, geben Sie Werte in beide Bereiche auf der Seite „Prozesssuche“ ein. Das System wendet eine implizite `AND` zwischen den beiden Bereichen an.

Wenn die Suche zu eng gefasst ist, werden keine Instanzen gefunden.
