---
title: 'Verbessern der Performance umfangreicher Formulare durch verzögertes Laden '
description: Verzögertes Laden (Lazy Loading) verbessert die Leistung von umfangreichen und komplexen adaptiven Formularen erheblich, indem Formularfragmente erst dann initialisiert und geladen werden, wenn sie sichtbar werden.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms,Foundation Components
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: 768f2f8a-6ac7-4a20-8500-bcfc960861ce
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 100%

---

# Verbessern der Performance umfangreicher Formulare durch verzögertes Laden {#improve-performance-of-large-forms-with-lazy-loading}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/lazy-loading-adaptive-forms.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

## Einführung in das verzögerte Laden {#introduction-to-lazy-loading}

Wenn Formulare infolge von Hunderten oder Tausenden von Feldern groß und komplex werden, bemerken die Endbenutzer während des Renderns von Formularen zur Laufzeit lange Reaktionszeiten. Um die Reaktionszeit zu minimieren, können Sie mit adaptiven Formularen Formulare in logische Fragmente aufteilen und so konfigurieren, dass die Initialisierung oder das Laden von Fragmenten so lange verschoben wird, bis das Fragment sichtbar sein muss. Dies wird als „verzögertes Laden“ bezeichnet. Darüber hinaus werden die für verzögertes Laden konfigurierten Fragmente entladen, sobald der Benutzer zu anderen Abschnitten im Formular navigiert und die Fragmente nicht mehr sichtbar sind.

Im Folgenden werden zunächst die Anforderungen und vorbereitenden Schritte vor dem Konfigurieren des verzögerten Ladens erklärt.

## Vorbereiten der Konfiguration von verzögertem Laden {#preparing-to-configure-lazy-loading}

Bevor Sie das verzögerte Laden von Fragmenten in Ihrem adaptiven Formular konfigurieren, müssen Sie Strategien für das Erstellen von Fragmenten entwickeln, Werte identifizieren, die in den Skripten verwendet oder in anderen Fragmenten referenziert werden, und Regeln definieren, die die Sichtbarkeit von Feldern in verzögert geladenen Fragmenten steuern.

* **Identifizieren und Erstellen von Fragmenten**
Sie können nur adaptive Formularfragmente für Lazy Loading (verzögertes Laden) konfigurieren. Ein Fragment ist ein unabhängiges Segment, das sich außerhalb eines adaptiven Formulars befindet und für mehrere Formulare wiederverwendet werden kann. Somit besteht der erste Schritt beim Implementieren des verzögerten Ladens in der Bestimmung der logischen Abschnitte in einem Formular und deren Konvertierung in Fragmente. Sie können ein Fragment von Grund auf neu erstellen oder einen vorhandenen Formularbereich als Fragment speichern.

   Weitere Informationen zum Erstellen von Fragmenten finden Sie unter [Adaptive Formularfragmente](../../forms/using/adaptive-form-fragments.md).

* **Identifizieren und Markieren globaler Werte**
Zu formularbasierten Transaktionen gehören dynamische Elemente, die relevante Daten von Benutzern erfassen und verarbeiten und dadurch das Ausfüllen des Formulars vereinfachen. Beispiel: Ihr Formular enthält Feld A in Fragment X, dessen Wert die Gültigkeit von Feld B in einem anderen Fragment bestimmt. Wenn in diesem Fall Fragment X für verzögertes Laden markiert ist, muss der Wert von Feld A verfügbar sein, um Feld B zu validieren, selbst wenn Fragment X nicht geladen wird. Um dies zu erreichen, können Sie Feld A als global markieren, wodurch sichergestellt wird, dass der zugehörige Wert für die Validierung von Feld B verfügbar ist, selbst wenn Fragment X noch nicht geladen ist.

  Weitere Informationen dazu, wie Sie einen Feldwert als „global“ kennzeichnen, finden Sie unter [Konfigurieren von verzögertem Laden](../../forms/using/lazy-loading-adaptive-forms.md#p-configuring-lazy-loading-p).

* **Erstellen von Regeln zur Steuerung der Sichtbarkeit von Feldern**
Formulare enthalten Felder und Abschnitte, die nicht für alle Benutzer und Bedingungen gelten. Menschen, die Formulare verfassen und entwickeln, verwenden Regeln für Sichtbarkeit oder Ein- und Ausblenden, um die Sichtbarkeit der Formulare anhand von Benutzereingaben zu steuern. Beispielsweise wird das Feld „Büroadresse“ nicht den Benutzenden angezeigt, die im Feld „Beschäftigungsstatus“ in einem Formular die Option „Arbeitslos“ auswählen. Weitere Informationen zum Erstellen von Regeln finden Sie unter [Verwenden des Regeleditors](../../forms/using/rule-editor.md).

  Sie können Sichtbarkeitsregeln in verzögert geladenen Fragmenten so nutzen, dass bedingte Felder nur angezeigt werden, wenn sie benötigt werden. Markieren Sie außerdem das bedingte Feld als „global“, um im Ausdruck für die Sichtbarkeit des verzögert geladenen Fragments darauf zu verweisen.

## Konfigurieren von verzögertem Laden {#configuring-lazy-loading}

Führen Sie zum Aktivieren des verzögerten Ladens in einem adaptiven Formularfragment folgende Schritte durch:

1. Öffnen Sie im Bearbeitungsmodus das adaptive Formular, das das Fragment enthält, für das Sie verzögertes Laden aktivieren möchten.
1. Wählen Sie das adaptive Formularfragment aus und dann ![cmppr](assets/cmppr.png) aus.
1. Aktivieren Sie in der Seitenleiste die Option **[!UICONTROL Fragment verzögert laden]** und wählen Sie **Fertig** aus.

   ![Verzögertes Laden für das adaptive Formularfragment aktivieren](assets/lazy-loading-fragment.png)

   Das Fragment ist jetzt für verzögertes Laden aktiviert.

Sie können die Werte von Objekten im verzögert geladenen Fragment als global markieren, damit sie in Skripten verwendet werden können, wenn das übergeordnete Fragment nicht geladen wird. Gehen Sie folgendermaßen vor:

1. Öffnen Sie das adaptive Formularfragment im Authoring-Modus.
1. Wählen Sie das Feld aus, dessen Wert Sie als „global“ markieren möchten, und wählen Sie dann ![cmppr](assets/cmppr.png) aus.
1. Aktivieren Sie in der Randleiste **Wert bei verzögertem Laden verwenden**.

   ![Feld „Verzögertes Laden“ in der Randleiste](assets/enable-lazy-loading.png)

   Der Wert ist jetzt als „global“ markiert und ist für die Verwendung in Skripten verfügbar, selbst wenn das Fragment, das ihn enthält, nicht geladen wurde.

## Aspekte und empfohlene Vorgehensweisen beim Konfigurieren von verzögertem Laden {#considerations-and-best-practices-for-configuring-lazy-loading}

Einige der folgenden Einschränkungen, Empfehlungen und wichtigen Aspekte sind beim Arbeiten mit verzögertem Laden zu beachten:

* Verwenden Sie bei umfangreichen Formularen XSD-schemabasierte statt XFA-basierte adaptive Formulare für die Konfiguration von verzögertem Laden. Die Leistungsverbesserung aufgrund von verzögertem Laden ist in XFA-basierten adaptiven Formularen verhältnismäßiger geringer als in XSD-basierten adaptiven Formularen.
* Konfigurieren Sie kein Lazy Loading (verzögertes Laden) für Fragmente in einem adaptiven Formular, die das Layout **[!UICONTROL Responsiv – alles auf einer Seite ohne Navigation]** für den Stammbereich verwenden. Infolge der Konfiguration „Responsive Layout“ werden in einem adaptiven Formular alle Fragmente gleichzeitig geladen. Dies kann ebenfalls die Performance beeinträchtigen.
* Es wird empfohlen, bei dem ersten Fragment in einem adaptiven Formular Lazy Loading nicht zu konfigurieren.
* Es wird empfohlen, verzögertes Laden für Fragmente nicht im ersten Bereich zu konfigurieren, der beim Laden des adaptiven Formulars gerendert wird.
* Verzögertes Laden wird für bis zu zwei Ebenen in der Fragmenthierarchie unterstützt.
* Vergewissern Sie sich, dass als „global“ markierte Felder im gesamten adaptiven Formular eindeutig sind.
* Erwägen Sie, Sichtbarkeitsregeln für Fragmente zu erstellen, die basierend auf einer Bedingung ein- bzw. ausgeblendet werden sollen. Beispielsweise können Sie je nach dem vom Benutzer angegebenen Familienstand das Fragment zum Ehepartner ein- oder ausblenden.
* In verzögert geladenen Fragmenten werden keine Komponenten für Dateianhänge und Geschäftsbedingungen unterstützt.

### Empfohlene Vorgehensweisen für das Entwerfen von Skripten von verzögertem Laden {#scripting-best-practices-for-configuring-lazy-loading}

Weiterhin sollten Sie Folgendes beim Entwickeln von Skripten für das verzögerte Laden beachten:

* Stellen Sie sicher, dass die initialisierten und berechneten Skripte, die in den Feldern des verzögert geladenen Fragments verwendet werden, idempotent sind. Idempotente Skripte sind diejenigen, die auch nach mehreren Ausführungen den gleichen Effekt haben.
* Verwenden Sie die global verfügbare Eigenschaft von Feldern, um die Werte von Feldern, die sich in einem verzögert geladenen Bereich befinden, für alle anderen Bereiche eines Formulars verfügbar zu machen.
* Leiten Sie den Referenzwert eines Felds in einem verzögerten Bereich nicht weiter, unabhängig davon, ob das Feld global über Fragmente hinweg markiert ist oder nicht.
* Verwenden Sie die Funktion zum Zurücksetzen des Bedienfelds, um alle im Bedienfeld sichtbaren Elemente mithilfe des folgenden Ausdrucks für ein Klickereignis zurückzusetzen.\
  guideBridge.resolveNode(guideBridge.getFocus({&quot;focusOption&quot;: &quot;navigablePanel&quot;})).resetData()
