---
title: Schritte zum Upgrade von Anwendungs-Server-Installationen (Tomcat)
description: Erfahren Sie, wie Sie Instanzen von AEM aktualisieren, die über Tomcat bereitgestellt werden.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 7f8de16f-9e9a-4d37-9978-d26c496b911c
source-git-commit: b835dbf6fd7f40a2a1e1ca26c8a6870b69a19cbe
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 17%

---

# Schritte zum Upgrade von Anwendungs-Server-Installationen (Tomcat) {#upgrade-steps-for-application-server-installations-tomcat}

>[!NOTE]
>
>Auf dieser Seite wird das Upgrade-Verfahren für AEM 6.5 LTS auf Tomcat beschrieben.

## Schritte vor der Aktualisierung {#pre-upgrade-steps}

Bevor Sie die Aktualisierung durchführen, müssen Sie einige Schritte ausführen. Weitere Informationen finden Sie unter [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) und [Wartungsaufgaben vor einer Aktualisierung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md). Stellen Sie außerdem sicher, dass Ihr System die [Anforderungen für AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md) erfüllt, und lesen Sie [Überlegungen zur Upgrade-](/help/sites-deploying/upgrade-planning.md) und wie [Analyzer](/help/sites-deploying/aem-analyzer.md) Ihnen bei der Schätzung der Komplexität helfen kann.


### Migrationsvoraussetzungen {#migration-prerequisites}

* **Erforderliche Java-Version**: Vergewissern Sie sich, dass Oracle® JRE 17 auf Ihrem Tomcat-Server installiert ist.
* **Tomcat-Server**: Die für 6.5 LTS erforderliche Tomcat-Server-Version ist **11.0.x**.

### Durchführen des Upgrades {#performing-the-upgrade}

In allen Beispielen in diesem Verfahren wird Tomcat als Anwendungs-Server verwendet. Zudem wird vorausgesetzt, dass Sie bereits eine funktionierende AEM-Version installiert haben. In dieser Anleitung wird die Aktualisierung von AEM Version **.6.5 auf**&#x200B;**6.5 LTS** beschrieben.

1. Wenn AEM 6.5 bereits bereitgestellt ist, überprüfen Sie, ob die Bundles ordnungsgemäß funktionieren, indem Sie Folgendes aufrufen: *`https://<serveraddress:port>/system/console/bundles`*
1. Beenden Sie als Nächstes AEM 6.5. Dies kann über den Tomcat App Manager unter folgender Adresse durchgeführt werden: *`https://<serveraddress:port>/manager/html`*
1. Vergewissern Sie sich, dass Sie die [Aktivitäten vor dem Upgrade](#pre-upgrade-steps) wie das Backup des AEM 6.5-Servers abgeschlossen haben, bevor Sie irgendwelche Upgrades durchführen
1. Installieren Sie Java 17 und stellen Sie sicher, dass es korrekt installiert ist, indem Sie den Befehl ausführen:

   ```
   java –version
   ```

1. Einrichten eines mit AEM 6.5 LTS kompatiblen Tomcat-Servers
1. Überprüfen Sie die Startparameter für den AEM-Server und stellen Sie sicher, dass Sie die Parameter entsprechend den Systemanforderungen aktualisieren. Weitere Informationen finden [ unter ](/help/sites-deploying/custom-standalone-install.md#java-considerations) zu Java 17
1. Stellen Sie den neu heruntergeladenen 6.5 LTS-WAR mit Java 17 auf dem Tomcat-Server bereit und starten Sie den AEM 6.5 LTS-Tomcat-Server, indem Sie Folgendes ausführen:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Sobald die AEM ausgeführt wird, stellen Sie sicher, dass alle Bundles den Status „Wird ausgeführt“ aufweisen, indem Sie auf zugreifen: *`https://<serveraddress:port>/cq/system/console/bundles`*
1. Beenden Sie den AEM 6.5 LTS Tomcat-Server. In den meisten Fällen können Sie dazu das Skript &quot;`./catalina.sh`&quot; ausführen, indem Sie diesen Befehl am Terminal ausführen:

   ```
   $CATALINA_HOME/bin/catalina.sh stop
   ```

1. Migrieren Sie jetzt Ihren Inhalt von AEM 6.5 zu AEM 6.5 LTS, indem Sie die folgenden Schritte hier ausführen: [Migration von AEM 6.5 zu AEM 6.5 LTS-Inhalt mit Oak-Upgrade](/help/sites-deploying/aem-65-to-aem-65lts-content-migration-using-oak-upgrade.md)
1. Nachdem der Inhalt migriert wurde, wenden Sie alle benutzerdefinierten Änderungen an, die in der `sling.properties` erforderlich sind
1. Starten Sie den Tomcat-Server für AEM 6.5 LTS, indem Sie Folgendes ausführen:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Überwachen Sie die Fehlerprotokolle beim Start von AEM, um sicherzustellen, dass keine Fehler vorhanden sind und AEM reibungslos ausgeführt wird
1. Nachdem AEM 6.5 LTS gestartet wurde, überprüfen Sie, ob die Bundles ordnungsgemäß funktionieren, indem Sie Folgendes aufrufen: *`https://<serveraddress:port>/cq/system/console/bundles`*

## Bereitstellen einer aktualisierten Code-Basis {#deploy-upgraded-codebase}

Nach Abschluss des Upgrade-Prozesses sollte die aktualisierte Code-Basis bereitgestellt werden. Informationen zur Aktualisierung der Code-Basis, sodass sie in der Zielversion von AEM funktioniert, finden Sie auf der Seite [Aktualisieren von Codes und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md).

## Durchführen von Prüfungen und Fehlerbehebungen nach einem Upgrade {#perform-post-upgrade-checks-and-troubleshooting}

Weitere Informationen [ Sie unter „Prüfungen und ](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) nach einem Upgrade“.
