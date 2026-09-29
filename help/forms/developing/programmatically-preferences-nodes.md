---
title: Programmgesteuerte Verwaltung der PreferencesNodes
description: Verwenden Sie die Preferences Manager Service-API (Java), um die Voreinstellungsknoten programmgesteuert zu verwalten.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 95a83858-c0b7-4c68-b4a9-d525bfc663c0
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 516393bc-fa69-5e74-a04e-f7ec9ffe2c5e
    internal-label: APIs & Integrations
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 49%
---
# Programmgesteuerte Verwaltung der Voreinstellungsknoten {#programmatically-managing-the-preferencesnodes}

**Die Beispiele in diesem Dokument gelten nur für AEM Forms in der JEE-Umgebung.**

In diesem Thema wird beschrieben, wie Sie mit der Preferences Manager Service-API (Java) die Voreinstellungsknoten programmgesteuert verwalten können.

Sie können die Konfigurationseinstellungen über die Administrator-Benutzeroberfläche manuell ändern. Um die Optionen zu ändern, navigieren Sie zu `Home>Settings>User Management> Configuration>Manual Configuration`. Wenn Sie `config.xml` importieren, nachdem Sie die Änderungen vorgenommen haben, werden Sie feststellen, dass alle Änderungen mit Ausnahme der Änderungen am Knoten `/Adobe/Adobe Experience Manager Forms/Config/UM persist` verloren gegangen sind. Die Vorschau von Import und Export für User Management unterstützt nicht das Ändern von Konfigurationseinstellungen für andere Komponenten. Diese Änderungen können jetzt mithilfe der `PreferencesManagerServiceClient`-APIs vorgenommen werden.

**Zusammenfassung der Schritte**
Gehen Sie wie folgt vor, um die Voreinstellungsknoten programmgesteuert zu verwalten:

1. Schließen Sie die Projektdateien ein.
1. Erstellen Sie einen`PreferencesManagerService`-Client.
1. Rufen Sie die entsprechenden Rollen- oder Berechtigungsvorgänge auf.

**Schließen Sie die Projektdateien ein**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines `PreferencesManagerService` Clients**

Bevor Sie einen User Management-`PreferencesManagerService` programmgesteuert durchführen können, müssen Sie einen `PreferencesManagerService`-Client erstellen. Erstellen Sie mit der Java-API ein `PreferencesManagerServiceClient`.

**Aufrufen der entsprechenden Rollen- oder Berechtigungsvorgänge**

Nachdem Sie den Service-Client erstellt haben, können Sie dann die Voreinstellungs-Manager-Vorgänge aufrufen. Mit dem Service-Client können Sie Berechtigungen lesen und festlegen.
