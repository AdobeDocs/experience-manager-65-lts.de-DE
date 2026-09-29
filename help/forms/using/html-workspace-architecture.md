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
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 97aafc4b-2598-52d6-9012-295a95969e38
    internal-label: HTML5 Forms
  - id: 59f95943-e802-56ac-990d-21ab923984c1
    internal-label: Mobile Forms
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
source-wordcount: '225'
ht-degree: 53%
---
# AEM Forms Workspace-Architektur {#aem-forms-workspace-architecture}

AEM Forms Workspace ist eine Web-Anwendung, die auf CRX™ gehostet wird. Wenn ein Arbeitsbereich in einem Browser geöffnet wird, wird auf eine CRX-Ressource zugegriffen und die Anwendung wird als HTML-Seite im Browser gerendert.

Die Anwendung greift auf den AEM Forms-Server über REST-Endpunkte zu, um folgende Aktionen durchzuführen:

* Abrufen von Benutzeraufgaben sowie Verarbeiten von Startpunkten, Verlauf und Benutzerinformationen
* Ausführen von Aktionen für Aufgaben
* Abfrage von Aufgaben in der Datenbank
* Aktualisieren von Benutzereinstellungen und mehr

Der AEM Forms-Server greift über JDBC auf die AEM Forms-Datenbank zu. Die Datenbank erfasst Aufgaben, Prozesse und deren Instanzen, Benutzende und zugehörige Informationen.

Der AEM Forms-Arbeitsbereich ist in modulare JavaScript-Komponenten unterteilt, die in anderen Web-Anwendungen individuell angepasst und wiederverwendet werden können. Die Komponenten basieren auf BackBone, einer JavaScript-Bibliothek, die Web-Anwendungen Struktur verleiht. Ein ausführlicher Artikel, der die Interaktion von Komponenten mit BackBone beschreibt, ist [hier](/help/forms/using/backbone-interaction.md). Die Organisation der Komponenten in der CRX-Ordnerstruktur wird in [diesem](/help/forms/using/folder-structure.md) Artikel behandelt.

Pakete, die für AEM Forms Workspace bereitgestellt werden:

* `adobe-lc-workspace-pkg-<version>.zip`: Dies ist ein CRX-Paket, das heißt, es kann mithilfe des Paket-Managers in CRX bereitgestellt werden.
* `adobe-lc-workspace-<version>-src.zip`: Dies ist ein Archiv, das den vollständigen Code von AEM Forms Workspace und Skripte enthält, um die Bereitstellungspakete (Lieferpaket, Debugging-Paket und Entwicklungspaket) zu erstellen.
