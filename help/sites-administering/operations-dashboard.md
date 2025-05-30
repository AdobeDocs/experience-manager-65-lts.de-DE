---
title: Vorgangs-Dashboard
description: Erfahren Sie, wie Sie das Vorgangs-Dashboard in Adobe Experience Manager verwenden.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
feature: Operations
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: fcabfd44-31c2-4884-8dbd-99aa74972cfa
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '5743'
ht-degree: 100%

---

# Vorgangs-Dashboard {#operations-dashboard}

## Einführung {#introduction}

Das Vorgangs-Dashboard in AEM 6 hilft Systembetreiberinnen und -betreibern, den AEM-Systemzustand auf einen Blick zu überwachen. Außerdem bietet das Dashboard automatisch erstellte Diagnosedaten zu relevanten Aspekten von AEM und ermöglicht die Konfiguration und Ausführung einer eigenständigen Wartungsautomatisierung, um Projektvorgänge und Support-Fälle deutlich zu reduzieren. Das Vorgangs-Dashboard kann mit benutzerdefinierten Konsistenzprüfungen und Wartungsaufgaben erweitert werden. Darüber hinaus ist der Zugriff auf die Daten des Vorgangs-Dashboards durch externe Überwachungs-Tools über JMX möglich.

**Das Vorgangs-Dashboard:**

* ist ein Systemstatus mit einem Klick, der Betriebsabteilungen effizienter macht
* stellt einen zentralen Überblick über die Systemkonsistenz bereit
* verringert den Zeitaufwand für das Erkennen, Analysieren und Beheben von Fehlern
* bietet eine eigenständige Wartungsautomatisierung, mit der die Kosten für den Projektbetrieb erheblich gesenkt werden können

Sie können auf dem AEM-Begrüßungsbildschirm über **Tools** > **Vorgänge** auf das Dashboard zugreifen.

>[!NOTE]
>
>Um auf das Vorgangs-Dashboard zugreifen zu können, muss die angemeldete Benutzerin oder der Benutzer zur Benutzergruppe „Operatoren“ gehören. Weitere Informationen finden Sie in der Dokumentation zu [Verwaltung von Benutzern, Gruppen und Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md).

## Konsistenzberichte {#health-reports}

Das Konsistenzberichtssystem stellt Informationen zum Zustand einer AEM-Instanz durch Sling-Konsistenzprüfungen bereit. Sie können diesen Vorgang entweder über OSGi, JMX, HTTP-Anfragen (über JSON) oder über die Touch-Benutzeroberfläche durchführen. Es bietet Messungen und Schwellenwerte für bestimmte konfigurierbare Zähler und liefert manchmal Informationen zur Lösung des Problems.

Es umfasst mehrere Funktionen, die unten beschrieben werden.

## Konsistenzprüfungen {#health-checks}

Die **Konsistenzberichte** sind ein System von Karten, die einen guten oder schlechten Status in einem bestimmten Produktbereich anzeigen. Diese Karten sind Visualisierungen der Sling-Konsistenzprüfungen, die Daten aus JMX und anderen Quellen aggregieren und verarbeitete Informationen als MBeans erneut verfügbar machen. Diese MBeans können auch in der [JMX-Web-Konsole](/help/sites-administering/jmx-console.md) unter der Domain **org.apache.sling.healthcheck** inspiziert werden.

Sie können auf dem AEM-Willkommensbildschirm über das Menü **Tools** > **Vorgänge** > **Konsistenzberichte** oder über die folgende URL auf die Konsistenzberichte zugreifen:

`https://<serveraddress>:port/libs/granite/operations/content/healthreports/healthreportlist.html`

![chlimage_1-116](assets/chlimage_1-116.png)

Das Kartensystem umfasst drei mögliche Status: **OK**, **WARNUNG** und **KRITISCH**. Diese Statusanzeigen sind das Ergebnis von Regeln und Schwellenwerten. Um diese zu konfigurieren, bewegen Sie den Mauszeiger über die Karte und klicken Sie auf das Zahnradsymbol in der Aktionsleiste:

![chlimage_1-117](assets/chlimage_1-117.png)

### Arten von Konsistenzprüfungen {#health-check-types}

Es gibt zwei Arten von Konsistenzprüfungen in AEMٔ 6:

1. Individuelle Konsistenzprüfungen
1. Verbund-Konsistenzprüfungen

Eine **Individuelle Konsistenzprüfung** ist eine einzelne Konsistenzprüfung, die einer Statuskarte entspricht. Individuelle Konsistenzprüfungen können mit Regeln oder Schwellenwerten konfiguriert werden und können einen oder mehrere Hinweise und Links zur Lösung identifizierter Statusprobleme bereitstellen. Nehmen wir als Beispiel die Prüfung „Fehler protokollieren“: Wenn die Instanzprotokolle FEHLER-Einträge enthalten, finden Sie diese auf der Detailseite der Konsistenzprüfung. Oben auf der Seite sehen Sie einen Link zum Analyzer „Protokollmeldung“ im Abschnitt „Diagnose-Tools“, mit dem Sie diese Fehler detaillierter analysieren und die Logger neu konfigurieren können.

Eine **Verbund-Konsistenzprüfung** ist eine Prüfung, die Informationen aus mehreren individuellen Prüfungen aggregiert.

Verbund-Konsistenzprüfungen werden mithilfe von **Filter-Tags** konfiguriert. Im Wesentlichen werden alle einzelnen Prüfungen mit demselben Filter-Tag als Verbund-Konsistenzprüfung gruppiert. Eine Verbund-Konsistenzprüfung weist nur dann den Status „OK“ auf, wenn alle individuellen Prüfungen, die sie umfasst, ebenfalls diesen Status aufweisen.

### Erstellen von Konsistenzprüfungen {#how-to-create-health-checks}

Im Vorgangs-Dashboard können Sie die Ergebnisse von individuellen sowie von Verbund-Konsistenzprüfungen visuell darstellen.

### Erstellen einer individuellen Konsistenzprüfung {#creating-an-individual-health-check}

Die Erstellung einer individuellen Konsistenzprüfung umfasst zwei Schritte: Implementieren einer Sling-Konsistenzprüfung und Hinzufügen eines Eintrags für die Konsistenzprüfung in den Konfigurationsknoten des Dashboards.

1. Um eine Sling-Konsistenzprüfung zu erstellen, erstellen Sie eine OSGi-Komponente, die die Sling HealthCheck-Schnittstelle implementiert. Fügen Sie diese Komponente in einem Bundle hinzu. Die Eigenschaften der Komponente identifizieren die Konsistenzprüfung vollständig. Nachdem die Komponente installiert wurde, wird automatisch ein JMX-MBean für die Konsistenzprüfung erstellt. In der [Dokumentation zur Sling-Konsistenzprüfung](https://sling.apache.org/documentation/bundles/sling-health-check-tool.html) finden Sie weitere Informationen.

   Beispiels einer Sling-Konsistenzprüfungs-Komponente, mit OSGi-Dienstkomponenten-Anmerkungen geschrieben:

   ```java
   @Component(service = HealthCheck.class,
   property = {
       HealthCheck.NAME + "=Example Check",
       HealthCheck.TAGS + "=example",
       HealthCheck.TAGS + "=test",
       HealthCheck.MBEAN_NAME + "=exampleHealthCheckMBean"
   })
    public class ExampleHealthCheck implements HealthCheck {
       @Override
       public Result execute() {
           // health check code
       }
    }
   ```

   >[!NOTE]
   >
   >Die Eigenschaft `MBEAN_NAME` definiert den Namen des MBean, die für diese Konsistenzprüfung erstellt wird.

1. Nach dem Erstellen der Konsistenzprüfung müssen Sie einen neuen Konfigurationsknoten erstellen, damit die Konsistenzprüfung in der Oberfläche des Vorgangs-Dashboards verfügbar ist. Für diesen Schritt müssen Sie den JMX-MBean-Namen der Konsistenzprüfung kennen (die Eigenschaft `MBEAN_NAME`). Um eine Konfiguration für die Konsistenzprüfung zu erstellen, öffnen Sie CRXDE und fügen Sie einen Knoten (des Typs **nt:unstructured**) unter dem folgenden Pfad hinzu: `/apps/settings/granite/operations/hc`

   Legen Sie die folgenden Eigenschaften für den neuen Knoten fest:

   * **Name:** `sling:resourceType`

      * **Typ:** `String`
      * **Wert:** `granite/operations/components/mbean`

   * **Name:** `resource`

      * **Typ:** `String`
      * **Wert:** `/system/sling/monitoring/mbeans/org/apache/sling/healthcheck/HealthCheck/exampleHealthCheck`

   >[!NOTE]
   >
   >Der o. g. Ressourcenpfad wird wie folgt erstellt: Wenn der MBean-Name der Konsistenzprüfung „test“ ist, fügen Sie am Ende des Pfads `/system/sling/monitoring/mbeans/org/apache/sling/healthcheck/HealthCheck` „test“ hinzu.
   >
   >Der endgültige Pfad lautet also:
   >
   >`/system/sling/monitoring/mbeans/org/apache/sling/healthcheck/HealthCheck/test`

   >[!NOTE]
   >
   >Stellen Sie sicher, dass beim Pfad `/apps/settings/granite/operations/hc` für die folgenden Eigenschaften „true“ festgelegt ist:
   >
   >
   >`sling:configCollectionInherit`
   >
   >`sling:configPropertyInherit`
   >
   >
   >Dadurch weiß der Konfigurations-Manager, dass die neuen Konfigurationen mit den vorhandenen aus `/libs` zusammengeführt werden sollen.

### Erstellen einer Verbund-Konsistenzprüfung {#creating-a-composite-health-check}

Die Rolle einer Verbund-Konsistenzprüfung besteht darin, mehrere individuelle Konsistenzprüfungen mit einer Reihe gemeinsamer Funktionen zu aggregieren. Beispielsweise gruppiert die Sicherheits-Verbund-Konsistenzprüfung alle individuellen Konsistenzprüfungen, die sicherheitsbezogene Überprüfungen durchführen. Der erste Schritt zum Erstellen einer Verbund-Konsistenzprüfung besteht darin, eine OSGi-Konfiguration hinzuzufügen. Damit er im Vorgangs-Dashboard angezeigt wird, muss ein neuer Konfigurationsknoten auf die gleiche Weise hinzugefügt werden wie für eine einfache Prüfung.

1. Wechseln Sie zum Web-Konfigurations-Manager in der OSGi-Konsole. Greifen Sie auf `https://serveraddress:port/system/console/configMgr` zu.
1. Suchen Sie nach dem Eintrag namens **Apache Sling Verbund-Konsistenzprüfung**. Nachdem Sie ihn gefunden haben, beachten Sie, dass bereits zwei Konfigurationen verfügbar sind: eine für die Systemprüfungen und eine andere für die Sicherheitsprüfungen.
1. Erstellen Sie eine Konfiguration, indem Sie auf die Schaltfläche „+“ rechts von der Konfiguration klicken. Ein neues Fenster wird geöffnet, wie unten abgebildet:

   ![chlimage_1-23](assets/chlimage_1-23.jpeg)

1. Erstellen Sie eine Konfiguration und speichern Sie sie. Ein MBean wird mit der neuen Konfiguration erstellt.

   Der Zweck jeder Konfigurationseigenschaft ist wie folgt:

   * **Name (hc.name):** Der Name der Verbund-Konsistenzprüfung. Es wird ein aussagekräftiger Name empfohlen.
   * **Tags (hc.tags):** Die Tags für diese Konsistenzprüfung. Wenn diese Verbund-Konsistenzprüfung Teil einer anderen Verbund-Konsistenzprüfung sein soll (z. B. in einer Hierarchie der Konsistenzprüfungen), fügen Sie die Tags hinzu, mit denen dieser Verbund verknüpft ist.
   * **MBean-Name (hc.mbean.name):** Der Name des MBean, der dem JMX-MBean dieser Verbund-Konsistenzprüfung übergeben wird.
   * **Filter-Tags (filter.tags):** Die Eigenschaft, die für Verbund-Konsistenzprüfungen spezifisch ist. Diese Tags werden durch den Verbund aggregiert. Die Verbund-Konsistenzprüfung aggregiert unter ihrer Gruppe alle Konsistenzprüfungen mit Tags, die einem der Filter-Tags dieser Verbund-Konsistenzprüfung entsprechen. Eine Verbund-Konsistenzprüfung mit den Filter-Tags **test** und **check** fasst beispielsweise alle individuellen und Verbund-Konsistenzprüfungen zusammen, die eines der Tags **test** und **check** in ihrer Tags-Eigenschaft (`hc.tags`) aufweisen.

   >[!NOTE]
   >
   >Ein neues JMX-MBean wird für jede neue Konfiguration des Apache Sling Composite Health Checks erstellt.**

1. Schließlich muss der Eintrag der erstellten Verbund-Konsistenzprüfung im Konfigurationsknoten des Vorgangs-Dashboards hinzugefügt werden. Die Vorgehensweise ist dieselbe wie bei individuellen Konsistenzprüfungen: es muss ein Knoten vom Typ **nt:unstructured** unter `/apps/settings/granite/operations/hc` angelegt werden. Die Ressourceneigenschaft des Knotens wird durch den Wert von **hc.mean.name** in der OSGi-Konfiguration definiert.

   Wenn Sie beispielsweise eine Konfiguration erstellt und den Wert **hc.mbean.name** auf **diskusage** gesetzt haben, sehen die Konfigurationsknoten wie folgt aus:

   * **Name:** `Composite Health Check`

      * **Typ:** `nt:unstructured`

   Mit den folgenden Eigenschaften:

   * **Name:** `sling:resourceType`

      * **Typ:** `String`
      * **Wert:** `granite/operations/components/mbean`

   * **Name:** `resource`

      * **Typ:** `String`
      * **Wert:** `/system/sling/monitoring/mbeans/org/apache/sling/healthcheck/HealthCheck/diskusage`

   >[!NOTE]
   >
   >Wenn Sie individuelle Konsistenzprüfungen erstellen, die logisch zu einer Verbund-Konsistenzprüfung gehören, welche standardmäßig bereits im Dashboard vorhanden ist, werden diese automatisch erfasst und unter der entsprechenden Verbund-Konsistenzprüfung gruppiert. Daher ist es nicht erforderlich, einen Konfigurationsknoten für diese Prüfungen zu erstellen.
   >
   >Wenn Sie beispielsweise eine individuelle Sicherheitskonsistenzprüfung erstellen, weisen Sie ihr das Tag „**Sicherheit**“ zu, und sie wird installiert. Sie wird automatisch unter den Verbund-Sicherheitsprüfungen im Vorgangs-Dashboard angezeigt.

### Im Lieferumfang von AEM enthaltene Konsistenzprüfungen {#health-checks-provided-with-aem}

<table>
 <tbody>
  <tr>
   <td><strong>Name der Konsistenzprüfung</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Abfrageleistung</td>
   <td><p>Diese Konsistenzprüfung wurde in <strong>AEM 6.4</strong> vereinfacht und überprüft nun das kürzlich überarbeitete MBean <code>Oak QueryStats</code>, genauer gesagt das Attribut <code>SlowQueries </code>. Wenn die Statistiken langsame Abfragen enthalten, gibt die Konsistenzprüfung eine Warnung zurück. Andernfalls wird der Status „OK“ zurückgegeben.<br /> </p> <p>Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DqueriesStatus%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=queriesStatus,type=HealthCheck</a>.</p> </td>
  </tr>
  <tr>
   <td>Länge der Überwachungswarteschlange</td>
   <td><p>Diese Prüfung wird für alle Event-Listener und Hintergrundbeobachter schrittweise durchgeführt. Sie vergleicht die <code>queueSize </code> mit ihrer <code>maxQueueSize</code> und:</p>
    <ul>
     <li>gibt den Status „Kritisch“ zurück, wenn der Wert für <code>queueSize</code> den Wert für <code>maxQueueSize</code> übersteigt (d. h., wenn Ereignisse entfernt werden)</li>
     <li>gibt eine Warnung zurück, wenn der Wert für <code>queueSize</code> über dem <code>maxQueueSize * WARN_THRESHOLD</code> liegt (der Standardwert liegt bei 0,75) </li>
    </ul> <p>Die maximale Länge jeder Warteschlange stammt aus separaten Konfigurationen (Oak und AEM) und kann von dieser Konsistenzprüfung nicht konfiguriert werden. Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DObservationQueueLengthHealthCheck%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=ObservationQueueLengthHealthCheck,type=HealthCheck</a>.</p> </td>
  </tr>
  <tr>
   <td>Abfrage-Ausnahmelimits</td>
   <td><p>Diese Prüfung überprüft das MBean <code>QueryEngineSettings</code>, genauer gesagt, die Attribute <code>LimitInMemory</code> und <code>LimitReads</code>, und gibt den folgenden Status zurück:</p>
    <ul>
     <li>den Status „Warnung“, wenn eines der Limits dem folgenden Wert entspricht oder größer ist <code>Integer.MAX_VALUE</code></li>
     <li>den Status „Warnung“, wenn eines der Limits kleiner als 10.000 (die empfohlene Einstellung von Oak) ist</li>
     <li>den Status „Kritisch“, wenn die <code>QueryEngineSettings</code> oder eines der Limits nicht abgerufen werden können</li>
    </ul> <p>Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DqueryTraversalLimitsBundle%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=queryTraversalLimitsBundle,type=HealthCheck</a>.</p> </td>
  </tr>
  <tr>
   <td>Synchronisierte Uhren</td>
   <td><p>Diese Prüfung ist nur für <a href="https://github.com/apache/sling-old-svn-mirror/blob/4df9ab2d6592422889c71fa13afd453a10a5a626/bundles/extensions/discovery/oak/src/main/java/org/apache/sling/discovery/oak/SynchronizedClocksHealthCheck.java">Dokumenten-NodeStore-Cluster</a> relevant. Es wird der folgende Status zurückgegeben:</p>
    <ul>
     <li>gibt den Status „Warnung“ zurück, wenn die Instanzuhren nicht mehr synchronisiert sind und ihr Unterschied einen vordefinierten niedrigen Schwellenwert überschreitet</li>
     <li>gibt den Status „Kritisch“ zurück, wenn die Instanzuhren nicht mehr synchronisiert sind und ihr Unterschied einen vordefinierten hohen Schwellenwert überschreitet</li>
    </ul> <p>Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DslingDiscoveryOakSynchronizedClocks%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=slingDiscoveryOakSynchronizedClocks,type=HealthCheck</a>.</p> </td>
  </tr>
  <tr>
   <td>Asynchrone Indizes</td>
   <td><p>Die Prüfung auf asynchrone Indizes:</p>
    <ul>
     <li>gibt den Status „Kritisch“ zurück, wenn mindestens eine Indizierungsspur fehlschlägt</li>
     <li>prüft <code>lastIndexedTime</code> für alle Indizierungsspuren und:
      <ul>
       <li>gibt den Status „Kritisch“ zurück, wenn sie mehr als 2 Stunden zurückliegt </li>
       <li>gibt den Status „Warnung“ zurück, wenn sie zwischen 2 Stunden und 45 Minuten zurückliegt </li>
       <li>gibt den Status „OK“ zurück, wenn sie weniger als 45 Minuten zurückliegt </li>
      </ul> </li>
     <li>Wenn keine dieser Bedingungen erfüllt ist, wird der Status „OK“ zurückgegeben.</li>
    </ul> <p>Die Statusschwellen „Kritisch“ und „Warnung“ sind konfigurierbar. Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DasyncIndexHealthCheck%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=asyncIndexHealthCheck,type=HealthCheck</a>.</p> <p><strong>Hinweis: </strong>Diese Konsistenzprüfung ist in AEM 6.4 und als Backport in AEM 6.3.0.1 verfügbar.</p> </td>
  </tr>
  <tr>
   <td>Große Lucene-Indizes</td>
   <td><p>Diese Prüfung nutzt die Daten des MBean <code>Lucene Index Statistics</code>, um große Indizes zu identifizieren, und:</p>
    <ul>
     <li>gibt den Status „Warnung“ zurück, wenn es einen Index mit mehr als 1 Mrd. Dokumenten gibt</li>
     <li>gibt den Status „Kritisch“ zurück, wenn es einen Index mit mehr als 1,5 Mrd. Dokumenten gibt</li>
    </ul> <p>Die Schwellenwerte sind konfigurierbar und das MBean für die Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DlargeIndexHealthCheck%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=largeIndexHealthCheck,type=HealthCheck.</a></p> <p><strong>Hinweis: </strong>Diese Konsistenzprüfung ist in AEM 6.4 und als Backport in AEM 6.3.2.0 verfügbar.</p> </td>
  </tr>
  <tr>
   <td>Systemwartung</td>
   <td><p>Die Systemwartung ist eine Verbund-Prüfung, die „OK“ zurückgibt, wenn alle Wartungsaufgaben wie konfiguriert ausgeführt werden. Bedenken Sie Folgendes:</p>
    <ul>
     <li>Zu jeder Wartungsaufgabe gehört eine entsprechende Konsistenzprüfung.</li>
     <li>Wenn eine Aufgabe nicht einem Wartungsfenster hinzugefügt wird, gibt ihre Konsistenzprüfung „Kritisch“ zurück.</li>
     <li>Die Wartungsaufgaben „Auditprotokoll“ und „Workflow-Bereinigung“ müssen konfiguriert werden oder ansonsten aus den Wartungsfenstern entfernt werden. Wenn diese Aufgaben nicht konfiguriert sind, schlagen sie beim ersten Versuch fehl, sodass die Systemwartungsprüfung den Status „Kritisch“ zurückgibt.</li>
     <li><strong>Bei AEM 6.4</strong> gibt es auch eine Prüfung für die Aufgabe <a href="/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks">Wartung von Lucene-Binärdateien</a>.</li>
     <li>Bei AEM 6.2 und niedriger gibt die Systemwartungsüberprüfung direkt nach dem Start den Status „Warnung“ zurück, da die Aufgaben nie ausgeführt werden. Ab 6.3 wird für sie „OK“ zurückgegeben, wenn das erste Wartungsfenster noch nicht erreicht wurde.</li>
    </ul> <p>Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3Dsystemchecks%2Ctype%3DHealthCheck">org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck</a>.</p> </td>
  </tr>
  <tr>
   <td>Replikations-Warteschlange</td>
   <td><p>Diese Prüfung durchläuft Replikationsagenten und untersucht deren Warteschlangen. Für das Element am Anfang der Warteschlange überprüft die Prüfung, wie oft der Agent die Replikation wiederholt versucht hat. Wenn diese Anzahl größer ist als der Wert des Parameters <code>numberOfRetriesAllowed</code>, wird eine Warnung zurückgegeben. Der Parameter <code>numberOfRetriesAllowed</code> ist konfigurierbar. </p> <p>Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DreplicationQueue%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck</a>.</p> </td>
  </tr>
  <tr>
   <td>Sling Jobs</td>
   <td>
    <div>
      Diese Prüfung überprüft die Anzahl an Aufträgen, die sich in der Warteschlange des Auftrags-Managers befinden, vergleicht sie mit dem Schwellenwert <code>maxNumQueueJobs</code> und:
    </div>
    <ul>
     <li>gibt den Status „Kritisch“ zurück, wenn sich mehr als <code>maxNumQueueJobs</code> in der Warteschlange befinden</li>
     <li>gibt den Status „Kritisch“ zurück, wenn es lang andauernde aktive Aufträge gibt, die seit mehr als einer Stunde ausgeführt werden</li>
     <li>gibt den Status „Kritisch“ zurück, wenn es Aufträge in der Warteschlange gibt und der letzte abgeschlossene Auftrag länger als 1 Stunde zurückliegt</li>
    </ul> <p>Nur der Parameter „Maximale Anzahl an Aufträgen in der Warteschlange“ kann konfiguriert werden und hat den Standardwert 1000.</p> <p>Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DslingJobs%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=slingJobs,type=HealthCheck</a>.</p> </td>
  </tr>
  <tr>
   <td>Anfrageleistung</td>
   <td><p>Diese Prüfung untersucht die <code>granite.request.metrics.timer</code> <a href="http://localhost:4502/system/console/slingmetrics" target="_blank">Sling-Metrik</a> und:</p>
    <ul>
     <li>gibt den Status „Kritisch“ zurück, wenn der 75. Perzentilwert über dem Schwellenwert für „Kritisch“ liegt (der Standardwert beträgt 500 Millisekunden)</li>
     <li>gibt eine Warnung zurück, wenn der 75. Perzentilwert über dem Schwellenwert für „Warnnung“ liegt (der Standardwert beträgt 200 Millisekunden)</li>
    </ul> <p>Das MBean für diese Konsistenzprüfung ist <em> </em><a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DrequestsStatus%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck</a>.</p> </td>
  </tr>
  <tr>
   <td>Fehlerprotokoll</td>
   <td><p>Diese Prüfung gibt den Status „Warnung“ zurück, wenn im Protokoll Fehler auftreten.</p> <p>Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DlogErrorHealthCheck%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck</a>.</p> </td>
  </tr>
  <tr>
   <td>Festplattenspeicher</td>
   <td><p>Diese Prüfung untersucht das MBean <code>FileStoreStats</code>, ruft die Größe des NodeStores und den Umfang des verfügbaren Festplatten-Speicherplatzes auf der NodeStore-Partition ab und:</p>
    <ul>
     <li>gibt eine Warnung zurück, wenn das Verhältnis zwischen verfügbarem Festplatten-Speicherplatz und Repository-Größe unter dem Schwellenwert für „Warnung“ liegt (der Standardwert ist 10)</li>
     <li>gibt den Status „Kritisch“ zurück, wenn das Verhältnis zwischen verfügbarem Festplatten-Speicherplatz und Repository-Größe unter dem Schwellenwert für „Kritisch“ liegt (der Standardwert ist 2)</li>
    </ul> <p>Beide Werte sind konfigurierbar. Die Prüfung funktioniert nur auf Instanzen mit einem Segmentspeicher.</p> <p>Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DDiskSpaceHealthCheck%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=DiskSpaceHealthCheck,type=HealthCheck</a>.</p> </td>
  </tr>
  <tr>
   <td>Scheduler-Statusprüfung</td>
   <td><p>Diese Prüfung gibt eine Warnung zurück, wenn die Instanz über Quartz-Aufträge verfügt, die länger als 60 Sekunden laufen. Der Schwellenwert für die zulässige Dauer ist konfigurierbar.</p> <p>Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DslingCommonsSchedulerHealthCheck%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=slingCommonsSchedulerHealthCheck,type=HealthCheck</a><em>.</em></p> </td>
  </tr>
  <tr>
   <td>Sicherheitsprüfungen</td>
   <td><p>Bei der Sicherheitsprüfung handelt es sich um einen Verbund, der die Ergebnisse mehrerer sicherheitsbezogener Prüfungen zusammenfasst. Diese individuellen Konsistenzprüfungen decken unterschiedliche Aspekte der Sicherheits-Checkliste ab, die auf der <a href="/help/sites-administering/security-checklist.md">Dokumentationsseite zur Sicherheits-Checkliste zu finden ist.</a> Die Prüfung ist als Feuerprobe beim Start der Instanz nützlich. </p> <p>Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3Dsecuritychecks%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=securitychecks,type=HealthCheck</a></p> </td>
  </tr>
  <tr>
   <td>Aktive Bundles</td>
   <td><p>„Aktive Bundles“ überprüft den Status aller Bundles und:</p>
    <ul>
     <li>gibt den Status „Warnung“ zurück, wenn eines der Bundles nicht aktiv ist oder (Start, mit verzögerter Aktivierung)</li>
     <li>ignoriert den Status von Bundles in der Ignorieren-Liste</li>
    </ul> <p>Der Parameter „Ignorieren-Liste“ kann konfiguriert werden.</p> <p>Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DinactiveBundles%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck</a>.</p> </td>
  </tr>
  <tr>
   <td>Code-Cache-Prüfung</td>
   <td><p>Eine Konsistenzprüfung, die mehrere JVM-Bedingungen überprüft, die einen in Java™ 7 vorhandenen Code-Cache-Fehler auslösen können:</p>
    <ul>
     <li>gibt eine Warnung zurück, wenn die Instanz auf Java™ 7 ausgeführt wird, wobei die Codecache-Bereinigung aktiviert ist</li>
     <li>gibt eine Warnung zurück, wenn die Instanz auf Java™ 7 ausgeführt wird und die Größe des reservierten Codecaches kleiner als ein Mindestschwellenwert ist (der Standardwert ist 90 MB)</li>
    </ul> <p>Der Schwellenwert <code>minimum.code.cache.size</code> ist konfigurierbar. Weitere Informationen zum Fehler finden Sie, wenn Sie unter <a href="https://bugs.java.com/bugdatabase/"> nach der Fehler-ID 8012547</a> suchen.</p> <p>Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DcodeCacheHealthCheck%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=codeCacheHealthCheck,type=HealthCheck</a>.</p> </td>
  </tr>
  <tr>
   <td>Fehler bei Ressourcen-Suchpfaden</td>
   <td><p>Prüft, ob unter dem Pfad <code>/apps/foundation/components/primary</code> Ressourcen vorhanden sind, und:</p>
    <ul>
     <li>gibt eine Warnung aus, wenn hierunter untergeordnete Knoten vorhanden sind: <code>/apps/foundation/components/primary</code></li>
    </ul> <p>Das MBean für diese Konsistenzprüfung ist <a href="http://localhost:4502/system/console/jmx/org.apache.sling.healthcheck%3Aname%3DresourceSearchPathErrorHealthCheck%2Ctype%3DHealthCheck" target="_blank">org.apache.sling.healthcheck:name=resourceSearchPathErrorHealthCheck,type=HealthCheck</a>.</p> </td>
  </tr>
 </tbody>
</table>

### Konfiguration der Konsistenzprüfung {#health-check-configuration}

Standardmäßig werden bei einer vordefinierten AEM-Instanz alle 60 Sekunden Konsistenzprüfungen ausgeführt.

Sie können den **Zeitraum** in der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) mit der **Konfiguration der Konsistenzprüfung von Anfragen** (com.adobe.granite.queries.impl.hc.QueryHealthCheckMetrics) festlegen.

## Überwachung mit externen Diensten {#monitoring-with-external-services}

Die Integration mit externen Technologien oder Anbietern ist möglich. Weitere Informationen finden Sie in der entsprechenden Dokumentation.

## Diagnose-Tools {#diagnosis-tools}

Das Vorgangs-Dashboard bietet außerdem Zugriff auf Diagnose-Tools, die Ihnen helfen, die Hauptursachen der Warnungen aus dem Konsistenzprüfungs-Dashboard zu finden und zu beheben, und die wichtige Debugging-Informationen für Systembetreiber bereitstellen.

Zu den wichtigsten Funktionen gehören:

* Ein Protokollmeldungs-Analyzer
* Zugriff auf Heap- und Thread-Dumps
* Leistungs-Analyse für Anfragen und Abfragen

Auf den Bildschirm „Diagnose-Tools“ können Sie über den AEM-Begrüßungsbildschirm über **Tools > Vorgänge > Diagnose** zugreifen. Über die folgende URL können Sie auch direkt auf die Diagnose-Tools zugreifen: `https://serveraddress:port/libs/granite/operations/content/diagnosis.html`

![chlimage_1-120](assets/chlimage_1-120.png)

### Protokollmeldungen {#log-messages}

Die Benutzeroberfläche der Protokollmeldungen zeigen standardmäßig alle Meldungen des Typs FEHLER an. Wenn Sie mehr Protokollmeldungen anzeigen möchten, konfigurieren Sie einen Logger mit der entsprechenden Protokollebene.

Die Protokollmeldungen nutzen einen speicherinternen Protokoll-Appender und hängen daher nicht mit den Protokolldateien zusammen. Eine weitere Konsequenz ist, dass sich bei Änderungen an den Protokollebenen in dieser Benutzeroberfläche die Informationen, die in den klassischen Protokolldateien aufgezeichnet werden, nicht ändern. Das Hinzufügen und Entfernen von Loggern in dieser Benutzeroberfläche wirkt sich nur auf die Speicherprotokollierung aus. Außerdem spiegelt sich das Ändern der Logger-Konfigurationen in der Zukunft des speicherinternen Loggers wider. Die Einträge, die bereits protokolliert sind und nicht mehr relevant sind, werden nicht gelöscht, aber ähnliche Einträge werden in Zukunft nicht protokolliert.

Sie können konfigurieren, was protokolliert wird, indem Sie Logger-Konfigurationen über die Zahnradschaltfläche oben links in der Benutzeroberfläche festlegen. Dort können Sie Logger-Konfigurationen hinzufügen, entfernen oder aktualisieren. Eine Logger-Konfiguration besteht aus einer **Protokollebene** (WARNUNG/INFO/DEBUG) und einem **Filternamen**. Der **Filtername** hat die Aufgabe, die Quelle der protokollierten Protokollmeldungen zu filtern. Andernfalls sollte, wenn ein Logger alle Protokollmeldungen für die angegebene Ebene erfassen soll, der Filtername „**Stamm**“ sein. Das Festlegen eines Loggers löst die Erfassung aller Meldungen mit einer Stufe aus, die höher als oder gleich der angegebenen Stufe ist.

Beispiele:

* Wenn Sie alle Meldungen des Typs **FEHLER** erfassen möchten, ist keine Konfiguration erforderlich. Alle FEHLER-Meldungen werden standardmäßig erfasst.
* Wenn alle Meldungen des Typs **FEHLER**, **WARNUNG** und **INFO** erfasst werden sollen, sollte der Logger-Name auf „**Stamm**“ und die Protokollierungsstufe auf **INFO** festgelegt werden.

* Wenn Sie alle Meldungen aus einem bestimmten Paket erfassen möchten (z. B. com.adobe.granite), sollte der Logger-Name auf „com.adobe.granite“ festgelegt werden. Darüber hinaus sollte die Protokollierungsebene auf **DEBUG** festgelegt werden (dadurch werden alle Meldungen des Typs **FEHLER**, **WARNUNG**, **INFO** und **DEBUG** erfasst), wie in der Abbildung unten dargestellt.

![chlimage_1-121](assets/chlimage_1-121.png)

>[!NOTE]
>
>Sie können keinen Logger-Namen festlegen, um nur Meldungen des Typs FEHLER über einen bestimmten Filter zu erfassen. Standardmäßig werden alle Meldungen des Typs FEHLER erfasst.

>[!NOTE]
>
>Die Benutzeroberfläche für Protokollmeldungen gibt nicht das tatsächliche Fehlerprotokoll wieder. Wenn Sie keine anderen Protokollnachrichten in der Benutzeroberfläche konfigurieren, werden nur FEHLER-Meldungen angezeigt. Informationen zum Anzeigen bestimmter Protokollmeldungen finden Sie in den Anweisungen oben.

>[!NOTE]
>
>Die Einstellungen auf der Diagnoseseite beeinflussen nicht, was in den Protokolldateien protokolliert wird, und umgekehrt. Während das Fehlerprotokoll also möglicherweise INFO-Meldungen erfasst, werden diese möglicherweise nicht in der Benutzeroberfläche für Protokollmeldungen angezeigt. Über die Benutzeroberfläche ist es auch möglich, DEBUG-Meldungen aus bestimmten Paketen zu erfassen, ohne dass dies das Fehlerprotokoll beeinflusst. Weitere Informationen zum Konfigurieren der Protokolldateien finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).

>[!NOTE]
>
>**In AEM 6.4** werden Wartungsaufgaben vorkonfiguriert in einem informationsreicheren Format auf INFO-Ebene protokolliert. Dieser Workflow ermöglicht eine bessere Übersicht über den Zustand der Wartungsaufgaben.
>
>Wenn Sie Tools von Drittanbietern (wie Splunk) zur Überwachung von und Reaktion auf Wartungsaufgaben verwenden, können Sie die folgenden Protokollanweisungen verwenden:

```
Log level: INFO
DATE+TIME [MaintanceLogger] Name=<MT_NAME>, Status=<MT_STATUS>, Time=<MT_TIME>, Error=<MT_ERROR>, Details=<MT_DETAILS>
```

### Anfrageleistung {#request-performance}

Die Anfrageleistungsseite ermöglicht die Analyse der langsamsten verarbeiteten Seitenanfragen. Nur Inhaltsanfragen werden auf dieser Seite registriert. Genauer gesagt werden die folgenden Anfragen erfasst:

1. Anfragen, die auf Ressourcen unter `/content` zugreifen
1. Anfragen, die auf Ressourcen unter `/etc/design` zugreifen
1. Anfragen mit der Erweiterung `".html"`

![chlimage_1-122](assets/chlimage_1-122.png)

Die Seite zeigt Folgendes an:

* die Zeit, zu der die Anfrage erfolgt ist
* die URL und die Methode der Anfrage
* Die Dauer in Millisekunden

Standardmäßig werden die langsamsten 20 Seitenanfragen erfasst. Diesen Wert können Sie aber im Konfigurations-Manager ändern.

### Abfrageleistung {#query-performance}

Die Abfrageleistungsseite ermöglicht die Analyse der langsamsten vom System durchgeführten Abfragen. Diese Informationen werden vom Repository in einem JMX-MBean bereitgestellt. In Jackrabbit stellt das JMX-MBean `com.adobe.granite.QueryStat` diese Daten bereit, im Oak-Repository werden sie von `org.apache.jackrabbit.oak.QueryStats.` geliefert.

Die Seite zeigt Folgendes an:

* Der Zeitpunkt der Abfrage
* Die Sprache der Abfrage
* Die Zahl, wie oft die Abfrage durchgeführt wurde
* Die Aussage der Abfrage
* Die Dauer in Millisekunden

![chlimage_1-123](assets/chlimage_1-123.png)

### Abfrage erläutern {#explain-query}

Bei jeder Abfrage versucht Oak, die beste Ausführungsmethode zu ermitteln, basierend auf den Oak-Indizes, die im Repository unter dem Knoten **oak:index** definiert sind. Je nach Abfrage kann Oak verschiedene Indizes auswählen. Der erste Schritt für die Abfrageoptimierung besteht darin, zu verstehen, wie Oak eine Abfrage ausführt.

„Abfrage erläutern“ ist ein Tool, das erklärt, wie Oak eine Abfrage ausführt. Sie können auf dem AEM-Willkommensbildschirm über **Tools – Vorgänge – Diagnose** darauf zugreifen. Klicken Sie anschließend auf **Abfrageleistung** und wechseln Sie zur Registerkarte **Abfrage erläutern**.

**Funktionen**

* Unterstützung der Abfragesprachen Xpath, JCR-SQL und JCR-SQL2
* Meldung der tatsächlichen Ausführungszeit der genannten Abfrage
* Erkennung langsamer Abfragen und Warnungen zu Abfragen, die möglicherweise langsam ausfallen könnten
* Gibt den Oak-Index an, der zum Ausführen der Abfrage verwendet wird
* Zeigt die tatsächliche Erläuterung der Oak-Abfrage-Engine an
* Stellt eine anklickbare Liste von langsamen und beliebten Abfragen zur Verfügung

Wenn Sie sich in der Benutzeroberfläche „Abfrage erläutern“ befinden, geben Sie die Abfrage ein und drücken Sie die Schaltfläche **Erläutern**:

![chlimage_1-124](assets/chlimage_1-124.png)

Der erste Eintrag im Bereich „Abfrage-Erläuterung“ ist die eigentliche Erklärung. Die Erklärung zeigt den Indextyp an, der für die Ausführung der Abfrage verwendet wurde.

Der zweite Eintrag ist der Ausführungsplan.

Wenn Sie das Kästchen **Ausführungszeit einbeziehen** ankreuzen, bevor Sie die Abfrage ausführen, wird auch die Zeit angezeigt, in der die Abfrage ausgeführt wurde. Mit der Option **Knotenanzahl einbeziehen** wird die Knotenanzahl angezeigt. Der Bericht liefert weitere Informationen, die zur Optimierung der Indizes für Ihre Anwendung oder Bereitstellung verwendet werden können.

![chlimage_1-125](assets/chlimage_1-125.png)

### Der Index-Manager {#the-index-manager}

Der Index-Manager soll die Indexverwaltung erleichtern, z. B. die Pflege von Indizes oder deren Statusanzeige.

Um auf ihn zuzugreifen, klicken Sie auf dem Begrüßungsbildschirm unter **Tools > Vorgänge > Diagnose** auf die Schaltfläche **Index-Manager**.

Darüber hinaus kann auf ihn direkt über diese URL zugegriffen werden: `https://serveraddress:port/libs/granite/operations/content/diagnosistools/indexManager.html`

![Index-Manager](assets/index_manager.png)

Die Benutzeroberfläche kann verwendet werden, um Indizes in der Tabelle zu filtern, indem die Filterkriterien in das Suchfeld in der linken oberen Ecke des Bildschirms eingegeben werden.

### Status-ZIP herunterladen {#download-status-zip}

Diese Aktion löst den Download einer ZIP-Datei aus, die nützliche Informationen zum Systemstatus und zur Systemkonfiguration enthält. Das Archiv enthält Instanzkonfigurationen, eine Liste von Bundles, OSGi, Sling-Metriken und Statistiken, was zu einer großen Datei führen kann. Um die Auswirkung großer Statusdateien zu minimieren, können Sie das Fenster **Status-ZIP herunterladen** nutzen. Das Fenster finden Sie unter **AEM > Tools > Vorgänge > Diagnose > Status-ZIP herunterladen**.

In diesem Fenster können Sie auswählen, was exportiert werden soll (Protokolldateien und/oder Thread-Speicherauszüge) und wie viele Tage die Protokolle im Verhältnis zum aktuellen Datum heruntergeladen werden sollen.

![download_status_zip](assets/download_status_zip.png)

### Thread-Sicherheitskopie herunterladen {#download-thread-dump}

Diese Aktion löst den Download einer ZIP-Datei aus, die Informationen zu den Threads enthält, die im System vorhanden sind. Es werden Informationen zu jedem Thread bereitgestellt, z. B. zum Status, Classloader und Stacktrace.

### Heap-Sicherheitskopie herunterladen {#download-heap-dump}

Sie können einen Snapshot des Heaps herunterladen, um ihn später zu analysieren. Diese Aktion löst den Download einer großen Datei (Hunderte von Megabytes) aus.

## Automatisierte Wartungsaufgaben {#automated-maintenance-tasks}

Auf der Seite „Automatisierte Wartungsaufgaben“ können Sie empfohlene Wartungsaufgaben, für die die regelmäßige Ausführung geplant ist, anzeigen und nachverfolgen. Die Aufgaben sind in das Konsistenzprüfungssystem integriert. Die Aufgaben können auch manuell über die Benutzeroberfläche ausgeführt werden.

Um zur Wartungsseite im Vorgangs-Dashboard zu gelangen, gehen Sie vom AEM-Willkommensbildschirm aus zu **Tools – Vorgänge – Dashboard – Wartung** oder folgen Sie direkt diesem Link:

`https://serveraddress:port/libs/granite/operations/content/maintenance.html`

Die folgenden Aufgaben sind im Vorgangs-Dashboard verfügbar:

1. die Aufgabe **Revisionsbereinigung**, zu finden im Menü **Tägliches Wartungsfenster**
1. die Aufgabe **Lucene-Binärdateien-Bereinigung**, zu finden im Menü **Tägliches Wartungsfenster**
1. die Aufgabe **Workflow-Bereinigung**, zu finden im Menü **Wöchentliches Wartungsfenster**
1. die Aufgabe **Datenspeicherbereinigung**, zu finden im Menü **Wöchentliches Wartungsfenster**
1. die Wartungsaufgabe **Auditprotokoll**, zu finden im Menü **Wöchentliches Wartungsfenster**
1. die Wartungsaufgabe **Versionsbereinigung**, zu finden im Menü **Wöchentliches Wartungsfenster**
1. Die Wartungsaufgabe **Projekt-Bereinigung** unter dem Menü **Wöchentliches Wartungsfenster** unter Verwendung der Option **Hinzufügen**.
1. Die Wartungsaufgabe **Bereinigung von Ad-hoc-Aufgaben** im Menü **Wöchentliches Wartungsfenster** unter Verwendung der Option **Hinzufügen**.

Der Standardzeitrahmen für das tägliche Wartungsfenster beträgt 2:00 Uhr bis 5:00 Uhr morgens. Die Aufgaben, die für das wöchentliche Wartungsfenster konfiguriert sind, werden samstags zwischen 1:00 und 2:00 Uhr morgens ausgeführt.

Sie können diese Zeiten auch konfigurieren. Klicken Sie dazu auf das Zahnradsymbol auf einer der beiden Wartungskarten:

![chlimage_1-126](assets/chlimage_1-126.png)

>[!NOTE]
>
>Seit AEM 6.1 können Sie die vorhandenen Wartungsfenster auch für eine monatliche Ausführung konfigurieren.

### Revisionsbereinigung {#revision-clean-up}

Weitere Informationen finden Sie unter [Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md).

### Lucene-Binärdateien-Bereinigung {#lucene-binaries-cleanup}

Mit dieser Aufgabe können Sie Lucene-Binärdateien bereinigen und die Anforderungen an die Größe des laufenden Datenspeichers verringern. Die Fluktuation der Lucene-Binärdateien wird täglich zurückgewonnen, statt wie bisher von einer erfolgreichen [Speicherbereinigung](/help/sites-administering/data-store-garbage-collection.md) abhängig zu sein.

Zwar wurde die Wartungsaufgabe speziell entwickelt, um den mit Lucene verbundenen Revisions-Müll zu reduzieren, aber es gibt auch allgemeine Effizienzgewinne, wenn die Aufgabe ausgeführt wird:

* Die wöchentliche Ausführung der automatischen Datenspeicherbereinigung kann schneller abgeschlossen werden.
* Auch die Gesamtleistung von AEM kann sich leicht verbessern.

Die Aufgabe „Lucene-Binärdateien-Bereinigung“ finden Sie unter **AEM > Tools > Vorgänge > Wartung > Tägliches Wartungsfenster > Lucene-Binärdateien-Bereinigung**.

### Datenspeicherbereinigung {#data-store-garbage-collection}

Weitere Informationen zur Datenspeicherbereinigung finden Sie auf der entsprechenden Dokumentationsseite zur [Datenspeicherbereinigung](/help/sites-administering/data-store-garbage-collection.md).

### Workflow-Bereinigung {#workflow-purge}

Workflows können auch über das Wartungs-Dashboard bereinigt werden. Gehen Sie wie folgt vor, um die Aufgabe „Workflow-Bereinigung“ auszuführen:

1. Klicken Sie auf die Seite **Wöchentliches Wartungsfenster**.
1. Klicken Sie auf der folgenden Seite auf **Wiedergabe** in der Karte **Workflow-Bereinigung**.

>[!NOTE]
>
>Weitere Informationen zur Workflow-Wartung finden Sie auf unter [Verwalten der Workflow-Instanzen](/help/sites-administering/workflows-administering.md#regular-purging-of-workflow-instances).

### Auditprotokoll-Wartung {#audit-log-maintenance}

Informationen zur Auditprotokoll-Wartung finden Sie auf der entsprechenden [Dokumentationsseite](/help/sites-administering/operations-audit-log.md).

### Versionsbereinigung {#version-purge}

Sie können die Wartungsaufgabe zur Versionsbereinigung planen, um alte Versionen automatisch zu löschen. Diese Aktion minimiert die Notwendigkeit, die [Tools zur Versionsbereinigung](/help/sites-deploying/version-purging.md) manuell zu verwenden. Um die Versionsbereinigung zu planen und zu konfigurieren, führen Sie unter **Tools > Vorgänge > Wartung > Wöchentliches Wartungsfenster** die folgenden Schritte durch:

1. Klicken Sie auf **Hinzufügen**.
1. Wählen Sie aus dem Dropdown-Menü **Versionsbereinigung** aus.

   ![version_purge_maintenance_etask](assets/version_purge_maintenancetask.png)

1. Um die Versionsbereinigungsaufgabe zu konfigurieren, klicken Sie auf das **Zahnradsymbol** auf der neu erstellten Wartungskarte „Versionsbereinigung“.

   ![version_purge_taskconfiguration](assets/version_purge_taskconfiguration.png)

**Mit AEM 6.4** können Sie die Wartungsaufgabe „Versionsbereinigung“ wie folgt stoppen:

* Automatisch – Wenn das geplante Wartungsfenster abläuft, bevor die Aufgabe abgeschlossen ist, wird die Aufgabe automatisch gestoppt. Sie wird fortgesetzt, wenn das nächste Wartungsfenster beginnt.
* Manuell – Um die Aufgabe manuell anzuhalten, klicken Sie auf der Versionsbereinigungs-Wartungskarte auf das **Stopp**-Symbol. Bei der nächsten Ausführung wird die Aufgabe sicher fortgesetzt.

>[!NOTE]
>
>Das Anhalten der Wartungsaufgabe bedeutet, die Ausführung auszusetzen, ohne den bereits ausgeführten Auftrag zu verlieren.

>[!CAUTION]
>
>Um die Größe des Repositorys zu optimieren, sollten Sie die Aufgabe zur Versionsbereinigung regelmäßig ausführen. Die Aufgabe sollte außerhalb der Geschäftszeiten geplant werden, wenn nur ein begrenzter Traffic vorhanden ist.

### Projektbereinigung {#project-purge}

<!--
Override the out-of-the-box Maintenance window configuration node under `/libs` by creating properties under the folder `/apps/settings/granite/operations/maintenance/granite_weekly`, `granite_daily` or `granite_monthly`. See the Maintenance Window table below for additional configuration details.

Enable the maintenance task by adding another node under the node above (name it `granite_ProjectPurgeTask`) with the appropriate properties. 
-->

Konfigurieren Sie die OSGi-Eigenschaften unter **Bereinigungskonfiguration von Adobe-Projekten** (com.adobe.cq.projects.purge.Scheduler).

### Bereinigung von Ad-hoc-Aufgaben {#purge-of-ad-hoc-tasks}

<!--
Override the out-of-the-box Maintenance window configuration node under `/libs` by creating properties under the folder `/apps/settings/granite/operations/maintenance/granite_weekly`, `granite_daily` or `granite_monthly`.

See the Maintenance Window table below for additional configuration details. Enable the maintenance task by adding another node under the node above. Name it `granite_TaskPurgeTask`, with attribute `sling:resourceType` set to `granite/operations/components/maintenance/task` and attribute `granite.maintenance.name` set to `TaskPurge`. 
-->

Konfigurieren Sie die OSGi-Eigenschaften unter **Bereinigung von Ad-hoc-Aufgaben** (`com.adobe.granite.taskmanagement.impl.purge.TaskPurgeMaintenanceTask`).

## Benutzerdefinierte Wartungsaufgaben {#custom-maintenance-tasks}

Sie können benutzerdefinierte Wartungsaufgaben als OSGi-Dienste implementieren. Da die Infrastruktur für Wartungsaufgaben auf der Auftragsverarbeitung von Apache Sling basiert, muss eine Wartungsaufgabe über die Java™-Schnittstelle ` [org.apache.sling.event.jobs.consumer.JobExecutor](https://sling.apache.org/apidocs/sling7/org/apache/sling/event/jobs/consumer/JobExecutor.html)` implementiert werden. Um als Wartungsaufgabe erkannt zu werden, muss sie zusätzlich mehrere Dienstregistrierungseigenschaften festlegen, wie nachfolgend aufgeführt:

<table>
 <tbody>
  <tr>
   <td><strong>Diensteigenschaftsname</strong><br /> </td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Beispiel</strong><br /> </td>
   <td><strong>Typ</strong></td>
  </tr>
  <tr>
   <td>granite.maintenance.isStoppable</td>
   <td>Boolesches Attribut, das definiert, ob die Aufgabe vom Benutzer angehalten werden kann. Wenn für eine Aufgabe festgelegt ist, dass sie angehalten werden kann, muss sie während ihrer Ausführung prüfen, ob sie angehalten wurde, und dann entsprechend reagieren. Der Standardwert lautet „false“.</td>
   <td>true</td>
   <td>Optional</td>
  </tr>
  <tr>
   <td>granite.maintenance.mandatory</td>
   <td>Boolesches Attribut, das definiert, ob eine Aufgabe obligatorisch ist und regelmäßig ausgeführt werden muss. Wenn eine Aufgabe obligatorisch ist, aber derzeit in keinem aktiven Zeitplanfenster existiert, meldet eine Konsistenzprüfung diesen Fehler. Der Standardwert lautet „false“.</td>
   <td>true</td>
   <td>Optional</td>
  </tr>
  <tr>
   <td>granite.maintenance.name</td>
   <td>Ein eindeutiger Name für die Aufgabe – der Name wird verwendet, um auf die Aufgabe zu verweisen, und ist nur ein einfacher Name.</td>
   <td>MyMaintenanceTask</td>
   <td>Erforderlich</td>
  </tr>
  <tr>
   <td>granite.maintenance.title</td>
   <td>Ein Titel für diese Aufgabe wird angezeigt</td>
   <td>Meine besondere Wartungsaufgabe</td>
   <td>Erforderlich</td>
  </tr>
  <tr>
   <td>job.topics</td>
   <td>Ein eindeutiges Thema der Wartungsaufgabe.<br /> Die Apache Sling-Auftragsverarbeitung startet einen Auftrag mit genau diesem Thema, um die Wartungsaufgabe auszuführen, und wenn die Aufgabe für dieses Thema registriert wird, wird sie ausgeführt.<br /> Das Thema muss mit <i>com/adobe/granite/maintenance/job/</i> beginnen.</td>
   <td>com/adobe/granite/maintenance/job/MyMaintenanceTask</td>
   <td>Erforderlich</td>
  </tr>
 </tbody>
</table>

Neben den o. g. Diensteigenschaften müssen Sie auch die `process()`-Methode der Schnittstelle `JobConsumer` implementieren. Fügen Sie dazu den Code hinzu, der für die Wartungsaufgabe ausgeführt werden soll. Mit dem bereitgestellten `JobExecutionContext` können Sie Statusinformationen ausgeben, prüfen, ob der Auftrag von der Benutzerin bzw. dem Benutzer angehalten wurde, und ein Ergebnis erstellen (Erfolg oder Fehlgeschlagen).

Für Situationen, in denen eine Wartungsaufgabe nicht auf allen Installationen ausgeführt werden soll (z. B. nur auf der Publishing-Instanz), können Sie durch Hinzufügen von `@Component(policy=ConfigurationPolicy.REQUIRE)` festlegen, dass der Dienst eine Konfiguration benötigt, um aktiv zu sein. Anschließend können Sie die entsprechende Konfiguration im Repository als abhängig vom Ausführungsmodus markieren. Weitere Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md#creating-the-configuration-in-the-repository).

Nachfolgend finden Sie ein Beispiel für eine benutzerdefinierte Wartungsaufgabe, die Dateien, die in den letzten 24 Stunden geändert wurden, aus einem konfigurierbaren temporären Ordner löscht:

src/main/java/com/adobe/granite/samples/maintenance/impl/DeleteTempFilesTask.java

<table>
 <tbody>
  <tr>
   <td><p> </p> <p><code>/*</code></p> <p><code> * #%L</code></p> <p><code> * sample-maintenance-task</code></p> <p><code> * %%</code></p> <p><code> * Copyright (C) 2014 Adobe</code></p> <p><code> * %%</code></p> <p><code> * Licensed under the Apache License, Version 2.0 (the "License");</code></p> <p><code> * you may not use this file except in compliance with the License.</code></p> <p><code> * You may obtain a copy of the License at</code></p> <p><code> * </code></p> <p><code> * <a href="https://www.apache.org/licenses/LICENSE-2.0">https://www.apache.org/licenses/LICENSE-2.0</a></code></p> <p><code> * </code></p> <p><code> * Unless required by applicable law or agreed to in writing, software</code></p> <p><code> * distributed under the License is distributed on an "AS IS" BASIS,</code></p> <p><code> * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.</code></p> <p><code> * See the License for the specific language governing permissions and</code></p> <p><code> * limitations under the License.</code></p> <p><code> * #L%</code></p> <p><code> */</code></p> <p><code> </code></p> <p><code>package com.adobe.granite.samples.maintenance.impl;</code></p> <p><code> </code></p> <p><code>import java.io.File;</code></p> <p><code>import java.util.Calendar;</code></p> <p><code>import java.util.Collection;</code></p> <p><code>import java.util.Map;</code></p> <p><code> </code></p> <p><code>import org.apache.commons.io.FileUtils;</code></p> <p><code>import org.apache.commons.io.filefilter.IOFileFilter;</code></p> <p><code>import org.apache.commons.io.filefilter.TrueFileFilter;</code></p> <p><code>import org.apache.felix.scr.annotations.Activate;</code></p> <p><code>import org.apache.felix.scr.annotations.Component;</code></p> <p><code>import org.apache.felix.scr.annotations.Properties;</code></p> <p><code>import org.apache.felix.scr.annotations.Property;</code></p> <p><code>import org.apache.felix.scr.annotations.Service;</code></p> <p><code>import org.apache.sling.commons.osgi.PropertiesUtil;</code></p> <p><code>import org.apache.sling.event.jobs.Job;</code></p> <p><code>import org.apache.sling.event.jobs.consumer.JobConsumer;</code></p> <p><code>import org.apache.sling.event.jobs.consumer.JobExecutionContext;</code></p> <p><code>import org.apache.sling.event.jobs.consumer.JobExecutionResult;</code></p> <p><code>import org.apache.sling.event.jobs.consumer.JobExecutor;</code></p> <p><code>import org.slf4j.Logger;</code></p> <p><code>import org.slf4j.LoggerFactory;</code></p> <p><code> </code></p> <p><code>import com.adobe.granite.maintenance.MaintenanceConstants;</code></p> <p><code> </code></p> <p><code>@Component(metatype = true,</code></p> <p><code> label = "Delete Temp Files Maintenance Task",</code></p> <p><code> description = "Maintatence Task which deletes files from a configurable temporary directory which have been modified in the last 24 hours.")</code></p> <p><code>@Service</code></p> <p><code>@Properties({</code></p> <p><code> @Property(name = MaintenanceConstants.PROPERTY_TASK_NAME, value = "DeleteTempFilesTask", propertyPrivate = true),</code></p> <p><code> @Property(name = MaintenanceConstants.PROPERTY_TASK_TITLE, value = "Delete Temp Files", propertyPrivate = true),</code></p> <p><code> @Property(name = JobConsumer.PROPERTY_TOPICS, value = MaintenanceConstants.TASK_TOPIC_PREFIX</code></p> <p><code> + "DeleteTempFilesTask", propertyPrivate = true) })</code></p> <p><code>public class DeleteTempFilesTask implements JobExecutor {</code></p> <p><code> </code></p> <p><code> private static final Logger log = LoggerFactory.getLogger(DeleteTempFilesTask.class);</code></p> <p><code> </code></p> <p><code> @Property(label = "Temporary Directory", description="Temporary Directory. Defaults to the java.io.tmpdir system property.")</code></p> <p><code> private static final String PROP_TEMP_DIR = "temp.dir";</code></p> <p><code> </code></p> <p><code> private File tempDir;</code></p> <p><code> </code></p> <p><code> @Activate</code></p> <p><code> private void activate(Map&lt;string, object=""&gt; properties) {</code></p> <p><code> this.tempDir = new File(PropertiesUtil.toString(properties.get(PROP_TEMP_DIR),</code></p> <p><code> System.getProperty("java.io.tmpdir")));</code></p> <p><code> }</code></p> <p><code> </code></p> <p><code> @Override</code></p> <p><code> public JobExecutionResult process(Job job, JobExecutionContext context) {</code></p> <p><code> log.info("Deleting old temp files from {}.", tempDir.getAbsolutePath());</code></p> <p><code> Collection&lt;file&gt; files = FileUtils.listFiles(tempDir, new LastModifiedBeforeYesterdayFilter(),</code></p> <p><code> TrueFileFilter.INSTANCE);</code></p> <p><code> int counter = 0;</code></p> <p><code> for (File file : files) {</code></p> <p><code> log.debug("Deleting file {}.", file.getAbsolutePath());</code></p> <p><code> counter++;</code></p> <p><code> file.delete();</code></p> <p><code> // TODO - capture the output of delete() and do something useful with it</code></p> <p><code> }</code></p> <p><code> return context.result().message(String.format("Deleted %s files.", counter)).succeeded();</code></p> <p><code> }</code></p> <p><code> </code></p> <p><code> /**</code></p> <p><code> * IOFileFilter which filters out files which have been modified in the last 24 hours.</code></p> <p><code> *</code></p> <p><code> */</code></p> <p><code> private static class LastModifiedBeforeYesterdayFilter implements IOFileFilter {</code></p> <p><code> </code></p> <p><code> private final long minTime;</code></p> <p><code> </code></p> <p><code> private LastModifiedBeforeYesterdayFilter() {</code></p> <p><code> Calendar cal = Calendar.getInstance();</code></p> <p><code> cal.add(Calendar.DATE, -1);</code></p> <p><code> this.minTime = cal.getTimeInMillis();</code></p> <p><code> }</code></p> <p><code> </code></p> <p><code> @Override</code></p> <p><code> public boolean accept(File dir, String name) {</code></p> <p><code> // this method is never actually called.</code></p> <p><code> return false;</code></p> <p><code> }</code></p> <p><code> </code></p> <p><code> @Override</code></p> <p><code> public boolean accept(File file) {</code></p> <p><code> return file.lastModified() <= this.minTime;</code></p> <p><code> }</code></p> <p><code> }</code></p> <p><code> </code></p> <p><code>}</code></p> <p><code>&lt;file&gt;&lt;/string,&gt;</code></p> <p> </p> </td>
  </tr>
 </tbody>
</table>

[experiencemanager-java-maintenancetask-sample ](https://github.com/Adobe-Marketing-Cloud/experiencemanager-java-maintenancetask-sample)- [src/main/java/com/adobe/granite/samples/maintenance/impl/DeleteTempFilesTask.java](https://github.com/Adobe-Marketing-Cloud/experiencemanager-java-maintenancetask-sample/blob/master/src/main/java/com/adobe/granite/samples/maintenance/impl/DeleteTempFilesTask.java)

Nachdem der Dienst bereitgestellt wurde, wird er der Benutzeroberfläche des Vorgangs-Dashboards angezeigt. Sie können ihn zu einem der verfügbaren Wartungszeitpläne hinzufügen:

![chlimage_1-127](assets/chlimage_1-127.png)

Daraufhin wird eine entsprechende Ressource unter „/apps/granite/operations/config/maintenance/`schedule`/`taskname`“ hinzugefügt. Wenn die Aufgabe vom Ausführungsmodus abhängig ist, muss die Eigenschaft „granite.operations.conditions.runmode“ auf diesem Knoten festgelegt werden, wobei die Werte der Ausführungsmodi, die für diese Wartungsaufgabe aktiv sein müssen, anzugeben sind.

## Systemübersicht {#system-overview}

Das **Systemübersicht-Dashboard** bietet einen allgemeinen Überblick über die Konfiguration, die Hardware und die Konsistenz der AEM-Instanz. Der Status der Systemkonsistenz ist also transparent, und alle entsprechenden Daten werden in einem zentralen Dashboard zusammengeführt.

>[!NOTE]
>
>Eine Einführung in das Systemübersicht-Dashboard erhalten Sie auch [in diesem Video](https://video.tv.adobe.com/v/40393?captions=ger).

### Zugriff {#how-to-access}

Um auf das Systemübersicht-Dashboard zuzugreifen, gehen Sie zu **Tools > Vorgänge > Systemübersicht**.

![system_overview_dashboard](assets/system_overview_dashboard.png)

### Erläuterung zum Systemübersichts-Dashboard {#system-overview-dashboard-explained}

In der nachfolgenden Tabelle werden alle Informationen beschrieben, die im Systemübersichts-Dashboard angezeigt werden. Wenn es keine relevanten anzuzeigenden Informationen gibt (z. B. es wird nicht gerade ein Backup durchgeführt, es gibt keine kritischen Konsistenzprüfungen), wird im entsprechenden Bereich die Meldung „Keine Einträge“ angezeigt.

Sie können auch eine `JSON`-Datei mit einer Zusammenfassung der Dashboard-Informationen herunterladen, indem Sie auf die Schaltfläche **Herunterladen** in der rechten oberen Ecke des Dashboards klicken. Der `JSON`-Endpunkt ist `/libs/granite/operations/content/systemoverview/export.json` und kann in einem `curl`-Skript zur externen Überwachung verwendet werden.

<table>
 <tbody>
  <tr>
   <td><strong>Abschnitt</strong></td>
   <td><strong>Angezeigte Informationen</strong></td>
   <td><strong>Wann liegt ein kritischer Status vor</strong></td>
   <td><strong>Ist verknüpft mit</strong></td>
  </tr>
  <tr>
   <td>Konsistenzprüfungen</td>
   <td>
    <ul>
     <li>eine Liste der Prüfungen mit dem Status „Kritisch“</li>
     <li>eine Liste der Prüfungen mit dem Status „Warnung“</li>
    </ul> </td>
   <td>Visueller Hinweis:<br />
    <ul>
     <li>ein rotes Tag für Prüfungen mit dem Status „Kritisch“</li>
     <li>ein orangefarbenes Tag für Prüfungen mit dem Status „Warnung“</li>
    </ul> </td>
   <td>
    <ul>
     <li>Konsistenzberichte-Seite</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Wartungsaufgaben</td>
   <td>
    <ul>
     <li>eine Liste der fehlgeschlagenen Aufgaben</li>
     <li>eine Liste der Aufgaben, die derzeit ausgeführt werden</li>
     <li>eine Liste der Aufgaben, die in der letzten Ausführung erfolgreich waren</li>
     <li>eine Liste von Aufgaben, die noch nie ausgeführt wurden</li>
     <li>eine Liste von Aufgaben, die nicht geplant sind</li>
    </ul> </td>
   <td><p>Visueller Hinweis:</p>
    <ul>
     <li>ein rotes Tag für fehlgeschlagene Aufgaben</li>
     <li>ein orangefarbenes Tag für laufende Aufgaben (da sie sich auf die Leistung auswirken können)</li>
     <li>graue Tags für jeden anderen Status</li>
    </ul> </td>
   <td>
    <ul>
     <li>Wartungsaufgaben-Seite</li>
    </ul> </td>
  </tr>
  <tr>
   <td>System</td>
   <td>
    <ul>
     <li>Betriebssystem und Betriebssystemversion (z. B. macOS X)</li>
     <li>durchschnittliche Systemlast, abgerufen von <a href="https://docs.oracle.com/javase/8/docs/api/java/lang/management/OperatingSystemMXBean.html#getSystemLoadAverage--">OperatingSystemMXBeanusable</a></li>
     <li>Festplattenspeicherplatz (auf der Partition, auf der sich das Basisverzeichnis befindet)</li>
     <li>maximaler Heap, wie zurückgegeben von <a href="https://docs.oracle.com/javase/8/docs/api/java/lang/management/MemoryMXBean.html#getHeapMemoryUsage--">MemoryMXBean</a></li>
    </ul> </td>
   <td>Nicht zutreffend</td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td>Instanz</td>
   <td>
    <ul>
     <li>die AEM-Version</li>
     <li>Liste der Ausführungsmodi</li>
     <li>das Datum, an dem die Instanz gestartet wurde</li>
    </ul> </td>
   <td>Nicht zutreffend</td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td>Repository</td>
   <td>
    <ul>
     <li>die Oak-Version</li>
     <li>Typ des Knotenspeichers („Segment-TAR“ oder „Dokument“)
      <ul>
       <li>Beim Typ „Dokument“ wird der Typ des Dokumentenspeichers angezeigt (RDB oder Mongo)</li>
      </ul> </li>
     <li>wenn ein benutzerdefinierter Datenspeicher vorhanden ist:
      <ul>
       <li>bei einem Dateidatenspeicher wird der Pfad angezeigt</li>
       <li>bei einem S3-Datenspeicher wird der Name des S3-Buckets angezeigt</li>
       <li>bei einem freigegebenen S3-Datenspeicher wird der Name des S3-Buckets angezeigt</li>
       <li>bei einem Azure-Datenspeicher wird der Container angezeigt</li>
      </ul> </li>
     <li>wenn es keinen benutzerdefinierten externen Datenspeicher gibt, wird eine entsprechende Meldung angezeigt.</li>
    </ul> </td>
   <td>Nicht zutreffend</td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td>Verteilungsagenten</td>
   <td>
    <ul>
     <li>eine Liste der Agenten mit blockierten Warteschlangen</li>
     <li>eine Liste der falsch konfigurierten Agenten („Konfigurationsfehler“)</li>
     <li>eine Liste der Agenten, bei denen die Warteschlangenverarbeitung pausiert wurde</li>
     <li>eine Liste der inaktiven Agenten</li>
     <li>eine Liste der ausgeführten Agenten (die derzeit Einträge verarbeiten)</li>
    </ul> </td>
   <td><p>Visueller Hinweis:</p>
    <ul>
     <li>ein rotes Tag für blockierte Agenten oder Konfigurationsfehler</li>
     <li>ein orangefarbenes Tag für pausierte Agenten</li>
     <li>ein graues Tag für pausierte, inaktive oder derzeit ausgeführte Agenten<br /> </li>
    </ul> </td>
   <td>Verteilungsseite<br /> </td>
  </tr>
  <tr>
   <td>Replikations-Agenten</td>
   <td>
    <ul>
     <li>eine Liste der Agenten mit blockierten Warteschlangen</li>
     <li>eine Liste der inaktiven Agenten</li>
     <li>eine Liste der ausgeführten Agenten (die derzeit Einträge verarbeiten)</li>
    </ul> </td>
   <td><p>Visueller Hinweis:<br /> </p>
    <ul>
     <li>ein rotes Tag für blockierte Agenten</li>
     <li>ein graues Tag für pausierte Agenten</li>
    </ul> </td>
   <td>Replikationsseite</td>
  </tr>
  <tr>
   <td>Workflows</td>
   <td>
    <ul>
     <li>Workflow-Aufträge:
      <ul>
       <li>Anzahl an fehlgeschlagenen Workflow-Aufträgen (falls vorhanden)</li>
       <li>Anzahl an abgebrochenen Workflow-Aufträgen (falls vorhanden)</li>
      </ul> </li>
    </ul>
    <ul>
     <li>Workflow-Anzahl – die Anzahl an Workflows in einem bestimmten Status (falls vorhanden):
      <ul>
       <li>Ausführung läuft</li>
       <li>fehlgeschlagen</li>
       <li>unterbrochen</li>
       <li>abgebrochen</li>
      </ul> </li>
    </ul> <p>Für jeden der oben aufgeführten Status wird eine Abfrage mit einer Beschränkung von 400 Millisekunden durchgeführt. Bei 400 Millisekunden wird die Anzahl der bis zu diesem Zeitpunkt erhaltenen Einträge angezeigt.</p> </td>
   <td><p>Nicht interpretiert:</p>
    <ul>
     <li>Die Benutzenden sollten nachforschen, wenn Workflows und Aufträge in unerwarteten Status vorhanden sind.</li>
    </ul> </td>
   <td>Seite „Workflow-Fehler“</td>
  </tr>
  <tr>
   <td>Sling Jobs</td>
   <td><p>Anzahl an Sling-Aufträgen – Anzahl an Aufträgen in einem bestimmten Status (falls vorhanden):</p>
    <ul>
     <li>fehlgeschlagen</li>
     <li>in der Warteschlange</li>
     <li>abgebrochen</li>
     <li>aktiv</li>
    </ul> </td>
   <td><p>Nicht interpretiert:</p>
    <ul>
     <li>Die Benutzenden sollten nachforschen, wenn Aufträge in unerwarteten Status oder mit hohen Zahlen vorliegen.</li>
    </ul> </td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td>Voraussichtliche Knotenanzahl</td>
   <td><p>Geschätzte Anzahl von:</p>
    <ul>
     <li>Seiten</li>
     <li>Assets</li>
     <li>tags</li>
     <li>autorisierbare</li>
     <li>Gesamtanzahl der Knoten<br /> </li>
    </ul> <p>Die Gesamtzahl an Knoten wird vom nodeCounterMBean abgerufen, die übrigen Statistiken dagegen von IndexInfoService.</p> </td>
   <td>Nicht zutreffend</td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td>Sicherung</td>
   <td>Zeigt ggf. „Online-Sicherung wird ausgeführt“ an.</td>
   <td>Nicht zutreffend</td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td>Indizierung</td>
   <td><p>Displays:</p>
    <ul>
     <li>„Indizierung wird ausgeführt“</li>
     <li>„Abfrage wird ausgeführt“</li>
    </ul> <p>Wenn ein Indizierungs- oder Abfrage-Thread in dem Thread-Speicherauszug vorhanden ist</p> </td>
   <td>Nicht zutreffend</td>
   <td>Nicht zutreffend</td>
  </tr>
 </tbody>
</table>
