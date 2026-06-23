---
title: Beheben von VULN-36128- und VULN-36120-Sicherheitslücken für AEM Forms on JEE 6.5 LTS SP2
description: Schritte zur Risikominderung für VULN-36128- und VULN-36120-Bereitstellungen in AEM Forms on JEE 6.5 LTS Service Pack 2, die auf JBoss ausgeführt werden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
solution: Experience Manager, Experience Manager Forms
feature: Security
role: Admin
exl-id: 7c4a9e12-3b8f-4d6a-9f1e-2a5c8d7e6b04
source-git-commit: 1b876f20cbc3a00a02a4449f0d353fb858695235
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 14%

---

# Beheben von VULN-36128- und VULN-36120-Sicherheitslücken für AEM Forms on JEE 6.5 LTS SP2

## Kurzübersicht {#quick-reference}

| Auswirkungsgrad | Betroffene Versionen | Empfohlene Aktion |
| --- | --- | --- |
| Kritisch | AEM Forms on JEE 6.5 LTS Service Pack 2 (6.5 LTS SP2) | Installieren Sie den [Hotfix](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear) manuell |
| Nicht betroffen | AEM Forms on OSGi, Workbench, Cloud Service | Keine Aktion erforderlich. |

**Behobene Sicherheitslücken:**

* **VULN-36128**: Schwachstelle bei der Ausführung von Remote-Code, durch die nicht autorisierte Angreifer beliebigen Code ausführen können.
* **VULN-36120**: Eine Schwachstelle bei der Validierung falscher Eingaben, die unbefugten Zugriff auf vertrauliche Informationen ermöglichen könnte.

## Schritte zur Risikominderung {#mitigation-steps}

### Bevor Sie beginnen {#before-you-start}

Bevor Sie Änderungen vornehmen, sichern Sie die EAR-Datei, die Sie ersetzen möchten:

* Suchen Sie `adobe-edcserver-jboss.ear` im Bereitstellungsverzeichnis:

  ```text
  [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
  ```

* Kopieren Sie die Datei an einen sicheren Sicherungsspeicherort außerhalb des Bereitstellungsverzeichnisses.
* Stellen Sie sicher, dass die Sicherung abgeschlossen ist und zugänglich ist, bevor Sie mit Aktualisierungen fortfahren.

Mit dieser Vorsichtsmaßnahme können Sie den Originalzustand wiederherstellen, wenn während des Aktualisierungsprozesses Probleme auftreten.

### Manuelle Hotfix-Installation für AEM Forms on JEE 6.5 LTS SP2 (JBoss) {#manual-hotfix-installation-aem-forms-jee-65-lts-sp2-jboss}

1. Laden Sie `adobe-edcserver-jboss.ear` vom [Adobe Software Distribution-](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear) herunter.

1. Suchen Sie `adobe-edcserver-jboss.ear` in Ihrem Bereitstellungsverzeichnis und ersetzen Sie sie durch die heruntergeladene Datei:

   ```text
   [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
   ```

1. Starten Sie den AEM Forms Configuration Manager, um die aktualisierte EAR-Datei erneut bereitzustellen und den Patch vollständig anzuwenden.

1. Starten Sie den Anwendungsserver neu, und bestätigen Sie die erfolgreiche Bereitstellung über die Serverprotokolle.

## Verweise {#references}

* [Best Practices für die Adobe Experience Manager Forms-Sicherheit](/help/forms/using/hardening-securing-aem-forms-environment.md)
