---
title: Konfigurieren von Suchformularen
description: Erfahren Sie, wie Sie mit Suchformularen die Auswahl der Suchprädikate anpassen können, die in den Suchbereichen der verschiedenen AEM-Konsolen und in Bedienfeldern der Autorenumgebung verwendet werden.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
exl-id: 68a4d4b2-91a3-4545-a491-2a1ec08ceec5
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '2072'
ht-degree: 100%

---

# Konfigurieren von Suchformularen{#configuring-search-forms}

Mit **Suchformularen** können Sie die Auswahl der Suchprädikate anpassen, die in den Suchbereichen der verschiedenen AEM-Konsolen und/oder in den Suchbereichen der Autorenumgebung verwendet werden. Auf diese Weise können Sie die Suchfunktion genau auf Ihre speziellen Anforderungen ausrichten.

Eine [Reihe an Prädikaten](#predicates-and-their-settings) ist vorkonfiguriert verfügbar. Sie können mehrere Prädikate hinzufügen, darunter (unter anderem) das Eigenschaftsprädikat, um nach Assets zu suchen, die mit einer von Ihnen angegebenen Eigenschaft übereinstimmen. Oder das Optionsprädikat, um nach Assets zu suchen, die einem oder mehreren Werten entsprechen, die Sie für eine bestimmte Eigenschaft angeben.

Sie können [die in verschiedenen Konsolen und im Asset-Browser (beim Bearbeiten von Seiten) verwendeten Suchformulare](#configuring-your-search-forms) konfigurieren. Die [Dialogfelder für die Konfiguration dieser Formulare](#configuring-your-search-forms) finden Sie unter:

* **Tools**

   * **Allgemein**

      * **Suchformulare**

Wenn Sie zum ersten Mal auf diese Konsole zugreifen, weisen alle Konfigurationen ein Vorhängeschlosssymbol auf. Dieses Symbol bedeutet, dass die richtige Konfiguration die (vorkonfigurierte) Standardkonfiguration ist und nicht gelöscht werden kann. Nachdem Sie die Konfiguration angepasst haben, wird das Schloss ausgeblendet, es sei denn, Sie [löschen Ihre benutzerdefinierte Konfiguration](#deleting-a-configuration-to-reinstate-the-default). In diesem Fall wird die Standardeinstellung (und das Vorhängeschlosssymbol) wieder aktiviert.

![Suchformulare-Fenster](assets/chlimage_1-374.png)

## Konfigurationen {#configurations}

Die verfügbaren Standardkonfigurationen sind:

* **Seiten-Editor (Dokumentensuche):**

  Diese Konfiguration definiert die Optionen, die bei der Suche nach Dokumenten im Assets-Browser (beim Bearbeiten einer Seite) verfügbar sind.

* **Seiten-Editor (Bildsuche):**

  Diese Konfiguration definiert die Optionen, die bei der Suche nach Bildern im Assets-Browser (beim Bearbeiten einer Seite) verfügbar sind.

* **Seiten-Editor (Manuskriptsuche):**

  Diese Konfiguration definiert die Optionen, die bei der Suche nach Manuskripten im Assets-Browser (beim Bearbeiten einer Seite) verfügbar sind.

* **Seiten-Editor (Seitensuche):**

  Diese Konfiguration definiert die Optionen, die bei der Suche nach Seiten im Assets-Browser (beim Bearbeiten einer Seite) verfügbar sind.

* **Seiten-Editor (Absatzsuche):**

  Diese Konfiguration definiert die Optionen, die bei der Suche nach Absätzen im Assets-Browser (beim Bearbeiten einer Seite) verfügbar sind.

* **Seiten-Editor (Produktsuche):**

  Diese Konfiguration definiert die Optionen, die bei der Suche nach Produkten im Assets-Browser (beim Bearbeiten einer Seite) verfügbar sind.

* **Seiten-Editor (Dynamic Media Classic [früher Scene7]-Suche)**:

  Diese Konfiguration definiert die Optionen, die bei der Suche nach Scene7-Ressourcen im Assets-Browser (beim Bearbeiten einer Seite) verfügbar sind.

* **Sites-Admin-Suchleiste**:

  Diese Konfiguration definiert die Suchoptionen, die in der Suchleiste der Sites-Konsole verfügbar sind.

* **Seiten-Editor (Videosuche):**

  Diese Konfiguration definiert die Optionen, die bei der Suche nach Videos im Assets-Browser (beim Bearbeiten einer Seite) verfügbar sind.

* **Asset-Admin-Suchleiste:**

  Diese Konfiguration definiert die Suchoptionen, die in der Assets-Konsole verfügbar sind.

* **Katalog-Admin-Suchleiste:**

  Diese Konfiguration definiert die Suchoptionen, die bei der Suche nach einem Commerce-Katalog verfügbar sind.

* **Auftrags-Admin-Suchleiste:**

  Diese Konfiguration definiert die Suchoptionen, die bei der Suche nach Commerce-Bestellungen verfügbar sind.

* **Admin-Suchleiste für Produktsammlungen:**

  Diese Konfiguration definiert die Suchoptionen, die bei der Suche nach Commerce-Produktsammlungen verfügbar sind.

* **Produkt-Admin-Suchleiste:**

  Diese Konfiguration definiert die Suchoptionen, die bei der Suche nach Commerce-Produkten verfügbar sind.

* **Projekt-Admin-Suchleiste:**

  Diese Konfiguration definiert die Suchoptionen, die bei der Suche nach Projekten verfügbar sind.

## Prädikate und ihre Einstellungen {#predicates-and-their-settings}

### Prädikate {#predicates}

Die folgenden Prädikate stehen je nach Konfiguration zur Verfügung:

<table>
 <tbody>
  <tr>
   <th>Prädikat</th>
   <th>Zweck</th>
   <th>Einstellungen</th>
  </tr>
  <tr>
   <td>Analyse </td>
   <td>Such-/Filterfunktionen im Sites-Browser, wenn analysebasierte Daten angezeigt werden. Analyse-Suchfilter werden geladen, um die zugeordneten angepassten Analysespalten abzugleichen.</td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Asset zuletzt geändert </td>
   <td>Letztes Änderungsdatum des Assets.<br /> </td>
   <td>Ein benutzerdefiniertes Prädikat, basierend auf dem Datumsprädikat.</td>
  </tr>
  <tr>
   <td>Komponenten </td>
   <td>Ermöglicht es einem Autor, nach Seiten zu suchen/zu filtern, die eine bestimmte Komponente enthalten. Beispiel: eine Bildergalerie.<br /> </td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Platzhalter</li>
     <li>Eigenschaftsname*</li>
     <li>Eigenschaftstiefe</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Datum </td>
   <td>Reglerbasierte Suche nach Assets basierend auf einer Datumseigenschaft.</td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Eigenschaftsname*</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Datumsbereich </td>
   <td>Suche nach Assets, die innerhalb eines angegebenen Bereichs für eine Datumseigenschaft erstellt wurden. Im Suchbereich können Sie das Start- und das Enddatum angeben.</td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Platzhalter</li>
     <li>Eigenschaftsname*</li>
     <li>Textbereich (von)*</li>
     <li>Textbereich (bis)*</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Gültigkeitsstatus </td>
   <td>Suche nach Assets basierend auf dem Ablaufstatus.</td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Eigenschaftsname*</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Dateigröße </td>
   <td>Suche nach Assets basierend auf ihrer Größe.</td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Eigenschaftsname*</li>
     <li>Optionspfad</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Ausgeblendeter Filter</td>
   <td>Ein Filter für Eigenschaft und Wert, der für die Benutzenden nicht sichtbar ist.</td>
   <td>
    <ul>
     <li>Eigenschaftsname</li>
     <li>Eigenschaftswert</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Optionen </td>
   <td><p>Die Optionen sind vom Benutzer erstellte Inhaltsknoten.</p> <p>Weitere Informationen finden Sie unter <a href="#addinganoptionspredicate">Hinzufügen eines Optionsprädikats</a>.</p> </td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>JSON-Pfad</li>
     <li>Eigenschaftsname*</li>
     <li>Einzelauswahl</li>
     <li>Optionspfad</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Options-Eigenschaft </td>
   <td>Suche nach einer Eigenschaft der Option.</td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Eigenschaftsname*</li>
     <li>Optionsknotenpfad<br /> </li>
     <li>Einzelauswahl</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Seitenstatus </td>
   <td>Suche nach Seiten basierend auf ihrem Status.</td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Veröffentlichungs-Eigenschaftsname</li>
     <li>LiveCopy-Eigenschaftsname</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Pfad   </td>
   <td>Suche nach Assets unter einem bestimmten Pfad.</td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Suchpfad hinzufügen</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Eigenschaft </td>
   <td>Suche nach einer angegebenen Eigenschaft.</td>
   <td>keine</td>
  </tr>
  <tr>
   <td>Veröffentlichungsstatus </td>
   <td>Suchen nach Assets basierend auf ihrem Veröffentlichungsstatus</td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Eigenschaftsname*</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Bereich </td>
   <td>Suche nach Ressourcen, die innerhalb eines bestimmten Bereichs liegen. Im Suchbereich können Sie den Mindest- und den Höchstwert für den Bereich angeben.</td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Eigenschaftsname</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Bereichsoptionen </td>
   <td>Ein spezifisches Suchprädikat für Assets und identisch mit dem allgemeinen Reglerprädikat. Ist aufgrund von Problemen mit der Abwärtskompatibilität noch verfügbar.</td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Eigenschaftsname*</li>
     <li>Optionspfad</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Bewertung </td>
   <td>Suche nach Assets basierend auf ihrer Bewertung.<br /> </td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Eigenschaftsname*</li>
     <li>Optionspfad</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Relatives Datum </td>
   <td>Suche nach Assets basierend auf ihrem relativen Erstellungsdatum.<br /> </td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Eigenschaftsname*</li>
     <li>Relatives Datum</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Reglerbereich </td>
   <td>Ein allgemeines Suchprädikat, das das Bereichsprädikat um die Reglerfunktion erweitert. Der Wert der gesuchten Eigenschaft muss zwischen den Grenzen des Reglers liegen.</td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Eigenschaftsname*</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Tag </td>
   <td>Suche Assets basierend auf Tags. Sie können die Pfadeigenschaft konfigurieren, um verschiedene Tags in der Tag-Liste zu füllen.</td>
   <td>
    <ul>
     <li>Feldbezeichnung</li>
     <li>Eigenschaftsname*</li>
     <li>Optionspfad</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Tags </td>
   <td>Suche basierend auf Tags.</td>
   <td>
    <ul>
     <li>Platzhalter</li>
     <li>Eigenschaftsname*</li>
     <li>Beschreibung</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Die allgemeinen Suchprädikate sind hier definiert:
>  `/libs/cq/gui/components/common/admin/customsearch/searchpredicates`
>
>* Sucheigenschaften, die nur mit siteadmin (klassische Benutzeroberfläche) verbunden sind, befinden sich unter:
>  `/libs/cq/gui/components/siteadmin/admin/searchpanel/searchpredicates`
>   * Sie sind veraltet und nur aus Gründen der Abwärtskompatibilität verfügbar.
>
>Diese Informationen dienen nur als Referenz. Ändern Sie `/libs` nicht.

### Prädikateinstellungen {#predicate-settings}

Je nach Prädikat stehen mehrere Einstellungen für die Konfiguration zur Verfügung:

* **Feldbezeichnung**

  Die Bezeichnung, die als ausblendbare Kopfzeile oder als Feldbezeichnung des Prädikats angezeigt wird.

* **Beschreibung**

  Beschreibende Informationen für die Benutzer.

* **Platzhalter**

  Leerer Text oder der Platzhalter des Prädikats, der angezeigt wird, wenn kein Filtertext eingegeben wird.

* **Eigenschaftsname**

  Die Eigenschaft, nach der gesucht werden soll. Sie nutzt einen relativen Pfad und die Platzhaltersymbole `*/*/*` geben die Tiefe der Eigenschaft in Relation zum `jcr:content`-Knoten an (jeder Asterisk steht für eine Knotenebene).

  Wenn Sie nur nach dem untergeordneten Knoten der ersten Ebene der Ressource suchen möchten, die die Eigenschaft `x` auf dem Knoten `jcr:content` aufweist, nutzen Sie `*/jcr:content/x`.

* **Eigenschaftstiefe**

  Die maximale Tiefe, die bei der Suche nach dieser Eigenschaft innerhalb der Ressourcen berücksichtigt werden soll. So können Sie eine Suche nach dieser Eigenschaft auf einer Ressource und rekursiven untergeordneten Elementen durchführen, bis die Ebene der untergeordneten Elemente der festgelegten Tiefe entspricht.

* **Eigenschaftswert**

  Der Eigenschaftswert als absolute Zeichenfolge oder als Ausdruckssprache, zum Beispiel `cq:Page` oder

  `${empty requestPathInfo.suffix ? "/content" : requestPathInfo.suffix}`.

* **Bereichstext**

  Die Bezeichnung des Bereichsfelds im Prädikat **Datumsbereich**.

* **Optionspfad**

  Die Benutzer können den Pfad mit dem Pfad-Browser auf der Registerkarte mit den Prädikatseinstellungen auswählen. Nach dem Auswählen wird das Plussymbol (**+**) verwendet, um die Auswahl zur Liste der gültigen Optionen hinzufügen. (Entfernen lässt sich die Auswahl mit dem Minussymbol (**-**), falls erforderlich.)

  Die Optionen sind Inhaltsknoten, die von Benutzern erstellt werden, und weisen die folgende Struktur auf:

  `(jcr:primaryType = nt:unstructured, value (String), jcr:title (String))`

* **Optionsknotenpfad** Praktisch dasselbe wie der **Optionspfad**, mit dem Unterschied, dass dieser Pfad sich im gemeinsamen Prädikatsfeld befindet, während der andere Pfad nur für Assets gilt.

* **Einzelauswahl** Wenn diese Option aktiviert ist, werden die Optionen als Kontrollkästchen gerendert, die nur eine Einzelauswahl zulassen. Wenn die Option versehentlich ausgewählt wurde, kann sie per Kontrollkästchen deaktiviert werden.

* **Veröffentlichungs- und Live Copy-Eigenschaftsnamen**
Die Bezeichnungen für die Veröffentlichungs- und Live Copy-Kontrollkästchen für das Sites-spezifische Prädikat.

* Das Sternchen (*) bei den Feldbezeichnungen auf der Registerkarte **Einstellungen** kennzeichnet Pflichtfelder. Werden diese nicht ausgefüllt, wird eine Fehlermeldung angezeigt.

## Konfigurieren Ihrer Suchformulare {#configuring-your-search-forms}

### Erstellen/Öffnen einer benutzerdefinierten Konfiguration {#creating-opening-a-customized-configuration}

1. Navigieren Sie zu **Tools** > **Allgemein** > **Suchformulare**.

1. Wählen Sie die Konfiguration aus, die Sie anpassen möchten.
1. Verwenden Sie das Symbol **Bearbeiten**, um die Konfiguration für die Aktualisierung zu öffnen.
1. Bei einer neuen Anpassung wollen Sie wahrscheinlich nach Bedarf [neue Prädikatsfelder hinzufügen und die Einstellungen definieren](#add-edit-a-predicate-field-and-define-field-settings). Bei einer vorhandenen Anpassung können Sie ein vorhandenes Feld auswählen und [die Einstellungen aktualisieren](#add-edit-a-predicate-field-and-define-field-settings).
1. Wählen Sie **Fertig** aus, um die Konfiguration zu speichern.

   >[!NOTE]
   >
   >Die angepassten Konfigurationen werden (wie jeweils angemessen) unter folgendem Pfad gespeichert:
   >
   >* `/apps/cq/gui/content/facets/<option>`
   >* `/apps/commerce/gui/content/facets/<option>`

### Hinzufügen/Bearbeiten eines Prädikatfelds und Definieren der Feldeinstellungen {#add-edit-a-predicate-field-and-define-field-settings}

Sie können Felder hinzufügen oder bearbeiten und deren Einstellungen definieren/aktualisieren:

1. [Öffnen Sie die benutzerdefinierte Konfiguration](#creating-opening-a-customized-configuration) für die Aktualisierung.
1. Um ein Feld hinzuzufügen, öffnen Sie die Registerkarte **Prädikat auswählen** und ziehen Sie das benötigte Prädikat an die gewünschte Stelle. Beispiel: die **Datumsbereich-Eigenschaft**:

   ![Bearbeiten eines Suchformulars](assets/chlimage_1-375.png)

1. Der nächste Schritt hängt davon ab, was Sie tun möchten:

   * Sie fügen ein Feld hinzu:

     Nach dem Hinzufügen des Prädikats öffnet sich die Registerkarte **Einstellungen**. Dort werden die Eigenschaften angezeigt, die definiert werden können.

   * Sie aktualisieren ein vorhandenes Prädikat:

     Wählen Sie das Prädikatsfeld aus (rechts) und öffnen Sie dann die Registerkarte **Einstellungen**.

   Beispiel: die Einstellungen für die **Datumsbereich-Eigenschaft**:

   ![Eigenschaften für Datumsbereichsprädikate](assets/chlimage_1-376.png)

1. Nehmen Sie die erforderlichen Änderungen vor und bestätigen Sie sie mit **Fertig**.

### Anzeigen einer Vorschau der Suchkonfiguration {#previewing-the-search-configuration}

1. Wählen Sie das Vorschausymbol aus:

   ![Suchformular-Vorschau](do-not-localize/chlimage_1-31.png)

1. Dies zeigt die Suchformulare so an, wie sie in der Suchspalte der entsprechenden Konsole angezeigt werden (vollständig ausgeklappt).

   ![Anzeigen der Suchformular-Vorschau](assets/chlimage_1-377.png)

1. **Schließen** Sie die Vorschau, um zur Konfiguration zurückzukehren und sie fertigzustellen.

### Löschen eines Prädikatfelds {#deleting-a-predicate-field}

1. [Öffnen Sie die benutzerdefinierte Konfiguration](#creating-opening-a-customized-configuration) für die Aktualisierung.
1. Wählen Sie das Prädikatsfeld (rechts) aus, öffnen Sie die Registerkarte **Einstellungen** und wählen Sie dann das Symbol **Löschen** (unten links) aus.

   ![Löschsymbol](do-not-localize/chlimage_1-32.png)

1. In einem Dialogfeld werden Sie dazu aufgefordert, die Löschaktion zu bestätigen.

1. Bestätigen Sie diese und andere Änderungen mit **Fertig**.

### Löschen einer Konfiguration (zur erneuten Aktivierung des Standards) {#deleting-a-configuration-to-reinstate-the-default}

Wenn Sie eine Konfiguration angepasst haben, werden die Standardwerte überschrieben. Sie können die Standardkonfiguration erneut aktivieren, indem Sie die angepasste Konfiguration löschen.

>[!NOTE]
>
>Sie können keine der beiden Standardkonfigurationen löschen.

Das Löschen einer angepassten Konfiguration erfolgt über die Konsole:

1. Wählen Sie die benötigte Konfiguration (z. B. **Seiten-Editor (Absatzsuche)**) und anschließend das Symbol **Löschen** in der Symbolleiste aus:

   ![Ein Formular löschen](assets/chlimage_1-378.png)

1. Die angepasste Konfiguration wird gelöscht und die Standardkonfiguration wiederhergestellt (erkennbar am Vorhängeschlosssymbol, das wieder in der Konsole angezeigt wird).

### Hinzufügen von Optionsprädikaten {#adding-options-predicates}

Mit Optionsprädikaten (Optionen, Optionseigenschaft) können Sie ein Element konfigurieren, nach dem gesucht werden soll. Sie werden verwendet, um etwas direkt unter der Seite zu suchen, z. B. eine Eigenschaft auf dem Seitenknoten.

Das folgende Beispiel (Suche entsprechend der Vorlage, mit der eine Seite erstellt wird) verdeutlicht die einzelnen Schritte:

1. Erstellen Sie den Knoten, der die zu suchende Eigenschaft enthält.

   Sie benötigen einen Stammknoten, der die Definitionen der einzelnen Optionen umfasst, die für Benutzende verfügbar sein sollen.

   Die Knoten für die einzelnen Optionen müssen die folgenden Eigenschaften aufweisen:

   * `jcr:title` – die Feldbezeichnung, die in der Suchschiene angezeigt werden soll
   * `value` – der Eigenschaftswert, nach dem gesucht werden soll

   ![ Hinzufügen von Optionen in CRXDE](assets/chlimage_1-379.png)

   >[!NOTE]
   >
   >Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen.
   >
   >da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)
   >
   >Die empfohlene Methode zur Konfiguration und für andere Änderungen sieht wie folgt aus:
   >
   >1. Aktivieren Sie das benötigte Element erneut so, wie es in `/libs` unter `/apps` vorhanden ist. In diesem Fall im folgenden Verzeichnis:
   >1. `/libs/cq/gui/content/common/options/predicates`
   >1. Nehmen Sie die gewünschten Änderungen in `/apps.` vor.

1. Öffnen Sie die **Suchformulare-Konsole** und wählen Sie die Konfiguration aus, die Sie aktualisieren möchten. Beispiel: **Sites-Admin-Suchleiste**.

   Klicken Sie dann auf das Symbol **Suchformulare bearbeiten**.

1. Je nach Konfiguration fügen Sie **Optionen** oder eine **Optionseigenschaft** zur Konfiguration hinzu.
1. Aktualisieren Sie die Felder, insbesondere:

   * **Eigenschaftsname**

     Geben Sie die Knoteneigenschaft an, nach der auf den Zielknoten gesucht werden soll. Zum Beispiel:

     `jcr:content/cq:template`

   * **Optionsknotenpfad**

     Wählen Sie den Pfad des Speicherorts der Optionen aus. Zum Beispiel:

     `/apps/cq/gui/content/common/options/predicates/templatetype`

   ![Eigenschaftspfad hinzufügen](assets/chlimage_1-380.png)

1. Wählen Sie **Fertig** aus, um die Konfiguration zu speichern.
1. Navigieren Sie zu der entsprechenden Konsole (in diesem Beispiel **Sites**) und öffnen Sie die **Suchleiste**. Die neu definierten Suchformulare werden zusammen mit den verschiedenen Optionen angezeigt. Wählen Sie die benötigte Option aus, um die Suchergebnisse anzuzeigen:

   ![Die Endergebnisse](assets/chlimage_1-381.png)

## Benutzerberechtigungen {#user-permissions}

In der folgenden Tabelle sind die Berechtigungen aufgeführt, die Benutzer benötigen, um Suchformulare zu bearbeiten, zu löschen und Vorschauen anzuzeigen.

<table>
 <tbody>
  <tr>
   <td><strong>Aktion</strong></td>
   <td><strong>Berechtigungen</strong></td>
  </tr>
  <tr>
   <td>Bearbeiten </td>
   <td>Lese- und Schreibberechtigungen für den Knoten <code>/apps </code>.</td>
  </tr>
  <tr>
   <td>Löschen</td>
   <td>Lese-, Schreib- und Löschberechtigungen für den Knoten <code>/apps</code>.</td>
  </tr>
  <tr>
   <td>Vorschau</td>
   <td>Lese-, Schreib- und Löschberechtigungen für den Knoten <code>/var/dam/content</code>.<br /> Lese- und Schreibberechtigungen für den Knoten <code>/apps</code>.</td>
  </tr>
 </tbody>
</table>
