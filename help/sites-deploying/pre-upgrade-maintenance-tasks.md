---
title: Wartungsaufgaben vor einem Upgrade
description: Erfahren Sie mehr über die Aufgaben, die vor einem AEM-Upgrade empfohlen werden.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 1dd5d370-d1d4-4d15-9663-35b941b9076b
source-git-commit: 8f7bbc3887601e10cf29e99ee54959a10c8a3f98
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Wartungsaufgaben vor einem Upgrade{#pre-upgrade-maintenance-tasks}

Bevor Sie mit dem Upgrade beginnen, ist es wichtig, die folgenden Wartungsaufgaben durchzuführen, damit das System bereit ist und zurückgesetzt werden kann, falls Probleme auftreten:

* [Indexdefinitionen](#index-definitions)
* [Überprüfung auf ausreichenden Festplattenspeicher](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#ensure-sufficient-disk-space)
* [Vollständige Sicherung von AEM](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#fully-back-up-aem)
* [Erstellen der quickstart.properties-Datei](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#generate-quickstart-properties)
* [Konfigurieren von Workflow- und Auditprotokoll-Löschung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#configure-wf-audit-purging)
* [Installieren, Konfigurieren und Ausführen der Aufgaben vor dem Upgrade](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#install-configure-run-pre-upgrade-tasks)
* [Entfernen von Updates aus dem /install-Verzeichnis](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#remove-updates-install-directory)
* [Beenden aller Cold-Standby-Instanzen](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#stop-tarmk-coldstandby-instance)
* [Deaktivieren von benutzerdefinierten geplanten Aufträgen](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-scheduled-jobs)
* [Durchführen der Offline-Revisionsbereinigung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-offline-revision-cleanup)
* [Durchführen der Datenspeicherbereinigung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-datastore-garbage-collection)
* [Upgrade des Datenbankschemas bei Bedarf](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#upgradethedatabaseschemaifneeded)
* [Rotieren von Protokolldateien](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#rotate-log-files)

## Indexdefinitionen {#index-definitions}

Vergewissern Sie sich, dass Sie die erforderlichen Indexdefinitionen installiert haben, die mit dem neuesten AEM 6.5 Service Pack veröffentlicht wurden. (Weitere Informationen finden Sie unter [Versionshinweise ](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/release-notes/release-notes) AEM 6.5 Service Pack .)

## Überprüfung auf ausreichenden Festplattenspeicher {#ensure-sufficient-disk-space}

Stellen Sie beim Ausführen des Upgrades sicher, dass ausreichend Speicherplatz vorhanden ist.

## Vollständige Sicherung von AEM {#fully-back-up-aem}

Bevor Sie mit dem Upgrade beginnen, sollten Sie eine vollständige Sicherungskopie von AEM erstellen. Stellen Sie sicher, dass Sie Ihr Repository, Ihre Anwendungsinstallation, Ihren Datenspeicher und gegebenenfalls Ihre Mongo-Instanzen sichern. Weitere Informationen zum Sichern und Wiederherstellen einer AEM-Instanz finden Sie unter [Sicherung und Wiederherstellung](/help/sites-administering/backup-and-restore.md).

## Erzeugen der Datei quickstart.properties {#generate-quickstart-properties}

Beim Starten von AEM aus der .jar-Datei wird eine Datei `quickstart.properties` unter `crx-quickstart/conf` erzeugt. Falls AEM bisher nur mit dem Startskript gestartet wurde, ist diese Datei nicht vorhanden und das Upgrade schlägt fehl. Überprüfen Sie, ob diese Datei vorhanden ist, und starten Sie AEM aus der jar-Datei neu, falls sie nicht vorhanden ist.

## Konfigurieren von Workflow- und Auditprotokoll-Löschung {#configure-wf-audit-purging}

Für die Aufgaben `WorkflowPurgeTask` und `com.day.cq.audit.impl.AuditLogMaintenanceTask` sind separate OSGi-Konfigurationen erforderlich, ohne die sie nicht ausgeführt werden können. Falls diese Aufgaben beim Ausführen von Aufgaben vor dem Upgrade fehlschlagen, sind die Ursache dafür wahrscheinlich fehlende Konfigurationen. Daher müssen Sie die OSGi-Konfigurationen für diese Aufgaben hinzufügen oder diese Aufgaben vollständig aus der Liste der Optimierungsaufgaben vor dem Upgrade löschen, falls Sie diese nicht ausführen möchten. Die Dokumentation zum Konfigurieren von Workflow-Bereinigungsaufgaben finden Sie unter [Verwalten von Workflow-Instanzen](/help/sites-administering/workflows-administering.md). Die Konfiguration der Wartungsaufgaben im Auditprotokoll finden Sie unter [Auditprotokollwartung in AEM 6](/help/sites-administering/operations-audit-log.md).


## Installieren, Konfigurieren und Ausführen der Aufgaben vor dem Upgrade {#install-configure-run-pre-upgrade-tasks}

Wartungsaufgaben vor einem Upgrade, die bisher manuell durchgeführt werden mussten, wurden optimiert und automatisiert. Die Wartungsoptimierung vor einem Upgrade ermöglicht eine einheitliche Trigger dieser Tasks und die Überprüfung der Ergebnisse nach Bedarf.

### Verwendung {#how-to-use-it}

Die OSGi-Komponente `PreUpgradeTasksMBean` ist mit einer Liste von Wartungsaufgaben vor dem Upgrade vorkonfiguriert, die gleichzeitig ausgeführt werden können. Sie können die Aufgaben mit den nachfolgenden Schritten konfigurieren:

1. Navigieren Sie zur Web-Konsole unter *https://Server-Adresse:Serverport/system/console/configMgr*.

1. Suchen Sie nach „**preupgradetasks**“ und klicken Sie auf die erste übereinstimmende Komponente. Der vollständige Name der Komponenten lautet `com.adobe.aem.upgrade.prechecks.mbean.impl.PreUpgradeTasksMBeanImpl`.

1. Ändern Sie die Liste der auszuführenden Wartungsaufgaben, wie unten dargestellt:

   ![1487758925984](assets/1487758925984.png)

Nachfolgend finden Sie eine Beschreibung des Ausführungsmodus, für den jede Wartungsaufgabe entwickelt wurde.

| Aufgabe | Anmerkungen |
|---|---|
| WorkflowPurgeTask | Vor der Ausführung muss die Adobe Granite Workflow-Bereinigungskonfigurations-OSGi konfiguriert werden. |
| GenerateBundlesListFileTask |   |
| RevisionCleanupTask |   |
| com.day.cq.audit.impl.AuditLogMaintenanceTask | Vor der Ausführung muss die OSGi-Konfiguration für den Auditprotokolllöschungs-Planer konfiguriert werden. |

### Standardkonfiguration der Konsistenzprüfungen vor einem Upgrade {#default-configuration-of-the-pre-upgrade-health-checks}

Die OSGi-Komponente `PreUpgradeTasksMBeanImpl` umfasst eine vorkonfigurierte Liste von Tags für Konsistenzprüfungen vor einem Upgrade, die ausgeführt werden sollen, wenn die Methode `runAllPreUpgradeHealthChecks` aufgerufen wird:

* **system** – das Tag, das von den Wartungs-Konsistenzprüfungen für Granite verwendet wird

* **pre-upgrade** – Ein benutzerdefiniertes Tag, das Sie allen Konsistenzprüfungen hinzufügen können, die vor einem Upgrade durchgeführt werden sollen

**MBean-Methoden**

Auf die Funktion für verwaltete Beans kann über die [JMX-Konsole](/help/sites-administering/jmx-console.md) zugegriffen werden.

Sie können wie folgt auf die MBeans zugreifen:

1. Wechseln Sie zur JMX-Konsole unter *https://Server-Adresse:Serverport/system/console/jmx*.
1. Suchen Sie nach **PreUpgradeTasks** und klicken Sie auf das Ergebnis.

1. Wählen Sie im Bereich **Operations** eine Methode und im daraufhin angezeigten Fenster **Invoke** aus.

Nachfolgend finden Sie eine Liste aller verfügbaren Methoden, die von `PreUpgradeTasksMBeanImpl` bereitgestellt werden:

| Name der Methode | Typ | Beschreibung |
|---|---|---|
| runAllPreUpgradeTasks() | ACTION | Führt alle in der Liste genannten Wartungsaufgaben vor dem Upgrade aus. |
| runPreUpgradeTask(preUpgradeTaskName) | ACTION | Führt die Wartungsaufgabe vor dem Upgrade mit dem als Parameter angegebenen Namen aus. |
| getPreUpgradeTaskLastRunTime(preUpgradeTaskName) | ACTION | Gibt die genaue Ausführungszeit der Wartungsaufgaben vor dem Upgrade mit dem Namen als Parameter an. |
| getPreUpgradeTaskLastRunState(preUpgradeTaskName) | ACTION | Gibt den letzten Ausführungsstatus der Wartungsaufgabe vor dem Upgrade mit dem Namen als Parameter an. |
| runAllPreUpgradeHealthChecks(shutdownOnSuccess) | ACTION | Führt alle Konsistenzprüfungen vor einem Upgrade aus und speichert deren Status in der Datei preUpgradeHCStatus.properties im Sling-Stammpfad. Wenn ShutdownOnSuccess auf „true“ gesetzt ist, wird die AEM-Instanz heruntergefahren, allerdings nur, wenn der Status für alle Konsistenzprüfungen vor einem Upgrade „OK“ lautet. Die Eigenschaftendatei wird als Vorbedingung für zukünftige Upgrades verwendet, und der Upgrade-Vorgang wird angehalten, wenn die Konsistenzprüfungen vor einem Upgrade fehlgeschlagen sind. Wenn Sie das Ergebnis der Konsistenzprüfungen vor einem Upgrade ignorieren und das Upgrade trotzdem starten möchten, können Sie die Datei löschen. |
| detectUsageOfUnavailableAPI(aemVersion) | ACTION | Listet alle importierten Pakete auf, die nach dem Upgrade auf die angegebene AEM-Version nicht mehr kompatibel sind. Die AEM-Zielversion muss als Parameter angegeben werden. |

>[!NOTE]
>
>Die MBean-Methoden können wie folgt aufgerufen werden:
>
>* Durch die JMX-Konsole
>* Durch jede externe Anwendung, die eine Verbindung zu JMX herstellt
>* cURL
>

## Entfernen von Updates aus dem /install-Verzeichnis {#remove-updates-install-directory}

>[!NOTE]
>
>Entfernen Sie nur Pakete aus dem Verzeichnis „crx-quickstart/install“, NACHDEM Sie die AEM-Instanz heruntergefahren haben. Dies ist einer der letzten Schritte vor dem Start der ersetzenden Aktualisierung.

Entfernen Sie alle Service Packs, Feature Packs oder Hotfixes, die im lokalen Dateisystem im Verzeichnis `crx-quickstart/install` bereitgestellt wurden. Dadurch wird verhindert, dass nach Abschluss der Aktualisierung versehentlich alte Hotfixes und Service Packs zusätzlich zur neuen AEM-Version installiert werden.

## Beenden aller Cold-Standby-Instanzen {#stop-tarmk-coldstandby-instance}

Wenn Sie TarMK-Cold-Standby verwenden, beenden Sie alle Cold-Standby-Instanzen. Dies garantiert eine effiziente Möglichkeit, bei Problemen im Upgrade wieder online zu gehen. Nach erfolgreichem Upgrade müssen die Cold-Standby-Instanzen auf Basis der aktualisierten primären Instanzen neu erstellt werden.

## Deaktivieren von benutzerdefinierten geplanten Aufträgen {#disable-custom-scheduled-jobs}

Deaktivieren Sie alle geplanten OSGi-Aufträge, die im Anwendungs-Code enthalten sind.

## Durchführen der Offline-Revisionsbereinigung {#execute-offline-revision-cleanup}

>[!NOTE]
>
>Dieser Schritt ist nur für TarMK-Installationen erforderlich.

Falls Sie TarMK verwenden, sollten Sie vor dem Upgrade eine Offline-Revisionsbereinigung durchführen. Dadurch werden die Repository-Migration und die nachfolgenden Upgrade-Aufgaben wesentlich schneller ausgeführt. Dies wiederum unterstützt die erfolgreiche Online-Revisionsbereinigung nach dem Upgrade. Informationen zum Ausführen der Offline-Revisionsbereinigung finden Sie unter [Durchführen der Offline-Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md#revision-cleanuprevision-cleanup).

## Durchführen der Datenspeicherbereinigung {#execute-datastore-garbage-collection}

Nachdem Sie die Revisionsbereinigung auf crx3-Instanzen ausgeführt haben, sollten Sie die Datenspeicherbereinigung ausführen, um alle nicht referenzierten Blobs im Datenspeicher zu entfernen. Anweisungen finden Sie in der Dokumentation zur [Datenspeicherbereinigung](/help/sites-administering/data-store-garbage-collection.md).

## Rotieren von Protokolldateien {#rotate-log-files}

Bevor Sie mit dem Upgrade beginnen, empfiehlt Adobe, die aktuellen Protokolldateien zu archivieren. Dadurch können Sie Protokolldateien vor und nach dem Upgrade einfacher überwachen und scannen, um auftretende Probleme zu identifizieren.
