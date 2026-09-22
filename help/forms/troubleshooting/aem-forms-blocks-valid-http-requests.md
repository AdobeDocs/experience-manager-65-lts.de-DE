---
title: AEM Forms blockiert gültige HTTP-Anfragen
description: XSS-Validierungsprüfungen in AEM Forms können gültige HTTP-Anfragen für Kunden blockieren, die benutzerdefinierte Komponenten verwenden. Erfahren Sie, wie Sie das Problem identifizieren und die Validierungsprüfungen vorübergehend lockern können.
solution: Experience Manager, Experience Manager Forms
feature: Security
role: Admin,Developer
exl-id: 10a02e57-7ff8-42d8-b31e-f714c0dd8338
source-git-commit: 4df5a9888532afd86562678a76c35841ac5634b8
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 8%
---
# AEM Forms blockiert gültige HTTP-Anfragen {#aem-forms-blocks-valid-http-requests}

## Problem {#issue}

AEM Forms umfasst Sicherheitsprüfungen, um Cross-Site-Scripting-Angriffe (XSS) zu verhindern. Diese Prüfungen können einige gültige HTTP-Anfragen für Kunden blockieren, die benutzerdefinierte Komponenten in AEM Forms verwenden. Wenn eine Anfrage blockiert wird, wird die folgende Meldung in den Serverprotokollen angezeigt:

```text
Got Exception while Validating XSS: HTTP parameter name: params[browserLocale]: Invalid input. Please conform to regex ^[a-zA-Z0-9_]{1,32}$ with a maximum length of 2000: org.owasp.esapi.errors.ValidationException: HTTP parameter name: params[browserLocale]: Invalid input. Please conform to regex ^[a-zA-Z0-9_]{1,32}$ with a maximum length of 2000.
```

>[!NOTE]
>
>Bei einer POST-Anfrage ist der Standardwert für den -Parameter **1048576**. Bei einer GET-Anfrage ist der Standardwert für den Parameter **2000**. Um den Parameterwert für eine POST-Anfrage zu ändern, übergeben Sie das `com.adobe.idp.dsc.provider.rest.httpParamMaxSize`-Argument beim Serverstart.

## Ursache {#cause}

Der XSS-Validierungs-Regex ist strenger als das Format des Parameterwerts, der von der benutzerdefinierten Komponente gesendet wird. Daher lehnt AEM Forms die Anfrage ab.

## Auflösung {#resolution}

>[!CAUTION]
>
>Das Entfernen der Sicherheitsprüfungen macht das System anfällig für Cross-Site-Scripting-Angriffe (XSS). Entfernen Sie die Sicherheitsprüfungen nur als temporäre Lösung.

So entfernen Sie die Sicherheitsprüfungen vorübergehend und lassen alle HTTP-Anfragen zu:

1. Stoppen Sie den AEM Forms-Server.

1. Erstellen Sie eine Sicherung der `[AEM-Forms-Installation-Directory]/configurationManager/export/adobe-livecycle-<application_server_name>.ear`.

1. Extrahieren Sie die `esapi-helper-2.x.x.jar` aus der `adobe-livecycle-<server_name>.ear`. Der Speicherort der `esapi-helper-2.x.x.jar`-Datei variiert je nach Anwendungsserver:

   | Anwendungs-Server | Speicherort der Datei esapi-helper-2.x.x.jar |
   | --- | --- |
   | JBoss | `adobe-livecycle-jboss.ear/lib` |
   | Oracle WebLogic | `adobe-livecycle-weblogic.ear/APP-INF/lib` |
   | IBM WebSphere | `adobe-livecycle-websphere.ear/` |

1. Öffnen Sie die `[extracted esapi-helper-2.x.x.jar]/esapi/validation.properties` und `[extracted esapi-helper-2.x.x.jar]/esapi/ESAPI.properties` Sie Dateien zur Bearbeitung.

1. Legen Sie den Wert der folgenden Eigenschaften auf `^[\\s\\S]*$` fest. Zum Beispiel: `Validator.HTTPParameterName=^[\\s\\S]*$`. Speichern und schließen Sie die Dateien.

   * `Validator.HTTPQueryString`
   * `Validator.PMCallParameterName`
   * `Validator.PMCallParameterValue`
   * `Validator.HTTPParameterName`
   * `Validator.HTTPParameterValue`
   * `Validator.xssSafeString`

1. Verpacken Sie die aktualisierten `esapi-helper-2.x.x.jar` in `adobe-livecycle-<application_server_name>.ear`. Stellen Sie die aktualisierte `adobe-livecycle-<application_server_name>.ear` auf dem Anwendungsserver bereit.

1. Starten Sie den AEM Forms-Server.

## Referenz {#references}

* [Beheben von SSRF-Schwachstellen (Server-Side Request Forgery) für AEM Forms on JEE 6.5 LTS SP2](/help/forms/troubleshooting/mitigating-server-side-request-forgery-vulnerabilities-for-aem-forms-on-jee-65-lts-sp2.md)
