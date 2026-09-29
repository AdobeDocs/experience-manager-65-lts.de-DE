---
title: Angeben der einzubettenden Schriftarten
description: Erfahren Sie, wie Sie Schriftarten angeben, die in ein adaptives Formular eingebettet werden sollen. Sie können angeben, welche Schriften in Formulare eingebettet oder nie eingebettet werden sollen, die vom Forms-Dienst erstellt werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 374f9425-b596-4481-8fd0-6df07c521a19
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
source-wordcount: '283'
ht-degree: 100%
---
# Angeben der einzubettenden Schriftarten{#specify-fonts-to-embed}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Sie können angeben, welche Schriftarten immer oder nie in Formulare eingebettet werden sollen, die von der Ausgabe verwendet werden. Das Einbetten von Schriften erhöht die Dateigröße von Formularen. Betten Sie ungewöhnliche Schriftarten ein, die Benutzende eher selten installiert haben, während gängige Schriften, die vermutlich installiert sind, nicht eingebettet werden sollten.

>[!NOTE]
>
>Wenn Sie eine benutzerdefinierte XCI-Datei für Output angegeben haben, setzt die Option „Schrift einbetten“ in der XCI-Datei diese Einstellungen außer Kraft. (Siehe [Angeben von Dateispeicherorten für die Ausgabe](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Ausgabe“.
1. Geben Sie unter „Schrifteinbettungseinstellungen“ in das Feld „Schriftarten immer einbetten“ die Namen der Schriftarten (durch Kommas getrennt) ein, die in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriftarten werden nur dann in dem erzeugten Formular eingebettet, wenn sie in dem Formular verwendet werden. Diese Einstellung wird ignoriert, wenn die Option „Schrift einbetten“ in der XCI-Datei, die an den Dienst übermittelt wird, aktiviert ist. In diesem Fall werden alle Schriftarten, die in der PDF-Datei verwendet werden, immer eingebettet.
1. Geben Sie in das Feld „Schriften nie einbetten“ die Namen der Schriftarten (durch Kommas getrennt) ein, die nicht in Formulare eingebettet werden sollen. Die hier von Ihnen angegebenen Schriftarten werden nicht in der PDF-Datei eingebettet, selbst wenn sie in der generierten PDF-Datei verwendet werden. Diese Einstellung wird ignoriert, wenn die Option „Schriftart einbetten“ in der XCI-Datei, die an den Dienst übermittelt wird, deaktiviert ist. In diesem Fall wird keine der Schriftarten, die in der PDF-Datei verwendet werden, eingebettet.
1. Klicken Sie auf Speichern.
