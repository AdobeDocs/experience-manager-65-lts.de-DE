---
title: Wiederverwenden adaptiver Formulare
description: Sie können ein vorhandenes adaptives Formular verwenden, um neue adaptive Formulare zu erstellen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: ef564750-f107-41cb-887e-fc6d22b7d32e
feature: Adaptive Forms,Foundation Components
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: 37637d7a-cbf3-4fe7-8506-0b4116a01808
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 100%

---

# Wiederverwenden adaptiver Formulare {#reusing-adaptive-forms}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/manage-metadata/reusing-adaptive-forms.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

## Einführung {#introduction}

Wenn Sie für ein neues adaptives Formular einige der Eigenschaften eines vorhandenen adaptiven Formulars verwenden möchten, können Sie einfach die Funktion zum Kopieren/Einfügen verwenden. Darüber hinaus können Sie das neue adaptive Formular in den gewünschten Ordnerpfad einfügen. Alle Metadateneigenschaften werden repliziert und die XFAs und XSDs für XFA- und XSD-basierte adaptive Formulare werden ebenfalls kopiert.

>[!NOTE]
>
>Status- und Überprüfungsdetails werden nicht kopiert. Wenn zum Beispiel Ihr adaptives Formular veröffentlicht wird und Sie es dann kopieren, befindet sich das eingefügte adaptive Formular im unveröffentlichten Status. Ebenso wenig wird, wenn ein kopiertes Asset überprüft wird, das eingefügte Asset derselben Überprüfung unterzogen.

### Kopieren adaptiver Formulare {#copy-an-adaptive-form}

Kopieren Sie ein adaptives Formular mithilfe eines der folgenden Verfahren:

1. Klicken Sie in Schnellaktionen auf das Symbol ![aem6forms_copy](assets/aem6forms_copy.png) zum Kopieren.

   >[!NOTE]
   >
   >Schnellaktionen sind die Aktionselemente, die beim Zeigen mit der Maus auf eine Miniaturansicht angezeigt werden.

1. Wählen Sie das adaptive Formular aus.  Der Auswahlprozess unterscheidet sich je nach Ansicht.

   Wenn Sie sich in der Kartenansicht befinden, wechseln Sie zum Auswahlmodus, indem Sie das Auswahlsymbol ![aem6forms_check-circle](assets/aem6forms_check-circle.png) und alle adaptiven Formulare anklicken, die Sie kopieren möchten.

   Wenn Sie sich in der Listenansicht befinden, aktivieren Sie die Kontrollkästchen der gewünschten adaptiven Formulare, um sie auszuwählen.

   >[!NOTE]
   >
   >Alle ausgewählten Assets müssen adaptive Formulare sein, da die Kopieren/Einfügen-Funktion nur bei adaptiven Formularen unterstützt wird. Außerdem müssen sich alle ausgewählten Elemente in demselben Ordner befinden.

   Nach dem Auswählen der Assets klicken Sie auf das Symbol ![aem6forms_copy](assets/aem6forms_copy.png) in der Symbolleiste, um das ausgewählte adaptive Formular zu kopieren.

### Einfügen adaptiver Formulare {#paste-an-adaptive-form}

Wenn Sie auf die Kopieraktion klicken, wird der Auswahlmodus automatisch beendet und das Symbol zum Einfügen ![aem6forms_paste](assets/aem6forms_paste.png) wird sichtbar. Gehen Sie nun zum gewünschten Ordnerpfad und klicken Sie auf das Symbol ![aem6forms_paste](assets/aem6forms_paste.png), um das kopierte adaptive Formular einzufügen.

Wenn Sie in denselben Ordner einfügen oder sich im Zielordner eine weitere Datei mit demselben Knotennamen (mit dem sie im CRX-Repository gespeichert ist) befindet, wird am Suffix eine 1 angehängt (zum Beispiel wird „myaf“ zu „myaf1“ und wenn sich „myaf1“ am selben Speicherort befindet, wird „myaf“ zu „myaf2“). Alle anderen Eigenschaften bleiben genauso wie beim ursprünglichen adaptiven Formular.

Nachdem Sie auf das Einfugen-Symbol ![aem6forms_paste](assets/aem6forms_paste.png) geklickt haben, wird es wieder ausgeblendet. Sie können jeweils nur einmal einfügen. Wenn Sie vom selben Asset erneut eine Kopie erstellen möchten, kopieren Sie es erneut.

### Ändern der Inhalte eines neuen adaptiven Formulars {#change-contents-of-new-adaptive-form}

Wenn Sie eingefügte adaptive Formulare anders als das kopierte Formular gestalten möchten, können ihre Inhalte mithilfe der folgenden Methoden geändert werden:

1. **Ändern der Metadateneigenschaften:**

   Sie können die Metadateneigenschaften des adaptiven Formulars ändern, z. B. Titel und Beschreibung. Weitere Informationen zu Metadateneigenschaften und dazu, wie diese geändert werden können, finden Sie unter [Verwalten von Formularmetadaten](/help/forms/using/manage-form-metadata.md).

1. **Ändern von XFA/XSD für XFA-/XSD-basierte adaptive Formulare:**

   Sie können die in adaptiven Formularen verwendete XFA/XSD ändern. Informationen zum Ändern dieser adaptiven Formulare finden Sie unter [Verwalten von Formularmetadaten](/help/forms/using/manage-form-metadata.md).

1. **Neu veröffentlichen:**

   Das eingefügte Asset unterscheidet sich vom kopierten Asset. Sie können es als neues Asset veröffentlichen, um es für Endbenutzende verfügbar zu machen. Informationen zum Veröffentlichen von Assets finden Sie unter [Veröffentlichen von Formularen und Veröffentlichungen rückgängig machen](/help/forms/using/publishing-unpublishing-forms.md).
