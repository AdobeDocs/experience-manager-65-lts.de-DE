---
title: Grundlagen der Ordnerstruktur
description: Grundlegendes zur Ordnerstruktur des Quell-Codes von AEM Forms Workspace zur Anpassung.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
exl-id: 08e6b25c-eef5-4f29-99fa-524f563e7f25
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 100%

---

# Grundlagen der Ordnerstruktur {#understanding-the-folder-structure}

AEM Forms Workspace-Komponenten basieren auf der MVC-Architektur mit Backbone. Jede Komponente verfügt über eine Datei für:

* ein Modell, das die Business-Logik enthält.
* eine Vorlage, hier eine HTML-Datei, die Steuerelemente für die Benutzeroberfläche enthält.
* eine Ansicht, die als Controller-Klasse für die Vorlage fungiert.

Die Assets für alle Komponenten werden in der unten beschriebenen Ordnerstruktur platziert. Um auf die Elemente zuzugreifen, melden Sie sich bei CRXDE Lite an und navigieren Sie zu `/libs/ws/js/runtime/`.

**models** Enthält Backbone-Modelle.

**views** Enthält Backbone-Ansichten.

**templates** Enthält nur die HTML-Vorlagen für die Komponenten.

**routes** Enthält universelle Routen. Der Ordner „templates“ unter „routes“ enthält den HTML-Code und die Verweise auf die Komponenten.

**services** Enthält die Serviceschnittstelle zum Aufrufen von Adobe Experience Manager-Server-APIs am REST-Endpunkt.

**util** Enthält generische Serviceprogramme, die von mehreren Komponenten verwendet werden können.
