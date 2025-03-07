---
title: Schritte zum Upgrade von Installationen auf Anwendungs-Servern (WLP)
description: Erfahren Sie, wie Sie Instanzen von AEM aktualisieren, die über WebSphere Liberty bereitgestellt werden.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 2a5d9026-49bc-4766-bcbe-38d834c14f72
source-git-commit: 82af7ee5b3665dcc33b47e05c8580e9981728888
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 17%

---

# Schritte zum Upgrade von Installationen auf Anwendungs-Servern (WLP) {#upgrade-steps-for-application-server-installations-wlp}

>[!NOTE]
>
>Auf dieser Seite wird das Upgrade-Verfahren für AEM 6.5 LTS auf WLP (WebSphere® Liberty) beschrieben.

## Schritte vor der Aktualisierung {#pre-upgrade-steps}

Bevor Sie die Aktualisierung durchführen, müssen Sie einige Schritte ausführen. Weitere Informationen finden Sie unter [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) und [Wartungsaufgaben vor einer Aktualisierung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md). Stellen Sie außerdem sicher, dass Ihr System die [Anforderungen für AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md) erfüllt.

Überprüfen Sie [Planung des Upgrades](/help/sites-deploying/upgrade-planning.md) und wie Sie mit dem [AEM Analyzer](/help/sites-deploying/aem-analyzer.md) die Komplexität eines Upgrades von AEM abschätzen können.

### Migrationsvoraussetzungen {#migration-prerequisites}

* **Erforderliche Java-Version**: Vergewissern Sie sich, dass Sie IBM® Sumeru JRE 17 auf Ihrem WLP-Server installiert haben.

### Durchführen des Upgrades {#performing-the-upgrade}

1. Vergewissern Sie sich, dass Sie die [vor dem Upgrade](#pre-upgrade-steps) Schritte wie das Sichern des AEM 6.5-Servers abgeschlossen haben, bevor Sie eine Aktualisierung durchführen
1. Wählen Sie je nach Ihren Anforderungen einen der folgenden Aktualisierungspfade aus:
   1. **In-Place-Upgrade**: Wenn Ihr aktueller WLP-Server Servlet 6 unterstützt, können Sie ein In-Place-Upgrade durchführen und mit Schritt 3 fortfahren.
   1. **Sidegrade**: Wenn Sie ein neues Setup bevorzugen oder wenn Ihr WLP-Server Servlet 6 nicht unterstützt, richten Sie eine neue WLP-Instanz mit AEM 6.5 LTS ein und migrieren Sie den Inhalt, indem Sie dem Handbuch zur Migration von [AEM 6.5 zu AEM 6.5 LTS-Inhalten mit Oak-Upgrade](/help/sites-deploying/aem-65-to-aem-65lts-content-migration-using-oak-upgrade.md) folgen und zum Abschnitt [Bereitstellen der aktualisierten Codebasis](#deploy-upgraded-codebase) wechseln

1. Halten Sie die AEM-Instanz an. Dies kann in der Regel mithilfe dieses Befehls erfolgen:

   ```shell
   <path-to-wlp-directory>/bin/server stop server_name
   ```

1. Entfernen Sie die nicht mehr benötigten Dateien und Ordner. Insbesondere müssen Sie die folgenden Elemente entfernen:

   * Die Datei **cq-quickstart-65.war** aus dem `dropins` Ordner und dem `expanded` Ordner, die sich normalerweise unter `<path-to-aem-server>/dropins/cq-quickstart-65.war` bzw. `<path-to-aem-server>/apps/expanded/cq-quickstart-65.war` befinden
   * Der `launchpad/startup`. Sie können ihn löschen, indem Sie am Terminal den folgenden Befehl ausführen, vorausgesetzt, Sie befinden sich im Ordner „server“:

     ```shell
     rm -rf crx-quickstart/launchpad/startup
     ```

   * Die `base.jar`. Sie können dies tun, indem Sie die folgenden Befehle ausführen:

     ```shell
     find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
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
1. Installieren Sie Java 17 und stellen Sie sicher, dass es korrekt installiert ist, indem Sie Folgendes ausführen:

   ```shell
   java -version
   ```

1. Überprüfen Sie die Startparameter für den AEM-Server und stellen Sie sicher, dass Sie die Parameter entsprechend Ihren Anforderungen aktualisieren. Weitere Informationen finden [ unter ](/help/sites-deploying/custom-standalone-install.md#java-considerations) zu Java 17.
1. Laden Sie den neuen 6.5 LTS-WAR herunter und kopieren Sie ihn in den Dropins-Ordner unter: `/<path-to-aem-server>/dropins/`
1. AEM-Instanz starten: Dies kann normalerweise mithilfe dieses Befehls erfolgen:

   ```shell
   <path-to-wlp-directory>/bin/server start server_name
   ```

1. Wenn Sie benutzerdefinierte Änderungen in `sling.properties` haben, befolgen Sie bitte die folgenden Anweisungen:

   1. Beenden Sie die AEM-Instanz, indem Sie `<path-to-wlp-directory>/bin/server stop server_name` ausführen
   1. Wenden Sie Ihre benutzerdefinierten `sling.properties` auf die neu generierte `sling.properties` an (indem Sie auf die in Schritt 5 erstellte Sicherungsdatei verweisen)
   1. AEM-Instanz starten. Dies kann in der Regel durch Ausführen von Folgendem geschehen: `<path-to-wlp-directory>/bin/server start server_name`

## Bereitstellen einer aktualisierten Code-Basis {#deploy-upgraded-codebase}

Nach Abschluss des Upgrade-Prozesses sollte die aktualisierte Code-Basis bereitgestellt werden. Informationen zur Aktualisierung der Code-Basis, sodass sie in der Zielversion von AEM funktioniert, finden Sie auf der Seite [Aktualisieren von Codes und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md).

## Durchführen von Prüfungen und Fehlerbehebungen nach einem Upgrade {#perform-post-upgrade-checks-and-troubleshooting}

Siehe [Prüfungen und Fehlerbehebung nach einer Aktualisierung](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
