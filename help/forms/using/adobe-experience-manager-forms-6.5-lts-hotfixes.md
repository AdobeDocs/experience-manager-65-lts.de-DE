---
title: Adobe Experience Manager Forms 6.5 LTS SP1 Hotfixes
description: Enthält Informationen zum Herunterladen und Installieren eines Hotfixes für AEM Forms 6.5 LTS.
exl-id: 37287332-3c8d-4ddc-a77e-3c5ee332898b
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: fbe90ee89a2c20496800b545ec5637e829e7c7d7
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 45%

---

# Hotfixes für Adobe Experience Manager Forms 6.5 LTS{#aem-form-hotfix}

In diesem Artikel werden die wichtigen Korrekturen aufgeführt, die implementiert wurden, um bekannte Probleme zu beheben, die Systemstabilität zu verbessern und die Gesamtleistung von AEM Forms 6.5 LTS zu verbessern.

>[!NOTE]
>
> Die Hotfixes sind kumulativ konzipiert und umfassen alle vorherigen Fehlerbehebungen. Wenn Sie das neueste Hotfix auf eine Version anwenden, wird nicht nur das jüngste Problem behoben, sondern das Hotfix enthält auch alle vorherigen Fehlerbehebungen und Verbesserungen.

## Hotfixes für AEM Forms 6.5 LTS {#hotfix-for-aem-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Datum</strong></td>
    <td><strong>Hotfix-Downloadlink (AEM Software Distribution-Link)</strong></td>
    <td><strong>Behobene Probleme</strong></td>
  </tr>
  <tr>
    <td>
      <strong>9. September 2025</strong><br>
    <td>
    <ul>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[…]1-hotfix-on-add-on/adobe-aemfd-win-pkg-6.1.176-RHF-002.zip">Hotfix2 für AEM Service Pack 6.5 LTS unter Windows</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[…]hotfix-on-add-on/adobe-aemfd-linux-pkg-6.1.176-RHF-002.zip">Hotfix2 für AEM Service Pack 6.5 LTS unter Linux</a></li>
     <li>MacOS- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[…]1-hotfix-on-add-on/adobe-aemfd-osx-pkg-6.1.176-RHF-002.zip">Hotfix2 für AEM Service Pack 6.5 LTS auf MacOS</a></li>
    <td>
    <ul>
    <li>Die Zuverlässigkeit der Formularübermittlung wurde verbessert, indem ein Problem behoben wurde, bei dem Übermittlungen fehlschlagen können, wenn die Server-seitige Validierung (SSV) aktiviert war. Wenn Probleme auftreten, wenden Sie sich an den [Adobe Experience Manager Forms-Support](https://business.adobe.com/in/support/main.html).
    </li>
    </ul>
    </td>    
  </tr>
    </ul>
    </td>    
  </tr>
  <tbody>
</table>

## Herunterladen und Installieren eines OSGi-Hotfixes {#download-install-hotfix}

Führen Sie die folgenden Schritte aus, um das Hotfix herunterzuladen und zu installieren:

1. Laden Sie das [Hotfix](#hotfix-for-adaptive-forms) über den Software Distribution-Link herunter.
1. Extrahieren Sie die Hotfix-Archivdatei, damit Sie ein Experience Manager-Paket (.zip) und Bundle-Dateien (.jar) abrufen können.
1. Laden Sie das Paket (.zip) über den [Paket-Manager](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=de#accessing) hoch und installieren Sie es.
1. Öffnen Sie die Bundles des Konfigurations-Managers `https://server:host/system/console/bundles`, laden Sie sie hoch und installieren Sie das Bundle (.jar). Das Hotfix wird installiert.
