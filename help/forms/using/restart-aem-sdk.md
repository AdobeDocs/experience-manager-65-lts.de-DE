---
title: Neustarten des AEM SDK
description: Best Practices für den Neustart des AEM SDK
role: Admin, Developer, User
feature: Adaptive Forms,AEM Forms on JEE,AEM Forms on OSGi
solution: Experience Manager, Experience Manager Forms
hide: true
hidefromtoc: true
exl-id: 68935045-89b1-4219-b111-88a4600200df
source-git-commit: 103250f3442cf7c2793c51a95b1bf4fbaff71463
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 100%

---

# Neustarten des AEM SDK

Wenn Sie das AEM SDK neu starten, indem Sie die Java™-Prozesse stoppen, kann dies zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen. Es tritt ein Fehler wie der folgende auf:

`javax.jcr.RepositoryException: Applying repoinit operation failed despite retry; set loglevel to DEBUG to see all exceptions. Last exception message was: Failed to set ACL (javax.jcr.ValueFormatException: Invalid type: 0) AclLine ALLOW {principals=[forms-xfa-writers], privileges=[jcr:modifyProperties]} restrictions=[rep:glob=[*/jcr:content/*], rep:itemNames=[xfaForm], fd:condition=[xfaForm, 1]]`

![Fehler beim AEM SDK-Neustart](/help/forms/using/assets/restart-sdk-error.png)

## Lösung

Wechseln Sie zum aktiven Befehlsfenster und drücken Sie die Tastenkombination `Ctrl + C`, um das AEM SDK neu zu starten.

Es wird empfohlen, den Befehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mithilfe alternativer Methoden, z. B. durch Beenden von Java™-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.
