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
hidefromtoc: true
exl-id: 95a83858-c0b7-4c68-b4a9-d525bfc663c0
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 100%

---

# Programmgesteuerte Verwaltung der Voreinstellungsknoten {#programmatically-managing-the-preferencesnodes}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

In diesem Artikel wird beschrieben, wie Sie die Preferences Manager Service-API (Java) verwenden können, um die Voreinstellungsknoten programmgesteuert zu verwalten.

Sie können die Konfigurationseinstellungen über die Administrator-Benutzeroberfläche manuell ändern. Um die Optionen zu ändern, navigieren Sie zu `Home>Settings>User Management> Configuration>Manual Configuration`. Wenn Sie `config.xml` importieren, nachdem Sie die Änderungen vorgenommen haben, werden Sie feststellen, dass alle Änderungen mit Ausnahme der Änderungen am Knoten `/Adobe/Adobe Experience Manager Forms/Config/UM persist` verloren gegangen sind. Die Vorschau von Import und Export für User Management unterstützt nicht das Ändern von Konfigurationseinstellungen für andere Komponenten. Diese Änderungen können jetzt mithilfe der `PreferencesManagerServiceClient`-APIs vorgenommen werden.

**Zusammenfassung der Schritte** Um die Voreinstellungsknoten programmgesteuert zu verwalten, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen eines PreferencesManagerService-Clients
1. Aufrufen der entsprechenden Rollen- oder Berechtigungsvorgänge

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PreferencesManagerService-Clients**

Bevor Sie einen PreferencesManagerService-Vorgang für das User Management programmgesteuert durchführen können, müssen Sie einen PreferencesManagerService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein PreferencesManagerServiceClient-Objekt erstellt wird.

**Aufrufen der entsprechenden Rollen- oder Berechtigungsvorgänge**

Nachdem Sie den Service-Client erstellt haben, können Sie dann die Voreinstellungs-Manager-Vorgänge aufrufen. Mit dem Service-Client können Sie Berechtigungen lesen und festlegen.
