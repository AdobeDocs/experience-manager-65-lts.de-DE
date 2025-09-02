---
title: Upgrade auf Adobe Experience Manager 6.5
description: Erfahren Sie mehr über die Grundlagen des Upgrades einer älteren Adobe Experience Manager (AEM)-Installation auf AEM 6.5.
contentOwner: sarchiz
topic-tags: upgrading
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: ebc34847-dc3d-41ed-b0d6-f004c3debcd9
source-git-commit: e9fc4a6294588b527a3b19d64101c81f0eb7bf55
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 28%

---

# Aktualisieren auf Adobe Experience Manager (AEM) 6.5 LTS {#upgrading-to-aem}

>[!NOTE]
>Das Upgrade auf AEM 6.5 LTS ist für alle unterstützten 6.5 Service Packs verfügbar.

>[!NOTE]
>
>Aus technischer Sicht ist der Upgrade-Prozess von AEM 6.5 LTS auf AEM 6.5 LTS Service Packs ein nahtloses [In-Place-Upgrade](/help/sites-deploying/in-place-upgrade.md). Dieser Prozess erfordert im Allgemeinen keine Code-Änderungen von Kunden, es sei denn, dies ist in den Versionshinweisen ausdrücklich angegeben.

Dieser Abschnitt behandelt das Upgrade einer AEM-Installation auf AEM 6.5 LTS:

<!-- Alexandru: drafting for now 

* [Planning Your Upgrade](/help/sites-deploying/upgrade-planning.md)
* [Assessing the Upgrade Complexity with Pattern Detector](/help/sites-deploying/pattern-detector.md)
* [Backward Compatibility in AEM 6.5](/help/sites-deploying/backward-compatibility.md)
  This was drafted before: * [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

<!--
* [Upgrade Procedure](/help/sites-deploying/upgrade-procedure.md)
* [Upgrading Code and Customizations](/help/sites-deploying/upgrading-code-and-customizations.md)
* [Pre-Upgrade Maintenance Tasks](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [Performing an In-Place Upgrade](/help/sites-deploying/in-place-upgrade.md)
* [Post Upgrade Checks and Troubleshooting](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [Sustainable Upgrades](/help/sites-deploying/sustainable-upgrades.md)
* [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md)

-->

Für ein einfacheres Verständnis der in diesen Verfahren verwendeten AEM-Instanzen werden die folgenden Begriffe in diesen Artikeln verwendet:

* Die Instanz *Quelle* ist die AEM-Instanz, von der Sie aktualisieren.
* Die Instanz *Ziel* ist diejenige, auf die Sie aktualisieren.

## Was hat sich geändert? {#what-has-changed}

### Updates {#updates}

Foundation Layer unterstützt jetzt Java 17 und Java 21 mit den neuesten Open-Source-Bundles von Apache Sling, Felix und Jackrabbit Oak. Darüber hinaus wurde die Paketerstellung des AEM 6.5 LTS uber-jar geändert. Darüber hinaus wurden einige ältere Funktionen aus AEM 6.5 LTS entfernt. Weitere Informationen finden Sie unter [Versionshinweise](/help/release-notes/release-notes.md#whats-new-what-s-new) und [Liste der nach dem Upgrade deinstallierten veralteten Bundles](/help/sites-deploying/obsolete-bundles.md)

AEM 6.5 LTS legt großen Wert auf die Abwärtskompatibilität der Funktionen und verfügt über ein Analyzer-Tool. Unter [Bewertung der Komplexität des Upgrades mit dem AEM Analyzer](/help/sites-deploying/aem-analyzer.md) finden Sie eine Bewertung der Komplexität zu Beginn [Planung des Upgrades](/help/sites-deploying/upgrade-planning.md).
