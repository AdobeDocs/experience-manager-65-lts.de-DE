---
title: Anpassen von Registerkarten für eine Aufgabe
description: Erfahren Sie, wie Sie die Namen der Registerkarten für Ihre Aufgaben in LiveCycle AEM Forms Workspace anpassen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 88f5093c-f249-4e4b-900a-5897f47e513c
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 100%

---

# Anpassen von Registerkarten für eine Aufgabe {#customizing-tabs-for-a-task}

Sie können benutzerdefinierte Registerkartennamen für die `Start Process`-Komponente in der Uber-Ansicht von `Start Process` und für die `Task Details`-Komponente in der Uber-Ansicht von `ToDo` festlegen.

1. Befolgen Sie die [generischen Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Ändern Sie den Wert von `tabname` in der Datei `translation.json`.

   Ändern Sie zum Beispiel für Englisch folgende Änderungen an „`/apps/ws/locales/en-US/translation.json`/“ vor.

   * Für Aufgaben, die im Startprozess initiiert werden, verwenden Sie folgenden Code-Ausschnitt aus dem Block `"startprocess" : {}`.

   ```json
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Für Aufgaben in „Aufgaben“ verwenden Sie folgenden Code-Ausschnitt aus dem Block `"todo" : {}`.

   ```json
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >Fügen Sie das entsprechende Schlüssel-Wert-Paar für alle unterstützten Sprachen hinzu.
