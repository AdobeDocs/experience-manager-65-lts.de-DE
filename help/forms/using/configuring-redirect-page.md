---
title: Konfigurieren einer Umleitungsseite
description: Nachdem sie ein adaptives Formular ausgefüllt haben, können Benutzende auf eine Web-Seite umgeleitet werden, die Formularautorinnen und -autoren beim Erstellen des Formulars konfigurieren können.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms,Foundation Components
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: dba191d6-4fe9-40e7-a995-00f0c3fd335d
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 100%

---

# Konfigurieren einer Umleitungsseite{#configuring-redirect-page}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-redirect-page.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Formularersteller können für jedes Formular eine Seite konfigurieren, zu der die Formularbenutzer nach dem Absenden eines Formulars umgeleitet werden.

1. Wählen Sie im Bearbeitungsmodus eine Komponente aus, klicken Sie dann auf ![field-level](assets/field-level.png) > **Container für ein adaptives Formular** und anschließend auf ![cmppr](assets/cmppr.png).

1. Klicken Sie in der Seitenleiste auf **Übermittlung**.

1. Geben Sie die URL der Umleitungsseite unter der Danksagung im Bereich „Senden“ an.
1. Optional können Sie unter „Übermittlungsaktion“ für die Aktion „An REST-Endpunkt übermitteln“ den Parameter konfigurieren, der zur Umleitungsseite weitergeleitet wird.

![Konfigurieren der Umleitungsseite](assets/thank-you-setting-1.png)

Konfigurieren der Umleitungsseite

Autorinnen und Autoren von Formularen können folgende Parameter verwenden, die an die Dankesseite weitergegeben werden. Bei allen verfügbaren Übermittlungsaktionen werden `status`- und `owner`-Parameter übergeben. Neben diesen beiden Parametern werden für die folgenden Übermittlungsaktionen einige weitere Parameter weitergeleitet:

* **Aktion für Inhaltsspeicherung** (veraltet): `contentPath` – der Pfad des Knotens im Repository, in dem gesendete Daten gespeichert werden – wird weitergeleitet.

* **Aktion zum Speichern einer PDF** (veraltet): `contentPath` – die gesendeten Daten und der Pfad des Knoten im Repository, in dem die PDF-Datei gespeichert wird, werden weitergeleitet.

* **An Formular-Workflow übermitteln**: Ausgabeparameter, die aus dem Formular-Workflow zurückgegeben wurden, werden weitergeleitet.

* **An REST-Endpunkt übermitteln**: Parameter, die für die Zuordnung feldinterner Werte zu Parametern hinzugefügt wurden, werden weitergeleitet. Die Parameter `status` und `owner` werden bei dieser Übermittlungsaktion nicht weitergeleitet. Weitere Informationen finden Sie unter [Konfigurieren der Übermittlungsaktion „An REST-Endpunkt übermitteln“](../../forms/using/configuring-submit-actions.md). 
