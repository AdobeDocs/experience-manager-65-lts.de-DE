---
title: Arbeiten mit Protokollen
description: Erfahren Sie, wie Sie mithilfe von Protokollen eine Fehlerbehebung in AEM durchführen können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
exl-id: f286ca06-e567-4d77-a0ff-6786a8bbf32a
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: 5ef752af-d616-5b23-8312-06964e46b208
    internal-label: Administering
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 100%
---
# Arbeiten mit Protokollen{#working-with-logs}

Dieser Abschnitt enthält detaillierte Informationen zu den verfügbaren Protokollen, die Ihnen bei der Fehlerbehebung helfen.

>[!NOTE]
>
>Weitere Informationen zu Protokollen finden Sie unter:
>
>* [Auditprotokollwartung in AEM](/help/sites-administering/operations-audit-log.md)
>* [Arbeiten mit Auditeinträge und Protokolldateien](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files)

CRX zeichnet detaillierte Protokolle auf. Nachdem Sie den Schnellstart entpackt und gestartet haben, finden Sie die Protokolle an den folgenden Speicherorten:

* crx-quickstart/launchpad/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## Aktivieren der DEBUG-Protokollebene {#activating-the-debug-log-level}

Die standardmäßige Protokollebene ist INFO, DEBUG-Meldungen werden also nicht protokolliert.

Zum Aktivieren der DEBUG-Protokollebene stellen Sie mit dem CRX-Explorer die Eigenschaft

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

auf „debug“ ein. Lassen Sie die DEBUG-Protokollebene nicht länger als notwendig aktiviert, da hierdurch zahlreiche Protokolle generiert werden.

Eine Zeile in der Debugdatei beginnt gewöhnlich mit DEBUG, gefolgt von der Angabe der Protokollebene, der Aktion des Installationsprogramms und der Protokollmeldung. Zum Beispiel:

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

Die Protokollebenen lauten wie folgt:

| 0 | Schwerwiegender Fehler | Die Aktion ist fehlgeschlagen und das Installationsprogramm kann nicht fortgesetzt werden. |
|---|---|---|
| 1 | Fehler | Die Aktion ist fehlgeschlagen. Die Installation wird fortgesetzt, aber ein CRX-Teil wurde nicht ordnungsgemäß installiert und funktioniert daher nicht. |
| 2 | Warnung | Die Aktion war erfolgreich, stieß aber auf Probleme. CRX funktioniert ggf. nicht ordnungsgemäß. |
| 3 | Informationen | Die Aktion war erfolgreich. |

## Ausführliche Option „verbose“ zur Fehlerbehebung {#verbose-option-used-for-troubleshooting}

Beim Starten von CRX können Sie der Befehlszeile die Option „- v“ (verbose, ausführlich) hinzufügen. Beispiel:

` java -jar crx-<*version*>-<*edition*>.jar -v`

Verwenden Sie die ausführliche Option „verbose“ zur Fehlerbehebung, da damit einige der Schnellstart-Protokollausgaben in der Konsole angezeigt werden.
