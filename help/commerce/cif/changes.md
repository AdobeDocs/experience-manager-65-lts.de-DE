---
title: Wesentliche Änderungen des CIF-Add-ons (Commerce Integration Framework)
description: Wesentliche Änderungen des CIF-Add-ons (Commerce Integration Framework) im Vergleich zu alten CIF-Versionen.
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: aced89a0-dec1-49fe-afbc-3ddf1318b900
source-git-commit: 79cce324382bada2e9aec107b8e494723bf490e9
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 99%

---

# Wesentliche Änderungen des CIF-Add-ons (Commerce Integration Framework){#notable-changes}

In diesem Dokument werden die wichtigen Unterschiede zwischen dem CIF-Add-on und alten CIF-Versionen, hauptsächlich bekannt als CIF Classic (Schnellstart) und CIF Open-Source, erläutert.

## Installation und Updates

Das AEM CIF-Add-On-Paket wird mit AEM Package Manager installiert und aktualisiert.

**Vorherige CIF-Versionen**

* CIF Classic: Keine Installation erforderlich, CIF war Teil des Schnellstarts. CIF-Updates waren Teil regelmäßiger AEM- oder Service Pack-Updates.
* CIF Open Source: Installation über GitHub. Updates waren Teil der manuellen Aktualisierung/Wartung.

## Konfiguration des Endpunkts

Der Endpunkt wird über die OSGi-Konsole konfiguriert.

**Vorherige CIF-Versionen**

* CIF Classic: Über die OSGi-Konfiguration in AEM
* CIF Open-Source: Über den CIF-Konfigurations-Browser

## Bereitstellung des CIF-Venia-Projekts

Projekt verfügbar unter [GitHub – AEM Guides – CIF Venia-Projekt](https://github.com/adobe/aem-cif-guides-venia) und Bereitstellung über AEM Package Manager.

**Vorherige CIF-Versionen**

* CIF Classic: Über AEM Package-Installation

## Produktkatalogdaten

Produktkatalogdaten werden bei Bedarf über Echtzeitaufrufe an einen externen Endpunkt, der die erforderlichen GraphQL-APIs unterstützt, angefragt. Diese APIs unterstützen den Zugriff auf Live- oder Staging-Daten zu einem beliebigen Zeitpunkt. Es ist keine Replikation erforderlich.

**Vorherige CIF-Versionen**

* CIF Classic: Live- und Staging-Produktdaten werden in JCR in der AEM-Autoreninstanz über den vollständigen oder einen Delta-Produktimport importiert und beibehalten. Live-Produktdaten werden in die AEM-Veröffentlichungsinstanz repliziert.

## Produktkatalogerlebnisse mit AEM-Rendering

AEM rendert Produktkatalog-Erlebnisse direkt mithilfe von AEM-Katalogvorlagen, die Produkten und Kategorien zugewiesen wurden. Es ist keine Replikation erforderlich.

**Vorherige CIF-Versionen**

* CIF Classic: Die AEM-Autoreninstanz erstellt mit dem Katalog-Blueprint-Tool eine AEM-Seite für jede Kategorie / jedes Produkt. Diese Seiten werden zur AEM-Veröffentlichungsinstanz repliziert.

>[!NOTE]
>
>Weitere Dokumentationen zur Verwendung von CIF mit AEM Managed Service oder AEM On-Premise finden Sie unter [Commerce Integration Framework](https://developer.adobe.com/apis/experiencecloud/commerce-integration-framework/getting-started.html).
