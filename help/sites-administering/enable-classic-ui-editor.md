---
title: Bearbeiter
description: Erfahren Sie, wie Sie zum klassischen Benutzerflächen-Editor zurückkehren.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 100%

---


# Bearbeiter{#editor}

Standardmäßig ist die Möglichkeit deaktiviert, vom Editor aus zur klassischen Benutzeroberfläche zu wechseln.

Um die Option **In klassischer Benutzeroberfläche öffnen** im Menü **Seiteninformationen** erneut zu aktivieren, gehen Sie wie folgt vor.

1. Suchen Sie mithilfe von CRXDE Lite den folgenden Knoten:

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   Beispiel

   ` [https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui)`

1. Erstellen Sie eine Überlagerung mit der Option **Überlagerungsknoten**. Beispiel:

   * **Pfad**: `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **Pfad für Überlagerung**: `/apps/`
   * **Knotentypen abgleichen**: aktiv (aktivieren Sie das Kontrollkästchen)

1. Fügen Sie die folgende Multiwert-Texteigenschaft zum überlagerten Knoten hinzu:

   `sling:hideProperties = ["granite:hidden"]`

1. Die Option **In klassischer Benutzeroberfläche öffnen** steht nun wieder beim Bearbeiten von Seiten im Menü **Seiteninformationen** zur Verfügung.

   ![Option „In klassischer Benutzeroberfläche öffnen“ über die Seiteninformationen öffnen](assets/syui-03-2019-02-27-15-19-48.png)
