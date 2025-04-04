---
title: Fehlerbehebung bei Replikationsproblemen
description: Dieser Artikel stellt Informationen zur Fehlerbehebung bei Replikationsproblemen bereit.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
docset: aem65
feature: Configuring
solution: Experience Manager, Experience Manager Sites
role: Admin
hide: true
hidefromtoc: true
exl-id: 015def31-c7de-42b3-8218-1284afcb6921
source-git-commit: f145e5f0d70662aa2cbe6c8c09795ba112e896ea
workflow-type: tm+mt
source-wordcount: '1224'
ht-degree: 100%

---

# Fehlerbehebung bei Replikationsproblemen{#troubleshooting-replication}

Diese Seite stellt Informationen zur Fehlerbehebung bei Replikationsproblemen bereit.

## Problem {#problem}

Die Replikation (nicht die Rückwärtsreplikation) schlägt aus irgendeinem Grund fehl.

## Auflösung {#resolution}

Es gibt verschiedene Gründe, warum eine Replikation fehlschlägt. Dieser Artikel beschreibt die mögliche Vorgehensweise beim Analysieren der Probleme.

**Werden beim Klicken auf die Schaltfläche „Aktivieren“ irgendwelche Replikationen ausgelöst? Falls NICHT, gehen Sie wie folgt vor:**

1. Wechseln Sie zu /crx/explorer und melden Sie sich als Admin an.
1. Öffnen Sie „Content Explorer“
1. Überprüfen Sie, ob der Knoten „/bin/replicate“ oder „/bin/replicate.json“ vorhanden ist. Falls er vorhanden ist, löschen Sie den Knoten und speichern Sie die Änderung.

**Werden die Replikationen in den Warteschlangen der Replikationsagenten gespeichert?**

Wechseln Sie zu /etc/replication/agents.author.html und klicken Sie dann auf die Replikationsagenten, um dies zu überprüfen.

**Wenn eine oder einige Agentenwarteschlangen hängen geblieben sind:**

1. Lautet der Status der Warteschlange **gesperrt**? Wenn dies der Fall ist, wird die Veröffentlichungsinstanz nicht ausgeführt oder reagiert sie nicht? Überprüfen Sie die Veröffentlichungsinstanz, um zu sehen, wo der Fehler liegt.  Überprüfen Sie also die Protokolle, ob ein OutOfMemory-Fehler oder ein anderes Problem vorliegt. Wenn die Instanz nur langsam ist, analysieren Sie die Thread-Sicherungskopien.
1. Lautet der Status der Warteschlange **Warteschlange ist aktiv – x ausstehend**? Möglicherweise wurde der Replikationsauftrag durch einen SocketRead-Vorgang unterbrochen und wartet auf eine Reaktion der Veröffentlichungsinstanz oder des Dispatchers. Das bedeutet, dass u. U. eine hohe Last auf der Veröffentlichungsinstanz oder dem Dispatcher vorliegt oder dass diese durch eine Sperre unterbrochen wurden. Überprüfen Sie in diesem Fall die Thread-Sicherungskopien der Autoren- und Veröffentlichungsinstanzen.

   * Öffnen Sie die Thread-Sicherungskopien der Autoreninstanz in einem Analyzer für Thread-Sicherungskopien und prüfen Sie, ob der Sling-Eventing-Auftrag des Replikationsagenten durch einen SocketRead-Vorgang unterbrochen wurde.
   * Öffnen Sie die Thread-Sicherungskopien der Veröffentlichungsinstanz in einem Analyzer für Thread-Sicherungskopien und analysieren Sie, aus welchen Grund die Veröffentlichungsinstanz möglicherweise nicht reagiert. Dabei sollte ein Thread mit „POST /bin/receive“ im Namen angezeigt werden. Dies ist der Thread, der die Replikation von der Autoreninstanz empfängt.

**Wenn alle Agentenwarteschlangen hängen geblieben sind:**

1. Möglicherweise kann ein bestimmter Teil des Inhalts aufgrund eines beschädigten Repositorys oder eines anderen Problems nicht unter /var/replication/data serialisiert werden. Überprüfen Sie die Datei „logs/error.log“ auf einen entsprechenden Fehler. Gehen Sie wie folgt vor, um das fehlerhafte Replikationselement zu entfernen:

   1. Wechseln Sie zu https://&lt;Host>:&lt;Port>/crx/de und melden Sie sich als Admin an.
   1. Klicken Sie im oberen Menü auf „Tools“.
   1. Klicken Sie auf die Lupenschaltfläche.
   1. Wählen Sie „XPath“ als Typ aus.
   1. Geben Sie die folgende Abfrage in das Feld „Abfrage“ ein: /jcr:root/var/eventing/jobs//element(&#42;,slingevent:Job) order by @slingevent:created
   1. Klicken Sie auf „Suchen“. 
   1. Die in den Ergebnissen ganz oben angezeigten Elemente sind die aktuellen Sling-Eventing-Aufträge. Klicken Sie auf die einzelnen Aufträge, um nach den unterbrochenen Replikationen zu suchen, die mit dem oben in der Warteschlange Angezeigten übereinstimmen.

1. Möglicherweise liegt ein Problem mit den Auftragswarteschlangen des Sling-Eventing-Frameworks vor. Versuchen Sie, das Bundle „org.apache.sling.event“ in „/system/console“ neu zu starten.
1. Möglicherweise ist die Auftragsverarbeitung deaktiviert. Dies kann in der Felix-Konsole auf der Registerkarte „Sling Eventing“ überprüft werden. Prüfen Sie, ob Folgendes angezeigt wird: „Apache Sling Eventing (JOB PROCESSING IS DISABLED!“)

   * Ist dies der Fall, überprüfen Sie auf der Registerkarte „Configuration“ der Felix-Konsole den Apache Sling Job Event Handler. Möglicherweise ist das Kontrollkästchen für „Job Processing Enabled“ deaktiviert. Falls es aktiviert ist und weiter „Job Processing Disabled“ angezeigt wird, überprüfen Sie, ob unter „/apps/system/config“ eine Überlagerung vorhanden ist, die die Auftragsverarbeitung deaktiviert. Versuchen Sie, einen „osgi:config“-Knoten für „jobmanager.enabled“ zu erstellen, dessen boolescher Wert auf „true“ gesetzt ist, und vergewissern Sie sich erneut, ob die Aktivierung gestartet wurde und keine Aufträge mehr in der Warteschlange vorhanden sind.

1. Möglicherweise ist auch der Status der Konfiguration „DefaultJobManager“ inkonsistent. Dies kann vorkommen, wenn die Konfiguration „Apache Sling Job Event Handler“ über die OSGi-Konsole manuell geändert wird (z. B. durch Deaktivieren und erneutes Aktivieren der Eigenschaft „Job Processing Enabled“ (Auftragsverarbeitung aktiviert) und Speichern der Konfiguration).

   * Dies führt dazu, dass der Status der unter „crx-quickstart/launchpad/config/org/apache/sling/event/impl/jobs/DefaultJobManager.config“ gespeicherten Konfiguration für „DefaultJobManager“ inkonsistent wird. Obwohl die Eigenschaft „Apache Sling Job Event Handler“ anzeigt, dass „Job Processing Enabled“ (Jobverarbeitung aktiviert) aktiviert ist, wird auf der Registerkarte „Sling Eventing“ die Meldung „JOB PROCESSING IS DISABLED“ (Auftragsverarbeitung ist deaktiviert) angezeigt und die Replikation funktioniert nicht.
   * Navigieren Sie zur Konfigurationsseite der OSGi-Konsole und löschen Sie die Konfiguration „Apache Sling Job Event Handler“, um dieses Problem zu beheben. Starten Sie dann den Primärknoten des Clusters neu, um den Status der Konfiguration wieder konsistent zu machen. Damit sollte das Problem behoben sein und die Replikation sollte wieder funktionieren.

**Erstellen einer „replication.log“-Datei**

In manchen Fällen ist es hilfreich, wenn die gesamte Replikationsprotokollierung auf DEBUG-Ebene in separaten Protokolldateien erfolgen soll. Gehen Sie hierfür wie folgt vor:

1. Wechseln Sie zu https://host:port/system/console/configMgr und melden Sie sich als Admin an.
1. Suchen Sie nach der Apache Sling Logging Logger-Factory-Konfiguration und erstellen Sie eine Instanz, indem Sie auf die **+**-Schaltfläche rechts neben der Factory-Konfiguration klicken. Dadurch wird eine neue Logging Logger-Konfiguration erstellt.
1. Richten Sie die Konfiguration wie folgt ein:

   * Protokollierungsebene: DEBUG
   * Pfad der Protokolldatei: logs/replication.log
   * Kategorien: com.day.cq.replication

1. Wenn Sie annehmen, dass das Problem in irgendeiner Weise mit „sling eventing/jobs“ verknüpft ist, können Sie auch dieses Java™-Paket unter „categories:org.apache.sling.event“ hinzufügen.

## Anhalten der Warteschlange des Replikationsagenten  {#pausing-replication-agent-queue}

In manchen Fällen ist es u. U. nützlich, die Replikations-Warteschlange anzuhalten, um die Last auf dem Autorensystem zu reduzieren, ohne dieses zu deaktivieren. Dies ist derzeit nur durch das vorübergehende Konfigurieren eines ungültigen Ports möglich. Ab Version 5.4 steht eine Schaltfläche zum Anhalten der Warteschlange des Replikationsagenten zur Verfügung, jedoch mit einigen Einschränkungen.

1. Der Status wird nicht persistiert, d. h., wenn Sie einen Server neu starten oder ein Replikations-Bundle wiederverwenden, kehrt die Warteschlange wieder in den Ausführungsstatus zurück.
1. Beim Anhalten für kurze Zeiträume tritt ein Leerlauf ein (OOB nach einer Stunde ohne Aktivitäten mit Replikation durch andere Threads), nicht jedoch für längere Zeiträume. Dies liegt an einer Funktion von Apache Sling, die Threads im Leerlauf verhindert. Überprüfen Sie also, ob ein Auftragswarteschlangen-Thread länger nicht verwendet wurde. Ist dies der Fall, werden Bereinigungszyklen gestartet. Durch den Bereinigungszyklus wird der Thread gestoppt und die Einstellung zum Anhalten wird nicht beibehalten. Da Aufträge persistiert werden, wird ein neuer Thread zum Verarbeiten der Warteschlange initiiert, der keine Details über die angehaltene Konfiguration umfasst. Aus diesem Grund wird die Warteschlange in den Ausführungsstatus versetzt.

## Seitenberechtigungen werden bei der Benutzeraktivierung nicht repliziert {#page-permissions-are-not-replicated-on-user-activation}

Seitenberechtigungen werden nicht repliziert, da sie für die Knoten gespeichert werden, auf die Zugriff erteilt wird, und nicht für die Benutzer.

Im Allgemeinen sollten Seitenberechtigungen nicht von der Autoreninstanz in die Veröffentlichungsinstanz repliziert werden und dies ist standardmäßig auch nicht der Fall. Der Grund hierfür ist, dass die Zugriffsrechte in diesen beiden Umgebungen unterschiedlich sein sollten. Daher empfiehlt Adobe, dass Sie ACLs in der Veröffentlichungsinstanz separat von der Autoreninstanz konfigurieren.

## Replikationswarteschlange wird bei der Replikation von Namespace-Informationen von der Autoren- in die Veröffentlichungsinstanz blockiert {#replication-queue-blocked-when-replicating-namespace-information-from-author-to-publish}

Manchmal wird die Replikationswarteschlange beim Versuch blockiert, Namespace-Informationen von der Autoreninstanz in die Veröffentlichungsinstanz zu replizieren. Dies geschieht, weil der Replikationsbenutzer nicht die Berechtigung `jcr:namespaceManagement` hat. Um dieses Problem zu vermeiden, stellen Sie Folgendes sicher:

* Der Replikationsbenutzer (wie auf der Registerkarte [Transport](/help/sites-deploying/replication.md#replication-agents-configuration-parameters) unter „Benutzer“ konfiguriert) existiert auch auf der Veröffentlichungsinstanz.
* Der Benutzer hat Lese- und Schreibrechte für den Pfad, in dem der Inhalt installiert ist.
* Der Benutzer hat die Berechtigung `jcr:namespaceManagement` auf Repository-Ebene. Sie können die Berechtigungen wie folgt erteilen:

1. Melden Sie sich als Admin bei CRX/DE (`https://localhost:4502/crx/de/index.jsp`) an.
1. Klicken Sie auf die Registerkarte **Zugriffssteuerung**.
1. Wählen Sie **Repository** aus.
1. Klicken Sie auf **Eintrag hinzufügen** (das Plussymbol).
1. Geben Sie den Namen der Benutzerin bzw. des Benutzers ein.
1. Wählen Sie in der Liste der Berechtigungen `jcr:namespaceManagement` aus.
1. Klicken Sie auf **OK**.
