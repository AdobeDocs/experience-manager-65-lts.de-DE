---
title: Skriptausführung schlägt auf AEM Forms 6.5 LTS mit JBoss EAP 8 (Linux) fehl
description: Beim Einrichten von JBoss EAP 8.0 in einer Linux-Umgebung können beim Ausführen von Shell-Skripten oder Startdateien bestimmte Fehler auftreten
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
exl-id: 4dfaa625-47fa-4681-9e2f-a3bbdca95276
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 1%
---
# Skriptausführung schlägt auf AEM Forms 6.5 LTS mit JBoss EAP 8 (Linux) fehl

## Problem

Beim Einrichten von **JBoss EAP 8.0 (AEM Forms 6.5.1 LTS)** in einer **Linux**-Umgebung kann beim Ausführen von Shell-Skripten oder Startdateien einer der folgenden Fehler auftreten:

```text
/bin/sh^M: bad interpreter
$'\r': command not found
```

Diese Fehler treten auf, wenn Shell-Skripte oder Konfigurationsdateien auf einem **Windows**-System erstellt oder bearbeitet wurden und **CRLF (Carriage Return + Line Feed)** Zeilenenden enthalten.
Linux-Systeme unterstützen nur **LF (Line Feed)** Zeilenenden, und Zeilenenden im Windows-Stil verursachen Fehler bei der Skriptausführung.

## Gilt für

* **JBoss EAP 8.0**
* **Linux/UNIX-basierte Betriebssysteme**

## Schritte zur Fehlerbehebung

1. **Identifizieren Sie die betroffene Datei**

   * Überprüfen Sie die Fehlerausgabe, um das `.sh` Skript oder die Konfigurationsdatei zu identifizieren, das bzw. die den Fehler verursacht.

2. **Konvertieren Sie die Datei in das Unix-Format**

   * Verwenden Sie das Dienstprogramm `dos2unix` , um Zeilenendungen im Windows-Stil in das Unix-Format zu konvertieren:

     ```bash
     dos2unix <file_name>
     ```

   * Ersetzen Sie `<file_name>` durch das Skript oder die Konfigurationsdatei, das/die den Fehler auslöst.

3. **Wiederholen Sie dies bei Bedarf**

   * Wenn mehrere Skripte betroffen sind, wiederholen Sie die Konvertierung für alle relevanten `.sh`-Dateien (z. B. Installationsprogramme, LCM- oder JBoss-Startskripte).

4. **Führen Sie das Skript erneut aus**

   * Führen Sie nach der Konvertierung das Skript erneut aus, um zu bestätigen, dass das Problem behoben ist.

Nach der Konvertierung der Dateien in Unix (LF)-Zeilenenden werden die `/bin/sh^M`- und `$'\r': command not found` behoben und JBoss-Skripte werden unter Linux erfolgreich ausgeführt.
