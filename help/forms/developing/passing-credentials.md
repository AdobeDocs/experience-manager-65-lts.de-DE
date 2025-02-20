---
title: Übergeben von Anmeldeinformationen mithilfe von WS-Security-Kopfzeilen
description: Erfahren Sie, wie Sie Berechtigungen mithilfe von WS-Security-Headern übergeben.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 100%

---

# Übergeben von Anmeldeinformationen mithilfe von WS-Security-Kopfzeilen {#using-execute-script-service-aem-forms-jee-workbench}

Beim Aufrufen eines AEM Forms on JEE-Service mithilfe von Webservices können Sie WS-Security-Kopfzeilen verwenden, um die für AEM Forms on JEE erforderlichen Client-Authentifizierungsinformationen zu übergeben. WS-Security definiert SOAP-Erweiterungen zur Implementierung von Client-Authentifizierung, Vertraulichkeit von Nachrichten und Nachrichtenintegrität. Daher können Sie AEM Forms on JEE-Services aufrufen, wenn AEM Forms on JEE als eigenständiger Server oder in einer Cluster-Umgebung bereitgestellt wird.

Wie Sie WS-Security-Kopfzeilen an AEM Forms on JEE übergeben, hängt davon ab, ob Sie Axis-generierte Java-Klassen oder eine .NET-Client-Assembly verwenden, die den nativen SOAP-Stapel eines Service nutzt.

>[!NOTE]
>
>Als Beispiel für das Aufrufen eines Service mithilfe von WS-Security-Kopfzeilen wird in diesem Thema ein PDF-Dokument mit einem Kennwort verschlüsselt, indem der Verschlüsselungs-Service aufgerufen wird.

In diesem Dokument werden folgende Themen behandelt:

* Übergeben der Client-Authentifizierung mit Axis-generierten Java-Klassen

* Generieren von Axis-Bibliotheksdateien zum Aufrufen des Verschlüsselungs-Service

* Aufrufen des Verschlüsselungs-Service mithilfe einer WS-Security-Kopfzeile

* Übergeben der Client-Authentifizierung mit einer .NET-Client-Assembly

* Aufrufen des Verschlüsselungs-Service mithilfe einer WS-Security-Kopfzeile


## Voraussetzungen {#requirements}

Um dieses Dokument optimal nutzen zu können, benötigen Sie ein solides Verständnis der AEM Forms auf JEE-Software.

>[!MORELIKETHIS]
>
>* [Übergeben von Anmeldeinformationen mithilfe von WS-Security-Kopfzeilen](assets/passing-credentials-using-ws-security-headers.pdf)
