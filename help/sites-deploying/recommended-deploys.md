---
title: Empfohlene Bereitstellungen
description: In diesem Artikel werden die empfohlenen Topologien für AEM beschrieben.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: 9baa4111-831a-4b68-9ce5-82aeeb06e07f
source-git-commit: 408f6aaedd2cc0315f6e66b83f045ca2716db61d
workflow-type: tm+mt
source-wordcount: '1493'
ht-degree: 99%

---

# Empfohlene Bereitstellungen{#recommended-deployments}

>[!NOTE]
>
>Diese Seite beschreibt empfohlene Topologien für AEM. Weitere Informationen zu Clustering-Funktionen und zum Konfigurieren derselben finden Sie in der [Apache Sling-Dokumentation zur Discovery-API](https://sling.apache.org/documentation/bundles/discovery-api-and-impl.html) (in englischer Sprache).

Ab AEM 6.2 fungieren Mikrokernel als Persistenz-Manager. Die Auswahl des geeigneten Mikrokernels für Ihre Anforderungen hängt vom Zweck der Instanz und von dem von Ihnen in Betracht gezogenen Bereitstellungstyp ab.

Die nachfolgenden Beispiele sollen ihre empfohlene Verwendung in den gängigsten AEM-Konfigurationen veranschaulichen.

## Bereitstellungsszenarien {#deployment-scenarios}

### Einzelne TarMK-Instanz {#single-tarmk-instance}

In diesem Szenario wird eine einzige TarMK-Instanz auf einem einzigen Server ausgeführt.

**Dies ist das Standard-Bereitstellungsszenario für Autoreninstanzen.**

![chlimage_1-15](assets/chlimage_1-15.png)

Die Vorteile:

* Einfach
* Einfache Wartung
* Gute Leistung

Die Nachteile:

* Nicht über die Grenzen der Server-Kapazität hinaus skalierbar
* Keine Failover-Kapazität

### TarMK-Cold-Standby {#tarmk-cold-standby}

Eine TarMK-Instanz fungiert als primäre Instanz. Das Repository der primären Instanz wird auf einem Standby-Failover-System repliziert.

Der Cold-Standby-Mechanismus kann auch als Sicherungsmechanismus verwendet werden, da das gesamte Repository ständig auf dem Failover-Server repliziert wird. Der Failover-Server wird im Cold-Standby-Modus ausgeführt. Das bedeutet, dass nur der HttpReceiver der Instanz ausgeführt wird.

![chlimage_1-16](assets/chlimage_1-16.png)

Die Vorteile:

* Einfachheit
* Wartbarkeit
* Leistung
* Failover

Die Nachteile:

* Nicht über die Grenzen der Server-Kapazität hinaus skalierbar
* Ein Server ist die meiste Zeit im Leerlauf
* Kein automatisches Failover. Eine externe Erkennung ist erforderlich, bevor das Failover-System Anfragen verarbeiten kann.

>[!NOTE]
>
>Weitere Informationen zum Konfigurieren von TarMK-Cold-Standby in AEM finden Sie in [diesem](/help/sites-deploying/tarmk-cold-standby.md) Artikel.

>[!NOTE]
>
>Für die Cold-Standby-Bereitstellung in diesem TarMK-Beispiel müssen die primäre und die Standby-Instanz separat lizenziert werden, da eine konstante Replikation auf dem Failover-Server stattfindet. Weitere Informationen zur Lizenzierung finden Sie in den [allgemeinen Lizenzbedingungen von Adobe](https://www.adobe.com/de/legal/terms/enterprise-licensing.html).

### TarMK-Farm {#tarmk-farm}

Mehrere Oak-Instanzen werden jeweils mit einer TarMK-Instanz ausgeführt. Die TarMK-Repositorys sind unabhängig voneinander und müssen synchron gehalten werden.

Die Synchronisierung der Repositorys wird dadurch erreicht, dass der Autorenserver dieselben Inhalte auf allen Mitgliedern der Farm veröffentlicht. Weitere Informationen finden Sie unter [Replikation](/help/sites-deploying/replication.md).

**Dies ist das Standard-Bereitstellungsszenario für Veröffentlichungsumgebungen.**

![chlimage_1-17](assets/chlimage_1-17.png)

Die Vorteile:

* Leistung
* Skalierbarkeit für Lesezugriff
* Failover

### Oak-Cluster mit MongoMK-Failover für hohe Verfügbarkeit in einem einzigen Rechenzentrum {#oak-cluster-with-mongomk-failover-for-high-availability-in-a-single-datacenter}

>[!NOTE]
>
>Die minimal unterstützte Version von Mongo ist Mongo 6.

Dieser Ansatz bedeutet, dass mehrere Oak-Instanzen auf ein MongoDB-Replikat in einem einzigen Rechenzentrum zugreifen und so einen aktiv-aktiven Cluster für die AEM-Autorenumgebung erstellen. In MongoDB dienen Replikatsätze dazu, bei Hardware- oder Netzwerkausfällen für hohe Verfügbarkeit und Redundanz zu sorgen.

![chlimage_1-18](assets/chlimage_1-18.png)

Die Vorteile:

* Möglichkeit zur horizontalen Skalierung mit neuen AEM-Autoreninstanzen
* Hohe Verfügbarkeit, Redundanz und automatisiertes Failover der Datenschicht

Die Nachteile:

* In einigen Szenarien kann die Leistung geringer sein als bei TarMK.

### Oak-Cluster mit MongoMK-Failover über mehrere Rechenzentren hinweg {#oak-cluster-with-mongomk-failover-across-multiple-datacenters}

Dieser Ansatz bedeutet, dass mehrere Oak-Instanzen auf ein MongoDB-Replikat in mehreren Rechenzentren zugreifen und so einen aktiv-aktiven Cluster für die AEM-Autorenumgebung erstellen. Bei mehreren Rechenzentren bietet die MongoDB-Replikation dieselbe hohe Verfügbarkeit und Redundanz sowie jetzt die Möglichkeit, Rechenzentrumsausfälle zu bewältigen.

![oakclustermongofailover2datacenters](assets/oakclustermongofailover2datacenters.png)

Die Vorteile:

* Möglichkeit zur horizontalen Skalierung mit neuen AEM-Autoreninstanzen
* Hohe Verfügbarkeit, Redundanz und automatisiertes Failover der Datenschicht (einschließlich Rechenzentrumsausfällen)

>[!NOTE]
>
>In der obigen Abbildung werden AEM-Server 3 und AEM-Server 4 mit einem inaktiven Status dargestellt, wobei von einer Netzwerklatenz zwischen den AEM-Servern im Rechenzentrum 2 und dem primären MongoDB-Knoten im Rechenzentrum 1 ausgegangen wird. Diese Latenz ist höher als die Anforderung, die unter [Adobe Experience Manager mit MongoDB – Checklisten](/help/sites-deploying/aem-with-mongodb.md#checklists) dokumentiert ist. Wenn die maximale Latenzzeit mit den Anforderungen vereinbar ist, z. B. durch die Verwendung von Verfügbarkeitszonen, können auch die AEM-Server im Rechenzentrum 2 aktiv sein und einen aktiv-aktiven AEM-Cluster über mehrere Rechenzentren hinweg bilden.

>[!NOTE]
>
>Weitere Informationen zu den in diesem Abschnitt beschriebenen MongoDB-Architekturkonzepten finden Sie unter [MongoDB-Replikation](https://docs.mongodb.org/manual/replication/).

## Mikro-Kernel: Welcher soll verwendet werden? {#microkernels-which-one-to-use}

Bei der Wahl zwischen den beiden verfügbaren Mikro-Kerneln muss eine Grundregel berücksichtigt werden: TarMK ist für Leistung konzipiert, während MongoMK für Skalierbarkeit eingesetzt wird.

Anhand dieser Entscheidungsmatrizen können Sie ermitteln, welche Bereitstellungsart für Ihre Anforderungen am besten geeignet ist.

Adobe empfiehlt Kundinnen und Kunden dringend, TarMK als Standard-Persistenztechnologie in allen Bereitstellungsszenarien zu verwenden, sowohl für die Autoren- als auch die Veröffentlichungsinstanz von AEM. Davon ausgenommen sind die unten aufgeführten Anwendungsfälle.

### Ausnahmen für die Auswahl von AEM MongoMK gegenüber TarMK auf Autoreninstanzen {#exceptions-for-choosing-aem-mongomk-over-tarmk-on-author-instances}

Der Hauptgrund dafür, warum anstatt des TarMK der MongoMK als Persistenz-Backend ausgewählt werden sollte, liegt in der horizontalen Skalierung der Instanzen. Das bedeutet, dass immer mindestens zwei aktive Autoreninstanzen ausgeführt werden und MongoDB als Persistenzspeichersystem verwendet wird. Die Notwendigkeit, mehr als eine Autoreninstanz auszuführen, resultiert im Allgemeinen aus der Tatsache, dass die CPU- und Speicherkapazität eines einzelnen Servers, der alle gleichzeitigen Authoring-Aktivitäten unterstützt, nicht mehr ausreicht.

Es ist quasi unmöglich, vorherzusagen, wie das genau Parallelitätsmodell nach der Live-Schaltung einer neuen Site aussehen wird. Daher empfiehlt Adobe, bei der Bewertung, ob MongoMK und zwei oder mehr aktive Autorenknoten verwendet werden sollen, die folgenden Kriterien zu berücksichtigen:

1. Anzahl der benannten, verbundenen Benutzer an einem Tag: Tausende oder mehr.
1. Anzahl der gleichzeitigen Benutzer: Hunderte oder mehr.
1. Volumen der erfassten Assets pro Tag: Hunderttausende oder mehr.
1. Volumen der Seitenbearbeitungen pro Tag: Hunderttausende oder mehr (einschließlich automatisierte Aktualisierungen, z. B. über Multi-Site-Manager oder Newsfeed-Erfassungen)
1. Volumen der Suchvorgänge pro Tag: Zehntausende oder mehr.

>[!NOTE]
>
>Mithilfe von [Tough Day](/help/sites-developing/tough-day.md) kann die Leistung der Kundenanwendung im Kontext der bereitgestellten Hardware-Konfiguration bewertet werden. 

Eine Mindestbereitstellung mit MongoDB umfasst normalerweise die folgende Topologie:

* Eine MongoDB-Replikatgruppe mit einem primären und zwei sekundären Knoten, wobei alle MongoDB-Instanzen in einer Verfügbarkeitszone mit einer Latenz von unter 15 Millisekunden für jeden Knoten ausgeführt werden.
* Ein Cluster von Autoreninstanzen mit einem Leader-Knoten, einem Nicht-Leader-Knoten und beiden, die jederzeit aktiv sind, wobei jede der Autoreninstanzen in jedem der Datenzentren ausgeführt wird, in denen die primären und sekundären MongoDB-Instanzen ausgeführt werden.

Darüber hinaus wird dringend empfohlen, den Datenspeicher auf einem freigegebenen Dateisystem oder Amazon S3 so zu konfigurieren, dass die Assets oder Binärdateien nicht in MongoDB gespeichert werden. Dadurch wird eine optimale Leistung innerhalb der Bereitstellung sichergestellt.

Ein weiterer Vorteil, der sich durch die Bereitstellung einer MongoDB-Replikatgruppe mit einem Cluster von zwei oder mehr Autoreninstanzen ergibt, ist das automatisierte Wiederherstellungsszenario mit minimalen Ausfallzeiten bei einem Ausfall der Autoreninstanzen, der MongoDB-Replikatgruppe oder des gesamten Rechenzentrums. Dennoch sollte die Wahl von MongoMK gegenüber TarMK nicht ausschließlich von der Wiederherstellungsanforderung bestimmt werden, da TarMK ebenfalls eine Lösung mit minimalen Ausfallzeiten und einem kontrollierten Failover-Mechanismus bieten kann.

Wenn erwartet wird, dass die oben genannten Kriterien innerhalb der ersten 18 Monate nach der Bereitstellung nicht erfüllt werden, wird Folgendes empfohlen: Stellen Sie AEM zunächst mit TarMK bereit, bewerten Sie Ihre Konfiguration zu einem späteren Zeitpunkt erneut, wenn die oben genannten Kriterien zutreffen, und entscheiden Sie dann, ob Sie bei TarMK bleiben oder zu MongoMK migrieren möchten.

### Ausnahmen für die Auswahl von AEM MongoMK gegenüber TarMK bei Veröffentlichungsinstanzen {#exceptions-for-choosing-aem-mongomk-over-tarmk-on-publish-instances}

Die Bereitstellung von MongoMK für Veröffentlichungsinstanzen wird nicht empfohlen. Die Veröffentlichungsschicht der Bereitstellung wird fast immer als Farm mit unabhängigen Veröffentlichungsinstanzen bereitgestellt, auf denen TarMK ausgeführt wird und die durch das Replizieren von Inhalten von den Autoreninstanzen synchronisiert werden. Diese für Veröffentlichnungsinstanzen geeignete Shared-Nothing-Architektur ermöglicht die horizontale, lineare Skalierung der bereitgestellten Veröffentlichungsschicht. Die Farm-Topologie bietet außerdem den Vorteil, dass Aktualisierungen oder Upgrades fortlaufend auf Veröffentlichungsinstanzen angewendet werden können, sodass bei Änderungen an der Veröffentlichungsebene keine Ausfallzeiten erforderlich sind.

### Voraussetzungen und Empfehlungen für die Bereitstellung von AEM mit MongoMK {#prerequisites-and-recommendations-when-deploying-aem-with-mongomk}

Falls Sie eine MongoMK-Bereitstellung für AEM in Betracht ziehen, liegt eine Reihe von Voraussetzungen und Empfehlungen für AEM vor.

**Obligatorische Voraussetzungen für MongoDB-Bereitstellungen:**

1. Die Bereitstellungsarchitektur und -dimensionierung von MongoDB muss Teil der Projektimplementierung sein und mithilfe von Adobe Consulting oder MongoDB-Architekten erfolgen, die mit AEM vertraut sind.
1. Das Partner- oder Kunden-Team muss über MongoDB-Fachwissen verfügen, um die Aufrechterhaltung und Wartung einer bestehenden oder neuen MongoDB-Umgebung sicher gewährleisten zu können.
1. Sie können sich für die Bereitstellung der kommerziellen oder Open-Source-Version von MongoDB entscheiden (AEM unterstützt beide), müssen jedoch einen Wartungs- und Supportvertrag für MongoDB direkt von MongoDB Inc. erwerben.
1. AEM- und MongoDB-Architekturen und -Infrastrukturen sollten insgesamt von einer Adobe AEM-Fachkraft klar definiert und validiert werden;
1. Prüfen Sie das Supportmodell für AEM-Bereitstellungen, die MongoDB umfassen.

**Dringende Empfehlungen für MongoDB-Bereitstellungen:**

* Lesen Sie den Artikel zur [MongoDB-Bereitstellungsprüfung für Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).
* Gehen Sie die [Betriebs-Checkliste für MongoDB](https://docs.mongodb.org/manual/administration/production-checklist/) durch.
* Nehmen Sie an einer [online verfügbaren Zertifizierungsschulung für MongoDB](https://university.mongodb.com/) teil.

>[!NOTE]
>
>Bei allen weiteren Fragen zu diesen Richtlinien, Voraussetzungen und Empfehlungen wenden Sie sich bitte an die [ Adobe-Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html).
