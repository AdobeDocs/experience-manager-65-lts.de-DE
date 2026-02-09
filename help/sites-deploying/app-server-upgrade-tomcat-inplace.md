---
title: Schritte zum Upgrade von Anwendungs-Server-Installationen (Tomcat)
description: Erfahren Sie, wie Sie Instanzen von AEM aktualisieren, die über Tomcat bereitgestellt werden.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: b3c4e946a3f235fa0e3a0945f1ad692ee195e3ef
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 9%

---

# Upgrade-Schritte für Anwendungs-Server-Installationen (Tomcat - Inplace-Upgrade) {#upgrade-steps-for-application-server-installations-tomcat-inplace}

>[!NOTE]
>
>Auf dieser Seite wird das Upgrade-Verfahren (Inplace Upgrade) von AEM 6.5 LTS auf AEM 6.5 LTS Servicepack on Tomcat beschrieben. Informationen zum Upgrade von AEM 6.5 auf 6.5 LTS [&#x200B; Sie hier](/help/sites-deploying/app-server-upgrade-tomcat.md).

## Schritte vor der Aktualisierung {#pre-upgrade-steps}

Bevor Sie die Aktualisierung durchführen, müssen Sie einige Schritte ausführen. Weitere [&#x200B; finden Sie unter &#x200B;](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) vor einem Upgrade . Stellen Sie außerdem sicher, dass Ihr System die [Anforderungen für AEM 6.5 LTS Servicepack](/help/sites-deploying/technical-requirements.md) erfüllt, und lesen Sie [Überlegungen zur Upgrade-Planung](/help/sites-deploying/upgrade-planning.md).


### Migrationsvoraussetzungen {#migration-prerequisites}

* **Erforderliche Java-Version**: Vergewissern Sie sich, dass Oracle® JRE 17/21 auf Ihrem Tomcat-Server installiert ist.
* **Tomcat-Server**: Die unterstützten Versionen von Tomcat-Server für AEM 6.5 LTS und seine ServicePacks sind **10.0.x** und **10.1.x**.

### Durchführen des Upgrades {#performing-the-upgrade}

Alle Beispiele in diesem Verfahren verwenden Tomcat als Anwendungsserver und setzen voraus, dass bereits eine funktionierende Version von AEM 6.5 LTS bereitgestellt wurde. In dieser Anleitung wird die Aktualisierung von AEM Version **6.5** LTS auf **6.5 LTS** Servicepack beschrieben.

1. Wenn AEM 6.5 LTS bereits bereitgestellt ist, überprüfen Sie, ob die Bundles ordnungsgemäß funktionieren, indem Sie Folgendes aufrufen: *`https://<serveraddress:port>/system/console/bundles`*
1. Beenden Sie als Nächstes AEM 6.5 LTS. Dies kann über den Tomcat App Manager unter folgender Adresse durchgeführt werden: *`https://<serveraddress:port>/manager/html`*
1. Vergewissern Sie sich, dass Sie die [Aktivitäten vor dem Upgrade](#pre-upgrade-steps) wie das Backup des AEM 6.5 LTS-Servers abgeschlossen haben, bevor Sie irgendeine Upgrade-Aktivität durchführen
1. Beenden Sie den AEM 6.5 LTS Tomcat-Server. In den meisten Fällen können Sie dazu das Skript &quot;`./catalina.sh`&quot; ausführen, indem Sie diesen Befehl am Terminal ausführen:

   ```
   $CATALINA_HOME/bin/catalina.sh stop
   ```

1. Entfernen Sie die nicht mehr benötigten Dateien und Ordner. Insbesondere müssen Sie die folgenden Elemente entfernen:

   * Die **cq-quickstart-65.war** und der `cq-quickstart-65` Ordner aus `webapps` Ordner, der sich normalerweise unter `<path-to-aem-server>/webapps` befindet
   * Der `launchpad/startup`. Sie können ihn löschen, indem Sie am Terminal den folgenden Befehl ausführen, vorausgesetzt, Sie befinden sich im Ordner „server“:

     ```shell
     rm -rf <path-to-aem-server>/bin/crx-quickstart/launchpad/startup
     ```

   * Die `base.jar`. Sie können dies tun, indem Sie die folgenden Befehle ausführen:

     ```shell
     find <path-to-aem-server>/bin/crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
     ```

   * Die Datei `BootstrapCommandFile_timestamp.txt`:

     ```shell
     rm -f <path-to-aem-server>/bin/crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt
     ```

   * Entfernen Sie die `sling.options`-Datei, indem Sie Folgendes ausführen:

     ```shell
     find <path-to-aem-server>/bin/crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \; 
     ```

   * Entfernen Sie die `sling.bootstrap.txt`:

     ```shell
     rm -rf <path-to-aem-server>/bin/crx-quickstart/launchpad/sling_bootstrap.txt
     ```

1. Erstellen Sie eine Sicherung der `sling.properties`-Datei (normalerweise in `<path-to-aem-server>/bin/crx-quickstart/launchpad/` vorhanden) und löschen Sie sie
1. Kopieren Sie die WAR-Datei des AEM 6.5 LTS Servicepack in `<path-to-aem-server>/webapps` Ordner .
1. Starten Sie den Tomcat-Server für AEM 6.5 LTS, indem Sie Folgendes ausführen:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Überwachen Sie die Fehlerprotokolle beim Start von AEM, um sicherzustellen, dass keine Fehler vorhanden sind und AEM reibungslos ausgeführt wird
1. Nachdem AEM 6.5 LTS gestartet wurde, überprüfen Sie, ob die Bundles ordnungsgemäß funktionieren, indem Sie Folgendes aufrufen: *`https://<serveraddress:port>/cq/system/console/bundles`*

## Durchführen von Prüfungen und Fehlerbehebungen nach einem Upgrade {#perform-post-upgrade-checks-and-troubleshooting}

Weitere Informationen [&#x200B; Sie unter „Prüfungen und &#x200B;](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) nach einem Upgrade“.
