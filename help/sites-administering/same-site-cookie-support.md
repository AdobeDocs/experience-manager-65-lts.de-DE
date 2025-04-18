---
title: Same-Site-Cookie-Unterstützung für AEM 6.5
description: Erfahren Sie mehr über Same-Site-Cookie-Unterstützung für AEM 6.5
topic-tags: security
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
exl-id: 8232d8a9-6df4-45f9-8924-7328a55093cb
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 100%

---

# Same-Site-Cookie-Unterstützung für AEM 6.5 {#same-site-cookie-support-for-aem-65}

Seit Version 80 ist in Chrome und Safari ein neues Modell für die Sicherheit von Cookies enthalten. Dieser Modus führt mittels der Einstellung `SameSite` Sicherheitskontrollen für Cookies auf Drittanbieter-Sites ein. Weitere Informationen finden Sie in [diesem web.dev-Artikel, wo SameSite-Cookies erklärt werden](https://web.dev/samesite-cookies-explained/).

Der Standardwert dieser Einstellung (`SameSite=Lax`) kann dazu führen, dass die Authentifizierung zwischen AEM-Instanzen oder -Services nicht funktioniert. Dies liegt daran, dass die Domains oder URL-Strukturen dieser Services möglicherweise nicht unter die Beschränkungen dieser Cookie-Richtlinie fallen.

Um dies zu umgehen, müssen Sie das Cookie-Attribut `SameSite` für das Login-Token auf `None` setzen.

>[!CAUTION]
>
>Die Einstellung `SameSite=None` wird nur angewendet, wenn das Protokoll sicher ist (HTTPS).
>
>Wenn das Protokoll nicht sicher (HTTP) ist, wird die Einstellung ignoriert und der Server zeigt diese Warnmeldung:
>
>`WARN com.day.crx.security.token.TokenCookie Skip 'SameSite=None'`

Sie können die Einstellung mit den nachfolgenden hinzufügen:

1. Wechseln Sie zur Web-Konsole unter `http://serveraddress:serverport/system/console/configMgr`
1. Suchen Sie nach dem **Adobe Granite Token Authentication Handler** und klicken Sie darauf.
1. Legen Sie das **SameSite-Attribut für das Cookie des Anmelde-Tokens** auf `None` fest, wie in der Abbildung unten dargestellt.
   ![samesite](assets/samesite1.png)
1. Klicken Sie auf „Speichern“.
1. Sobald diese Einstellung aktualisiert wurde und Benutzer sich abgemeldet und erneut angemeldet haben, ist für `login-token`-Cookies das `None`-Attribut festgelegt und sie sind in den Site-übergreifenden Anforderungen enthalten.
