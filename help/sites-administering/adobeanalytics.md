---
title: Integration mit Adobe Analytics
description: Erfahren Sie, wie Sie Adobe Experience Manager (AEM) mit Adobe Analytics integrieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
exl-id: 4f7e1794-af5a-45a2-8dc6-80029c47caeb
source-git-commit: 929a2175449a371ecf81226fedb98a0c5c6d7166
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 94%

---

# Integration mit Adobe Analytics{#integrating-with-adobe-analytics}

Die Integration von Adobe Analytics und AEM ermöglicht es Ihnen, Web-Seiten-Aktivität nachzuverfolgen:

* Eine Adobe Analytics-Konfiguration ermöglicht AEM die Authentifizierung mit Adobe Analytics.
* Ein Framework identifiziert die Daten, die an die Adobe Analytics-Report Suite übermittelt werden.

Die Daten umfassen Seiten- und Benutzerdaten, z. B.:

* Daten, die von AEM-Komponenten erfasst werden
* Link-Klicks
* Videonutzungsdaten
* die Anzahl von Seitenbesuchen aus Adobe Analytics

Die folgenden Seiten helfen Ihnen beim Konfigurieren der Integration:

* [Herstellen einer Verbindung mit Adobe Analytics und Erstellen von Frameworks](/help/sites-administering/adobeanalytics-connect.md)
* [Konfigurieren des Linktrackings für Adobe Analytics](/help/sites-administering/adobeanalytics-link.md)
* [Zuordnen von Komponentendaten zu Adobe Analytics-Eigenschaften](/help/sites-administering/adobeanalytics-mapping.md)
* [Konfigurieren von Video-Tracking für Adobe Analytics](/help/sites-administering/adobeanalytics-video.md)
* [Adobe-Klassifizierungen](/help/sites-administering/adobeanalytics-classifications.md)

Der [Opt-in-Assistent](/help/sites-administering/opt-in.md) erleichtert die Durchführung der Integration.

>[!NOTE]
>
>Siehe auch [Integrieren von AEM in Adobe Target und Adobe Analytics mithilfe von DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

## Weiterführende Informationen {#further-information}

Siehe:

* [Erweitern der Adobe Analytics-Integration](/help/sites-developing/extending-analytics.md), um Informationen zur Entwicklung von Komponenten zu erhalten, die Benutzerdaten erfassen, und zur Anpassung des Adobe Analytics-Frameworks.

>[!NOTE]
>
>Wenn Sie Adobe Analytics mit einer benutzerdefinierten Proxykonfiguration verwenden, müssen Sie zwei OSGi-Pakete[ (z. B. mit der Web Console) ](/help/sites-deploying/configuring-osgi.md)konfigurieren, die für die **Apache HTTP Client**-Proxykonfigurationen erforderlich sind. Beide sind erforderlich, da einige Funktionen von AEM die 3.x-APIs verwenden, während andere die 4.x-APIs verwenden. Konfigurieren:
>
>* **Day Commons HTTP Client 3.1** zum Konfigurieren der 3.x-API;
>  >  Beispiel: [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>
>* **Apache HTTP Components Proxy Configuration** zum Konfigurieren der 4.x-API;
>  >  Beispiel: [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>
