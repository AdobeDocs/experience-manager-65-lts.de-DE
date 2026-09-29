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
removedfrom6.5.2025: 'yes'
exl-id: bdd884c4-ae12-4827-8251-01033cbc0185
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
