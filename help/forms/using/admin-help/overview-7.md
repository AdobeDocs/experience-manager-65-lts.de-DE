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
removedfrom6.5.2025: 'yes'
exl-id: 68e43842-cba9-47b8-b7a3-6f625dbfca08
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 100%
---
# Grundlagen der Konfiguration von Formularen {#basics-of-configuring-forms}

Der AEM Forms-Dienst ermöglicht es Ihnen, interaktive Client-Anwendungen zur Datenerfassung zu erstellen, die üblicherweise in Designer erstellte Formulare überprüfen, verarbeiten, transformieren und bereitstellen. Formularautorinnen und -autoren entwickeln einen einzelnen Formularentwurf, den der Forms-Dienst in verschiedenen Formaten rendert:

* als PDF in Adobe Reader oder in einem Browser
* als HTML in verschiedenen Browser-Umgebungen, einschließlich kompatiblem XHTML 1.0-Rendering
* als Formularleitfäden in verschiedenen Browser-Umgebungen, die Adobe Flash Player unterstützen

Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz](https://www.adobe.com/go/learn_aemforms_services_63).

Mithilfe der Forms-Seite in der Administrationskonsole können Sie das Verhalten des Forms-Dienstes konfigurieren. Diese Einstellungen gelten für alle Aufrufe des Dienstes. Alle Parameter, die durch das AEM Forms-SDK gesendet werden, überschreiben die in der Administrationskonsole festgelegten Einstellungen. Sie betreffen jedoch nur diesen bestimmten Aufruf.

Nachdem Sie die Forms-Einstellungen in der Administrationskonsole geändert haben, klicken Sie auf „Speichern“. Der Server muss nicht neu gestartet werden, damit die Änderungen wirksam werden. Sie müssen jedoch ggf. den Forms-Dienst anhalten und neu starten, wenn Sie Cache-Moduseinstellungen konfigurieren. (Siehe [Starten und Stoppen von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
