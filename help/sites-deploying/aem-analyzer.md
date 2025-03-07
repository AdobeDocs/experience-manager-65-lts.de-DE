---
title: Bewerten der Aktualisierungskomplexität mit dem AEM Analyzer
description: Erfahren Sie, wie Sie mit dem AEM Analyzer die Komplexität Ihres Upgrades bewerten können.
topic-tags: upgrading
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 87c30912-c89a-42f1-b37b-ec439e7318c7
source-git-commit: 6b846e456466492f4be2c1e5a1f6b3913ae4dab4
workflow-type: tm+mt
source-wordcount: '2069'
ht-degree: 23%

---

# Bewerten der Aktualisierungskomplexität mit dem AEM Analyzer {#assessing-the-upgrade-complexity-with-the-aem-analyzer}

## Überblick {#overview}

Der AEM 6.5 LTS Analyzer bietet eine Bewertung Ihrer aktuellen AEM-Implementierung, indem er Bereiche angibt, die aktualisiert werden müssen, um ein nahtloses Upgrade auf 6.5 LTS zu ermöglichen.

Das Tool generiert einen Bericht, der Bereiche identifiziert, in denen eine Umgestaltung möglich ist.

## AEM 6.5 LTS Analyzer-Bericht {#aem-65lts-analyzer-report}

Der LTS Analyzer-Bericht zu AEM 6.5 dient dazu, allgemeine Kenntnisse über die allgemeine Aktualisierungsbereitschaft zu erlangen. Der Bericht enthält Befunde innerhalb von Problemkategorien, die behoben werden müssen, um ein erfolgreiches Upgrade auf AEM 6.5 LTS sicherzustellen.

Der LTS Analyzer-Bericht zu AEM 6.5 umfasst die folgenden Kategorien:

* Anwendungsfunktionalität, die überarbeitet werden muss
* Repository-Elemente, die an einen unterstützten Speicherort verschoben werden müssen
* Konfigurationsprobleme
* Funktionen von AEM 6.5, die durch neue Funktionen entfernt wurden oder die derzeit nicht von AEM 6.5 LTS unterstützt werden
* Java- und Guava-API-Nutzung entfernen

Weitere Informationen zu den Kategorien sowie möglichen Auswirkungen und Lösungen in Verbindung mit diesen Kategorien erhalten Sie über Links im LTS Analyzer-Bericht zu AEM 6.5.

## Verfügbarkeit {#analyzer-availability}

Der AEM Analyzer kann als ZIP-Datei vom [Software Distribution-Portal) heruntergeladen ](https://experience.adobe.com/#/downloads/content/software-distribution/de/aem.html). Sie können das Paket über [Package Manager](/help/sites-administering/package-manager.md) auf Ihrer AEM-Quellinstanz installieren.

## Wichtige Überlegungen zur Verwendung von AEM Analyzer {#important-considerations-for-using-aem-analyzer}

Im folgenden Abschnitt finden Sie wichtige Überlegungen zur Ausführung von AEM Analyzer:

* Der Analyzer-Bericht wird mit der Ausgabe des AEM-Musterdetektors erstellt. Die von Analyzer verwendete Version des Musterdetektors ist im Installationspaket von AEM Analyzer enthalten
* AEM Analyzer kann nur vom Benutzer **Admin** oder einem Benutzer in der Gruppe **Administratoren** ausgeführt werden
* Analyzer wird auf AEM-Instanzen mit Version 6.5 und höher unterstützt.

>[!NOTE]
>
>Um Auswirkungen auf geschäftskritische Instanzen zu vermeiden, wird empfohlen, AEM Analyzer in einer Staging-Umgebung auszuführen, die der Produktions-Umgebung im Hinblick auf Anpassungen, Konfigurationen, Inhalte und Anwenderprogrammen möglichst nahekommt. Alternativ kann BPA in einem Klon der Autoren-Produktionsumgebung ausgeführt werden.

* Die Erstellung von AEM Analyzer-Berichtsinhalten kann viel Zeit in Anspruch nehmen, von mehreren Minuten bis zu einigen Stunden. Der erforderliche Zeitraum hängt stark von der Größe und Art des AEM-Repository-Inhalts, der AEM-Version und anderen Faktoren ab
* Aufgrund der erheblichen Zeit, die möglicherweise zum Generieren des Berichtsinhalts erforderlich ist, wird dieser von einem Hintergrundprozess generiert und in einem Cache gespeichert. Der Bericht sollte relativ schnell angezeigt und heruntergeladen werden, da er den Inhalts-Cache nutzt, bis dieser abläuft oder der Bericht explizit aktualisiert wird. Bei der Erstellung von Berichtsinhalten können Sie die Browser-Registerkarte schließen und zu einem späteren Zeitpunkt zurückkehren, um den Bericht anzuzeigen, sobald seine Inhalte im Cache verfügbar sind.

## Anzeigen des AEM Analyzer-Berichts {#viewing-the-aem-analyzer-report}

Gehen Sie wie folgt vor, um den AEM Analyzer-Bericht anzuzeigen:

1. Wählen Sie Adobe Experience Manager aus und navigieren Sie **Tools > Vorgänge > 6.5 LTS Modernizer**

   ![Anzeigen des Analyzer-Berichts 1](/help/sites-deploying/assets/view-analyzer-report-1.png)

1. Klicken Sie auf **AEM 6.5 LTS Analyzer**, um ihn zu öffnen

   ![Anzeigen des Analyzer-Berichts 2](/help/sites-deploying/assets/view-analyzer-report-2.png)

1. Klicken Sie auf **Bericht erstellen**, um AEM Analyzer auszuführen

   ![Anzeigen des Analyzer-Berichts 3](/help/sites-deploying/assets/view-analyzer-report-3.png)

1. Während AEM Analyzer den Bericht generiert, können Sie den Fortschritt des Tools auf dem Bildschirm sehen. Der Fortschritt wird als abgeschlossener Prozentsatz angezeigt. Außerdem werden die Anzahl der analysierten Elemente und die Anzahl der Ergebnisse angezeigt

   ![Anzeigen des Analyzer-Berichts 4](/help/sites-deploying/assets/view-analyzer-report-4.png)

1. Nachdem der LTS Analyzer-Bericht in 6.5 generiert wurde, wird eine Zusammenfassung und die Anzahl der Ergebnisse in einem tabellarischen Format angezeigt, sortiert nach Art des Ergebnisses und Wichtigkeitsstufe. Um weitere Details zu einer bestimmten Suche zu erhalten, können Sie auf die Zahl klicken, die dem Typ der Suche in der Tabelle entspricht

   ![Anzeigen des Analyzer-Berichts 5](/help/sites-deploying/assets/view-analyzer-report-5.png)

1. Sie haben die Möglichkeit, den Bericht in einem kommagetrennten Format (CSV) herunterzuladen, indem Sie auf **In CSV exportieren** klicken. Sie können Analyzer zwingen, seinen Cache zu leeren und den Bericht neu zu generieren, indem Sie auf **Bericht aktualisieren** klicken. Wenn der Cache abläuft, müssen Sie den Bericht neu generieren.

## Interpretieren des AEM Analyzer-Berichts {#interpreting-the-aem-analyzer-report}

Wenn das 6.5 LTS Analyzer-Tool in der AEM-Instanz ausgeführt wird, wird der Bericht als Ergebnis im Toolfenster angezeigt.

Das Format des Berichts lautet:

* **Berichtsübersicht**: Informationen zum Bericht selbst, einschließlich der Folgenden:

   * **Berichtszeit**: Zeitpunkt, zu dem die Berichtsinhalte generiert und erstmals bereitgestellt wurden
   * **Ablaufzeit**: Wann der Zwischenspeicher für Berichtsinhalte abläuft
   * **Generierungszeitraum**: Der Zeitraum, in dem der Bericht generiert wurde
   * **Anzahl der Ergebnisse**: Die Gesamtzahl der im Bericht enthaltenen Ergebnisse

* **Systemübersicht**: Informationen zum AEM-System, auf dem der Analyzer ausgeführt wurde
* **Suchen von Kategorien**: Mehrere Abschnitte, die jeweils eine oder mehrere Ergebnisse derselben Kategorie behandeln. Jeder Abschnitt enthält Folgendes: Name der Kategorie, Untertypen, Anzahl und Wichtigkeit der Ergebnisse, Zusammenfassung, Link zur Dokumentation der Kategorien und individuelle Suchinformationen.

  ![Analyzer-Bericht - Zusammenfassung](/help/sites-deploying/assets/analyzer-report-summary.png)

  Jedem Ergebnis wird eine Wichtigkeitsstufe zugewiesen, um eine ungefähre Priorität für das Handeln anzugeben.

>[!NOTE]
>
>Weitere Informationen zu den einzelnen Kategorien finden Sie unter [Musterdetektorkategorien](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/aso).

Um die Wichtigkeitsstufen zu verstehen, folgen Sie der folgenden Tabelle:

| Wichtigkeit | Beschreibung |
|---|---|
| INFO | Diese Ergebnisse werden zu Informationszwecken bereitgestellt. |
| ADVISORY | Diese Ergebnisse stellen möglicherweise ein Problem bei der Aktualisierung dar. Weitere Untersuchungen werden empfohlen. |
| CRITICAL | Diese Ergebnisse stellen wahrscheinlich ein Problem bei der Aktualisierung dar, das behoben werden muss, um Funktionsverlust oder Leistungseinbußen zu vermeiden. |

## Interpretieren des LTS Analyzer-CSV-Berichts zu AEM 6.5 {#interpreting-the-aem-65lts-analyzer-report}

Wenn Sie in Ihrer AEM-Instanz auf **CSV**-Option klicken, wird das CSV-Format des Analyzer-Berichts aus dem Inhalts-Cache erstellt und an Ihren Browser zurückgegeben. Abhängig von Ihren Browser-Einstellungen wird dieser Bericht automatisch als Datei mit dem Standardnamen `report.csv` heruntergeladen.

Wenn der Cache abgelaufen ist, wird der Bericht erneut generiert, bevor die CSV-Datei erstellt und heruntergeladen wird.

Das CSV-Format des Berichts enthält Informationen, die aus der Mustererkennungsausgabe generiert wurden und nach Kategorie, Untertyp und Wichtigkeitsstufe sortiert und organisiert sind. Sein Format eignet sich zum Anzeigen und Bearbeiten in einem Programm wie Microsoft Excel. Es ist beabsichtigt, alle Ergebnisinformationen in einem wiederholbaren Format bereitzustellen, das beim Vergleich von Berichten im Zeitverlauf hilfreich sein kann, um den Fortschritt zu messen.

Die Spalten des Berichts im CSV-Format sind:

* **code**: der Code der Kategorie
* **type**: der Name der Kategorie
* **subtype**: der Untertyp der Kategorie
* **importance**: die Wichtigkeitsstufe
* **identifier**: die primäre Kennung des Ergebnisses
* **message**: die für das Ergebnis angegebene Meldung
* **context**: eine JSON-Zeichenfolge von Ergebnisdaten

Der Wert &quot;`\N`&quot; in einer Spalte für einen einzelnen Fund zeigt an, dass keine Daten bereitgestellt wurden.

## HTTP-Schnittstelle {#http-interface}

Der 6.5 LTS Analyzer bietet eine HTTP-Schnittstelle, die als Alternative zu seiner Benutzeroberfläche in AEM verwendet werden kann. Die Benutzeroberfläche unterstützt sowohl `HEAD` als auch `GET`. Er kann verwendet werden, um den Analyzer-Bericht zu generieren und ihn in einem von drei Formaten zurückzugeben: JSON, CSV und tabulatorgetrennte Werte (TSV).

Die folgenden URLs stehen für den HTTP-Zugriff zur Verfügung, wobei `<host>` der Host-Name neben dem Port des Servers ist, auf dem der Analyzer installiert ist:

* `http://<host>/apps/aem66-analyzer/analysis/report.json` für das JSON-Format
* `http://<host>/apps/aem66-analyzer/analysis/report.csv` für das CSV-Format
* `http://<host>/apps/aem66-analyzer/analysis/report.tsv` für das TSV-Format

### Ausführen einer HTTP-Anfrage {#executing-an-http-request}

Eine einfache Möglichkeit, eine HTTP-Anfrage auszuführen, besteht darin, eine Registerkarte im selben Browser zu öffnen, in dem Sie sich bereits als Admin bei AEM angemeldet haben. Sie können die URL in der Browser-Registerkarte eingeben und die Ergebnisse vom Browser anzeigen oder herunterladen lassen.

Sie können auch ein Befehlszeilen-Tool wie `curl` oder `wget` oder eine beliebige HTTP-Client-Anwendung verwenden. Wenn Sie keine Browser-Registerkarte mit einer authentifizierten Sitzung verwenden, müssen Sie als Teil des Kommentars einen Administrator-Benutzernamen und ein Kennwort angeben.

Im Folgenden finden Sie ein Beispiel dafür, wie dies möglich ist:

```shell
curl -u admin:admin 'http://localhost:4502/apps/aem66-analyzer/analysis/report.csv' > report.csv.
```

## Anpassen der Cache-Lebensdauer {#adjusting-the-cache-lifetime}

Die standardmäßige Gültigkeitsdauer des AEM 6.5 LTS Analyzer-Caches beträgt 24 Stunden. Mit der Option zum Aktualisieren eines Berichts und zum erneuten Generieren des Caches sowohl in der AEM-Instanz als auch in der HTTP-Schnittstelle ist dieser Standardwert wahrscheinlich für die meisten Benutzenden von AEM 6.5 LTS Analyzer geeignet. Wenn die Zeit für die Berichterstellung für Ihre AEM-Instanz besonders lang ist, möchten Sie möglicherweise die Cache-Lebensdauer anpassen, um das erneute Generieren des Berichts zu minimieren.

Der Wert der Cache-Lebensdauer wird als `maxCacheAge` Eigenschaft auf dem folgenden Repository-Knoten gespeichert:

```
/apps/aem66-analyzer/content/modernizer/analyzer/jcr:content
```

Der Wert dieser Eigenschaft ist die Cache-Lebensdauer in Sekunden. Ein Administrator kann die Cache-Lebensdauer mit CRX/DE Lite anpassen.

## Verwenden von Content Transformer {#using-content-transformer}

### Verfügbarkeit {#content-transformer-availability}

Der Content Transformer ist im Lieferumfang des AEM 6.5 LTS Analyzer enthalten und kann als ZIP-Datei vom Software Distribution Portal heruntergeladen werden.

### Wichtige Überlegungen zur Verwendung von Content Transformer {#important-considerations-for-using-content-transformer}

Im folgenden Abschnitt finden Sie wichtige Überlegungen zur Verwendung des Content Transformer (CT):

* Um den Inhaltstransformer verwenden zu können, müssen Sie zunächst AEM Analyzer in Ihrer AEM-Umgebung ausführen
* Obwohl Sie den Content Transformer in Ihrer Produktionsumgebung ausführen können, wird empfohlen, den Content Transformer in einem Klon Ihrer Produktionsumgebung auszuführen. Darüber hinaus müssen Sie sicherstellen, dass der AEM Analyzer und der CT in derselben Umgebung ausgeführt werden
* Sie müssen Administrator der Umgebung sein, in der Sie den Content Transformer ausführen möchten
* Bei einem Entfernen-Vorgang, der den Quellinhalt ändern kann, wird vor der Transformation standardmäßig ein Backup-Paket der Quellpfade unter `/etc/packages/modernizer-content-transformation` erstellt. Obwohl das Dialogfeld für den Entfernen-Vorgang eine Option zum Deaktivieren/Aktivieren der Erstellung des Sicherungspakets enthält, wird dringend empfohlen, immer die Option Paketerstellung aktivieren auszuwählen
* Jede Seite im Content Transformer ist so konfiguriert, dass maximal 50 Ergebnisse aufgelistet werden. Somit können maximal 50 Funde gleichzeitig transformiert werden. Dies geschieht, um eine zeitnahe Antwort in der Benutzeroberfläche zu ermöglichen.

### Öffnen von Content Transformer {#opening-the-content-transformer}

1. Melden Sie sich bei der AEM-Quellinstanz als Administrator an und gehen Sie zur Startseite unter *https://host:port/aem/start.htm*
1. Navigieren Sie zu **Tools > Vorgänge > 6.5 LTS Modernizer**

   ![Öffnen von Content Transformer 1](/help/sites-deploying/assets/opening-content-transformer-1.png)

1. Klicken Sie auf die Karte **Content Transformer for 6.5 LTS Analyzer Report**.

   ![Öffnen von Content Transformer 2](/help/sites-deploying/assets/opening-content-transformer-2.png)

1. Wenn der Analyzer-Bericht nicht generiert wird, wird auf **Seite „Inhalt**&quot; **Kein Bericht** angezeigt. Dieselbe **Kein Bericht** wird auch angezeigt, wenn alle inhaltsbezogenen Ergebnisse entfernt wurden

   ![Öffnen von Content Transformer 3](/help/sites-deploying/assets/opening-content-transformer-3.png)

1. Nachfolgend finden Sie ein Beispiel dafür, wie die Seite Übersicht über Content Transformer aussieht, wenn die Erstellung des AEM Analyzer-Berichts erfolgreich war und Probleme mit dem Inhalt aufgetreten sind.

Die für den AEM Analyzer-Bericht verbleibende Gültigkeitsdauer wird in der Seitenleiste angezeigt. Es wird empfohlen, Content Transformer mit dem neuesten AEM Analyzer-Bericht auszuführen, um zu vermeiden, dass inhaltsbezogene Ergebnisse fehlen

![Öffnen von Content Transformer 4](/help/sites-deploying/assets/opening-content-transformer-4.png)

1. Sie können die Probleme nach Muster-Code, Untertyp, Wichtigkeit und Source filtern

   ![Öffnen von Content Transformer 5](/help/sites-deploying/assets/opening-content-transformer-5.png)

### Pfade werden entfernt {#removing-paths}

1. Sie können alle oder bestimmte Probleme auswählen und auf &quot;**&quot;**, um sie zu beheben

   ![Entfernen von Pfaden 1](/help/sites-deploying/assets/removing-paths-1.png)

   >[!NOTE]
   >Beim Entfernen wird vor der Transformation standardmäßig ein Backup-Paket der Quellpfade unter `/etc/packages/modernizer-content-transformation` erstellt. Obwohl das Dialogfeld für den Entfernen-Vorgang eine Option zum Deaktivieren/Aktivieren der Erstellung des Sicherungspakets enthält, wird dringend empfohlen, immer die Option Paketerstellung aktivieren auszuwählen.

   ![Entfernen von Pfaden 2](/help/sites-deploying/assets/removing-paths-2.png)

1. Ein Beispiel für ein Backup-Paket, das für den Entfernungsvorgang der Pfade erstellt wurde, ist unten dargestellt. Sie können auf **Installieren** klicken, um die Quellpfade zurückzukehren

   ![Entfernen von Pfaden 3](/help/sites-deploying/assets/removing-paths-3.png)

   >[!CAUTION]
   >
   >Löschen Sie `/etc/packages/modernizer-content-transformation` nicht, da dies der Speicherort ist, an dem sich die Backup-Pakete befinden. Sie können diesen Speicherort löschen, um die Größe des Repositorys nur dann zu reduzieren, wenn Sie sicher sind, dass Sie diese Pakete nicht mehr benötigen.

1. Optional können Sie ausgewählte Inhaltsergebnisse für die zukünftige Verwendung verpacken. Wählen Sie dazu die gewünschten Ergebnisse aus und klicken Sie dann oben links **Paket**. Geben Sie einen Paketnamen ein, wählen Sie einen Paketpfad aus und klicken Sie auf die Schaltfläche **Paket**, um den Vorgang abzuschließen.

   ![Entfernen von Pfaden 3](/help/sites-deploying/assets/removing-paths-4.png)

### Bekannte Probleme {#known-issues}

* Manchmal wird beim Entfernen-Vorgang möglicherweise die Benachrichtigung angezeigt: *„Einige Pfade wurden nicht erfolgreich entfernt. Bitte die Protokolle überprüfen und erneut versuchen.*&quot;. Wenn die Pfade jedoch tatsächlich entfernt wurden, können Sie diese Nachricht ignorieren
* Ebenso kann der Paketvorgang mit folgendem Fehler fehlschlagen: „Fehler *beim Ausführen des gewünschten Vorgangs, bitte die Protokolle überprüfen und erneut versuchen.*&quot;. Dies ist wahrscheinlich auf den Ablauf der Sitzung zurückzuführen. In solchen Fällen sollte das Problem durch Wiederholen des Vorgangs behoben werden.
