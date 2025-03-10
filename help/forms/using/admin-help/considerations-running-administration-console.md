---
title: Erwägungen beim Ausführen der Administrationskonsole
description: In diesem Dokument werden einige Erwägungen zum Ausführen der Administrationskonsole aufgeführt.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: bdd884c4-ae12-4827-8251-01033cbc0185
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 100%

---

# Erwägungen beim Ausführen der Administrationskonsole {#considerations-when-running-administrationconsole}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Folgendes sollte beim Ausführen der Administrationskonsole beachtet werden:

* Wenn Sie über die URL `https://[hostname]:'port'/adminui` auf die Administration-Console zugreifen, darf der angegebene Host-Name keine Unterstrichzeichen enthalten. Andernfalls funktionieren Links zu einigen Bereichen der Administrationskonsole eventuell nicht ordnungsgemäß.
* Wenn Sie eine Administrationskonsole in Windows Explorer unter einem japanischen Betriebssystem ausführen, können Sie auf folgende Probleme stoßen:

   * Beim Klicken auf einen Link werden Sie zur Anmeldeseite zurückgeleitet, nicht zum erwarteten Ziel des Links.
   * Beim Klicken auf einen Link wird ein Berechtigungsfehler angezeigt.

  Es wird empfohlen, die Administrationskonsole in einem anderen Browser auszuführen, z. B. Mozilla Firefox, um sicherzustellen, dass keine Links fehlerhaft sind.

* Verwenden Sie bei Suchvorgängen in der Administrationskonsole keine umgekehrten Schrägstriche (\).
