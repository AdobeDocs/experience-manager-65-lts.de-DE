---
title: Überprüfen der Informationen zur Verwendung von Anmeldedaten
description: Erfahren Sie, wie Sie die Informationen zur Verwendung von Anmeldedaten überprüfen. Auf die Informationen zur Verwendung von Anmeldedaten, die ihre Verwendung beschreiben, kann über die Acrobat Reader-Erweiterung zugegriffen werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 5cc5c9fe-50ce-4863-bfa4-a009a6c3b06f
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 100%

---

# Überprüfen der Informationen zur Verwendung von Anmeldedaten {#review-credential-use-information}

Die Anmeldedaten enthalten Informationen zur Beschreibung der vorgesehenen Verwendung, auf die über die Acrobat Reader DC-Erweiterungen-Web-Anwendung für Endbenutzende zugegriffen werden kann. Anhand dieser Informationen können Sie den Typ der installierten Anmeldedaten (entweder Test oder Produktion) und die Gültigkeitsdauer bestimmen.

1. Öffnen Sie einen Webbrowser und geben Sie diese URL ein:

   http://localhost:port/ReaderExtensions (wobei *port* die Port-Nummer Ihres Programm-Servers ist)

1. Melden Sie sich mit dem standardmäßigen Benutzernamen und Kennwort an:

   Benutzername: administrator

   Kennwort: password

   >[!NOTE]
   >
   >Sie benötigen Administrator- oder Hauptbenutzer-Berechtigungen, um sich mit dem standardmäßigen Benutzernamen und Kennwort anmelden zu können. Um anderen Benutzenden den Zugriff auf Acrobat Reader DC-Erweiterungen zu erlauben, erstellen Sie die Benutzerkonten in User Management und weisen Sie ihnen die Rolle „Acrobat Reader DC-Erweiterungen-Web-Anwendung“ zu.

1. Wählen Sie den Anmeldedaten-Alias in der Liste „Anmeldedaten auswählen“ aus und überprüfen Sie die Informationen in den Feldern „Ablaufdatum“ und „Hinweis zur bestimmungsgemäßen Verwendung“.

>[!NOTE]
>
>Das Ablaufdatum der Anmeldedaten finden Sie auch in der Administrationskonsole auf der Seite „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Anmeldedaten“ unter „Ablaufdatum“.
