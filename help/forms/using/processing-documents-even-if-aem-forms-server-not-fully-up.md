---
title: Der AEM Forms-Server beginnt mit der Verarbeitung der Dokumente, noch bevor alle Dienste ausgeführt werden.
description: Der AEM Forms-Server beginnt mit der Verarbeitung der Dokumente, noch bevor alle Dienste auf dem JEE- und OSGi-Server ausgeführt werden.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 22dd8daa-b8c6-4e7d-bca3-3958a79fb4b5
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 99%

---

# Der AEM Forms-Server beginnt mit der Verarbeitung der Dokumente, noch bevor alle Dienste ausgeführt werden.{#aem-forms-server-start-processing-documents-even-if-it-is-not-fully-up}

## Problem {#issue}

<!--When user restarts AEM Forms server, the current calling processes or services still continue such as rendering PDF documents and more. It causes the restart of the AEM Forms server to not startup correctly.-->

Der AEM Forms-Server beginnt, noch bevor er vollständig eingerichtet ist und alle Anwendungen ausgeführt werden, mit der Verarbeitung der Dokumente.


## Gilt für {#applies-to}

Diese Lösung gilt für AEM Forms on JEE-Server und AEM Forms on OSGi-Server.

## Lösung {#solution}

Um das Problem zu beheben, fügen Sie während des Server-Starts das Argument `Dcom.adobe.livecycle.dsc.deferServiceStart=true` zur [Batch-Datei](https://experienceleague.adobe.com/docs/experience-manager-65-lts/deploying/deploying/command-line-start-and-stop.html#windows-platform-start-bat-script-example) hinzu.
