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
source-git-commit: f66bb283e5c2a746821839269e112be8c2714ba7
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 29%

---

# Aktualisieren auf Adobe Experience Manager (AEM) 6.5 LTS {#upgrading-to-aem}

>[!NOTE]
>Das Upgrade auf AEM 6.5 LTS wird von den letzten 6 Service Packs unterstützt.

Dieser Abschnitt behandelt das Upgrade einer AEM-Installation auf AEM 6.5:

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

Im Folgenden werden die wichtigsten Änderungen der letzten Versionen von AEM beschrieben:

1. Die Foundation-Ebene wurde aktualisiert, um Java 17 zu unterstützen (das Open-Source-Ebenen von Bundles von Apache Sling, Apache Felix und Apache Jackrabbit Oak umfasst)

1. Das AEM 6.5 LTS-JAR-Packaging unterstützt jetzt die Jarkarta Servlet-APIs-Spezifikationen 5. WAR-Packaging kann in Servlet-Containern bereitgestellt werden, die die Jakarta Servlet-API-Spezifikationen 5/6 implementieren

1. Das Verpacken von AEM 6.5 LTS uber-jar hat sich geändert. Weitere Informationen finden [ unter „Aktualisieren von Code ](/help/sites-deploying/upgrading-code-and-customizations.md) Anpassungen“.

### Entfernte alte Funktionen/Artefakte {#removed-legacy-features-artifacts}

Die folgenden Legacy-Lösungen wurden aus AEM 6.5 LTS entfernt. Weitere Informationen finden Sie unter TBD: link to release notes and [list of obsolete Bundles uninstalled after the upgrade](/help/sites-deploying/obsolete-bundles.md)

1. Social
1. Commerce 
1. Screens
1. We-retail
1. Integration von Suche und Promotion

**Entfernte Artefakte**

1. CRX-Explorer
1. crx2oak
1. Google Guava (aufgrund von Sicherheitslücken entfernt)
1. Abdera-parser (wegen Sicherheitslücken entfernt)
1. JDOM (`org.apache.servicemix.bundles.jdom`) (aufgrund von Sicherheitslücken entfernt)
1. `com.github.jknack.handlebars` (aufgrund von Sicherheitslücken entfernt)

AEM 6.5 LTS legt großen Wert auf die Abwärtskompatibilität der Funktionen und verfügt über ein Analyzer-Tool. Unter [Bewertung der Komplexität des Upgrades mit dem AEM Analyzer](/help/sites-deploying/pattern-detector.md) finden Sie eine Bewertung der Komplexität, wenn Sie mit der Planung des Upgrades beginnen. Weitere Informationen zu den weiteren Änderungen finden Sie in den vollständigen Versionshinweisen hier. TBD: Link zu den Versionshinweisen von AEM 6.5 LTS