---
title: Aktuelle Versionshinweise für Adobe Experience Manager 6.5 LTS
description: Hier finden Sie die aktuellen Versionsinformationen zu Adobe Experience Manager 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 02b9f90dc9ef504f04a9b1f692358089d4626094
workflow-type: tm+mt
source-wordcount: '1016'
ht-degree: 31%

---

# Aktuelle Versionshinweise für Adobe Experience Manager 6.5 LTS {#release-notes}

## Versionshinweise {#release-information}

| Produkt | [!DNL Adobe Experience Manager] |
|---|---|
| Version | 6,5 LTS |
| Typ | Hauptversion |
| Datum der allgemeinen Verfügbarkeit | Samstag, 7. März 2025 |

## Neue Funktionen {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 LTS ist eine Upgrade-Version für die Code-Basis von [!DNL Adobe Experience Manager] 6.5. Es bietet wichtige Kundenkorrekturen, Erweiterungen für Kunden mit hoher Priorität und allgemeine Fehlerbehebungen zur Steigerung der Stabilität des Produkts. Es enthält auch [!DNL Adobe Experience Manager] 6.5 Service Pack-Versionen bis SP22.

Die folgende Liste bietet eine Übersicht und die nachfolgenden Seiten enthalten die vollständigen Details.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Die Plattform von [!DNL Adobe Experience Manager] 6.5 LTS basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java™ Content Repository Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x wird als Servlet-Engine für den Schnellstart verwendet.

#### Java™-Unterstützung  {#java-support}

* Unterstützung für Java™ 17 und Java™ 21.
* Um eine optimale Leistung zu erzielen, überschreiben Sie die standardmäßigen GC-Werte mit anderen Werten. Weitere Informationen finden Sie im Abschnitt [Installieren und Aktualisieren](/help/sites-deploying/custom-standalone-install.md).
* Adobe verteilt Wartungs-Updates für Java™ 17 und Java™ 21 für die Verwendung durch Kunden in AEM-bezogenen Projekten, sofern diese nicht in Oracle öffentlich verfügbar sind.

#### UberJar-Verpackung {#uber-jar-packaging}

* Es gibt einen geringfügigen Unterschied beim Verpacken von Uberjar in AEM 6.5 LTS. Weitere Informationen finden Sie unter [Aktualisieren der Uber Jar-Version von AEM](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

#### Aktualisierung {#upgrade}

* Weitere Informationen zum Upgrade-Verfahren finden Sie unter [Dokumentation zu Upgrades](/help/sites-deploying/upgrade.md).

## Installieren und Aktualisieren {#install-update}

Informationen zu Setup-Anforderungen finden Sie unter [Installationsanweisungen](/help/sites-deploying/custom-standalone-install.md).

Detaillierte Anweisungen finden Sie unter [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md).

## Unterstützte Plattformen {#supported-platforms}

Die vollständige Matrix der unterstützten Plattformen, einschließlich der Support-Ebene, finden Sie unter [AEM 6.5 LTS - Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Die empfohlenen Versionen für die Verwendung mit AEM 6.5 LTS sind Java™ 17/Java™ 21.

## Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe überprüft kontinuierlich die Produktfunktionen, um den Kundenwert zu verbessern, indem ältere Funktionen modernisiert oder ersetzt werden. Diese Änderungen werden mit größter Sorgfalt vorgenommen, um Abwärtskompatibilität zu gewährleisten.

Für die Bekanntgabe der bevorstehenden Entfernung oder Ersetzung von Adobe Experience Manager (AEM)-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Obwohl diese Funktionen veraltet sind, sind sie weiterhin verfügbar, sie werden jedoch nicht weiter verbessert.
1. Das Entfernen veralteter Funktionen erfolgt frühestens mit Einführung der nächsten Hauptversion. Das tatsächliche Zieldatum für die Entfernung soll später bekannt gegeben werden.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

### Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden Funktionen aufgeführt, die Adobe in AEM 6.5 LTS nicht mehr unterstützt. In der Regel werden Funktionen von Adobe verworfen, bevor sie in einer zukünftigen Version entfernt werden, und es wird eine Alternative bereitgestellt.


Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung nutzen, und die Änderung ihrer Implementierung zu planen, um die bereitgestellte Alternative nutzen zu können.

| Bereich | Funktion | Ersatz | Version (SP) |
|---|---|---|---|
| Sites | [SPA-Editor](/help/sites-developing/spa-overview.md) | Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind: <br>- der [universelle Editor](/help/sites-developing/universal-editor/introduction.md) zur visuellen Bearbeitung<br>- der [Inhaltsfragment-Editor](/help/assets/content-fragments/content-fragments-managing.md) zur formularbasierten Bearbeitung | 6.5 LTS GA |

### Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen aufgeführt, die aus AEM 6.5 LTS entfernt wurden. In früheren Versionen waren diese Funktionen als veraltet gekennzeichnet.

| Bereich | Funktion | Ersatz | Version (SP) |
|--- |--- |--- |--- |
| Commerce  | AEM CIF Classic wird nicht unterstützt. | Migrieren Sie zu [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Lösungen | Social Media/Communities wird nicht unterstützt. | Kein Ersatz verfügbar. | 6.5 LTS GA |
| Screens | Screens werden nicht unterstützt. | Kein Ersatz verfügbar. | 6.5 LTS GA |
| Assets | `dam-pim` und `dam-rating` werden nicht unterstützt, da Pakete von Social Media abhängig sind. | Kein Ersatz verfügbar. | 6.5 LTS GA |
| Assets | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` wurde entfernt. | Verwenden Sie die hinzugefügte alternative API-`com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()`. | 6.5 LTS GA |
| Portal | AEM Portal Director wird nicht unterstützt. | Kein Ersatz verfügbar. | 6.5 LTS GA |
| Granite | Paket `com.adobe.granite.socketio` wird entfernt. | Kein Ersatz verfügbar. | 6.5 LTS GA |
| Granite | `com.adobe.granite.crx-explorer` wird nicht unterstützt. | Kein Ersatz verfügbar. | 6.5 LTS GA |
| Granite | `crx2oak` wird nicht unterstützt. | Wählen Sie die entsprechende Version von [oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6.5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` wird nicht unterstützt. | Kein Ersatz verfügbar. | 6.5 LTS GA |
| Guave | Alle Guava-Abhängigkeiten werden jetzt in AEM entfernt, und daher ist das `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002`-Bundle nicht Teil von AEM. | Kunden können Guava selbst hinzufügen, wenn sie von Guava abhängig sind, oder Guava-Code durch Java-Sammlungen oder andere Alternativen ersetzen, sofern möglich. | 6.5 LTS GA |
| We.Retail | Die Beispiel-Site „We-Retail“ wird nicht unterstützt. | Kein Ersatz verfügbar. | 6.5 LTS GA |
| Open Source | `oak-solr-osgi` Paket wird nicht unterstützt. | Kein Ersatz verfügbar. | 6.5 LTS GA |
| Open Source | `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` und `org.apache.sling.atom.taglib` werden nicht unterstützt. | Kein Ersatz verfügbar. | 6.5 LTS GA |
| Open Source | `org.apache.commons.io` Pakete werden jetzt aus `org.apache.commons.commons-io` exportiert. | Keine Änderung erforderlich. | 6.5 LTS GA |
| Open Source | `javax.mail` Pakete werden aus dem `com.sun.javax.mail` Bundle exportiert. | Keine Änderung erforderlich. | 6.5 LTS GA |
| Open Source | `org.apache.jackrabbit.api` Pakete werden jetzt aus dem `org.apache.jackrabbit.oak-jackrabbit-api`-Bundle exportiert. | Keine Änderung erforderlich. | 6.5 LTS GA |
| Open Source | `com.github.jknack.handlebars` wird nicht unterstützt | Wählen Sie die entsprechende [Version](https://mvnrepository.com/artifact/com.github.jknack/handlebars) | 6.5 LTS GA |

## Bekannte Probleme {#known-issues}

### Problem mit dem JSP-Skriptpaket in AEM 6.5.21-6.5.23 und AEM 6.5 LTS GA

AEM 6.5.21, 6.5.22, 6.5.23 und AEM 6.5 LTS GA werden mit dem `org.apache.sling.scripting.jsp:2.6.0`-Bundle ausgeliefert, das ein bekanntes Problem enthält. Das Problem tritt in der Regel bei hoher Auslastung auf, wenn die AEM-Instanz viele gleichzeitige Anfragen verarbeitet.

Wenn dieses Problem auftritt, kann eine der folgenden Ausnahmen in den Fehlerprotokollen neben Verweisen auf `org.apache.sling.scripting.jsp:2.6.0` angezeigt werden:

* `java.io.IOException: classFile.delete() failed`
* `java.io.IOException: tmpFile.renameTo(classFile) failed`
* `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
* `java.io.FileNotFoundException`

Wenn dieser Fehler auftritt, besteht die einzige Wiederherstellungsmethode darin, die AEM-Instanz neu zu starten.

Wenden Sie sich an den Kunden-Support von Adobe und referenzieren Sie diese Versionshinweise für eine Lösung.

### Dispatcher-Verbindungsfehler mit Funktion „Nur SSL“ {#ssl-only-feature}

Bei der Aktivierung der Funktion „Nur SSL“ in AEM-Bereitstellungen gibt es ein bekanntes Problem, das die Verbindung zwischen der Dispatcher- und der AEM-Instanz beeinträchtigt. Nach Aktivierung dieser Funktion können Konsistenzprüfungen fehlschlagen und die Kommunikation zwischen Dispatcher- und AEM-Instanzen kann unterbrochen werden.

**Impact:**

* Systemdiagnosefehler mit HTTP 500-Antwort-Codes
* Beschädigter Traffic zwischen Dispatcher- und AEM-Instanzen
* Inhalte können nicht ordnungsgemäß über die Dispatcher bereitgestellt werden

**Betroffene Umgebungen:**

* AEM-Bereitstellungen mit Dispatcher-Konfigurationen
* Systeme, bei denen die Funktion „Nur SSL“ aktiviert wurde

**Lösung:**
Wenn dieses Problem auftritt, wenden Sie sich an den Adobe-Support. Zur Lösung dieses Problems ist ein [ (cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.0.zip)) verfügbar. Versuchen Sie nicht, nur SSL-Funktionen zu aktivieren, bis Sie den erforderlichen Hotfix angewendet haben.

## Eingeschränkte Websites{#restricted-sites}

Diese Websites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Adobe-Kundendienst](https://experienceleague.adobe.com/de/docs/customer-one/using/home).

