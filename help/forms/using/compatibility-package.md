---
title: Kompatibilitätspaket
description: Durch die Installation des Kompatibilitätspakets auf AEM Forms 6.5 LTS können Sie Correspondence Management-Assets aus AEM Forms 6.5 und früheren Versionen sowie veraltete Vorlagen und Seiten für adaptive Formulare verwenden
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: 3a529a82-e2fd-423c-96c1-a5accc87775e
source-git-commit: 2e0cbe62754866d31de69547f9af1f2f63930f2c
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 54%

---

# Kompatibilitätspaket{#compatibility-package}

## Übersicht {#overview}

Interaktive Kommunikation ist der standardmäßige und empfohlene Ansatz zum Erstellen von Kundenkommunikation in AEM Forms 6.5 LTS. Um Briefe in AEM Forms 6.5 LTS weiterhin verwenden zu können, müssen Sie das neueste AEMFD[Kompatibilitätspaket &#x200B;](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).

Mit dem AEMFD-Kompatibilitätspaket können [&#x200B; auch die folgenden Assets aus AEM Forms 6.5.22.0, 6.4, 6.3 und 6.2 für AEM Forms 6.5 LTS verwenden](../../forms/using/compatibility-package.md#add-support-for-aem-forms-and-assets-in-aem-forms)

* Dokumentfragmente
* Briefe
* Datenwörterbücher
* Veraltete Vorlagen und Seiten für adaptive Formulare

Weitere Informationen finden Sie unter [Durch Installation des Kompatibilitätspakets mit AEM Forms 6.5 kompatible Assets](../../forms/using/compatibility-package.md#assetsmadecompatible).

## Hinzufügen von Unterstützung für Assets aus AEM Forms 6.5, 6.4, 6.3 und 6.2 in AEM Forms 6.5 LTS {#add-support-for-aem-forms-and-assets-in-aem-forms-6.5.lts}

Gehen Sie nach der Aktualisierung wie folgt vor, um das AEM-Kompatibilitätspaket zu installieren und Ihre Assets mit Version 6.5 kompatibel zu machen:

Stellen Sie sicher, dass das [AEM-Kompatibilitätspaket](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) vorinstalliert ist.

1. Installieren Sie das neueste AEM 6.5 LTS [Kompatibilitätspaket](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).

   Weitere Informationen zum Hochladen und Installieren des Pakets finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).

1. Nachdem die Protokolle stabilisiert sind, starten Sie den Server neu.
1. Verwenden Sie das Migrationsdienstprogramm, um Ihre Assets mit 6.5 LTS kompatibel zu machen.

   >[!NOTE]
   >
   > Es wird empfohlen, den `Ctrl + C`-Befehl zu verwenden, um SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

   Weitere Informationen finden Sie unter [Migrationsdienstprogramm](../../forms/using/migration-utility.md).

## Durch Installation des Kompatibilitätspakets wurde Assets mit AEM Forms 6.5 LTS kompatibel gemacht {#assetsmadecompatible}

Durch die Installation des Kompatibilitätspakets können Sie die folgenden Assets und Vorlagen mit AEM Forms 6.5 LTS kompatibel machen:

* Correspondence Management-Assets aus AEM 6.4 und früher:

   * [Briefe](../../forms/using/create-letter.md)
   * [Datenwörterbücher](/help/forms/using/data-dictionary.md)
   * Dokumentfragmente

* Veraltete Vorlagen für adaptive Formulare:

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* Veraltete Seiten für adaptive Formulare:

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment
