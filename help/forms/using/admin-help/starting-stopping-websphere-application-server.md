---
title: Starten und Anhalten des WebSphere-Anwendungs-Servers
description: Bei mehreren Verfahren müssen Sie die WebSphere-Instanz stoppen oder starten, für die Sie AEM Forms-Produkte bereitstellen möchten. In diesem Dokument wird beschrieben, wie Sie WebSphere Application Server starten und stoppen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 20cd6efb-edcf-4c87-b0f5-bdec5a0f6280
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 100%

---

# Starten und Anhalten des WebSphere-Anwendungs-Servers {#starting-and-stopping-websphere-application-server}

Bei mehreren Verfahren müssen Sie die WebSphere-Instanz stoppen oder starten, für die Sie AEM Forms-Produkte bereitstellen möchten. Wenn Sie nicht sicher sind, ob der Anwendungs-Server gestartet wurde, können Sie zunächst den WebSphere Application Server-Status anzeigen.

## Anzeigen des WebSphere Application Server-Status {#view-the-status-of-websphere-application-server}

1. Wechseln Sie ausgehend von einer Eingabeaufforderung in das Verzeichnis `[appserver root]/bin`.
1. Geben Sie den folgenden Befehl ein. Ersetzen Sie dabei *Servername* durch den Namen Ihres WebSphere Application Servers:

   * (Windows) `serverStatus.bat`*server_name*
   * (Linux, UNIX) ./ `serverStatus.sh`*server_name*

## WebSphere Application Server starten {#start-websphere-application-server}

1. Wechseln Sie ausgehend von einer Eingabeaufforderung in das Verzeichnis `[appserver root]/bin`.
1. Geben Sie den folgenden Befehl ein. Ersetzen Sie dabei *Servername* durch den Namen Ihres WebSphere Application Servers:

   * (Windows) `startServer.bat`*server_name*
   * (Linux, UNIX) ./ `startServer.sh`*server_name*

## WebSphere Application Server stoppen {#stop-websphere-application-server}

1. Wechseln Sie ausgehend von einer Eingabeaufforderung in das Verzeichnis `[appserver root]/bin`.
1. Geben Sie den folgenden Befehl ein. Ersetzen Sie dabei *Servername* durch den Namen Ihres WebSphere Application Servers:

   * (Windows) `stopServer.bat`*server_name*
   * (Linux, UNIX) ./ `stopServer.sh`*server_name*
