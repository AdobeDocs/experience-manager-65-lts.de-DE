---
title: Von Acrobat Reader DC Extensions verwendete Zertifikatstypen
description: Erfahren Sie mehr über die von Acrobat Reader DC Extensions verwendeten Zertifikatstypen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: ca919915-c37b-4793-b5e2-21a464c5dcdf
source-git-commit: 253e2b5a39fd4c2fe7ab9aeaafb72930b4aa39ff
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 65%

---

# Von Acrobat Reader DC Extensions verwendete Zertifikatstypen {#certificate-types-used-by-acrobat-reader-dc-extensions}

Die Zertifikatsanzeige enthält die folgenden Informationen zum Zertifikat:

* Anzeigename des Zertifikats
* Zertifikatsprofile
* Gültigkeitsdauer
* Verwendungsrechte für Acrobat Reader DC Extensions

## Anzeigename des Zertifikats {#certificate-friendly-name}

Der Anzeigename eines Acrobat Reader DC Extensions-Zertifikats ist eine Zeichenfolge, die die Eigenschaften des Zertifikats beschreibt, wie im folgenden Beispiel gezeigt:

ARE 2D Barcode Full Production V6.1 P8 0002054

Die Zeichenfolge enthält folgende Elemente:

**Zertifikatstyp:** Beschreibt die AEM Forms-Module, die das Zertifikat aktiviert, sowie den Grad der Aktivierung (beispielsweise ARE 2D Barcode Full). Eine Liste der verfügbaren Zertifikatstypen finden Sie im Abschnitt „Zertifikatprofile“ in der Tabelle in der Spalte „Typ“.

**Bereitstellungstyp:** Gibt den vorgesehenen Zweck des Zertifikats an (z. B. Produktion). Der Wert kann „Test“ oder „Produktion“ lauten. Eine Liste der Bereitstellungstypen für jeden Zertifikatstyp finden Sie im Abschnitt „Zertifikatprofile“ in der Tabelle in der Spalte „Bereitstellungstyp“.

**Verwendungsrechteversion:** Beschreibt die Version des Verwendungsrechtealgorithmus, für die das Zertifikat verwendet werden kann, z. B. V6.1. Diese Version gibt nicht die Version von Acrobat oder Acrobat Reader DC Extensions an.

**Profilcode:** Der Profilcode ist eine Kurzbeschreibung der vollständigen Zertifikateigenschaften (beispielsweise P8). Eine Liste der Profilcodes für jeden Dateityp finden Sie im Abschnitt „Zertifikatprofile“ in der Tabelle in der Spalte „Profilcode“.

**Seriennummer:** Jedem von Adobe ausgestellten Zertifikat wird eine Seriennummer zugewiesen (z. B. 0002054). Der Adobe-Unternehmens-Support oder die -Kundenbetreuung kann anhand dieser Seriennummer das Zertifikat einer bestimmten Produktbestellung oder einem OEM-Vertrag zuordnen.

## Zertifikatsprofile {#certificate-profiles}

In der folgenden Tabelle sind die Zertifikatprofile aufgeführt, die bei der Analyse von Acrobat Reader DC Extensions-Zertifikaten auftreten können.

<table>
 <thead>
  <tr>
   <th><p>Profil-Code</p></th>
   <th><p>Typ</p></th>
   <th><p>Gültigkeitsdauer</p></th>
   <th><p>Bereitstellungstyp</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>P1</p></td>
   <td><p>SAP-Produktion</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion</p></td>
  </tr>
  <tr>
   <td><p>P2</p></td>
   <td><p>SAP – Interner Test</p></td>
   <td><p>2 Jahre</p></td>
   <td><p>Beurteilung und Test</p></td>
  </tr>
  <tr>
   <td><p>P3</p></td>
   <td><p>Acrobat Reader DC Extensions, Produktion</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion</p></td>
  </tr>
  <tr>
   <td><p>P4</p></td>
   <td><p>Acrobat Reader DC Extensions, interne Verwendung von Adobe</p></td>
   <td><p>2 Jahre</p></td>
   <td><p>Produktion</p></td>
  </tr>
  <tr>
   <td><p>P5</p></td>
   <td><p>Acrobat Reader DC Extensions, Partnerintegration</p></td>
   <td><p>2 Jahre</p></td>
   <td><p>Beurteilung und Test</p></td>
  </tr>
  <tr>
   <td><p>P6</p></td>
   <td><p>Acrobat Reader DC Extensions, Auswertung</p></td>
   <td><p>60 Tage</p></td>
   <td><p>Test</p></td>
  </tr>
  <tr>
   <td><p>P8</p></td>
   <td><p>Forms, Produktion</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion</p></td>
  </tr>
  <tr>
   <td><p>P9</p></td>
   <td><p>Adobe Acrobat 7.x, Produktion</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion</p></td>
  </tr>
  <tr>
   <td><p>I10</p></td>
   <td><p>Forms; OEMs können Forms verwenden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Auswertung</p></td>
  </tr>
  <tr>
   <td><p>I11</p></td>
   <td><p>Forms; OEMs können Forms verwenden.</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Auswertung</p></td>
  </tr>
  <tr>
   <td><p>I12</p></td>
   <td><p>Nur Signatur; OEMs dürfen nur Signaturen verwenden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Auswertung</p></td>
  </tr>
  <tr>
   <td><p>I13</p></td>
   <td><p>Nur Offline-Kommentare; OEMs können Offline-Kommentare verwenden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Auswertung</p></td>
  </tr>
  <tr>
   <td><p>I14</p></td>
   <td><p>Nur Kommentare; OEMs dürfen nur Kommentare verwenden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Auswertung</p></td>
  </tr>
  <tr>
   <td><p>I15</p></td>
   <td><p>Vollständige Berechtigungen; OEMs können vollständige Berechtigungen verwenden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Auswertung</p></td>
  </tr>
 </tbody>
</table>

## Gültigkeitsdauer {#validity-period}

Auswertungszertifikate werden Kundinnen und Kunden sowie Entwickelnden ausgestellt, damit sie Beispielanwendungen für Produkte entwickeln und testen können. Die Gültigkeitsdauer dieser Zertifikate liegt zwischen 60 und 90 Tagen.  Sie laufen am Ende des zweiten Monats nach Ablauf der Ausgabedaten ab.

Zertifikate für die Partnerintegration werden Adobe-Geschäftspartnern ausgestellt, um die Softwareentwicklung, Integration, Erstellung von Prototypen und Demos zu unterstützen.  Diese Zertifikate gelten zwei Jahre ab dem Ausstellungsdatum.

Adobe Internal Use-Zertifikate werden innerhalb von Adobe verwendet, um die Entwicklung, Integration, Prototyping und Demonstration von Software zu unterstützen. Diese Zertifikate gelten zwei Jahre ab dem Ausstellungsdatum.

Produktionszertifikate werden Kunden ausgestellt, die Acrobat Reader DC Extensions erworben haben. Diese Zertifikate sind für den von der Zertifizierungsstelle maximal zugelassenen Zeitraum gültig (siehe die Spalte „*Maximal*“ in der Tabelle „Zertifikatsprofile“).

## Verwendungsrechte für Acrobat Reader DC Extensions {#acrobat-reader-dc-extensions-usage-rights}

Wenn Sie das Zertifikat für Acrobat Reader DC Extensions im Zertifikatbetrachter überprüfen, können Sie das Element „Verwendungsrechte“ auf der Registerkarte „Details“ auswählen (falls konfiguriert). Sie können eine detaillierte Liste der Adobe Reader-Verwendungsrechte sehen, die das Zertifikat aktivieren kann. Die für ein bestimmtes Dokument aktivierten Verwendungsrechte können eine Teilmenge dieser durch das Zertifikat aktivierten Rechte sein.

Wenn die Online-Kommentierung in einer Umgebung ohne Zusammenarbeitsfunktionalität erforderlich ist, wenden Sie sich wegen weiterer Informationen an den Adobe-Support.  Die Modus-Eigenschaft entspricht dem Bereitstellungstyp und lautet entweder *production* (Produktion) oder *evaluation* (Test).

Die zulässigen Verwendungsrechte für Acrobat Reader DC-Erweiterungen bestehen aus einem oder mehreren bestimmten Elementen. Diese Elemente werden in verschiedenen Kombinationen verwendet, um Variationen lizenzierter Produktfunktionen zu ermöglichen.

<table>
 <thead>
  <tr>
   <th><p>Element der Verwendungsrechte</p></th>
   <th><p>In Adobe Reader aktivierte Funktion bei der Anzeige eines PDF-Dokuments mit aktivierten Verwendungsrechten</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>FormFillInAndSave</p></td>
   <td><p>Füllen Sie die Formularfelder aus und speichern Sie die Dateien lokal.</p></td>
  </tr>
  <tr>
   <td><p>FormImportExport</p></td>
   <td><p>Formulardaten als FDF-, XFDF-, XML- und XDP-Dateien importieren und exportieren</p></td>
  </tr>
  <tr>
   <td><p>FormAddDelete</p></td>
   <td><p>Felder und Feldeigenschaften im PDF-Formular hinzufügen, ändern oder löschen</p></td>
  </tr>
  <tr>
   <td><p>SubmitStandalone</p></td>
   <td><p>Daten per E-Mail oder offline an einen Server senden, der nicht in einer Browser-Sitzung ausgeführt wird</p></td>
  </tr>
  <tr>
   <td><p>SpawnTemplate</p></td>
   <td><p>Seiten aus Vorlagenseiten innerhalb desselben Formulars erstellen</p></td>
  </tr>
  <tr>
   <td><p>Unterzeichnen</p></td>
   <td><p>PDF-Dokumente digital signieren und speichern und digitale Signaturen löschen</p></td>
  </tr>
  <tr>
   <td><p>AnnotModify</p></td>
   <td><p>Dokumentanmerkungen (z. B. Kommentare) erstellen und ändern</p></td>
  </tr>
  <tr>
   <td><p>AnnotImportExport</p></td>
   <td><p>Anmerkungen (z. B. Kommentare) in einer getrennten Datei speichern und Kommentare aus einer Datei laden</p></td>
  </tr>
  <tr>
   <td><p>BarcodePlaintext</p></td>
   <td><p>Ein Dokument mit Formulardaten in einem unverschlüsselten Barcode-Format drucken, für das zum Dekodieren keine lizenzierte Server-Software erforderlich ist</p></td>
  </tr>
  <tr>
   <td><p>AnnotOnline</p></td>
   <td><p>Anmerkungen (z. B. Kommentare) auf einen Server für die Online-Überprüfung und -Kommentierung von Dokumenten hochladen und von diesem herunterladen</p></td>
  </tr>
  <tr>
   <td><p>FormOnline</p></td>
   <td><p>Mit Web-Diensten oder Datenbanken verbinden, die in einem PDF-Formular definiert sind</p></td>
  </tr>
  <tr>
   <td><p>EFModif</p></td>
   <td><p>Eingebettete Dateiobjekte ändern, die mit dem PDF-Dokument verknüpft sind</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Die Nutzungsrechte für Acrobat Reader DC Extensions können von Adobe nur in bestimmten Kombinationen lizenziert werden, die zusammenarbeiten. Es ist nicht möglich, diese Funktionen einzeln zu lizenzieren. Informationen zu den möglichen Kombinationen von Verwendungsrechten erhalten Sie von Ihrer AEM Forms-Kundenbetreuung.
