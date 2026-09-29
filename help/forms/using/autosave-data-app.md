---
title: Verwenden der automatischen Speicherung in der AEM Forms-App
description: Erfahren Sie, wie Sie in der AEM Forms-App die automatische Speicherung verwenden, mit der Sie Datenverlust vermeiden können.
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 8f504453-1009-46d9-83a5-d4a8531d7e2c
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
source-wordcount: '295'
ht-degree: 90%
---
# Verwenden der automatischen Speicherung in der AEM Forms-App{#using-autosave-in-aem-forms-app}

Wenn Sie Daten in die Adobe Experience Manager Forms-App eingeben, speichert die Funktion sie automatisch in regelmäßigen Abständen. Die automatische Speicherung in der AEM Forms-App hilft Ihnen, Datenverlust zu vermeiden, wenn die App versehentlich geschlossen wird.

Ihre App kann versehentlich geschlossen werden:

* Wenn sich Ihr Gerät aufgrund eines niedrigen Akkustands ausschaltet.
* Wenn der Benutzer die App abbricht
* Wenn es zu einem unerwarteten Absturz kommt.

Sie können die Intervalle angeben, in denen die App die eingegebenen Daten speichert.

>[!NOTE]
>
>Wählen Sie den Wert sorgfältig aus. Eine häufige automatische Speicherung kann spürbare Auswirkungen auf die Leistung Ihres Geräts haben.

Führen Sie die folgenden Schritte aus, um die automatische Speicherung in der AEM Forms-App zu verwenden:

1. Melden Sie sich bei der App an und navigieren Sie zu **Einstellungen > Allgemein**.
1. Verwenden Sie im Bildschirm „General“ die Option **Autosave Frequency**, um die Intervalle auszuwählen, in denen das Programm die eingegebenen Daten speichern soll.
   [![Einstellen der Häufigkeit der automatischen Speicherung](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Wenn Sie die App neu starten und sich als derselbe Benutzer anmelden, werden Sie aufgefordert, Ihre Aufgabe mit dem Dialogfeld „Nicht gespeicherte Aufgabe wiederherstellen“ wiederherzustellen. Klicken Sie in diesem Dialogfeld auf **OK**, um die Arbeit an der gespeicherten Aufgabe fortzusetzen. Klicken Sie auf **Abbrechen**, um die gespeicherten Daten entsprechend der zuletzt ausgelösten automatischen Speicherung zu löschen und an einer neuen Aufgabe zu arbeiten.

   Wenn Sie auf **OK** klicken, wird die Aufgabe mit den Daten entsprechend der zuletzt ausgelösten automatischen Speicherung vor Absturz der App wiederhergestellt. Sie enthält die Formulardaten und alle Anlagen, die mit der Aufgabe verbunden sind.
   [![Wiederherstellen einer Aufgabe &#x200B;](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**a.** Ein Formular mit laufenden Arbeiten (**.**-Programm wurde erzwungen geschlossen **C.**-Programm wurde mit dem Dialogfeld „Nicht gespeicherte Aufgabe wiederherstellen“ neu gestartet **D.** Formular wurde mit Originaldaten wiederhergestellt
