---
title: Bearbeiten und Konvertieren bestehender Domains
description: Erfahren Sie, wie Sie auf der Seite „Domain-Verwaltung“ die Einstellungen für bestehende Domains ändern. Konvertieren Sie eine bestehende Unternehmens-Domain in eine Hybrid-Domain oder umgekehrt.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 0dafef83-a516-48df-9175-019984843cfa
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 100%

---

# Bearbeiten und Konvertieren bestehender Domains{#editing-and-converting-existing-domains}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Sie können auf der Seite „Domain-Verwaltung“ die Einstellungen für bestehende Domains ändern. Sie können auch eine bestehende Unternehmens-Domain in eine Hybrid-Domain umwandeln.

## Eine vorhandene Domain bearbeiten {#edit-an-existing-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Klicken Sie auf den Namen der Domain, die bearbeitet werden soll.
1. Um den Domain-Namen zu ändern, bearbeiten Sie den Text im Feld „Name“.
1. Um die Authentifizierungsinformationen für eine Unternehmens- oder Hybrid-Domain zu ändern, klicken Sie auf den entsprechenden Authentifizierungsnamen am unteren Rand der Seite. Auf der Seite „Authentifizierung bearbeiten“ können Sie die Einstellungen nach Bedarf ändern. (Siehe [Authentifizierungseinstellungen](/help/forms/using/admin-help/configuring-authentication-providers.md#authentication-settings)).
1. Um die Ordnerinformationen für eine Unternehmens-Domain zu ändern, klicken Sie auf den entsprechenden Ordnernamen am unteren Rand der Seite. Auf der Seite „Verzeichnis bearbeiten“ können Sie die Einstellungen nach Bedarf ändern. (Siehe [Hinzufügen von Verzeichnissen oder benutzerdefinierten SPIs](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis)).
1. Wenn Sie Ihre Änderungen abgeschlossen haben, klicken Sie auf „OK“.

## Konvertieren einer Unternehmens-Domain in eine Hybrid-Domain {#convert-an-enterprise-domain-to-a-hybrid-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Klicken Sie auf den Namen der Unternehmens-Domain, die umgewandelt werden soll.
1. Klicken Sie auf „In Hybrid-Domain konvertieren“.
1. Überprüfen Sie die angezeigten Informationen zu Benutzer- und Gruppendaten sowie zur Authentifizierung von Benutzenden und klicken Sie auf „OK“.
1. Bearbeiten Sie die Einstellungen der Hybrid-Domain und klicken Sie auf „OK“.

>[!NOTE]
>
>Wenn die Unternehmens-Domain, die Sie konvertieren, keine Ordnereinstellungen enthält, gehen alle LDAP-Authentifizierungseinstellungen verloren.

## Eine Hybrid-Domain in eine Unternehmens-Domain umwandeln {#convert-a-hybrid-domain-to-an-enterprise-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Klicken Sie auf den Namen der Hybrid-Domain, die umgewandelt werden soll.
1. Klicken Sie auf „In Unternehmens-Domain konvertieren“.
1. Überprüfen Sie die angezeigten Informationen zu Benutzer- und Gruppendaten sowie zur Authentifizierung von Benutzenden und klicken Sie auf „OK“.
1. Klicken Sie auf „Verzeichnis hinzufügen“ und konfigurieren Sie die erforderlichen Verzeichnisdaten. (Siehe [Hinzufügen von Verzeichnissen oder benutzerdefinierten SPIs](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis))
