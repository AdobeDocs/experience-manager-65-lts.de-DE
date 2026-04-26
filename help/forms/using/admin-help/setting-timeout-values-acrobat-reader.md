---
title: Festlegen von Timeout-Werten für die Verwendung mit Acrobat Reader DC-Erweiterungen
description: Erfahren Sie, wie Sie Timeout-Werte für die Verwendung mit Acrobat Reader DC-Erweiterungen festlegen.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: c2f96686-15e3-4d92-acfe-f971c5849de4
source-git-commit: 103250f3442cf7c2793c51a95b1bf4fbaff71463
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 100%

---

# Festlegen von Timeout-Werten für die Verwendung mit Acrobat Reader DC-Erweiterungen  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Stellen Sie bei der Arbeit an vielen PDF-Dateien in Acrobat Reader DC-Erweiterungen sicher, dass die folgenden Timeout-Werte angemessen festgelegt sind, damit es bei Aufträgen nicht zu Zeitüberschreitungen und somit zu Fehlern kommt:

**Standard-Timeout für Entsorgung:**

Dieser Wert kann in der Administrationskonsole festgelegt werden. Wählen Sie „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“ aus und geben Sie einen Wert für „Standard-Timeout für Dokumententsorgung“ an.

**Timeout des User Managers von AEM Forms:** Dieser Wert kann durch Bearbeiten der Datei config.xml festgelegt werden. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“ und dann auf „Exportieren“. Öffnen Sie die exportierte Datei „config.xml“ und bearbeiten Sie die folgenden Zeilen:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Speichern Sie die Datei „config.xml“ und importieren Sie sie wieder zurück in die Administrationskonsole.

**Timeout bei einer Anwendungsserversitzung:** Dieser Wert kann auf dem Anwendungsserver festgelegt werden. Weitere Informationen finden Sie in der Dokumentation des entsprechenden Anwendungsservers.
