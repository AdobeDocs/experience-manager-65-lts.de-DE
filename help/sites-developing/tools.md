---
title: Test- und Tracking-Tools
description: AEM bietet ein Framework zum Testen der Benutzeroberfläche der Komponenten und einen Mechanismus zum Testen und Debuggen von Komponenten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 4aa0f10d-e915-4ad2-a886-080ed8b9b10f
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 100%

---

# Test- und Tracking-Tools{#testing-and-tracking-tools}

## Testen {#testing}

AEM bietet:

* [ein Framework für das Testen von Komponentenbenutzeroberflächen](/help/sites-developing/hobbes.md).
* [einen Mechanismus zum Testen und Debuggen von Komponenten](/help/sites-developing/developer-mode.md).

Im Folgenden finden Sie zwei Open-Source-Test-Tools:

**Selenium**

Selenium wird für Funktionstests in einem Browser mit einer Benutzerin bzw. einem Benutzer pro Aktivität verwendet. Das Tool zeichnet Testschritte (Klicks) entweder als HTML-Tabellen oder als Java™-Klassen auf.

Weitere Informationen finden Sie unter [https://www.selenium.dev/](https://www.selenium.dev/).

**JMeter**

JMeter wird für das Tracking von Anfragen verwendet und kann für Funktions-, Leistungs- und Belastungstests verwendet werden.

Weitere Informationen finden Sie unter [https://jmeter.apache.org/](https://jmeter.apache.org/).

Außerdem sind viele proprietäre Tools für die Automatisierung von Tests und die Verwaltung von Testplänen verfügbar.

### Tracking {#tracking}

Die folgenden Tools stehen zur Verfügung. Eine wichtige Angelegenheit ist jedoch in allen Fällen die Verfügbarkeit der Daten für alle Mitglieder des Projekt-Teams, sowohl auf Partner- als auch auf Kundenseite.

**Bugzilla**

Ein Fehler-Tracking, das Ihren eigenen Anforderungen entsprechend konfiguriert werden kann.

**Tabellen**

Tabellen sind zwar nicht für das Fehler-Tracking gedacht, werden aber oft als solche *miss* braucht, da sie leicht verständlich sind und viele Benutzer Erfahrung mit ihrer Verwendung haben.

Wenn Tabellen als Tracker verwendet werden, dann:

* sollten sie einfach gehalten werden.
* sollte die Anzahl der einzelnen Tabellen möglichst gering gehalten werden.
* müssen sie regelmäßig aktualisiert werden.
* sollte nur eine Primärkopie gepflegt werden, deren Speicherort allen bekannt ist.
* sollten sie allen Projektmitgliedern zugänglich sein.
* dürfen Kopien verteilt werden, falls Sicherheit ein Anliegen ist (oft in großen Unternehmen) und ein gemeinsamer Zugriff nicht möglich ist, solange alle verstehen, dass es sich bei den Tabellen um Kopien handelt, die nicht aktualisiert werden können.

Auch für das Tracking von Fehlern und Funktionsanforderungen sind proprietäre Tools vorhanden.
