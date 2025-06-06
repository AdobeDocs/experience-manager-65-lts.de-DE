---
title: Grundlegende Handhabung
description: Ein Überblick über die grundlegende Handhabung der Adobe Experience Manager-Autorenumgebung. Als Grundlage wird die Sites-Konsole verwendet.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
exl-id: bc424dcd-f3a7-48f5-848d-1b14b8e26862
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 100%

---

# Grundlegende Handhabung{#basic-handling}

>[!NOTE]
>
>* Diese Seite soll einen Überblick über die grundlegende Handhabung der Adobe Experience Manager(AEM)-Autorenumgebung geben. Als Grundlage wird die **Sites-Konsole** verwendet.
>
>* Einige Funktionen sind nicht in allen Konsolen verfügbar, bzw. zusätzliche Funktionen sind in bestimmten Konsolen verfügbar. Ausführlichere Informationen zu den einzelnen Konsolen und ihren jeweiligen Funktionen finden Sie auf anderen Seiten.
>* In AEM stehen verschiedene Tastaturbefehle zur Verfügung, insbesondere bei der [Verwendung von Konsolen](/help/sites-classic-ui-authoring/author-env-keyboard-shortcuts.md) und der [Bearbeitung von Seiten](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md).
>

## Der Begrüßungsbildschirm {#the-welcome-screen}

Die klassische Benutzeroberfläche bietet eine Auswahl an Konsolen, die bekannte Mechanismen zum Navigieren und Initiieren von Aktionen verwenden, einschließlich Klicken, Doppelklicken und [Kontextmenüs](#context-menus).

Nach der Anmeldung wird der Begrüßungsbildschirm angezeigt. Er enthält eine Liste von Links zu Konsolen und Diensten:

![screen_shot_2012-01-30at61745pm](assets/screen_shot_2012-01-30at61745pm.png)

## Konsolen {#consoles}

Die Hauptkonsolen sind: 

<table>
 <tbody>
  <tr>
   <td><strong>Konsole</strong></td>
   <td><strong>Zweck</strong></td>
  </tr>
  <tr>
   <td><strong>Willkommen</strong></td>
   <td>Bietet einen Überblick über und (über Links) direkten Zugriff auf die Hauptfunktionen von AEM.</td>
  </tr>
  <tr>
   <td><strong>Digitale Assets</strong><br /> </td>
   <td>In diesen Konsolen können Sie digitale Assets wie Bilder, Videos, Dokumente und Audiodateien importieren und <a href="/help/sites-classic-ui-authoring/classicui-assets.md">verwalten</a>. Diese Assets können dann von jeder Website verwendet werden, die auf derselben AEM-Instanz ausgeführt wird. </td>
  </tr>
  <tr>
   <td><strong>Launches</strong></td>
   <td>Hier können Sie Ihre <a href="/help/sites-classic-ui-authoring/classic-launches.md">Launches</a> verwalten. Damit können Sie Inhalte für eine künftige Version einer oder mehrerer aktivierter Webseiten entwickeln.<br /> <i>Hinweis: In der Touch-optimierten Benutzeroberfläche sind die meisten der Funktionen in der Sites-Konsole verfügbar ebenso wie die Leiste „Verweise“.</i> <i>Bei Bedarf ist diese Konsole über die Tools-Konsole verfügbar. Wählen Sie dazu „Vorgänge“ und dann „Launches“ aus.</i></td>
  </tr>
  <tr>
   <td><strong>Posteingang </strong></td>
   <td>Häufig sind mehrere Personen an den Unteraufgaben eines Workflows beteiligt. Jede Person muss dabei ihren Schritt abschließen, bevor die Arbeit an die nächste Person weitergegeben wird. Im Posteingang werden Benachrichtigungen zu diesen Aufgaben angezeigt. Siehe <a href="/help/sites-administering/workflows.md">Arbeiten mit Workflows</a>. <br /> </td>
  </tr>
  <tr>
   <td><strong>Tagging</strong></td>
   <td>In der Tagging-Konsole können Sie Tags verwalten. Bei Tags handelt es sich um kurze Namen oder Begriffe, mit denen Sie Inhaltsbereiche kommentieren können, sodass diese leichter gefunden und organisiert werden können. Weitere Informationen finden Sie unter <a href="/help/sites-classic-ui-authoring/classic-feature-tags.md">Verwenden und Verwalten von Tags</a>.</td>
  </tr>
  <tr>
   <td><strong>Tools</strong></td>
   <td>Die <a href="/help/sites-administering/tools-consoles.md">Tools-Konsolen</a> bieten Zugriff auf verschiedene spezialisierte Tools und Konsolen, mit denen Sie Websites, digitale Assets und andere Bereiche Ihres Inhalts-Repositorys verwalten können.</td>
  </tr>
  <tr>
   <td><strong>Benutzer</strong></td>
   <td>In diesen Konsolen können Sie Zugriffsberechtigungen für Benutzerinnen bzw. Benutzer und Gruppen verwalten. Ausführliche Informationen finden Sie unter <a href="/help/sites-administering/security.md">Benutzerverwaltung und Sicherheit</a>.<br /> </td>
  </tr>
  <tr>
   <td><strong>Websites</strong></td>
   <td>Mit den Sites/Websites-Konsolen können Sie <a href="/help/sites-classic-ui-authoring/classic-page-author.md">Websites erstellen, anzeigen und verwalten</a>, die in Ihrer AEM-Instanz betrieben werden. In diesen Konsolen können Sie Website-Seiten erstellen, kopieren und verschieben, Workflows starten und Seiten aktivieren (veröffentlichen). Sie können eine Seite auch zur Bearbeitung öffnen.<br /> </td>
  </tr>
  <tr>
   <td><strong>Workflows</strong></td>
   <td>Bei einem Workflow handelt es sich um eine definierte Abfolge von Schritten, die zum Ausführen einer bestimmten Aufgabe erforderlich sind. Häufig sind mehrere Personen an einer Aufgabe beteiligt. Jede Person muss dabei ihren Schritt abschließen, bevor die Arbeit an die nächste Person weitergegeben wird. In der Konsole „Workflow“ können Sie Workflow-Modelle erstellen und Workflow-Instanzen verwalten, die ausgeführt werden. Siehe <a href="/help/sites-administering/workflows.md">Arbeiten mit Workflows</a>.<br /> </td>
  </tr>
 </tbody>
</table>

Die Konsole **Websites** bietet zwei Bereiche zum Navigieren und Verwalten Ihrer Seiten:

* Linker Bereich

  Zeigt die Baumstruktur Ihrer Websites und die darin enthaltenen Seiten.

  Er enthält außerdem Informationen zu anderen Optionen in AEM, einschließlich Projekten, Blueprints und Assets.

* Rechter Bereich

  Zeigt die Seiten (an der im linken Bereich gewählten Position) und kann für die Durchführung von Aktionen genutzt werden.

Von hier aus können Sie [Ihre Seiten verwalten](/help/sites-authoring/managing-pages.md), entweder über die Symbolleiste, ein Kontextmenü oder indem Sie eine Seite für weitere Aktionen öffnen.

>[!NOTE]
>
>Die grundlegende Handhabung ist in allen Konsolen gleich. Dieser Abschnitt konzentriert sich auf die Konsole **Websites**, da dies die primäre Konsole ist, die beim Bearbeiten verwendet wird.

![chlimage_1-9](assets/chlimage_1-9a.png)

## Zugreifen auf die Hilfe {#accessing-help}

In verschiedenen Konsolen (z. B. Websites) ist eine **Hilfe**-Schaltfläche verfügbar. Durch Klicken auf **Hilfe** wird entweder Package Share oder die Dokumentations-Site geöffnet.

![chlimage_1-10](assets/chlimage_1-10a.png)

Beim Bearbeiten einer Seite [verfügt auch der Sidekick über eine Schaltfläche für den Zugriff auf die Hilfe](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#accessing-help).

## Navigieren mit der Konsole „Websites“ {#navigating-with-the-websites-console}

Die Konsole **Websites** listet Ihre Inhaltsseiten in einer Baumstruktur auf (linker Bereich). Um die Navigation zu vereinfachen, können Abschnitte der Baumstruktur nach Bedarf eingeblendet (+) oder ausgeblendet (-) werden:

* Durch Klicken auf den Seitennamen im linken Bereich wird Folgendes ausgeführt:

   * Die untergeordneten Seiten werden im rechten Bereich angezeigt.
   * Die Struktur wird im linken Bereich erweitert.

     Aus Leistungsgründen hängt diese Aktion von der Anzahl der untergeordneten Knoten ab. Bei einer Standardinstallation wird die Baumstruktur eingeblendet, wenn höchstens `30` untergeordnete Knoten vorhanden sind.

* Durch Doppelklicken auf den Seitennamen (linker Bereich) wird die Baumstruktur eingeblendet, wobei dieser Effekt durch das gleichzeitige Öffnen der Seite nicht so offensichtlich ist.

>[!NOTE]
>
>Der Standardwert ( `30`) kann konsolenweise in den anwendungsspezifischen Konfigurationen des SiteAdmin-Widgets geändert werden:
>
>Führen Sie im SiteAdmin-Knoten folgende Aktionen durch:
>
>Ändern Sie den Wert der Eigenschaft:
>`treeAutoExpandMax`
>in:
>`/apps/wcm/core/content/siteadmin`
>
>Sie können die Einstellung auch global im Thema ändern:
>Ändern Sie den Wert von:
>`TREE_AUTOEXPAND_MAX`
>in:
>`/apps/cq/ui/widgets/themes/default/widgets/wcm/SiteAdmin.js`
>
>Weitere Details finden Sie unter [SiteAdmin in der CQ Widget-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.SiteAdmin).

## Seiteninformationen in der Konsole „Websites“ {#page-information-on-the-websites-console}

Der rechte Bereich der Konsole **Websites** bietet eine Listenansicht mit Informationen zu Seiten:

![page-info](assets/page-info.png)

Die folgenden sind verfügbar, ein Teil dieser Felder wird standardmäßig angezeigt:

<table>
 <tbody>
  <tr>
   <td><strong>Säulendiagramm</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Miniaturansicht</td>
   <td>Zeigt eine Miniaturansicht für die Seite an.</td>
  </tr>
  <tr>
   <td>Titel</td>
   <td>Der Titel, der auf der Seite angezeigt wird</td>
  </tr>
  <tr>
   <td>Name</td>
   <td>Der Name AEM verweist auf die Seite</td>
  </tr>
  <tr>
   <td>Veröffentlicht</td>
   <td>Gibt an, ob die Seite veröffentlicht wurde, und gibt Datum und Uhrzeit der Veröffentlichung an.</td>
  </tr>
  <tr>
   <td>Geändert</td>
   <td>Gibt an, ob die Seite geändert wurde, und gibt Datum und Uhrzeit der Änderung an. Zum Speichern von Änderungen müssen Sie die Seite aktivieren.</td>
  </tr>
  <tr>
   <td>Scene7 Publish</td>
   <td>Gibt an, ob die Seite in Scene7 veröffentlicht wurde.<br /> </td>
  </tr>
  <tr>
   <td>Status</td>
   <td>Gibt den Status der Seite an, z. B. ob die Seite Teil eines Workflows oder einer Live Copy ist oder ob eine Seite derzeit gesperrt ist.</td>
  </tr>
  <tr>
   <td>Impressionen</td>
   <td>Zeigt die Aktivität auf einer Seite in Anzahl der Treffer an.</td>
  </tr>
  <tr>
   <td>Vorlage</td>
   <td>Gibt die Vorlage an, auf der eine Seite basiert.</td>
  </tr>
  <tr>
   <td>In Workflow</td>
   <td>Zeigt an, wenn sich die Seite in einem Workflow befindet.</td>
  </tr>
  <tr>
   <td>Gesperrt durch</td>
   <td>Zeigt an, wann eine Seite gesperrt wurde und welches Benutzerkonto sie gesperrt hat.</td>
  </tr>
  <tr>
   <td>Live Copy</td>
   <td>Zeigt an, wann die Seite Teil einer Live Copy ist.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Um die sichtbaren Spalten auszuwählen, bewegen Sie den Mauszeiger über einen Spaltentitel. Ein Dropdown-Menü wird angezeigt, über das Sie die Option **Spalten** verwenden können.

Die Farben neben den Seiten in den Spalten **Veröffentlicht** und **Geändert** geben den Veröffentlichungsstatus an:

| **Spalte** | **Farbe** | **Beschreibung** |
|---|---|---|
| Veröffentlicht | Grün | Die Veröffentlichung war erfolgreich. Der Inhalt wird veröffentlicht. |
| Veröffentlicht | Gelb | Die Veröffentlichung steht aus. Die Bestätigung der Veröffentlichung ist noch nicht im System eingegangen. |
| Veröffentlicht | Rot | Veröffentlichung fehlgeschlagen. Es besteht keine Verbindung zur Publishing-Instanz. Dies kann auch bedeuten, dass der Inhalt deaktiviert wurde. |
| Veröffentlicht | *blank* | Diese Seite wurde noch nie veröffentlicht. |
| Geändert | Blau | Die Seite wurde seit der letzten Veröffentlichung geändert. |
| Geändert | *blank* | Diese Seite wurde noch nie geändert, auch nicht seit der letzten Veröffentlichung. |

## Kontextmenüs {#context-menus}

Die klassische Benutzeroberfläche nutzt für die Navigation und für das Starten von Aktionen vertraute Mechanismen wie Klicks oder Doppelklicks. Abhängig von der aktuellen Situation stehen auch verschiedene Kontextmenüs zur Verfügung (die sich mit der rechten Maustaste öffnen lassen):

![chlimage_1-11](assets/chlimage_1-11a.png)
