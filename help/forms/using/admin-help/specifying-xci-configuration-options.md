---
title: Angeben der XCI-Konfigurationsoptionen
description: Erfahren Sie, wie Sie die XCI-Konfigurationsoptionen festlegen. Sie können benutzerdefinierte XCI-Dateiwerte für das adaptive Formular angeben, damit sie beim Rendern von Formularen verwendet werden können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 198016d7-0fb5-47e6-91ed-f2f0c98b2224
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 100%

---

# Angeben der XCI-Konfigurationsoptionen {#specifying-xci-configuration-options}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Mit Forms können Sie eine benutzerdefinierte XCI-Datei angeben, die für das Rendern verwendet werden kann. (Siehe [Konfigurieren der Speicherorte für Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).) Forms überschreibt standardmäßig einige der in der XCI-Datei angegebenen Optionen, darunter die folgenden:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Sie können Optionen auswählen, die die Überschreibung für die oben aufgeführten Optionen abbrechen. In diesem Fall verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.

1. Klicken Sie in der Administrationskonsole auf **Dienste** > **Forms**.
1. Aktivieren bzw. deaktivieren Sie das Kontrollkästchen „XCI-Systemstandardoptionen verwenden“. Wenn diese Option aktiviert ist, verwendet Forms seine Standardwerte für die Einstellungen „packets“, „creator“, „producer“ und „compressObjectStream“. Wenn diese Option deaktiviert ist, verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.
1. Klicken Sie auf **Speichern**.
