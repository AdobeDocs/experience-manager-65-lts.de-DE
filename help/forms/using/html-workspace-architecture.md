---
title: Architektur von AEM Forms Workspace
description: Grundlegende Informationen und Überblick über die Architektur von LiveCycle AEM Forms Workspace.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: User, Developer
exl-id: d317274f-2c9a-4809-b43e-2efebc8fcb3f
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 100%

---

# Architektur von AEM Forms Workspace {#aem-forms-workspace-architecture}

AEM Forms Workspace ist eine Web-Anwendung, die auf CRX™ gehostet wird. Wenn Workspace in einem Browser geöffnet wird, wird auf eine CRX-Ressource zugegriffen und die Anwendung als HTML-Seite im Browser gerendert. 

Die Anwendung greift auf den AEM-Formular-Server an den REST-Endpunkten zu, um folgende Aktionen auszuführen:

* Abrufen von Benutzeraufgaben sowie Verarbeiten von Startpunkten, Verlauf und Benutzerinformationen
* Ausführen von Aktionen für Aufgaben
* Abfrage von Aufgaben in der Datenbank
* Aktualisieren von Benutzereinstellungen und mehr

Der AEM-Formular-Server greift auf die AEM Forms-Datenbank über JDBC zu. Die Datenbank erfasst Aufgaben, Prozesse und deren Instanzen, Benutzende und zugehörige Informationen.

AEM Forms Workspace ist aus modularen JavaScript™-Komponenten aufgebaut, die in anderen Web-Anwendungen individuell angepasst und wiederverwendet werden können. Die Komponenten basieren auf Backbone, einer JavaScript-Bibliothek, die eine Struktur für Web-Anwendungen zur Verfügung stellt. Einen ausführlichen Artikel, der die Interaktion von Komponenten mit Backbone beschreibt, finden Sie [hier](/help/forms/using/backbone-interaction.md). Die Organisation der Komponenten in der CRX-Ordnerstruktur wird in [diesem](/help/forms/using/folder-structure.md) Artikel behandelt.

Pakete, die für AEM Forms Workspace bereitgestellt werden:

* `adobe-lc-workspace-pkg-<version>.zip`: Dies ist ein CRX-Paket, das heißt, es kann mithilfe des Package Manager in CRX bereitgestellt werden.
* `adobe-lc-workspace-<version>-src.zip`: Dies ist ein Archiv, das den vollständigen Code von AEM Forms Workspace und Skripte enthält, um die Bereitstellungspakete (Lieferpaket, Debugging-Paket und Entwicklungspaket) zu erstellen.
