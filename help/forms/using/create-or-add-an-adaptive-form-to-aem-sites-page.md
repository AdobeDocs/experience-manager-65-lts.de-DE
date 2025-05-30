---
title: Erstellen oder Hinzufügen eines adaptiven Formulars zur AEM Sites-Seite
description: Erfahren Sie, wie Sie mühelos ein adaptives Formular erstellen oder nahtlos zu Ihrer AEM Sites-Seite hinzufügen können. Lernen Sie schrittweise Techniken und Best Practices für die Integration dynamischer und anpassbarer Formulare in Ihre Website kennen, um Ihre digitalen Erlebnisse für eine maximale Wirkung zu optimieren.
Keywords: AEM Forms in sites, AF in Sites editor, af in aem sites, aem sites af, add af to a sites page, af aem sites, af sites, create af in a sites page, adaptive form in aem sites, forms aem sites, add form to a sites page, adaptive forms aem sites, add adaptive forms to aem page, create forms in an aem sites page
feature: Adaptive Forms,Foundation Components
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: 6e69ca67-883f-4079-96e2-5b7a9c843ada
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '2884'
ht-degree: 100%

---

# Erstellen oder Hinzufügen eines adaptiven Formulars zur AEM Sites-Seite {#create-or-add-an-adaptive-form-to-aem-sites-page}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | Dieser Artikel |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/create-or-add-an-adaptive-form-to-aem-sites-page.html?lang=de) |

Mit AEM Forms können Sie adaptive Formulare nahtlos in Ihre Web-Seiten integrieren. Dadurch können Ihre Besuchenden bequem Formulare ausfüllen und senden, ohne jemals die Seite verlassen zu müssen, auf der sie sich befinden. Sie können mühelos mit anderen Elementen der Website interagieren und gleichzeitig aktiv mit dem Formular interagieren.

Mit dem AEM-Seiteneditor können Sie schnell mehrere Formulare erstellen und zu Ihren AEM Sites-Seiten hinzufügen. Die Verwendung des AEM-Seiteneditors ermöglicht es Inhaltsautorinnen und -autoren, nahtlose Erlebnisse zur Datenerfassung auf einer Sites-Seite erstellen, indem sie die Leistung adaptiver Formularkomponenten nutzen, einschließlich dynamischem Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Außerdem können Sie verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager.

AEM Forms bietet Container für adaptive Formulare und die „Adaptive Formulare – Einbettungskomponente“. Sie können den Container für adaptive Formulare verwenden, um ein Formular auf einer Experience Fragment- oder AEM Sites-Seite zu erstellen. Sie können auch mit der Einbettungskomponente für adaptive Formulare ein vorhandenes adaptives Formular hinzufügen oder mit dem Editor für adaptive Formulare ein neues Formular erstellen.

![Adaptives Formular auf der Sites-Seite](/help/forms/using/assets/adaptive-form-in-sites-page.png)

## Vorteile der Verwendung der Container-Komponente für adaptive Formulare im AEM-Seiteneditor oder im Experience Fragment

Mit dem Container für adaptive Formulare im AEM-Seiteneditor können Sie nahtlose Erlebnisse zur Datenerfassung auf einer Sites-Seite erstellen, indem Sie die Möglichkeiten der Komponenten für adaptive Formulare nutzen, darunter dynamisches Verhalten, Validierungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Darüber hinaus können Sie verschiedene Funktionen von AEM Sites-Seiten verwenden, wie z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager, wodurch die Erstellung und Verwaltung von Formularen insgesamt verbessert wird. Sehen wir uns einige dieser Funktionen an:

* **Versionierung:** AEM Sites-Seiten bieten eine [robuste Versionierungfähigkeiten](/help/sites-authoring/working-with-page-versions.md), mit der Sie verschiedene Versionen Ihrer Formulare verfolgen und verwalten können. Dadurch können Sie Änderungen und Verbesserungen an Formularen vornehmen und gleichzeitig bei Bedarf frühere Versionen wiederherstellen. Versionierung stellt einen kontrollierten und organisierten Ansatz für die Formularentwicklung und -weiterentwicklung sicher.
* **Targeting (Integration mit Adobe Target):** Mit den Targeting-Funktionen von AEM Sites-Seiten können Sie auch [das Formularerlebnis für verschiedene Zielgruppen personalisieren](/help/sites-administering/target.md). Mithilfe von Benutzersegmenten und Targeting-Kriterien können Sie den Inhalt, das Design oder das Verhalten des Formulars an bestimmte Benutzergruppen anpassen. Auf diese Weise können Sie ein personalisiertes und relevantes Formularerlebnis bereitstellen und die Interaktions- und Konversionsraten steigern.
* **Übersetzung:** AEM Sites kann [nahtlos mit Übersetzungsdiensten integriert werden](/help/sites-administering/translation.md), sodass Sie Formulare einfach in mehrere Sprachen übersetzen können. Diese Funktion vereinfacht den Lokalisierungsprozess und stellt sicher, dass Ihre Formulare für eine globale Zielgruppe zugänglich ist. Sie können Übersetzungen effizient in AEM-Übersetzungsprojekten verwalten und so Zeit und Aufwand für die Unterstützung mehrsprachiger Formulare reduzieren. Weitere Informationen zur Übersetzung finden Sie im Abschnitt „Überlegungen“.
* **Multi-Site-Management und Live Copy:** AEM Sites bietet robuste [Multi-Site-Management- und Live Copy-Funktionen](/help/sites-administering/msm.md), mit denen Sie mehrere Websites in einer einzigen Umgebung erstellen und verwalten können. Mit dieser Funktion können Sie nun Formulare über verschiedene Sites hinweg wiederverwenden, was Konsistenz gewährleistet und doppelte Arbeit vermeidet. Mit zentralisierter Kontrolle und Verwaltung können Sie Formulare effizient über mehrere Websites hinweg verwalten und aktualisieren.
* **Themen:** AEM Sites-Seiten bieten ein Framework für das Entwerfen und Verwalten konsistenter visueller Stile auf mehreren Web-Seiten. Diese definieren Farben, Schriftarten, Stylesheets und andere visuelle Elemente, die zum allgemeinen Look-and-Feel der Website beitragen. [Sie können die Designs verwenden, die für ein adaptives Formular einer AEM Sites-Seite entwickelt wurden, was Zeit und Mühe spart.](/help/sites-authoring/style-system.md).
* **Tagging:** Mit AEM Sites-Seiten können Sie [Tags oder Beschriftungen zu einer Seite, einem Asset oder anderen Inhalten zuweisen](/help/sites-authoring/tags.md). Tags sind Keywords oder Metadatenbeschriftungen, die eine Möglichkeit bieten, Inhalte basierend auf bestimmten Kriterien zu kategorisieren und zu organisieren. Sie können Seiten, Assets oder anderen Inhaltselementen in AEM ein oder mehrere Tags zuweisen, um die Suche zu verbessern und die Assets zu kategorisieren.
* **Sperren und Entsperren von Inhalten:** Mit AEM Sites können Benutzerinnen und Benutzer in der AEM Sites-Umgebung [Zugriff und Änderungen auf Seiten steuern](/help/sites-authoring/editing-content.md#locking-a-page-locking-a-page). Wenn eine Seite gesperrt ist, bedeutet dies, dass sie von anderen Benutzenden vor unbefugten Änderungen oder Bearbeitungen geschützt ist. Nur Benutzende, die den Inhalt gesperrt haben, oder Admins können ihn entsperren, um Änderungen zuzulassen.


## Verschiedene Optionen zum Hinzufügen eines adaptiven Formulars im AEM-Seiteneditor

Sie können diese Funktion voll nutzen, indem Sie die folgenden Optionen verwenden:

* **[Fügen Sie ein benutzerdefiniertes adaptives Formular zu einer AEM Sites-Seite hinzu:](#create-an-adaptive-form-in-sites-editor)** Erstellen Sie ein ganz neues Formular, passen Sie es speziell an Ihre Anforderungen und Design-Vorlieben an.

* **[Fügen Sie ein benutzerdefiniertes adaptives Formular zu einem Experience Fragments hinzu:](#create-an-adaptive-form-in-experience-fragment)** Erweitern Sie die Reichweite Ihrer Formulare, indem Sie sie zu AEM Experience Fragments hinzufügen, sodass sie nahtlos über mehrere Seiten oder Sites hinweg wiederverwendet werden können.

* **[Konvertieren eines adaptiven Formulars in ein Experience Fragment:](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)** Konvertieren Sie ein adaptives Formular, das zu einer AEM Sites-Seite hinzugefügt wurde, in ein Experience Fragment, um das Formular auf mehreren AEM Sites-Seiten wiederzuverwenden.

* **Erstellen Sie Formulare basierend auf genehmigten Vorlagen und fügen Sie sie einer AEM Sites-Seite hinzu:** Nutzen Sie vorab genehmigte Vorlagen, um schnell Formulare zu erstellen, die den Branding-Richtlinien und Design-Standards Ihres Unternehmens entsprechen. Die Option ist nur für adaptive Formulare verfügbar, die mit dem adaptiven Formular-Editor oder der „Adaptiven Formular – Einbettungskomponente“ erstellt wurde.

* **Fügen Sie vorhandene Formulare zu einer AEM Sites-Seite hinzu:** Einfache Integration von bereits erstellten Formularen in Ihre Websites, sodass Besuchende direkt mit ihnen interagieren können. Die Option ist nur für adaptive Formulare verfügbar, die mit dem adaptiven Formular-Editor oder der „Adaptiven Formular – Einbettungskomponente“ erstellt wurde.

* **Fügen Sie einer AEM Sites-Seite oder einem Experience Fragment mehrere Formulare hinzu:** Fügen Sie einer Seite mehrere Formulare hinzu, um Benutzenden basierend auf ihren Voreinstellungen und Anforderungen mehrere Optionen zur Verfügung zu stellen. Diese können eine Kombination aus neuen und vorhandenen Formularen darstellen.

## Überlegungen {#consideration}

* Wenn Sie den Container für adaptive Formulare verwenden, um ein Formular zu erstellen oder hinzuzufügen, werden die Formulare über den AEM Sites-Übersetzungsfluss übersetzt und lokalisiert. Für jede Sprache wird eine separate Kopie (Sprachkopie) der Sites-Seite und der entsprechenden Formulare generiert. Wenn Inhaltsautorinnen oder -autoren eine Regel in einem Formular auf der übergeordneten Seite ändern, müssen dieselben Änderungen in allen Sprachkopien des Formulars vorgenommen werden. Mit dem Container für adaptive Formulare können Sie auch verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager.

* Wenn Sie ein Formular mithilfe der Einbettungskomponente für adaptive Formulare erstellen oder hinzufügen, werden die Formulare mithilfe des Übersetzungsflusses von AEM Forms übersetzt und lokalisiert. In diesem Fall wird ein einzelnes Formular beibehalten und in allen Sprachkopien der Sites-Seiten referenziert. Die Einbettungskomponente für adaptive Formulare bietet keinen Zugriff auf verschiedene Funktionen von AEM Sites-Seiten wie Versionierung, Targeting, Übersetzung und Multi-Site-Manager.


## Bevor Sie beginnen {#before-you-start}

+++  Aktivieren der Kernkomponenten adaptiver Formulare für Ihre Umgebung

Stellen Sie sicher, dass die [Kernkomponenten adaptiver Formulare für Ihre Umgebung aktiviert sind](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/quick-setup/enable-headless-adaptive-forms-and-core-components.html?lang=de).

+++

+++  Hinzufügen von Client-Bibliotheken adaptiver Formulare zu Ihren AEM Sites-Seiten- und Experience Fragment-Seitenkomponenten

Um die vollständige Funktionalität der adaptiven Formular-Container-Komponente zu aktivieren, fügen Sie die Client-Bibliotheken „customHeaderlibs“ und „customfooterlibs“ mithilfe der Bereitstellungs-Pipeline zu Ihrer AEM Sites-Seite hinzu. So fügen Sie die Bibliotheken hinzu:

1. Melden Sie sich bei Ihrer AEM Authoring-Instanz an und öffnen Sie CRX DE. Die Standard-URL für eine lokal ausgeführte Authoring-Instanz lautet: `http://localhost:4502/crx/de`.

1. Öffnen Sie die Datei `/apps/[your-sites-project]/components/page/customheaderlibs.html` und fügen Sie ihr den folgenden Code hinzu:

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Öffnen Sie die Datei `/apps/[your-sites-project]/components/page/customfooterlibs.html` und fügen Sie ihr den folgenden Code hinzu:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. Öffnen Sie die Datei `/apps/[your-sites-project]/components/xfpage/customheaderlibs.html` und fügen Sie ihr den folgenden Code hinzu:

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Öffnen Sie die Datei `/apps/[your-sites-project]/components/customfooterlibs.html` und fügen Sie ihr den folgenden Code hinzu:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. Wiederholen Sie die obigen Schritte für alle Authoring- und Publishing-Instanzen in Ihrer Umgebung.

+++

+++ Aktivieren der Container-Komponente adaptiver Formulare

Um die Komponente [!UICONTROL Container für adaptive Formulare] in der Richtlinie der Vorlage zu aktivieren, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die AEM Sites-Seite oder das Experience Fragment zur Bearbeitung. Um die Seite zur Bearbeitung zu öffnen, wählen Sie die Seite aus und klicken Sie auf „Bearbeiten“.
1. Öffnen Sie die Vorlage Ihrer Sites- oder Experience Fragment-Seite. Um die Vorlage zu öffnen, navigieren Sie zu [!UICONTROL Seiteninformationen] ![Seiteninformationen](/help/forms/using/assets/Smock_Properties_18_N.svg) > [!UICONTROL Vorlage bearbeiten]. Dadurch wird die entsprechende Vorlage im Vorlageneditor geöffnet.
1. Klicken Sie in der Strukturansicht auf das Symbol **[!UICONTROL Richtlinie]** ![Richtlinie](/help/forms/using/assets/Smock_FeedManagement_18_N.svg) in der Menüleiste. Klicken Sie auf die Liste **[!UICONTROL Zulässige Komponenten]** und aktivieren Sie das Kontrollkästchen **[!UICONTROL Container für adaptive Formulare]** unter **[AEM-Projektarchetyp-Name] – Adaptives Formular**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

## Erstellen eines adaptiven Formulars {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

Sie können ein brandneues Formular direkt auf einer AEM Sites-Seite oder im Experience Fragment von Grund auf neu erstellen und es speziell an Ihre Anforderungen und Design-Voreinstellungen anpassen. Bei Formularen mit nur einem Verwendungszweck wird empfohlen, eine AEM Sites-Seite direkt zu erstellen, während Experience Fragments sich ideal für Formulare eignen, die auf mehreren Seiten auf Ihrer Website wiederverwendet werden müssen.

* [Erstellen eines Formulars auf einer AEM Sites-Seite](#create-an-adaptive-form-in-sites-editor)
* [Erstellen eines Formulars in einem Experience Fragment](#create-an-adaptive-form-in-experience-fragment)
* [Konvertieren eines adaptiven Formulars auf einer AEM-Sites-Seite zu einem Experience Fragment](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### Erstellen eines Formulars auf einer AEM Sites-Seite {#create-an-adaptive-form-in-sites-editor}

Sie können die Container-Komponente für adaptive Formulare im AEM-Seiteneditor verwenden, um ein benutzerdefiniertes Formular zu erstellen. Mit der Komponente können Sie ein Formular erstellen, indem Sie die Formularkomponenten per Drag-and-Drop verschieben. Die Formularkomponenten basieren auf Kernkomponenten. Sie können diese einfach entsprechend den Anforderungen Ihrer Organisation anpassen.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

So erstellen Sie ein adaptives Formular auf einer Sites-Seite:

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie die Container-Komponente für **[!UICONTROL adaptive Formulare]** vom Komponenten-Browser per Drag-and-Drop zur Sites-Seite. Dadurch wird Platz auf der Seite für das Formular erstellt. Sie können den Layout-Modus verwenden, um die Größe des Container-Bereichs zu ändern.
1. Ziehen Sie Kernkomponenten des adaptiven Formulars per Drag-and-Drop in den Container-Bereich, um das Formular zu erstellen.
1. Fügen Sie die Schaltfläche „Senden“ hinzu.

Legen Sie als Nächstes die [Aktion „Senden“](#configure-submit-action-for-form) und erweiterte Eigenschaften fest.

### Erstellen eines Formulars in einem Experience Fragment {#create-an-adaptive-form-in-experience-fragment}

Sie können die Reichweite Ihrer Formulare erweitern, indem Sie sie zu AEM Experience Fragments hinzufügen, wodurch eine nahtlose Wiederverwendung über mehrere Seiten oder Sites hinweg ermöglicht wird. Sie können beispielsweise ein Newsletter-Anmeldeformular in ein Experience Fragment einfügen. Dadurch können Sie das Fragment bequem über mehrere Seiten Ihrer Website hinweg wiederverwenden, sodass das Formular nicht wiederholt neu erstellt werden muss. Alle Aktualisierungen oder Änderungen, die im Experience Fragment am Newsletter-Anmeldeformular vorgenommen werden, werden automatisch auf alle Seiten übertragen, auf denen es verwendet wird. Dadurch wird der Prozess optimiert und ein nahtloses Benutzererlebnis bei gleichzeitiger Vereinfachung der Verwaltung von Formularen auf Ihrer Website sichergestellt.

So erstellen Sie ein adaptives Formular in einem Experience Fragment:

1. Öffnen Sie ein Experience Fragment.
1. Ziehen Sie die Container-Komponente für **[!UICONTROL adaptive Formulare]** vom Komponenten-Browser per Drag-and-Drop zum Experience Fragment.
1. Ziehen Sie Kernkomponenten des adaptiven Formulars per Drag-and-Drop in den Container-Bereich im Experience Fragment, um das Formular zu erstellen.
1. Fügen Sie die Schaltfläche „Senden“ hinzu.

Legen Sie als Nächstes die [Sendeaktion](#configure-submit-action-for-form) und erweiterte Eigenschaften fest.

### Konvertieren eines adaptiven Formulars in einer AEM Sites-Seite in ein Experience Fragment {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

Sie können ein vorhandenes adaptives Formular in einem Sites-Seiten-Editor in ein Experience Fragment konvertieren, um es auf mehreren Seiten oder Sites wiederzuverwenden.

So konvertieren Sie ein adaptives Formular auf einer AEM Sites-Seite in ein Experience Fragment:

1. Öffnen Sie die AEM Sites-Seite mit dem adaptiven Formular (in der Komponente „Container für adaptive Formulare“) im Bearbeitungsmodus.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]**, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formulare hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Wählen Sie in der Menüleiste das Symbol ![In Experience Fragment-Variante konvertieren](/help/forms/using/assets/Smock_FilingCabinet_18_N.svg).
   ![Konvertieren eines adaptiven Formulars in einer Sites-Seite in ein Experience Fragment](/help/forms/using/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Es wird ein Dialogfeld zum Konvertieren des Containers für adaptive Formulare in ein neues Experience Fragment oder zu dessen Hinzufügen zu einem vorhandenen Experience Fragment angezeigt.
1. Legen Sie im Dialogfeld „In Experience Fragment-Variante konvertieren“ Werte für die folgenden Optionen fest:

   * **Aktion:** Wählen Sie diese Option aus, um ein Experience Fragment zu erstellen oder zu einem vorhandenen Experience Fragment hinzuzufügen.
   * **Übergeordneter Pfad:** Geben Sie den Pfad des Ordners an, in dem das Experience Fragment gehostet werden soll. Die Option ist nur zum Erstellen eines Experience Fragments verfügbar.
   * **Vorlage:** Geben Sie den Pfad der Experience Fragment-Vorlage an. Wenn Sie keine Experience Fragment-Vorlage haben, [erstellen Sie eine](/help/sites-developing/experience-fragments.md). Die Option ist nur zum Hinzufügen des adaptiven Formulars zu einem vorhandenen Experience Fragment verfügbar.
   * **Fragmenttitel:** Geben Sie den Titel des Experience Fragments an. Der Titel identifiziert ein Experience Fragment eindeutig.


## Konfigurieren der Sendeaktion für das Formular {#configure-submit-action-for-form}

Mit einer Übermittlungsaktion können Sie das Ziel der Daten auswählen, die über ein adaptives Formular erfasst werden. Eine Übermittlungsaktion wird ausgelöst, wenn eine Benutzerin bzw. ein Benutzer in einem adaptiven Formular auf die Schaltfläche „Senden“ klickt. Adaptive Formulare enthalten einige vordefinierte Sendeaktionen. Sie können außerdem die standardmäßigen Sendeaktionen erweitern, um Ihre eigene benutzerdefinierte Sendeaktion zu erstellen. So konfigurieren Sie eine Sendeaktion für Ihr Formular:

1. Öffnen Sie den AEM Seiten-Editor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]**, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formulare hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld des Containers für adaptive Formulare zum Konfigurieren von Sendeaktionen wird geöffnet.
   ![Container für adaptive Formulare](/help/forms/using/assets/adaptive-forms-container.png)
1. Wählen Sie je nach Ihren Anforderungen eine Sendeaktion aus und konfigurieren Sie sie. Detaillierte Informationen zu Übermittlungsaktionen finden Sie unter [Übermittlungsaktion für adaptive Formulare](configuring-submit-actions.md)


## Konfigurieren eines Schema- oder Formulardatenmodells für ein Formular {#configure-schema-or-data-model-for-form}

Sie können das Formulardatenmodell verwenden, um ein Formular mit einer Datenquelle zu verbinden und Daten basierend auf Benutzeraktionen zu senden und zu empfangen. Sie können auch ein Formular mit einem JSON-Schema verbinden, um die gesendeten Daten in einem vordefinierten Format zu empfangen.

Bevor Sie ein Formular mit einem Schema oder Formulardatenmodell verbinden

* [Erstellen Sie ein JSON-Schema und laden Sie es in Ihre Umgebung hoch](adaptive-form-json-schema-form-model.md)
* [Erstellen eines Formulardatenmodells](create-form-data-models.md)

So konfigurieren Sie ein JSON-Schema oder ein Formulardatenmodell für Ihr Formular:

1. Öffnen Sie den AEM Seiten-Editor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]**, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formulare hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld der Container für adaptive Formulare zum Konfigurieren von Datenmodellen wird geöffnet.
   ![Formulardatenmodell – Container für adaptive Formulare](/help/forms/using/assets/form-data-model-adaptive-forms-container.png)
1. Wählen Sie ein JSON-Schema oder ein Formulardatenmodell aus und konfigurieren Sie es entsprechend Ihren Anforderungen. Detaillierte Informationen zu Sendeaktionen finden Sie unter [Sendeaktion für adaptive Formulare](configuring-submit-actions.md).

   * Wenn Sie die Option **[!UICONTROL Formularmodell]** wählen, können Sie mit der Option **[!UICONTROL Formulardatenmodell auswählen]** ein vorkonfiguriertes Formulardatenmodell auswählen.
   * Wenn Sie die Option **[!UICONTROL Schema]** wählen, verwenden Sie die Option **[!UICONTROL Schema]**, um ein JSON-Schema für Ihr Formular auszuwählen.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Konfigurieren eines Vorbefüllungsdienstes für ein Formular {#configure-prefill-service-for-form}

Sie können den Vorbefüllungsdienst verwenden, um Felder eines adaptiven Formulars mit vorhandenen Daten automatisch auszufüllen. Wenn eine Benutzerin oder ein Benutzer ein Formular öffnet, sind die Werte für diese Felder schon vorbefüllt. Sie haben folgende Möglichkeiten:

* [Erstellen eines benutzerdefinierten Vorbefüllungsdienstes](prepopulate-adaptive-form-fields.md)
* [Verwenden des Vorbefüllungsdienstes für Formulardatenmodelle](#fdm-prefill-service)

### Verwenden des Vorbefüllungsdienstes für Formulardatenmodelle {#fdm-prefill-service}

Sie können den Vorbefüllungsdienst für Formulardatenmodelle verwenden, um Felder eines Formulars mit einem konfigurierten Formulardatenmodell im Voraus auszufüllen. Der Vorbefüllungsdienst für das Formulardatenmodell verwendet den [Get-Dienst des konfigurierten Formulardatenmodells](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) zum Abrufen von Daten. So verwenden Sie für ein adaptives Formular den Vorbefüllungsdienst für Formulardatenmodelle:

1. Öffnen Sie den AEM Seiten-Editor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]**, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formulare hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld der Container für adaptive Formulare zum Konfigurieren von Datenmodellen wird geöffnet.
   ![Vorbefüllungsdienst für Formulardatenmodelle – Seiteneditor von AEM Sites](/help/forms/using/assets/prefill-service-fdm-aem-sites-page-editor.png)
1. Wählen Sie ein Formulardatenmodell aus. Öffnen Sie die Registerkarte **[!UICONTROL Allgemein]**. Wählen Sie im Vorbefüllungsdienst die Option **[!UICONTROL Formularportal-Entwurf des Vorbefüllungsdienstes]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Leitet die Benutzenden bei der Formularübermittlung an eine neue Benutzerin bzw. einen neuen Benutzer weiter oder zeigt eine Dankesnachricht an

Beim Senden eines Formulars können Sie die Benutzenden zu einer anderen Web-Seite oder Nachricht umleiten. So leiten Sie die Benutzenden um oder konfigurieren die Dankesnachricht:

1. Öffnen Sie den AEM Seiten-Editor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]**, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formulare hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld der Container für adaptive Formulare zum Konfigurieren von Datenmodellen wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Übermittlung]**.

   * Um eine Umleitungs-URL zu konfigurieren, wählen Sie für die Sendeoption die Option „Zu URL umleiten“ aus und geben Sie eine absolute Adresse, eine Umleitungs-URL oder einen relativen Pfad einer AEM Sites-Seite an.

   * Um eine benutzerdefinierte Nachricht oder eine Dankesnachricht zu konfigurieren, wählen Sie für die Sendeoption die Option „Nachricht anzeigen“ und geben Sie im Feld „Nachrichteninhalt“ eine Nachricht ein. Es handelt sich um ein Rich-Text-Feld. Sie können die Vollbildoption verwenden, um alle verfügbaren Rich-Text-Elemente anzuzeigen.

## Siehe auch {#see-also}

* [Erstellen eines eigenständigen, auf Kernkomponenten basierenden adaptiven Formulars](/help/forms/using/create-an-adaptive-form-core-components.md)
* [Erstellen von Stilen oder Designs für Ihre Formulare](/help/forms/using/create-or-customize-themes-for-adaptive-forms-core-components.md)
