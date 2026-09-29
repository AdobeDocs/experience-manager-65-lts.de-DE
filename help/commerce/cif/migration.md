---
title: Migration zum Add-on für das AEM Commerce Integration Framework (CIF)
description: So migrieren Sie von einer alten Version zum Add-on für das AEM Commerce Integration Framework (CIF).
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: 847c33c1-17d6-447a-9f2c-91f2a81a3f04
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 84%
---
# Leitfaden zur Migration für das Experience Manager Add-on {#cif-migration}

Dieser Leitfaden hilft bei der Identifizierung von Bereichen, die für die Experience Manager Add-on-Migration aktualisiert werden müssen.

## CIF-Add-on

Das CIF-Add-on ist über das [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?fulltext=commerce*&2_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3Aversion&2_group.propertyvalues.operation=equals&2_group.propertyvalues.0_values=target-version%3Aaem%2F6-5-lts&orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&orderby.sort=desc&layout=list&p.offset=0&p.limit=16) verfügbar. Es ist mit dem CIF-Add-on kompatibel und bietet dieselben Funktionen für Experience Manager as a Cloud Service.

Siehe [Erste Schritte mit AEM Content and Commerce](getting-started.md).

Um Projekte mit CIF-Bereitstellung zu unterstützen, stellt Adobe die [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) bereit.

## Produktkatalog

Der Import von Produktkatalogdaten wird vom CIF-Add-on nicht unterstützt. Die Verwendung der CIF-Add-on-Prinzipale für Produkt- und Kataloganforderungen erfolgt über Echtzeit-Aufrufe an eine externe Lösung für den Handel. Wechseln Sie zum Kapitel über Integration, um mehr über die Integration von Lösungen für den Handel zu erfahren.

>[!TIP]
>
>Wenn keine Echtzeit-APIs verfügbar sind, sollte für die Integration ein externer Produkt-Cache mit APIs verwendet werden. Beispiel: [Magento Open Source](https://business.adobe.com/de/products/magento/open-source.html).

## Produktkatalogerlebnisse mit AEM-Rendering

Wenn Sie die Katalog-Blueprint mit dem klassischen CIF verwenden, müssen Sie den Workflow für den Produktkatalog aktualisieren. Das CIF-Add-on rendert Produktkatalog-Erlebnisse mithilfe von AEM-Katalogvorlagen nun direkt. Die Replikation von Produktdaten oder Produktseiten ist nicht mehr erforderlich.

## Nicht Cache-taugliche Daten und Shopping-Interaktionen

Client-seitige Anforderungen für nicht Cache-taugliche Daten und Interaktionen (z. B. Warenkorb-Interaktionen, Suchen) sollten direkt über das CDN bzw. den Dispatcher an den Commerce-Endpunkt (entweder Lösung für den Handel oder Integrationsschicht) gesendet werden. Entfernen Sie alle Aufrufe, bei denen AEM nur als Proxy fungierte.
