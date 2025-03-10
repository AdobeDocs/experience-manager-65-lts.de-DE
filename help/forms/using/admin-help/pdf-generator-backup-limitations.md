---
title: Backup-Beschränkungen für PDF Generator
description: Erfahren Sie mehr über die Backup-Beschränkungen für PDF Generator. Das von PDF Generator verwendete temporäre Verzeichnis kann nicht gesichert werden, da der Inhalt in festgelegten Zeitabständen gelöscht wird.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
noindex: true
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: f76ce3be-6d50-4531-a982-2e902f866208
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '73'
ht-degree: 100%

---

# Backup-Beschränkungen für PDF Generator {#pdf-generator-backup-limitations}

Der temporäre Ordner, der von PDF Generator zum Konvertieren von Dateien verwendet wird, kann nicht gesichert werden. Auch wenn der Dienst ordnungsgemäß wiederhergestellt wird, können dennoch Daten verloren gehen, weil PDF Generator den Inhalt des temporären Ordners in festgelegten Zeitabständen prüft und löscht.
