---
title: Einbinden von Tagging in eine AEM-Anwendung
description: Programmgesteuert mit Tags oder erweiterten Tags innerhalb einer benutzerdefinierten AEM-Anwendung arbeiten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
feature: Developing,Tagging
solution: Experience Manager, Experience Manager Sites
role: Developer
exl-id: c835a110-89cf-4857-9ee0-c0ad781a66ae
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 99%

---

# Einbinden von Tagging in eine AEM-Anwendung{#building-tagging-into-an-aem-application}

Für das programmatische Arbeiten mit Tags oder das Erweitern von Tags in einem benutzerdefinierten AEM-Programm wird in diesem Dokument die Verwendung der

* [Tagging-API](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/tagging/package-summary.html),

die mit dem

* [Tagging-Framework interagiert, beschrieben.](/help/sites-developing/framework.md)

Weitere Informationen zum Tagging finden Sie unter:

* [Verwalten von Tags](/help/sites-administering/tags.md). Hier finden Sie außerdem Informationen zum Erstellen und Verwalten von Tags sowie dazu, welchen Inhalten Tags zugewiesen wurden.
* [Verwenden von Tags](/help/sites-authoring/tags.md) für Informationen zum Tagging von Inhalten.

## Übersicht über die Tagging-API {#overview-of-the-tagging-api}

Die Implementierung des [Tagging-Frameworks](/help/sites-developing/framework.md) in AEM ermöglicht die Verwaltung von Tags und Tag-Inhalten mithilfe der JCR-API. Der TagManager stellt sicher, dass Tags, die als Werte in der Zeichenfolgen-Array-Eigenschaft `cq:tags` eingegeben wurden, nicht dupliziert werden. Er entfernt TagIDs, die auf nicht vorhandene Tags verweisen, und aktualisiert TagIDs für verschobene oder zusammengefügte Tags. TagManager verwendet einen JCR Observation Listener, der alle falschen Änderungen zurücksetzt. Die wichtigsten Klassen befinden sich im Paket [com.day.cq.tagging](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/index.html?com/day/cq/tagging/package-summary.html):

* JcrTagManagerFactory – gibt eine JCR-basierte Implementierung eines `TagManager` zurück. Es ist die Referenzimplementierung der Tagging-API.
* `TagManager` – ermöglicht das Auflösen und Erstellen von Tags nach Pfaden und Namen.
* `Tag` - definiert das Tag-Objekt.

### Abrufen eines JCR-basierten TagManagers {#getting-a-jcr-based-tagmanager}

Um eine TagManager-Instanz abzurufen, benötigen Sie eine JCR-`Session`, und Sie müssen `getTagManager(Session)` aufrufen:

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

Im typischen Sling-Kontext können Sie sich auch mit dem `ResourceResolver` an einen `TagManager` anpassen:

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Abrufen eines Tag-Objekts {#retrieving-a-tag-object}

Ein `Tag` kann über den `TagManager` abgerufen werden, indem entweder ein vorhandenes Tag aufgelöst oder eines erstellt wird:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

Für die JCR-basierte Implementierung, die `Tags` auf JCR-`Nodes` abbildet, können Sie den Mechanismus `adaptTo` von Sling direkt verwenden, wenn Sie die Ressource haben (z. B. `/content/cq:tags/default/my/tag`):

```java
Tag tag = resource.adaptTo(Tag.class);
```

Während ein Tag nur „von“ einer Ressource (kein Knoten) konvertiert werden kann, kann ein Tag sowohl in einen Knoten als auch in eine Ressource konvertiert werden :

```java
Node node = tag.adaptTo(Node.class);
Resource node = tag.adaptTo(Resource.class);
```

>[!NOTE]
>
>Die direkte Anpassung von `Node` zu `Tag` ist nicht möglich, da `Node` die Sling-Methode `Adaptable.adaptTo(Class)` nicht implementiert.

### Abrufen und Festlegen von Tags {#getting-and-setting-tags}

```java
// Getting the tags of a Resource:
Tag[] tags = tagManager.getTags(resource);

// Setting tags to a Resource:
tagManager.setTags(resource, tags);
```

### Suchen nach Tags {#searching-for-tags}

```java
// Searching for the Resource objects that are tagged with the tag object:
Iterator<Resource> it = tag.find();

// Retrieving the usage count of the tag object:
long count = tag.getCount();

// Searching for the Resource objects that are tagged with the tagID String:
 RangeIterator<Resource> it = tagManager.find(tagID);
```

>[!NOTE]
>
>Der gültige zu verwendete `RangeIterator` ist:
>
>`com.day.cq.commons.RangeIterator`

### Löschen von Tags {#deleting-tags}

```java
tagManager.deleteTag(tag);
```

### Replizieren von Tags {#replicating-tags}

Es ist möglich, den Replikations-Service (`Replicator`) mit Tags zu verwenden, da Tags vom Typ `nt:hierarchyNode` sind:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## Tagging auf der Client-Seite {#tagging-on-the-client-side}

Das Formular-Widget `CQ.tagging.TagInputField` dient zur Eingabe von Tags. Es beinhaltet ein Popup-Menü für die Auswahl vorhandener Tags, einschließlich Autovervollständigen und vieler anderer Funktionen. Sein xtype ist `tags`.

## Der Tag Garbage Collector {#the-tag-garbage-collector}

Der Tag Garbage Collector ist ein Hintergrund-Service, der die ausgeblendeten und nicht verwendeten Tags bereinigt. Ausgeblendete und nicht verwendete Tags sind Tags unter `/content/cq:tags`, die eine Eigenschaft `cq:movedTo` haben und nicht auf einem Inhaltsknoten verwendet werden, d. h. ihre Anzahl beträgt null. Durch Verwenden dieses Lazy-Deletion-Prozesses muss der Inhaltsknoten (d. h. die Eigenschaft `cq:tags`) nicht als Teil des Verschiebungs- oder des Zusammenführungsvorgangs aktualisiert werden. Die Verweise in der Eigenschaft `cq:tags` werden automatisch aktualisiert, wenn die Eigenschaft `cq:tags` aktualisiert wird, z. B. durch das Seiteneigenschaften-Dialogfeld.

Der Garbage Collector für Tags wird standardmäßig einmal täglich ausgeführt. Sie können ihn hier konfigurieren:

```xml
http://localhost:4502/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector
```

## Tag-Suche und Tag-Auflistung {#tag-search-and-tag-listing}

Die Tag-Suche und die Tag-Auflistung funktionieren folgendermaßen:

* Die Suche nach TagID sucht nach den Tags, für die die Eigenschaft `cq:movedTo` auf TagID gesetzt ist, und folgt den `cq:movedTo`-TagIDs.

* Die Suche nach Tag-Titel sucht nur die Tags, die keine Eigenschaft `cq:movedTo` besitzen.

## Tags in verschiedenen Sprachen {#tags-in-different-languages}

Wie in der Dokumentation zur Verwaltung von Tags im Abschnitt [Verwalten von Tags in verschiedenen Sprachen](/help/sites-administering/tags.md#managing-tags-in-different-languages) beschrieben, kann ein Tag-`title` in verschiedenen Sprachen definiert werden. Eine sprachempfindliche Eigenschaft wird dann dem Tag-Knoten hinzugefügt. Diese Eigenschaft weist das Format `jcr:title.<locale>` auf, beispielsweise `jcr:title.fr` für die französische Übersetzung. `<locale>` muss eine ISO-Gebietsschema-Zeichenfolge in Kleinbuchstaben sein und „_“ anstelle von „-“ enthalten, z. B. `de_ch`.

Wenn das Tag **Animals** zur **Produktseite** hinzugefügt wird, wird der Wert `stockphotography:animals` zur Eigenschaft `cq:tags` des Knotens „/content/geometrixx/de/products/jcr:content“ hinzugefügt. Die Übersetzung wird vom Tag-Knoten referenziert.

Die Server-seitige API verfügt über lokalisierte `title`-bezogene Methoden:

* [com.day.cq.tagging.Tag](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/index.html?com/day/cq/tagging/Tag.html)

   * getLocalizedTitle(Locale locale)
   * getLocalizedTitlePaths()
   * getLocalizedTitles()
   * getTitle(Locale locale)
   * getTitlePath(Locale locale)

* [com.day.cq.tagging.TagManager](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/index.html?com/day/cq/tagging/TagManager.html)

   * canCreateTagByTitle(String tagTitlePath, Locale locale)
   * createTagByTitle(String tagTitlePath, Locale locale)
   * resolveByTitle(String tagTitlePath, Locale locale)

In AEM kann die Sprache entweder aus der Seitensprache oder aus der Benutzersprache abgerufen werden:

* So rufen Sie die Seitensprache in einer JSP ab:

   * `currentPage.getLanguage(false)`

* So rufen Sie die Benutzersprache in einer JSP ab:

   * `slingRequest.getLocale()`

`currentPage` und `slingRequest` sind in einer JSP über das Tag [&lt;cq:definedObjects>](/help/sites-developing/taglib.md) verfügbar.

Beim Tagging hängt die Lokalisierung vom Kontext ab, da das Tag `titles` in der Seitensprache, in der Anwendersprache oder in jeder anderen Sprache angezeigt werden kann.

### Hinzufügen einer neuen Sprache zum Dialogfeld „Tag bearbeiten“ {#adding-a-new-language-to-the-edit-tag-dialog}

Im folgenden Verfahren wird beschrieben, wie Sie eine Sprache (Finnisch) zum Dialogfeld **Tag bearbeiten** hinzufügen:

1. Bearbeiten Sie in **CRXDE** die Mehrwerteigenschaft `languages` des Knotens `/content/cq:tags`.

1. Fügen Sie `fi_fi` hinzu, das das finnische Gebietsschema darstellt, und speichern Sie die Änderungen.

Die neue Sprache (Finnisch) ist jetzt im Tag-Dialogfeld der Seiteneigenschaften und im Dialogfeld **Tag bearbeiten** verfügbar, wenn Sie ein Tag in der **Tagging-Konsole** bearbeiten.

>[!NOTE]
>
>Die neue muss eine Sprache sein, die von AEM erkannt wird. Das heißt, sie muss als Knoten unter `/libs/wcm/core/resources/languages` verfügbar sein.

>[!CAUTION]
>
>Durch die Installation von Tag-bezogenen, vorkonfigurierten Inhalten über ein offizielles Update-Paket (einschließlich Service Packs, Security Service Packs, Extended Feature Packs, Cumulative Feature Packs, Patches usw.) wird die Spracheigenschaft des Knotens „`/content/cq:tags`“ auf den Standardwert zurückgesetzt. Daher ist es erforderlich, sie vor der Installation aus den Eigenschaften hinzuzufügen.
