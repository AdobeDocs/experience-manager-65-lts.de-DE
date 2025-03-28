---
title: Konfigurationseigenschaften für interaktive Kommunikation
description: Bearbeiten Sie die Standardkonfigurationseigenschaften für interaktive Kommunikationen.
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
topic-tags: interactive-communications
docset: aem65
feature: Interactive Communication
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: 73e4cd72-0479-4b3c-82d2-653cded590b9
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 100%

---

# Konfigurationseigenschaften für interaktive Kommunikation{#interactive-communications-configuration-properties}

Interaktive Kommunikation enthält Eigenschaften, die nach der Installation des Pakets [AEM Forms Add-On](../../forms/using/installing-configuring-aem-forms-osgi.md) automatisch konfiguriert werden. Autoren der interaktiven Kommunikation können diese Standardkonfigurationseigenschaften mit Hilfe der Seite **Konfiguration von Adobe Experience Manager Web Console** bearbeiten.

Öffnen Sie die Seite für die **Konfiguration von Adobe Experience Manager Web Console** unter der folgenden URL:

`https:/[server]:[port]/<contextPath>/system/console/configMgr`

Die Konfigurationseigenschaften umfassen Folgendes:

* [Konfiguration für Dokumentfragment](#document-fragments-configuration)
* [Korrespondenzkonfiguration erstellen](#create-correspondence-configuration)
* [Webkanal-Konfiguration für adaptive Formulare und interaktive Kommunikation](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Webkanalthemen-Konfiguration für adaptive Formulare und interaktive Kommunikation](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Konfiguration für Dokumentfragment {#document-fragments-configuration}

Wählen Sie auf der Seite zur **Konfiguration der Adobe Experience Manager-Web-Konsole** die Option **Dokumentfragment-Konfiguration** aus, um die Konfigurationseigenschaften für Dokumentfragmente anzuzeigen.

<table>
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Beschreibung</td> 
   <td>Standard</td> 
   <td>Zulässige Werte</td> 
  </tr> 
  <tr> 
   <td>Datenanzeigeformate</td> 
   <td>Gebietsschema-spezifisches Anzeigeformat für Felder, Variablen und Formulardatenmodellelemente, die beim Erstellen einer interaktiven Kommunikation für Druck- und Webkanäle verfügbar sind.</td> 
   <td> 
    <ul> 
     <li>locale = en_US, de_DE, fr_FR und ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>--</p> </td> 
  </tr> 
  <tr> 
   <td>Einzug</td> 
   <td>Die Breite der einzelnen Einzugseinheit, die auf den Text in Listendokumentfragmenten angewendet wird.</td> 
   <td>12,7 mm</td> 
   <td>Zahl</td> 
  </tr> 
  <tr> 
   <td>Mindestbreite bei römischen Zahlen</td> 
   <td>Mindestbreite für das Aufzählungszeichen- oder Zahlenfeld, wenn römische Zahlen in Listendokumentfragmenten verwendet werden. </td> 
   <td>12,7 mm</td> 
   <td>Zahl</td> 
  </tr> 
  <tr> 
   <td>Mindestbreite bei Zahlen</td> 
   <td>Mindestbreite für das Aufzählungszeichen- oder Zahlenfeld, wenn neben römischen Zahlen nummerierte Listen in Listendokumentfragmenten verwendet werden.</td> 
   <td>8,0 mm</td> 
   <td>Zahl</td> 
  </tr> 
 </tbody> 
</table>

## Erstellen der Korrespondenzkonfiguration {#create-correspondence-configuration}

Wählen Sie auf der Seite zur **Konfiguration der Adobe Experience Manager-Web-Konsole** die Option **Korrespondenzkonfiguration erstellen** aus, um die Konfigurationseigenschaften für die Agent-Benutzeroberfläche anzuzeigen.

<table>
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Beschreibung</td> 
   <td>Standard</td> 
   <td>Zulässige Werte</td> 
  </tr> 
  <tr> 
   <td>Aufgelöste Inhalte zur Bearbeitung anzeigen</td> 
   <td>Aktivieren Sie das Kontrollkästchen, um aufgelöste Inhalte (tatsächliche Werte anstelle von Platzhaltern) anzuzeigen, während Sie Textmodule auf der Agent-Benutzeroberfläche bearbeiten.</td> 
   <td>Nicht ausgewählt</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td>Wasserzeichen während der Vorschau anwenden</td> 
   <td>Aktivieren Sie das Kontrollkästchen, um ein Wasserzeichen auf den Druckkanal der interaktiven Kommunikation im Vorschaumodus anzuwenden.</td> 
   <td>Nicht ausgewählt</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td>Aktivieren der Schrifteinbettung in PDF</td> 
   <td><p>Aktivieren Sie das Kontrollkästchen, um das Einbetten von Schriftarten in die PDF-Dokumente zu aktivieren. Nach Auswahl dieser Option können Sie neue Schriftarten einbetten, nachdem Sie die PDF-Dokumente über die Benutzeroberfläche für Agenten generiert oder in der Vorschau angezeigt haben. Verwenden Sie den Druckkanal der interaktiven Kommunikation, um PDF-Dokumente zu generieren und in der Vorschau anzuzeigen.</p> <p>Das Einbetten von Schriftarten in ein PDF-Dokument ist nützlich, wenn eine Schriftart auf einem Computer verfügbar ist, der zum Generieren des PDF verwendet wird, und nicht auf dem Clientcomputer verfügbar ist, der auf das PDF zugreift.</p> <p>Weitere Informationen zum Einbetten von Schriftarten finden Sie unter <a href="../../forms/using/customize-text-editor.md" target="_blank">Texteditor anpassen</a>.</p> </td> 
   <td>Nicht ausgewählt</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
 </tbody> 
</table>

## Konfiguration des Web-Kanals für adaptive Formulare und interaktive Kommunikation {#adaptive-form-and-interactive-communication-web-channel-configuration}

Wählen Sie auf der Seite zur **Konfiguration der Adobe Experience Manager-Web-Konsole** die Option zur **Web-Kanal-Konfiguration für adaptive Formulare und interaktive Kommunikation** aus, um die Konfigurationseigenschaften für den Web-Kanal für adaptive Formulare und interaktive Kommunikation anzuzeigen. Die folgende Tabelle enthält eine Beschreibung der Eigenschaften, die sich auf die interaktive Kommunikation beziehen:

| Eigenschaft | Beschreibung | Standard | Zulässige Werte |
|---|---|---|---|
| Platzhalter anzeigen | Aktivieren Sie das Kontrollkästchen, um die Anzeige von Platzhaltern für Felder zu aktivieren, die in adaptiven Formularen und in interaktiver Kommunikation enthalten sind. | Ausgewählt | Nicht zutreffend |
| Maximale Cache-Einträge | Legen Sie die maximale Anzahl an adaptiven Formularen und interaktiven Kommunikationen fest, die mithilfe des Cache-Speichers abgerufen werden können. | 100 | Zahl |
| Dateinamen als eindeutig festlegen | Aktivieren Sie das Kontrollkästchen, um eindeutige Namen für Dateien zu erhalten, die als Anlagen in adaptiven Formularen und interaktiven Kommunikationen enthalten sind. | Nicht ausgewählt | Nicht zutreffend |

## Konfiguration der Web-Kanalthemen für adaptive Formulare und interaktive Kommunikation {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Wählen Sie auf der Seite zur **Konfiguration der Adobe Experience Manager-Web-Konsole** die Option **Web-Kanalthemen-Konfiguration für adaptive Formulare und interaktive Kommunikation** aus, um die Konfigurationseigenschaften für die Web-Kanalthemen für adaptive Formulare und interaktive Kommunikationen anzuzeigen.

<table>
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Beschreibung</td> 
   <td>Standard</td> 
   <td>Zulässige Werte</td> 
  </tr> 
  <tr> 
   <td>Liste der Schriftartennamen</td> 
   <td>Liste der Schriften, die beim Erstellen von adaptiven Formularen und interaktiven Kommunikationen verwendet werden können.</td> 
   <td><p>Georgia</p> <p>Book Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Schwarz</p> <p>Auswirkungen</p> <p>Palatino Linotype</p> </td> 
   <td>Alle gültigen Adobe-Server-Schriften</td> 
  </tr> 
 </tbody> 
</table>
