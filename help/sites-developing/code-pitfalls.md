---
title: Fallstricke beim Programmieren
description: Häufige Fallstricke beim Programmieren, die Sie bei der Entwicklung für AEM vermeiden sollten
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 95656312-2648-455e-80fb-3e03bf1cd633
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 100%

---

# Fallstricke beim Programmieren{#code-pitfalls}

## Sling-Bindungen im Java-Code vermeiden {#avoid-sling-bindings-in-java-code}

Sling-Bindungen sind in 90 % der Fälle ungeeignet, um Zugriff auf einen Dienst zu erhalten. Stattdessen sollten Sie *@Reference*- oder *@Inject*-Anmerkungen verwenden.

## Thread.interrupt im Java-Code vermeiden {#avoid-thread-interrupt-in-java-code}

Bei *Thread.interrupt* ist Vorsicht geboten, da diese Methode Dateien, darunter Lucene-Dateien und persistente Cache-Dateien, schließen kann, wenn sie zum falschen Zeitpunkt aufgerufen wird.

## Mischen von Java-Synchronisierung mit ReadWriteLocks vermeiden {#avoid-mixing-java-synchronization-with-readwritelocks}

Dies kann zu Überschneidungen führen, bei denen der Code irgendwann zum Stillstand kommt.
