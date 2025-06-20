---
title: Einrichten von IMS-Integrationen für AEM
description: Erfahren Sie, wie Sie IMS-Integrationen für AEM einrichten.
feature: Security
role: Admin
exl-id: 05ba39fc-4b53-43c0-9a9f-7da3293b1ca2
source-git-commit: 929a2175449a371ecf81226fedb98a0c5c6d7166
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 95%

---

# Einrichten von IMS-Integrationen für AEM {#setting-up-ims-integrations-for-aem}


>[!NOTE]
>
>Mit der [Adobe Developer Console](https://developer.adobe.com/console) können Kundinnen und Kunden von Adobe Anmeldedaten generieren, die den Zugriff auf verschiedene APIs ermöglichen. Dabei können sie unter verschiedenen Anmeldedatentypen wählen, von OAuth Server-zu-Server bis zu Single-Page-App. Der Berechtigungstyp Dienstkonto (JWT) wird jetzt zugunsten der OAuth Server-zu-Server-Anmeldeinformationen nicht mehr unterstützt.

Adobe Experience Manager (AEM) kann mit vielen anderen Adobe-Lösungen integriert werden. Zum Beispiel Adobe Target, Adobe Analytics und vielen weiteren.

Die Integrationen verwenden eine IMS-Integration, die mit S2S OAuth konfiguriert ist.

* Nach der Erstellung von:

   * [Anmeldedaten in der Developer Console](#credentials-in-the-developer-console)

* Anschließend können Sie:

   * Eine (neue) [OAuth-Konfiguration](#creating-oauth-configuration) erstellen

   * [Eine vorhandene JWT-Konfiguration in eine OAuth-Konfiguration migrieren](#migrating-existing-JWT-configuration-to-oauth)

>[!CAUTION]
>
>Zuvor wurden Konfigurationen mit [JWT-Anmeldedaten erstellt, die in der Adobe Developer Console nicht mehr unterstützt werden](/help/sites-administering/jwt-credentials-deprecation-in-adobe-developer-console.md).
>
>Solche Konfigurationen können nicht mehr erstellt oder aktualisiert werden, können aber zu OAuth-Konfigurationen migriert werden.

## Anmeldedaten in der Developer Console {#credentials-in-the-developer-console}

Als ersten Schritt müssen Sie die OAuth-Anmeldedaten in der Adobe Developer Console konfigurieren.

Weitere Informationen zu dieser Konfiguration finden Sie in der Dokumentation zur Developer Console, abhängig von Ihren Anforderungen:

* Übersicht:

   * [Server-zu-Server-Authentifizierung](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

* Erstellen von neuen OAuth-Anmeldedaten:

   * [OAuth-Implementierungshandbuch für Server-zu-Server-Anmeldedaten](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)

* Migration von vorhandenen JWT-Anmeldedaten zu OAuth-Anmeldedaten:

   * [Migration von JWT-Anmeldedaten (Service Account) zu OAuth-Server-zu-Server-Anmeldedaten](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration?lang=de)

Zum Beispiel:

![OAuth-Anmeldedaten in der Developer Console](assets/ims-configuration-developer-console.png)

## Erstellen einer OAuth-Konfiguration {#creating-oauth-configuration}

So erstellen Sie eine neue Adobe IMS-Integration mithilfe von OAuth:

1. Navigieren Sie in AEM zu **Tools** > **Sicherheit** > **Adobe IMS-Integration**.

1. Wählen Sie **Erstellen** aus.

1. Schließen Sie die Konfiguration basierend auf Details aus der [Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) ab. Zum Beispiel:

   ![Erstellen einer OAuth-Konfiguration](assets/ims-create-oauth-configuration.png)

1. **Speichern** Sie Ihre Änderungen.

## Migration einer vorhandenen JWT-Konfiguration zu einer OAuth-Konfiguration {#migrating-existing-JWT-configuration-to-oauth}

So migrieren Sie eine vorhandene Adobe IMS-Integration basierend auf JWT-Anmeldedaten:

>[!NOTE]
>
>Dieses Beispiel zeigt eine IMS-Konfiguration für Launch.

1. Navigieren Sie in AEM zu **Tools** > **Sicherheit** > **Adobe IMS-Integration**.

1. Wählen Sie die zu migrierende JWT-Konfiguration aus. JWT-Konfigurationen sind mit einer Warnung gekennzeichnet: **JWT-Anmeldedaten (nicht mehr unterstützt)**.

1. Wählen Sie **Eigenschaften** aus.

   ![Auswählen der JWT-Konfiguration](assets/ims-migrate-jwt-select-configuration.png)

1. Die Konfiguration wird als schreibgeschützt geöffnet:

   ![Konfigurationseigenschaften – Schreibgeschützt](assets/ims-migrate-jwt-properties-read-only.png)

1. Wählen Sie **OAuth** aus der Dropdown-Liste **Authentifizierungstyp** aus:

   ![Auswählen des Authentifizierungstyps](assets/ims-migrate-jwt-authentication-type.png)

1. Die verfügbaren Eigenschaften werden aktualisiert. Verwenden Sie Details aus der Developer Console, um sie zu vervollständigen:

   ![Vervollständigen von OAuth-Details](assets/ims-migrate-jwt-complete-oauth-details.png)

1. Verwenden Sie **Speichern und schließen**, um Ihre Aktualisierungen beizubehalten.
Wenn Sie zur Konsole zurückkehren, ist die Warnung **JWT-Anmeldedaten (nicht mehr unterstützt)** verschwunden.
