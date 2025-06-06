---
title: Konfigurieren von Connector for IBM® Content Manager
description: Konfigurieren Sie Connector for IBM® Content Manager, um die Kommunikation zwischen AEM Forms und IBM® Content Manager zu aktivieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
hide: true
hidefromtoc: true
exl-id: 106f01a2-39fb-474b-8c58-5ab08666b918
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 100%

---

# Konfigurieren von Connector for IBM® Content Manager{#configuring-connector-for-ibm-content-manager}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Connector for IBM® Content Manager ermöglicht die Kommunikation zwischen AEM Forms und IBM® Content Manager. Weitere Hintergrundinformationen finden Sie unter „Connectors for ECM“ in der [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

## Konfigurieren der Verbindung mit IBM® Content Manager {#configure-the-ibm-content-manager-connection}

1. Wählen Sie in der Administrationskonsole „Dienste“ > „Connector for IBM® Content Manager“ aus.
1. Geben Sie in das Feld „Datenspeichername“ den Namen des IBM® Content Manager-Datenspeichers ein, mit dem eine Verbindung hergestellt werden soll. Wenn es sich um eine lokale Datenbank handelt, geben Sie den Namen der Datenbank ein. Wenn es sich um eine Remote-Datenbank handelt, geben Sie deren Aliasnamen ein.
1. Geben Sie in das Feld „Benutzername“ die Benutzer-ID der Person ein, die mit dem IBM® Content Manager-Datenspeicher eine Verbindung herstellen können soll.
1. Geben Sie in das Feld „Kennwort“ das Kennwort der Benutzerin bzw. des Benutzers ein.
1. (Optional) Geben Sie in das Feld „Alias-Verbindungszeichenfolge“ zusätzliche Verbindungsargumente ein. Normalerweise sollte dieses Feld leer sein. Weitere Informationen finden Sie in der IBM®-Dokumentation.
1. Klicken Sie auf Speichern.

## Validierung der Diensteinstellungen {#validation-of-service-settings}

Wenn Sie einen falschen Aliasnamen für den Datenspeicher, einen falschen Benutzernamen oder ein falsches Kennwort eingeben, erhalten Sie in Abhängigkeit davon, ob der Content-Repository-Dienst für Connector for IBM® Content Manager ausgeführt wird, folgende Ergebnisse:

* Wenn der Dienst beim Speichern der Dienstkonfigurationsinformationen beendet ist, tritt kein Fehler auf. Beim nächsten Start des Dienstes wird jedoch eine Ausnahme ausgelöst und der Dienst startet nicht.
* Wenn der Dienst beim Speichern der Dienstkonfigurationsinformationen gestartet ist, versucht der Dienst sofort, die Anmeldeinformationen zu überprüfen. In diesem Fall tritt ein Fehler auf und die Konfigurationsinformationen werden nicht gespeichert.
