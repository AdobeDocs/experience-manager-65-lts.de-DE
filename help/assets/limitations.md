---
title: Grenzwerte für Dynamic Media
description: Erfahren Sie mehr über die Best Practices und durchgesetzten Grenzwerte beim Erstellen eines Bildsets oder eines Rotationssets oder beim Hochladen einer PDF. Außerdem erhalten Sie Informationen zu nicht unterstützten Kombinationen von Webbrowsern und Betriebssystemen für Dynamic Media.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/Dynamic-Media-Classic
geptopics: SG_SCENESEVENONDEMAND_PK/categories/ecatalogs
feature: Dynamic Media Classic,Asset Management,Image Sets,Spin Sets,eCatalog
role: User
solution: Experience Manager, Experience Manager Assets
exl-id: 5aa07827-8483-4a99-9197-a17485226a13
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 100%

---

# Grenzwerte für Dynamic Media

In den folgenden Abschnitten werden Grenzwerte für Dynamic Media beschrieben.

Dieses Thema enthält die folgenden Abschnitte:

* [Best Practices und durchgesetzte Grenzwerte in Dynamic Media für Asset-Typen](#best-practice-enforced-limits)
* [Nicht unterstützte Webbrowser- und Betriebssystemkombinationen für Dynamic Media](#unsupported-browser-os)

## Best Practices und durchgesetzte Grenzwerte in Dynamic Media für Asset-Typen {#best-practice-enforced-limits}

Wenn Sie ein Rotationsset oder Bildset erstellen oder PDFs zur Seitenextrahierung hochladen, empfiehlt Adobe die folgenden Best Practices und setzt die folgenden Grenzwerte durch:

| Asset – Art des Grenzwerts | Best Practice | Erzwungene Begrenzung |
| --- | --- | --- |
| **Bild**: Anzahl der smarten Zuschnitte pro Bild | 5 | 100 |
| **Alle Sets**: Anzahl doppelter Assets pro Set | Keine Duplikate | 20‡ |
| **Alle Sets**: Maximale Anzahl von Assets pro Set | 5–10 Bilder pro Set | 1000 |
| **Rotationsset**: Maximale Anzahl von Zeilen/Spalten pro 2D-Set | 12–18 Bilder pro Set | 1000 |
| **PDF**: Maximale Zahl der Seiten für eine PDF-Datei, die für die Extraktion berücksichtigt werden sollen |  | 100 (für alle PDFs) |

‡ Best Practice ist, keine doppelten Assets in einem Satz zu haben. Das Limit beträgt 20 Duplikate für ein einzelnes Asset. Wenn Sie ein weiteres Duplikat für dieses Asset innerhalb dieses Satzes hinzufügen, gibt die Anfrage entweder einen Fehler aus oder ignoriert das Duplikat.
<!-- See also [Dynamic Media limitations](/help/assets/limitations.md). -->

## Nicht unterstützte Webbrowser- und Betriebssystemkombinationen für Dynamic Media {#unsupported-browser-os}

Dynamic Media unterstützt nicht die folgenden Kombinationen aus Webbrowser und Betriebssystem.

* Internet Explorer 11 + Windows 7
* Internet Explorer 11 + Windows 8.1
* Internet Explorer 11 + Windows Phone 8.1
* Internet Explorer 11 + Windows Phone 8.1 Update
* Safari 6 + iOS 6.0.1
* Safari 7 + iOS 7.1
* Safari 7 + OS X 10.9 Mavericks
* Safari 8 + iOS 8.4
* Safari 8 + OS X 10.10 Yosemite

## Ende der Unterstützung für Secure Socket Layer 2.0 und 3.0 und Transport Layer Security 1.0 und 1.1 {#tls}

<!-- CQDOC-19433 (original ticket)
and CQDOC-19792 (removed as per this ticket December 5, 2022) -->

Seit dem 30. April 2024 stellt Adobe Dynamic Media die Unterstützung für Folgendes ein:

* SSL (Secure Socket Layer) 2.0
* SSL 3.0
* TLS (Transport Layer Security) 1.0 und 1.1
* Die folgenden schwachen Verschlüsselungsverfahren in TLS 1.2:
   * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
   * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
   * `TLS_RSA_WITH_AES_256_GCM_SHA384`
   * `TLS_RSA_WITH_AES_256_CBC_SHA256`
   * `TLS_RSA_WITH_AES_256_CBC_SHA`
   * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
   * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
   * `TLS_RSA_WITH_AES_128_GCM_SHA256`
   * `TLS_RSA_WITH_AES_128_CBC_SHA256`
   * `TLS_RSA_WITH_AES_128_CBC_SHA`
   * `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
   * `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
   * `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
   * `TLS_RSA_WITH_SDES_EDE_CBC_SHA`
