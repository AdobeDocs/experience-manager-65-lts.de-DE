---
title: Schritte zur Aktualisierung von Installationen auf Anwendungs-Servern
description: Erfahren Sie, wie Sie Instanzen von AEM aktualisieren, die über Anwendungs-Server bereitgestellt werden.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 28701105452c347c5470fdb582d783e7aef1adb0
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 20%

---

# Schritte zur Aktualisierung von Installationen auf Anwendungs-Servern {#upgrade-steps-for-application-server-installations}

>[!NOTE]
>
>Auf dieser Seite wird das Upgrade-Verfahren für AEM 6.5 LTS war on WLP (WebSphere Liberty) beschrieben.

## Schritte vor der Aktualisierung {#pre-upgrade-steps}

Bevor Sie die Aktualisierung durchführen, müssen Sie einige Schritte ausführen. Weitere Informationen finden Sie unter [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) und [Wartungsaufgaben vor einer Aktualisierung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md). Stellen Sie außerdem sicher, dass Ihr System die Anforderungen für AEM 6.5 LTS erfüllt. Erfahren Sie, wie Analyzer Ihnen dabei helfen kann, die Komplexität Ihres Upgrades zu schätzen, und lernen Sie außerdem Planen des Upgrades kennen ([Planung des Upgrades](/help/sites-deploying/upgrade-planning.md)).

### Migrationsvoraussetzungen {#migration-prerequisites}

* **Erforderliche Mindestversion für Java**: Vergewissern Sie sich, dass IBM Sumeru JRE 17 auf Ihrem WLP-Server installiert ist.

### Durchführen des Upgrades {#performing-the-upgrade}

1. Erstellen Sie eine Sicherungskopie Ihrer Instanz, bevor Sie mit einer Aktualisierung beginnen.
1. Identifizieren Sie, ob Sie ein In-Place-Upgrade oder ein Sidegrade benötigen, je nach der Version des verwendeten WLP-Servers. Wenn Ihr aktueller WLP-Server Servlet 6 unterstützt, können Sie ein In-Place-Upgrade durchführen und mit dieser Dokumentation fortfahren. Andernfalls müssen Sie Sidegrade durchführen. Für das Sidegrade folgen Sie bitte dem Link Inhaltsmigration mit Oak-Upgrade-Dokumentation - [ hinzufügen]
1. Halten Sie die AEM-Instanz an. Dies kann in der Regel mithilfe dieses Befehls erfolgen:

   ```shell
   <path-to-wlp-directory>/bin/server stop server_name
   ```

1. Entfernen Sie die nicht mehr benötigten Dateien und Ordner. Insbesondere müssen Sie die folgenden Elemente entfernen:

   * Die `cq-quickstart-65.war` aus dem Ordner `dropins` und dem erweiterten Ordner befinden sich normalerweise unter `<path-to-aem-server>/dropins/cq-quickstart-65.war` bzw. `<path-to-aem-server>/apps/expanded/cq-quickstart-65.war`
   * Der `launchpad/startup`. Sie können ihn löschen, indem Sie am Terminal den folgenden Befehl ausführen, vorausgesetzt, Sie befinden sich im Ordner „server“:

     ```shell
     rm -rf crx-quickstart/launchpad/startup
     ```

   * Die `base.jar`. Sie können dies tun, indem Sie die folgenden Befehle ausführen:

     ```shell
     find crx-quickstart/launchpad -type f -name 
     "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
     ```

   * Die Datei `BootstrapCommandFile_timestamp.txt`:

     ```shell
     rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt
     ```

   * Entfernen Sie die `sling.options`-Datei, indem Sie Folgendes ausführen:

     ```shell
     find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \; 
     ```

   * Entfernen Sie die `sling.bootstrap.txt`:

     ```shell
     rm -rf crx-quickstart/launchpad/sling_bootstrap.txt
     ```

1. Erstellen Sie eine Sicherung der `sling.properties`-Datei (normalerweise in `crx-quickstart/conf/` vorhanden) und löschen Sie sie
1. **Ändern Sie in der `server.xml`-Datei die Version des Servlets** 6.0).
1. Überprüfen Sie die Startparameter für den AEM-Server und stellen Sie sicher, dass Sie die Parameter entsprechend Ihren Systemanforderungen aktualisieren. Weitere Informationen finden [ unter ](/help/sites-deploying/custom-standalone-install.md) eigenständige Installation
1. Installieren Sie Java 17 und stellen Sie sicher, dass es korrekt installiert ist, indem Sie Folgendes ausführen:

   ```shell
   java -version
   ```

1. Laden Sie das neue WAR 6.5 LTS von Software Distribution herunter und kopieren Sie es in den Dropins-Ordner unter: `/<path-to-aem-server>/dropins/`
1. AEM-Instanz starten: Dies kann normalerweise mithilfe dieses Befehls erfolgen:

   ```shell
   <path-to-wlp-directory>/bin/server start server_name
   ```

1. Wenn Sie benutzerdefinierte Änderungen in `sling.properties` haben, befolgen Sie bitte die folgenden Anweisungen:

   1. Beenden Sie die AEM-Instanz, indem Sie `<path-to-wlp-directory>/bin/server stop server_name` ausführen
   1. Wenden Sie Ihre benutzerdefinierten `sling.properties` auf die neu generierte `sling.properties` an (indem Sie auf die in Schritt 6 erstellte Sicherungsdatei verweisen)
   1. AEM-Instanz starten. Dies kann in der Regel durch Ausführen von Folgendem geschehen: `<path-to-wlp-directory>/bin/server start server_name`

## Bereitstellen einer aktualisierten Code-Basis {#deploy-upgraded-codebase}

Sobald die ersetzende Aktualisierung abgeschlossen ist, sollte die aktualisierte Code-Basis bereitgestellt werden. Die Schritte zum Aktualisieren der Code-Basis, sodass sie in der Zielversion von AEM funktioniert, finden Sie auf der Seite [Aktualisieren von Codes und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) .

## Durchführen von Prüfungen und Fehlerbehebungen nach einem Upgrade {#perform-post-upgrade-checks-and-troubleshooting}

Weitere Informationen [ Sie unter „Prüfungen und ](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) nach einem Upgrade“.