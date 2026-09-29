---
title: Wählen eines Persistenztyps für eine AEM Forms-Installation
description: Wählen Sie einen Persistenztyp mit Bedacht aus. Er hilft Ihnen beim Aufbau einer effizienten und skalierbaren AEM Forms-Umgebung.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Foundation Components
exl-id: 8ddfc767-08a5-4045-86a7-97150e028a14
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 7da902b6-fe94-5180-8e7c-f6d1e38d01d5
    internal-label: Foundation Components
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 96%
---
# Wählen eines Persistenztyps für eine AEM Forms-Installation {#choosing-a-persistence-type-for-an-aem-forms-installation}

Wählen Sie einen Persistenztyp mit Bedacht aus. Er hilft Ihnen beim Aufbau einer effizienten und skalierbaren AEM Forms-Umgebung.

Persistenz ist die Methode zum Speichern von Inhalten auf den physischen Speichern. Sie definiert die tatsächliche Datenstruktur und den Speichermechanismus für die Daten. MicroKernels fungieren als Persistenz-Manager in AEM Forms. AEM Forms unterstützt Persistenz (MicroKernels) vom Typ TarMK, MongoMK und RDBMK. Sie können je nach Zweck und Bereitstellungstyp (Einzel-Server, Farm oder Cluster) einer AEM Forms-Instanz einen Persistenztyp für AEM Forms auswählen.

>[!NOTE]
>
>LiveCycle ES4 SP1 verwendet TarPM-Persistenz zum Speichern von Inhalten.

In der folgenden Tabelle werden alle unterstützten Persistenztypen zusammen mit verschiedenen Parametern aufgeführt, um Ihnen die Auswahl eines Persistenztyps für Ihre Umgebung zu erleichtern:

<table>
 <tbody>
  <tr>
   <th><strong>Installationstyp/Kosten</strong></th>
   <th><strong>TarMK</strong></th>
   <th><strong>MongoMK</strong></th>
   <th><strong>RDBMK</strong></th>
  </tr>
  <tr>
   <th><strong>Eigenständige Einrichtung</strong></th>
   <td>Unterstützt<br /> </td>
   <td>Unterstützt</td>
   <td>Unterstützt</td>
  </tr>
  <tr>
   <th><strong>Cluster-Einrichtung</strong></th>
   <td>Nicht unterstützt</td>
   <td>Unterstützt</td>
   <td>Unterstützt</td>
  </tr>
  <tr>
   <th><strong>Lizenzkosten</strong></th>
   <td>Im Lieferumfang von AEM enthalten </td>
   <td>Separate Lizenz erforderlich</td>
   <td>Separate Lizenz erforderlich</td>
  </tr>
 </tbody>
</table>

TarMK ist auf Leistung ausgelegt, während MongoMK und RDBMK auf Skalierbarkeit ausgelegt sind. Adobe empfiehlt TarMK als Standardpersistenztechnologie für alle AEM Forms-Bereitstellungsszenarien für die Autoren- und Veröffentlichungsinstanz, außer in Fällen, die im Abschnitt [Mongo auswählt oder ein relationale Datenbank-Microkernel über TarMK](#p-choosing-mongo-or-a-relational-database-microkernel-over-tarmk-p) erläutert werden.

Eine Liste der unterstützten Mikrokernels finden Sie unter [Technische Anforderungen für AEM Forms on OSGi](/help/sites-deploying/technical-requirements.md) <!--or [AEM Forms on JEE supported platform combinations](/help/forms/using/aem-forms-jee-supported-platforms.md) articles-->.

## Auswählen von Mongo oder eines relationalen Datenbank-Mikro-Kernels anstelle von TarMK {#choosing-mongo-or-a-relational-database-microkernel-over-tarmk}

Eine skalierbare (Cluster-) AEM Forms-Umgebung ist ein Satz von zwei oder mehr horizontal konfigurierten, aktiven Autoreninstanzen. Sie können mehr als eine Autoreninstanz ausführen, wenn ein einzelner Server, der alle gleichzeitigen Autorenaktivitäten unterstützt, nicht mehr tragbar ist.

<!--Only MongoMK and RDBMK persistence type are supported for a scalable (clustered) AEM Forms on JEE environment.-->

Die Anzahl der Server oder die Größe der skalierbaren Umgebung variiert je nach Installation. Eine Liste mit Überlegungen und Beispielen finden Sie in den Artikeln [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md) und oder [ Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md). Sie können sich auch an den AEM Forms-Support wenden, um detaillierte Informationen zur Kapazitätsplanung für AEM Forms mit RDBMK und TarMK zu erhalten.
