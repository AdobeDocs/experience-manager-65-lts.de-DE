---
title: Installations- und Upgrade-Workflow für AEM Forms on JEE
description: Installations- und Upgrade-Workflow für AEM Forms 6.5 LTS on JEE (JBoss) mit einer konsolidierten Liste der relevanten PDFs und deren Zweck.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: AEM Forms on JEE,AEM Forms Upgrade
exl-id: 6d8c0e24-7f08-4e66-bb12-2cf1cfe1d5d3
source-git-commit: fb9f6ef794da7f3b242e9e81a6c2505692c16cd8
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 3%

---


# Installations- und Upgrade-Workflow für AEM Forms on JEE {#aem-forms-jee-installation-upgrade-documentation}

## Gilt für {#applies-to}

Diese Dokumentation gilt für **AEM 6.5 LTS Forms**.

Verwenden Sie den folgenden Workflow und die folgenden Tabellen, um die richtigen Anleitungen für Ihr Szenario auszuwählen. Einige Dokumente werden als PDF-Dateien veröffentlicht. Weitere Dokumente können im Laufe der Zeit hinzugefügt werden, sobald sie verfügbar werden.

## Installations- und Upgrade-Workflow {#installation-upgrade-workflow}

1. Überprüfen Sie [Unterstützte Plattformen für AEM Forms on JEE](/help/forms/using/aem-forms-jee-supported-platforms.md) und stellen Sie sicher, dass Ihr System die erforderlichen Software-/Hardwarekombinationen erfüllt.
2. Entscheiden Sie, ob Sie eine **Neuinstallation** oder ein **Upgrade** durchführen.
3. Folgen Sie für den ausgewählten Pfad der unten beschriebenen Reihenfolge (für einige Szenarien ist mehr als ein Handbuch erforderlich).

## Schritte vor der Installation und vor dem Upgrade {#start-here}

| -Anleitung | Beschreibung |
| --- | --- |
| [Unterstützte Plattformen für AEM Forms on JEE](/help/forms/using/aem-forms-jee-supported-platforms.md) | Listet die unterstützten Software- und Hardwarekombinationen für AEM Forms on JEE auf. Validieren Sie auf diese Weise die Voraussetzungen, bevor Sie mit der Installation oder dem Upgrade beginnen. |
| [Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md) | Erläutert empfohlene Architekturen und Bereitstellungstopologien, damit Sie einen Ansatz wählen können, der Ihrer Umgebung entspricht (z. B. Einzelserver vs. Cluster). |
| [Auswählen eines Persistenztyps für eine AEM Forms-Installation](/help/forms/using/choosing-persistence-type-for-aem-forms.md) | Hilft Ihnen bei der Auswahl eines geeigneten Persistenztyps für Ihre Installationstopologie, bevor Sie beginnen. |

## Wie installiere ich Adobe Experience Manager Forms (AEM Forms) on JEE auf JBoss? {#installing-aem-forms-jee-jboss}

### schlüsselfertig {#install-jee-jboss-turnkey}

| -Anleitung | Beschreibung |
| --- | --- |
| [Installieren und Bereitstellen von AEM Forms 6.5 LTS on JEE mithilfe von JBoss Turnkey (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/install-turnkey.pdf) | Verwenden Sie für eine **neue Turnkey-Installation** auf JBoss. Dieses Dokument enthält Anweisungen zur Installation und Bereitstellung von AEM Forms on JEE mithilfe der Turnkey-Verteilung von JBoss. |

### Einzel-Server (nicht schlüsselfertig) {#install-jee-jboss-single-server}

| -Anleitung | Beschreibung |
| --- | --- |
| [Vorbereiten der Installation von AEM Forms (Einzel-Server) (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/prepare-install-single-server.pdf) | Verwenden Sie **vor** eine **neue Einzel-Server-Installation (keine Turnkey-Installation**. In diesem Dokument werden die Voraussetzungen und Umgebungsvorbereitungsschritte für die Installation von AEM Forms on JEE in einer Einzelserver-Topologie aufgeführt. |
| [Installieren und Bereitstellen von AEM Forms on JEE für JBoss (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/install-jboss.pdf) | Verwenden Sie für die **schrittweise Installation und Bereitstellung** von AEM Forms on JEE auf JBoss (**Nicht-Turnkey**). Folgen Sie bei Einzelserverinstallationen diesem Handbuch (**) nach Abschluss von** Vorbereiten *Installation von AEM Forms (Einzelserver)*. |

<!--
| Preparing to Install AEM Forms (Server Cluster) (PDF) (**TBD**) | Use **before** a **fresh cluster installation**. Describes prerequisites and environment preparation steps for installing AEM Forms on JEE in a server cluster topology. *(Link will be added once the PDF is available.)* |
| [Configuring AEM Forms on JEE on JBoss Cluster (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/cluster-jboss.pdf) | Use when setting up and configuring a **JBoss cluster topology** for AEM Forms on JEE. |
-->

## Wie aktualisiere ich Adobe Experience Manager Forms (AEM Forms) on JEE auf JBoss? {#upgrading-aem-forms-jee-jboss}

### schlüsselfertig {#upgrade-jee-jboss-turnkey}

| -Anleitung | Beschreibung |
| --- | --- |
| [Aktualisieren auf AEM Forms 6.5 LTS on JEE für JBoss Turnkey (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/upgrade-turnkey.pdf) | Verwenden Sie für ein **-Upgrade**. Dieses Dokument enthält Anweisungen zum Aktualisieren einer bestehenden Turnkey-Installation von AEM Forms on JEE JBoss. |

### Einzelserver {#upgrade-jee-jboss-single-server}

| -Anleitung | Beschreibung |
| --- | --- |
| [Vorbereiten der Aktualisierung von AEM Forms (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/prepare-upgrade.pdf) | Verwenden Sie **vor** ein **Einzel-Server-Upgrade**. Beschreibt, wie die Umgebung vor dem Upgrade auf AEM 6.5 LTS Forms vorbereitet wird. Dies gilt für Umgebungen, in denen AEM Forms on JEE in einem Einzelserver-Installationsmodus ausgeführt wird. |
| [Aktualisieren auf AEM Forms on JEE für JBoss (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/upgrade-jboss.pdf) | Verwenden Sie für das **-für-Schritt-Upgrade** auf JBoss in einem **Einzel-Server** Installationsmodus. Folgen Sie dieser Anleitung **nach** Abschluss von *Vorbereiten der Aktualisierung von AEM Forms*. |

<!--
| Preparing to Install AEM Forms (Server Cluster) (PDF) (**TBD**) | Use **before** a **cluster upgrade**. Describes how to prepare the environment for a server cluster before upgrading to AEM 6.5 LTS Forms. It applies to environments running AEM Forms on JEE in a server cluster installation mode. *(Link will be added once the PDF is available.)* |
| Upgrading to AEM Forms on JEE for JBoss (Cluster) (PDF) (**TBD**) | Use for the **step-by-step upgrade procedure** on JBoss in a **clustered** installation mode. Follow this guide **after** completing *Preparing to Install AEM Forms (Server Cluster)*. *(Link will be added once the PDF is available.)* | -->

