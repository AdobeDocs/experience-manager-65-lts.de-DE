---
title: Designer installieren und konfigurieren
description: Designer ist als eigenständiges Installationsprogramm sowie als Teil von WorkBench verfügbar. Erfahren Sie, wie Sie eine eigenständige Designer installieren.
role: Admin, User, Developer
feature: Forms Designer,Designer
solution: Experience Manager, Experience Manager Forms
exl-id: 526bbc59-62c3-4e6d-a938-e368d07fe6b0
source-git-commit: eb6f6b994fdd3b2b01e77700d2deb7bd2830ac8f
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 65%

---

# Designer installieren und konfigurieren{#installing-and-configuring-designer}

## Voraussetzungen {#pre-requisites}

+++ Für die 64-Bit-Version von AEM Forms Designer (empfohlen)

* Installieren Sie eine 64-Bit-Version von [Visual C++ 2019 Redistributable (x64)](https://learn.microsoft.com/de-de/cpp/windows/latest-supported-vc-redist?view=msvc-170). Stellen Sie vor Installationsbeginn sicher, dass die oben genannten Redistributable Runtime Packages installiert sind.
* Eine Benutzerin bzw. ein Benutzer mit Administratorrechten zum Installieren oder Deinstallieren von AEM Forms Designer.

+++

+++ Für die 32-Bit-Version von AEM Forms Designer

* Installieren Sie eine 32-Bit-Version von [Visual C++ 2019 Redistributable (x64)](https://learn.microsoft.com/de-de/cpp/windows/latest-supported-vc-redist?view=msvc-170). Stellen Sie vor Installationsbeginn sicher, dass die oben genannten Redistributable Runtime Packages installiert sind.
* Eine Benutzerin bzw. ein Benutzer mit Administratorrechten zum Installieren oder Deinstallieren von AEM Forms Designer.

+++

>[!NOTE]
>
>* Die 64-Bit-Version von Designer wurde mit AEM 6.5 Forms Service Pack 19 (6.5.19.0) eingeführt.
>* Die 32-Bit-Version von Designer ist seit der Veröffentlichung von [AEM Forms Service Pack 21 (6.5.21.0) veraltet](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).
> * Die unterstützten Plattformen für Forms Designer sind auf die von AEM Forms unterstützten Plattformen ausgerichtet. Um mehr über die unterstützten Plattformen für Forms Designer zu erfahren[ klicken Sie hier](/help/sites-deploying/technical-requirements.md)

Weitere Informationen zur Installation von Forms Designer finden Sie unter [Häufig gestellte Fragen](#fandq).

## Installieren von AEM Forms Designer {#install-designer}

Designer ist als eigenständiges Installationsprogramm sowie als Teil von WorkBench verfügbar. Wenn Sie ein eigenständiges Installationsprogramm für AEM Forms Designer verwenden, führen Sie die folgenden Schritte aus:

1. Deinstallieren Sie die vorherige Version von AEM Forms Designer, falls sie installiert ist.
1. Laden Sie die 64-Bit-Version von AEM Forms Designer (empfohlen) oder die 32-Bit-Version von AEM Forms Designer entsprechend Ihren Anforderungen herunter.

   >[!NOTE]
   > 
   >* Die 32-Bit-Version von Forms Designer wird voraussichtlich ab AEM 6.5 Forms Service Packs 20 (6.5.20.0) nicht mehr unterstützt. Adobe empfiehlt eine Aktualisierung auf 64-Bit-Forms Designer.
   >* Die 64-Bit-Version von Forms Designer ist nur für AEM 6.5 Forms Service Packs 19 (6.5.19.0) oder höher verfügbar.
   >* Ab Adobe Experience Manager 6.5 Forms Service Pack 15 (6.5.15.0) umfasst die Version von Forms Designer auch die Version des Service Packs. Für Service Pack 15 ist die Versionsnummer beispielsweise 6.5.15.20221112.1.0. In diesem Beispiel ist 6.5.15 die Service Pack-Version.

1. Starten Sie das Installationsprogramm für AEM Forms Designer, indem Sie auf die Datei „setup.exe“ doppelklicken.
1. Fahren Sie fort und geben Sie Ihre Details und die Seriennummer auf dem Bildschirm „Personalisierung“ an.

   >[!NOTE]
   >
   >* Beziehen Sie Ihren Forms Designer-Lizenzschlüssel von der [Adobe-Lizenzierungswebsite](https://licensing.adobe.com/).

1. Wenn Sie die Lizenzvereinbarung akzeptieren, klicken Sie auf Weiter, um fortzufahren.
1. (Optional) Ändern Sie den standardmäßigen Installationspfad, wenn Sie Designer an einem anderen Speicherort installieren möchten. Klicken Sie auf Weiter.
1. Klicken Sie auf Zurück, um gegebenenfalls die Voreinstellungen zu ändern. Um Designer zu installieren, klicken Sie auf Installieren.
1. Klicken Sie auf Fertig stellen, wenn die Installation abgeschlossen ist.

Alternativ können Sie AEM Forms Designer über die Befehlszeile im passiven oder stillen Modus installieren.

* Passives Befehlszeileninstall: Das Installationsprogramm zeigt eine Fortschrittsleiste an, die anzeigt, dass die Installation noch nicht abgeschlossen ist, jedoch keine Eingabeaufforderungen oder Fehlermeldungen angezeigt werden. Nach dem Start kann die Installation nicht mehr abgebrochen werden.

```shell
msiexec /i "<absolute path>\Designer.msi" /passive SERIALNUMBER=****-****-****-****-****-****
```

* Stille Befehlszeilen-Installation: Das Installationsprogramm führt die Installation aus, ohne eine Benutzeroberfläche anzuzeigen. Es werden keine Eingabeaufforderungen, Meldungen oder Dialogfelder angezeigt. Nach dem Start kann die Installation nicht mehr abgebrochen werden.

```shell
msiexec /i "<absolute path>\Designer.msi" /quiet SERIALNUMBER=****-****-****-****-****-****
```

## Aktualisieren von AEM Forms Designer {#update-forms-designer}

Beim Aktualisieren der neuesten Version (6.5.16.0) von AEM Forms Designer gibt es zwei Fälle:

* **1. Fall**: Wenn die Benutzerin bzw. der Benutzer eine frühere Version von AEM Forms Designer als 6.5.15.0 verwendet.
* **2. Fall**: Wenn die Benutzerin bzw. der Benutzer die Version 6.5.15.0 von AEM Forms Designer verwendet.

+++**Wenn die Benutzerin bzw. der Benutzer eine frühere Version von AEM Forms Designer als 6.5.15.0 verwendet.**

Wenn Sie ein eigenständiges Installationsprogramm für AEM Forms Designer verwenden, führen Sie die folgenden Schritte aus:

1. Vor der Installation von **AEM Forms Designer6.5.16.0** müssen Benutzende alle vorherigen Versionen deinstallieren.
1. Laden Sie [AEM Forms Designer 6.5.15.0](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#) von der Seite von AEM Forms-Versionen herunter und installieren Sie es.
1. Nach erfolgreicher Installation von **AEM Forms Designer6.5.15.0** laden Sie [AEM Forms Designer 6.5.16.0](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#) herunter und installieren Sie es durch Doppelklick auf die heruntergeladene Installationsdatei.

+++

+++**Wenn die Benutzerin bzw. der Benutzer über die AEM Forms Designer-Version 6.5.15.0 verfügt**

Wenn Sie ein eigenständiges Installationsprogramm für AEM Forms Designer verwenden, führen Sie die folgenden Schritte aus:

1. Laden Sie die neueste Version von AEM Forms Designer vom [Software Distribution-Portal](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#) herunter.
1. Installieren Sie die neueste Version von AEM Forms Designer, indem Sie auf die heruntergeladene Installationsdatei doppelklicken.

+++

## Häufig gestellte Fragen {#fandq}

* **Kann ein Anwender 64-Bit-Designer direkt aktualisieren oder installieren?**
   * Ja, Benutzer können Designer direkt aktualisieren oder installieren. Installieren Sie zum Upgrade das Vollinstallationsprogramm für [SP19](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/Designer-Patch/sp19_x64/aemforms_designer_6_5_0_wwe_win.zip) Designer und wenden Sie die nachfolgende Designer-Patch-Version darauf an.

     >[!NOTE]
     > Bevor Sie auf 64-Bit-Designer aktualisieren, deinstallieren Sie zunächst 32-Bit-Designer, falls vorhanden.

* **Können Benutzerinnen und Benutzer sowohl 32-Bit als auch 64-Bit auf ihrem System installiert lassen?**
   * Nein. Eine 32-Bit- und 64-Bit-Installation funktioniert nicht auf demselben Computer. Benutzer können entweder über eine 32-Bit-Designer oder eine 64-Bit-Designer verfügen.

* **Wie kann überprüft werden, ob eine Benutzerin bzw. ein Benutzer 64-Bit-Designer oder 32-Bit-Designer verwendet?**
   * Es gibt zwei Möglichkeiten, die Version von Forms Designer zu überprüfen:

      1. Öffnen Sie Designer.
      1. Klicken Sie auf **Hilfe** > **Über Designer**, um die Designer-Versions- und Bitness-Informationen anzuzeigen.
Beispielsweise endet die Versionszeichenfolge mit **64-Bit**, wie im folgenden Beispiel gezeigt:
         `6.5.21.20240522.1.161 | 64 bit`
      1. Öffnen Sie Designer. Links oben sehen Sie ein Branding-Symbol, das 64-Bit-Informationen mit dem Produktnamen enthält.
