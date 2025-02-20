---
title: Best Practices für die Bereitstellung
description: Erfahren Sie, wie Sie Adobe Experience Manager (AEM) so effizient und effektiv wie möglich bereitstellen und verwalten.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: ac26c0163309b6cb6c0cfde2098a8cc05955d03f
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 100%

---

# Best Practices für die Bereitstellung{#deploying-best-practices}

In den Best Practices für die Bereitstellung wird beschrieben, wie Adobe Experience Manager (AEM) am effizientesten und wirkungsvollsten bereitgestellt und verwaltet wird. Diese laufend erweiterte Liste von Themen enthält eine Vielzahl von Bereichen in AEM.

Für die folgenden Bereiche ist Dokumentation zu Best Practices und Empfehlungen für die Bereitstellung und Wartung verfügbar:

* [Oak](#oak)
* [Benutzeroberfläche](#ui)
* [Leistung](#performance)

Informationen zu Best Practices zur Verwaltung, Entwicklung oder Inhaltserstellung finden Sie in den folgenden Abschnitten:

* [Best Practices für die Verwaltung](/help/sites-administering/administer-best-practices.md)
* [Best Practices für die Entwicklung](/help/sites-developing/best-practices.md)
* [Best Practices für die Inhaltserstellung](/help/sites-authoring/best-practices.md)

Spezifische Dokumente werden in den folgenden Tabellen beschrieben und verlinkt.

## Oak {#oak}

[Oak](/help/sites-deploying/platform.md) ist ein leistungsstarkes skalierbares, hierarchisches Inhalts-Repository, das die Basis von AEM bildet.

<table>
 <tbody>
  <tr>
   <td><p>Skalierbarkeit, Leistung und Notfallwiederherstellung</p> </td>
   <td><a href="/help/sites-deploying/performance.md">Leistung und Skalierbarkeit</a></td>
   <td>Ein Whitepaper über die technischen Funktionen für Agilität, Leistung und Notfallwiederherstellung</td>
  </tr>
  <tr>
   <td>Empfohlene Oak-Bereitstellungen</td>
   <td><a href="/help/sites-deploying/recommended-deploys.md">Empfohlene Bereitstellungen</a></td>
   <td>Beschreibt Bereitstellungsszenarien</td>
  </tr>
  <tr>
   <td>Mongo-Topologie</td>
   <td><a href="/help/sites-deploying/recommended-deploys.md">Best Practices für die Mongo-Topologie</a></td>
   <td>Beschreibt die Mongo-Topologie – wann welche Topologie verwendet werden soll.</td>
  </tr>
  <tr>
   <td>Datenspeicheroptionen</td>
   <td><a href="/help/sites-deploying/data-store-config.md">Konfigurieren von Knoten und Datenspeichern</a></td>
   <td>In diesem Dokument werden Best Practices zum Speichern von Binärdaten und Inhaltsknoten erläutert. Enthält Informationen zur Verwendung des Datenspeichers Amazon S3.</td>
  </tr>
  <tr>
   <td>Suchen in Oak</td>
   <td><a href="/help/sites-deploying/best-practices-for-queries-and-indexing.md">Best Practices für Abfragen und Indizierung</a><br /> </td>
   <td>Beschreibt Best Practices für die Indizierung von Inhalten.</td>
  </tr>
 </tbody>
</table>

## Benutzeroberfläche {#ui}

Best Practices für die Benutzeroberfläche werden hier beschrieben: 

[Empfehlungen für Kunden zur Benutzeroberfläche](/help/sites-deploying/ui-recommendations.md)

AEM verfügt derzeit über zwei Benutzeroberflächen: die klassische und die Touch-optimierte Benutzeroberfläche in derselben Version. Daher müssen sich Kunden während der Projektimplementierung für die Nutzung der einen oder anderen entscheiden. Dieses Dokument soll bei der Entscheidungsfindung behilflich sein.

## Leistung {#performance}

Best Practices bezüglich der Leistung sind hier aufgeführt:

<table>
 <tbody>
  <tr>
   <td>Best Practices zur Qualitätssicherung</td>
   <td><a href="/help/sites-deploying/configuring-performance.md#best-practices-for-quality-assurance">Best Practices zur Qualitätssicherung</a></td>
   <td>Ein einheitlicher Überblick über die Probleme bei der Definition eines Testkonzepts speziell für Leistungstests in der <em>Veröffentlichungsumgebung</em>. Dies ist vor allem für QS-Beauftragte, Projektleitende und Systemadmins von Interesse.</td>
  </tr>
  <tr>
   <td>Verwenden des Dispatchers mit einem CDN </td>
   <td><a href="https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de#using-dispatcher-with-a-cdn">Verwenden des Dispatchers mit einem CDN</a></td>
   <td>Ein CDN (Content Delivery Network) wie Akamai Edge Delivery oder Amazon Cloud Front stellt Inhalte von einem Speicherort in der Nähe des Endbenutzers bereit.</td>
  </tr>
  <tr>
   <td>Leistungsoptimierung</td>
   <td><a href="/help/sites-deploying/configuring-performance.md">Leistungsoptimierung</a></td>
   <td>Ein wichtiger Faktor ist die Zeit, die Ihre Website benötigt, um auf Anfragen durch Besucherinnen und Besucher zu reagieren.</td>
  </tr>
  <tr>
   <td>Leistungstests</td>
   <td><a href="/help/sites-deploying/best-practices-for-performance-testing.md">Best Practices für Leistungstests</a></td>
   <td>Beschreibt Best Practices für die Durchführung von Leistungstests bei der AEM-Bereitstellung<br />  </td>
  </tr>
 </tbody>
</table>
