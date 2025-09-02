---
title: Häufig gestellte Fragen (FAQ)
description: Häufig gestellte Fragen zu AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: d18c9dc3-fdcc-4558-b9b6-ecf1ce61048a
source-git-commit: 9f9da819550b93d7a06b151962bf41751ecbc8b3
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 49%

---

# Häufig gestellte Fragen (FAQ) zu AEM 6.5 LTS {#faq}

Auf dieser Seite finden Sie Antworten auf häufig gestellte Fragen zu AEM 6.5 LTS.

## Warum hat Adobe 6.5 LTS für AEM veröffentlicht?

Adobe setzt sich weiterhin für die Sicherheit und Stabilität der bereitgestellten Anwendungen ein. Die langfristige Unterstützung für AEM 6.5 bildet die Grundlage für zukünftige Aktualisierungen für AEM 6.5. Insbesondere bietet AEM 6.5 LTS Unterstützung für Oracle Java 17 und Java 21 und ist die AEM-Verzweigung, die neue AEM-Funktionen und -Innovationen erhält.

## Ich gehöre zur On-Premise-Kundschaft. Was passiert, wenn ich nicht auf AEM 6.5 LTS aktualisiere?

AEM 6.5 LTS enthält wichtige Sicherheits- und Stabilitätsaktualisierungen, einschließlich Unterstützung für Oracle Java 17 und Java 21. Adobe unterstützt AEM 6.5 zwar noch für mindestens zwei Jahre, es wird jedoch empfohlen, dass Unternehmen beginnen, ein Upgrade auf 6.5 LTS zu planen.

## Sind meine bestehenden Anpassungen und Integrationen betroffen, wenn ich auf AEM 6.5 LTS aktualisiere?

AEM 6.5 LTS ist zwar auf Abwärtskompatibilität ausgerichtet, einige ältere Funktionen und Artefakte wurden jedoch entfernt.
Sie müssen unbedingt die [Versionshinweise](/help/release-notes/release-notes.md#deprecated-and-removed-features) lesen und das [AEM Analyzer-Tool](/help/sites-deploying/aem-analyzer.md) verwenden, um die Auswirkungen auf Ihre Anpassungen und Integrationen zu bewerten.

## Wie kann ich einen reibungslosen Übergang zu AEM 6.5 LTS sicherstellen?

Um einen reibungslosen Übergang sicherzustellen, wird Folgendes empfohlen:

* Lesen Sie die [Versionshinweise](/help/release-notes/release-notes.md) und die Dokumentation sorgfältig durch.
* Verwenden Sie das [AEM Analyzer-Tooö](/help/sites-deploying/aem-analyzer.md), um die Komplexität des Upgrades zu bewerten.
* Planen Sie den Upgrade-Prozess mit ausreichend Zeit und Ressourcen.
* Interagieren Sie mit den Support- und Aktivierungssitzungen von Adobe, um Beratung und Unterstützung zu erhalten.

## Was sind AEM 6.5 LTS Service Packs?

AEM 6.5 LTS Service Packs sind ein kumulatives Update, das alle Fehlerbehebungen und Verbesserungen enthält, die seit der ersten Version von AEM 6.5 LTS vorgenommen wurden. Es wird empfohlen, das neueste Service Pack anzuwenden, um sicherzustellen, dass Ihre AEM-Instanz mit den neuesten Funktionen und Sicherheits-Patches aktualisiert wird.

## Ich arbeite derzeit mit AEM 6.5. Kann ich direkt auf AEM 6.5 LTS Service Pack aktualisieren, ohne auf AEM 6.5 LTS GA zu aktualisieren?

Ja, Sie können direkt von AEM 6.5 auf ein beliebiges AEM 6.5 LTS Service Pack aktualisieren. Es wird empfohlen, den Abschnitt [Versionshinweise](/help/release-notes/release-notes.md) und [Aktualisieren auf AEM 6.5 LTS](/help/sites-deploying/upgrade.md) zu lesen.

## Ich arbeite derzeit mit AEM 6.5 LTS GA. Muss ich Code-Änderungen vornehmen, um auf AEM 6.5 LTS Service Packs zu aktualisieren?

Nein, Sie müssen keine Code-Änderungen vornehmen, um von AEM 6.5 LTS auf AEM 6.5 LTS Service Packs zu aktualisieren. Es wird jedoch immer empfohlen, die [Versionshinweise“ zu lesen ](/help/release-notes/release-notes.md) Ihre Anpassungen und Integrationen in einer Staging-Umgebung zu testen, bevor Sie das Service Pack auf Ihre Produktionsinstanz anwenden.

## Ich möchte neu mit einem neuen AEM 6.5 LTS-Setup beginnen. Kann ich direkt mit dem AEM 6.5 LTS Service Pack beginnen?

Ja, Sie können ein neues AEM 6.5 LTS Service Pack direkt einrichten, ohne den AEM 6.5 LTS GA-Build einzurichten. Es wird empfohlen, den Abschnitt [Versionshinweise](/help/release-notes/release-notes.md) und [Benutzerdefinierte eigenständige Installation](/help/sites-deploying/custom-standalone-install.md) für weitere Details zu lesen.
