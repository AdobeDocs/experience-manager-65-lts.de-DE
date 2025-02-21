---
title: Prüfungen und Fehlerbehebung nach einem Upgrade
description: Erfahren Sie, wie Sie Probleme beheben, die nach einem Upgrade auftreten können.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
docset: aem65
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: ee5f1f68f6f961ba0a18296eaf198ebe8671b226
workflow-type: tm+mt
source-wordcount: '1242'
ht-degree: 92%

---

# Prüfungen und Fehlerbehebung nach einem Upgrade{#post-upgrade-checks-and-troubleshooting}

## Prüfungen nach einem Upgrade {#post-upgrade-checks}

Nach einem [ersetzenden Upgrade](/help/sites-deploying/in-place-upgrade.md) sollten folgende Schritte durchgeführt werden, um das Upgrade abzuschließen. Es wird davon ausgegangen, dass AEM mit dem JAR 6.5.2025 gestartet und die aktualisierte Code-Basis bereitgestellt wurde.

* [Überprüfen der Protokolle auf ein erfolgreiches Upgrade](#main-pars-header-290365562)

* [Überprüfen von OSGi-Paketen](#main-pars-header-1637350649)

* [Überprüfen der Oak-Version](#main-pars-header-1293049773)

* [Überprüfen des Ordners „PreUpgradeBackup“](#main-pars-header-988995987)

* [Erstüberprüfung von Seiten](#main-pars-header-20827371)
* [Anwenden von AEM Service Packs](#main-pars-header-215142387)

* [Migrieren von AEM-Funktionen](#main-pars-header-1434457709)

* [Überprüfen der Konfigurationen für die geplante Wartung](#main-pars-header-1552730183)

* [Aktivieren von Replikationsagenten](#main-pars-header-823243751)

* [Aktivieren von benutzerdefinierten geplanten Aufträgen](#main-pars-header-244535083)

* [Ausführen des Testplans](#main-pars-header-1167972233)

### Überprüfen der Protokolle auf ein erfolgreiches Upgrade {#verify-logs-for-upgrade-success}

**upgrade.log**

Bisher mussten diverse Protokolldateien, Teile des Repositorys und das Launchpad sorgfältig überprüft werden, um den Status Ihrer Instanz nach einem Upgrade zu bestimmen. Durch das Generieren von Berichten nach einer Aktualisierung können defekte Upgrades erkannt werden, bevor Instanzen zum Einsatz kommen.

Der primäre Zweck dieser Funktion besteht darin, den manuellen Interpretationsaufwand zu reduzieren oder eine komplexe Parsing-Logik für mehrere Endpunkte zu vermeiden, die erforderlich sind, um den Erfolg eines Upgrades zu qualifizieren. Ziel der Lösung ist es, eindeutige Informationen für externe Automatisierungssysteme bereitzustellen, damit diese auf den Erfolg oder den erkannten Fehlschlag einer Aktualisierung reagieren können.

Sie dient vor allem dazu, Folgendes sicherzustellen:

* Fehlgeschlagene Upgrades, die vom Upgrade-Framework erkannt werden, werden in einem einzigen Upgrade-Bericht zusammengefasst.
* Der Upgrade-Bericht enthält Indikatoren über notwendige manuelle Eingriffe.

Um diesem Rechnung zu tragen, wurde das Verfahren für die Generierung von Protokollen in der Datei `upgrade.log` geändert.

**error.log**

Die Datei „error.log“ sollte beim Start von AEM und danach anhand der JAR-Datei der JAR-Zielversion sorgfältig überprüft werden. Alle Warnungen und Fehler müssen dabei geprüft werden. Im Allgemeinen ist es am besten, am Anfang des Protokolls nach möglichen Problemen zu suchen. Fehler, die weiter unten im Protokoll aufgeführt werden, sind u. U. Nebeneffekte einer Grundursache, die sich am Dateianfang findet. Wenn wiederholte Fehler und Warnungen auftreten, finden Sie im nachfolgenden Abschnitt [Analysieren von Problemen beim Upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-the-upgrade) weitere Informationen.

### Überprüfen von OSGi-Paketen {#verify-osgi-bundles}

Navigieren Sie zur OSGi-Konsole unter `/system/console/bundles` und überprüfen Sie, ob irgendwelche Pakete nicht gestartet wurden. Wenn Bundles den Status „Installiert“ aufweisen, überprüfen Sie die Datei `error.log`, um das ursächliche Problem zu ermitteln.

### Überprüfen der Oak-Version {#verify-oak-version}

Nach dem Upgrade sollte ersichtlich sein, dass die Oak-Version auf Version **.1.68.0 aktualisiert**. Um die Oak-Version zu überprüfen, navigieren Sie zur OSGi-Konsole und suchen Sie nach der entsprechenden Version der Oak-Bundles: Oak Core, Oak Commons, Oak Segment Tar.

### Erstüberprüfung von Seiten {#initial-validation-of-pages}

Führen Sie in AEM eine Erstüberprüfung mithilfe von mehreren Seiten durch. Wenn eine Autorenumgebung ein Upgrade erhält, öffnen Sie die Startseite und die Begrüßungsseite (`/aem/start.html`, `/libs/cq/core/content/welcome.html`). Öffnen Sie in Autoren- und Veröffentlichungsumgebungen einige Anwendungsseiten und prüfen Sie, ob diese richtig angezeigt werden. Wenn Probleme auftreten, finden Sie in der Datei `error.log` weitere Informationen zur Fehlerbehebung.

### Überprüfen der Konfigurationen für die geplante Wartung {#verify-scheduled-maintenance-configurations}

#### Aktivieren der Bereinigung des Datenspeichers {#enable-data-store-garbage-collection}

Wenn Sie einen Dateidatenspeicher verwenden, stellen Sie sicher, dass die Aufgabe „Data Store-Abfallsammlung“ aktiviert ist und zur Liste für die wöchentliche Wartung hinzugefügt wurde. Anweisungen hierzu finden Sie unter [Revisionsbereinigung](/help/sites-administering/data-store-garbage-collection.md).

>[!NOTE]
>
>Die Aufgabe wird nicht für benutzerdefinierte S3-Datenspeicherinstallationen empfohlen oder wenn ein freigegebener Datenspeicher verwendet wird.

#### Aktivieren der Online-Revisionsbereinigung {#enable-online-revision-cleanup}

Wenn Sie MongoMK oder das neue TarMK-Segmentformat verwenden, stellen Sie sicher, dass die Aufgabe „Revisionsbereinigung“ aktiviert ist und zur Liste für die tägliche Wartung hinzugefügt wurde. Anweisungen hierzu finden Sie unter [Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md).

### Ausführen des Testplans {#execute-test-plan}

Führen Sie einen detaillierten Testplan durch, wie unter [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) im Abschnitt **Testverfahren** beschrieben.

### Aktivieren von Replikationsagenten {#enable-replication-agents}

Wenn eine Veröffentlichungsumgebung vollständig upgegradet und überprüft wurde, aktivieren Sie die Replikationsagenten in der Autorenumgebung. Vergewissern Sie sich, dass die Agenten eine Verbindung mit den jeweiligen Veröffentlichungsinstanzen herstellen können. Siehe [Upgrade-Verfahren](/help/sites-deploying/upgrade-procedure.md) für weitere Informationen zur Reihenfolge der Ereignisse.

### Aktivieren von benutzerdefinierten geplanten Aufträgen {#enable-custom-scheduled-jobs}

Zu diesem Zeitpunkt können alle geplanten Aufträge, die Teil der Codebasis sind, aktiviert werden.

## Analysieren von Upgrade-Problemen {#analyzing-issues-with-upgrade}

Dieser Abschnitt enthält einige Problemszenarien, die möglicherweise im Zuge des Upgrades auf AEM 6.5.2025 auftreten.

Diese Szenarien sollen dabei helfen, die Grundursache der mit der Aktualisierung im Zusammenhang stehenden Probleme zu identifizieren. Ferner sollen sie dazu beitragen, projekt- oder produktspezifische Probleme zu ermitteln.

### Fehlerhafte Aktualisierung von Paketen  {#packages-and-bundles-fail-to-update-}

Wenn Pakete während des Upgrades nicht installiert werden können, werden die darin enthaltenen Pakete ebenfalls nicht aktualisiert. Diese Kategorie von Problemen geht auf eine Fehlkonfiguration des Datenspeichers zurück.  Sie werden auch als **ERROR**- und **WARN**-Meldungen in der Datei error.log angezeigt. Da in den meisten dieser Fälle die Standardanmeldung möglicherweise nicht funktioniert, können Sie CRXDE direkt verwenden, um die Konfigurationsprobleme zu untersuchen und zu finden.

### Upgrade wurde nicht ausgeführt {#the-upgrade-did-not-run}

Stellen Sie vor Beginn der vorbereitenden Schritte sicher, dass zuerst die **Quellinstanz** ausgeführt wird. Verwenden Sie hierzu den Java™-Befehl „-jar aem-quickstart.jar“. Dieser Schritt ist notwendig, um zu gewährleisten, dass die Datei „quickstart.properties“ ordnungsgemäß generiert wird. Fehlt diese Datei, wird das Upgrade nicht durchgeführt. Alternativ dazu können Sie im Installationsordner der Quellinstanz unter `crx-quickstart/conf` prüfen, ob die Datei vorhanden ist. Außerdem muss sie beim Starten von AEM für das Upgrade mit dem Java™-Befehl „-jar aem-quickstart.jar“ ausgeführt werden. Beim Starten mit einem Startskript wird AEM nicht im Upgrade-Modus gestartet.

### Einige AEM-Pakete wechseln nicht in den aktiven Status {#some-aem-bundles-are-not-switching-to-the-active-state}

Wenn Bundles nicht starten, prüfen Sie diese auf nicht erfüllte Abhängigkeiten.

Wenn dieses Problem auftritt, jedoch auf eine fehlerhafte Paketinstallation zurückzuführen ist, wodurch Pakete nicht aktualisiert werden, werden diese für die neue Version als inkompatibel angesehen. Weitere Informationen über die entsprechende Fehlerbehebung finden Sie oben unter **Fehlerhafte Aktualisierung von Pakete**.

Es wird außerdem empfohlen, die Bundle-Liste einer neuen AEM 6.5.2025-Instanz mit der upgegradeten zu vergleichen, um nicht upgegradete Bundles zu erkennen. Dadurch kann der Bereich der zu suchenden Elemente in der Datei `error.log` eingegrenzt werden.

### Benutzerdefinierte Pakete wechseln nicht in den aktiven Status {#custom-bundles-not-switching-to-the-active-state}

Wenn Ihre benutzerdefinierten Bundles nicht in den aktiven Status wechseln, liegt dies höchstwahrscheinlich an Code, der die geänderte API nicht importiert. Dies führt oftmals zu nicht erfüllten Abhängigkeiten.

Es empfiehlt sich zudem, zu überprüfen, ob die Änderung, die das Problem verursacht hat, nötig war, und sie zurückzusetzen, wenn dies nicht der Fall ist. Überprüfen Sie zudem, ob die Version des Paketexports unter Beachtung einer strengen semantischen Versionierung mehr als nötig erhöht wurde.

### Analysieren der Dateien „error.log“ und „upgrade.log“ {#analyzing-the-error.log-and-upgrade.log}

In den meisten Situationen müssen die Protokolle auf Fehler untersucht werden, um die Ursache eines Problems zu ermitteln. Bei Upgrades ist es jedoch ebenfalls erforderlich, Abhängigkeitsfehler zu überwachen, da alte Bundles möglicherweise nicht ordnungsgemäß aktualisiert werden.

Dafür sollten Sie alle Meldungen aus der Datei „error.log“ entfernen, die erwartungsgemäß nicht mit Ihrem Problem in Zusammenhang stehen. Dies ist mit einem Tool wie grep möglich, indem Sie Folgendes verwenden:

```shell
grep -v UnrelatedErrorString
```

Einige Fehlermeldungen sind möglicherweise nicht sofort selbsterklärend. In diesem Fall kann die Anzeige des Kontexts, in dem sie auftreten, verdeutlichen, wo der Fehler verursacht wurde. Sie können den Fehler mithilfe der folgenden Befehle trennen:

* `grep -B` für das Hinzufügen von Zeilen vor dem Fehler

oder

* `grep -A` für das Hinzufügen von Zeilen nach dem Fehler.

In einigen Fällen können Fehler auch in WARN-Meldungen gefunden werden, da gültige Fälle vorliegen können, die zu diesem Status führen. Die Anwendung kann darüber hinaus nicht immer entscheiden, ob ein tatsächlicher Fehler vorliegt. Sie sollten diese Meldungen ebenfalls lesen.

### Kontaktaufnahme mit dem Adobe-Support {#contacting-adobe-support}

Wenn Sie die Empfehlungen auf dieser Seite befolgt haben und weiterhin Fehler auftreten, wenden Sie sich an den Adobe-Support. Um dem Supportteam so viele Informationen wie möglich für Ihren Fall bereitzustellen, fügen Sie Ihrer Support-Anfrage die Datei „upgrade.log“ für das Upgrade hinzu.
