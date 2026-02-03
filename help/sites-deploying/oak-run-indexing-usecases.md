---
title: Oak-run.jar – Indizierungsanwendungsfälle
description: Erfahren Sie mehr über die verschiedenen Anwendungsfälle für die Durchführung der Indizierung mit dem Oak-run-Tool.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
noindex: true
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: a7a8a20a-e513-43df-80b7-1e6daf957f20
source-git-commit: c714e51f0c0368988ce552969747ab5fce5c186f
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 47%

---

# Oak-run.jar – Indizierungsanwendungsfälle{#oak-run-jar-indexing-use-cases}

Oak-run unterstützt Indizierungs-Anwendungsfälle über die Befehlszeile, ohne dass die Ausführung dieser Anwendungsfälle über die JMX-Konsole von AEM orchestriert werden muss.

Die allgemeinen Vorteile der Verwendung des Ansatzes &quot;`oak-run.jar` index command“ zur Verwaltung von Oak-Indizes sind:

* Der Befehl &quot;Oak-run index“ bietet seit der Veröffentlichung von AEM 6.4 ein neues Indizierungs-Tool.
* Oak-run verkürzt die Neuindizierungszeit, was sich insbesondere bei größeren Repositorys auszahlt.
* Oak-run verringert den Ressourcenverbrauch während der Neuindizierung in AEM, was die Gesamtleistung des Systems verbessert.
* Oak-run bietet eine bandexterne Neuindizierung und unterstützt damit Szenarios, in denen die Produktion verfügbar sein muss und keine Wartungs- oder Ausfallzeiten eingeplant werden können.

Die folgenden Abschnitte enthalten Beispielbefehle. Der Oak-run-Befehl „index“ unterstützt alle NodeStore- und BlobStore-Setups. Die folgenden Beispiele sind für Setups mit FileDataStore und SegmentNodeStore.

## Anwendungsfall 1: Prüfung der Indexkonsistenz {#usercase1indexconsistencycheck}

Dieser Anwendungsfall steht im Zusammenhang mit Indexbeschädigungen. In einigen Fällen ist es nicht möglich, festzustellen, welcher Index beschädigt wurde. Hierzu stellt Adobe Tools für folgende Aufgaben bereit:

* Führt Konsistenzprüfungen aller Indizes durch und erstellt einen Bericht darüber, welche Indizes gültig und welche nicht gültig sind.
* Das Tool kann auch verwendet werden, wenn kein Zugriff auf AEM möglich ist. 
* Die Verwendung ist einfach.

Verwenden Sie `--index-consistency-check`, um nach beschädigten Indizes zu suchen:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-consistency-check
```

Dieser Vorgang generiert einen Bericht in `indexing-result/index-consistency-check-report.txt`. Unten sehen Sie ein Beispiel für diesen Bericht:

```
Valid indexes :
        - /content/oak:index/enablementResourceName
        - /oak:index/cqProjectLucene
        - /oak:index/cqTagLucene
        - /oak:index/lucene
        - /oak:index/ntBaseLucene
        - /oak:index/socialLucene
    Invalid indexes :
        - /oak:index/atDamIndex
        - /oak:index/atIndex
        - /oak:index/cqPageLucene
        - /oak:index/damAssetLucene
        - /oak:index/groups
        - /oak:index/slingeventJob
        - /oak:index/users
        - /oak:index/workflowDataLucene
    Ignored indexes as these are not of type lucene:
        - /oak:index/acPrincipalName
        - /oak:index/active
```

### Vorteile {#uc1benefits}

Support- und Systemadministratoren können die Tools verwenden, um beschädigte Indizes schnell zu identifizieren und neu zu indizieren.

## Anwendungsfall 2: Indexstatistiken {#usecase2indexstatistics}

Zur Diagnose einiger Fälle im Zusammenhang mit der Abfrageleistung benötigte Adobe häufig eine vorhandene Indexdefinition sowie indexbezogene Statistiken aus der Kundeneinrichtung. Um die Fehlerbehebung zu vereinfachen, hat Adobe Tools erstellt, die Folgendes können:

1. Dump aller im System vorhandener Indexdefinitionen in einer einzigen JSON-Datei.

1. Dump wichtiger Statistiken aus vorhandenen Indizes. 

1. Dump von Indexinhalten für Offline-Analysen. 

1. Sie ist auch dann verwendbar, wenn kein Zugriff auf AEM möglich ist

Sie können die oben genannten Vorgänge mithilfe der folgenden Indexbefehle ausführen:

* `--index-info` – Sammelt verschiedene indexbezogene Statistiken und gibt deren Speicherinhalt aus

* `--index-definitions` – Sammelt Indexdefinitionen und gibt deren Speicherinhalt aus

* `--index-dump` – Gibt den Speicherinhalt von Indexinhalten aus

Unten sehen Sie ein Beispiel dafür, wie der Befehl in der Praxis arbeitet:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-info --index-definitions --index-dump
```

Die Berichte werden in `indexing-result/index-info.txt` und `indexing-result/index-definitions.json` erstellt.

Darüber hinaus werden dieselben Details über die Web-Konsole bereitgestellt und wären Teil der Konfigurations-Dump-Zip. Der Zugriff ist über folgende URL möglich:

`https://serverhost:serverport/system/console/status-oak-index-defn`

### Vorteile {#uc2benefits}

Dieses Tool aktiviert die schnelle Sammlung aller erforderlichen Details, die mit Indizierungs- oder Abfrageproblemen zusammenhängen, und verkürzt die für das Extrahieren dieser Informationen benötigte Zeit.

## Anwendungsfall 3 - Neuindizierung {#usecase3reindexing}

Je nach [Szenario](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing) muss manchmal eine Neuindizierung durchgeführt werden. Derzeit können Sie die Neuindizierung durchführen, indem Sie das `reindex`-Flag im Indexdefinitionsknoten mithilfe von CRXDE oder der Benutzeroberfläche des Index-Managers auf `true` setzen. Nachdem Sie das Flag gesetzt haben, wird die Neuindizierung asynchron ausgeführt. Nach dem Setzen der Markierung wird die Neuindizierung asynchron ausgeführt.

Einige wichtige Aspekte der Neuindizierung:

* Die Neuindizierung verläuft in `DocumentNodeStore`-Setups weitaus langsamer als in `SegmentNodeStore`-Setups, in denen der gesamte Inhalt lokal gespeichert ist. 

* Während der Neuindizierung wird beim derzeitigen Design der asynchrone Indexer blockiert, weshalb alle anderen asynchronen Indizes veralten, weil sie während der Indizierung nicht mehr aktualisiert werden. Wenn das System verwendet wird, können die Benutzer daher möglicherweise keine aktuellen Ergebnisse sehen.
* Bei der Neuindizierung muss das gesamte Repository durchlaufen werden, was die AEM-Einrichtung stark belasten und sich negativ auf das Endbenutzererlebnis auswirken kann.
* Bei einer `DocumentNodeStore`-Installation, in der die Neuindizierung sehr lange dauern kann, kann ein Mongo-Datenbankverbindungsfehler während des Vorgangs die Indizierung unterbrechen. In diesem Fall müssen Sie die Indizierung von Grund auf neu starten.


* Manchmal kann die Neuindizierung aufgrund der Textextraktion lange dauern. Ein solches Problem kann auftreten, wenn es spezifisch für Setups ist, die viele PDF-Dateien haben, wobei die Zeit, die mit der Textextraktion verbracht wird, sich auf die Indizierungszeit auswirken kann.

Um diese Ziele zu erreichen, unterstützt das Oak-run-Tool für Indizes verschiedene Modi für die Neuindizierung, die bei Bedarf verwendet werden können. Der Befehl Oak-run index bietet die folgenden Vorteile:

* **Out-of-Band-**: Die von Oak ausgeführte Neuindizierung kann getrennt von einem ausgeführten AEM-Setup ausgeführt werden. Dies minimiert die Auswirkungen auf die verwendete AEM-Instanz.

* **Out-of-Lane-Neuindizierung** – Die Neuindizierung hat keine Auswirkungen auf Indizierungsvorgänge. Der asynchrone Indexer kann andere Indizes weiterhin indizieren.

* **Vereinfachte Neuindizierung für DocumentNodeStore-Installationen** – Für `DocumentNodeStore`-Installationen kann die Neuindizierung mit einem einzigen Befehl ausgeführt werden, der sicherstellt, dass die Neuindizierung auf die optimalste Weise erfolgt.

* **Unterstützt die Aktualisierung der Indexdefinitionen und das Erstellen neuer Indexdefinitionen** 

### Neuindizierung – DocumentNodeStore {#reindexdocumentnodestore}

Für `DocumentNodeStore` Installationen können Sie die Neuindizierung mit einem einzigen Oak-Ausführungsbefehl durchführen:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore mongodb://server:port/aem
```

Dieser Vorgang bietet die folgenden Vorteile:

* Minimale Auswirkung auf das Ausführen von AEM-Instanzen. Die meisten Lesevorgänge können von Sekundär-Servern ausgeführt werden, und ausgeführte AEM-Caches sind nicht von all den für die Neuindizierung erforderlichen Durchläufen betroffen. 
* Benutzende können über die Option `--index-definitions-file` auch eine JSON-Datei eines neuen oder aktualisierten Indexes bereitstellen.

### Neuindizierung – SegmentNodeStore {#reindexsegmentnodestore}

Für `SegmentNodeStore`-Installationen kann die Neuindizierung auf eine der folgenden Weisen durchgeführt werden:

#### Online-Neuindizierung - SegmentNodeStore {#onlinereindexsegmentnodestore}

Folgen Sie dem üblichen Verfahren, bei dem die Neuindizierung durch Festlegen der Markierung `reindex` erfolgt.

#### Online-Neuindizierung - SegmentNodeStore - Die AEM-Instanz wird ausgeführt {#onlinereindexsegmentnodestoretheaeminstanceisrunning}

In `SegmentNodeStore`-Installationen kann nur ein Prozess im Lese-/Schreibmodus auf Segmentdateien zugreifen. Daher erfordern einige Vorgänge in der von Oak ausgeführten Indizierung zusätzliche manuelle Schritte, z. B.:

1. Text des Schritts.
1. Verbinden Sie die `oak-run` mit dem von AEM verwendeten Repository im schreibgeschützten Modus.
1. Führen Sie eine Indizierung anhand des folgenden Beispiels durch:

   ```shell
   java -jar oak-run-1.7.6.jar index --fds-path=/Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/datastore/ --checkpoint 26b7da38-a699-45b2-82fb-73aa2f9af0e2 --reindex --index-paths=/oak:index/lucene /Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/segmentstore/
   ```

1. Importieren Sie nach dem Ausführen des obigen Befehls die erstellten Indexdateien mit dem Vorgang `IndexerMBean#importIndex` aus dem Pfad, unter dem Oak-run die Indexdateien gespeichert hat.

In diesem Szenario müssen Sie den AEM-Server nicht stoppen und keine neue Instanz bereitstellen. Da für die Indizierung jedoch das gesamte Repository durchlaufen werden muss, erhöht sich die E/A-Last der Installation, was sich negativ auf die Performance auswirkt.

#### Online-Neuindizierung - SegmentNodeStore - Die AEM-Instanz wird heruntergefahren {#onlinereindexsegmentnodestoreaeminstanceisdown}

Für `SegmentNodeStore` Installationen können Sie die Neuindizierung mit einem einzigen Oak-Ausführungsbefehl durchführen. Die AEM-Instanz muss allerdings heruntergefahren werden.

Sie können die Neuindizierung mit dem folgenden Befehl auslösen:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore  /path/to/segmentstore/
```

Der Unterschied zwischen diesem und dem oben erläuterten Ansatz besteht darin, dass das Erstellen des Checkpoints und das Importieren des Indexes automatisch erfolgen. Der Nachteil besteht darin, dass AEM während des Prozesses beendet sein muss.

#### Out-of-Band-Neuindizierung - SegmentNodeStore {#outofbandreindexsegmentnodestore}

In diesem Anwendungsfall können Sie die Neuindizierung in einem geklonten Setup durchführen, um die Auswirkungen auf die laufende AEM-Instanz zu minimieren:

1. Erstellen Sie einen Checkpoint mithilfe eines JMX-Vorgangs. Wechseln Sie zur [JMX-Konsole](/help/sites-administering/jmx-console.md) und suchen Sie nach `CheckpointManager`. Klicken Sie anschließend auf den Vorgang **createCheckpoint (long p1)** und verwenden Sie einen hohen Ablaufwert in Sekunden (z. B. **2592000**).
1. Kopieren Sie den `crx-quickstart` Ordner auf einen neuen Computer.
1. Führen Sie die Neuindizierung mithilfe des Oak-run-Indexbefehls durch.

1. Kopieren Sie die generierten Indexdateien auf einen AEM-Server.

1. Importieren Sie die Indexdateien über JMX.

In diesem Anwendungsfall muss der Zugriff auf den Datenspeicher von einer anderen Instanz aus möglich sein. Dies ist möglicherweise nicht möglich, wenn `FileDataStore` sich in einer Cloud-basierten Speicherlösung wie EBS befindet. Diese Situation schließt das Szenario aus, in dem auch `FileDataStore` geklont wird. Wenn die Indexdefinition keine Volltextindizierung durchführt, ist kein Zugriff auf den `DataStore` erforderlich.

## Anwendungsfall 4 - Aktualisieren von Indexdefinitionen {#usecase4updatingindexdefinitions}

Zurzeit können Sie Änderungen der Indexdefinitionen über das Paket [ACS Ensure Index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) versenden. Sie können die Indexdefinitionen in einem Inhaltspaket bereitstellen und dann eine Neuindizierung durchführen, indem Sie das `reindex`-Flag auf `true` setzen.


Dies funktioniert gut für kleinere Installationen, bei denen die Neuindizierung nicht viel Zeit in Anspruch nimmt. Bei sehr großen Repositorys benötigt die Neuindizierung jedoch erheblich mehr Zeit. In solchen Fällen können Sie jetzt die Tools für die Oak-Index-Ausführung verwenden.

Oak-run unterstützt jetzt die Bereitstellung von Indexdefinitionen im JSON-Format und das Erstellen des Indexes im bandexternen Modus, in dem keine Änderungen an einer Live-Instanz ausgeführt werden.

Für diesen Anwendungsfall ist der folgende Prozess zu berücksichtigen:

1. Ein Entwickler aktualisiert die Indexdefinitionen in einer lokalen Instanz und generiert dann mit der Option `--index-definitions` eine JSON-Indexdefinitionsdatei.
1. Die aktualisierte JSON-Datei wird dann an den Systemadministrator weitergeleitet.
1. Die bzw. der Systemadmin verfolgt den Out-of-Band-Ansatz und bereitet den Index in einer anderen Installation vor.
1. Nach Abschluss des Vorgangs werden die generierten Indexdateien in eine laufende AEM-Installation importiert.
