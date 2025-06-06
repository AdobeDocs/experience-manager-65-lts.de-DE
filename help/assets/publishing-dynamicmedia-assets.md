---
title: Veröffentlichen von Dynamic Media-Assets
description: Erfahren Sie, wie Sie Dynamic Media-Assets wie Videos und Bilder veröffentlichen, einschließlich der HTTP/2-Bereitstellung solcher Assets.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
role: User, Admin
feature: Publishing
solution: Experience Manager, Experience Manager Assets
exl-id: 7b31db6e-1b3f-4dfe-8b87-8d70548e9c42
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 100%

---

# Veröffentlichen von Dynamic Media-Assets {#publishing-dynamic-media-assets}

Sie veröffentlichen Ihre Dynamic Media-Assets, indem Sie die bereits hochgeladenen Assets auswählen und auf **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL Quick Publish]** tippen. Nach dem Veröffentlichen Ihrer Dynamic Media-Assets können diese über eine URL oder einen Code in eine Web-Seite eingebettet werden.

Sie können hochgeladene Assets auch umgehend und ohne Anwenderinteraktion veröffentlichen. Siehe [Konfigurieren von Dynamic Media – Scene7-Modus](config-dms7.md).
Sie können Assets für Dynamic Media oder Adobe Experience Manager auch selektiv veröffentlichen (sich gegenseitig ausschließend), indem Sie auf der Ordnerebene die Option **[!UICONTROL Selektive Veröffentlichung]** verwenden. Siehe [Arbeiten mit selektiver Veröffentlichung in Dynamic Media](/help/assets/selective-publishing.md).

In der **[!UICONTROL Kartenansicht]** wird ein kleines Globussymbol direkt unter dem Namen eines Assets und links von Datum und Uhrzeit angezeigt, um anzuzeigen, dass es veröffentlicht wurde. In der **[!UICONTROL Listenansicht]** gibt eine Spalte **[!UICONTROL Veröffentlicht]** an, welche Assets veröffentlicht sind.

>[!NOTE]
>
>Angenommen, ein Asset wurde bereits veröffentlicht. Dann verschieben Sie es mit Adobe Experience Manager in einen anderen Ordner und veröffentlichen Sie es von seinem neuen Speicherort erneut. Die ursprüngliche Position des veröffentlichten Assets sowie das neu veröffentlichte Asset sind weiterhin verfügbar. Das ursprünglich veröffentlichte Asset ist allerdings für Experience Manager nicht mehr zugänglich. Daher kann dessen Veröffentlichung nicht rückgängig gemacht werden. Deshalb wird empfohlen, die Veröffentlichung von Assets zunächst rückgängig zu machen, bevor Sie sie in einen anderen Ordner verschieben.

Wenn Sie Video-Assets sofort nach der Kodierung veröffentlichen möchten, achten Sie darauf, dass die Kodierung abgeschlossen ist. Wenn Videos kodiert werden, erhalten Sie eine Systemmeldung, dass ein Videoverarbeitungs-Workflow aktiv ist. Wenn die Videokodierung abgeschlossen ist, können Sie eine Vorschau der Videoausgabedarstellungen anzeigen. Jetzt können Sie die Videos veröffentlichen, ohne dass Publishing-Fehler auftreten.

Siehe auch [Verknüpfen von URLs mit Ihrer Web-Anwendung](linking-urls-to-yourwebapplication.md).

Siehe auch [Einbetten des Dynamic Media- oder Bild-Viewers auf einer Web-Seite](embed-code.md).

>[!NOTE]
>
>* Assets müssen zunächst veröffentlicht werden, bevor Sie die URL verwenden können. Wenn Assets nicht veröffentlicht sind, können Sie die URL nicht kopieren und in einen Webbrowser einfügen.
>* Bild- und Viewer-Vorgaben müssen für die Live-Bereitstellung aktiviert und veröffentlicht sein.
>

Ausführliche Informationen zum Veröffentlichen von Sets oder des Assets finden Sie unter [Veröffentlichen von Assets](manage-assets.md).

## Bereitstellung von Dynamic Media-Assets über HTTP/2 {#http-delivery-of-dynamic-media-assets}

Experience Manager unterstützt jetzt die Bereitstellung aller Dynamic Media-Inhalte (Bilder und Videos) über HTTP/2. Das heißt, dass eine veröffentlichte URL oder ein Einbettungs-Code für ein Bild oder Video verfügbar ist und in beliebige Programme integriert werden kann, die gehostete Assets akzeptiert. Das veröffentlichte Asset wird dann über das HTTP/2-Protokoll bereitgestellt. Diese Bereitstellungsmethode verbessert die Kommunikation von Browsern und Servern, sodass die Antwort- und Ladezeiten aller Dynamic Media-Assets verbessert werden.

Weitere Informationen finden Sie unter [Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ)](/help/sites-administering/scene7-http2faq.md).
