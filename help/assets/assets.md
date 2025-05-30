---
title: Einführung in  [!DNL Adobe Experience Manager Assets]
description: Erstellen, verwalten, verarbeiten und verteilen Sie digitale Assets in Experience Manager. In diesen Handbüchern werden Best Practices, Barrierefreiheitsfunktionen und die Verwendung von AEM 6.5 LTS-Assets beschrieben.
hide: true
feature: Asset Management
role: Leader, Architect, User
solution: Experience Manager, Experience Manager Assets
exl-id: 2f2eb576-4924-4314-b348-c4b290a57fe3
source-git-commit: aafd340d9ef03f9bf12ed23aad5eb03dc055af38
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 100%

---

# Über [!DNL Adobe Experience Manager Assets] als DAM-Lösung {#administering-assets}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/overview) |
| AEM 6.5 | Dieser Artikel |

AEM [!DNL Assets] ist ein Digital Asset Management(DAM)-Tool, das Teil der [!DNL Experience Manager]-Plattform ist und Ihrem Unternehmen die Verwaltung und Verteilung digitaler Assets ermöglicht. Benutzende im Unternehmen können viele Arten von digitalen Assets verwalten, speichern und darauf zugreifen, z. B. Bilder, Videos, Dokumente, Audio-Clips, 3D-Dateien und Rich-Media-Dateien, die im Web, in gedruckten Dokumenten und für die digitale Verteilung verwendet werden können.

## Was ist Digital Asset Management? {#what-is-digital-asset-management}

[!DNL Assets] ermöglicht die unternehmensweite Frei- und Weitergabe der wichtigsten digitalen Assets einer Organisation. Benutzende in einer Organisation können digitale Assets wie Bilder, Grafiken, Audio- und Videodateien sowie Dokumente über eine Webschnittstelle (oder einen CIFS- oder WebDAV-Ordner) speichern, verwalten und aufrufen.

Die [!DNL Assets]-Funktionen von [!DNL Experience Manager] bieten Ihnen folgende Möglichkeiten:

* Hinzufügen und Freigeben von Bildern, Dokumenten sowie Audio- und Videodateien in verschiedenen Dateiformaten.
* Verwalten von Assets durch Gruppierung nach Tags, Lightbox oder Bewertung (Favoriten). Hinzufügen von Anmerkungen zu Assets.
* Aufspüren von Assets, indem Sie nach Dateinamen, dem Volltext von Dokumenten und nach Datumsangaben, Dokumenttyp und Tags suchen.
* Hinzufügen oder Bearbeiten von Metadateninformationen für Assets. Metadaten werden automatisch mit dem entsprechenden Asset in einer Version zusammengefasst. Sie können Asset-Metadaten importieren und exportieren.
* Ausführen von Bildbearbeitungsvorgängen, beispielsweise Skalieren und Hinzufügen von Bildfiltern. Gleichzeitiges Importieren und Exportieren mehrerer digitaler Assets mithilfe eines WebDAV- oder CIFS-Ordners.
* Verwenden von Workflows und Benachrichtigungen, um die gemeinsame Verarbeitung und den gemeinsamen Download mehrerer Assets zu ermöglichen und Zugriffsrechte auf Assets zu verwalten.

### [!DNL Experience Manager Assets] ist mit [!DNL Experience Manager Sites] integriert {#aem-assets-fully-integrated-in-cq-wcm}

[!DNL Assets] ist vollständig mit [!DNL Sites] integriert und funktioniert nahtlos für alle Anwendungsfälle. Wenn Sie z. B. Web-Seiten erstellen, können [!DNL Sites]-Autoren können die digitalen Assets über den Content Finder suchen und verwenden. Die Benutzeroberfläche von [!DNL Assets] entspricht der von [!DNL Sites]. Ausführliche Informationen finden Sie unter [Überblick über Sites](/help/sites-authoring/page-authoring.md).

Die grundlegende Benutzeroberfläche entspricht der von [!DNL Sites]. Ausführliche Informationen finden Sie unter [Überblick über Sites](/help/sites-authoring/page-authoring.md).

### Digital Asset Management und Bildkomponente {#digital-asset-management-versus-image-component}

Um zu bestimmen, ob ein Bild im DAM-Repository bereitgestellt oder eine Bildkomponente verwendet werden soll, ist der Bildlebenszyklus zu berücksichtigen:

* Wenn das Bild denselben Lebenszyklus hat wie die Seite, verwenden Sie die Bildkomponente.
* Wenn das Bild einen eigenen Lebenszyklus hat – beispielsweise, wenn Sie das Bild zweimal oder außerhalb von WCM verwenden –, verwenden Sie [!DNL Assets].

## Was sind digitale Assets? {#what-are-digital-assets}

Ein Asset ist ein digitales Dokument, Bild, Video oder Audio (oder ein Teil davon), das mehrere Ausgabedarstellungen aufweisen kann. Es kann auch Teil-Assets enthalten, z. B. Ebenen in einer Photoshop-Datei, Folien in einer PowerPoint-Datei, Seiten in einem PDF-Dokument oder Dateien in einer ZIP-Datei.

Ein Asset ist im Wesentlichen eine Binärdatei, die zudem Metadaten, Ausgabedarstellungen und Teil-Assets enthalten kann. Ausführliche Informationen finden Sie im [Handbuch zur DAM-Leistung](/help/sites-deploying/assets-performance-sizing.md).

>[!CAUTION]
>
>Das Hochladen bzw. Bearbeiten von sehr vielen Assets (insbesondere von Bildern) kann die Leistung Ihrer [!DNL Experience Manager]-Bereitstellung beeinträchtigen.

### [!DNL Experience Manager Assets] – Terminologie {#aem-assets-terminology}

Bei der Arbeit mit digitalen Assets in [!DNL Experience Manager] ist es hilfreich, mit der folgenden Terminologie vertraut zu sein:

* **Sammlung**: Eine Sammlung von Assets, entweder auf Grundlage ihres physischen Speicherorts (Ordner), allgemeinen Eigenschaften (gespeicherter Suchordner) oder Benutzerauswahl (Lightbox-Ordner).

* **Metadaten**: [!DNL Assets] verfügen über Metadaten, darunter Autorin oder Autor, Ablaufdatum, Digital Rights Management(DRM)-Informationen usw. Metadaten sind unter der Zugangssteuerung zu finden. [!DNL Assets] unterstützt standardmäßig die folgenden allgemeinen Metadaten-Schemata:

   * Dublin Core: einschließlich Autorin oder Autor, Beschreibung, Datum, Thema usw.
   * IPTC: einschließlich Ereignis, Modell, Ort usw.
   * WCM: einschließlich Seiteneigenschaften, [!UICONTROL Einschaltzeit] und [!UICONTROL Ausschaltzeit] usw.

* **Tagging**: [!DNL Assets] können mit Tags versehen und klassifiziert werden. Siehe [Organisieren von Assets](/help/assets/organize-assets.md).

* **Ausgabedarstellungen**: Eine Ausgabedarstellung ist die binäre Darstellung eines Assets. [!DNL Assets] verfügen stets über eine primäre Darstellung, nämlich die der hochgeladenen Datei. Sie können über eine beliebige Anzahl zusätzlicher Darstellungen verfügen, die beispielsweise durch benutzerdefinierte Workflow-Schritte oder beim Hochladen eines Assets erstellt werden. Ausgabedarstellungen können eine andere Größe aufweisen, mit einer anderen Auflösung, einem hinzugefügten Wasserzeichen oder einem anderen geänderten Merkmal.

* **Versionen**: Bei der Versionierung wird eine Momentaufnahme von digitalen Assets zu einem bestimmten Zeitpunkt aufgezeichnet. Sie können frühere Versionen von Assets wiederherstellen. Siehe [Versionierung in [!DNL Assets]](manage-assets.md#asset-versioning).

* **Unter-Assets**: Bei Unter-Assets handelt es sich um Assets, die zusammen ein Asset bilden, z. B. Ebenen in einer [!DNL Adobe Photoshop]-Datei oder Seiten in einer PDF-Datei. In [!DNL Assets] lassen sich Unter-Assets genau so wie normale Assets verwalten.

### Arbeiten mit digitalen Assets {#how-to-work-with-assets}

Sie können für Assets oder Sammlungen Aktionen durchführen. Mit Aktionen können Assets, Sammlungen und Ausgabedarstellungen erstellt oder geändert werden. Viele der grundlegenden Aktionen, die Sie für Assets durchführen können – Hochladen, Löschen, Aktualisieren, Speichern von Unter-Assets –, lösen vorkonfigurierte Workflows aus. Diese sind in [!DNL Assets] automatisch aktiviert und werden in den Medien-Handlern für [!DNL Assets] detailliert beschrieben.

Folgende Aufgaben können Sie mit diesen vorkonfigurierten Workflows durchführen:

* Speichern von Assets in oder Löschen aus dem Repository.
* Extrahieren und Speichern von Metadaten der Assets. Die einzelnen Metadatenelemente werden als XMP gespeichert.
* Generieren von Ausgabedarstellungen und Miniaturansichten der Assets, einschließlich automatischer Skalierung und Zuschnitt, wo erforderlich.
* Transkodieren der Assets, sofern erforderlich. Beispielsweise werden Videos für Mobilgeräte und Verwendung im Netz mit 24 Bildern pro Sekunde transkodiert, für Downloads vorgesehene Videos hingegen mit 30 Bildern pro Sekunde. Audio für Mobilgeräte und Verwendung im Netz wird mit 128 Kbit/s transcodiert, Audio für den Download mit 192 Kbit/s.

Sie können Workflows auch manuell anwenden. Eine Liste der Standard-Workflows finden Sie unter [Medien-Handler in Assets](media-handlers.md).

## [!DNL Experience Manager Assets] und [!DNL Media Library] {#cq-dam-vs-cq-medialibrary}

Informationen zu den Unterschieden finden Sie unter [Assets und Media Library](medialibrary.md).

>[!MORELIKETHIS]
>
>* [Videoeinführung: Experience Manager Assets als modernes DAM-System](https://www.youtube.com/watch?v=PBwQqZgC-yo)
>* [Grundlagen von Metadatenkonzepten](/help/assets/metadata-concepts.md)
