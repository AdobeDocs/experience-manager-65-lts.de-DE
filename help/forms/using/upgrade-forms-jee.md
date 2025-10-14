---
title: Aktualisierung auf AEM 6.5 Forms on JEE
description: Sie können direkt von AEM 6.1 Forms, AEM 6.2 Forms und LiveCycle ES4 SP1 auf AEM 6.3 Forms aktualisieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms Upgrade,AEM Forms on JEE
hide: true
hidefromtoc: true
exl-id: 643bc966-b2d8-4626-8c25-b63c8909287e
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 75%

---

# Aktualisierung auf AEM 6.5 Forms auf JEE {#upgrade-to-aem-forms-jee}

AEM 6.5.18.0 Forms on JEE bietet zwei Arten von Installationsprogrammen: ein Vollinstallationsprogramm und ein Patch-Installationsprogramm.

**Vollinstallationsprogramm**: Sie können das Vollinstallationsprogramm für [AEM 6.5.18.0 on JEE](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) verwenden, um neue AEM Forms-Instanzen einzurichten oder Aktualisierungen von AEM 6.5.x.x Forms on JEE auf AEM 6.5.18.0 Forms on JEE durchzuführen.

**Patch-Installationsprogramm**: Das [Patch-Installationsprogramm für AEM 6.5.18.0 on JEE](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) ist für Kundinnen und Kunden bestimmt, die bereits AEM 6.5.x.x verwenden. Mit dem Patch-Installationsprogramm können Sie eine Aktualisierung auf die neueste Version von AEM Forms durchführen.

Die folgende Tabelle zeigt Szenarien für die Verwendung des Installationsprogramms für vollständige Installationen und Patches.

![Szenario für das Vollinstallations- und Patch-Installationsprogramm](assets/full-and-patch-installer.png)

Gehen Sie wie folgt vor, um mit dem vollständigen Installationsprogramm ein Upgrade von AEM Forms 6.5.x.x auf JEE auf AEM 6.5.18.0 Forms auf JEE durchzuführen:

1. Laden Sie das Installationsprogramm für AEM 6.5 Forms on JEE von der [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) herunter. Sie benötigen einen gültigen Wartungs- und Supportvertrag, um das Installationsprogramm zu verwenden.
1. Lesen Sie das Dokument [Checkliste für die Aktualisierung und Planung](https://www.adobe.com/go/learn_aemforms_upgrade_checklist_65_de), um sich über die Überprüfungen zu informieren, die für eine erfolgreiche Aktualisierung ausgeführt werden müssen.
1. Lesen Sie das Dokument [Vorbereiten auf die Aktualisierung auf AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_65_de), um zu erfahren, wie Sie die Aufgaben durchführen, die sicherstellen, dass die Aktualisierung richtig und nur mit minimalem Serverausfall verläuft.
1. Wählen Sie je nach vorhandener Umgebung und Anwendungsserver eines der folgenden Dokumente und befolgen Sie die Anweisungen.

   * [Upgrade von AEM 6.3 oder AEM 6.4 Forms auf AEM 6.5 Forms for JBoss &#x200B;](https://www.adobe.com/go/learn_aemforms_upgradeJBoss_65_de)
   * [Upgrade von AEM 6.3 oder AEM 6.4 Forms auf AEM 6.5 Forms for WebSphere](https://www.adobe.com/go/learn_aemforms_upgradeWebSphere_65_de)
   * [Upgrade von AEM 6.3 oder AEM 6.4 Forms auf AEM 6.5 Forms for JBoss Turnkey](https://www.adobe.com/go/learn_aemforms_upgradeTurnkey_65_de)

Die direkte Aktualisierung von LiveCycle ES2, Live Cycle ES3, AEM 6.0 Forms, AEM 6.1 Forms oder AEM 6.2 Forms auf AEM 6.5 Forms ist nicht verfügbar. Sie können eine Zwischenaktualisierung auf eine oder mehrere Versionen von LiveCycle oder AEM Forms durchführen und dann auf AEM 6.5 Forms aktualisieren. Eine Liste der Zwischenversionen und entsprechenden Aktualisierungsanweisungen finden Sie unter [Auswählen eines Aktualisierungspfads](upgrade.md).
