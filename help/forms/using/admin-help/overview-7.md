---
title: Grundlagen der Konfiguration von Formularen
description: Erfahren Sie mehr über die verschiedenen Formulardienste, mit denen Sie interaktive Datenerfassungsanwendungen erstellen können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 68e43842-cba9-47b8-b7a3-6f625dbfca08
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 100%

---

# Grundlagen der Konfiguration von Formularen {#basics-of-configuring-forms}

Der AEM Forms-Dienst ermöglicht es Ihnen, interaktive Client-Anwendungen zur Datenerfassung zu erstellen, die üblicherweise in Designer erstellte Formulare überprüfen, verarbeiten, transformieren und bereitstellen. Formularautorinnen und -autoren entwickeln einen einzelnen Formularentwurf, den der Forms-Dienst in verschiedenen Formaten rendert:

* als PDF in Adobe Reader oder in einem Browser
* als HTML in verschiedenen Browser-Umgebungen, einschließlich kompatiblem XHTML 1.0-Rendering
* als Formularleitfäden in verschiedenen Browser-Umgebungen, die Adobe Flash Player unterstützen

Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz](https://www.adobe.com/go/learn_aemforms_services_63).

Mithilfe der Forms-Seite in der Administrationskonsole können Sie das Verhalten des Forms-Dienstes konfigurieren. Diese Einstellungen gelten für alle Aufrufe des Dienstes. Alle Parameter, die durch das AEM Forms-SDK gesendet werden, überschreiben die in der Administrationskonsole festgelegten Einstellungen. Sie betreffen jedoch nur diesen bestimmten Aufruf. 

Nachdem Sie die Forms-Einstellungen in der Administrationskonsole geändert haben, klicken Sie auf „Speichern“. Der Server muss nicht neu gestartet werden, damit die Änderungen wirksam werden. Sie müssen jedoch ggf. den Forms-Dienst anhalten und neu starten, wenn Sie Cache-Moduseinstellungen konfigurieren. (Siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
