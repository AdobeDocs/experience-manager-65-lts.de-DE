---
title: Konfigurieren der Acrobat Reader DC-Erweiterungen für die Datenerfassung
description: Erfahren Sie, wie Sie die Acrobat Reader DC-Erweiterungen für die Datenerfassung konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Document Services,Reader Extensions
exl-id: f9b01de7-1de5-43aa-bcc3-b15719bfa5c0
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 100%

---

# Konfigurieren der Acrobat Reader DC-Erweiterungen für die Datenerfassung {#configuring-acrobat-reader-dc-extensions-for-data-capture}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Wenn Benutzende Ihrer AEM Forms-Installation die Datenerfassungsfunktion von Content Services (nicht mehr unterstützt) verwenden, wird empfohlen, eine Rolle mit schreibgeschütztem Zugriff für diese Benutzenden zu erstellen.

***Hinweis **: Adobe® LiveCycle® Content Services ES (nicht mehr unterstützt) ist ein Content-Management-System, das mit LiveCycle installiert wird. Es ermöglicht Benutzenden, am Menschen orientierte Prozesse zu entwerfen, zu verwalten, zu überwachen und zu optimieren. Die Unterstützung von Content Services (veraltet) endet am 31.12.2014. Weitere Informationen finden Sie unter [Adobe Produkt-Lifecycle-Dokument](https://helpx.adobe.com/de/support/programs/eol-matrix.html).*

Für die Datenerfassung ist es erforderlich, dass eine Benutzerrolle für den Zugriff auf „SampleReaderExtensionsCredential“ zugewiesen wird. Sie können die standardmäßige Vertrauensadmin-Rolle zuweisen. Beachten Sie jedoch, dass diese Rolle allgemeinen, nicht administrativen Benutzenden Administratorberechtigungen gewährt, mit denen die PKI-Vertrauenseinstellungen gesteuert und PKI-Berechtigungen verwaltet werden, wodurch die Sicherheit Ihrer AEM Forms-Installation in einer Produktionsumgebung gefährdet werden kann. AEM Forms-Systemadmins sollten eine Rolle erstellen, die nur schreibgeschützten Zugriff auf den Trust Store gewährt, und diese neue Rolle nicht administrativen Benutzenden zuweisen, die die Datenerfassungsfunktion verwenden.

## Erstellen einer Rolle für Benutzende der Datenerfassungsfunktion {#create-a-role-for-data-capture-users}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Rollenverwaltung“ und dann auf „Neue Rolle“.
1. Geben Sie in den entsprechenden Feldern den Rollennamen (z. B. „Datenerfassungsbenutzer“) und eine Beschreibung ein und klicken Sie dann auf „Weiter“.
1. Klicken Sie im Bildschirm „Rollenberechtigungen“ auf „Berechtigungen suchen“ und wählen Sie dann die Leseberechtigung aus der Liste verfügbarer Berechtigungen aus.
1. Klicken Sie auf „OK“ und dann auf „Beenden“.

## Zuweisen der Datenerfassungsrolle {#assign-the-data-capture-role}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Rollenverwaltung“ und dann auf „Suchen“.
1. Klicken Sie auf die von Ihnen erstellte Datenerfassungsbenutzerrolle.
1. Klicken Sie auf der Registerkarte „Rollenbenutzer/-gruppen“ auf „Benutzer/Gruppen suchen“.
1. Klicken Sie im Bildschirm „Benutzer und Gruppen suchen“ auf „Suchen“, wählen Sie die Benutzenden aus, die die Datenerfassungsbenutzerrolle benötigen, und klicken Sie auf „OK“.
1. Klicken Sie im Bildschirm „Rolle bearbeiten“ auf „Speichern“.
