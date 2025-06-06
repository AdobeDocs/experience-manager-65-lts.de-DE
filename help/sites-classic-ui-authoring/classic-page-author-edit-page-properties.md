---
title: Bearbeiten von Seiteneigenschaften
description: Die Eigenschaften einer Seite können je nach Art der Seite variieren. Beispielsweise sind einige Seiten möglicherweise mit einer Live Copy verbunden und andere Seiten nicht. Entsprechend sind auch die Live Copy-Informationen verfügbar.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
exl-id: 0dd160d5-6a08-4c11-92d2-a5a75fc47dba
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 100%

---

# Bearbeiten der Seiteneigenschaften{#editing-page-properties}

Sie können die erforderlichen Eigenschaften für eine Seite definieren. Diese können je nach Art der Seite variieren. Beispielsweise sind einige Seiten möglicherweise mit einer Live Copy verbunden und andere Seiten nicht. Entsprechend sind auch die Live Copy-Informationen verfügbar.

## Seiteneigenschaften {#page-properties}

Die Eigenschaften sind auf verschiedene Registerkarten verteilt:

### Einfach {#basic}

* **Titel**

  Der Titel der Seite wird an verschiedenen Stellen angezeigt. Zum Beispiel in der Liste auf der Registerkarte **Websites** und in den Karten-/Listenansichten **Sites**.

  Dies ist ein Pflichtfeld.

* **Tags**

  Hier können Sie der Seite Tags hinzufügen (oder davon entfernen), indem Sie die Liste im Auswahlfeld aktualisieren:

   * Nachdem Sie ein Tag ausgewählt haben, wird es unterhalb des Auswahlfelds aufgelistet. Sie können ein Tag mit dem „x“ aus dieser Liste entfernen.
   * Sie können ein völlig neues Tag eingeben, indem Sie den Namen in ein leeres Auswahlfeld eingeben.

     Das neue Tag wird erstellt, wenn Sie die Eingabetaste drücken. Das neue Tag wird dann in einem Feld angezeigt. Ein kleiner Stern auf der rechten Seite markiert es als neues Tag.

   * In der Dropdown-Liste können Sie aus vorhandenen Tags auswählen.
   * Wenn Sie den Mauszeiger über einen Tag-Eintrag im Auswahlfeld bewegen, wird ein x angezeigt, mit dessen Hilfe Sie das Tag löschen können.

* **In Navigation ausblenden**

  Ein Umschalter gibt an, ob die Seite in der Seitennavigation ein- oder ausgeblendet sein soll.

* **Seitentitel**

  Ein Titel zur Verwendung auf der Seite.

* **Navigationstitel**

  Sie können einen separaten Titel für die Verwendung in der Navigation angeben (z. B. wenn Sie eine kürzere Alternative wählen möchten). Wenn dies leer gelassen wird, wird der **Titel** verwendet.

* **Untertitel**

  Ein Untertitel zur Verwendung auf der Seite.

* **Beschreibung**

  Ihre Beschreibung der Seite, ihr Zweck oder beliebige andere Details, die Sie hinzufügen möchten.

* **Einschaltzeit**

  Datum und Uhrzeit der Aktivierung der veröffentlichten Seite. Nach der Veröffentlichung dieser Seite ruht sie bis zum angegebenen Zeitpunkt.

  Lassen Sie diese Felder für Seiten, die Sie sofort veröffentlichen möchten (das normale Szenario), leer.

* **Ausschaltzeit**

  Der Zeitpunkt, zu dem die veröffentlichte Seite deaktiviert wird.

  Lassen Sie diese Felder wiederum leer, wenn die Seite sofort veröffentlicht werden soll.

* **Vanity-URL**

  Ermöglicht die Eingabe einer Vanity-URL für diese Seite. Dadurch können Sie eine kürzere, ausdrucksstärkere URL verwenden.

  Beispiel: Wenn die Vanity-URL w`elcome` für die Seite mit dem Pfad /`v1.0/startpage` auf der Website h`ttp://example.com,` verwendet wird, wäre h`ttp://example.com/welcome` die Vanity-URL von h`ttp://example.com/content/v1.0/startpage`.

  >[!CAUTION]
  >
  >Vanity-URLs:
  >
  >* müssen eindeutig sein. Sie müssen also darauf achten, dass der Wert nicht bereits von einer anderen Seite verwendet wird.
  >* unterstützen keine Regex-Muster.

* **Vanity-URL umleiten**

  Gibt an, ob für die Seite eine Vanity-URL verwendet werden soll.

### Erweitert {#advanced}

* **Sprache**

  Die Seitensprache.

* **Umleiten**

  Geben Sie die Seite an, zu der diese Seite automatisch umgeleitet werden soll.

* **Design**

  Geben Sie das [Design](/help/sites-developing/designer.md) an, das für diese Seite verwendet werden soll.

* **Alias**

  Geben Sie einen Alias an, der für diese Seite verwendet werden soll.

* **Geschlossene Benutzergruppe aktivieren**

  Aktiviert (oder deaktiviert) die Verwendung von [geschlossenen Benutzergruppen](/help/sites-administering/cug.md) (CUGs).

* **Anmeldeseite**

  Die Seite, die für die Anmeldung verwendet werden soll.

* **Zugelassene Gruppen**

  Gruppen, die für die Anmeldung bei der CUG berechtigt sind.

* **Bereich**

  Bereichsname für die CUG.

* **Konfiguration exportieren**

  Geben Sie eine Exportkonfiguration an.

### Miniaturansicht  {#thumbnail}

* **Seitenminiatur**

  Zeigt das Miniaturbild der Seite an. Sie haben folgende Möglichkeiten:

   * **Vorschau generieren**

     Generieren Sie eine Vorschau der Seite, die als Miniatur verwendet werden soll.

   * **Bild hochladen**

     Laden Sie ein Bild hoch, das als Miniatur verwendet werden soll.

### Cloud-Services {#cloud-services}

* **Cloud Services**

  Definieren Sie Eigenschaften für [Cloud-Services](/help/sites-developing/extending-cloud-config.md).

### Personalisierung  {#personalization}

* **Personalisierung**

  Wählen Sie eine [Marke, um einen Bereich für das Targeting anzugeben](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md).

### Berechtigungen {#permissions}

* **Berechtigungen** (Touch-optimierte Benutzeroberfläche)

  Zeigen Sie die [effektiven Berechtigungen an und fügen Sie neue Berechtigungen hinzu](/help/sites-administering/user-group-ac-admin.md).

### Blueprint {#blueprint}

* **Blueprint**

  Legen Sie Eigenschaften für eine Blueprint-Seite fest, die für die [Verwaltung mehrerer Websites](/help/sites-administering/msm.md) verwendet wird. Steuert die Umstände, unter denen Änderungen an die Live Copy propagiert werden.

### Live Copy {#live-copy}

* **Live Copy**

  Legen Sie Eigenschaften für eine Live Copy-Seite fest, die für die [Verwaltung mehrerer Websites](/help/sites-administering/msm.md) verwendet wird. Steuert die Umstände, unter denen Änderungen von der Blueprint-Seite propagiert werden.

### Site-Struktur {#site-structure}

* Bieten Sie Links zu Seiten an, die eine Funktionalität für die ganze Site bieten, wie **Anmeldeseite**, **Offline-Seite** und andere.

## Bearbeiten der Seiteneigenschaften {#editing-page-properties-2}

### Bearbeiten der Seiteneigenschaften für eine bestimmte Seite {#editing-page-properties-for-a-specific-page}

Seiteneigenschaften definieren die verschiedenen Eigenschaften der Seite, z. B. Titel, wenn sie auf der Website und anderen Seiten angezeigt werden.

1. Öffnen Sie die Seite, die Sie bearbeiten möchten.

1. Öffnen Sie im Sidekick die Registerkarte **Seite** und wählen Sie anschließend **Seiteneigenschaften...** aus.

   Ein Dialogfeld mit mehreren Registerkarten wird geöffnet.

1. Nehmen Sie die erforderlichen Änderungen vor und klicken Sie dann auf **OK**, um zu speichern.
