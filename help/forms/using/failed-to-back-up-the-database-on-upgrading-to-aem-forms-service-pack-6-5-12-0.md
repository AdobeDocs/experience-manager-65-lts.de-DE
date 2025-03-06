---
title: Fehler beim Sichern der Datenbank beim Upgrade auf 6.5.12.0 für MySQL.
description: Wenn ein Benutzer ein Upgrade auf Experience Manager 6.5.12.0 vornimmt und auf „MySQL aktualisieren“ klickt, kann der Konfigurations-Manager die vorherige Experience Manager Forms-Datenbank nicht sichern.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms on JEE
role: User, Developer
exl-id: afc09a9f-58ef-4292-a2f2-b62d3246c006
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 39%

---

# Fehlschlagen des Datenbank-Backups beim Upgrade auf 6.5.12.0 für MySQL {#issue}

Wenn ein Benutzer auf Experience Manager 6.5.12.0 aktualisiert und auf „MySQL aktualisieren“ klickt, kann der Konfigurations-Manager die vorherige Experience Manager Forms-Datenbank nicht sichern. Es wird der Fehler angezeigt:

`Failed to backup the previous Adobe Experience Manager Forms Database`


## Gilt für {#applies-to}

* Experience Manager 6.5 Forms

## Lösung {#solution}

Um das Problem zu beheben, erhöhen Sie den max_packet_size-Wert der Datenbank auf 100 MB oder wie in der Datei „my.ini“ unter {AEM_HOME}/mysql erforderlich.
