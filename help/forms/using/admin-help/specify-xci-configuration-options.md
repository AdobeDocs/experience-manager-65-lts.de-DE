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
hidefromtoc: true
exl-id: 5fb6e6cc-6af7-4cf5-804b-bb3030079383
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
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
