---
title: Konfigurieren der AEM DS-Einstellungen
description: Erfahren Sie, wie Sie die URL des Verarbeitungs-Servers angeben, bevor Sie ein Formular übermitteln.
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: 8ad3afd6-e1c6-4f21-bb0f-4d97ef50710e
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 89%

---

# Konfigurieren der AEM DS-Einstellungen{#configuring-aem-ds-settings}

In diesem Artikel wird beschrieben, wie Sie den **AEM DS-Einstellungsdienst** konfigurieren. Diese Einstellung kann in mehreren Szenarien verwendet werden, zum Beispiel:

* In Correspondence Management

   * zur AEM Forms Workflow-Konfiguration
   * bei Verwendung des Formularportals zur Remote-Speicherung von Entwürfen/Übermittlung

* in adaptiven Formularen für Fälle, in denen ein adaptives Formular aus der Veröffentlichungsinstanz übermittelt wird

Führen Sie die folgenden Schritte aus, um die **[!UICONTROL AEM DS-Einstellungen]** zu konfigurieren:

1. Öffnen Sie den Konfigurations-Manager unter der Veröffentlichungsinstanz mit der URL:\
   *https://localhost:port/system/console/configMgr*

   ![AEM-Web-Konsolenkonfiguration](assets/web_configuration_console_new.png)

1. Klicken Sie im Fenster **[!UICONTROL Adobe Experience Manager Web-Konsolenkonfiguration]** auf die Option **[!UICONTROL AEM DS-Einstellungen]**.

   ![DS-Einstellungen](assets/ds_settings_new.png)

1. Das Fenster **[!UICONTROL AEM DS-Einstellungendienst]** zeigt die allgemeinen Konfigurationseinstellungen für AEM DS-Komponenten.

   ![DS-Einstellungs-Service](assets/ds_settings_service_new.png)

1. Fügen Sie die folgenden Informationen in die entsprechenden Felder ein:

   **[!UICONTROL Processing Server URL]** (Verarbeitungs-Server-URL): Der Verarbeitungs-Server ist der Server, auf dem der Forms- oder AEM-Workflow ausgelöst werden muss. Dabei kann es sich um die gleiche URL wie die der AEM-Autoreninstanz oder die andere Server-URL handeln (d. h. https://localhost:port/).

   **[!UICONTROL Verarbeitungs-Server-Benutzername]**: Benutzername des Workflow-Benutzers [basiert auf der verwendeten Server-URL]

   **[!UICONTROL Verarbeitungs-Server-Kennwort]**: Dies ist das Kennwort der Benutzenden des Workflows.

   >[!NOTE]
   >
   >
   >    
   >    
   >    * Wenn Sie Forms- oder AEM-Workflows verwenden, müssen Sie den DS-Einstellungsdienst konfigurieren, bevor Sie Übermittlungen vom Veröffentlichungs-Server durchführen. Andernfalls schlägt die Formularübermittlung fehl.
   >    
   >
