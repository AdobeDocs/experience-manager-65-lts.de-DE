---
title: Hinzufügen von Schriftarten für das Grafik-Rendering
description: Mit AEM können Sie Grafiken erstellen, die Text enthalten, der dynamisch aus Ihrem Inhalt übernommen wird.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 5ceaa9f0-aba1-40a3-97ef-f5ade0c2a54a
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 100%

---

# Hinzufügen von Schriftarten für das Grafik-Rendering{#adding-fonts-for-graphic-rendering}

Mit AEM können Sie Grafiken erstellen, die Text enthalten, der dynamisch aus Ihrem Inhalt übernommen wird.

Hierfür können Sie auch Ihre eigenen Schriftarten hochladen und verwenden.

Derzeit unterstützen alle Implementierungen der Java-Plattform [TrueType](https://de.wikipedia.org/wiki/TrueType)-Schriftarten.

1. Öffnen Sie CRXDE Lite und navigieren Sie zu Ihrem Projekt-Programmordner:

   `/apps/<your-project>/`

1. Erstellen Sie einen Knoten unter `/apps/<your-project>/`:

   * **Name**: `fonts`
   * **Typ**: `sling:Folder`

   Speichern Sie alle Änderungen.

1. Kopieren Sie die Schriftarten-Dateien in diesen Ordner, z. B. mit WebDAV.

   >[!NOTE]
   >
   >Die Schriftarten-Dateien im Repository müssen die Dateiendung `*.ttf` oder `*.TTF` aufweisen.

1. Aktualisieren Sie die [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) von [Day Commons GFX Font Helper](/help/sites-deploying/osgi-configuration-settings.md). Fügen Sie den Pfad zum Schriftarten-Ordner hinzu, d. h. `/apps/<your-project>/fonts`.

1. Kehren Sie zu CRXDE Lite zurück. Sie sollten jetzt in Ihrem Ordner einen Knoten namens `.fontlist` sehen, der den Namen der importierten Schriftarten enthält.

   Diese Schriftarten stehen jetzt für die Verwendung in der Java-API zur Verfügung.

Ausführliche Informationen zur Verwendung der Schriftarten in der Java-API finden Sie in der [Dokumentation zur Font-Klasse der Java-API](https://download.oracle.com/javase/6/docs/api/java/awt/Font.html).
