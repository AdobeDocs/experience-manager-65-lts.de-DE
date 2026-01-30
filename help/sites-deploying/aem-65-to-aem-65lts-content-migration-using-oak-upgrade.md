---
title: Migration von AEM 6.5 zu AEM 6.5 LTS-Inhalten mit Oak-Upgrade
description: Erfahren Sie, wie Sie mithilfe des Oak-Upgrade-Tools Inhalte von AEM 6.5 auf AEM 6.5 LTS migrieren.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 8c4ffb0e-b4dc-4a81-ac43-723754cbc0de
source-git-commit: a85b54d5a7c3b00f95f439941a390dcfee883187
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Migration von AEM 6.5 zu AEM 6.5 LTS-Inhalten mit Oak-Upgrade {#aem-65-to-aem-65lts-content-migration-using-oak-upgrade}

In diesem Dokument wird erläutert, wie Sie Adobe Experience Manager von **6.5** auf **6.5 LTS** aktualisieren, wobei der Schwerpunkt auf der Migration des Inhalts-Repositorys liegt. Es behandelt die Verwendung des Oak-Upgrade-Tools zur präzisen und kontrollierten Übertragung von Inhalten zwischen Repositorys.

## Voraussetzungen {#prerequisites}

Stellen Sie vor Beginn der Migration sicher, dass die folgenden Anforderungen erfüllt sind:

1. Java-Kompatibilität: AEM 6.5 LTS muss installiert und für die Ausführung mit Java™ 17 konfiguriert sein. Starten Sie nach der Einrichtung die AEM-Instanz und stellen Sie sicher, dass alle Bundles aktiv sind und ohne Probleme ausgeführt werden
1. Systemressourcen: Stellen Sie sicher, dass ausreichend Speicherplatz und Arbeitsspeicher für beide Repositorys während des Migrationsprozesses verfügbar sind
1. Oak-Upgrade-Tool: Laden Sie die `oak-upgrade`-JAR-Datei aus dem [offiziellen Maven-Repository](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) herunter. Stellen Sie sicher, dass die Version mit der in AEM 6.5 LTS verwendeten Oak-Kernversion übereinstimmt. Das Oak-Upgrade-Tool läuft auf Oracle® Java™ 11 oder höher

## Migrationsprozess {#step-by-step-migration-process}

### Anhalten von AEM 6.5 und AEM 6.5 LTS {#stopping-aem65-and-aem65lts}

Beenden Sie vor Beginn der Migration Ihre LTS-Instanzen von AEM 6.5 und AEM 6.5. Dadurch wird sichergestellt, dass das Repository sich in einem stabilen Zustand befindet und während der Migration keine zusätzlichen Schreibvorgänge stattfinden.

### Sichern der AEM 6.5-Instanz {#backing-up-the-aem65-instance}

Erstellen Sie eine vollständige Sicherung Ihrer AEM 6.5-Instanz, falls noch nicht geschehen.

### Verwenden des Oak-Upgrade-Tools für die Inhaltsmigration {#using-the-oak-upgrade-tool-for-content-migration}

Das Oak-Upgrade-Tool wird wie im Folgenden gezeigt über die Befehlszeile ausgeführt:

```
java -jar oak-upgrade-*.jar [options] /path/to/source/repository /path/to/destination/repository 
```

Im Folgenden finden Sie die wichtigsten Befehle und Optionen:

**Schlüsseloptionen**

* `--include-paths`: Geben Sie Teilbäume an, die in die Migration einbezogen werden sollen. In diesem Beispiel wird der Befehl verwendet:

  ```
  java -jar oak-upgrade-*.jar --include-paths=/content/site /old/repository /new/repository
  ```

* `--exclude-paths`: Schließen Sie bestimmte Pfade von der Migration aus. Seien Sie vorsichtig, wenn Sie diese Option verwenden. Wenn der Pfad auf dem Zielsystem vorhanden ist, wird er entfernt. In diesem Beispiel wird der Befehl verwendet:

  ```
  java -jar oak-upgrade-*.jar --exclude-paths=/content/old_site /old/repository /new/repository 
  ```

* `--copy-binaries`: Standardmäßig migriert Oak-upgrade nur Verweise auf Binärdateien, sodass die Dateien im ursprünglichen Blob-/Datenspeicher verbleiben. Daher ist das neue Repository weiterhin auf den Quellspeicher für Binärdateien angewiesen. Um Binärdateien zusammen mit dem Repository-Inhalt zu migrieren, verwenden Sie den Parameter `--copy-binaries` , um alle Binärdaten in den neuen Speicher zu kopieren, wie unten dargestellt:

  ```
  java -jar oak-upgrade-*.jar \
  --copy-binaries \
  --src-datastore=/old/repository/datastore \
  --datastore=/new/repository/datastore \
  /old/repository \
  /new/repository 
  ```

### Checkpoints migrieren {#migratiing-checkpoints}

Beim Migrieren eines alten SegmentMK-Repositorys (vor Oak 1.6) zu einem neuen SegmentMK (Oak-Version größer oder gleich 1.6) werden die Checkpoints ebenfalls migriert. Durch diesen Prozess wird eine Neuindizierung vermieden, wenn die Oak zum ersten Mal im neuen Repository ausgeführt wird. Die Checkpoints werden jedoch in den folgenden Fällen nicht migriert:

1. Benutzerdefinierte Ein-, Ausschluss- oder Zusammenführungspfade werden angegeben oder
1. Das System kopiert die Binärdateien per Verweis. Es wird kein Quelldatenspeicher angegeben und zwei verschiedene Checkpoints enthalten eine andere Binärdatei unter demselben Pfad.

Im zweiten Fall gibt Oak-Upgrade die folgende Warnung aus und bricht ab:

```
Checkpoints are not copied, because no external datastore has been specified. This results in the full repository reindexing on the first start. Use --skip-checkpoints to force the migration or see https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration for more info. 
```

Die einfachste Möglichkeit, dieses Problem zu beheben, besteht darin, den Quelldatenspeicher in den Befehlszeilenoptionen anzugeben (beispielsweise `--src-datastore` oder `--src-s3datastore`).

Die Warnung kann auch ignoriert werden, aber in diesem Fall wird das Repository beim ersten Start vollständig neu indiziert. Es kann sich um einen langen Prozess handeln, insbesondere für die große Instanz. Das Repository kann erst nach Abschluss des Neuindizierungsprozesses verwendet werden. Verwenden Sie die Option `--skip-checkpoints` , um die Warnung zu unterdrücken.

Sie können das Repository auch offline neu indizieren, bevor Sie AEM mit [Offline-Neuindizierung](/help/sites-deploying/offline-reindexing.md) starten, um eine vollständige Neuindizierung beim ersten Start zu vermeiden.

Weitere Informationen zum Oak-Upgrade-Tool und zur erweiterten Verwendung finden Sie in der [offiziellen Dokumentation](https://jackrabbit.apache.org/oak/docs/migration.html).
