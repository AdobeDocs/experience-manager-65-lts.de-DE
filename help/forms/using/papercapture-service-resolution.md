---
title: Artikel zur Fehlerbehebung für das Problem, wenn der PaperCapture-Dienst OCR-Vorgänge (Optical Character Recognition) für PDFs nicht ausführt.
description: Erfahren Sie die Schritte zur Behebung des Problems, dass der PaperCapture-Dienst OCR-Vorgänge (Optical Character Recognition) für PDFs nicht ausführt.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: de3cd0ad-0b18-4d9a-8c6b-72cc16149cfc
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
source-wordcount: '247'
ht-degree: 87%
---
# Der PaperCapture-Dienst kann keine OCR-Vorgänge für PDFs ausführen

## Problem

Nach der Aktualisierung auf AEM Forms Service Pack 6.5.21.0 kann der `PaperCapture`-Dienst keine OCR-Vorgänge (optische Zeichenerkennung) mehr für PDFs durchführen. Der Dienst generiert keine Ausgabe in Form einer PDF oder einer Protokolldatei.

## Gilt für

Diese Lösung gilt für:

* AEM Forms auf allen JEE-Servern (JBoss®, WebLogic, WebSphere®)
* AEM Forms auf OSGi-Servern

## Lösung

1. Laden Sie [Hotfix](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&reserved=0) vom Software Distribution-Portal herunter.
1. Extrahieren und kopieren Sie den Inhalt des heruntergeladenen Ordners.
1. Navigieren Sie für die entsprechenden Anwendungs-Server zu den unten angegebenen Pfaden:
   * **JBoss®**:
     `..\Adobe\Adobe_Experience_Manager_Forms\jboss\standalone\svcnative\PaperCaptureSvc`
   * **WebLogic**:
     `..\Adobe\Adobe_Experience_Manager_Forms\crx-repository\bedrock\svcnative\PaperCaptureSvc`
   * **Websphere®**:\
     `..\Adobe\Adobe_Experience_Manager_Forms\crx-repository\bedrock\svcnative\PaperCaptureSvc`
   * **OSGi-Setup**:\
     `..\quickstart\crx-quickstart\bedrock\svcnative\PaperCaptureSvc`
1. Stoppen Sie den AEM Forms-Anwendungs-Server.
1. Ersetzen Sie den vorhandenen Inhalt des Ordners `PaperCaptureSvc` durch den kopierten Inhalt.
1. Starten Sie den AEM Forms-Anwendungs-Server neu.

   >[!NOTE]
   >
   >Adobe empfiehlt die Verwendung des Befehls `Ctrl + C` zum Neustart von SDK. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.
