---
title: Angeben von XCI-Konfigurationsoptionen
description: Erfahren Sie, wie Sie die XCI-Konfigurationsoptionen festlegen. Sie können benutzerdefinierte XCI-Dateiwerte für das adaptive Formular angeben, damit sie beim Rendern von Formularen verwendet werden können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 5fb6e6cc-6af7-4cf5-804b-bb3030079383
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
source-wordcount: '161'
ht-degree: 100%
---
# Angeben von XCI-Konfigurationsoptionen {#specify-xci-configuration-options}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Mit Output können Sie eine benutzerdefinierte XCI-Datei angeben, die zum Rendern verwendet wird. Siehe [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).

Standardmäßig überschreibt Output einige der in der XCI-Datei angegebenen Optionen, darunter die folgenden:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Sie können Optionen auswählen, die die Überschreibung für die oben aufgeführten Optionen abbrechen. In diesem Fall verwendet Output die in der benutzerdefinierten XCI-Datei angegebenen Werte.

1. Klicken Sie in Administration-Console auf **Dienste > Ausgabe**.
1. Aktivieren bzw. deaktivieren Sie das Kontrollkästchen „XCI-Systemstandardoptionen verwenden“. Wenn diese Option aktiviert ist, verwendet Output seine Standardwerte für die Einstellungen „packet“, „creator“, „manufacturer“und „compressObjectStream“. Wenn diese Option deaktiviert ist, verwendet Output die in der benutzerdefinierten XCI-Datei angegebenen Werte.
1. Klicken Sie auf **Speichern**.
