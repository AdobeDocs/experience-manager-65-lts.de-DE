---
title: Durchführen einer ersetzenden Aktualisierung
description: Erfahren Sie, wie Sie ein In-Place-Upgrade für AEM 6.5 LTS durchführen.
topic-tags: upgrading
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 67bd9b29ccc525111710a397cca5de1c961486ac
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 47%

---

# Durchführen einer ersetzenden Aktualisierung {#performing-an-in-place-upgrade}

>[!NOTE]
>
>Auf dieser Seite wird das Verfahren für das In-Place-Upgrade für AEM 6.5 LTS beschrieben. Wenn Sie eine Installation haben, die auf einem Anwendungs-Server bereitgestellt wird, lesen Sie [Upgrade-Schritte für Anwendungs-Server-Installationen](/help/sites-deploying/app-server-upgrade.md).

## Schritte vor der Aktualisierung {#pre-upgrade-steps}

Bevor Sie die Aktualisierung durchführen, müssen Sie einige Schritte ausführen. Weitere Informationen finden Sie unter [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) und [Wartungsaufgaben vor einer Aktualisierung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md). Stellen Sie außerdem sicher, dass Ihr System die [Anforderungen für AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md) erfüllt, und lesen Sie [Überlegungen zur Upgrade-](/help/sites-deploying/upgrade-planning.md) und wie [Analyzer](/help/sites-deploying/pattern-detector.md) Ihnen bei der Schätzung der Komplexität helfen kann.

<!--Finally, the downtime during the upgrade can be significally reduced by indexing the repository **before** performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

## Migrationsvoraussetzungen {#migration-prerequisites}

* **Erforderliche Java-Mindestversion:** Stellen Sie sicher, dass Oracle Java™ 17 auf Ihrem System installiert ist.

## Vorbereitung der „AEM Quickstart“-JAR-Datei {#prep-quickstart-file}

1. Herunterladen der neuen JAR-Datei für AEM 6.5 LTS

1. [Bestimmen des korrekten Befehls zum Starten des Upgrades](/help/sites-deploying/in-place-upgrade.md#determining-the-correct-upgrade-start-command-determining-the-correct-upgrade-start-command)

1. Instanz anhalten, wenn sie gerade ausgeführt wird

1. Verwenden Sie die neue AEM 6.5 LTS-JAR-Datei, um die alte JAR-Datei außerhalb des `crx-quickstart` zu ersetzen

1. Erstellen Sie ein Backup der `sling.properties`-Datei (normalerweise im `crx-quickstart/conf/` vorhanden) und löschen Sie sie dann

1. Entpacken Sie die Quickstart-JAR-Datei, indem Sie Folgendes ausführen:

   ```shell
   java -Xmx4096m -jar aem-quickstart.jar -unpack
   ```

1. Der Befehl „unpack“ generiert eine neue `sling.properties`-Datei unter dem `crx-quickstart/conf/`. Sie können Ihre benutzerdefinierten Änderungen jetzt auf die neu generierte `sling.properties`-Datei anwenden.

<!-- Alexandru: drafting temporarily

## Content Repository Migration {#content-repository-migration}

This migration is not required if you are upgrading from AEM 6.3. For versions older than 6.3, Adobe provides a tool that can be used to migrate the repository to the new version of the Oak Segment Tar present in AEM 6.3. It is provided as part of the quickstart package and is mandatory for any upgrades that will be using TarMK. Upgrades for environments that are using MongoMK do not require repository migration. For more information on what the benefits of the new Segment Tar format are, see the [Migrating to Oak Segment Tar FAQ](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions).

The actual migration is performed using the standard AEM quickstart jar file, executed with a new `-x crx2oak` option which executes the crx2oak tool to simplify the upgrade and make it more robust.

>[!NOTE]
>
>If you are performing TarMK repository content migration using the CRX2Oak Quickstart extension, you might remove the **samplecontent** runmode by adding the following to the migration command line:
>
>* `--promote-runmode nosamplecontent`
>

To determine the command that you should run, use the following command:

```shell
java -Xmx4096m -jar aem-quickstart.jar -v -x crx2oak -xargs -- --load-profile <<YOUR_PROFILE>> <<ADDITIONAL_FLAGS>>
```

Where `<<YOUR_PROFILE>>` and `<<ADDITIONAL_FLAGS>>` are replaced with the profile and flags listed in the following table:

<table>
 <tbody>
  <tr>
   <td><strong>Source Repository</strong></td>
   <td><strong>Target Repository</strong></td>
   <td><strong>Profile</strong></td>
   <td><strong>Additional Flags</strong><br /> </td>
  </tr>
  <tr>
   <td>crx2 or TarMK with <code>FileDataStore</code></td>
   <td>TarMK</td>
   <td>segment-fds</td>
   <td>See Troubleshooting section below</td>
  </tr>
  <tr>
   <td>crx2</td>
   <td>MongoMK</td>
   <td>mongo-from-crx2 </td>
   <td><code>-T mongo-uri=mongo://mongo-host:mongo-port -T mongo-db=mongo-database-name</code></td>
  </tr>
  <tr>
   <td>TarMK or crx2 with <code>S3DataStore</code></td>
   <td>TarMK</td>
   <td>segment-custom-ds</td>
   <td>See Troubleshooting section below</td>
  </tr>
  <tr>
   <td>TarMK with no datastore</td>
   <td>TarMK</td>
   <td>segment-no-ds</td>
   <td> </td>
  </tr>
  <tr>
   <td>MongoMK</td>
   <td>MongoMK</td>
   <td>No migration is needed</td>
   <td> </td>
  </tr>
 </tbody>
</table>

**Where:**

* `mongo-host` is the MongoDB server IP (for example, 127.0.0.1)

* `mongo-port` is the MongoDB server port (for example: 27017)

* `mongo-database-name` represents the name of the database (for example: aem-author)

**You may also require additional switches for the following scenarios:**

* If you are performing the upgrade on a Windows system where Java memory mapping is not handled correctly, add the `--disable-mmap` parameter to the command.

For additional instructions on using the crx2oak tool, see Using the [CRX2Oak Migration Tool](/help/sites-deploying/using-crx2oak.md). The crx2oak helper JAR can be manually upgraded if needed, by manually replacing it with newer versions after unpacking the quickstart. Its location in the AEM installation folder is: `<aem-install>/crx-quickstart/opt/extensions/crx2oak.jar`. The newest version of the CRX2Oak migration tool is available for download from the Adobe Repository at: [https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/)

If the migration has completed successfully, the tool will exit with an exit code of zero. Additionally, check for WARN and ERROR messages in the `upgrade.log` file, located under `crx-quickstart/logs` in the AEM installation directory, as these could indicate non-fatal errors that occurred during the migration.

Check the configuration files beneath `crx-quickstart/install` folder. If a migration was necessary these will be updated to reflect the target repository.

**A note on datastores:**

While `FileDataStore` is the new default for AEM 6.3 installations, using an external datastore is not required. While using an external datastore is recommended as a best practice for production deployments, it is not a prerequisite to upgrade. Due to the complexity already present in upgrading AEM, Adobe recommends performing the upgrade without doing a datastore migration. If desired, a datastore migration can be executed afterwards as a separate effort.

## Troubleshooting Migration Issues {#troubleshooting-migration-issues}

Skip this section if you are upgrading from 6.3. While the provided crx2oak profiles should meet the needs of most customers, there are times when additional parameters will be necessary. If you run into an error during your migration, it is possible that there are aspects of your environment that require additional configuration options to be provided. If so, you will likely encounter the following error:

**Checkpoints are not copied, because no external datastore has been specified. This will result in the full repository reindexing on the first start. Use --skip-checkpoints to force the migration or see https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration for more info.**

For some reason, the migration process needs access to binaries in the datastore and is unable to find it. To specify your datastore configuration, include the following flags in the `<<ADDITIONAL_FLAGS>>` portion of your migration command:

**For S3 datastores:**

```shell
--src-s3config=/path/to/SharedS3DataStore.config --src-s3datastore=/path/to/datastore
```

Where `/path/to/SharedS3DataStore.config` represents the path to your S3 datastore config file and `/path/to/datastore` represents the path to your S3 datastore.

**For File datastores:**

```shell
--src-datastore=/path/to/datastore
```

Where `/path/to/datastore` represents the path to your File Datastore.

-->

## Durchführen der Aktualisierung {#performing-the-upgrade}

**Bei Verwendung von S3:**

1. Entfernen Sie etwaige JARs unter `crx-quickstart/install`, die mit einer früheren Version des S3 Connectors verknüpft sind.

1. Laden Sie die neueste Version des S3 Connectors 1.60.2 von [https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/) <!-- Alexandru: this is a stub link for now --> herunter.

1. Extrahieren Sie den S3-Connector (Version 1.60.2) und kopieren Sie den Inhalt der folgenden Ordner unter `crx-quickstart/install` wie folgt:

   1. `com.adobe.granite.oak.s3connector-1.60.2/jcr_root/libs/system/install/1` unter `crx-quickstart/install/1` kopieren
   1. `com.adobe.granite.oak.s3connector-1.60.2/jcr_root/libs/system/install/15` unter `crx-quickstart/install/15` kopieren

Starten Sie nun die AEM-Instanz mit dem neuen Befehl, der anhand der Informationen im Abschnitt [Bestimmen des richtigen Startbefehls für das Upgrade](#determining-the-correct-upgrade-start-command) ermittelt wurde.

### Bestimmen des korrekten Befehls zum Starten des Upgrades {#determining-the-correct-upgrade-start-command}

>[!NOTE]
>
>Die Unterstützung für einige Java 8/11-Argumente wurde in Java 17 entfernt. Weitere Informationen finden Sie unter [Oracle Java™ 17-](https://docs.oracle.com/en/java/javase/17/docs/specs/man/java.html) und [Überlegungen zu Java&amp;trade-Argumenten für AEM 6.5 LTS](/help/sites-deploying/custom-standalone-install.md#java-17-considerations-java-considerations).

Um das Upgrade auszuführen, ist es wichtig, AEM mithilfe der JAR-Datei zu starten, um die Instanz aufzurufen.

Beachten Sie, dass der Start von AEM über das Startskript das Upgrade nicht startet. Die meisten Kundinnen und Kunden starten AEM per Startskript und haben dieses Startskript so angepasst, dass es Schalter für Umgebungskonfigurationen wie Speichereinstellungen, Sicherheitszertifikate usw. enthält. Aus diesem Grund empfiehlt Adobe die folgende Vorgehensweise, um den richtigen Upgrade-Befehl zu ermitteln:

1. Führen Sie in einer aktiven AEM-Instanz Folgendes in der Befehlszeile aus: 

   ```shell
   ps -ef | grep java
   ```

1. Suchen Sie nach dem AEM-Prozess. Er sieht in etwa so aus:

   ```shell
   /usr/bin/java -server -Xmx1024m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar crx-quickstart/app/cq-quickstart-6.5.0-standalone-quickstart.jar start -c crx-quickstart -i launchpad -p 4502 -Dsling.properties=conf/sling.properties
   ```

1. Ändern Sie den Befehl, indem Sie den Pfad zur vorhandenen JAR-Datei (in diesem Fall `crx-quickstart/app/aem-quickstart*.jar`) durch die neue LTS-JAR-Datei für AEM 6.5 ersetzen, die dem `crx-quickstart` gleichgeordnet ist. Wenn wir unseren vorherigen Befehl als Beispiel heranziehen, würde unser Befehl folgendermaßen lauten:

   ```shell
   /usr/bin/java -server -Xmx4096m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar <AEM-6.5-LTS.jar> -c crx-quickstart -p 4502 -Dsling.properties=conf/sling.properties
   ```

   Dadurch wird sichergestellt, dass alle richtigen Speichereinstellungen, benutzerdefinierten Ausführungsmodi und anderen Umgebungsparametern für das Upgrade angewendet werden. Nach Abschluss des Upgrades kann die Instanz bei zukünftigen Starts vom Startskript gestartet werden.

## Bereitstellen einer aktualisierten Code-Basis {#deploy-upgraded-codebase}

Sobald die ersetzende Aktualisierung abgeschlossen ist, sollte die aktualisierte Code-Basis bereitgestellt werden. Informationen zur Aktualisierung der Code-Basis, sodass sie in der Zielversion von AEM funktioniert, finden Sie auf der Seite [Aktualisieren von Codes und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md).

## Durchführen von Prüfungen und Fehlerbehebung nach einer Aktualisierung {#perform-post-upgrade-check-troubleshooting}

Siehe [Prüfungen und Fehlerbehebung nach einer Aktualisierung](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
