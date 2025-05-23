---
title: Designer installieren und konfigurieren
description: Designer ist als eigenständiges Installationsprogramm sowie als Teil von WorkBench verfügbar. Erfahren Sie, wie Sie Designer als eigenständige Anwendung installieren.
role: Admin, User, Developer
feature: Forms Designer,Designer
solution: Experience Manager, Experience Manager Forms
exl-id: 526bbc59-62c3-4e6d-a938-e368d07fe6b0
source-git-commit: 060bb23d64a90f0b2da487ead4c672cbf471c9a8
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 76%

---

# Designer installieren und konfigurieren{#installing-and-configuring-designer}

## Voraussetzungen {#pre-requisites}

+++ Für die 64-Bit-Version von AEM Forms Designer (empfohlen)

* Installation der 64-Bit-Version von [Visual C++ 2019 Redistributable (x64)](https://learn.microsoft.com/de-de/cpp/windows/latest-supported-vc-redist?view=msvc-170). Stellen Sie vor Installationsbeginn sicher, dass die oben genannten Redistributable Runtime Packages installiert sind.
* Eine Benutzerin bzw. ein Benutzer mit Administratorrechten zum Installieren oder Deinstallieren von AEM Forms Designer.

+++

+++ Für die 32-Bit-Version von AEM Forms Designer

* Installation der 32-Bit-Version von [Visual C++ 2019 Redistributable (x64)](https://learn.microsoft.com/de-de/cpp/windows/latest-supported-vc-redist?view=msvc-170). Stellen Sie vor Installationsbeginn sicher, dass die oben genannten Redistributable Runtime Packages installiert sind.
* Eine Benutzerin bzw. ein Benutzer mit Administratorrechten zum Installieren oder Deinstallieren von AEM Forms Designer.

+++

>[!NOTE]
>
>* Die 64-Bit-Version von Designer wurde mit AEM 6.5 Forms Service Pack 19 (6.5.19.0) eingeführt.
>* Die 32-Bit-Version von Designer wird seit der Veröffentlichung von [AEM Forms Service Pack 21 (6.5.21.0) nicht mehr unterstützt](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).
> * Die unterstützten Plattformen für Forms Designer sind auf die von AEM Forms unterstützten Plattformen ausgerichtet. Um mehr über die unterstützten Plattformen für Forms Designer zu erfahren[ klicken Sie hier](/help/sites-deploying/technical-requirements.md)

Weitere Informationen zur Installation von Forms Designer finden Sie unter [Häufig gestellte Fragen](#fandq).

## Installieren von AEM Forms Designer {#install-designer}

Designer ist als eigenständiges Installationsprogramm sowie als Teil von WorkBench verfügbar. Wenn Sie ein eigenständiges Installationsprogramm für AEM Forms Designer verwenden, führen Sie die folgenden Schritte aus:

1. Deinstallieren Sie die vorherige Version von AEM Forms Designer, falls sie installiert ist.
1. Laden Sie die 64-Bit-Version von AEM Forms Designer (empfohlen) oder die 32-Bit-Version von AEM Forms Designer entsprechend Ihren Anforderungen herunter.

   >[!NOTE]
   > 
   >* Die Einstellung von 32-Bit-Forms Designer ist mit AEM 6.5 Forms Service Packs 20 (6.5.20.0) geplant. Adobe empfiehlt ein Upgrade auf die 64-Bit-Version von Forms Designer.
   >* 64-Bit Forms Designer ist nur für AEM 6.5 Forms Service Packs 19 (6.5.19.0) oder höher verfügbar.
   >* Ab Adobe Experience Manager 6.5 Forms Service Pack 15 (6.5.15.0) enthält die Forms Designer-Version auch die Service Pack-Version. Beispielsweise ist 6.5.15.20221112.1.0 die Versionsnummer für Service Pack 15. Hier ist 6.5.15 die Version des Service Packs.

1. Starten Sie das Installationsprogramm für AEM Forms Designer, indem Sie auf die Datei „setup.exe“ doppelklicken.
1. Fahren Sie fort und geben Sie Ihre Details und die Seriennummer auf dem Bildschirm „Personalisierung“ an.

   >[!NOTE]
   >
   >* Beziehen Sie Ihren Forms Designer-Lizenzschlüssel über die [Lizenzierungs-Website von Adobe](https://licensing.adobe.com/).

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

Beim Aktualisieren der neuesten Version von AEM Forms Designer 6.5.16.0 gibt es zwei Fälle:

* **1.**: Wenn die Benutzerin bzw. der Benutzer eine frühere Version von AEM Forms Designer als 6.5.15.0 verwendet.
* **Fall 2**: Wenn die Benutzerin bzw. der Benutzer die Version von AEM Forms Designer 6.5.15.0 hat.

+++**Wenn die Benutzerin bzw. der Benutzer eine frühere Version von AEM Forms Designer als 6.5.15.0 verwendet.**

Wenn Sie ein eigenständiges Installationsprogramm für AEM Forms Designer verwenden, führen Sie die folgenden Schritte aus:

1. Vor der Installation von **AEM Forms Designer6.5.16.0** müssen Benutzende alle vorherigen Versionen deinstallieren.
1. Laden Sie [AEM Forms Designer 6.5.15.0](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) von der Seite AEM-Formularversionen herunter und installieren Sie es.
1. Nach erfolgreicher Installation von **AEM Forms Designer6.5.15.0** laden Sie [AEM Forms Designer 6.5.16.0](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) herunter und installieren Sie es durch Doppelklicken auf die heruntergeladene Installationsdatei.

+++

+++**Wenn die Benutzerin bzw. der Benutzer die Version 6.5.15.0 AEM Forms Designer verwendet**

Wenn Sie ein eigenständiges Installationsprogramm für AEM Forms Designer verwenden, führen Sie die folgenden Schritte aus:
1. Laden Sie die neueste Version von AEM Forms Designer vom [Software Distribution-Portal](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) herunter.
1. Installieren Sie die neueste Version von AEM Forms Designer, indem Sie auf die heruntergeladene Installationsdatei doppelklicken.

+++

## Häufig gestellte Fragen {#fandq}

* **Können Benutzerinnen und Benutzer direkt auf die 64-Bit-Version von Designer aktualisieren oder sie installieren?**
   * Ja, Benutzerinnen und Benutzer können direkt auf die 64-Bit-Version von Designer aktualisieren oder sie installieren. Zur Aktualisierung installieren Sie das vollständige [SP19](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/Designer-Patch/sp19_x64/aemforms_designer_6_5_0_wwe_win.zip) Designer-Installationsprogramm und wenden Sie darüber die nachfolgende Designer-Patch-Version an.

     >[!NOTE]
     > Deinstallieren Sie vor dem Upgrade auf die 64-Bit-Version von Designer zunächst die 32-Bit-Version, sofern diese vorhanden ist.

* **Können Benutzerinnen und Benutzer sowohl 32-Bit als auch 64-Bit auf ihrem System installiert lassen?**
   * Nein, 32-Bit- und 64-Bit-Installationen funktionieren nicht auf derselben Maschine. Es kann nur entweder ein 32-Bit- oder ein 64-Bit-Designer installiert sein.

* **Wie überprüfe ich, ob eine Benutzerin oder ein Benutzer den 64-Bit- oder den 32-Bit-Designer verwendet?**
   * Es gibt zwei Möglichkeiten, die Version von Forms Designer zu überprüfen:

      1. Öffnen Sie Designer, gehen Sie zu „Hilfe“ und klicken Sie auf „Über Designer“. Dort finden Sie Informationen zur Designer-Version sowie die Bit-Informationen. Beispielsweise sehen Sie am Ende der Version den Zusatz „64 Bit“, wie hier gezeigt:

         `6.5.21.20240522.1.161 | 64 bit`
      1. Öffnen Sie Designer. Oben links sehen Sie ein Markensymbol, das 64-Bit-Informationen und den Produktnamen enthält.
