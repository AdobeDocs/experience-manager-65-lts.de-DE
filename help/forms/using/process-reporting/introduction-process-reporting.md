---
title: Einführung in das Prozess-Reporting
description: Einführung und Schlüsselfunktionen von Process Reporting mit AEM Forms auf JEE
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 755df7e2-3603-4c0d-ad07-ec6f27de8c64
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 96%

---

# Einführung in das Prozess-Reporting{#introduction-to-process-reporting}

![process-reporting](assets/process-reporting.png)

Process Reporting ist ein Browser-basiertes Tool, mit dem Sie Berichte zu AEM Forms-Prozessen und -Aufgaben erstellen und anzeigen können.

Das Prozess-Reporting bietet eine Reihe vordefinierter Berichte, mit denen Sie Informationen zu langlebigen Prozessen, Prozessdauer und Workflow-Volumen filtern und anzeigen können.

Darüber hinaus bietet Process Reporting eine Oberfläche zum Ausführen von Ad-hoc-Abfragen und zum Integrieren benutzerdefinierter Berichtsansichten in die Process Reporting-Benutzeroberfläche.

Eine Liste der unterstützten Browser finden Sie unter [Von AEM Forms unterstützte Plattformen](/help/sites-deploying/technical-requirements.md)

Process Reporting basiert auf Modulen, die:

* Prozessdaten aus der AEM Forms-Datenbank lesen
* Prozessdaten in einem eingebetteten Process Reporting-Repository veröffentlichen
* Eine browserbasierte Benutzeroberfläche zum Anzeigen von Berichten bieten

## Schlüsselfunktionen {#key-capabilities}

### Always-on-Reporting {#always-on-reporting}

![site-management](assets/site-management.png)

Zeigen Sie die Liste der Prozesse mit langer Laufzeit an, erstellen Sie Diagramme zur Prozessdauer und führen Sie benutzerdefinierte Abfragen mithilfe von Filtern aus.

Process Reporting bietet außerdem die Möglichkeit, die Berichts- und Abfragedaten im CSV-Format zu exportieren.

### Ad-hoc-Berichte {#adhoc-reports}

![print-&amp;-colour](assets/print-&-colour.png)

Verwenden Sie Filter, um eine bestimmte Ansicht Ihrer Daten zu erhalten.

Sie können Prozesse oder Aufgaben nach ID, Dauer, Start- und Enddatum, Prozessinitiator usw. durchsuchen.

Sie können mehrere Filter kombinieren, um bestimmte Berichte zu erstellen.

Anschließend können Sie die Berichtsfilter speichern, um sie zu einem späteren Zeitpunkt auszuführen.

### Prozess-/Aufgabenverlauf {#process-task-history}

![file-management](assets/file-management.png)

AEM Forms-Server führen zahlreiche Prozesse parallel aus. Diese Prozesse gehen immer wieder von einem Zustand in einen anderen über. Durch die regelmäßige Veröffentlichung von Forms-Daten in das Process Reporting-Repository werden die Übergangsinformationen zu den in AEM Forms ausgeführten Prozessen in Process Reporting beibehalten.

### Zugriffssteuerung {#access-control-br}

![untitled](assets/untitled.png)

Process Reporting bietet berechtigungsbasierten Zugriff auf die Benutzeroberfläche.

Dies bedeutet, dass nur Benutzer mit Berichterstellungsberechtigungen Zugriff auf die Process Reporting-Benutzeroberfläche haben.
