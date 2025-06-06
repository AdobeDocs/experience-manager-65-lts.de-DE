---
title: Tipps zum Minimieren des Datenbankwachstums
description: 'Langlebige Prozesse speichern Prozessdaten in der AEM Forms-Datenbank. Das Wachstum der AEM Forms-Datenbank kann mithilfe weniger einfacher Prozessentwurfs- und Produktkonfigurationsstrategien minimiert werden. '
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: ac3766c5-b741-4e65-8053-0c9cfd66a2f9
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 93%

---

# Tipps zum Minimieren des Datenbankwachstums {#tips-for-minimizing-database-growth}

Langlebige Prozesse speichern Prozessdaten in der AEM Forms-Datenbank. Das Wachstum der AEM Forms-Datenbank kann mithilfe weniger einfacher Prozessentwurfs- und Produktkonfigurationsstrategien minimiert werden. 

## Tipps zum Prozessentwurf {#process-design-tips}

Verwenden Sie kurzlebige Prozesse, wann immer dies möglich ist. Kurzlebige Prozesse speichern keine Prozessdaten in der Datenbank. Der Nachteil beim Verwenden von kurzlebigen Prozessen besteht darin, dass ihr Status und Zustand nicht in der Administrationskonsole nachvollzogen werden und es keine Historie des Prozesses gibt.

Einige Dienstvorgänge, z. B. der Vorgang „Aufgabe zuweisen“ (User-Dienst), müssen in langlebigen Prozessen verwendet werden. In diesem Fall können Sie den Prozess in mehrere Unterprozesse aufteilen und daraus kurzlebige Prozesse machen, wo dies möglich ist. Wenn Sie diese Strategie verwenden, sollten kurzlebige Prozesse große Datenelemente, z. B. Dokumentwerte, verarbeiten können.

Verwenden Sie Variablen nur sparsam.  Wenn Sie langlebige Prozesse verwenden, wird bei jeder Prozessinstanz für jede Variable im Prozess Speicherplatz in der Datenbank zugewiesen. Wenn Sie Variablen strategisch verwenden, können Sie hier viel Speicherplatz sparen. Sie können beispielsweise Variablenwerte überschreiben, wenn alte Werte nicht mehr in dem Prozess benötigt werden. Und Sie können alle von Ihnen erstellten Variablen, die Sie nicht mehr verwenden, löschen. Sie können den Prozess überprüfen, um nicht verwendete Variablen zu suchen.

Verwenden Sie einfache Variablentypen (z. B. String oder Int) und vermeiden Sie es, wo immer möglich, komplexe Variablentypen zu verwenden. Speicherplatz in der Datenbank wird Variablen auch dann zugewiesen, wenn diese keinen Wert enthalten. Komplexe Variablen erfordern in der Regel mehr Speicherplatz als einfache Variablen.

## Tipps zur Produktverwaltung {#product-administration-tips}

Verwenden Sie den globalen Dokumentenspeicher (GDS) effizient.  Das GDS-Verzeichnis auf dem Formular-Server wird unter anderem zum Speichern von Dateien verwendet, die an Dienste übergeben werden, die Teil von AEM Forms in Prozessen sind. Zum Verbessern der Leistung werden kleinere Dokumente stattdessen im Arbeitsspeicher gespeichert und bleiben in der Datenbank erhalten.

Die Administrationskonsole stellt die Eigenschaft „Standardmäßige Maximalgröße für Inline-Dokumente“ zum Konfigurieren der Maximalgröße von Dokumenten bereit, die im Arbeitsspeicher gespeichert werden und in der Datenbank erhalten bleiben. (Siehe [Konfigurieren allgemeiner AEM Forms-Einstellungen](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).) Wenn Sie diese Eigenschaft auf einen niedrigen Wert festlegen, werden die meisten Dokumente im Ordner des globalen Dokumentenspeichers gespeichert, anstatt in der Datenbank. Der Vorteil besteht darin, dass Sie nicht mehr benötigte Dateien leichter löschen können, wenn sie im GDS-Verzeichnis gespeichert sind.
