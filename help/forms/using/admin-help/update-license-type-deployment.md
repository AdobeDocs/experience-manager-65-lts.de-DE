---
title: Aktualisieren des Lizenztyps für die Bereitstellung
description: Aktualisieren Sie den Lizenztyp für die Bereitstellung, indem Sie die Seite „Lizenz ändern“ in der Administrationskonsole verwenden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/get_started_with_administering_aem_forms_on_jee
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 21f062c6-bb9a-4e18-9fb2-2bb7f0050c9c
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 100%

---

# Aktualisieren des Lizenztyps für die Bereitstellung {#update-the-license-type-for-the-deployment}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Als Teil des Installationsprozesses von AEM Forms haben Sie mithilfe von Configuration Manager die erforderlichen AEM Forms-Module konfiguriert und bereitgestellt. Diese Module sind standardmäßig mit einer 60-Tage-Testlizenz konfiguriert. Verwenden Sie die Seite „Lizenz ändern“ in der Administrationskonsole, um den Lizenztyp für die Bereitstellung zu ändern. Die zurzeit bereitgestellten Module werden auf der Seite „Lizenz ändern“ angezeigt.

Auf der Seite „Lizenz ändern“ werden Informationen über Ihre Lizenz angezeigt:

* der aktuelle Lizenztyp
* Datum und Uhrzeit der letzten Lizenzaktualisierung
* Person, die die letzte Aktualisierung ausgeführt hat
* der aktuelle Status der Lizenz
* das Installationsdatum von AEM Forms
* das Ablaufdatum der aktuellen Lizenz

>[!NOTE]
>
>Die Lizenzänderung wird auf alle bereitgestellten Module angewendet. Bevor Sie den Lizenztyp ändern, heben Sie die Bereitstellung aller nicht lizenzierten Module auf. Wählen Sie nicht den Lizenztyp „Produktion“ aus, wenn die Liste bereitgestellter Module andere Module enthält als die, die Sie von Adobe erworben haben.

## Aktualisieren des Lizenztyps {#update-the-license-type}

1. Klicken Sie in der Administrationskonsole auf „Lizenzierung“.
1. Lesen Sie die AEM Forms-Lizenzvereinbarung für Endanwendende, wählen Sie „Akzeptieren“ aus, wenn Sie den Bedingungen der Vereinbarung zustimmen, und klicken Sie dann auf „Weiter“.
1. Wählen Sie auf der Seite „Lizenz ändern“ einen Lizenztyp aus:

   * **EVAL:** 60-Tage-Testlizenz
   * **DEV:** Permanente Entwicklungslizenz
   * **NFR:** 2-Jahres-Testlizenz
   * **IDEV:** 1-Jahres-Abonnement des Entwicklerprogramms von Adobe
   * **Production:** Permanente Lizenz

1. Wählen Sie die Option „Ja, die Lizenzänderung ist für alle bereitgestellten Module gültig“ aus.
1. Klicken Sie auf „Lizenzänderung bestätigen“. In einer Meldung wird angezeigt, dass die Lizenz erfolgreich aktualisiert wurde.
