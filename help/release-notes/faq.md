---
title: Häufig gestellte Fragen (FAQ)
description: Häufig gestellte Fragen zu AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: d18c9dc3-fdcc-4558-b9b6-ecf1ce61048a
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 91%
---
# Häufig gestellte Fragen (FAQ) zu AEM 6.5 LTS {#faq}

Auf dieser Seite finden Sie Antworten auf häufig gestellte Fragen zu AEM 6.5 LTS.

## Warum hat Adobe 6.5 LTS für AEM veröffentlicht?

Adobe setzt sich weiterhin für die Sicherheit und Stabilität der bereitgestellten Anwendungen ein. Die langfristige Unterstützung für AEM 6.5 bildet die Grundlage für zukünftige Aktualisierungen für AEM 6.5. Insbesondere bietet AEM 6.5 LTS Unterstützung für Oracle Java 17 und Java 21 und ist die AEM-Verzweigung, die neue AEM-Funktionen und -Innovationen erhält.

## Ich gehöre zur On-Premise-Kundschaft. Was passiert, wenn ich nicht auf AEM 6.5 LTS aktualisiere?

AEM 6.5 LTS enthält wichtige Sicherheits- und Stabilitätsaktualisierungen, einschließlich Unterstützung für Oracle Java 17 und Java 21. Es wird empfohlen, dass Unternehmen ein Upgrade auf 6.5 LTS planen. Adobe unterstützt AEM 6.5 noch bis zum 28. Februar 2027. Weitere Einzelheiten finden Sie [ &quot;](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap#aem65)&quot;.

## Hat es Auswirkungen auf meine vorhandenen Anpassungen und Integrationen, wenn ich auf AEM 6.5 LTS aktualisiere?

AEM 6.5 LTS ist zwar auf Abwärtskompatibilität ausgerichtet, einige ältere Funktionen und Artefakte wurden jedoch entfernt.
Sie müssen unbedingt die [Versionshinweise](/help/release-notes/release-notes.md#deprecated-and-removed-features) lesen und das [AEM Analyzer-Tool](/help/sites-deploying/aem-analyzer.md) verwenden, um die Auswirkungen auf Ihre Anpassungen und Integrationen zu bewerten.

## Wie kann ich einen reibungslosen Übergang zu AEM 6.5 LTS sicherstellen?

Um einen reibungslosen Übergang sicherzustellen, wird Folgendes empfohlen:

* Lesen Sie die [Versionshinweise](/help/release-notes/release-notes.md) und die Dokumentation sorgfältig durch.
* Verwenden Sie das [AEM Analyzer-Tooö](/help/sites-deploying/aem-analyzer.md), um die Komplexität des Upgrades zu bewerten.
* Planen Sie den Upgrade-Prozess mit ausreichend Zeit und Ressourcen.
* Interagieren Sie mit den Support- und Aktivierungssitzungen von Adobe, um Beratung und Unterstützung zu erhalten.

## Was sind AEM 6.5 LTS Service Packs?

AEM 6.5 LTS Service Packs sind ein kumulatives Update, das alle Fehlerbehebungen und Verbesserungen enthält, die seit der ersten Version von AEM 6.5 LTS vorgenommen wurden. Es wird empfohlen, das neueste Service Pack anzuwenden, um sicherzustellen, dass Ihre AEM-Instanz die aktuellen Funktionen und Sicherheits-Patches umfasst.

## Ich verwende derzeit AEM 6.5. Kann ich direkt auf AEM 6.5 LTS Service Pack aktualisieren, ohne vorher auf AEM 6.5 LTS GA zu aktualisieren?

Ja, Sie können direkt von AEM 6.5 auf ein beliebiges AEM 6.5 LTS Service Pack aktualisieren. Es wird empfohlen, die [Versionshinweise](/help/release-notes/release-notes.md) und den Abschnitt [Aktualisieren auf AEM 6.5 LTS](/help/sites-deploying/upgrade.md) zu lesen.

## Ich verwende derzeit AEM 6.5 LTS GA. Muss ich Code-Änderungen vornehmen, um auf AEM 6.5 LTS Service Packs zu aktualisieren?

Nein, Sie müssen keine Code-Änderungen vornehmen, um von AEM 6.5 LTS auf AEM 6.5 LTS Service Packs zu aktualisieren. Es wird jedoch immer empfohlen, die [Versionshinweise](/help/release-notes/release-notes.md) zu lesen und Ihre Anpassungen und Integrationen in einer Staging-Umgebung zu testen, bevor Sie das Service Pack auf Ihre Produktionsinstanz anwenden.

## Ich möchte mit einem neuen AEM 6.5 LTS-Setup von vorne beginnen. Kann ich direkt mit dem AEM 6.5 LTS Service Pack beginnen?

Ja, Sie können ein neues AEM 6.5 LTS Service Pack direkt einrichten, ohne AEM 6.5 LTS GA einzurichten. Es wird empfohlen, die [Versionshinweise](/help/release-notes/release-notes.md) und den Abschnitt [Benutzerdefinierte eigenständige Installation](/help/sites-deploying/custom-standalone-install.md) zu lesen, um weitere Informationen zu erhalten.
