---
title: Konfigurieren des Connectors für Microsoft SharePoint
description: Konfigurieren Sie Connector für Microsoft SharePoint, um die Kommunikation zwischen AEM Forms und Microsoft SharePoint zu ermöglichen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
hide: true
removedfrom6.5.2025: 'yes'
exl-id: d1575576-3a05-496c-b683-bb5badc02711
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
source-wordcount: '223'
ht-degree: 100%
---
# Connector für Microsoft SharePoint konfigurieren {#configuring-connector-for-microsoft-sharepoint}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Connector für Microsoft SharePoint ermöglicht die Kommunikation zwischen AEM Forms und Microsoft SharePoint. Weitere Hintergrundinformationen finden Sie unter „Connector-Dienste für ECM“ in der [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Connector für Microsoft SharePoint“.
1. Geben Sie die folgenden Einstellungen für Ihren SharePoint-Server an:

   **Hostname des SharePoint-Servers:** Die Hostnamen-Anschlussnummer der Webanwendung auf dem SharePoint-Server im Format `[hostname]:'port'`.

   **Benutzername:** Das Benutzerkonto, das zum Herstellen einer Verbindung mit dem SharePoint-Server verwendet wird.

   **Kennwort:** Das Kennwort für das Benutzerkonto, das zum Herstellen einer Verbindung mit dem SharePoint-Server verwendet wird.

   **Domain-Name:** Die Domain, in der sich der SharePoint-Server befindet.

1. Klicken Sie auf Speichern.

## Microsoft SharePoint-Konfigurationsdienst {#microsoft-sharepoint-configuration-service}

Mit dem Microsoft SharePoint-Konfigurations-Service (`(MSSharePointConfigService)`) können Sie Anmeldedaten für den AEM Forms-Benutzer angeben, der über die Berechtigung zum Identitätswechsel verfügt. Weitere Informationen zu Berechtigungen zum Identitätswechsel finden Sie unter [Connector für Microsoft SharePoint konfigurieren](https://help.adobe.com/de_DE/AEMForms/6.1/SharePointConfig/index.html). Führen Sie folgende Schritte aus, um die Einstellungen für `MSSharePointConfigService` anzugeben:

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Durchlaufen Sie die Liste der Dienste und klicken Sie auf `MSSharePointConfigService`.
1. Geben Sie auf der Seite „Konfiguration“ die folgenden Einstellungen an:

   * Benutzername für Benutzer mit Berechtigungen zum Identitätswechsel
   * Kennwort für oben genannten Benutzer

1. Klicken Sie auf Speichern.
