---
title: Beheben von SSRF-Schwachstellen (Server-Side Request Forgery) für AEM Forms on JEE 6.5 LTS SP2
description: Schritte zur Behebung von Sicherheitslücken bei Server-seitigen Request Forgery (SSRF) in AEM Forms on JEE 6.5 LTS Service Pack 2-Bereitstellungen, die auf JBoss ausgeführt werden.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
exl-id: 7c4a9e12-3b8f-4d6a-9f1e-2a5c8d7e6b04
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 30%
---
# Beheben von SSRF-Schwachstellen (Server-Side Request Forgery) für AEM Forms on JEE 6.5 LTS SP2

## Kurzübersicht {#quick-reference}

| Auswirkungsgrad | Betroffene Versionen | Empfohlene Aktion |
| --- | --- | --- |
| Kritisch | AEM Forms on JEE 6.5 LTS Service Pack 2 (6.5 LTS SP2) | Installieren Sie den [Hotfix](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear) manuell |
| Nicht betroffen | AEM Forms on OSGi, Workbench, Cloud Service | Keine Aktion erforderlich. |

**Behobene Sicherheitslücken:**

* Server-seitige Request Forgery (SSRF) (CWE-918)

## Überblick {#overview}

### Betroffene Elemente {#whats-affected}

| Schwachstelle | Auswirkungen | Betroffene Komponenten |
| --- | --- | --- |
| Server-seitige Request Forgery (SSRF) (CWE-918) | Angreifer können den Server dazu bringen, unbeabsichtigte Anfragen an interne oder externe Ressourcen zu stellen | AEM Forms on JEE 6.5 LTS SP2 |

### Was nicht betroffen ist {#whats-not-affected}

* Experience Manager Forms Workbench (alle Versionen)
* Experience Manager Forms auf OSGi (alle Versionen)
* Experience Manager Forms as a Cloud Service

## Optionen zur Auflösung {#resolution-options}

### Bevor Sie beginnen {#before-you-start}

Bevor Sie Änderungen vornehmen, sichern Sie die EAR-Datei, die Sie ersetzen möchten:

* Suchen Sie `adobe-edcserver-jboss.ear` im Bereitstellungsverzeichnis:

  ```text
  [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
  ```

* Kopieren Sie die Datei an einen sicheren Sicherungsspeicherort außerhalb des Bereitstellungsverzeichnisses.
* Stellen Sie sicher, dass die Sicherung abgeschlossen ist und zugänglich ist, bevor Sie mit Aktualisierungen fortfahren.

Dank dieser Vorsichtsmaßnahme können Sie den Originalzustand wiederherstellen, falls während des Aktualisierungsprozesses Probleme auftreten.

### Manuelle Hotfix-Installation für AEM Forms on JEE 6.5 LTS SP2 (JBoss)

1. Laden Sie `adobe-edcserver-jboss.ear` vom [Adobe Software Distribution-](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear) herunter.

1. Suchen Sie `adobe-edcserver-jboss.ear` in Ihrem Bereitstellungsverzeichnis und ersetzen Sie sie durch die heruntergeladene Datei:

   ```text
   [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
   ```

1. Starten Sie den AEM Forms Configuration Manager, um die aktualisierte EAR-Datei erneut bereitzustellen und den Hotfix anzuwenden.

1. Starten Sie den Anwendungsserver neu, und bestätigen Sie die erfolgreiche Bereitstellung über die Serverprotokolle.

## Referenz {#references}

* [Best Practices für die Adobe Experience Manager Forms-Sicherheit](/help/forms/using/hardening-securing-aem-forms-environment.md)
