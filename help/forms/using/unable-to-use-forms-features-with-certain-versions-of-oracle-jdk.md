---
title: Experience Manager Forms kann mit bestimmten Versionen von Oracle JDK nicht verwendet werden
description: Experience Manager Forms kann mit bestimmten Versionen von Oracle JDK nicht verwendet werden
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 4aa45f02-ff89-4e40-a15d-e62c5879a87d
source-git-commit: cf2f70432ccf9ebc80847cf5ec6acfe630feb39f
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 100%

---

# Experience Manager Forms kann mit bestimmten Versionen von Oracle JDK nicht verwendet werden {#unable-to-use-forms-with-certain-versions-of-oracle-jdk}

Das Problem tritt bei den folgenden Versionen auf:

* Experience Manager 6.3 Forms
* Experience Manager 6.4 Forms
* Experience Manager 6.5 Forms

## Problem {#issue}

Der Benutzer stößt auf die folgende Ausnahme:
`Caused by: javax.xml.xpath.XPathExpressionException: javax.xml.transform.TransformerException: JAXP0801002: the compiler encountered an XPath expression containing '101' operators that exceeds the '100' limit set by 'FEATURE_SECURE_PROCESSING'.`

## Grund {#reason}

Die Ausnahme tritt auf, wenn Sie Experience Manager Forms mit einer Version von Oracle JDK (Java Development Kit) ausführen, die größer oder gleich den folgenden Versionen ist:

* [JDK7u341](https://www.oracle.com/java/technologies/javase/7u341-relnotes.html)
* [JDK8u331](https://www.oracle.com/java/technologies/javase/8u331-relnotes.html)
* [JDK11u15](https://www.oracle.com/java/technologies/javase/11-0-15-relnotes.html)

Die oben genannten Versionen und spätere Versionen von Java enthalten neue XML-Verarbeitungsbeschränkungen in der JVM (Java Virtual Machine), die dazu führen, dass bestimmte Forms-spezifische Vorgänge fehlschlagen.

## Problemumgehung {#workaround}

1. Stoppen Sie Ihren Experience Manager Forms-Server.
1. Konfigurieren Sie das folgende JVM-Argument für Ihren Anwendungs-Server:

   `-Djdk.xml.xpathExprGrpLimit=100`
   `-Djdk.xml.xpathExprOpLimit=10000`
   `-Djdk.xml.xpathTotalOpLimit=10000`

   Dies setzt die Systemeigenschaft in JVM auf einen relativ hohen Wert, sodass das Standard-Limit nicht erreicht wird.

1. Starten Sie Ihren Experience Manager Forms-Server.
