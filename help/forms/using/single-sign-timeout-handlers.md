---
title: Single Sign-On und Zeitüberschreitungs-Handler
description: Gehen Sie wie folgt vor, um einen Sitzungs-Zeitüberschreitungswert für AEM Forms Workspace festzulegen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: c6bdfa6f-0d9b-4473-a2e1-6cad73fbd1ed
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 100%

---

# Single Sign-On und Zeitüberschreitungs-Handler {#single-sign-on-and-timeout-handlers}

AEM Forms Workspace ist SSO-fähig. Wenn Sie sich bei einer AEM Forms-Anwendung wie Forms Manager oder der PDF Generator-Benutzeroberfläche angemeldet haben und in derselben Browser-Sitzung auf AEM Forms Workspace zugreifen, werden Sie bei AEM Forms Workspace angemeldet und umgekehrt.

## Die Handhabung der Server-Zeitüberschreitung in AEM Forms Workspace {#handling-server-timeout-in-nbsp-aem-forms-workspace}

Sitzungs-Zeitüberschreitungen für Benutzende können in der Administrationskonsole konfiguriert werden.

Um den Timeout festzulegen, melden Sie sich bei `https://'[server]:[port]'/adminui` an, navigieren zu **Einstellungen > Benutzerverwaltung > Konfiguration > Erweiterte Systemattribute konfigurieren** und nehmen die gewünschten Einstellungen vor.

In AEM Forms wird die Zeitüberschreitung im Arbeitsbereich wie folgt behandelt:

* Die Sitzungsdauer für einen Benutzer ist in der Antwort auf den Aufruf `initialize` verfügbar, der die Benutzersitzung initialisiert.
* Ein Popup-Dialogfeld informiert Benutzende 15 Sekunden im Voraus, dass die Sitzung gleich ablaufen wird.

In diesem Popup-Dialogfeld:

* Klicken Sie auf „OK“, um die Benutzersitzung zu beenden.
* Klicken Sie auf „Abbrechen“, um die Benutzersitzung neu zu initialisieren.

>[!NOTE]
>
>Wird keine Aktion ausgeführt, wird der Benutzer drei Sekunden vor Ablauf der Sitzung automatisch vom AEM Forms-Arbeitsbereich abgemeldet.
