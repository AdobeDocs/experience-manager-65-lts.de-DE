---
title: Bereitstellen und Verwalten
description: Erfahren Sie, wie Sie mit der AEM-Installation beginnen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: 4a2ada26-b859-4a32-9ab0-2d4c2b695245
source-git-commit: 929a2175449a371ecf81226fedb98a0c5c6d7166
workflow-type: tm+mt
source-wordcount: '1363'
ht-degree: 93%

---

# Bereitstellen und Verwalten {#deploying-and-maintaining}

Inhalt dieser Seite:

* [Grundlegende Konzepte](#basic-concepts)

   * [Was ist AEM?](#what-is-aem)
   * [Typische Bereitstellungen](#typical-deployment-scenarios)

      * [On-Premise](#on-premise)
      * [Managed Services mit Cloud Manager](#managed-services-using-cloud-manager)

* [Erste Schritte](#getting-started)

   * [Voraussetzungen](#prerequisites)
   * [Abrufen der Software](#getting-the-software)
   * [Standardmäßige lokale Installation](#default-local-install)
   * [Installation von Erstellungs- und Veröffentlichungsinstanzen](#author-and-publish-installs)
   * [Entpacktes Installationsverzeichnis](#unpacked-install-directory)
   * [Starten und Anhalten](#starting-and-stopping)

Nachdem Sie sich mit diesen Grundlagen vertraut gemacht haben, finden Sie auf den folgenden Unterseiten komplexere und ausführlichere Informationen:

* [Technische Anforderungen](/help/sites-deploying/technical-requirements.md)
* [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md)
* [Benutzerdefinierte Standalone-Installation](/help/sites-deploying/custom-standalone-install.md)
* [Anwendungsserver-Installation](/help/sites-deploying/application-server-install.md)
* [Start und Stopp über die Befehlszeile](/help/sites-deploying/command-line-start-and-stop.md)
* [Konfiguration](/help/sites-deploying/configuring.md)
* [Aktualisieren auf AEM 6.5 LTS](/help/sites-deploying/upgrade.md)
* [Artikel mit Anleitungen für die Konfiguration](/help/sites-deploying/ht-deploy.md)
* [Web-Konsole](/help/sites-deploying/web-console.md)
* [Fehlerbehebung bei Replikationsproblemen](/help/sites-deploying/troubleshoot-rep.md)
* [Best Practices](/help/sites-deploying/best-practices.md)
* [Einführung in die AEM-Plattform](/help/sites-deploying/platform.md)

## Grundlegende Konzepte {#basic-concepts}

### Was ist AEM? {#what-is-aem}

Adobe Experience Manager ist ein Web-basiertes Client-Server-System für das Erstellen, Verwalten und Bereitstellen von kommerziellen Websites und zugehörigen Services. Es kombiniert mehrere Funktionen auf Infrastrukturebene und Anwendungsebene in einem einzelnen integrierten Paket.

Auf Infrastrukturebene bietet AEM Folgendes:

* **Web-Anwendungs-Server**: AEM kann im eigenständigen Modus (es umfasst einen integrierten Jetty-Webserver) oder als Web-Anwendung innerhalb eines Anwendungs-Servers eines Drittanbieters bereitgestellt werden.
* **Web-Anwendungs-Framework**: AEM beinhaltet das Sling-Web-Anwendungs-Framework, das das Schreiben von RESTful-Web-Anwendungen vereinfacht.
* **Content-Repository**: AEM enthält ein Java Content™ Repository (JCR), eine Art hierarchische Datenbank, die speziell für unstrukturierte und teilstrukturierte Daten entwickelt wurde. Das Repository speichert nicht nur den für die Benutzenden sichtbaren Inhalt, sondern auch den gesamten Code, die Vorlagen und die internen Daten, die von der Anwendung verwendet werden.

Auf dieser Grundlage bietet AEM einige Funktionen auf Anwendungsebene für die Verwaltung von:

* **Websites**
* **Digitalen Veröffentlichungen**
* **Formulare und Dokumente**
* **Digitale Assets**

Schließlich können Kundinnen und Kunden diese Bausteine auf Infrastruktur- und Anwendungsebene nutzen, um individuelle Lösungen zu erstellen, indem sie eigene Anwendungen entwickeln.

Der AEM-Server ist **Java-basiert** und kann auf den meisten Betriebssystemen ausgeführt werden, die diese Plattform unterstützen. Die gesamte Client-Interaktion mit AEM erfolgt über einen **Webbrowser**.

>[!NOTE]
>
>Die Funktion „Adaptive Forms&quot;, die in AEM 6.5 LTS QuickStart verfügbar ist, ist nur für Explorations- und Auswertungszwecke konzipiert. Für die Verwendung in der Produktion muss eine gültige Lizenz für AEM Forms erworben werden, da für die Funktion „Adaptive Formulare“ eine Lizenzierung erforderlich ist.

### Typische Bereitstellungsszenarien {#typical-deployment-scenarios}

In der Terminologie von AEM entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server ausgeführt wird. AEM-Installationen betreffen in der Regel mindestens zwei Instanzen, die normalerweise auf separaten Computern ausgeführt werden:

* **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
* **Publish**: Eine AEM-Instanz, die den Inhalt veröffentlicht.

Diese Instanzen sind hinsichtlich der installierten Software identisch. Sie unterscheiden sich nur in Bezug auf ihre Konfiguration. Darüber hinaus verwenden die meisten Installationen einen Dispatcher:

* **Dispatcher**: Ein mit dem AEM-Dispatcher-Modul angereicherter statischer Webserver (Apache httpd, Microsoft® IIS).  Er speichert die durch die Veröffentlichungsinstanz generierten Web-Seiten zwischen, um die Leistung zu verbessern.

Es gibt viele erweiterte Optionen und Ausarbeitungen dieses Setups, aber das grundlegende Muster von Author, Publish und Dispatcher bildet den Kern der meisten Bereitstellungen. Zunächst konzentrieren wir uns auf ein einfaches Setup.  Die Erläuterung der erweiterten Bereitstellungsoptionen folgt.

In den folgenden Abschnitten werden beide Szenarien beschrieben:

* **On-Premise**: AEM in Ihrer Unternehmensumgebung bereitgestellt und verwaltet.

* **Managed Services – Cloud-Manager für Adobe Experience Manager**: AEM von Adobe Managed Services bereitgestellt und verwaltet.

### On-Premise {#on-premise}

Sie können AEM auf Servern in Ihrer Unternehmensumgebung installieren. Typische Installationsinstanzen umfassen: Bereitstellungs-, Test- und Veröffentlichungsumgebungen. Unter [Erste Schritte](#getting-started) finden Sie grundlegende Informationen darüber, wie Sie die AEM-Software erhalten, um sie lokal zu installieren.

<!-- To learn more about the typical on-premises deployments, see [Recommended Deployments](/help/sites-deploying/recommended-deploys.md). -->

### Managed Services mit Cloud Manager {#managed-services-using-cloud-manager}

<i>Wird in Kürze bekannt gegeben.</i>

## Erste Schritte {#getting-started}

### Voraussetzungen {#prerequisites}

Während Produktionsinstanzen für gewöhnlich auf dedizierten Computern ausgeführt werden, auf denen wiederum offiziell unterstützte Betriebssysteme ausgeführt werden (siehe [Technische Anforderungen](/help/sites-deploying/technical-requirements.md)), kann der Experience Manager-Server tatsächlich auf jedem System ausgeführt werden, das [**Java™ Standard Edition 17**](https://www.oracle.com/java/technologies/downloads/#java17) unterstützt.

Um sich mit AEM vertraut zu machen bzw. um die Entwicklung auf AEM vorzunehmen, wird häufig eine auf Ihrem lokalen Computer installierte Instanz verwendet, auf der Apple OS X oder Desktop-Versionen von Microsoft® Windows oder Linux® ausgeführt werden.

Client-seitig arbeitet AEM mit allen modernen Browsern (**Microsoft® Edge**, **Chrome 51+**, **Firefox 47+**, **Safari 8+**) sowohl auf Desktop- als auch auf Tablet-Betriebssystemen. Details finden Sie unter [Unterstützte Clientplattformen](/help/sites-deploying/technical-requirements.md#supported-client-platforms).

### Abrufen der Software {#getting-the-software}

Kunden mit einem gültigen Wartungs- und Supportvertrag sollten eine E-Mail-Benachrichtigung mit einem Code erhalten haben und in der Lage sein, AEM über die [**Adobe-Lizenzierungswebsite**](https://licensing.adobe.com/) herunterzuladen. Geschäftspartner können den Downloadzugriff über [**spphelp@adobe.com**](mailto:spphelp@adobe.com) anfordern.

Das AEM-Software-Paket steht in zwei Formen zur Verfügung:

* **CQ AEM 6.5 LTS.jar** Eine eigenständige ausführbare *jar*-Datei, die alles enthält, was Sie zum Ausführen benötigen.

* **CQ AEM 6.5 LTS WAR:** Eine *war*-Datei zur Bereitstellung auf einem Anwendungsserver eines Drittanbieters.

Im folgenden Abschnitt wird die **eigenständige Installation** beschrieben. Weitere Informationen zum Installieren von AEM auf einem Anwendungs-Server finden Sie unter [Anwendungs-Server-Installation](/help/sites-deploying/application-server-install.md).

### Standardmäßige lokale Installation {#default-local-install}

1. Erstellen Sie auf Ihrem lokalen Computer ein Installationsverzeichnis. Beispiel:

   UNIX®-Installationsspeicherort: **/opt/aem**

   Windows-Installationsspeicherort: **`C:\Program Files\aem`**

   Ebenso ist es üblich, Beispielinstanzen in einem Ordner direkt auf dem Desktop zu installieren. In jedem Fall wird bei Adobe dieser Speicherort meist wie folgt bezeichnet:

   `<aem-install>`

   *Der Pfad des Dateiverzeichnisses darf nur aus US-ASCII-Zeichen bestehen.*

1. Platzieren Sie die **jar**- und **license**-Dateien in diesem Verzeichnis:

   ```shell
   <aem-install>/
       <aem-65-lts>.jar
       license.properties
   ```

   Wenn Sie keine Datei `license.properties` bereitstellen, leitet AEM Ihren Browser beim Start zu einem **Begrüßungsbildschirm** um, wo Sie Ihren Lizenzschlüssel eingeben können. Sie müssen einen gültigen Lizenzschlüssel von Adobe anfordern, wenn Sie noch nicht über einen verfügen.

1. Doppelklicken Sie zum Starten der Instanz in einer GUI-Umgebung einfach auf die Datei **`<aem-65-lts>.jar`**.

   Alternativ können Sie AEM über die Befehlszeile starten:

   ```shell
       java -Xmx1024M -jar <aem-65-lts>.jar
   ```

AEM braucht ein paar Minuten, um die JAR-Datei zu entpacken, sich selbst zu installieren und zu starten. Das obige Verfahren führt zu:

* einer **AEM author**-Instanz,
* die auf **localhost**
* auf Port **4502** ausgeführt wird

Lassen Sie Ihren Browser für den Zugriff auf die Instanz auf die folgende URL verweisen:

**`https://localhost:4502`**

Das Ergebnis in der Erstellungsinstanz wird automatisch so konfiguriert, dass eine Verbindung zu einer **Veröffentlichungsinstanz** auf **`localhost:4503`** hergestellt wird.

### Installation von Erstellungs- und Veröffentlichungsinstanzen {#author-and-publish-installs}

Die Standardinstallation (eine **author**-Instanz auf **`localhost:4502`**) kann einfach durch das Umbenennen der `jar`-Datei geändert werden, bevor sie das erste Mal gestartet wird. Das Benennungsmuster lautet:

**`cq-<instance-type>-p<port-number>.jar`**

So führt beispielsweise das Umbenennen der Datei zu

**`cq-author-p4502.jar`**

und das Starten dieser Datei zu einer Autoreninstanz, die auf **`localhost:4502`** ausgeführt wird.

Ähnlich verhält es sich beim Umbenennen und Starten der Datei

**`cq-publish-p4503.jar`**

Dies führt zu einer Veröffentlichungsinstanz, die auf **`localhost:4503`** ausgeführt wird.

Diese zwei Instanzen würden Sie beispielsweise installieren in:

`<aem-install>/author`und

**`<aem-install>/publish`**

Weitere Informationen über das Anpassen Ihrer Installation finden Sie unter:

* [Benutzerdefinierte Standalone-Installation](/help/sites-deploying/custom-standalone-install.md)
<!-- * [Run Modes](/help/sites-deploying/configure-runmodes.md) -->

### Entpacktes Installationsverzeichnis {#unpacked-install-directory}

Wenn die JAR-Datei für den Schnellstart erstmals gestartet wird, entpackt sie sich selbst im selben Verzeichnis unter einem neuen Unterverzeichnis mit dem Namen `crx-quickstart`. Sie müssen über Folgendes verfügen:

```xml
<aem-install>/
    license.properties
    <aem-65-lts>.jar
    crx-quickstart/
        app/
        bin/
        conf/
        launchpad/
        logs/
        metrics/
        monitoring/
        opt/
        repository/
        threaddumps/
        eula-de_DE.html
        eula-en_US.html
        eula-fr_FR.html
        eula-ja_JP.html
        readme.txt
```

Wenn die Instanz über die Benutzeroberfläche installiert wurde, werden automatisch ein Browser-Fenster und ein Desktop-Anwendungsfenster geöffnet, in denen der Host und Port der Instanz sowie ein Ein-/Aus-Schalter angezeigt werden:

![Startbildschirm](assets/screen_shot_.png)

### Starten und Anhalten {#starting-and-stopping}

Nachdem sich AEM selbst entpackt und erstmals gestartet hat, lässt sich die Instanz durch einfaches Doppelklicken auf die JAR-Datei im Installationsverzeichnis starten. Sie wird dadurch nicht erneut installiert.

Um die Instanz über die grafische Benutzeroberfläche zu stoppen, klicken Sie einfach auf den **Ein-/Aus**-Schalter im Fenster der Desktop-Anwendung.

Sie können AEM auch über die Befehlszeile anhalten und starten. Angenommen, Sie haben die Instanz bereits erstmalig installiert, dann befinden sich die **Befehlszeilenskripte** hier:

**`<aem-install>/crx-quickstart/bin/`**

Dieser Ordner enthält die folgenden Unix®-Bash-Shell-Skripte:

* **`start`**: Startet die Instanz
* `stop`: Hält die Instanz an
* **`status`**: Meldet den Status der Instanz
* **`quickstart`**: Wird bei Bedarf zum Konfigurieren der Startinformationen verwendet

Es stehen auch entsprechende **`bat`**-Dateien für Windows zur Verfügung. Detaillierte Informationen finden Sie in:

* [Start und Stopp über die Befehlszeile](/help/sites-deploying/command-line-start-and-stop.md)

AEM startet und leitet Ihren Webbrowser automatisch zur entsprechenden Seite um. Für gewöhnlich handelt es sich um die Anmeldeseite, beispielsweise:

`https://localhost:4502/`

![Anmeldebildschirm](assets/screen_shot_2019-04-08at83533am.png)


Nach der Anmeldung haben Sie Zugriff auf AEM. Weitere Informationen finden Sie je nach Ihrer Rolle hier:

* [Authoring –](/help/sites-authoring/first-steps.md)
* [Verwalten](/help/sites-administering/home.md)
* [Entwickeln](/help/sites-developing/getting-started.md)
* [Verwaltung](/help/managing/best-practices.md)

## Erweiterte Bereitstellung {#advanced-deployment}

Der obige Abschnitt sollte Ihnen ein gutes Verständnis der Grundlagen zur AEM-Installation vermitteln. Die Installation eines vollständigen Produktionssystems von AEM kann jedoch erheblich komplexer sein. In den folgenden Unterseiten wird die erweiterte Installation vollständig abgedeckt:

* [Technische Anforderungen](/help/sites-deploying/technical-requirements.md)
* [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md)
* [Benutzerdefinierte Standalone-Installation](/help/sites-deploying/custom-standalone-install.md)
* [Anwendungsserver-Installation](/help/sites-deploying/application-server-install.md)
* [Start und Stopp über die Befehlszeile](/help/sites-deploying/command-line-start-and-stop.md)
* [Konfiguration](/help/sites-deploying/configuring.md)
* [Aktualisieren auf AEM 6.5 LTS](/help/sites-deploying/upgrade.md)
* [Artikel mit Anleitungen für die Konfiguration](/help/sites-deploying/ht-deploy.md)
* [Web-Konsole](/help/sites-deploying/web-console.md)
* [Fehlerbehebung bei Replikationsproblemen](/help/sites-deploying/troubleshoot-rep.md)
* [Best Practices](/help/sites-deploying/best-practices.md)
* [Einführung in die AEM-Plattform](/help/sites-deploying/platform.md)

