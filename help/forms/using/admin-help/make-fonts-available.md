---
title: Bereitstellen von Schriften
description: Stellen Sie sicher, dass die in einem Formular verwendeten Schriften für den J2EE-Anwendungs-Server zur Verfügung stehen, der als Host für AEM Forms dient.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: eded255b54ff83f60f73cece8824c778d3a87680
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 100%

---

# Bereitstellen von Schriften {#make-fonts-available}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Stellen Sie sicher, dass die in einem Formular verwendeten Schriften für den J2EE-Anwendungs-Server zur Verfügung stehen, der als Host für AEM Forms dient. Betrachten Sie beispielsweise das folgende Szenario. Eine Formularentwicklerin oder ein Formularentwickler fügt dem Schriftartenverzeichnis, das von Designer verwendet wird, eine Schrift hinzu und erstellt ein Formular, das diese Schrift verwendet, auf einem separaten Computer. Damit der Ausgabe-Service diese Schrift verwenden kann, legen Sie sie im Verzeichnis für Kundenschriftarten ab. Wenn das Verzeichnis für Kundenschriftarten nicht vorhanden ist, erstellen Sie ein entsprechendes Verzeichnis auf dem J2EE-Anwendungs-Server, der als Host für AEM Forms dient.

Weitere Informationen zu Schrifteinstellungen finden Sie unter [Konfigurieren allgemeiner AEM Forms-Einstellungen](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).

**Angeben des Speicherorts des Verzeichnisses für Kundenschriftarten**

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“.
1. Geben Sie im Feld „Speicherort des Verzeichnisses für Systemschriftarten“ den Pfad für das Verzeichnis für Kundenschriftarten an. Mehrere Ordner können hinzugefügt werden, indem sie durch ein Semikolon **;** voneinander getrennt werden.
1. Klicken Sie auf OK.
1. Starten Sie das System neu, auf dem AEM Forms installiert ist.

>[!NOTE]
>
>Schriften werden aus dem Schriftarten-Cache des Windows-Systems ausgewählt, und ein Neustart des Systems ist erforderlich, um den Cache zu aktualisieren. Nachdem Sie das Verzeichnis für Kundenschriftarten angegeben haben, müssen Sie das System neu starten, auf dem AEM Forms installiert ist.
