---
title: Eogenschaften der Correspondence Management-Konfiguration
description: In diesem Thema wird erläutert, wie Sie Asset Composer mit lösungsspezifischen Konfigurationen bearbeiten können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: 23be6248-1013-488e-91e6-ac1f6fb7da50
source-git-commit: c714e51f0c0368988ce552969747ab5fce5c186f
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 48%

---

# Eogenschaften der Correspondence Management-Konfiguration {#correspondence-management-configuration-properties}

Öffnen Sie folgende URL einem Browser, um diese Eigenschaftenin zu konfigurieren: `https://<server>:<port>/<contextPath>/system/console/configMgr` und wählen Sie **Correspondence Management-Konfigurationen**.

Correspondence Management verfügt über die folgenden Konfigurationseigenschaften:

<table>
 <tbody>
  <tr>
   <th><p><strong>Eigenschaft</strong></p> </th>
   <th><p><strong>Beschreibung</strong></p> </th>
   <th><p><strong>Standard</strong></p> </th>
   <th><p><strong>Zulässige Werte</strong></p> </th>
  </tr>
  <tr>
   <td><p>Einzug</p> </td>
   <td>Einzug bei Modulen<p> </p> </td>
   <td><p>12,7 mm</p> </td>
   <td><p>Beliebige Zahl</p> </td>
  </tr>
  <tr>
   <td>Mindestbreite bei Zahlen</td>
   <td>Mindestbreite, die auf das Aufzählungs-/Zahlenfeld angewendet wird, wenn nummerierte Listen außer römischen Zahlen verwendet werden.</td>
   <td>8,0 mm</td>
   <td>Beliebige Zahl</td>
  </tr>
  <tr>
   <td><p>Mindestbreite bei römischen Zahlen</p> </td>
   <td><p>Mindestbreite, die bei Verwendung römischer Zahlen auf das Aufzählungs-/Zahlenfeld angewendet wird.</p> </td>
   <td><p>12,7 mm</p> </td>
   <td><p>Beliebige Zahl</p> </td>
  </tr>
  <tr>
   <td>Typ der Ausgabedarstellung</td>
   <td>Der Typ der Ausgabedarstellung, den die Anwendung zum Rendern der Briefvorschau verwendet. </td>
   <td>HTML-Ausgabedarstellung</td>
   <td>HTML-Ausgabedarstellung/PDF-Ausgabedarstellung</td>
  </tr>
  <tr>
   <td><p>CCR-PDF-Hervorhebung aktivieren</p> </td>
   <td><p>Aktiviert die Hervorhebung von PDF in der Anwendung.</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Typ der Zielhervorhebung</p> </td>
   <td><p>Hervorhebungstyp des Ziels in der Anwendung.</p> </td>
   <td><p>border</p> </td>
   <td><p>Rahmen/Füllung/keine</p> </td>
  </tr>
  <tr>
   <td><p>Hervorhebungsfarbe des Ziels</p> </td>
   <td><p>Hervorhebungsfarbe des Ziels in der Anwendung.</p> </td>
   <td><p>90;155;245</p> </td>
   <td><p>Beliebige RGB-Farbe im Format R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Typ der Inhaltshervorhebung</p> </td>
   <td><p>Hervorhebungstyp des Inhalts in der Anwendung.</p> </td>
   <td><p>Füllung</p> </td>
   <td><p>Rahmen/Füllung/keine</p> </td>
  </tr>
  <tr>
   <td><p>Farbe der Inhaltshervorhebung</p> </td>
   <td><p>Hervorhebungsfarbe des Inhalts in der Anwendung.</p> </td>
   <td><p>210;225;245</p> </td>
   <td><p>Beliebige RGB-Farbe im Format R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Typ der Feldhervorhebung</p> </td>
   <td><p>Hervorhebungstyp des Felds in der Anwendung.</p> </td>
   <td><p>Füllung</p> </td>
   <td><p>Rahmen/Füllung/keine</p> </td>
  </tr>
  <tr>
   <td><p>Farbe der Feldhervorhebung</p> </td>
   <td><p>Hervorhebungsfarbe des Feldes in der Anwendung.</p> </td>
   <td><p>210;225;245</p> </td>
   <td><p>Beliebige RGB-Farbe im Format R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Timeout für die Anwendung</p> </td>
   <td><p>Anwendungstimeout in Sekunden.</p> </td>
   <td><p>1.200</p> </td>
   <td><p>Beliebige Zahl</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für PDF-Dokument</p> </td>
   <td><p>Parametername für das PDF-Dokument in der Nachbearbeitung.</p> </td>
   <td><p>inPDFDoc</p> </td>
   <td><p>Beliebiger Name für Zeichenfolge</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für XML-Daten</p> </td>
   <td><p>Parametername für XML-Dokument (Daten) in der Nachbearbeitung.</p> </td>
   <td><p>inXMLDoc</p> </td>
   <td><p>Beliebiger Name für Zeichenfolge</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für XDP-Dokument</p> </td>
   <td><p>Parametername für das XDP-Dokument, das an den Nachbearbeitungsprozess gesendet wird.</p> </td>
   <td><p>inXDPDoc</p> </td>
   <td><p>Beliebiger Name für Zeichenfolge</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für Umleitungs-URL</p> </td>
   <td><p>Parametername für die Umleitungs-URL, die vom Nachbearbeitungsprozess gesendet wird. Dieser Wert kann ein beliebiger Zeichenfolgenvariablenname sein.</p> </td>
   <td><p>redirectURL</p> </td>
   <td><p>Beliebiger Name für Zeichenfolge</p> </td>
  </tr>
  <tr>
   <td><p>Typ der gesendeten PDF</p> </td>
   <td><p>PDF-Übermittlungstyp (Typ der PDF, der beim Senden aus dem Programm generiert wird).</p> </td>
   <td><p>nonInteractive</p> </td>
   <td><p>interaktiv/nicht interaktiv</p> </td>
  </tr>
  <tr>
   <td><p>Datenwörterbuchinstanz optimieren</p> </td>
   <td><p>Aktiviert die optimierte Übertragung der Datenwörterbuchinstanz per Server und Client.</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Inkonsistenzen in der Autokorrektur </p> </td>
   <td><p>Wenn diese Option aktiviert ist, werden mögliche Inkonsistenzen in Briefzuweisungen automatisch verarbeitet.</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Konfigurierte Datenformate verwenden</p> </td>
   <td><p>Steuert, ob konfigurierte Datenbearbeitungs- und Datenanzeigeformate verwendet werden.</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Datenanzeigeformate</p> </td>
   <td><p>Gibt ein Gebietsschema-spezifisches Anzeigeformat für Daten an.</p> </td>
   <td><p>locale=en_US; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=truelocale=de_DE; dateFormat=dd-MM-yyyy; numberDecimalSeparator=,; numberGroupSeparator=.; numberUseGroupSeparator=truelocale=fr_FR; dateFormat=dd-MM-yyyy; numberDecimalSeparator=,; numberGroupSeparator= ; numberUseGroupSeparator=truelocale=ja_JP; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td><p>--</p> </td>
  </tr>
  <tr>
   <td><p>Datenbearbeitungsformat</p> </td>
   <td><p>Das Format für Daten bearbeiten. Wird beim Schreiben von Daten als Zeichenfolge oder beim Analysieren von Daten aus Zeichenfolge verwendet.</p> </td>
   <td><p>locale=en_US; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td>--<p> </p> </td>
  </tr>
  <tr>
   <td><p>Briefinstanzen in Veröffentlichungsinstanz verwalten</p> </td>
   <td><p>Brieffunktion aktivieren/deaktivieren (gilt nur für den Veröffentlichungs-Server).</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung aktivieren</p> </td>
   <td><p>Audit-Funktion aktivieren/deaktivieren. Bei „false“ sind die Auditprotokolle für alle Aktionen deaktiviert.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Asset-Abruf aktivieren</p> </td>
   <td><p>Audit-Funktionen für Asset-Lesevorgänge aktivieren/deaktivieren.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Erstellung aktivieren</p> </td>
   <td><p>Audit-Funktionen für die Asset-Erstellung aktivieren/deaktivieren.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Aktualisierung aktivieren</p> </td>
   <td><p>Audit-Funktionen für die Asset-Aktualisierung aktivieren/deaktivieren.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Wiederherstellung aktivieren</p> </td>
   <td><p>Audit-Funktionen für die Asset-Wiederherstellung aktivieren/deaktivieren.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Veröffentlichung aktivieren</p> </td>
   <td><p>Audit-Funktionen für die Asset-Veröffentlichung aktivieren/deaktivieren.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Speichern von Briefentwürfen aktivieren</p> </td>
   <td><p>Audit-Funktion zum Speichern von Briefentwürfen aktivieren/deaktivieren.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Senden aktivieren</p> </td>
   <td><p>Audit-Funktionen für die Briefsendung aktivieren/deaktivieren.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für E-Mails aktivieren</p> </td>
   <td><p>Audit-Funktion für E-Mails aktivieren/deaktivieren.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Drucken aktivieren</p> </td>
   <td><p>Audit-Funktionen für das Drucken von Briefen aktivieren/deaktivieren.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für benutzerdefinierten Versand aktivieren</p> </td>
   <td><p>Audit-Funktionen für den benutzerdefinierten Versand von Briefen aktivieren/deaktivieren.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für Anlagendokumente</p> </td>
   <td><p>Parametername für Anlagendokumente, die an den Nachbearbeitungsprozess gesendet werden.</p> </td>
   <td><p>inAttachmentDocs</p> </td>
   <td><p>Beliebiger Name für Zeichenfolge</p> </td>
  </tr>
  <tr>
   <td><p>CM-Benutzerstamm</p> </td>
   <td><p>URL des Ordners mit allen Correspondence Management-Benutzer-Assets.</p> </td>
   <td><p>--</p> </td>
   <td><p>Gültiger Ordner-Speicherort</p> </td>
  </tr>
  <tr>
   <td><p>Brief-Cache-Größe</p> </td>
   <td><p>Geben Sie die maximale Anzahl von Briefen an, die im Cache gespeichert werden sollen.</p> <p>Wenn Sie diesen Wert ändern, wird <code>in-memory</code> Cache bereinigt.</p> </td>
   <td><p>100</p> </td>
   <td><p>Jeder numerische Wert</p> </td>
  </tr>
  <tr>
   <td><p>Brief-Cache aktivieren</p> </td>
   <td><p>Aktivieren/Deaktivieren des Brief-Cache.</p> <p>Wenn Sie diesen Wert ändern, wird <code>in-memory </code> Cache bereinigt.</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Reihenfolge von Datenelementen</p> </td>
   <td><p>Sortiert Datenelemente in der Benutzeroberfläche in der Reihenfolge ihrer Reihenfolge im Brief.</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Neuladen unterstützen</p> </td>
   <td><p>Aktivieren/Deaktivieren der Neuladungsunterstützung in Briefen, die Server-seitig gerendert werden.</p> <p>Durch Deaktivieren wird die Leistung beim Rendern von Briefen verbessert.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> <p> </p> </td>
  </tr>
  <tr>
   <td>Temporärer Ordner </td>
   <td>Speicherort des temporären Ordners.</td>
   <td>acm.tpmFolder</td>
   <td> </td>
  </tr>
  <tr>
   <td>Remote speichern</td>
   <td>Speichert die Briefinstanzen auf dem angegebenen verarbeitenden Autorensystem.</td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Kompatibilitätsoptionen</td>
   <td>Kompatibilitätsoptionen des Formats configName : configValue durch Komma getrennt.</td>
   <td>acm.compatibilityOptions</td>
   <td> </td>
  </tr>
  <tr>
   <td><p>Debug-Ordner </p> <p> </p> </td>
   <td>Ordnerpfad im Dateisystem für das Debugging. Wenn das Verzeichnis nicht <code>exists</code> wird, werden keine Debug-Dumps generiert.</td>
   <td>acm.debugDirectory</td>
   <td> </td>
  </tr>
 </tbody>
</table>
