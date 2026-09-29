---
title: Aktivieren des Funktionsumschalters, um Early-Adopter- und Vorabversionsfunktionen zu integrieren
description: Der Funktionsumschalter ist eine Funktion in AEM, mit der Admins neue Funktionen in einer Laufzeitumgebung aktivieren können.
feature: Adaptive Forms, Foundation Components
role: User, Developer
exl-id: 8b6dea41-540b-498a-b52b-e584a9255f25
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: ae206583-dab1-444b-b978-a37aad4a988c
    internal-label: Experience Manager 6.5 LTS
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 100%
---
# Umschalten zwischen Funktionen in Adobe Experience Manager (AEM) 6.5{#enable-feature-toggle-aem-forms-65}

Der Funktionsumschalter ist eine Funktion in AEM, mit der Admins bestimmte Funktionen dynamisch aktivieren oder deaktivieren können. Diese Funktion ist besonders nützlich für die Verwaltung von **Early-Adopter**- und **Vorabversionsfunktionen** ohne größere Bereitstellungen oder Änderungen an der Code-Basis. Sie gewährleistet Flexibilität und Kontrolle darüber, auf welche Funktionen in einer AEM-Umgebung zugegriffen werden kann.

## Funktionsumschalter aktivieren {#enable-feature-toggle-65}

Funktionsumschalter für Early Adopters oder neue Funktionen können über die **AEM-Web-Konsole** konfiguriert werden, indem Sie die folgenden Schritte ausführen:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.
2. Navigieren Sie zu `http://<author-instance-url>:portnumber/system/console/configMgr`.
3. Suchen Sie im Konfigurations-Manager nach **Adobe Granite Dynamic Toggle Provider**.
4. Klicken Sie auf das Symbol ![Bleistiftsymbol](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. Klicken Sie im Abschnitt [!UICONTROL Aktivierte Umschalter] auf das ![Bleistiftsymbol](assets/aem6forms_add.png).
6. Fügen Sie die Funktionsumschalter-ID für die Funktion hinzu, wie in der Abbildung unten dargestellt.
   ![Umschalter hinzufügen](assets/add_toggle_number_forms.png)

   >[!NOTE]
   >
   >Die Funktionsumschalter-ID finden Sie im dedizierten Dokument für die Early-Adopter-Funktionen.

7. Klicken Sie auf „Speichern“.

## Deaktivieren des Funktionsumschalters {#disable-feature-toggle-65}

Gehen Sie wie folgt vor, um die Funktionsumschalter für Funktionen zu deaktivieren, deren Umschalter aktiviert sind:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.
2. Navigieren Sie zu `http://<author-instance-url>:portnumber/system/console/configMgr`.
3. Suchen Sie im Konfigurations-Manager nach **Adobe Granite Dynamic Toggle Provider**.
4. Klicken Sie auf das Symbol ![Bleistiftsymbol](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. Klicken Sie im Abschnitt [!UICONTROL Deaktivierte Umschalter] auf das ![Bleistiftsymbol](assets/aem6forms_add.png).
6. Fügen Sie die Umschalternummer für die zu deaktivierende Funktion hinzu.
   ![Umschalter entfernen](assets/remove_toggle_feature_forms.png)
7. Klicken Sie auf „Speichern“.

## Technische Überlegung

Funktionsumschalter sind umgebungsspezifisch und werden zur Laufzeit verwaltet, sodass kein Neustart des Servers erforderlich ist. Bei einigen Funktionen ist es jedoch möglicherweise erforderlich, die relevanten Seiten zu aktualisieren oder den Cache zu löschen, um Änderungen widerzuspiegeln.
Sie können über `http://<author-instance-url>:4502/etc.clientlibs/toggles.json` auf die Liste der Funktionen zugreifen, die über den Funktionsumschalter für Ihre Umgebung aktiviert sind.
