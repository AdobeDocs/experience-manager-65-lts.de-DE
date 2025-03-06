---
title: Konfigurieren von Ersatzschriftarten
description: Erfahren Sie, wie Sie Ersatzschriftarten für AEM Forms konfigurieren. Sie können die Datei „FontManagerResources.properties“ verwenden, um die Standardschriftarten den Ersatzschriftarten manuell zuzuordnen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: d11bb8dc-d0fe-4182-88dd-9ef1ecf687db
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 100%

---

# Konfigurieren von Ersatzschriftarten {#configuring-fallback-fonts}

Sie können die Datei „FontManagerResources.properties“ zum Zuordnen der AEM Forms-Standardschriftarten zu Ersatzschriftarten manuell konfigurieren, falls die Standardschriftarten auf dem Server nicht verfügbar sind. Diese Eigenschaftendatei ist in der Datei „adobe-fontmanager.jar“ enthalten.

>[!NOTE]
>
>Die Konfiguration der Ersatzschriftarten gilt auch für den Assembler-Dienst.

1. Wechseln Sie im Ordner „*`[aem-forms root]`*/configurationManager/export“ zur Datei „adobe-livecycle-*`[appserver]`*.ear“, erstellen Sie eine Sicherungskopie und dekomprimieren Sie die Originaldatei.
1. Suchen Sie die Datei „adobe-fontmanager.jar“ und dekomprimieren Sie sie.
1. Suchen Sie die Datei „FontManagerResources.properties“ und öffnen Sie sie in einem Texteditor.
1. Ändern Sie die Speicherorte und Namen der Standard- und Ersatzschriftarten den Anforderungen entsprechend und speichern Sie die Datei.

   Die Schriftarteinträge in der Datei „FontManagerResources.properties“ sind relativ zum Ordner „*`[aem-forms root]`*/fonts“. Wenn Sie Schriftarten angeben, die keine AEM Forms-Standardschriftarten sind, müssen Sie diese Schriftarten in dieser Verzechnisstruktur installieren (entweder in einem vorhandenen oder einem neu erstelltem Verzeichnis).

   >[!NOTE]
   >
   >Wenn die angegebene Schriftart bzw. Standardschriftart kein spezifisches Unicode-Zeichen enthält oder nicht verfügbar ist, wird das Zeichen gemäß der folgenden Priorität in einer Ersatzschriftart ausgewählt:

   * Gebietsschemaspezifische Schriftart
   * ROOT-Schriftart, wenn kein Gebietsschema festgelegt ist
   * Allgemeine Schriftart, die gemäß der in der Tabelle mit den Ersatzschriftarten festgelegten Reihenfolge gesucht wird

1. Komprimieren Sie die Datei „adobe-fontmanager.jar“ wieder.
1. Komprimieren Sie die Datei „adobe-livecycle-*`[appserver]`*.ear“ neu und stellen Sie sie anschließend manuell oder durch Ausführen von Configuration Manager erneut bereit.

>[!NOTE]
>
>Komprimieren Sie die Datei „adobe-livecycle-`[appserver]`.ear“ nicht mit Configuration Manager, da dadurch Ihre Änderungen mit den AEM Forms-Standardwerten überschrieben würden.
