---
title: Konfigurieren der Überprüfungsmeldungen
description: Erfahren Sie, wie Sie angeben können, wie die Validierungsnachrichten und deren Position relativ zum im Webbrowser zurückgegebenen Formular angezeigt werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 1172f1f2-b297-4021-a9ee-507b0a4e628a
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 100%

---

# Konfigurieren der Überprüfungsmeldungen {#configuring-validation-messages}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Für als HTML gerenderte Formulare werden den Benutzenden Formular-Validierungsfehler angezeigt. Sie können die Darstellung von Validierungsmeldungen anpassen. In Abhängigkeit davon, wo die Validierungsmeldungen angezeigt werden, können Sie auch die Position der Meldung im Formular sowie die Rahmenstärke steuern.

## Angeben, wie Validierungsmeldungen angezeigt werden {#specify-how-validation-messages-are-displayed}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Forms“.
1. Wählen Sie in der Liste „Berichte“ unter „Validierungsausgabe“ eine der folgenden Optionen aus:

   **Meldungsfeld**, um Validierungsmeldungen in einem gesonderten Dialogfeld anzuzeigen.

   **Rahmen**, um Validierungsmeldungen in einem Rahmen desselben Fensters anzuzeigen.

   **Kein Rahmen**, um Validierungsmeldungen im selben Fenster anzuzeigen. Dies ist der Standardwert.

   **Per API (mit Daten)**, um die Validierungsmeldungen über die API zurückzugeben (mit Daten). Die Validierungsmeldungen werden nicht auf dem Bildschirm angezeigt.

   **Per API (mit Formular)**, um die Validierungsmeldungen über die API zurückzugeben (mit dem Formular). Die Validierungsmeldungen werden nicht auf dem Bildschirm angezeigt.

   **Ohne**, um keine Validierungsmeldungen anzuzeigen.

1. Klicken Sie auf Speichern.

## Angeben der Position der Validierungsmeldungen relativ zum im Webbrowser zurückgegebenen Formular {#specify-the-location-of-validation-messages-relative-to-the-form-returned-in-the-web-browser}

Wenn „Berichte“ auf „Rahmen“ oder „Kein Rahmen“ festgelegt ist, können Sie die Position der Validierungsmeldungen angeben.

1. Wählen Sie unter „Validierungsausgabe“ in der Liste „Position“ eine der folgenden Optionen aus:

   **Links:**, um Validierungsmeldungen in der linken Hälfte des Webbrowsers anzuzeigen.

   **Rechts:**, um Validierungsmeldungen in der rechten Hälfte des Webbrowsers anzuzeigen.

   **Oben**, um Validierungsmeldungen oben im Webbrowser anzuzeigen. Dies ist der Standardwert.

   **Unten**, um Validierungsmeldungen unten im Webbrowser anzuzeigen.

1. Klicken Sie auf Speichern.

## Festlegen der Rahmenstärke {#specify-the-frame-border-size}

Wenn „Berichte“ auf „Rahmen“ festgelegt ist, können Sie die Rahmenstärke angeben.

1. Geben Sie unter „Validierungsausgabe“ im Feld „Rahmenstärke“ die Stärke des Rahmens in Pixel ein.

   Die Rahmenstärke muss gleich oder größer als 0 sein. Der Standardwert ist 1.

1. Klicken Sie auf Speichern.
