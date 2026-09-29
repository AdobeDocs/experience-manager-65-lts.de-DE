---
title: Konfigurieren freigegebener Warteschlangen
description: Mit freigegebenen Warteschlangen können Sie Benutzerwarteschlangen effektiv konfigurieren und verwalten. Erfahren Sie, wie Sie freigegebene Warteschlangen konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 6665b95a-39fd-472a-b3b5-8b97257c69a7
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 83%
---
# Konfigurieren freigegebener Warteschlangen{#configuring-shared-queues}

Mit freigegebenen Warteschlangen können Sie Benutzerwarteschlangen effektiv konfigurieren und verwalten. Eine Benutzerwarteschlange besteht einfach aus allen Aufgaben, die Benutzenden zugewiesen sind. Weitere Informationen finden Sie unter [Aufgabenlisten](https://help.adobe.com/de_DE/livecycle/11.0/WorkspaceHelp/WS92d06802c76abadb-2b6ab502126beb6ba2f-7ffc.2.html). Sie können Benutzerwarteschlangen entsprechend Ihren organisatorischen Anforderungen zuweisen, die Zuweisung aufheben und neu zuweisen. Sie können freigegebene Warteschlangen auf zwei Arten verwalten:

**Zugriff auf einen Benutzer verwalten**

Mit dieser Option können Sie den Zugriff auf eine ausgewählte Benutzerwarteschlange verwalten.

**Zugriff durch einen Benutzer verwalten**

Mit dieser Option können Sie freigegebene Warteschlangen verwalten, die einer ausgewählten Person zugewiesen sind.

## Verwalten des Zugriffs auf eine ausgewählte Benutzerwarteschlange {#managing-access-to-a-selected-user-queue}

Mit der Funktion „Zugriff auf einen Benutzer verwalten“ können Sie den Zugriff auf eine ausgewählte Benutzerwarteschlange verwalten. Sie können anderen Benutzenden in Ihrer Organisation Zugriff auf eine ausgewählte Benutzerwarteschlange gewähren oder widerrufen. Zum Beispiel: Sarah Müller ist außer Haus. Mit der Funktion „Zugriff auf einen Benutzer verwalten“ kann ihre Warteschlange zur Fertigstellung für Anna Bauer und Jakob Wagner freigegeben werden. Wenn Sarah später ins Büro zurückkehrt, können Sie den Zugriff auf ihre Warteschlange von Anna Bauer und Jakob Wagner widerrufen.

Nach der Freigabe können diese Aufgaben von der Person mit Zugriff auf die Warteschlange mithilfe von Workspace abgeschlossen werden.

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.

### Konfigurieren des Zugriffs auf eine ausgewählte Benutzerwarteschlange {#configuring-access-to-a-selected-user-queue}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

1. Melden Sie sich mit einem Adminkonto bei der Administrationskonsole an.
1. Wählen Sie **Dienste** > **Forms-Workflow** > **Freigegebene Warteschlange**.

1. Suchen Sie auf der Registerkarte Zugriff auf einen Benutzer verwalten den Benutzer, dessen Warteschlange Sie freigeben möchten, und wählen Sie ihn aus. Das untere rechte Fenster zeigt die Liste der Benutzenden an, die Zugriff auf die ausgewählte Benutzerwarteschlange haben.
1. Wählen Sie im unteren linken Bereich die Benutzerin bzw. den Benutzer aus. Klicken Sie auf „Freigeben“.
1. Klicken Sie zum Abschluss auf „Speichern“.

### Sperren des Zugriffs auf eine ausgewählte Benutzerwarteschlange {#revoking-access-to-a-selected-user-queue}

1. Melden Sie sich mit einem Adminkonto bei der Administrationskonsole an.
1. Wählen Sie **Dienste** > **Forms-Workflow** > **Freigegebene Warteschlange**.

1. Suchen Sie auf der Registerkarte Zugriff auf einen Benutzer verwalten den Benutzer, den Sie verwalten möchten, und wählen Sie ihn aus.
1. Im rechten unteren Bereich wird die Liste der Benutzenden mit Zugriff auf die ausgewählte Benutzerwarteschlange angezeigt. Wählen Sie die Person aus und klicken Sie auf „Widerrufen“.
1. Klicken Sie zum Abschluss auf „Speichern“.

## Verwalten der Warteschlangen, die einer Person zugewiesen sind {#managing-queues-assigned-to-a-user}

Mit der Funktion „Zugriff durch einen Benutzer verwalten“ können Sie Warteschlangen verwalten, die einer ausgewählten Person zugewiesen sind. Sie können einer ausgewählten Person einzeln Zugriff auf Benutzerwarteschlangen gewähren oder widerrufen. Beispielsweise können Sie Kara Bowman die Benutzerwarteschlangen Akira Tanaka und John Jacobs zuweisen. Mit der Funktion „Zugriff durch einen Benutzer verwalten“ können Sie nach Sarah Müller suchen und ihr Zugriff auf Aufgaben gewähren, die Anna Bauer und Jakob Wagner zugewiesen sind. Zu einem späteren Zeitpunkt können Sie den Zugriff von Sarah Müller auf diese Benutzerwarteschlangen widerrufen.

Nach der Zuweisung können diese Aufgaben von der Person, der Workspace verwendet, ausgeführt werden.

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.

### Gewähren des Zugriffs auf eine ausgewählte Benutzerwarteschlange {#granting-access-to-a-selected-user-queue}

1. Melden Sie sich mit einem Adminkonto bei der Administrationskonsole an.
1. Wählen Sie **Dienste** > **Forms-Workflow** > **Freigegebene Warteschlange**.

1. Suchen Sie auf der Registerkarte Zugriff auf einen Benutzer verwalten den Benutzer, dessen Warteschlange Sie freigeben möchten, und wählen Sie ihn aus. Das untere rechte Fenster zeigt die Liste der Benutzenden an, die Zugriff auf die ausgewählte Benutzerwarteschlange haben.
1. Suchen Sie im linken unteren Fensterbereich nach Benutzerwarteschlangen, die Sie für den ausgewählten Benutzer freigeben möchten, und wählen Sie sie aus. Klicken Sie auf „Freigeben“.
1. Klicken Sie zum Abschluss auf „Speichern“.

### Sperren des Zugriffs auf eine ausgewählte Benutzerwarteschlange {#revoking_access_to_a_selected_user_queue-1}

1. Melden Sie sich mit einem Adminkonto bei der Administrationskonsole an.
1. Wählen Sie **Dienste** > **Forms-Workflow** > **Freigegebene Warteschlange**.

1. Suchen Sie auf der Registerkarte Zugriff durch einen Benutzer verwalten den Benutzer, dessen Warteschlange Sie verwalten möchten, und wählen Sie ihn aus.
1. Im rechten unteren Bereich wird die Liste der Benutzerwarteschlangen angezeigt, die der ausgewählten Person zugewiesen sind. Wählen Sie die Benutzerwarteschlange und klicken Sie auf „Widerrufen“.
1. Klicken Sie zum Abschluss auf „Speichern“.
