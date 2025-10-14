---
title: Planung von Upgrades
description: Dieser Artikel unterstützt Sie bei der Formulierung von klaren Zielen, Phasen und Arbeitsergebnissen bei der Planung eines Upgrades von AEM.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 3fe5421e-e97e-43c4-b34b-b84bf189a779
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1188'
ht-degree: 61%

---

# Planung von Upgrades {#planning-your-upgrade}

## AEM-Upgrade - Übersicht {#aem-upgrade-overview}

AEM kommt häufig in umfangreichen Bereitstellungen zum Einsatz, die möglicherweise von Millionen von Benutzern genutzt werden. In der Regel werden auf den Instanzen auch benutzerdefinierte Anwendungen bereitgestellt, wodurch die Komplexität weiter erhöht wird. Jedes Upgrade einer solchen Bereitstellung muss deshalb methodisch angegangen werden.

Dieser Leitfaden unterstützt Sie bei der Formulierung von klaren Zielen, Phasen und Ergebnissen bei der Planung des Upgrades. Es konzentriert sich auf die allgemeine Durchführung von Upgrades und Richtlinien. Er gibt einen Überblick über die konkreten Upgrade-Schritte und verweist auf verfügbare technische Ressourcen, falls erforderlich. Es sollte mit den verfügbaren technischen Ressourcen verwendet werden, auf die in dem Dokument verwiesen wird.

Der Upgrade-Prozess für AEM erfordert sorgfältig ausgeführte Planungs-, Analyse- und Durchführungsphasen, für die jeweils wichtige Ergebnisse festgelegt werden müssen.

>[!NOTE]
>
>Das Upgrade auf AEM 6.5 LTS wird von den letzten 6 Service Packs unterstützt

Sie müssen sicherstellen, dass ein unterstütztes Betriebssystem, eine unterstützte Java™-Laufzeitumgebung sowie eine unterstützte httpd- und Dispatcher-Version ausgeführt werden. Weitere Informationen finden Sie unter [Technische Anforderungen für AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md). Das Upgrade dieser Komponenten muss in Ihrem Upgrade-Plan berücksichtigt werden und sollte vor dem Upgrade von AEM stattfinden.

<!-- Alexandru: drafting for now

## Upgrade Scope and Requirements {#upgrade-scope-requirements}

Below you will find a list of areas that are impacted in a typical AEM Upgrade project:

<table>
 <tbody>
  <tr>
   <td><strong>Component</strong></td>
   <td><strong>Impact</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>Operating System</td>
   <td>Uncertain, but subtle effects</td>
   <td>At the time of the AEM upgrade, it may be time to upgrade the operating system as well and this might have some impact.</td>
  </tr>
  <tr>
   <td>Java&trade; Runtime</td>
   <td>Moderate Impact</td>
   <td>AEM 6.3 requires JRE 1.7.x (64 bit) or later. JRE 1.8 is the only version currently supported by Oracle.</td>
  </tr>
  <tr>
   <td>Hardware</td>
   <td>Moderate Impact</td>
   <td>Online Revision Cleanup requires free<br /> disk space equal to 25% of the repository's size and 15% free heap space<br /> to complete successfully. You may need to upgrade your hardware to<br /> ensure sufficient resources for Online Revision Cleanup to fully<br /> run. Also, if upgrading from a version prior to AEM 6, there<br /> may be additional storage requirements.</td>
  </tr>
  <tr>
   <td>Content Repository (CRX or Oak)</td>
   <td>High Impact</td>
   <td>Starting from version 6.1, AEM does not support CRX2, so a migration to<br /> Oak (CRX3) is required if upgrading from an older version. AEM 6.3 has<br /> implemented a new Segment Node Store that also requires a migration. The<br /> crx2oak tool is used for this purpose.</td>
  </tr>
  <tr>
   <td>AEM Components/Content</td>
   <td>Moderate Impact</td>
   <td><code>/libs</code> and <code>/apps</code> are easily handled through the upgrade, but <code>/etc</code> usually requires some manual reapplication of customizations.</td>
  </tr>
  <tr>
   <td>AEM Services</td>
   <td>Low Impact</td>
   <td>Most AEM core services are tested for upgrade. This is an area of low impact.</td>
  </tr>
  <tr>
   <td>Custom Application Services</td>
   <td>Low to High Impact</td>
   <td>Depending on the application and customization, there may be<br /> dependencies on JVM, operating system versions, and some indexing related<br /> changes, as indexes are not generated automatically in Oak.</td>
  </tr>
  <tr>
   <td>Custom Application Content</td>
   <td>Low to High Impact</td>
   <td>Content that will not be handled through the upgrade can be backed up<br /> before the upgrade takes place and then moved back into the repository.<br /> Most content can be handled through the migration tool.</td>
  </tr>
 </tbody>
</table>

It is important to ensure that you are running a supported operating system, Java&trade; runtime, httpd, and Dispatcher version. For more information, see the [AEM 6.5 Technical Requirements page](/help/sites-deploying/technical-requirements.md). Upgrading these components must be accounted for in your project plan and should take place before upgrading AEM. -->

## Upgrade-Phasen {#upgrade-phases}

Die Planung und Durchführung eines AEM-Upgrades ist mit viel Arbeit verbunden. Um den unterschiedlichen Aufwand zu verdeutlichen, der mit diesem Prozess verbunden ist, hat Adobe die Planung und Ausführung in verschiedene Phasen unterteilt. In den folgenden Abschnitten führt jede Phase zu einem Ergebnis, das häufig in einer zukünftigen Phase des Upgrades verwendet wird.

<!-- Alexandru:drafting for now

### Planning for Author Training {#planning-for-author-training}

With any new release, there are potential changes to the UI and user workflows that may be introduced. Also, new releases introduce new features that may be beneficial for the business to use. Adobe recommends reviewing the functional changes that have been introduced and organizing a plan to train your users on using them effectively.

![unu_cropped](assets/unu_cropped.png)

New features in AEM 6.5 can be found in [the AEM section of adobe.com](/help/release-notes/release-notes.md). Make sure to note any changes to UIs or product features that are commonly used in your organization. As you look through the new features, also take note of any that can be of value to your organization. After looking through what has changed in AEM 6.5, develop a training plan for your authors. This could involve using freely available resources like the help feature videos or formal training offered through [Adobe Digital Learning Services](https://learning.adobe.com/). -->

### Erstellen eines Testplans {#creating-a-test-plan}

Jede Kundenimplementierung von AEM ist einzigartig und auf die Geschäftsanforderungen des Unternehmens zugeschnitten. Daher ist es wichtig, alle am System vorgenommenen Anpassungen zu bestimmen, damit sie in einen Testplan aufgenommen werden können.

Die Produktionsumgebung muss exakt dupliziert und nach dem Upgrade getestet werden, um sicherzustellen, dass alle Anwendungen und benutzerdefinierter Code weiterhin wie gewünscht ausgeführt werden. Sie müssen alle Anpassungen rückgängig machen und Leistungs-, Last- und Sicherheitstests durchführen. Beziehen Sie beim Organisieren des Testplans neben den vorkonfigurierten Benutzeroberflächen und Workflows, die für Ihre täglichen Betriebsabläufe genutzt werden, alle am System vorgenommenen Anpassungen in den Plan mit ein. Hierzu gehören möglicherweise benutzerdefinierte OSGi-Dienste und -Servlets, Integrationen mit Adobe Experience Cloud, Integrationen mit Drittanbieteranwendungen über AEM-Connectoren, benutzerdefinierte Drittanbieterintegrationen, benutzerdefinierte Komponenten und Vorlagen, benutzerdefinierte Benutzeroberflächen-Überlagerungen in AEM und benutzerdefinierte Workflows. Darüber hinaus sollten benutzerdefinierte Abfragen weiterhin getestet werden, um sicherzustellen, dass ihre Indizes nach dem Upgrade weiterhin effektiv funktionieren.

### Bewertung der Komplexität des Upgrades {#assessing-upgrade-complexity}

Aufgrund der großen Vielfalt an Anpassungen, die Adobe-Kunden an ihren AEM-Umgebungen vornehmen, ist es wichtig, im Voraus den gesamten Aufwand zu bestimmen, der bei einem Upgrade zu erwarten ist. [AEM Analyzer für AEM 6.5 LTS](/help/sites-deploying/aem-analyzer.md) kann Ihnen bei der Bewertung der Komplexität des Upgrades helfen.

Der [AEM Analyer für AEM 6.5 LTS](/help/sites-deploying/pattern-detector.md) liefert Ihnen eine recht genaue Schätzung dessen, was Sie während eines Upgrades in den meisten Fällen erwarten können. Für komplexere Anpassungen und Bereitstellungen, in denen inkompatible Änderungen vorhanden sind, können Sie jedoch eine Entwicklungsinstanz auf AEM 6.5 LTS upgraden. Eine Anleitung finden Sie unter [&#x200B; eines In-Place-Upgrades](/help/sites-deploying/in-place-upgrade.md). Führen Sie nach der Aktualisierung eine Reihe Feuerproben der hohen Stufe für die Umgebung durch. Ziel dieser Übung ist es nicht, den Testfallbestand vollständig abzuschließen und eine formelle Liste von Fehlern zu erstellen, sondern uns eine grobe Schätzung des Arbeitsaufwands für das Upgrade des Codes für die Kompatibilität mit AEM 6.5 LTS zu geben. In Kombination mit dem [AEM Analyzer](/help/sites-deploying/aem-analyzer.md) und den Architekturänderungen, die im vorherigen Abschnitt ermittelt wurden, kann das Projektmanagement-Team eine grobe Schätzung für die Planung des Upgrades erhalten.

### Erstellen des Runbooks für das Upgrade und das Rollback {#building-the-upgrade-and-rollback-runbook}

Obwohl Adobe den Prozess für die Aktualisierung von AEM-Instanzen dokumentiert hat, muss der Ansatz entsprechend dem Netzwerk-Layout, der Bereitstellungsarchitektur und den Anpassungen jeder Kundin und jedes Kunden optimiert und darauf zugeschnitten werden. Aus diesem Grund empfiehlt Ihnen Adobe, die gesamte bereitgestellte Dokumentation zu lesen und sie zu verwenden, um ein upgradespezifisches Runbook mit den spezifischen Upgrade- und Rollback-Verfahren zu erstellen, die Sie in Ihrer Umgebung anwenden werden.

<!--Alexandru:drafting for now

![runbook-diagram](assets/runbook-diagram.png) -->

Unter [Upgrade-Verfahren](/help/sites-deploying/upgrade-procedure.md) finden Sie Upgrade- und Rollback-Verfahren sowie Schritt-für-Schritt-Anleitungen für die Durchführung eines [In-Place-Upgrades](/help/sites-deploying/in-place-upgrade.md). Diese Anweisungen sollten überprüft und für Ihre Systemarchitektur, Anpassungen und Ausfallzeitentoleranz berücksichtigt werden, um die entsprechenden Switchover- und Rollback-Vorgänge zu bestimmen, die Sie während des Upgrades ausführen. Änderungen an der Architektur oder Servergröße sollten beim Entwerfen des benutzerdefinierten Runbooks miteinbezogen werden.

### Entwickeln eines Aktualisierungsplans {#developing-an-upgrade-plan}

Die Ergebnisse der vorherigen Übungen können verwendet werden, um einen Upgrade-Plan zu erstellen, der die erwarteten Zeitpläne für Ihre Test- oder Entwicklungsbemühungen und die tatsächliche Ausführung des Upgrades abdeckt.

<!--Alexandru: drafting for now

![develop-project-plan](assets/develop-project-plan.png) -->

Ein umfassender Projektplan sollte folgende Punkte beinhalten:

* Finalisierung der Entwicklungs- und Testpläne
* Aktualisierung von Entwicklungs- und QS-Umgebungen
* Aktualisieren der benutzerdefinierten Code-Basis für AEM 6.5 LTS
* Test- und Fehlerbehebungszyklus zur Qualitätssicherung
* Aktualisierung der Staging-Umgebung
* Integrations-, Leistungs- und Lasttests
* Zertifizierung der Umgebung
* Live schalten

### Durchführung von Entwicklung und Qualitätssicherung {#performing-development-and-qa}

Adobe hat Verfahren für das [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) bereitgestellt, damit diese mit AEM 6.5 LTS kompatibel sind. Während dieser iterative Prozess ausgeführt wird, sollten nach Bedarf Änderungen am Runbook vorgenommen werden.

<!--Alexandru: drafting for now

![patru_cropped](assets/patru_cropped.png) -->

Der Entwicklungs- und Testprozess ist in der Regel iterativ. Werden Probleme identifiziert, die Anpassungen des Upgrade-Prozesses erfordern, stellen Sie sicher, dass Sie diese zum benutzerdefinierten Runbook für das Upgrade hinzufügen. Nach mehreren Iterationen von Tests und Fehlerbehebung sollte die Code-Basis vollständig validiert und für die Bereitstellung in der Staging-Umgebung bereit sein.

### Abschließende Tests {#final-testing}

Nach der Zertifizierung der Code-Basis durch das Qualitätssicherungs-Team Ihres Unternehmens wird eine abschließende Testrunde empfohlen. Diese Testrunde beinhaltet die Validierung Ihres Runbooks in einer Staging-Umgebung, gefolgt von Benutzerakzeptanz-, Leistungs- und Sicherheitstests.

<!--Alexandru: drafting for now

![cinci_cropped](assets/cinci_cropped.png) -->

Dieser Schritt ist notwendig, da dies die einzige Gelegenheit ist, bei der Sie die Schritte im Runbook in einer produktionsähnlichen Umgebung überprüfen können. Wenn ein Upgrade für die Umgebung durchgeführt wurde, müssen die Endbenutzenden genügend Zeit haben, um sich anzumelden und ihre üblichen täglichen Aktivitäten im System durchzuführen. Durch die Identifizierung und Behebung von Fehlern in diesen Bereichen vor der Live-Schaltung können kostspielige Produktionsausfälle verhindert werden.

### Durchführen des Upgrades {#performing-the-upgrade}

Sobald die endgültige Abnahme von allen Beteiligten eingegangen ist, ist es an der Zeit, die definierten Runbook-Verfahren auszuführen. Adobe hat unter [Upgrade-Verfahren](/help/sites-deploying/upgrade-procedure.md) Schritte für das Upgrade und das Rollback sowie als Referenz die Installationsschritte bei der Durchführung eines [In-Place-Upgrades](/help/sites-deploying/in-place-upgrade.md) zur Verfügung gestellt.

![perform-upgrade](assets/perform-upgrade.png)

Adobe hat in den Upgrade-Anweisungen eine Reihe von Schritten für die Validierung der Umgebung bereitgestellt. Hierzu gehören grundlegende Prüfungen wie das Überprüfen der Upgrade-Protokolle und die Verifizierung des ordnungsgemäßen Starts aller OSGi-Bundles. Adobe empfiehlt jedoch auch eine Validierung anhand eigener Nutzungsszenarien für Ihre Geschäftsprozesse. Darüber hinaus empfiehlt Adobe die Überprüfung des Zeitplans für die Online-Revisionsbereinigung von AEM sowie der zugehörigen Routinen, um sicherzustellen, dass diese nicht zu Stoßzeiten durchgeführt werden. Diese Routinen sind für die langfristige Leistungsfähigkeit von AEM von entscheidender Bedeutung.
