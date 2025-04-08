---
title: Häufig gestellte technische Fragen (FAQ)
description: Häufig gestellte technische Fragen zu AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 2352420843c613884ad3cae487ed048bd775e294
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 2%

---

# Häufig gestellte technische Fragen zu AEM 6.5 LTS {#technical-faq}

Auf dieser Seite finden Sie Antworten auf häufig gestellte technische Fragen zu AEM 6.5 LTS.

## Häufig gestellte Fragen zu technischen Themen

### Der `/systemalive`-Endpunkt ist in AEM 6.5 LTS nicht mehr verfügbar.

Das Felix System Ready-Bundle, das konfiguriert wurde, um den `/systemalive`-Endpunkt bereitzustellen, wird nicht mehr unterstützt und durch Apache Felix Health Checks ersetzt. Dieses Bundle ist nicht mehr in AEM 6.5 LTS enthalten.

Der neue Endpunkt für die Konsistenzprüfung ist unter `/system/health` verfügbar und wird mithilfe von Apache Felix-Konsistenzprüfungen implementiert.

Eine ausführliche Dokumentation zum Felix Health Check-Framework finden Sie in der [Felix-](https://github.com/apache/felix-dev/blob/master/healthcheck/README.md).

### Unterstützung der AEM Groovy-Konsole

Die AEM Groovy-Konsolenversion, die in AEM 6.5 verwendet wurde, funktioniert möglicherweise in AEM 6.5 LTS nicht, da Guava-Abhängigkeiten fehlen. Die neu unterstützte Version der AEM Groovy-Konsole ist [.0.8](https://mvnrepository.com/artifact/be.orbinson.aem/aem-groovy-console/19.0.8).

## Abrufen zusätzlicher Hilfe

Wenn Probleme auftreten, die hier nicht behandelt werden:
* Lesen Sie [Versionshinweise](/help/release-notes/release-notes.md) auf bekannte Probleme.
* Wenn Sie Unterstützung benötigen, wenden Sie sich an den Adobe-Support.
