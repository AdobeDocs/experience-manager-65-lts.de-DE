---
title: Erstellen des Formulardatenmodells
description: Erfahren Sie, wie Sie Formulardatenmodelle mit oder ohne konfigurierte Datenquellen erstellen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integration
docset: aem65
feature: Form Data Model
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: b27fceaf-38f8-433e-96c6-4f98bafa31af
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 100%

---

# Erstellen des Formulardatenmodells{#create-form-data-model}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/create-form-data-models.html?lang=de) |
| AEM 6.5 | Dieser Artikel |


![hero-image](do-not-localize/data-integration.png)

Die AEM Forms-Datenintegration bietet eine intuitive Benutzeroberfläche, um Formulardatenmodelle zu erstellen und mit ihnen zu arbeiten. Ein Formulardatenmodell stützt sich auf Datenquellen für den Austausch von Daten. Sie können jedoch ein Formulardatenmodell mit oder ohne Datenquelle erstellen. Je nachdem, ob Sie Datenquellen konfiguriert haben, gibt es zwei Möglichkeiten, ein Formulardatenmodell zu erstellen:

* **Vorkonfigurierte Datenquellen verwenden**: Wenn Sie Datenquellen wie in [Konfigurieren von Datenquellen](../../forms/using/configure-data-sources.md) konfiguriert haben, können Sie diese beim Erstellen eines Formulardatenmodells auswählen. Es stellt alle Datenmodellobjekte, Eigenschaften und Services aus den ausgewählten Datenquellen zur Verwendung im Formulardatenmodell zur Verfügung.

* **Ohne Datenquellen**: Wenn Sie keine Datenquellen für Ihr Formulardatenmodell konfiguriert haben, können Sie es auch ohne Datenquellen erstellen. Sie können das Formulardatenmodell verwenden, um adaptive Formulare und interaktive Kommunikation zu erstellen und sie anhand von Beispieldaten zu testen. Wenn Datenquellen verfügbar sind, können Sie das Formulardatenmodell an Datenquellen binden, was sich automatisch in den zugehörigen adaptiven Formularen und interaktiven Kommunikationen reflektiert.

>[!NOTE]
>
>Sie müssen Mitglied der beiden Gruppen **fdm-author** und **forms-user** sein, um Formulardatenmodelle erstellen und verwenden zu können. Wenden Sie sich an Ihre AEM-Admins, um Mitglied der Gruppe zu werden.

## Erstellen des Formulardatenmodells {#data-sources}

Stellen Sie sicher, dass Sie die Datenquellen konfiguriert haben, die Sie im Formulardatenmodell verwenden möchten, wie in [Konfigurieren von Datenquellen](../../forms/using/configure-data-sources.md) beschrieben. Gehen Sie folgendermaßen vor, um ein Formulardatenmodell basierend auf konfigurierten Datenquellen zu erstellen:

1. Navigieren Sie in der AEM-Autoreninstanz zu **[!UICONTROL Formulare > Datenintegration]**.
1. Wählen Sie **[!UICONTROL Erstellen > Formulardatenmodell]** aus.
1. Im Dialogfeld „Formulardatenmodell erstellen“:

   * Geben Sie einen Namen für das Formulardatenmodell an.
   * (**Optional**) Geben Sie Titel, Beschreibung und Tags für das Formulardatenmodell an.
   * (**Optional und nur anwendbar, wenn Datenquellen konfiguriert sind**) Wählen Sie das Häkchensymbol neben dem Feld **[!UICONTROL Datenquellenkonfiguration]** und dann den Konfigurationsknoten aus, in dem sich die Cloud-Services für die Datenquellen befinden, die verwendet werden sollen. Das beschränkt die Liste der Datenquellen, die auf der nächsten Seite zur Auswahl stehen, auf diejenigen, die im ausgewählten Konfigurationsknoten verfügbar sind. Alle JDBC-Datenbank- und AEM-Benutzerprofildatenquellen werden jedoch standardmäßig aufgelistet. Wenn Sie keinen Konfigurationsknoten auswählen, werden Datenquellen aus allen Konfigurationsknoten aufgelistet.

   Wählen Sie **[!UICONTROL Weiter]** aus.

1. (**Trifft nur zu, wenn Datenquellen konfiguriert sind**) Der Bildschirm **[!UICONTROL Datenquelle auswählen]** listet verfügbare Datenquellen auf, falls vorhanden. Wählen Sie Datenquellen aus, die Sie im Formulardatenmodell verwenden möchten.
1. Wählen Sie **[!UICONTROL Erstellen]** und dann im Bestätigungsdialog die Option **[!UICONTROL Öffnen]** aus, um den Formulardatenmodelleditor zu öffnen.

Im Folgenden werden die verschiedenen Komponenten der Benutzeroberfläche im Formulardatenmodell-Editor beschrieben.

![Formulardatenmodell mit drei Datenquellen: einem RESTful-Dienst, einem AEM-Benutzerprofil und eines RDBMS](assets/fdm-ui.png)

**A. Data Sources**: Listet Datenquellen in einem Formulardatenmodell auf. Erweitern Sie eine Datenquelle, um ihre Datenmodellobjekte und Services anzuzeigen.

**B. Datenquellendefinitionen aktualisieren**: Ruft alle Änderungen in den Datenquellendefinitionen aus den konfigurierten Datenquellen ab und aktualisiert sie in der Registerkarte „Datenquellen“ des Formulardatenmodell-Editors.

**C. Modell**: Inhaltsbereich, in dem hinzugefügte Datenmodellobjekte erscheinen.

**D. Services**: Inhaltsbereich, in dem hinzugefügte Datenquellenvorgänge oder -Services angezeigt werden.

**E. Symbolleiste**: Tools zum Arbeiten mit einem Formulardatenmodell. Die Symbolleiste zeigt mehr Optionen, abhängig vom ausgewählten Objekt im Formulardatenmodell.

**F. Ausgewählte hinzufügen**: Fügt dem Formulardatenmodell ausgewählte Datenmodellobjekte und Services hinzu.

Weitere Informationen zum Formulardatenmodell-Editor und dazu, wie Sie damit das Formulardatenmodell bearbeiten und konfigurieren können, finden Sie unter [Arbeiten mit einem Formulardatenmodell](../../forms/using/work-with-form-data-model.md).

## Aktualisieren von Datenquellen {#update}

Führen Sie folgende Schritte aus, um Datenquellen zu einem vorhandenen Formulardatenmodell hinzuzufügen oder sie zu aktualisieren.

1. Gehen Sie zu **[!UICONTROL Formulare > Datenintegrationen]**. Wählen Sie erst das Formulardatenmodell aus, in dem Datenquellen hinzugefügt oder aktualisiert werden sollen, und dann **[!UICONTROL Eigenschaften]**.
1. Wechseln Sie in den Eigenschaften des Formulardatenmodells zur Registerkarte **[!UICONTROL Quelle aktualisieren]**.

   Auf der Registerkarte Quelle aktualisieren:

   * Wählen Sie das Symbol „Durchsuchen“ im Feld **[!UICONTROL Kontextabhängige Konfiguration]** und dann einen Konfigurationsknoten aus, in dem sich die Cloud-Konfiguration für die hinzuzufügende Datenquelle befindet. Wenn Sie keinen Knoten auswählen, werden nur Cloud-Konfigurationen im Knoten `global` aufgelistet, wenn Sie **[!UICONTROL Quellen hinzufügen]** auswählen.

   * Um eine neue Datenquelle hinzuzufügen, wählen Sie **[!UICONTROL Quellen hinzufügen]** und dann die Datenquellen aus, die dem Formulardatenmodell hinzugefügt werden sollen. Alle in `global` konfigurierten Datenquellen und ggf. der ausgewählte Konfigurationsknoten werden angezeigt.

   * Um eine vorhandene Datenquelle durch eine andere Datenquelle desselben Typs zu ersetzen, wählen Sie das Symbol **[!UICONTROL Bearbeiten]** für die Datenquelle und dann diese Datenquelle aus der Liste der verfügbaren Datenquellen aus.
   * Um eine vorhandene Datenquelle zu löschen, wählen Sie das Symbol **[!UICONTROL Löschen]** für die Datenquelle aus. Das Symbol „Löschen“ ist deaktiviert, wenn ein Datenmodellobjekt in der Datenquelle im Formulardatenmodell hinzugefügt wird.

   ![fdm-properties](assets/fdm-properties.png)

1. Wählen Sie **[!UICONTROL Speichern und schließen]** aus, um die Aktualisierungen zu speichern.

>[!NOTE]
>
>Nachdem Sie neue Datenquellen hinzugefügt oder vorhandene Datenquellen in einem Formulardatenmodell aktualisiert haben, stellen Sie sicher, dass Sie die Bindungsreferenzen in adaptiven Formularen und interaktiven Kommunikationen, die das aktualisierte Formulardatenmodell verwenden, entsprechend aktualisieren.

## Nächste Schritte {#next-steps}

Jetzt haben Sie ein Formulardatenmodell, dem Datenquellen hinzugefügt wurden. Als Nächstes können Sie das Formulardatenmodell bearbeiten, um Datenmodellobjekte und -dienste hinzuzufügen und zu konfigurieren, Verknüpfungen zwischen Datenmodellobjekten hinzuzufügen, Eigenschaften zu bearbeiten, benutzerdefinierte Datenmodellobjekte und -eigenschaften hinzuzufügen, Beispieldaten zu generieren usw.

Weitere Informationen finden Sie unter [Arbeiten mit einem Formulardatenmodell](../../forms/using/work-with-form-data-model.md).
