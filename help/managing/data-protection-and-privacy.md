---
title: Datenschutzbestimmungen – Einhaltung durch Adobe Experience Manager
description: Erfahren Sie mehr über die Unterstützung von Adobe Experience Manager für die verschiedenen Datenschutzbestimmungen. Dazu gehören die Datenschutz-Grundverordnung (DSGVO) der EU, der kalifornische Consumer Privacy Act und die Einhaltung der Vorschriften bei der Implementierung eines neuen AEM-Projekts.
contentOwner: AEM Docs
topic-tags: introduction, grdp
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
docset: aem65
solution: Experience Manager, Experience Manager 6.5
feature: Compliance
role: Developer,Leader,Architect,Data Architect,User
source-git-commit: d1297182b801ff4db163b8ae91332f5aebb94b9b
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 100%

---

# Adobe Experience Manager – Einhaltung von Datenschutzbestimmungen {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Wenden Sie sich an die Rechtsabteilung Ihres Unternehmens, um Ratschläge zu Datenschutzbestimmungen zu erhalten.

>[!NOTE]
>
>Weitere Informationen über die Reaktion von Adobe auf Datenschutzprobleme und dazu, was dies für Sie als Kundin bzw. Kunde von Adobe bedeutet, finden Sie im [Datenschutzzentrum von Adobe](https://www.adobe.com/de/privacy.html).

Adobe stellt Dokumentationen und Verfahren bereit (mit APIs, sofern verfügbar), damit AEM-Admins oder Admins für den Schutz von Kundendaten Datenschutzanfragen bearbeiten können. Dies kann Ihnen dabei helfen, diese Vorschriften einzuhalten. Mit den dokumentierten Verfahren können Kundinnen und Kunden die Regulierungsanforderungen entweder manuell oder API-gestützt (sofern verfügbar) über ein externes Portal oder einen externen Service erfüllen.

>[!CAUTION]
>
>Die hier dokumentierten Details sind auf Adobe Experience Manager beschränkt.
>
>Bei Daten aus einem anderen On-Demand-Service von Adobe und den damit verbundenen Datenschutzanfragen müssen Maßnahmen für den betreffenden Service ergriffen werden.
>
>Weitere Informationen finden Sie im [Datenschutzzentrum von Adobe](https://www.adobe.com/de/privacy.html).

## Einführung {#introduction}

Instanzen von Adobe Experience Manager und die darauf ausgeführten Anwendungen liegen in der Verantwortung der Adobe-Kundinnen und -Kunden und werden von ihnen betrieben.

Daher sind Datenschutzbestimmungen wie die DSGVO, der CCPA und andere größtenteils Kundensache.

Zur Einführung sei darauf hingewiesen, dass die Datenschutzbestimmungen neue Regeln beinhalten, die von den folgenden Rollen befolgt werden müssen:

* Unternehmens-Entitäten (CCPA) und/oder Datenverantwortliche (DSGVO)

* Dienstleister (CCPA) und/oder Auftragsverarbeiter (DSGVO)

Die wichtigsten Bestimmungen dieser Verordnungen sind:

1. Erweiterte Definition personenbezogener Daten, um alle eindeutigen Kennungen einzuschließen; wie in direkt und indirekt identifizierbaren Daten.

2. Verschärfte Anforderungen an das Einverständnis.

3. Verstärkter Fokus auf Löschrechte (Datenlöschung).

4. Opt-out vom Verkauf von Daten.

Für Adobe Experience Manager gilt:

* Die Instanzen und die darauf ausgeführten Anwendungen liegen in der Verantwortung der Kundinnen und -Kunden und werden von ihnen betrieben.

   * Die regulatorischen Rollen werden auf Kundenseite verwaltet, was etwa Unternehmensentitäten und Dienstleister, Datenverantwortliche und Auftragsverarbeiter einschließt.

   * Der Adobe Experience Platform Privacy Service ist nicht Teil des Workflows für AEM, wie in der folgenden Abbildung dargestellt.

* AEM umfasst Dokumentationen und Verfahren für den Datenschutzadministrator und/oder AEM-Administrator des Kunden, die Datenschutzanfragen manuell oder über APIs (sofern verfügbar) zu bearbeiten.

* Es wurde kein neuer Service und keine neue Benutzeroberfläche hinzugefügt.

   * Stattdessen werden Verfahren und APIs für die Verwendung durch die Benutzeroberflächen/Portale von Kunden dokumentiert, die Datenschutzanfragen bearbeiten.

* AEM enthält keine vorkonfigurieren Tools zur Unterstützung des Workflows für Datenschutzanfragen.

   * Adobe stellt Datenschutz-Admins und/oder AEM-Admins auf Kundenseite Dokumentationen und Verfahren zur Verfügung, mit denen sie Anfragen im Zusammenhang mit den Datenschutzbestimmungen manuell bearbeiten können.

Adobe bietet Verfahren für die Bearbeitung von Datenschutzanfragen im Zusammenhang mit Zugriff, Löschen und Opt-out für Adobe Experience Manager. In einigen Fällen sind APIs verfügbar, die von einem auf Kundenseite entwickelten Portal oder von Skripten aufgerufen werden können, um die Automatisierung zu unterstützen.

Die folgende Abbildung zeigt, wie ein Workflow für Datenschutzanfragen aussehen könnte (unter Verwendung von Adobe Experience Manager 6.5):

![Datenschutz](assets/data-protection-and-privacy-01.png)

## Befolgung der Vorschriften durch Adobe Experience Manager {#aem-and-regulatory-readiness}

In den folgenden Abschnitten finden Sie die Dokumentation zu Vorschriften für einzelne Produktbereiche von AEM.

## AEM Foundation {#aem-foundation}

Siehe [Umgang mit Datenschutzanfragen für die AEM Foundation](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

## Opt-in für die Sammlung aggregierter Nutzungsstatistiken von AEM {#aem-opting-into-aggregate-usage-statistics-collection}

Siehe [Sammlung aggregierter Nutzungsstatistiken](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

## AEM Sites {#aem-sites}

Siehe [AEM Sites – Einhaltung von Datenschutzbestimmungen.](/help/sites-administering/gdpr-compliance-sites.md)

## AEM-Integration mit Adobe Target und Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Diese Adobe Experience Manager-Integrationen verfügen über datenschutzfreundliche Dienste (z. B. DSGVO oder CCPA). In AEM werden keine personenbezogenen Daten von Adobe Target oder Adobe Analytics in Bezug auf die Integrationen gespeichert.

Weitere Informationen finden Sie unter den folgenden Themen:

* [Adobe Target – Datenschutzübersicht](https://developer.adobe.com/target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation/?lang=de)

* [Adobe Analytics-Datenschutz-Workflow](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/data-governance/an-gdpr-workflow.html?lang=de)

## AEM Forms {#aem-forms}

AEM Forms beinhaltet Komponenten und Workflows, die zur Orchestrierung von Geschäftsprozessen und zum Abschließen von digitalen Transaktionen Daten erfassen, verarbeiten und speichern. Die einzelnen Komponenten verwenden unterschiedliche Datenspeicher und ermöglichen darüber hinaus die Integration mit benutzerdefinierten Datenspeichern. In der folgenden Dokumentation werden Verfahren und Richtlinien für den Zugriff auf und die Verarbeitung von Benutzerdaten erläutert, um Datenschutzarbeitsabläufe (z. B. DSGVO oder CCPA) für eine Komponente zu unterstützen.

* [Formularportal](/help/forms/using/forms-portal-handling-user-data.md)
* [Correspondence Management](/help/forms/using/correspondence-management-handling-user-data.md)
* [Integration mit Adobe Sign](/help/forms/using/integration-adobe-sign-handling-user-data.md)
* [Forms-zentrierte Workflows auf OSGi](/help/forms/using/forms-workflow-osgi-handling-user-data.md)
* [Forms JEE-Workflows](/help/forms/using/forms-workflow-jee-handling-user-data.md) (Nur AEM Forms JEE)
* [Documentensicherheit](/help/forms/using/document-security-handling-user-data.md) (Nur AEM Forms JEE)
* [User Management](/help/forms/using/user-management-handling-user-data.md) (Nur AEM Forms JEE)
