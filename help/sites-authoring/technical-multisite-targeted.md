---
title: Strukturierung von Multisite-Management für zielgerichtete Inhalte
description: Im Diagramm ist der Aufbau der Multisite-Unterstützung für zielgerichtete Inhalte dargestellt.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User,Admin,Architect,Developer
exl-id: 435fcee8-ddb4-4b3c-a55f-fca1b91b7d52
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 100%

---

# Strukturierung von Multisite-Management für zielgerichtete Inhalte{#how-multisite-management-for-targeted-content-is-structured}

Im folgenden Diagramm ist der Aufbau der Multisite-Unterstützung für Targeting-Inhalte dargestellt.

Gebiete werden unter **/content/campaigns/&lt;Marke>** eingeordnet und jede Marke verfügt standardmäßig über ein automatisch erstelltes Hauptgebiet. In jedem Gebiet ist ein eigener Satz Aktivitäten, Erlebnisse und Angebote enthalten.

![chlimage_1-268](assets/chlimage_1-268.png)

Seiten oder Sites können Gebieten zugeordnet werden, sodass sich Targeting-Inhalte nachschlagen lassen. Sollte kein Gebiet konfiguriert sein, bezieht sich AEM für diese Marke auf das primäre Gebiet.

Im folgenden Diagramm finden Sie ein Beispiel dafür, wie die Logik im Falle der drei Sites Site1, Site2 und Site3 funktioniert.

![chlimage_1-269](assets/chlimage_1-269.png)

* site1 schlägt myarea1 für brand1 und otherarea2 für brand2 basierend auf der Bereichszuordnung nach.
* Site2 bezieht sich für Marke1 auf MeinGebiet1 und für Marke2 auf das primäre Gebiet, da nur für Marke1 Gebiete zugewiesen wurden.
* Site3 bezieht sich für Marke1 und für Marke2 auf das primäre Gebiet, weil für diese Site keine Gebietszuordnung vorgenommen wurde.
