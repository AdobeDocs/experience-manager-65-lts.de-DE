---
title: Versionshinweise für  [!DNL Adobe Experience Manager] .6.5 LTS
description: Hier finden Sie die aktuellen Versionsinformationen zu Adobe Experience Manager 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 70436606-d95c-4208-94f6-e33f3eefdf66
source-git-commit: 7f9f24f173604640b454449b389da9fcdcf7017d
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 95%

---

# Aktuelle Versionshinweise zu Adobe Experience Manager 6.5 LTS. {#release-notes}

## Versionshinweise {#release-information}

| Produkt | [!DNL Adobe Experience Manager] |
|---|---|
| Version | 6.5 LTS |
| Typ | Hauptversion |
| Allgemeine Verfügbarkeit | &#x200B;7. März 2025 |

## Neue Funktionen {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 ist eine Upgrade-Version für die Code-Basis von [!DNL Adobe Experience Manager] 6.5. Sie bietet wichtige Kundenkorrekturen, Kundenerweiterungen mit hoher Priorität und allgemeine Fehlerbehebungen zur Steigerung der Stabilität des Produkts. Darüber hinaus enthält sie [!DNL Adobe Experience Manager] 6.5 Service Pack-Versionen bis SP22.

Die folgende Liste bietet eine Übersicht, und die nachfolgenden Seiten enthalten die vollständigen Details.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Die Plattform von [!DNL Adobe Experience Manager] 6.5 LTS basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java™ Content-Repository Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x wird als Servlet-Engine für den Schnellstart verwendet.

#### Java™-Unterstützung  {#java-support}

* Unterstützung für Java™ 17 und Java™ 21.
* Um eine optimale Leistung zu erzielen, überschreiben Sie die GC-Standardwerte mit anderen Werten. Weitere Informationen finden Sie im Abschnitt [Installieren und Aktualisieren](/help/sites-deploying/custom-standalone-install.md).
* Adobe verteilt Wartungs-Updates für Java™ 17 und Java™ 21 für die Verwendung durch Kunden in AEM-bezogenen Projekten, sofern diese nicht über Oracle öffentlich verfügbar sind.

#### UberJar-Verpackung {#uber-jar-packaging}

* Es gibt einen geringfügigen Unterschied beim Verpacken von Uber Jar in AEM 6.5 LTS. Weitere Informationen finden Sie unter [Aktualisieren der Uber Jar-Version von AEM](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

#### Aktualisieren {#upgrade}

* Weitere Informationen zum Upgrade-Verfahren finden Sie unter [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md).

## Installieren und Aktualisieren {#install-update}

Informationen zu Setup-Anforderungen finden Sie unter [Installationsanweisungen](/help/sites-deploying/custom-standalone-install.md).

Detaillierte Anweisungen finden Sie unter [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> Für neue AEM 6.5 LTS-Installationen müssen Indexdefinitionen separat installiert werden. Weitere Informationen finden Sie in [diesem Artikel](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Unterstützte Plattformen {#supported-platforms}

Die vollständige Matrix der unterstützten Plattformen, einschließlich der Support-Ebene, finden Sie unter [AEM 6.5 LTS – Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java™ 17/Java™ 21 sind die empfohlenen Versionen für AEM 6.5 LTS.

## Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe überprüft kontinuierlich die Produktfunktionen, um den Kundenwert zu verbessern, indem ältere Funktionen modernisiert oder ersetzt werden. Diese Änderungen werden mit größter Sorgfalt vorgenommen, um Abwärtskompatibilität zu gewährleisten.

Für die Bekanntgabe der bevorstehenden Entfernung oder Ersetzung von Adobe Experience Manager (AEM)-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Obwohl diese Funktionen veraltet sind, sind sie weiterhin verfügbar, sie werden jedoch nicht weiter verbessert.
1. Das Entfernen veralteter Funktionen erfolgt frühestens mit Einführung der nächsten Hauptversion. Das tatsächliche Zieldatum für die Entfernung wird später bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

### Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden Funktionen aufgeführt, die Adobe in AEM 6.5 LTS nicht mehr unterstützt werden. In der Regel werden Funktionen von Adobe eingestellt, bevor sie aus einer zukünftigen Version entfernt werden, und es wird eine Alternative bereitgestellt.


Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung nutzen, und die Änderung ihrer Implementierung zu planen, um die bereitgestellte Alternative nutzen zu können.

| Bereich | Funktion | Ersatz | Version (SP) |
|---|---|---|---|
| Sites | [SPA-Editor](/help/sites-developing/spa-overview.md) | Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind: <br>- der [universelle Editor](/help/sites-developing/universal-editor/introduction.md) zur visuellen Bearbeitung<br>- der [Inhaltsfragment-Editor](/help/assets/content-fragments/content-fragments-managing.md) zur formularbasierten Bearbeitung | 6.5 LTS GA |

### Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden die Funktionen aufgeführt, die aus AEM 6.5 LTS entfernt wurden. In früheren Versionen wurden diese Funktionen als veraltet gekennzeichnet.

| Bereich | Funktion | Ersatz | Version (SP) |
|--- |--- |--- |--- |
| Commerce  | AEM CIF Classic wird nicht unterstützt. | Migrieren Sie zu [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Lösungen | Social/Communities wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Screens | Screens werden nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Assets | `dam-pim` und `dam-rating` werden nicht unterstützt, da Bundles von Social abhängig sind. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Assets | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` wurde entfernt. | Verwenden Sie die hinzugefügte alternative API `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()`. | 6.5 LTS GA |
| Portal | AEM Portal Director wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Granite | Bundle `com.adobe.granite.socketio` wird entfernt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Granite | `com.adobe.granite.crx-explorer` wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Granite | `crx2oak` wird nicht unterstützt. | Wählen Sie die entsprechende Version von [Oak-Upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6.5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Guava | Alle Guava-Abhängigkeiten sind jetzt aus AEM entfernt und daher ist das Bundle `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` nicht Teil von AEM. | Kunden können Guava selbst hinzufügen, wenn sie von Guava abhängig sind, oder Guava-Code durch Java-Sammlungen oder andere Alternativen ersetzen, sofern möglich. | 6.5 LTS GA |
| `We.Retail` | `We-retail` Beispiel-Site wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Open Source | Bundle `oak-solr-osgi` wird nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Open Source | `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` und `org.apache.sling.atom.taglib` werden nicht unterstützt. | Es steht kein Ersatz zur Verfügung. | 6.5 LTS GA |
| Open Source | `org.apache.commons.io`-Pakete werden jetzt aus `org.apache.commons.commons-io` exportiert. | Keine Änderung erforderlich. | 6.5 LTS GA |
| Open Source | `javax.mail`-Pakete werden aus dem Bundle `com.sun.javax.mail` exportiert. | Keine Änderung erforderlich. | 6.5 LTS GA |
| Open Source | `org.apache.jackrabbit.api`-Pakete werden jetzt aus dem Bundle `org.apache.jackrabbit.oak-jackrabbit-api` exportiert. | Keine Änderung erforderlich. | 6.5 LTS GA |
| Open Source | `com.github.jknack.handlebars` wird nicht unterstützt | Wählen Sie die relevante [Version](https://mvnrepository.com/artifact/com.github.jknack/handlebars) aus | 6.5 LTS GA |

## Bekannte Probleme {#known-issues}

### Problem mit dem JSP-Scripting-Bundle in AEM 6.5.21–6.5.23 und AEM 6.5 LTS GA

AEM 6.5.21, 6.5.22, 6.5.23 und AEM 6.5 LTS GA werden mit dem Bundle `org.apache.sling.scripting.jsp:2.6.0` ausgeliefert, das ein bekanntes Problem enthält. Das Problem tritt in der Regel bei hoher Auslastung auf, wenn die AEM-Instanz viele Anfragen gleichzeitig verarbeitet.

Wenn dieses Problem auftritt, kann eine der folgenden Ausnahmen in den Fehlerprotokollen neben Verweisen auf `org.apache.sling.scripting.jsp:2.6.0` angezeigt werden:

* `java.io.IOException: classFile.delete() failed`
* `java.io.IOException: tmpFile.renameTo(classFile) failed`
* `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
* `java.io.FileNotFoundException`

Zur Lösung dieses Problems ist Hotfix [cq-6.5.lts.0-hotfix-NPR-42640](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-NPR-42640-1.2.zip) verfügbar.

### Dispatcher-Verbindungsfehler mit der Funktion „Nur SSL“ {#ssl-only-feature}

Bei der Aktivierung der Funktion „Nur SSL“ in AEM-Bereitstellungen gibt es ein bekanntes Problem, das die Verbindung zwischen dem Dispatcher und AEM-Instanzen beeinträchtigt. Nach Aktivierung dieser Funktion können Konsistenzprüfungen fehlschlagen und die Kommunikation zwischen dem Dispatcher und AEM-Instanzen kann unterbrochen werden. Dieses Problem tritt insbesondere auf, wenn Kundinnen und Kunden versuchen, eine Verbindung über `https + IP` von der Dispatcher zu AEM-Instanzen herzustellen. Dies steht im Zusammenhang mit SNI-Validierungsproblemen (Server Name Indication).

**Auswirkungen:**

* Konsistenzprüfungsfehler mit HTTP 400-Antwort-Codes
* Unterbrochener Traffic zwischen Dispatcher und AEM-Instanzen
* Inhalte können nicht ordnungsgemäß über den Dispatcher bereitgestellt werden
* Verbindungsfehler bei Verwendung von HTTPS mit IP-Adressen in der Dispatcher-Konfiguration
* HTTP 400-Fehler vom Typ „Ungültige SNI“ bei der Verbindung über HTTPS + IP

**Betroffene Umgebungen:**

* AEM-Bereitstellungen mit Dispatcher-Konfigurationen
* Systeme, in denen die Funktion „Nur SSL“ aktiviert wurde
* Dispatcher-Konfigurationen mit der Verbindungsmethode `https + IP` zu AEM-Instanzen

**Lösung:**
Wenn dieses Problem auftritt, wenden Sie sich an den Adobe-Kundensupport. Zur Lösung dieses Problems ist Hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) verfügbar. Versuchen Sie nicht, „Nur SSL“-Funktionen zu aktivieren, bis Sie den erforderlichen Hotfix angewendet haben.

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/de/docs/customer-one/using/home).