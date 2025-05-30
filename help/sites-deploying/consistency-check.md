---
title: Konsistenz- und Durchlaufprüfungen
description: Erfahren Sie, wie Sie Konsistenz- und Ausnahmeprüfungen durchführen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
feature: Configuring
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 6ed130d5-30b5-4864-8bea-dfe41bed5422
source-git-commit: 408f6aaedd2cc0315f6e66b83f045ca2716db61d
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 100%

---

# Konsistenz- und Durchlaufprüfungen{#consistency-and-traversal-checks}

Beim Aktualisieren können aufgrund von Arbeitsbereichsinkonsistenzen Probleme auftreten. Sie können eine Testaktualisierung ausführen, um anzuzeigen, ob dies ein Problem darstellt, oder Konsistenzüberprüfungen als Präventivmaßnahme ausführen.

Wenn Sie eine Testaktualisierung ausführen, die aufgrund von Arbeitsbereichsinkonsistenzen fehlschlägt, werden in der Datei „crx-quickstart/logs/crx/error.log“ Einträge angezeigt, die den folgenden ähneln:

```xml
*ERROR* TarPersistenceManager: No bundle found for uuid 'deadbeef-cafe-babe-cafe-babecafebabe'
 ...
*ERROR* RepositoryImpl: Failed to initialize workspace 'crx.default'
javax.jcr.RepositoryException: Error indexing workspace: Error indexing workspace: Error indexing workspace
...
```

## Ausführen einer Konsistenzüberprüfung {#perform-a-consistency-check}

Navigieren Sie zum Ausführen einer Konsistenzüberprüfung zur Verwaltungsseite für das JMX MBean **com.adobe.granite (Repository)**. Wechseln Sie auf dem AEM-Hauptbildschirm zu:

**Tools > Webkonsole > Haupt (auf der Menüleiste) > JMX > com.adobe.granite (Repository)**

In einer Standardinstallation befindet er sich hier: **[|Anzeigen|](http://localhost:4502/system/console/jmx/com.adobe.granite%3Atype%3DRepository)**

Im Abschnitt **Vorgänge** der Seite finden Sie zwei Methoden: **`traversalCheck`** und **`consistencyCheck`**.  Klicken Sie zum Ausführen einer Überprüfung auf den Vorgang und geben Sie die gewünschten Parameter ein.

![chlimage_1-117](assets/chlimage_1-117.png)
