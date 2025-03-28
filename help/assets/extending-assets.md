---
title: Anpassen und Erweitern von  [!DNL Assets]
description: Informieren Sie sich, wie Sie die Asset-Freigabe und den Asset-Editor anpassen und erweitern können, um Benutzern eine maßgeschneiderte Oberfläche und passende Funktionen zur Verfügung zu stellen.
contentOwner: AG
role: Developer
feature: Developer Tools
solution: Experience Manager, Experience Manager Assets
exl-id: d4826314-a714-47b2-bf4d-029dc47982ce
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 100%

---

# Anpassen und Erweitern von [!DNL Assets] {#customizing-and-extending-assets}

Der Asset-Editor ist der primäre Zugangspunkt, den Benutzende einer Adobe Enterprise Manager-Website verwenden, um die digitalen Assets in Ihrem Repository zu suchen, anzuzeigen und zu bearbeiten.

Als [!DNL Experience Manager]-Entwicklerin oder -Entwickler können Sie den Asset-Editor auf mehrere Arten anpassen und erweitern und Benutzenden eine maßgeschneiderte Oberfläche und passende Funktionen zur Verfügung stellen.

Die folgenden Funktionen können angepasst bzw. verbessert werden:

* [Erweitern des Asset-Editors](asseteditorx.md)
* [Erweitern der Asset-Suche](searchx.md)
* [Verarbeiten von Assets mithilfe von Medien-Handlern und Workflows](media-handlers.md)
* [Integrieren von Assets in den Aktivitäts-Stream](extending-activity-stream.md)
* [Entwicklung von Asset-Proxys](proxy.md)
* [Best Practices zum Konfigurieren von ImageMagick](best-practices-for-imagemagick.md)

## Anpassen des Erscheinungsbilds {#customizing-the-look-and-feel}

Die folgenden Aspekte des Erscheinungsbilds des Asset-Editors sind anpassbar:

* Logo: Sie können das Logo Ihrer Organisation zur Benutzeroberfläche hinzufügen.
* Farben und Schriftarten: Sie können die Farben und Schriftarten ändern, die in der Benutzeroberfläche verwendet werden.
* HTML-Code: Zur besseren Anpassung können Sie den zugrunde liegenden HTML-Code ändern, der die Benutzeroberflächen definiert.

## Anpassen von Ausgabedarstellungen {#customizing-renditions}

In der [!DNL Experience Manager Assets]-Terminologie ist ein Ausgabeformat die Form, in der ein Asset dargestellt wird. Im Allgemeinen kann ein Asset mehrere Ausgabedarstellungen haben.  Z. B. kann ein Farbbild in seiner Originalgröße ausgegeben, verkleinert oder verkleinert und in Graustufen konvertiert sein.

Die Ausgabedarstellungen, in denen ein bestimmtes Asset verfügbar ist, können angepasst werden und es können neue Ausgabedarstellungen erstellt werden.
