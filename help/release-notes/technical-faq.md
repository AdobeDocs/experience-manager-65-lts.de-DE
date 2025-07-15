---
title: Häufig gestellte technische Fragen (FAQ)
description: Häufig gestellte technische Fragen zu AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 051244f1-cc67-4222-bd45-0c135c28bb15
source-git-commit: ec722773ce3acff1d0de861523db8ff7df552c4b
workflow-type: tm+mt
source-wordcount: '247'
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

### Unterstützt AEM 6.5 LTS die Benutzersynchronisierung?

Ja, AEM 6.5 LTS unterstützt die Benutzersynchronisierung. Die Funktionalität der Benutzersynchronisierung zwischen AEM 6.5 und 6.5 LTS hat sich nicht geändert.

### Das Uber JAR auf Maven Central scheint beschädigt zu sein - was ist das Problem?

Stellen Sie sicher, dass Sie Uber JAR mit dem `apis` Classifier verwenden. Beachten Sie, dass sich die Verpackungsstruktur von Uber JAR in AEM 6.5 LTS geändert hat. Weitere Informationen finden Sie unter [Aktualisieren der Uber Jar-Version von AEM](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

## Abrufen zusätzlicher Hilfe

Wenn Probleme auftreten, die hier nicht behandelt werden:
* Lesen Sie [Versionshinweise](/help/release-notes/release-notes.md) auf bekannte Probleme.
* Wenn Sie Unterstützung benötigen, wenden Sie sich an den Adobe-Support.
