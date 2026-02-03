---
title: Verwenden von Sling-Adaptern
description: Sling bietet ein Adaptermuster zum praktischen Übersetzen von Objekten, die die anpassbare Schnittstelle implementieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 7eae83bd-7982-4051-821f-b43f65c5af2b
source-git-commit: cf22b13e0f7c8e66b598f85aab81b022480e60bc
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 50%

---

# Verwenden von Sling-Adaptern{#using-sling-adapters}

[Sling](https://sling.apache.org) bietet ein [Adaptermuster](https://sling.apache.org/documentation/the-sling-engine/adapters.html) um Objekte bequem zu übersetzen, die die [adaptable](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29)-Schnittstelle implementieren. Diese Schnittstelle stellt eine generische [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29)-Methode bereit, mit der das Objekt in den Klassentyp übersetzt wird, der als Argument übergeben wird.

Um zum Beispiel ein Ressourcenobjekt in das entsprechende Knotenobjekt zu übersetzen, können Sie einfach wie folgt vorgehen:

```java
Node node = resource.adaptTo(Node.class);
```

## Anwendungsfälle {#use-cases}

Es gibt die folgenden Nutzungsszenarien:

* Rufen Sie spezifische Objekte für die Implementierung ab.

  Eine JCR-basierte Implementierung der generischen [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html)-Schnittstelle ermöglicht beispielsweise Zugriff auf das zugrunde liegende JCR-[`Node`](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html)-Element.

* Erstellung von direkten Verknüpfungen für Objekte, für die interne Kontextobjekte übergeben werden müssen.

  Beispielsweise enthält die JCR-basierte [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) einen Verweis auf die [`JCR Session`](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Session.html) der Anfrage, die wiederum für viele Objekte erforderlich ist, die auf Grundlage dieser Anfragesitzung funktionieren können, z. B. die [`PageManager`](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/PageManager.html) oder die [`UserManager`](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/security/UserManager.html).

* Direkte Verknüpfung mit Services.

  Dies ist ein seltener Fall, da `sling.getService()` bereits eine einfache Möglichkeit darstellt.

### NULL-Rückgabewert {#null-return-value}

Die `adaptTo()` gibt null zurück.

Die Gründe variieren, einschließlich der folgenden:

* Die Implementierung unterstützt den Zieltyp nicht.
* Eine Adapter-Factory, die diesen Fall behandelt, ist nicht aktiv (z. B. aufgrund fehlender Service-Referenzen)
* Eine interne Bedingung ist fehlgeschlagen.
* Der Dienst ist nicht verfügbar.

Es ist wichtig, dass Sie den Null-Fall angemessen behandeln. Für JSP-Renderings kann es akzeptabel sein, die JSP fehlschlagen zu lassen, wenn dies zu einem leeren Inhaltselement führt.

### Caching {#caching}

Zur Verbesserung der Leistung dürfen Implementierungen das Objekt zwischenspeichern, das über einen `obj.adaptTo()`-Aufruf zurückgegeben wird. Wenn das `obj` gleich ist, ist auch das zurückgegebene Objekt dasselbe.

Diese Zwischenspeicherung wird für alle auf `AdapterFactory` basierenden Fälle durchgeführt.

Es gibt jedoch keine allgemeine Regel – das Objekt kann entweder eine neue oder eine vorhandene Instanz sein. Dies bedeutet, dass Sie sich nicht auf eines der beiden Verhalten verlassen können. Daher ist es wichtig, insbesondere in `AdapterFactory`, dass Objekte in diesem Szenario wiederverwendbar sind.

### Funktionsweise {#how-it-works}

Es gibt verschiedene Möglichkeiten, `Adaptable.adaptTo()` zu implementieren:

* Über das Objekt selbst. Die eigentliche Methode wird implementiert. Anschließend erfolgt die Zuordnung zu bestimmten Objekten.
* Über ein [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html), mit dem zufällige Objekte zugeordnet werden können.

  Die Objekte müssen trotzdem noch die `Adaptable`-Schnittstelle implementieren und [`SlingAdaptable`](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (übergibt den `adaptTo`-Aufruf an einen zentralen Adapter-Manager) erweitern.

  Erweitert den `adaptTo` für vorhandene Klassen, z. B. `Resource`.

* Eine Kombination beider Vorgehensweisen.

Im ersten Fall kann über Java™ Docs angegeben werden, welche `adaptTo-targets` möglich sind. Bei bestimmten Unterklassen wie der JCR-basierten Ressource ist dies jedoch häufig nicht möglich. Im letzteren Fall sind Implementierungen von `AdapterFactory` normalerweise Teil der privaten Klassen eines Bundles und werden daher nicht in einer Client-API bereitgestellt oder in Java™-Dokumenten aufgeführt. Theoretisch wäre es möglich, auf alle `AdapterFactory`-Implementierungen über die [OSGi](/help/sites-deploying/configuring-osgi.md)-Service-Laufzeit zuzugreifen und sich die Konfigurationen der „adaptierbaren Elemente“ (Quellen und Ziele) anzusehen, diese aber nicht einander zuzuordnen. Letztlich hängt es von der internen Logik ab, die dokumentiert werden muss. Daher die Referenz.

## Verweis {#reference}

### Sling {#sling}

Adaption von [**Resource**](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html) für:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html">Knoten</a></td>
   <td>Wenn es sich um eine JCR-basierte Ressource oder eine JCR-Eigenschaft handelt, die auf einen Knoten verweist</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Property.html">Eigenschaft</a></td>
   <td>Wenn es sich um eine auf einer JCR-Eigenschaft basierende Ressource handelt</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Item.html">Element</a></td>
   <td>Wenn es sich um eine JCR-basierte Ressource handelt (Knoten oder Eigenschaft)</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Map.html">Zuordnung</a></td>
   <td>Gibt eine Zuordnung der Eigenschaften zurück, wenn es sich um eine JCR-knotenbasierte Ressource (oder eine andere Ressource mit unterstützenden Wertzuordnungen) handelt.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td>
   <td>Es gibt eine benutzerfreundliche Zuordnung der Eigenschaften zurück, wenn es sich um eine JCR-knotenbasierte Ressource oder eine andere Ressource handelt, die Wertzuordnungen unterstützt. Dies kann (auf einfachere Weise) auch durch die Verwendung von <br /><code><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ResourceUtil.html">ResourceUtil.getValueMap(Resource)</a></code> (zur Verarbeitung von NULL-Fällen usw.) erreicht werden.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td>
   <td>Erweiterung von <a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>, mit der beim Suchen nach Eigenschaften die Hierarchie der Ressourcen berücksichtigt werden kann.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ModifiableValueMap.html">ModifiableValueMap</a></td>
   <td>Eine Erweiterung von <a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>, mit der Sie Eigenschaften dieses Knotens ändern können.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td>
   <td>Er gibt den binären Inhalt einer Dateiressource zurück, wenn sie auf einem JCR-Knoten (<code>nt:file</code> oder <code>nt:resource</code>), einer Bundle-Ressource oder einer Dateisystemressource basiert. Es werden die Daten einer binären JCR-Eigenschaftenressource zurückgegeben.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/net/URL.html">URL</a></td>
   <td>Gibt eine URL für die Ressource zurück. Sie gibt die Repository-URL für eine auf einem JCR-Knoten basierende Ressource, die JAR-Bundle-URL für eine Bundle-Ressource oder die Datei-URL für eine Dateisystemressource zurück.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/io/File.html">File</a></td>
   <td>Wenn es eine Dateisystemressource ist</td>
  </tr>
  <tr>
   <td><a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/api/scripting/SlingScript.html">SlingScript</a></td>
   <td>Wenn diese Ressource ein Skript ist (z. B. eine JSP-Datei), für das eine Scripting-Engine bei Sling registriert ist.</td>
  </tr>
  <tr>
   <td><a href="https://www.oracle.com/java/technologies/servlet-technology.html">Servlet</a></td>
   <td>Wenn diese Ressource ein Skript ist (z. B. eine JSP-Datei), für das eine Skript-Engine bei Sling registriert ist, oder wenn es eine Servlet-Ressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/String.html">String</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Boolean.html">Boolean</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Long.html">Long</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Double.html">Double</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Calendar.html">Calendar</a><br /> <a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Value.html">Value</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/String.html">String[]</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Boolean.html">Boolean[]</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Long.html">Long[]</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Calendar.html">Calendar[]</a><br /> <a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Value.html">Value[]</a></td>
   <td>Gibt die Werte zurück, wenn es sich um eine JCR-Eigenschaftenbasierte Ressource handelt (und der Wert passt).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Wenn es sich um eine auf einem JCR-Knoten basierende Ressource handelt</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/Page.html">Page</a></td>
   <td>Wenn es sich um eine JCR-basierte Ressource handelt und der Knoten eine <code>cq:Page</code> (oder <code>cq:PseudoPage</code>) ist.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/components/Component.html">Komponente</a></td>
   <td>Wenn es sich um eine <code>cq:Component</code>-Knotenressource handelt</td>
  </tr>  
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/designer/Design.html">Design</a></td>
   <td>Wenn es sich um einen Design-Knoten handelt (<code>cq:Page</code>)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/Template.html">Vorlage  </a></td>
   <td>Wenn es sich um eine <code>cq:Template</code>-Knotenressource handelt</td>
  </tr>  
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/msm/api/Blueprint.html">Blueprint</a></td>
   <td>Wenn es sich um eine <code>cq:Template</code>-Knotenressource handelt</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/dam/api/Asset.html">Asset</a></td>
   <td>Wenn es sich um eine <code>dam:Asset</code>-Knotenressource handelt</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/dam/api/Rendition.html">Rendition</a></td>
   <td>Wenn es sich um eine <code>dam:Asset</code> Ausgabedarstellung handelt (<code>nt:file</code> unter dem Ausgabedarstellungsordner einer <code>dam:Asset</code>)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/tagging/Tag.html">Tag</a></td>
   <td>Wenn es sich um eine <code>cq:Tag</code>-Knotenressource handelt</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td>
   <td>Basiert auf der JCR-Sitzung, wenn es sich um eine JCR-basierte Ressource handelt und der Benutzer berechtigt ist, auf UserManager zuzugreifen.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Authorizable</a></td>
   <td>Die Authorizable-Funktion ist die allgemeine Basisschnittstelle für Benutzer und Gruppe.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/User.html">User</a></td>
   <td>Der Benutzer ist ein spezieller autorisierbarer Benutzer, der authentifiziert und stellvertretend agiert werden kann.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/search/SimpleSearch.html">SimpleSearch</a></td>
   <td>Sucht unterhalb der Ressource (oder verwendet setSearchIn()), wenn es sich um eine JCR-basierte Ressource handelt.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/workflow/status/WorkflowStatus.html">WorkflowStatus</a></td>
   <td>Workflow-Status für die angegebene Seite/den angegebenen Workflow-Payload-Knoten.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/replication/ReplicationStatus.html">ReplicationStatus</a></td>
   <td>Replikationsstatus für die angegebene Ressource oder deren <code>jcr:content</code> Unterknoten (zuerst überprüft).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/connector/ConnectorResource.html">ConnectorResource</a></td>
   <td>Es gibt eine angepasste Connector-Ressource für bestimmte Typen zurück, wenn es sich um eine JCR-basierte Ressource handelt.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/contentsync/config/package-summary.html">Config</a></td>
   <td>Wenn es sich um eine <code>cq:ContentSyncConfig</code>-Knotenressource handelt</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/contentsync/config/package-summary.html">ConfigEntry</a></td>
   <td>Wenn es unter einer <code>cq:ContentSyncConfig</code>-Knotenressource liegt</td>
  </tr>
 </tbody>
</table>

Adaption von [**ResourceResolver**](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ResourceResolver.html) für:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Session.html">Session</a></td>
   <td>Die JCR-Sitzung der Anfrage, wenn es sich um einen JCR-basierten Ressourcen-Resolver handelt (Standard).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td>
   <td>Basiert auf der JCR-Sitzung, wenn es sich um einen JCR-basierten Ressourcen-Resolver handelt.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td>
   <td>Basiert auf der JCR-Sitzung, wenn es sich um einen JCR-basierten Ressourcen-Resolver handelt.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/UserManager.html">UserManager</a></td>
   <td>UserManager bietet Zugriff auf und Mittel zum Verwalten autorisierbarer Objekte, bei denen es sich um Benutzer und Gruppen handelt. Der UserManager ist an eine bestimmte Sitzung gebunden.
   </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Authorizable</a> </td>
   <td>Der aktuelle Benutzer.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/User.html">User</a><br /> </td>
   <td>Der aktuelle Benutzer.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/Externalizer.html">Externalizer</a></td>
   <td>Zum Externalisieren absoluter URLs, auch ohne das Anfrageobjekt<br /> </td>
  </tr>
 </tbody>
</table>

Adaptierung von [**SlingHttpServletRequest**](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) für:

Es sind noch keine Ziele vorhanden, aber „Adaptable“ wird implementiert und kann als Quelle in einer benutzerdefinierten „AdapterFactory“ verwendet werden.

Adaptierung von [**SlingHttpServletResponse**](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) für:

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td>
   <td>Wenn es eine Sling Rewriter-Antwort ist</td>
  </tr>
 </tbody>
</table>

#### WCM {#wcm}

**Die [Seite](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/Page.html)** passt sich an:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><br /> </td>
   <td>Ressource der Seite.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Die Ressource mit dem Titel ist die aktuelle Ressource. Das heißt, das gleiche Objekt, das Sie gerade betrachten.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html">Knoten</a></td>
   <td>Knoten der Seite.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alle Elemente, für die die Ressource der Seite adaptiert werden kann.</td>
  </tr>
 </tbody>
</table>

**Die [Komponente](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/components/Component.html)** passt sich an:

| [Resource](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource der Komponente. |
| --- | --- |
| [LabeledResource](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/LabeledResource.html) | Die Ressource mit dem Titel ist die aktuelle Ressource. Das heißt, das gleiche Objekt, das Sie gerade betrachten. |
| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) | Knoten der Komponente. |
| ... | Alle Elemente, für die die Ressource der Komponente adaptiert werden kann. |

**Die [Vorlage](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/Template.html)** passt sich an:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td>
   <td>Ressource der Vorlage.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Die Ressource mit dem Titel ist die aktuelle Ressource. Das heißt, das gleiche Objekt, das Sie gerade betrachten.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html">Knoten</a></td>
   <td>Knoten dieser Vorlage.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alle Elemente, für die die Ressource der Vorlage adaptiert werden kann.</td>
  </tr>
 </tbody>
</table>

#### Sicherheit {#security}

Adaption von **Authorizable**, **User und **Group** für:

| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) | Gibt den Hauptknoten des Benutzers/der Gruppe zurück. |
| --- | --- |
| [ReplicationStatus](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/replication/ReplicationStatus.html) | Gibt den Replikationsstatus für den Benutzer-/Gruppen-Hauptknoten zurück. |

#### DAM {#dam}

Adaption von **Asset** für:

| [Resource](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource des Assets. |
| --- | --- |
| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) | Knoten des Assets. |
| ... | Alle Elemente, für die die Ressource des Assets adaptiert werden kann. |

#### Tag {#tagging}

Adaption von **Tag** für:

| [Resource](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource des Tags. |
| --- | --- |
| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) | Knoten des Tags. |
| ... | Alle Elemente, für die die Ressource des Tags adaptiert werden kann. |

#### Andere {#other}

Darüber hinaus bietet Sling/JCR/OCM auch eine ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` für benutzerdefinierte OCM-Objekte [Object Content Mapping](https://jackrabbit.apache.org/jcr/object-content-mapping.html)).
