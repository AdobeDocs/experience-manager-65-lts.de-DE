---
title: Inhaltsarchitektur
description: 'Tipps für die Entwicklung einer Inhaltsarchitektur (Hinweis: Alles ist Inhalt.)'
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: eb47f730-ac26-47a0-9bd7-3b7e94c79ecd
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 50%
---
# Inhaltsarchitektur{#content-architecture}

## David Nüschelers Modell als Vorbild {#follow-david-s-model}

David Nuescheler schrieb „David’s Model“ vor Jahren, aber seine Ideen sind bis heute gültig. Die wichtigsten Grundsätze des Modells lauten:

* Erst die Daten, dann die Struktur. Zumindest gegebenenfalls.
* Steuern Sie die Inhaltshierarchie. Lassen Sie es nicht zu.
* Workspaces sind für `clone()`, `merge()` und `update()` vorgesehen.
* Bei gleichgeordneten Elementen mit identischem Namen ist Vorsicht geboten.
* Verweise können als schädlich betrachtet werden.
* Dateien sind Dateien.
* IDs sind zu vermeiden.

Sie finden das Modell von David Nüscheler auf Jackrabbit Wiki unter [http://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

### Alles ist Inhalt {#everything-is-content}

Sie sollten alles im Repository speichern, anstatt sich auf separate Datenquellen von Dritten wie etwa Datenbanken zu verlassen. Ein solcher Ansatz gilt für erstellte Inhalte, Binärdaten wie Bilder, Code und Konfigurationen. Damit können wir einen Satz von APIs verwenden, um alle Inhalte zu verwalten und die Promotion dieser Inhalte durch Replikation zu verwalten. Außerdem profitieren Sie von nur einer einzigen Quelle für Backups, Protokollierung usw.

### Anwenden des Design-Grundsatzes „Content Model First“ {#use-the-content-model-first-design-principle}

Wenn Sie eine neue Funktion entwickeln, beginnen Sie immer damit, zunächst die JCR-Inhaltsstruktur zu entwerfen. Befassen Sie sich dann erst mit dem Lesen und Schreiben Ihrer Inhalte mithilfe der standardmäßigen Sling-Servlets. Mit einem solchen Ansatz können Sie sicherstellen, dass Ihre Implementierung gut mit vorkonfigurierten Zugriffssteuerungsmechanismen funktioniert, und die Erstellung unnötiger Servlets im CRUD-Stil vermeiden.

### RESTful statt Panik {#be-restful}

Definieren Sie Servlets basierend auf Ressourcentypen anstelle von Pfaden. Dieser Ansatz ermöglicht die Verwendung von JCR-Zugriffssteuerungen, die Einhaltung von REST-Prinzipien und die Verwendung der Ressource und des Ressourcen-Resolvers, die in der Anfrage bereitgestellt werden. Mit diesem Ansatz können Sie die Skripte ändern, die URLs Server-seitig rendern, ohne die Client-seitigen URLs zu ändern. Außerdem werden Server-seitige Implementierungsdetails vor dem Client ausgeblendet, um die Sicherheit zu erhöhen.

### Vermeiden der Definition neuer Knotentypen {#avoid-defining-new-node-types}

Knotentypen funktionieren auf niedriger Ebene in der Infrastrukturschicht. Die meisten Anforderungen werden erfüllt, indem ein `sling:resourceType` verwendet wird, der einem `nt:unstructured`-, `oak:Unstructured`-, `sling:Folder`- oder `cq:Page`-Knotentyp zugewiesen ist. Knotentypen entsprechen dem Schema im Repository, wobei sich das Ändern von Knotentypen im weiteren Verlauf als kostspielig erweisen kann.

### Einhalten Sie Namenskonventionen im JCR {#adhere-to-naming-conventions-in-the-jcr}

Durch die Einhaltung von Namenskonventionen wird die Konsistenz der Code-Basis erhöht, die Fehler-Inzidenzrate gesenkt und der Arbeitsprozess der beteiligten Entwickelnden beschleunigt. Adobe wendet die folgenden Konventionen bei der Entwicklung von AEM an:

* Knotennamen

  * Alles Kleinbuchstaben.
  * Worttrennung mithilfe von Bindestrichen.

* Eigenschaftsnamen

  * Binnenmajuskel, beginnend mit einem Kleinbuchstaben.

* Komponenten (JSP/HTML)

  * Alles Kleinbuchstaben.
  * Worttrennung mithilfe von Bindestrichen.
