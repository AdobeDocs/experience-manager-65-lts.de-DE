---
title: Bereinigen von Prozessdaten
description: Prozessdaten, die beim Aufrufen eines Prozesses mit langer Lebensdauer generiert werden, können zu stark anwachsen, was zu einer Beeinträchtigung der Leistung von AEM Forms und zur unnötigen Belegung von Speicherplatz führt. Erfahren Sie, wie Sie Prozessdaten bereinigen können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 53ce63a3-704a-4da6-b652-362a436f05a7
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
source-wordcount: '207'
ht-degree: 100%
---
# Bereinigen von Prozessdaten {#purging-process-data}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Prozessdaten, die beim Aufrufen eines Prozesses mit langer Lebensdauer generiert werden, können zu stark anwachsen, was zu einer Beeinträchtigung der Leistung von AEM Forms und zur unnötigen Belegung von Speicherplatz führt. Es ist empfehlenswert, Prozessdaten zu bereinigen, wenn die Einträge nicht mehr benötigt werden. AEM Forms bietet mehrere Möglichkeiten, Prozessdaten zu bereinigen:

* Sie können die Administrationskonsole verwenden, um eine einmalige Bereinigung von veralteten Einträgen im Zusammenhang mit dauerhaft genutzten Prozessen auszuführen oder regelmäßige automatische Bereinigungen zu planen. (Weitere Informationen finden Sie unter [Bereinigen von Einträgen in der Job Manager-Datenbank](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).)
* Sie können die AEM Forms Java-API und die Webservice-API verwenden, um Prozessdaten im Zusammenhang mit dauerhaft genutzten Prozessen programmgesteuert zu bereinigen. (Siehe „Bereinigen von Prozessdaten“ in [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).)
* Verwenden Sie das Prozessbereinigungswerkzeug zum Bereinigen von Prozessen anhand des Prozessnamens und anderer Parameter. Weitere Informationen finden Sie in der Datei „Bitte lesen“ zum Prozessbereinigungswerkzeug, die sich unter „*[aem_forms root]*\sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt“ befindet.
