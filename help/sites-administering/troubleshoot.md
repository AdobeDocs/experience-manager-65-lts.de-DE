---
title: Fehlerbehebung bei Adobe Experience Manager
description: Erfahren Sie mehr über die Fehlerbehebung bei einigen Problemen, die möglicherweise mit Adobe Experience Manager auftreten.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
exl-id: 802130c3-9cb8-46b7-98c2-fd9e83d18ec3
source-git-commit: 929a2175449a371ecf81226fedb98a0c5c6d7166
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 97%

---

# Fehlerbehebung bei Adobe Experience Manager {#troubleshooting-aem}

Der folgende Abschnitt behandelt einige Probleme, die bei der Verwendung von AEM (Adobe Experience Manager) auftreten können, sowie Vorschläge zur Fehlerbehebung.

>[!NOTE]
>
>Wenn Sie Probleme beim Erstellen von Inhalten in AEM beheben möchten, lesen Sie den Abschnitt [Fehlerbehebung für Autoren und Autorinnen](/help/sites-authoring/troubleshooting.md).

>[!NOTE]
>
>Bei Problemen ist es auch sinnvoll, die Liste der [Bekannten Probleme](/help/release-notes/release-notes.md) für Ihre Instanz (Version und Service Packs) zu prüfen.

## Fehlerbehebungsszenarien für Admins {#troubleshooting-scenarios-for-administrators}

Die folgende Tabelle bietet einen Überblick über Probleme, die Admins beheben können:

<table>
 <tbody>
  <tr>
   <td><strong>Rolle</strong></td>
   <td><strong>Problem </strong></td>
  </tr>
  <tr>
   <td>Systemadmin</td>
   <td><p>Ein Doppelklick auf die JAR-Datei für den Schnellstart zeigt keine Wirkung oder öffnet die JAR-Datei mit einem anderen Programm (z. B. dem Archiv-Manager)</p> </td>
  </tr>
  <tr>
   <td><p>Systemadmin</p> </td>
   <td><p>Über CRX ausgeführte Anwendung erzeugt Fehler wegen unzureichendem Arbeitsspeicher</p> </td>
  </tr>
  <tr>
   <td><p>Systemadmin</p> </td>
   <td><p>Der AEM-Willkommensbildschirm wird nach einem Doppelklick auf den AEM-CM-Schnellstart nicht im Browser angezeigt</p> </td>
  </tr>
  <tr>
   <td><p>Systemadmin</p> <p>Admin-Benutzer</p> </td>
   <td><p>Erstellen von Thread-Speicherauszügen</p> </td>
  </tr>
  <tr>
   <td><p>Systemadmin</p> <p>Admin-Benutzer</p> </td>
   <td><p>Überprüfung auf nicht beendete JCR-Sitzungen</p> </td>
  </tr>
 </tbody>
</table>


## Methoden zur Fehlerbehebung in der Analyse {#methods-for-troubleshooting-analysis}

### Erstellen von Thread-Speicherauszügen {#making-a-thread-dump}

Ein Thread-Speicherauszug ist eine Liste aller Java™-Threads, die derzeit aktiv sind. Wenn AEM nicht richtig reagiert, kann der Thread-Speicherauszug helfen, Deadlocks oder andere Probleme zu identifizieren.

### Verwendung vom Sling-Thread-Speicherauszug {#using-sling-thread-dumper}

1. Öffnen Sie die **AEM-Web-Konsole**, zum Beispiel unter `https://localhost:4502/system/console/`.
1. Wählen Sie auf der Registerkarte **Status** die Option **Threads** aus.

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### Verwenden von jstack (Befehlszeile) {#using-jstack-command-line}

1. Suchen Sie die PID (Prozess-ID) der AEM-Java™-Instanz.

   Sie können beispielsweise `ps -ef` oder `jps` verwenden.

1. Ausführen:

   `jstack <pid>`

1. Zeigt den Thread-Speicherauszug an.

>[!NOTE]
>
>Sie können die Thread-Speicherauszüge an eine Protokolldatei anhängen, indem Sie die `>>`-Ausgabeumleitung verwenden:
>
>`jstack <pid> >> /path/to/logfile.log`

Weitere Informationen dazu finden Sie in der Dokumentation [Erstellen von Thread-Speicherauszügen von einem JVM](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17452.html?lang=de).

### Überprüfen auf nicht beendete JCR-Sitzungen {#checking-for-unclosed-jcr-sessions}

Wenn Funktionen für AEM WCM entwickelt werden, können JCR-Sitzungen geöffnet werden (vergleichbar mit dem Öffnen einer Datenbankverbindung). Wenn die geöffneten Sitzungen nie geschlossen werden, kann Ihr System folgende Symptome aufweisen:

* Das System wird langsamer.
* Es befinden sich viele „CacheManager: resizeAll“-Einträge in der Protokolldatei. Die folgende Zahl (size=&lt;x>) gibt die Anzahl an Caches an; jede Sitzung öffnet mehrere Caches.
* Gelegentlich reicht der Speicherplatz des Systems nicht aus (nach einigen Stunden, Tagen oder Wochen – je nach Schweregrad).

Informationen zum Starten der Analyse nicht geschlossener Sitzungen finden Sie im Knowledgebase-Artikel [Nicht geschlossener Ressourcen-Resolver](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-23761).

### Verwenden der Adobe Experience Manager-Web-Konsole {#using-the-adobe-experience-manager-web-console}

Der Status der OSGi-Pakete kann auch frühzeitig auf mögliche Probleme hinweisen.

1. Öffnen Sie die **AEM-Web-Konsole**, zum Beispiel unter `https://localhost:4502/system/console/`.
1. Wählen auf der Registerkarte **OSGi** die Option **Pakete** aus.
1. Überprüfen Sie Folgendes:

   * den Status der Pakete. Falls Status wie „Inaktiv“ oder „Nicht erfüllt“ angezeigt werden, versuchen Sie, das Paket zu stoppen und neu zu starten. Wenn das Problem weiterhin besteht, untersuchen Sie es mit anderen Methoden weiter.
   * ob Pakete mit fehlenden Abhängigkeiten vorliegen. Dies können Sie herausfinden, indem Sie auf den einzelnen Paketnamen klicken, bei dem es sich um einen Link handelt (im folgenden Beispiel sind keine Probleme aufgetreten):

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)
