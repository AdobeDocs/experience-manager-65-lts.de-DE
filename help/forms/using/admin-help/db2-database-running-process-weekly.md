---
title: 'DB2&reg;-Datenbank: Einen Prozess wöchentlich ausführen'
description: Erfahren Sie, wie Sie die Leistung Ihrer AEM Forms-DB2®-Datenbank verbessern können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: e8cf9e73-345c-4dea-8361-b678c1a3cd1b
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 95%

---

# DB2®-Datenbank: Wöchentliche Ausführung eines Prozesses{#db-database-running-a-process-weekly}

Wenn Ihre AEM Forms-DB2®-Datenbank langsam wird, kann die Ausführung des folgenden wöchentlichen Prozesses die Leistung verbessern:

1. Starten Sie das DB2® Control Center:

   (Windows) Wählen Sie „Start“ > „Programme“ > „IBM DB2®“ > „Allgemeine Administrations-Tools“ > „Control Center“.

   (Linux® und UNIX®) Geben Sie in einer Eingabeaufforderung den Befehl `db2jcc` ein.

1. Klicken Sie in der Objektstruktur des DB2® Control Center auf „Alle Datenbanken“.
1. Klicken Sie auf die Datenbank, die Sie für AEM Forms erstellt haben, und klicken Sie auf den Ordner „Tabellen“.
1. Wählen Sie alle Datenbanktabellen im Inhaltsbereich aus, klicken Sie mit der rechten Maustaste darauf und wählen Sie „Statistiken ausführen“.
1. Gehen Sie zu „Statistiken“ > „Indexstatistiken“.
1. Wählen Sie „Statistik für alle Indizes sammeln“, wählen Sie „Statistik für Indizes mit erweiterter detaillierter Statistik sammeln“ und klicken Sie dann auf „OK“.

Nach Abschluss des Vorgangs wird eine entsprechende Meldung angezeigt. Schließen Sie die Meldung.
