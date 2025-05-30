---
title: Bereitstellen von Dynamic Media-Assets
description: Erfahren Sie, wie Sie Dynamic Media-Assets wie Videos und Bilder auf Ihren Web-Seiten bereitstellen.
role: User, Admin
feature: Asset Management,Renditions
solution: Experience Manager, Experience Manager Assets
exl-id: b91173b4-f1d1-4aad-97d2-782bc8aeaeab
source-git-commit: 47b82956b41c3f78bed5ae220c7e993ce29e0385
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 100%

---

# Bereitstellen von Dynamic Media-Assets{#delivering-dynamic-media-assets}

Wie Sie Dynamic Media-Assets (sowohl Videos als auch Bilder) bereitstellen können, ist davon abhängig, wie Ihre Website implementiert ist.

Mit Dynamic Media haben Sie mehrere Optionen:

* Wenn Ihre Website auf Adobe Experience Manager gehostet wird, können Sie die Dynamic Media-Assets direkt zu Ihrer Seite hinzufügen.
* Wenn sich Ihre Website nicht in Experience Manager befindet, können Sie eine der folgenden Aktionen ausführen:

   * Einbetten Ihrer Videos oder Bilder auf Ihrer Website.
   * Verknüpfen Sie URLs mit Ihrer Web-Anwendung. Verwenden Sie die Verknüpfung, wenn Sie einen Video-Player als Popup- oder modales Fenster bereitstellen möchten.
   * Wenn Ihre Website dynamisch ist, können Sie [optimierte Bilder bereitstellen](/help/assets/responsive-site.md).

>[!NOTE]
>
>Die intelligente Bildbearbeitung arbeitet mit bestehenden Bildvorgaben und reduziert im letzten Moment abhängig vom Browser oder der Geschwindigkeit der Netzverbindung die Größe der Bilddatei intelligent noch weiter. Weitere Informationen finden Sie unter [Intelligente Bildbearbeitung](/help/assets/imaging-faq.md).

Weitere Informationen finden Sie in den folgenden Themen:

* [Hinzufügen von Dynamic Media-Assets zu Web-Seiten](/help/assets/adding-dynamic-media-assets-to-pages.md)
* [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/embed-code.md)
* [Aktivieren des Hotlink-Schutzes in Dynamic Media](/help/assets/hotlink-protection.md)
* [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/linking-urls-to-yourwebapplication.md)
* [Bereitstellen optimierter Bilder für eine responsive Website](/help/assets/responsive-site.md)
* [Bereitstellung von Inhalten per HTTP/2](/help/assets/http2.md)
* [Verwenden von Regelsätzen zum Konvertieren von URLs](/help/assets/using-rulesets-to-transform-urls.md)

## Bereitstellung von Dynamic Media-Assets über HTTP/2 {#http-delivery-of-dynamic-media-assets}

Experience Manager unterstützt jetzt die Bereitstellung aller Dynamic Media-Inhalte (Bilder und Videos) über HTTP/2. Das heißt, dass eine veröffentlichte URL oder ein Einbettungs-Code für ein Bild oder Video verfügbar ist und in beliebige Programme integriert werden kann, die gehostete Assets akzeptiert. Das veröffentlichte Asset wird dann über das HTTP/2-Protokoll bereitgestellt. Diese Bereitstellungsmethode verbessert die Kommunikation von Browsern und Servern, sodass die Antwort- und Ladezeiten aller Dynamic Media-Assets verbessert werden.

Weitere Informationen finden Sie unter [Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ)](/help/sites-administering/scene7-http2faq.md).
