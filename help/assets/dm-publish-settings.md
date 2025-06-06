---
title: Konfigurieren des Veröffentlichungs-Setups von Dynamic Media für Bild-Server
description: Erfahren Sie, wie Sie die Dynamic Media-Veröffentlichungseinstellungen für Bild-Server konfigurieren, damit Sie Assets veröffentlichen können. Sie können Ihre Assets auch testen, bevor Sie sie veröffentlichen.
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
solution: Experience Manager, Experience Manager Assets
exl-id: 9cad4bbc-64f6-4ea2-a9b2-b6b9aaa72f11
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '3364'
ht-degree: 99%

---

# Konfigurieren des Veröffentlichungs-Setups von Dynamic Media für Bild-Server

Die Setup-Optionen für Dynamic Media-Veröffentlichungen können nur konfiguriert werden, wenn Folgendes zutrifft:

* Sie führen Dynamic Media im Scene7-Modus aus. Siehe [Aktivieren von Dynamic Media im Scene7-Modus](/help/assets/config-dms7.md#enabling-dynamic-media-in-scene-mode).
* Sie haben eine *vorhandene* **[!UICONTROL Dynamic Media-Konfiguration]** (in **[!UICONTROL Cloud Services]**) in Adobe Experience Manager. Weitere Informationen finden Sie unter [Erstellen einer Dynamic Media-Konfiguration in Cloud Services](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services).
* Sie sind ein Experience Manager-Systemadministrator mit Administratorrechten.

Das Veröffentlichungs-Setup von Dynamic Media ist für erfahrene Website-Entwickelnde und Programmierende gedacht. Adobe Dynamic Media empfiehlt, dass Benutzende, die die Veröffentlichungseinstellungen ändern, mit Adobe Dynamic Media, HTTP-Protokollstandards und -Konventionen und grundlegender Bildbearbeitungstechnologie vertraut sind.

Auf der Seite „Veröffentlichungseinstellungen von Dynamic Media“ werden Standardeinstellungen festgelegt, die festlegen, wie Assets von Adobe Dynamic Media-Servern für Websites oder Programme bereitgestellt werden. Wenn keine Einstellung festgelegt ist, stellt der Adobe Dynamic Media-Server ein Asset gemäß einer Standardeinstellung bereit, die auf der Seite „Veröffentlichungseinstellungen von Dynamic Media“ konfiguriert wurde.

Informationen zu weiteren optionalen Konfigurationsaufgaben finden Sie unter [Optional – Einrichtung und Konfiguration der Scene7-Modus-Einstellungen von Dynamic Media](/help/assets/config-dms7.md#optional-setup-and-configuration-of-dynamic-media-scene7-mode-settings).

>[!NOTE]
>
>Sie möchten ein Upgrade von Dynamic Media Classic auf Dynamic Media auf Adobe Experience Manager durchführen? Die Seite [Allgemeine Einstellungen](/help/assets/dm-general-settings.md) und die Seite zu Veröffentlichungseinstellungen in Dynamic Media werden vorab mit den Werten ausgefüllt, die von Ihrem Dynamic Media Classic-Konto übernommen werden. Die Ausnahmen sind alle Werte, die im Bereich **[!UICONTROL Standardmäßige Upload-Optionen]** auf der Seite „Allgemeine Einstellungen“ angezeigt werden. Diese Werte befinden sich bereits in Experience Manager. Alle Änderungen, die Sie unter **[!UICONTROL Standardmäßige Upload-Optionen]** auf einer der fünf Registerkarten in der Experience Manager-Benutzeroberfläche vornehmen, werden in Dynamic Media, nicht jedoch in Dynamic Media Classic angezeigt. Alle anderen Einstellungen und Werte auf der Seite [Allgemeine Einstellungen](/help/assets/dm-general-settings.md) und der Seite „Veröffentlichungseinstellungen“ werden von Dynamic Media Classic und Dynamic Media in Experience Manager verwaltet.

**So konfigurieren Sie den Dynamic Media Publish Setup Image Server:**

1. Klicken Sie im Autorenmodus in Experience Manager auf das Experience Manager-Logo, um auf die Konsole für die globale Navigation zuzugreifen.
1. Klicken Sie in der linken Leiste auf das Symbol „Tools“ und navigieren Sie dann zu **[!UICONTROL Assets]** > **[!UICONTROL Veröffentlichungs-Setup für Dynamic Media]**.
1. Wählen Sie auf der Seite „Bild-Server“ aus der Dropdown-Liste Ihren Veröffentlichungskontext aus, um die Standardeinstellungen für die Bereitstellung von Bildern von Bild-Servern festzulegen.

| Veröffentlichungskontext | Beschreibung |
| --- | --- |
| Bereitstellung von Bildern | Gibt den Kontext für Veröffentlichungseinstellungen an. |
| Bereitstellung von Testbildern | Gibt den Kontext für das Testen von Veröffentlichungseinstellungen an.<br>Nur für neue Dynamic Media-Konten wird das Feld **[!UICONTROL Client-Adresse]** standardmäßig automatisch auf `127.0.0.1` gesetzt.<br>Siehe [Testen von Assets, bevor sie veröffentlicht werden](#test-assets-before-making-public). |

1. Konfigurieren Sie auf den fünf Registerkarten die Standardeinstellungen des Veröffentlichungskontexts.

   * Registerkarte [Sicherheit](#security-tab)
   * Registerkarte [Katalogverwaltung](#catalog-management-tab)
   * Registerkarte [Anfrage-Attribute](#request-attributes-tab)
   * Registerkarte [Allgemeine Attribute für Miniaturansichten](#common-thumbnail-attributes-tab)
   * Registerkarte [Farb-Management-Attribute](#color-management-attributes-tab)

   ![Seite mit den Dynamic Media-Veröffentlichungseinstellungen](/help/assets/assets-dm/dm-publish-setup.png)
   *Seite „Dynamic Media-Veröffentlichungseinstellungen“ mit ausgewählter Registerkarte **[!UICONTROL Anfrage-Attribute]**.*<br><br>

1. Wenn Sie fertig sind, wählen Sie in der rechten oberen Ecke der Seite **[!UICONTROL Speichern]** aus. 

## Registerkarte „Sicherheit“ {#security-tab}

>[!NOTE]
>
>Sicherheitseinstellungen werden für den Veröffentlichungskontext *Bereitstellung von Bildern* nicht unterstützt.

Wenn *Bereitstellung von Testbildern* als Veröffentlichungskontext festgelegt ist, können Sie die folgende Sicherheitseinstellung festlegen:

**[!UICONTROL Client-Adresse]**: Hier können Sie eine oder mehrere IP-Adressen oder IP-Adressbereiche angeben. Wenn diese Option angegeben ist, werden Anfragen an diesen Bildkatalog abgelehnt, wenn sie von einem Client stammen, der eine nicht aufgeführte IP-Adresse hat. Diese Regel gilt sowohl für die Bereitstellung von Bildern als auch für gerenderte Bilder.

![Registerkarte „Sicherheit“](/help/assets/assets-dm/dm-ipallowlist.png)<br>*Die Registerkarte „Sicherheit“ enthält das Feld „IP zulassen“.*

## Registerkarte „Katalogverwaltung“ {#catalog-management-tab}

**[!UICONTROL Dateipfad für Definitionsregeln]**: Gibt die Datei an, die die Regelsatzdefinitionen für den Bildkatalog enthält.

Siehe auch den Parameter [RuleSetFile](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-rulesetfile) im Dynamic Media Viewer-Referenzhandbuch.

>[!NOTE]
>
>Wenn für Ihr Dynamic Media Classic-Konto ein **[!UICONTROL Dateipfad für Regelsatzdefinitionen]** unter **[!UICONTROL Setup]** > **[!UICONTROL Anwendung]** > **[!UICONTROL Veröffentlichungs-Setup]** ausgewählt ist, ruft Experience Manager die Datei ab. Ihr Dynamic Media-Konto ruft die Datei von Dynamic Media Classic ab. Die Datei wird dann gespeichert und in diesem Feld verfügbar gemacht, wenn Sie die **[!UICONTROL Veröffentlichungseinstellungen für Dynamic Media]** zum ersten Mal öffnen.

## Registerkarte „Anfrage-Attribute“ {#request-attributes-tab}

Diese Einstellungen beziehen sich auf das standardmäßige Erscheinungsbild von Bildern.

| Einstellung | Beschreibung |
| --- | --- |
| **[!UICONTROL Maximale Größe des Antwortbildes]** | Erforderlich.<br>Nur für neue Dynamic Media-Konten werden die Standardgrößenbeschränkungen automatisch auf „Breite: `3000`“ und „Höhe: `3000`“ sowohl für die **[!UICONTROL Bereitstellung von Bildern]** als auch für die **[!UICONTROL Bereitstellung von Testbildern]** festgelegt.<br>Gibt die maximale Breite und Höhe des Antwortbildes an, das an den Client zurückgegeben wird. Der Server gibt einen Fehler zurück, wenn eine Anfrage zu einem Antwortbild führt, dessen Breite und/oder Höhe größer als diese Einstellung ist.<br>Siehe auch den Parameter [MaxPix](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-maxpix) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Verschleierungsmodus für Anfragen]** | Aktivieren Sie diese Option, wenn die base64-Codierung auf gültige Anfragen angewendet werden soll.<br>Siehe auch den Parameter [RequestObfuscation](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestobfuscation) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Verschlüsselungsmodus für Anfragen]** | Aktivieren Sie diese Option, wenn in Anfragen eine einfache Hash-Sperre enthalten sein soll.<br>Siehe auch den Parameter [RequestLock](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestlock) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardattribute für Anfragen]** | |
| **[!UICONTROL Standarderweiterung für Bilddatei]** | Erforderlich.<br>Standard-Datendateierweiterung, die an die Werte für Katalogpfad und Maskenpfad angehängt wird, wenn der Pfad keine Dateiendung enthält.<br>Siehe auch den Parameter [DefaultExt](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultext) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Name der Standardschriftart]** | Gibt an, welche Schriftart verwendet wird, wenn keine Schriftart durch eine Textebenenanforderung bereitgestellt wird. Wenn angegeben, muss es sich um einen gültigen Schriftnamenswert in der Schriftzuordnung dieses Bildkatalogs oder der Schriftzuordnung des Standardkatalogs handeln.<br>Siehe auch den Parameter [DefaultFont](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultfont) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardbild]** | Wenn bei einer Anfrage ein angefordertes Bild nicht gefunden werden kann, wird ein Standardbild angezeigt.<br>Siehe auch den Parameter [DefaultImage](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-defaultimage) im Dynamic Media Viewer-Referenzhandbuch.<br>**HINWEIS**: Wenn für Ihr Dynamic Media Classic-Konto **[!UICONTROL Standardbild]** unter **[!UICONTROL Setup]** > **[!UICONTROL Anwendung]** > **[!UICONTROL Veröffentlichungs-Setup]** ausgewählt ist, ruft Experience Manager in der Gruppe **[!UICONTROL Standardattribute für Anfragen]** die Datei ab. Die Datei wird dann gespeichert und in diesem Feld verfügbar gemacht, wenn Sie die **[!UICONTROL Veröffentlichungseinstellungen für Dynamic Media]** zum ersten Mal öffnen. |
| **[!UICONTROL Standardbildmodus]** | Wenn das Schiebereglerfeld aktiviert ist (Schieberegler auf der rechten Seite), ersetzt **[!UICONTROL Standardbild]** jede fehlende Ebene im Quellbild durch das Standardbild und gibt die Kombination wie gewohnt zurück. Wenn das Regler-Feld deaktiviert ist (Regler links), ersetzt das Standardbild das gesamte zusammengesetzte Bild, selbst wenn das fehlende Bild nur eine von mehreren Ebenen ist.<br>Siehe auch den Parameter [DefaultImageMode](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultimagemode) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standard-Ansichtsgröße]** | Erforderlich.<br>Nur für neue Dynamic Media-Konten werden die standardmäßigen Ansichtsgrößen automatisch auf „Breite: `1280`“ und „Höhe: `1280`“ sowohl für die **[!UICONTROL Bereitstellung von Bildern]** als auch für die **[!UICONTROL Bereitstellung von Testbildern]** festgelegt.<br>Der Server schränkt Antwortbilder dahingehend ein, dass ihre Breite und Höhe nicht größer sind als diese Werte, wenn die Anfrage die Anzeigegröße nicht explizit mithilfe von `wid=`, `hei=` oder `scl=` angibt.<br>Siehe auch den Parameter [DefaultPix](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultpix) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardgröße für Miniaturansichten]** | Erforderlich.<br>Wird anstelle des Attributs **[!UICONTROL Standardansichtsgröße]** für Miniaturanfragen (`req=tmb`) verwendet. Der Server schränkt Antwortbilder dahingehend ein, dass sie nicht größer sind als diese Breite und Höhe, wenn eine Miniaturbildanforderung (`req=tmb`) die Größe nicht explizit mithilfe von `wid=`, `hei=` oder `scl=` angibt.<br>Siehe auch den Parameter [DefaultThumbPix](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultthumbpix) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standard-Hintergrundfarbe]** | Gibt den RGB-Wert an, mit dem alle Bereiche des Antwortbildes gefüllt werden, die keine Bilddaten enthalten.<br>Siehe auch den Parameter [BkgColor](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-bkgcolor) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Attribute für JPEG-Codierung]** |  |
| **[!UICONTROL Qualität]** | <br>Legt die Standardattribute von JPEG-Antwortbildern fest.<br>Nur für neue Dynamic Media-Konten werden die Standardwerte für **[!UICONTROL Qualität]** automatisch auf `80` sowohl für die **[!UICONTROL Bereitstellung von Bildern]** als auch für die **[!UICONTROL Bereitstellung von Testbildern]** festgelegt.<br>Dieses Feld wird im Bereich von 1 bis 100 definiert.<br>Siehe auch den Parameter [JpegQuality](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-jpegquality) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Chromatisches Downsampling]** | Aktiviert bzw. deaktiviert das chromatische Downsampling, das von der JPEG-Codierung verwendet wird. |
| **[!UICONTROL Standard-Resampling-Modus]** | Gibt die standardmäßigen Resampling- und Interpolationsattribute an, die für die Skalierung von Bilddaten verwendet werden. Verwenden Sie dies, wenn `resMode` in einer Anforderung nicht angegeben wird.<br>Nur für neue Dynamic Media-Konten werden die standardmäßigen Resampling-Modi automatisch auf `Sharp2` sowohl für die **[!UICONTROL Bereitstellung von Bildern]** als auch für die **[!UICONTROL Bereitstellung von Testbildern]** festgelegt.<br>Siehe auch den Parameter [ResMode](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-resmode) im Dynamic Media Viewer-Referenzhandbuch. |

## Registerkarte „Allgemeine Attribute für Miniaturansichten“ {#common-thumbnail-attributes-tab}

Diese Einstellungen beziehen sich auf die standardmäßige Darstellung und Ausrichtung von Miniaturansichten.

| Einstellung | Beschreibung |
| --- | --- |
| **[!UICONTROL Standardhintergrundfarbe für Miniaturansicht]** | Gibt den RGB-Wert an, der zum Ausfüllen des Bereichs eines Ausgabeminiaturbilds verwendet wird, das keine tatsächlichen Bilddaten enthält. Wird nur für Anforderungen von Miniaturansichten (`req=tmb`) verwendet und wenn der **[!UICONTROL Standardtyp für Miniaturansichten]** auf **[!UICONTROL Anpassen]** oder **[!UICONTROL Textur]** festgelegt ist.<br>Siehe auch den Parameter [ThumbBkgColor](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbbkgcolor) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Horizontale Ausrichtung]** | Gibt die horizontale Ausrichtung des Miniaturbilds im Rechteck des Antwortbilds an, angegeben durch die Werte `wid=` und `hei=`.<br>Wird nur für Anforderungen von Miniaturansichten (`req=tmb`) verwendet und wenn der **[!UICONTROL Standardtyp für Miniaturansichten]** auf **[!UICONTROL Anpassen]** festgelegt ist.<br>Es gibt drei horizontale Ausrichtungen zur Auswahl: **[!UICONTROL Ausrichtung zentriert]**, **[!UICONTROL Linksbündig]** und **[!UICONTROL Rechtsbündig]**.<br>Siehe auch den Parameter [ThumbHorizAlign](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbhorizalign) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Vertikale Ausrichtung]** | Gibt die vertikale Ausrichtung des Miniaturbilds im Rechteck des Antwortbilds an, angegeben durch die Werte `wid=` und `hei=`. Wird nur für Anforderungen von Miniaturansichten (`req=tmb`) verwendet und wenn der **[!UICONTROL Standardtyp für Miniaturansichten]** auf **[!UICONTROL Anpassen]** festgelegt ist.<br>Es gibt drei vertikale Ausrichtungen zur Auswahl: **[!UICONTROL Ausrichtung oben]**, **[!UICONTROL Ausrichtung zentriert]** und **[!UICONTROL Ausrichtung unten]**.<br>Siehe auch den Parameter [ThumbVertAlign](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbvertalign) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standard-Cache für Time-to-Live]** | Ein standardmäßiges Ablaufintervall in Stunden ist vorgegeben für den Fall, dass ein bestimmter Katalogeintrag keinen gültigen Katalog-Ablaufwert aufweist. Legen Sie die Einstellung auf `-1` fest, um dies als nie ablaufend zu markieren. <br>Siehe auch den Parameter [Ablauf](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-expiration) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardtyp für Miniaturansichten]** | Ein Standard für den Typ von Miniaturansichten wird für den Fall angegeben, dass ein bestimmter Katalogdatensatz keinen gültigen ThumbType-Katalogwert aufweist. Wird nur für Anfragen von Miniaturansichten verwendet (`req=tmb`).<br>Es gibt drei Typen von Miniaturansichten, aus denen Sie wählen können: **[!UICONTROL Zuschneiden]**, **[!UICONTROL Anpassen]** und **[!UICONTROL Textur]**.<br>Siehe auch den Parameter [ThumbType](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbtype) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardauflösung für Miniaturansichten]** | Ein Standardwert für die Objektauflösung für Miniaturansichten wird für den Fall angegeben, dass ein bestimmter Katalogdatensatz keinen gültigen ThumbRes-Katalogwert aufweist. Wird nur für Anfragen von Miniaturansichten verwendet (`req=tmb`) und wenn die Einstellung **[!UICONTROL Standardtyp für Miniaturansichten]** auf **[!UICONTROL Textur]** festgelegt ist.<br>Siehe auch den Parameter [ThumbRes](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbres) im Dynamic Media Viewer-Referenzhandbuch. |

## Registerkarte „Farbverwaltungsattribute“ {#color-management-attributes-tab}

Diese Einstellungen bestimmen, welche ICC-Farbprofile für Bilder verwendet werden.

**Rendering-Intent für Farbkonvertierung**
Ein Rendering-Intent für die Farbkonvertierung ermöglicht das Überschreiben des standardmäßigen Rendering-Intents der Arbeitsprofile, um zu bestimmen, wie die Quellfarben angepasst werden. Verwendung:

1. Eines der standardmäßigen ICC-Profile ist der Zielfarbraum einer Farbkonvertierung.
1. Dieses Profil kennzeichnet ein Ausgabegerät, wie etwa einen Drucker oder einen Monitor.
1. Der angegebene Rendering-Intent ist für dieses Profil gültig.

Verschiedene Rendering-Intents verwenden unterschiedliche Regeln, um zu bestimmen, wie die Quellfarben angepasst werden.

Siehe auch den Parameter [IccRenderIntent](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccrenderintent) im Dynamic Media Viewer-Referenzhandbuch.

>[!NOTE]
>
>Verwenden Sie im Allgemeinen den standardmäßigen Rendering Intent für die ausgewählte Farbeinstellung. Dieser wurde von Adobe auf die Einhaltung von Branchenstandards getestet. Wenn Sie beispielsweise eine Farbeinstellung für Nordamerika oder Europa auswählen, lautet der standardmäßige Rendering-Intent der Farbkonvertierung **[!UICONTROL Relativ farbmetrisch]**. Wenn Sie eine Farbeinstellung für Japan auswählen, lautet der standardmäßige Rendering-Intent der Farbkonvertierung **[!UICONTROL Wahrnehmungsoptimiert]**.

| Einstellung | Merkmale |
| --- | --- |
| **[!UICONTROL CMYK-Standardfarbraum]** | Gibt den Namen des ICC-Farbprofils an, das als Arbeitsprofil für CMYK-Daten verwendet werden soll. Wenn **[!UICONTROL Keine Angabe]** ausgewählt ist, wird das Farbmanagement für diesen Bildkatalog deaktiviert, wenn CMYK-Quellbilder verwendet werden. Alle CMYK-Arbeitsbereiche sind geräteabhängig, sie basieren also auf tatsächlichen Tinten- und Papierkombinationen. Die von Adobe bereitgestellten CMYK-Arbeitsbereiche basieren auf den üblichen kommerziellen Druckbedingungen.<br> Siehe auch [IccProfileCMYK-Parameter](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilecmyk) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Graustufen-Standardfarbraum]** | Gibt den Namen des ICC-Farbprofils an, das als Arbeitsprofil für Graustufendaten verwendet werden soll. Wenn **[!UICONTROL Keine Angabe]** ausgewählt ist, wird das Farbmanagement für diesen Bildkatalog deaktiviert, wenn Quellbilder mit Graustufen verwendet werden.<br>Siehe auch den Parameter [IccProfileGray](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilegray) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL RGB-Standardfarbraum]** | Gibt den Namen des ICC-Farbprofils an, das als Arbeitsprofil für RGB-Daten verwendet werden soll. Wenn **[!UICONTROL Keine Angabe]** ausgewählt ist, wird das Farbmanagement für diesen Bildkatalog deaktiviert, wenn RGB-Quellbilder verwendet werden. Im Allgemeinen ist es am besten, **[!UICONTROL Adobe RGB]** oder **[!UICONTROL sRGB]** statt des Profils für ein bestimmtes Gerät (z. B. ein Monitorprofil) auszuwählen. **[!UICONTROL sRGB]** wird empfohlen, wenn Sie Bilder für das Internet oder mobile Geräte vorbereiten, da dadurch der Farbraum des Standardmonitors definiert wird, der zum Anzeigen von Bildern im Internet verwendet wird. **[!UICONTROL sRGB]** ist auch eine gute Wahl, wenn Sie mit Bildern von handelsüblichen Digitalkameras arbeiten, da die meisten dieser Kameras sRGB als Standardfarbraum verwenden.<br>Siehe auch den Parameter [IccProfileRGB-](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilergb) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Rendering Intent für Farbkonvertierung]** | **[!UICONTROL Wahrnehmungsoptimiert]**: Ziel ist es, die visuelle Beziehung zwischen Farben so zu erhalten, dass sie für das menschliche Auge als natürlich wahrgenommen werden, auch wenn sich die Farbwerte selbst ändern können. Dieser Intent eignet sich für fotografische Bilder mit vielen Farben, die außerhalb der Farbskala liegen. Diese Einstellung ist der standardmäßige Rendering-Intent für die japanische Druckindustrie. |
|  | **[!UICONTROL Relativ farbmetrisch]** – Vergleicht die extreme Hervorhebung des Quellfarbraums mit der des Zielfarbraums und verschiebt alle Farben entsprechend. Die Farben außerhalb der Farbskala werden zur nächstmöglichen reproduzierbaren Farbe im Zielfarbraum verschoben. Mit „Relativ farbmetrisch“ erhalten Sie mehr Originalfarben in einem Bild als mit „Wahrnehmungsoptimiert“. Diese Einstellung ist der standardmäßige Rendering-Intent beim Drucken in Nordamerika und Europa. |
|  | **[!UICONTROL Sättigung]** – Versucht, auf Kosten der Farbgenauigkeit lebendige Farben in einem Bild zu produzieren. Dieser Rendering-Intent eignet sich für Geschäftsgrafiken wie Diagrammen, bei denen helle gesättigte Farben wichtiger sind als die exakte Beziehung zwischen Farben. |
|  | **[!UICONTROL Absolut farbmetrisch]**: Lässt Farben, die sich im Zielfarbraum befinden, unverändert. Farben außerhalb des Farbraums werden abgeschnitten. Es wird keine Skalierung der Farben auf den Ziel-Weißpunkt durchgeführt. Diese Absicht dient der Einhaltung der Farbgenauigkeit auf Kosten der Beibehaltung von Beziehungen zwischen Farben und ist für Korrekturabzüge geeignet, die die Ausgabe eines bestimmten Geräts simulieren. Dieser Zweck ist nützlich für die Vorschau, wie die Papierfarbe sich auf die gedruckten Farben auswirkt. |

## Testen von Assets vor der Veröffentlichung {#test-assets-before-making-public}

Mit Secure Testing können Sie eine sichere Testumgebung definieren und eine robuste Business-to-Business-Lösung erstellen, die auf einem konfigurierbaren Satz von IP-Adressen und -Bereichen basiert. Mit dieser Funktion können Sie Ihre Adobe Dynamic Media-Bereitstellungen mit der Architektur Ihres Content-Management- und Business-Systems abgleichen.

Mit Secure Testing können Sie eine Vorschau der Staging-Version der Website mit unveröffentlichten Inhalten anzeigen.

Aus den folgenden Gründen sollten Sie bei Bedarf eine Staging-Umgebung erstellen, anstatt Assets öffentlich verfügbar zu machen:

* Vorschau von Websites vor dem öffentlichen Start (Staging-Website).
* Bereitstellen von Assets, die eingeschränkten Zugriff erfordern, wie z. B. E-Kataloge, die Preise in einer B2B-Web-Anwendung anzeigen.
* Verwenden von Assets hinter einer Firewall als Teil eines Produktinformations-Management-Systems, einer Kundendienstanwendung, einer Schulungs-Website usw.

>[!NOTE]
>
>Secure Testing hat keine Auswirkungen auf den Zugriff auf Adobe Dynamic Media Classic. Die Adobe Dynamic Media Classic-Sicherheit bleibt konsistent und erfordert die üblichen Anmeldeinformationen für den Zugriff auf Adobe Dynamic Media Classic und zugehörige Web-Services.

### Funktionsweise von Secure Testing {#how-test-assets-works}

Die meisten Unternehmen betreiben ihr Internet hinter einer Firewall. Der Zugang zum Internet ist über bestimmte Routen und in der Regel über eine begrenzte Anzahl öffentlicher IP-Adressen möglich.

Über Ihr Unternehmensnetzwerk können Sie mithilfe von Websites wie [https://www.whatismyip.com](https://www.whatismyip.com/de/) Ihre IP-Adresse in Erfahrung bringen oder Sie fordern diese Information einfach von Ihrem IT-Unternehmen an.

Mit Secure Testing richtet Adobe Dynamic Media einen dedizierten Image-Server für Staging-Umgebungen oder interne Programme ein. Mit einer beliebigen Anfrage an diesen Server wird die Ursprung-IP-Adresse geprüft. Wenn die eingehende Anfrage nicht in der Liste genehmigter IP-Adressen enthalten ist, erfolgt die Antwort mit einer Fehlermeldung. Firmenadmins, die für Adobe Dynamic Media zuständig sind, konfigurieren die Liste der genehmigten IP-Adressen für die Secure Testing-Umgebung der Firma.

Da der Ort der ursprünglichen Anfrage bestätigt werden muss, wird der Traffic des Secure Testing-Services nicht über ein Inhaltsverteilungsnetzwerk geleitet, wie der öffentliche Traffic des Dynamic Media Image Servers. Anfragen an den Secure Testing-Service weisen im Vergleich zu den öffentlichen Dynamic Media-Bild-Servern eine etwas höhere Latenz auf.

Nicht veröffentlichte Assets sind sofort über die Secure Testing-Services verfügbar, ohne dass sie veröffentlicht werden müssen. Auf diese Weise können Sie eine Vorschau ausführen, bevor Assets auf ihrem öffentlichen Bild-Server veröffentlicht werden.

>[!NOTE]
>
>Secure Testing-Services verwenden den Katalog-Server, der mit einem internen Veröffentlichungskontext konfiguriert ist. Wenn Ihr Unternehmen für die Veröffentlichung auf Secure Testing konfiguriert ist, werden daher hochgeladene Assets in Adobe Dynamic Media sofort in den Secure Testing-Services verfügbar. Diese Funktionen gelten unabhängig davon, ob die Assets beim Hochladen zur Veröffentlichung markiert sind.

Secure Testing-Services unterstützen derzeit die folgenden Asset-Typen und -Funktionen:

* Bilder.
* Vignetten (Rendering-Server-Anfragen).
* Kundinnen und Kunden müssen explizit Rendering-Server-Support anfordern, der verfügbar ist.
* Sets, einschließlich Bildsets, E-Katalog, Rendering-Sets und Mediensets.
* Standardmäßige Adobe Dynamic Media-Rich-Media-Viewer.
* Adobe Dynamic Media-On-Demand-JSP-Seiten.
* Statische Inhalte wie PDF-Dateien und progressiv bereitgestellte Videos.
* HTTP-Video-Streaming.
* Progressives Video-Streaming.

Die folgenden Asset-Typen und -Funktionen werden derzeit nicht unterstützt:

* Adobe Dynamic Media Classic-Info- oder E-Katalog-Suche
* RTMP-Video-Streaming
* Web-to-Print
* UGC-Services (benutzergenerierte Inhalte)

  >[!IMPORTANT]
  >
  >Ab dem 1. Mai 2023 stehen UGC-Assets in Dynamic Media bis zu 60 Tage ab dem Datum des Uploads zur Verfügung. Nach 60 Tagen werden die Assets entfernt.

  >[!NOTE]
  >
  >Die Unterstützung für neue oder vorhandene UGC-Vektorbild-Assets in Adobe Dynamic Media wurde am 30. September 2021 eingestellt.

### Testen des Secure Testing-Services {#test-secure-testing-service}

Gehen Sie wie folgt vor, um sicherzustellen, dass der Secure Testing-Service erwartungsgemäß funktioniert:

#### Bereiten Sie Ihr Konto vor

1. Wenden Sie sich an die Kundenunterstützung von Adobe und bitten Sie sie, Secure Testing für Ihr Konto zu aktivieren.
1. Wählen Sie in Adobe Experience Manager **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Veröffentlichungseinstellungen für Dynamic Media]**.
1. Wählen Sie auf der Seite „Image-Server“ in der Dropdown-Liste **[!UICONTROL Veröffentlichungskontext]** die Option **[!UICONTROL Image-Serving testen]** aus.
1. Wählen Sie die Registerkarte **[!UICONTROL Sicherheit]**.
1. Wählen Sie für den Filter **[!UICONTROL Client-Adresse]** die Option **[!UICONTROL Hinzufügen]**.
1. Geben Sie in das Feld **[!UICONTROL IP-Adresse]** eine IP-Adresse ein.
1. Geben Sie in das Feld **[!UICONTROL Maske]** eine Netzmaske ein.

   >[!NOTE]
   >
   >Wenn Sie mehr als eine IP-Adresse und Netzmaske hinzufügen, ermöglicht dies effektiv *allen* IP-Adressen, Asset-Aufrufe durchzuführen, und sie werden alle angezeigt.

1. Führen Sie einen der folgenden Schritte aus:

   * Um weitere IP-Adressen hinzuzufügen, wiederholen Sie die drei vorherigen Schritte.
   * Fahren Sie mit dem nächsten Schritt fort.

1. Klicken Sie in der rechten oberen Ecke der Seite „Image-Server“ auf **[!UICONTROL Speichern]**.
1. Laden Sie die gewünschten Bilder in Ihr Adobe Dynamic Media-Konto hoch.

<!--    See [Upload files](uploading-files.md#uploading_files). -->

1. Stellen Sie sicher, dass einige der Bilder zur Veröffentlichung markiert und andere nicht markiert sind, und senden Sie dann den Veröffentlichungsauftrag.

<!--    See [Publish files](publishing-files.md#publishing_files). -->

1. Bestimmen Sie den Namen Ihres Secure Testing-Services, indem Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Allgemeine Dynamic Media-Einstellungen]** gehen.
1. Suchen Sie auf der Seite **[!UICONTROL Server]** den Server-Namen rechts neben **[!UICONTROL Veröffentlichungs-Server-Name]**.

Wenden Sie sich an die Adobe-Kundenunterstützung, wenn der Servername fehlt oder die URL zum Server nicht funktioniert.

#### Vorbereiten von Website-Varianten

Sie benötigen zwei Varianten einer Website, auf der einmal die veröffentlichten und einmal die nicht veröffentlichten Assets verknüpft sind:

* Öffentliche Version: Verknüpfen Sie Assets mithilfe Ihrer üblichen URL-Syntax von Adobe Dynamic Media.
* Staging-Version: Verknüpfen Sie Assets mithilfe derselben Syntax, aber mit dem Namen der Secure Testing-Site.

#### Ausführen der Tests

Führen Sie die folgenden Tests durch:

1. Überprüfen Sie, ob Assets in Ihrem Unternehmensnetzwerk sichtbar sind.

   Innerhalb des Unternehmensnetzwerks, das durch den zuvor definierten IP-Adressbereich identifiziert wurde, zeigt die Staging-Version der Website alle Bilder an, unabhängig davon, ob sie zur Veröffentlichung markiert wurden oder nicht. Daher können Sie hier Tests durchführen, ohne Bilder versehentlich vor der Genehmigung der Vorschau oder dem Produktstart verfügbar zu machen.

   Vergewissern Sie sich, dass die öffentliche Version Ihrer Site veröffentlichte Assets anzeigt, wie Sie es bereits von Adobe Dynamic Media gewohnt sind.

1. Vergewissern Sie sich von außerhalb Ihres Unternehmensnetzwerks, dass nicht veröffentlichte (d. h. nicht zur Veröffentlichung markierte) Assets vor dem Zugriff Dritter geschützt sind.

   Greifen Sie dazu von außerhalb auf Ihr Netzwerk zu (z. B. von Ihrem privaten Computer oder über eine 4G/5G-Verbindung) und überzeugen Sie sich davon, dass in der öffentlichen Version der Site alle veröffentlichten Assets, aber keine unveröffentlichten Inhalte angezeigt werden.

   Vergewissern Sie sich, dass in der Staging-Version kein Asset angezeigt wird, da Sie von einer nicht genehmigten IP-Adresse aus auf den Secure Testing-Service zugreifen.
