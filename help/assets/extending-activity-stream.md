---
title: Integrieren von  [!DNL Assets]  in den Aktivitäts-Stream
description: Beschreibt die Aufzeichnungsfunktionen von  [!DNL Experience Manager]  und die Konfiguration zum Aufzeichnen bestimmter Ereignisse.
contentOwner: AG
role: Developer
feature: Asset Management
solution: Experience Manager, Experience Manager Assets
exl-id: 44604607-e49d-469c-a6f1-dedbcd657d65
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 99%

---

# Integrieren von [!DNL Assets] in den Aktivitäts-Stream {#integrating-assets-with-activity-stream}

[!DNL Adobe Experience Manager Assets]-Benutzende führen viele Aktionen durch, z. B. das Erstellen, Hochladen und Löschen von Assets. Diese Aktionen können aufgezeichnet werden, sodass Sie für eine Person einen Aktivitätenverlauf erstellen können. Dieser Abschnitt beschreibt die Aufzeichnungsfunktionen von [!DNL Experience Manager] und wie sich [!DNL Experience Manager] für die Aufzeichnung bestimmter Ereignisse konfigurieren lässt.

## Überlegungen zur Leistung und Standardverhalten {#performance-considerations-and-default-behavior}

Diese Integration kann CPU- und Speicherplatz-intensiv sein, beispielsweise beim Massenimport. Aus diesen Gründen ist die [!DNL Assets]-Integration in den Aktivitäts-Stream standardmäßig deaktiviert.

## Unterstützte Aktionsereignisse {#supported-action-events}

Sie können die folgenden Ereignisse für die Aufzeichnung konfigurieren:

* Lizenz akzeptiert (ACCEPTED)
* Asset erstellt (ASSET_CREATED)
* Asset verschoben (ASSET_MOVED)
* Asset entfernt (ASSET_REMOVED)
* Lizenz abgelehnt (REJECTED)
* Asset heruntergeladen (DOWNLOADED)
* Asset versioniert (VERSIONED)
* Asset-Version wiederhergestellt (RESTORED)
* Asset-Metadaten aktualisiert (METADATA_UPDATED)
* Asset in externem System veröffentlicht (PUBLISHED_EXTERNAL)
* Original des Assets aktualisiert (ORIGINAL_UPDATED)
* Asset-Ausgabedarstellung aktualisiert (RENDITION_UPDATED)
* Asset-Ausgabedarstellung entfernt (RENDITION_REMOVED)
* Teil-Asset aktualisiert (SUBASSET_UPDATED)
* Teil-Asset entfernt (SUBASSET_REMOVED)

## Konfigurieren der [!DNL Assets]-Ereignisaufzeichnung {#configuring-aem-assets-events-recording}

Die Einstellungen für die Assets-Ereignisaufzeichnung können über die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) vorgenommen werden. Zum Konfigurieren der Assets-Ereignisaufzeichnung gehen Sie wie folgt vor:

1. Navigieren Sie zur **[!UICONTROL Web-Konsole]**.

1. Klicken Sie auf **[!UICONTROL Konfiguration]**.

1. Doppelklicken Sie auf **[!UICONTROL Day CQ DAM Event Recorder]**.

1. Aktivieren Sie die Option **[!UICONTROL Diesen Service aktivieren]**.

1. Überprüfen Sie, welche **[!UICONTROL Ereignistypen]** im Benutzeraktivitäts-Stream aufgezeichnet werden sollen.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Lesen aufgezeichneter Ereignisse {#reading-recorded-events}

Die aufgezeichneten Ereignisse werden als Aktivitäten gespeichert. Sie können sie programmgesteuert über die [ActivityManager-API](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/adobe/granite/activitystreams/ActivityManager.html) lesen.
