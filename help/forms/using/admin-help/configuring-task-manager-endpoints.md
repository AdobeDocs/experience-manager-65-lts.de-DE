---
title: Konfigurieren der Task Manager-Endpunkte
description: Erfahren Sie, wie Sie Task Manager-Endpunkte konfigurieren, um den Dienst aufzurufen.  Zum Konfigurieren von Task Manager-Endpunkten sind verschiedene Einstellungen erforderlich.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 57fd8b5d-6347-4b83-9489-e8ee59ee39a5
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 100%

---

# Konfigurieren der Task Manager-Endpunkte {#configuring-task-manager-endpoints}

Task Manager-Endpunkte ermöglichen es Workspace-Benutzenden, den Dienst aufzurufen.

**Task Manager-Endpunkteinstellungen**

Mithilfe der folgenden Einstellungen können Sie einen Task Manager-Endpunkt konfigurieren.

**Name:** (Obligatorisch) Identifiziert den Endpunkt. Der Name wird in Workspace in der Kartenansicht angezeigt. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird. Wenn Sie eine URL als Name des Endpunktes angeben, vergewissern Sie sich, dass sie den in RFC1738 angegebenen Syntaxregeln entspricht.

**Beschreibung**: Eine Beschreibung des Endpunkts. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird.

**Aufgabenanweisungen:** Anweisungen für den Benutzer, der diesen Workflow startet.

**Prozesseigentümer:** Der Name der für den Prozess verantwortlichen Person.

**Benutzer kann Aufgabe weiterleiten:** Ermöglicht dem Benutzer die Weiterleitung der ursprünglichen Aufgabe.

**Anlagenfenster anzeigen:** Ermöglicht dem Benutzer, das Anlagenfenster zu sehen.

**Hinzufügen von Anhängen zulassen:** Ermöglicht dem Benutzer das Hinzufügen von Anlagen und Notizen.

**Aufgabe ursprünglich gesperrt:** Sperrt die ursprüngliche Aufgabe.

**ACLs für freigegebene Warteschlangen hinzufügen:** Die ursprüngliche Aufgabe wird mit ACLs für Benutzer freigegebener Warteschlangen erstellt.

**Kategorsierung:** (Obligatorisch) Die Kategorie, in der das Formular in Workspace dem Benutzer angezeigt wird. Wählen Sie eine Kategorie aus der Liste aus oder wählen Sie „Neue Kategorie“, um eine Kategorie hinzuzufügen.

**Vorgangsname:** (Obligatorisch) Eine Liste von Vorgängen, die dem Endpunkt zugewiesen werden können.
