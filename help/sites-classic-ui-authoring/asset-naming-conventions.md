---
title: Benennungskonventionen für das Testen von Assets
description: Knoten im Repository unterliegen den Benennungskonventionen des Java Content Repository. Adobe Experience Manager schreibt jedoch weitere Konventionen für den Namen von Asset-Knoten vor.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
exl-id: 37de1a8b-b7db-469e-98a7-20ddb6218510
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 100%

---

# Benennungskonventionen für das Testen von Assets{#naming-conventions-for-assets-testing}

Knoten im Repository unterliegen den Benennungskonventionen des [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). Adobe Experience Manager schreibt aber weitere Konventionen für den Namen von Asset-Knoten vor.

## Klassische Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche weist stärkere Einschränkungen auf:

* Prüft den Asset-Namen bei expliziten Knotennamen, wenn:

   * ein Asset-Titel für die Konvertierung in den Knotennamen bereitgestellt wird
   * ein expliziter Knotenname angegeben ist

* Gültige Zeichen (nur diese Zeichen sind tatsächlich gültig, wenn ein Asset in der klassischen Benutzeroberfläche erstellt wird):

   * „a“ bis „z“
   * „A“ bis „Z“
   * „0“ bis „9“
   * _ (Unterstrich)
   * `-` (Strich/Minus)
