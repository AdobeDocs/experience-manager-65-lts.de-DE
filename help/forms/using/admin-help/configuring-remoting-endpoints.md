---
title: Konfigurieren der Remoting-Endpunkte
description: Erfahren Sie, wie Sie Remoting-Endpunkte konfigurieren.  In diesem Dokument wird erläutert, wie Sie eine Anwendung aktivieren, die mit Flex erstellt wurde, um den Dienst mithilfe von AEM Forms Remoting aufzurufen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: d19b7265-42cc-41d9-9897-e7b044c4529c
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 100%

---

# Konfigurieren der Remoting-Endpunkte {#configuring-remoting-endpoints}

Ein Remoting-Endpunkt aktiviert eine Anwendung, die mit Flex erstellt wurde, um den Dienst mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt) aufzurufen.  Ein Remoting-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt. Ein Flex-Ziel mit demselben Namen wie der Endpunkt wird erstellt, und Flex-Kundinnen und -Kunden können Remote-Objekte erstellen, die auf dieses Ziel verweisen, um Vorgänge für den entsprechenden Service aufzurufen.

## Remoting-Endpunkteinstellungen {#remoting-endpoint-settings}

**Flex-Client-Authentifizierungsmethode**: Bestimmt den Typ der Antwort, die der Server zum Client zurücksendet, wenn die Sicherheit für den aufgerufenen Service aktiviert ist, der Vorgang keine anonymen Aufrufe unterstützt und der Client keine oder ungültige Anmeldeinformationen übergibt.
