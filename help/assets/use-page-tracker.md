---
title: Seitenverfolgung und Einbettungs-Code in Web-Seiten verwenden
description: Erfahren Sie mehr über das Einbinden der Seitenverfolgung und das Einbetten von JavaScript-Codes in Ihren Website-Code, damit Adobe Analytics Nutzungsdaten zu Assets erfassen kann.
contentOwner: AG
role: Architect, Admin
feature: Asset Reports
solution: Experience Manager, Experience Manager Assets
exl-id: bf8b2e51-60f8-423e-8ed6-167d71d6ec94
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 100%

---

# Seitenverfolgung und Einbettungs-Code in Web-Seiten verwenden {#using-page-tracker-and-embed-code-in-web-pages}

Die Seitenverfolgung ist Teil des JavaScript-Codes, den Sie in Code von Drittanbieter-Websites einbinden, damit Adobe Analytics Nutzungsdaten rund um [!DNL Adobe Experience Manager Assets] auf diesen Websites erfassen kann.

Um Ereignisse wie z. B. Klicks zu erfassen, die spezifisch für ein Asset sind, fügen Sie den Einbettungs-Code auch in den Code von Websites Dritter ein.

Der folgende Beispiel-Code veranschaulicht, wie eine Web-Seite aussieht, die sowohl den Seitenverfolgungs-Code als auch Einbettungs-Code enthält:

```html
<!DOCTYPE html>
<html>
    <head>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/sitecatalyst/appmeasurement.js"></script>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/assetinsights/pagetracker.js"></script>
            <script type="text/javascript">
                                assetAnalytics.attrTrackable = 'trackable';
                assetAnalytics.defaultTrackable = false;
                assetAnalytics.attrAssetID = 'aem-asset-id';
                assetAnalytics.assetImpressionPollInterval = 200; // interval in milliseconds
                assetAnalytics.charsLimitForGET = 2000; // bytes
                assetAnalytics.dispatcher.init("assetstesting","xxxx","xxx","list1","eVar3","event8","event7");
            </script>

    </head>

    <body>

                                <img
            src="https://10.41.52.147:4502/xxxx/content/dam/test/abc.jpg"
            data-aem-asset-id="aaid:a386f2cd78234becb66bd11575f9452d"
            data-trackable=true
            onload=assetAnalytics.core.assetLoaded(this)>

        <a
            href="https://www.adobe.com"

            onclick="assetAnalytics.core.assetClicked(this);return false">
                <img
                    src="http://localhost/xxxx/content/dam/test/xyz.jpg"
                    data-aem-asset-id="aaid:7fa01fce0ebe40268cd6dcf07e2d9cb1"
                    data-trackable=true
                    onload=assetAnalytics.core.assetLoaded(this)>
        </a>

    </body>
</html>
```

## Seitenverfolgungs-Code hinzufügen {#adding-page-tracker-code}

Sie fügen den Seitenverfolgungs-Code in der Kopfzeile des Website-Codes hinzu. Das folgende Code-Beispiel zeigt den Seitenverfolgungs-Code, der in einer Beispiel-Web-Seite enthalten ist:

```xml
 <head>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/sitecatalyst/appmeasurement.js"></script>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/foundation/assetinsights/pagetracker.js"></script>
            <script type="text/javascript">
                                assetAnalytics.attrTrackable = 'trackable';
                assetAnalytics.defaultTrackable = false;
                assetAnalytics.attrAssetID = 'aem-asset-id';
                assetAnalytics.assetImpressionPollInterval = 200; // interval in millis
                assetAnalytics.charsLimitForGET = 2000; // bytes
                assetAnalytics.dispatcher.init("assetstesting","abc.net","bee","list1","eVar3","event8","event7");
            </script>

 </head>
```

## Einbettungs-Code hinzufügen {#add-embed-code}

Sie können Einbettungs-Code im Hauptteil des Website-Codes hinzufügen. Das folgende Code-Beispiel zeigt den Einbettungs-Code, der in einer Web-Seite enthalten ist:

```xml
<body>

      <img
            src="http://localhost:4502/xxxx/content/dam/test/xyz.jpg"
            data-aem-asset-id="aaid:a386f2cd78234becb66bd11575f9452d"
            data-trackable=true
            onload=assetAnalytics.core.assetLoaded(this)>

        <a
            href="https://www.adobe.com"

            onclick="assetAnalytics.core.assetClicked(this);return false">
           <img
                    src="http://localhost:4502/xxxx/content/dam/test/xyz.jpg"
                    data-aem-asset-id="aaid:7fa01fce0ebe40268cd6dcf07e2d9cb1"
                    data-trackable=true
                    onload=assetAnalytics.core.assetLoaded(this)>
        </a>

    </body>
```
