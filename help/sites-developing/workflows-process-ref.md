---
title: Prozessreferenz für Workflows
description: Lesen Sie diese Prozessreferenz für Workflows in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 20fd27e2-0eb7-4fab-a56a-f83816947579
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 100%

---

# Prozessreferenz für Workflows{#workflow-process-reference}

AEM bietet verschiedene Prozessschritte für die Erstellung von Workflow-Modellen. Darüber hinaus können auch benutzerdefinierte Prozessschritte für Aufgaben hinzugefügt werden, die nicht von den integrierten Schritten abgedeckt werden (siehe [Erstellen von Workflow-Modellen](/help/sites-developing/workflows-models.md)).

## Prozessmerkmale {#process-characteristics}

Die folgenden Merkmale werden für jeden Prozessschritt beschrieben.

### Java™-Klasse oder ECMA-Pfad {#java-class-or-ecma-path}

Prozessschritte werden entweder durch eine Java™-Klasse oder ein ECMAScript definiert.

* Für die Java™-Klassenprozesse wird der vollqualifizierte Klassenname angegeben.
* Bei ECMAScript-Prozessen wird der Pfad des Skripts angegeben.

### Payload {#payload}

Die Payload ist die Entität, auf die die Workflow-Instanz reagiert. Die Payload wird implizit durch den Kontext ausgewählt, in dem eine Workflow-Instanz gestartet wird.

Wenn beispielsweise ein Workflow auf die AEM-Seite *P* angewendet wird, durchläuft *P* bei fortlaufendem Workflow die verschiedenen Schritte. Dabei wirkt sich jeder Schritt optional in irgendeiner Weise auf *P* aus.

Meist besteht die Payload aus einem JCR-Knoten im Repository (beispielsweise eine AEM-Seite oder ein AEM-Asset). Eine JCR-Knoten-Payload wird als Zeichenfolge übergeben, die entweder aus einem JCR-Pfad oder einer JCR-Kennung besteht (UUID). Manchmal ist die Payload eine JCR-Eigenschaft (sie wird dann als JCR-Pfad übergeben), eine URL, ein Binärobjekt oder ein generisches Java™-Objekt. Einzelne Prozessschritte, die auf die Payload reagieren, erwarten in der Regel einen bestimmten Typ Payload oder verhalten sich je nach Payload-Typ anders. Der erwartete Payload-Typ (falls vorhanden) wird für jeden der unten beschriebenen Prozesse angegeben.

### Argumente {#arguments}

Einige Workflow-Prozesse akzeptieren Argumente, die die Administratorin oder der Administrator beim Einrichten des Workflow-Schritts angibt.

Argumente werden als einzelne Zeichenfolge im Bereich **Eigenschaften** des Workflow-Editors in der Eigenschaft **Prozess-Argumente** angegeben. Das Format der Argumentzeichenfolge wird für jeden unten beschriebenen Prozess in einfacher EBNF-Grammatik angegeben. Im folgenden Beispiel besteht die Argumentzeichenfolge aus einem oder mehreren durch Kommas getrennten Paaren. Jedes Paar besteht aus einem Namen (einer Zeichenfolge) und einem Wert, die durch einen zweifachen Doppelpunkt getrennt werden:

```
    args := name '::' value [',' name '::' value]*
    name := /* A string */
    value := /* A string */
```


### Maximale Wartezeit {#timeout}

Nach dieser maximalen Wartezeit funktioniert der Workflow-Schritt nicht mehr. Einige Workflow-Prozesse respektieren die maximale Wartezeit, für andere gilt sie nicht und wird daher ignoriert.

### Berechtigungen {#permissions}

Die Sitzung, die an den `WorkflowProcess` übergeben wird, wird durch den Dienstbenutzer für den Workflow-Prozessdienst gestützt, der über folgende Berechtigungen am Stamm des Repositorys verfügt:

* `jcr:read`
* `rep:write`
* `jcr:versionManagement`
* `jcr:lockManagement`
* `crx:replicate`

Wenn dieser Berechtigungssatz nicht ausreichend für die `WorkflowProcess`-Implementierung ist, muss auf eine Sitzung mit den erforderlichen Berechtigungen zurückgegriffen werden.

Hierfür wird empfohlen, eine Dienstbenutzerin oder einen Dienstbenutzer mit einer minimalen Teilmenge der erforderlichen Berechtigungen einzusetzen.

>[!CAUTION]
>
>Wenn Sie ein Upgrade von einer früheren Version auf AEM 6.2 durchführen, müssen Sie möglicherweise auch Ihre Implementierung aktualisieren.
>
>In den vorherigen Versionen wurde die Adminsitzung an die `WorkflowProcess`-Implementierungen übergeben. Danach war der uneingeschränkte Zugriff auf das Repository ohne Definition der spezifischen ACLs möglich.
>
>Die Berechtigungen werden nun wie oben dargestellt definiert ([Berechtigungen](#permissions)). Dasselbe gilt für die empfohlene Methode zum Aktualisieren Ihrer Implementierung.
>
>Wenn Code-Änderungen nicht praktikabel sind, steht eine kurzfristige Lösung für die Abwärtskompatibilität zur Verfügung:
>
>* Öffnen Sie die Web-Konsole (`/system/console/configMgr`) und suchen Sie nach dem **Adobe Granite Workflow-Konfigurationsdienst**.
>
>* Aktivieren Sie den **Legacymodus des Workflow-Prozesses**.
>
>Dadurch wird das bisherige Verhalten wieder aktiviert, nach dem eine Adminsitzung an die `WorkflowProcess`-Implementierung übergeben und wieder uneingeschränkter Zugriff auf das gesamte Repository eingeräumt wird.

## Workflow-Steuerungsprozesse {#workflow-control-processes}

Die folgenden Prozesse wirken sich nicht auf Inhalte aus. Sie dienen der Steuerung des Workflows.

### AbsoluteTimeAutoAdvancer (automatisches Voranschreiten für absolute Uhrzeit) {#absolutetimeautoadvancer-absolute-time-auto-advancer}

Der Prozess `AbsoluteTimeAutoAdvancer` (automatisches Voranschreiten für absolute Uhrzeit) verhält sich wie **AutoAdvancer**. Ausnahme ist, dass die Zeitüberschreitung nach einer bestimmten Zeit und einem gewissen Datum anstelle einer entsprechenden Dauer eintritt.

* **Java™-Klasse**: `com.adobe.granite.workflow.console.timeout.autoadvance.AbsoluteTimeAutoAdvancer`
* **Payload**: Keine.
* **Argumente**: Keine.
* **Zeitüberschreitung**: Zeitüberschreitung nach festgelegter Zeit und festgelegtem Datum.

### AutoAdvancer (Auto-Advancer) {#autoadvancer-auto-advancer}

Der `AutoAdvancer`-Prozess bringt den Workflow automatisch zum nächsten Schritt. Falls mehr als nur ein nächster Schritt möglich ist (beispielsweise bei einer ODER-Teilung), bringt der Prozess den Workflow auf der *Standardroute* voran. Wurde keine Standardroute festgelegt, wird der Workflow nicht vorangebracht.

* **Java™-Klasse**: `com.adobe.granite.workflow.console.timeout.autoadvance.AutoAdvancer`

* **Payload**: Keine.
* **Argumente**: Keine.
* **Zeitüberschreitung**: Nach einem festgelegtem Zeitraum.

### ProcessAssembler (Prozess-Assembler) {#processassembler-process-assembler}

Der `ProcessAssembler`-Prozess führt mehrere Teilprozesse nacheinander in einem einzigen Workflow-Schritt aus. Erstellen Sie für die Nutzung des `ProcessAssembler` einen einzelnen entsprechenden Schritt im Workflow und legen Sie die Argumente so fest, dass sie die Namen und Argumente der auszuführenden Teilprozesse angeben.

* **Java™-Klasse**: `com.day.cq.workflow.impl.process.ProcessAssembler`

* **Payload**: DAM-Asset, AEM-Seite oder keine Payload (je nach Anforderungen der Teilprozesse).
* **Argumente**:

```
        args := arg [',' arg]
        arg := processname ['::' processargs]
        processname := /* A fully qualified Java Class or absolute
        repository path to an ECMAScript */
        processargs := processarg [';' processarg]*
        processarg := '[' nobracketprocessarg ']' | nobracketprocessarg
        nobracketprocessarg := listitem [':' listitem]*
        listitem := /* A string */
```

* **Zeitüberschreitung**: Berücksichtigt.

Beispiel:

* Extrahieren Sie die Metadaten des Assets.
* Erstellen Sie drei Miniaturansichten der drei angegebenen Größen.
* Erstellen Sie ein JPEG-Bild aus dem Asset, vorausgesetzt, das Asset ist ursprünglich weder eine GIF- noch eine PNG-Datei (in diesem Fall wird kein JPEG-Bild erstellt).
* Legen Sie das Datum der letzten Änderung für das Asset fest.

```shell
com.day.cq.dam.core.process.ExtractMetadataProcess,
    com.day.cq.dam.core.process.CreateThumbnailProcess::[140:100];[48:48];[319:319:false],
    com.day.cq.dam.core.process.CreateWebEnabledImageProcess::dimension:1280:1280;mimetype:image/jpeg,
    com.day.cq.dam.core.process.AssetSetLastModifiedProcess
```

## Grundlegende Prozesse {#basic-processes}

Die folgenden Prozesse führen einfache Aufgaben durch oder dienen als Beispiel.

>[!CAUTION]
>
>Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen.
>
>da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal upgraden. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)

### Löschen Sie {#delete}

Das Element unter dem angegebenen Pfad wird gelöscht.

* **ECMA-Skript-Pfad**: `/libs/workflow/scripts/delete.ecma`

* **Payload**: JCR-Pfad
* **Argumente**: Keine
* **Zeitüberschreitung**: Ignoriert

### noop {#noop}

Dies ist der Null-Prozess. Es wird kein Vorgang ausgeführt, jedoch eine Debugmeldung protokolliert.

* **ECMA-Skript-Pfad**: `/libs/workflow/scripts/noop.ecma`

* **Payload**: Keine
* **Argumente**: Keine
* **Zeitüberschreitung**: Ignoriert

### rule-false {#rule-false}

Dies ist ein Null-Prozess, der `false` für die `check()`-Methode zurückgibt.

* **ECMA-Skript-Pfad**: `/libs/workflow/scripts/rule-false.ecma`

* **Payload**: Keine
* **Argumente**: Keine
* **Zeitüberschreitung**: Ignoriert

### Beispiel {#sample}

Dies ist ein Beispiel für einen ECMAScript-Prozess.

* **ECMA-Skript-Pfad**: `/libs/workflow/scripts/sample.ecma`

* **Payload**: Keine
* **Argumente**: Keine
* **Zeitüberschreitung**: Ignoriert

### LockProcess {#lockprocess}

Sperrt die Payload des Workflows.

* **Java™-Klasse:** `com.day.cq.workflow.impl.process.LockProcess`

* **Payload:** JCR_PATH und JCR_UUID
* **Argumente**: Keine
* **Zeitüberschreitung:** Ignoriert

Unter folgenden Bedingungen ist der Schritt nicht wirksam:

* Die Payload wurde bereits gesperrt
* Der Payload-Knoten enthält keinen untergeordneten jcr:content-Knoten

### UnlockProcess {#unlockprocess}

Entsperrt die Payload des Workflows.

* **Java™-Klasse:** `com.day.cq.workflow.impl.process.UnlockProcess`

* **Payload:** JCR_PATH und JCR_UUID
* **Argumente**: Keine
* **Zeitüberschreitung:** Ignoriert

Unter folgenden Bedingungen ist der Schritt nicht wirksam:

* Die Payload wurde bereits entsperrt
* Der Payload-Knoten enthält keinen untergeordneten jcr:content-Knoten

## Versionierungsprozesse {#versioning-processes}

Der folgende Prozess führt eine versionsbezogene Aufgabe aus.

### CreateVersionProcess {#createversionprocess}

Erstellt eine Version der Workflow-Payload (AEM-Seite oder DAM-Asset).

* **Java™-Klasse**: `com.day.cq.wcm.workflow.process.CreateVersionProcess`

* **Payload**: JCR-Pfad oder UUID, der auf eine Seite oder ein DAM-Asset verweist
* **Argumente**: Keine
* **Zeitüberschreitung**: Berücksichtigt
