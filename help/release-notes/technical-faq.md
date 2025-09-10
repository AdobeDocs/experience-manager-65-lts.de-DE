---
title: Häufig gestellte technische Fragen (FAQ)
description: Häufig gestellte technische Fragen zu AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 051244f1-cc67-4222-bd45-0c135c28bb15
source-git-commit: f983fc1edc613feaa070c4e82a92aabab9d50cbb
workflow-type: ht
source-wordcount: '247'
ht-degree: 100%

---

# Technische FAQ zu AEM 6.5 LTS {#technical-faq}

Auf dieser Seite finden Sie Antworten auf häufig gestellte technische Fragen zu AEM 6.5 LTS.

## Technische FAQs

### Der Endpunkt `/systemalive` ist in AEM 6.5 LTS nicht mehr verfügbar.

Das Felix System Ready-Bundle, das konfiguriert wurde, um den Endpunkt `/systemalive` bereitzustellen, wird nicht mehr unterstützt und durch Apache Felix Health Checks ersetzt. Dieses Bundle ist nicht mehr in AEM 6.5 LTS enthalten.

Der neue Endpunkt für die Konsistenzprüfung ist unter `/system/health` verfügbar und wird mithilfe von Apache Felix Health Checks implementiert.

Eine ausführliche Dokumentation zum Felix Health Check-Framework finden Sie in der [Felix-Dokumentation](https://github.com/apache/felix-dev/blob/master/healthcheck/README.md).

### AEM Groovy-Konsolenunterstützung

Die AEM Groovy-Konsolenversion, die in AEM 6.5 verwendet wurde, funktioniert möglicherweise in AEM 6.5 LTS nicht, da Guava-Abhängigkeiten fehlen. Die neu unterstützte Version der AEM Groovy-Konsole ist [19.0.8](https://github.com/orbinson/aem-groovy-console/releases/download/19.0.8/aem-groovy-console-all-19.0.8.zip).

### Unterstützt AEM 6.5 LTS die Benutzersynchronisierung?

Ja, AEM 6.5 LTS unterstützt die Benutzersynchronisierung. Die Funktionalität der Benutzersynchronisierung hat sich zwischen AEM 6.5 und 6.5 LTS nicht geändert.

### Uber Jar auf Maven Central scheint beschädigt zu sein. Wo liegt das Problem?

Stellen Sie sicher, dass Sie Uber Jar mit dem Classifier `apis` verwenden. Beachten Sie, dass sich die Verpackungsstruktur von Uber Jar in AEM 6.5 LTS geändert hat. Weitere Informationen finden Sie unter [Aktualisieren der Uber Jar-Version von AEM](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

## Abrufen zusätzlicher Hilfe

Wenn Probleme auftreten, die hier nicht behandelt werden:
* Prüfen Sie die [Versionshinweise](/help/release-notes/release-notes.md) auf bekannte Probleme.
* Wenn Sie Unterstützung benötigen, wenden Sie sich an den Adobe-Support.
