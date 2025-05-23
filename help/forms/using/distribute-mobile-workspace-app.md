---
title: Bereitstellen der AEM Forms-App
description: Verwenden Sie Mobile Device Management (MDM) für die Bereitstellung von Apps auf Mobilgeräten im großen Stil.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 840dadca-6691-4244-9383-7dbc8e14f0a0
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 100%

---

# Verteilen der AEM Forms-App {#distribute-aem-forms-app}

Mobile Device Management (MDM) ermöglicht die Bereitstellung von Apps auf Mobilgeräten im großen Stil.

>[!NOTE]
>
>Diese Distribution ist nur für iOS- und Android™-Geräte verfügbar.

## Hauptfunktionen, die von MDM-Lösungen bereitgestellt werden: {#main-features-generally-provided-by-mdm-solutions}

* Aktivieren der Geräte-Einschreibung in der Unternehmensumgebung
* Zulassen der Konfiguration und Aktualisierung von Geräte-Einstellungen
* Erzwingen Sie die Sicherheitskompatibilität.
* Sicherer mobiler Zugriff auf Unternehmensressourcen

Mit einer MDM-Lösung sowie Mobile Application Management können Sie interne, öffentliche und erworbene Apps auf allen Mobilgeräten in Ihrem Unternehmen verwalten.

MDM-Admins können sowohl IPA- als auch APK-Dateien auf den MDM-Server hochladen und die Benutzenden steuern, die auf die IPA- oder APK-Dateien zugreifen können. Die Admins können auch die Profileinstellungen für die einzelnen Anwendungen steuern.

## Profileinstellungen mit Auswirkung auf die AEM Forms-App {#profile-settings-affecting-the-aem-forms-app-br}

Die folgenden Profileinstellungen auf Ihrem Gerät haben Auswirkungen auf die Funktion der AEM Forms-App auf Ihrem Gerät:

* **Nutzung der Kamera erlauben** im Abschnitt **Gerätefunktionalität**

Wenn Sie **Verwendung der Kamera erlauben** deaktivieren, funktioniert die Kamerafunktion der [Fotokommentare](/help/forms/using/add-attachments.md) nicht. Aktivieren Sie diese Option, um die Kamera in der App zu verwenden.

* **Passcode auf dem Gerät verlangen** im Abschnitt „Passcode-Richtlinien“

Um die **Verschlüsselung von Anwendungsdaten** zu aktivieren, wird empfohlen, den **Passcode** auf Ihrem Gerät zu aktivieren. Wenn der Passcode auf dem Gerät nicht festgelegt ist, werden die auf dem Gerät gespeicherten Anwendungsdaten nicht verschlüsselt.
