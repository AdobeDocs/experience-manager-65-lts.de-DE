---
title: Verwenden von PDF Rasterizer zum Generieren von Ausgabedarstellungen
description: Mit der Adobe PDF Rasterizer-Bibliothek können Sie hochwertige Miniaturansichten und Ausgabedarstellungen erstellen.
contentOwner: AG
role: Developer, Admin
feature: Developer Tools,Renditions
solution: Experience Manager, Experience Manager Assets
exl-id: 003ca1f1-5653-4b6c-a63f-ad5196adf3f2
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 100%

---

# Verwenden von PDF Rasterizer {#using-pdf-rasterizer}

Wenn Sie große, inhaltslastige PDF- oder AI-Dateien in [!DNL Adobe Experience Manager Assets] hochladen, erstellt die Standardbibliothek u. U. keine genaue Ausgabe. Die Adobe PDF Rasterizer-Bibliothek kann zuverlässigere und präzisere Ausgaben erstellen als Standardbibliotheken. Adobe empfiehlt die Verwendung der PDF Rasterizer-Bibliothek für folgende Szenarien:

Adobe empfiehlt die Verwendung der PDF Rasterizer-Bibliothek für folgende Dateien:

* Hohe, inhaltsintensive AI-Dateien oder PDF-Dateien.
* AI-Dateien und PDF-Dateien mit Miniaturansichten, die nicht standardmäßig generiert werden.
* AI-Dateien mit PMS-Farben (Pantone Matching System)

Mit PDF Rasterizer erstellte Miniaturansichten und Vorschauen weisen im Vergleich mit der standardmäßigen Ausgabe eine bessere Qualität auf und bieten daher eine konsistente Darstellung auf allen Geräten. Die Adobe PDF Rasterizer-Bibliothek unterstützt keine Farbraumkonvertierung. Die Ausgabe erfolgt unabhängig vom Farbraum der Quelldatei immer in RGB.

1. Installieren Sie das PDF Rasterizer-Paket auf Ihrer [!DNL Adobe Experience Manager]-Bereitstellung von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/aem-assets-pdf-rasterizer-pkg-4.6.zip).

   >[!NOTE]
   >
   >Die PDF Rasterizer-Bibliothek ist nur für Windows und Linux® verfügbar.

1. Greifen Sie auf die [!DNL Assets] Workflow-Konsole zu unter `https://[aem_server]:[port]/workflow`. Öffnen Sie den Workflow [!UICONTROL DAM-Update-Asset].

1. Gehen Sie folgendermaßen vor, um die Generierung von Miniaturansichten und Web-Ausgabedarstellungen für PDF- und AI-Dateien mit den Standardmethoden zu verhindern:

   * Öffnen Sie den Schritt **[!UICONTROL Miniaturansichten verarbeiten]** und fügen Sie nach Bedarf `application/pdf` oder `application/postscript` in das Feld **[!UICONTROL MIME-Typen überspringen]** auf der Registerkarte **[!UICONTROL Miniaturansichten]** ein.

   ![skip_mime_types-2](assets/skip_mime_types-2.png)

   * Fügen Sie auf der Registerkarte **[!UICONTROL Webfähiges Bild]** je nach Ihren Anforderungen `application/pdf` oder `application/postscript` unter **[!UICONTROL Liste zum Überspringen]** hinzu.

   ![Konfiguration zum Überspringen der Verarbeitung von Miniaturansichten für ein Bildformat](assets/web_enabled_imageskiplist.png)

1. Öffnen Sie den Schritt **[!UICONTROL PDF-/AI-Bildvorschau-Wiedergabe rastern]** und entfernen Sie den MIME-Typ, für den Sie die standardmäßige Erstellung von Bildvorschau-Ausgabedarstellungen überspringen möchten. Entfernen Sie beispielsweise den MIME-Typ `application/pdf`, `application/postscript` oder `application/illustrator` aus der Liste **[!UICONTROL MIME-Typen]**.

   ![process_arguments](assets/process_arguments.png)

1. Ziehen Sie den Schritt **[!UICONTROL PDF Rasterizer-Handler]** aus dem Seitenbereich unter den Schritt **[!UICONTROL Miniaturansichten verarbeiten]**.
1. Konfigurieren Sie die folgenden Argumente für den Schritt **[!UICONTROL PDF Rasterizer-Handler]**:

   * MIME-Typen: `application/pdf` oder `application/postscript`
   * Befehle: `PDFRasterizer -d -s 1280 -t PNG -i ${file}`
   * Fügen Sie Größen für Miniaturansichten hinzu: 319:319, 140:100, 48:48. Fügen Sie ggf. eine benutzerdefinierte Konfiguration für Miniaturansichten hinzu.

   Die Befehlszeilenargumente für den `PDFRasterizer`-Befehl können Folgendes enthalten:

   * `-d`: Flag für eine reibungslose Darstellung von Text, Vektorgrafiken und Bildern. Erstellt Bilder mit besserer Qualität. Die Verwendung dieses Parameters führt allerdings zu einer langsamen Ausführung des Befehls und zu größeren Bildern.

   * `-s`: Maximale Bildabmessung (Höhe oder Breite). Dieser Wert wird für jede Seite in DPI umgewandelt. Bei Seiten mit unterschiedlichen Größen wird u. U. jede Seite mit einem anderen Wert skaliert. Der Standardwert ist die tatsächliche Seitengröße.

   * `-t`: Typ des Ausgabebildes. Gültige Formate sind JPEG, PNG, GIF und BMP. Das Standardformat ist JPEG.

   * `-i`: Pfad für die Eingabe-PDF. Dieser Parameter ist erforderlich.

   * `-h`: Hilfe

1. Um Zwischenausgabeformate zu löschen, wählen Sie **[!UICONTROL Erzeugte Ausgabe löschen]**.
1. Um Web-Ausgabedarstellungen von PDF Rasterizer generieren zu lassen, wählen Sie **[!UICONTROL Webausgabe erstellen]** aus.

   ![generate_web_renditions1](assets/generate_web_renditions1.png)

1. Legen Sie die Einstellungen auf der Registerkarte **[!UICONTROL Webfähiges Bild]** fest.

   ![web_enabled_image1](assets/web_enabled_image1.png)

1. Speichern Sie den Workflow.
1. Damit PDF Rasterizer PDF-Seiten mit PDF-Bibliotheken verarbeiten kann, öffnen Sie das Modell **[!UICONTROL DAM-Prozess-Teil-Asset]** über die [!UICONTROL Workflow]-Konsole.
1. Ziehen Sie im Seitenbereich den Schritt „PDF Rasterizer-Handler“ unter den Schritt **[!UICONTROL Webfähige Bildwiedergaben erstellen]**.
1. Konfigurieren Sie die folgenden Argumente für den Schritt **[!UICONTROL PDF Rasterizer-Handler]**:

   * MIME-Typen: `application/pdf` oder `application/postscript`
   * Befehle: `PDFRasterizer -d -s 1280 -t PNG -i ${file}`
   * Fügen Sie Größen für Miniaturansichten hinzu: `319:319`, `140:100`, `48:48`. Fügen Sie ggf. eine benutzerdefinierte Konfiguration für Miniaturansichten hinzu.

   Die Befehlszeilenargumente für den `PDFRasterizer`-Befehl können Folgendes enthalten:

   * `-d`: Flag für eine reibungslose Darstellung von Text, Vektorgrafiken und Bildern. Erstellt Bilder mit besserer Qualität. Die Verwendung dieses Parameters führt allerdings zu einer langsamen Ausführung des Befehls und zu größeren Bildern.

   * `-s`: Maximale Bildabmessung (Höhe oder Breite). Dieser Wert wird für jede Seite in DPI umgewandelt. Bei Seiten mit unterschiedlichen Größen wird u. U. jede Seite mit einem anderen Wert skaliert. Der Standardwert ist die tatsächliche Seitengröße.

   * `-t`: Typ des Ausgabebildes. Gültige Formate sind JPEG, PNG, GIF und BMP. Das Standardformat ist JPEG.

   * `-i`: Pfad für die Eingabe-PDF. Dieser Parameter ist erforderlich.

   * `-h`: Hilfe

1. Um Zwischenausgabeformate zu löschen, wählen Sie **[!UICONTROL Erzeugte Ausgabe löschen]**.
1. Um Web-Ausgabedarstellungen von PDF Rasterizer generieren zu lassen, wählen Sie **[!UICONTROL Webausgabe erstellen]** aus.

   ![generate_web_renditions](assets/generate_web_renditions.png)

1. Legen Sie die Einstellungen auf der Registerkarte **[!UICONTROL Webfähiges Bild]** fest.

   ![web_enabled_image-1](assets/web_enabled_image-1.png)

1. Speichern Sie den Workflow.
1. Laden Sie eine PDF- oder AI-Datei in [!DNL Experience Manager Assets] hoch. PDF Rasterizer erstellt die Miniaturansichten und Webausgaben für die Datei.
