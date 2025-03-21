---
title: Anleitung für den programmgesteuerten Zugriff auf das AEM-JCR
description: Sie können programmgesteuert Knoten und Eigenschaften ändern, die sich innerhalb des AEM-Repositorys befinden, das Teil von Adobe Experience Cloud ist.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing,JCR
role: Developer
exl-id: 0b375003-183d-4007-b1a1-0c48607745d1
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 100%

---

# Anleitung für den programmgesteuerten Zugriff auf das AEM-JCR{#how-to-programmatically-access-the-aem-jcr}

Sie können programmgesteuert Knoten und Eigenschaften ändern, die sich innerhalb des Adobe CQ-Repositorys befinden, das Teil von Adobe Experience Cloud ist. Um auf das CQ-Repository zuzugreifen, verwenden Sie die Java™ Content Repository(JCR)-API. Sie können die Java™ JCR-API zum Erstellen, Ersetzen, Aktualisieren und Löschen (CRUD, Create, Replace, Update, Delete) von Inhalten verwenden, die sich im Adobe CQ-Repository befinden.  Weitere Informationen zur Java™ JCR-API finden Sie unter [https://jackrabbit.apache.org/jcr/jcr-api.html](https://jackrabbit.apache.org/jcr/jcr-api.html)

>[!NOTE]
>
>In diesem Entwicklungsartikel wird der Adobe CQ JCR von einer externen Java™-Anwendung aus geändert.  Im Gegensatz dazu können Sie den JCR mithilfe der JCR-API innerhalb eines OSGi-Bundles ändern.  Details finden Sie unter [Beibehalten von CQ-Daten im Java™ Content Repository](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de).

>[!NOTE]
>
>Fügen Sie dem Klassenpfad Ihrer Java™-Anwendung die Datei `jackrabbit-standalone-2.4.0.jar` hinzu, um die JCR-API zu verwenden. Diese JAR-Datei finden Sie auf der Web-Seite der Java™ JCR-API unter [https://jackrabbit.apache.org/jcr/jcr-api.html](https://jackrabbit.apache.org/jcr/jcr-api.html).

>[!NOTE]
>
>Informationen zum Abfragen des Adobe CQ JCR mithilfe der JCR-Abfrage-API finden Sie unter [Abfragen von Adobe Experience Manager-Daten mit der JCR-API](https://helpx.adobe.com/de/experience-manager/using/querying-experience-manager-data-using1.html).

## Erstellen einer Repository-Instanz {#create-a-repository-instance}

Es gibt unterschiedliche Verfahren zur Herstellung einer Verbindung mit einem Repository. In diesem Entwicklungsartikel wird eine statische Methode verwendet, die der Klasse `org.apache.jackrabbit.commons.JcrUtils` zuzuordnen ist. Der Name der Methode lautet `getRepository`. Diese Methode verwendet einen Zeichenfolgenparameter, der die URL des Adobe CQ-Servers darstellt. Zum Beispiel: `http://localhost:4503/crx/server`.

Die Methode `getRepository` gibt eine `Repository`-Instanz zurück, was im folgenden Code-Beispiel veranschaulicht wird.

```java
//Create a connection to the AEM JCR repository running on local host
Repository repository = JcrUtils.getRepository("http://localhost:4503/crx/server");
```

## Erstellen einer Sitzungsinstanz {#create-a-session-instance}

Die `Repository`-Instanz stellt das CRX-Repository dar. Mit der `Repository`-Instanz stellen Sie eine Sitzung mit dem Repository her. Zum Erstellen einer Sitzung rufen Sie die Methode `login` der `Repository`-Instanz auf und übergeben ein `javax.jcr.SimpleCredentials`-Objekt. Die Methode `login` gibt eine `javax.jcr.Session`-Instanz zurück.

Sie erstellen ein `SimpleCredentials`-Objekt, indem Sie seinen Konstruktor verwenden und die folgenden Zeichenfolgenwerte übergeben:

* den Benutzernamen
* das zugehörige Kennwort

Rufen Sie bei der Übergabe des zweiten Parameters die Methode `toCharArray` des Zeichenfolgeobjekts auf. Der folgende Code zeigt, wie Sie die Methode `login` aufrufen, die eine `javax.jcr.Sessioninstance` zurückgibt.

```java
//Create a Session instance
javax.jcr.Session session = repository.login( new SimpleCredentials("admin", "admin".toCharArray()));
```

## Erstellen einer Knoteninstanz {#create-a-node-instance}

Verwenden Sie eine `Session`-Instanz, um eine `javax.jcr.Node`-Instanz zu erstellen. Mit einer `Node`-Instanz können Sie Knotenvorgänge durchführen. Beispielsweise können Sie einen Knoten erstellen. Um einen Knoten zu erstellen, der den Stammknoten darstellt, rufen Sie die Methode `getRootNode` der `Session`-Instanz auf, wie in der folgenden Code-Zeile veranschaulicht.

```java
//Create a Node
Node root = session.getRootNode();
```

Nach der Erstellung der `Node`-Instanz können Sie verschiedene Aufgaben ausführen, z. B. einen anderen Knoten erstellen und ihm einen Wert hinzufügen. Der folgende Code erstellt beispielsweise zwei Knoten und fügt dem zweiten Knoten einen Wert hinzu.

```java
// Store content
Node day = adobe.addNode("day");
day.setProperty("message", "Adobe CQ is part of the Adobe Digital Marketing Suite!");
```

## Abrufen von Knotenwerten {#retrieve-node-values}

Zum Abrufen eines Knotens und seines Werts rufen Sie die Methode `getNode` der `Node`-Instanz auf und übergeben Sie einen Zeichenfolgenwert, der den vollqualifizierten Pfad zum Knoten darstellt. Betrachten Sie die im vorherigen Code-Beispiel erstellte Knotenstruktur.  Um den Tagesknoten abzurufen, geben Sie „adobe/day“ an, wie im folgenden Code gezeigt:

```java
// Retrieve content
Node node = root.getNode("adobe/day");
System.out.println(node.getPath());
System.out.println(node.getProperty("message").getString());
```

## Erstellen von Knoten im Adobe CQ-Repository {#create-nodes-in-the-adobe-cq-repository}

Im folgenden Java™-Code-Beispiel wird eine Java™-Klasse dargestellt, die eine Verbindung mit Adobe CQ herstellt, eine `Session`-Instanz erstellt und neue Knoten hinzufügt. Einem Knoten wird ein Datenwert zugewiesen, woraufhin der Wert des Knotens und seines Pfades aus der Konsole geschrieben wird. Melden Sie sich ab, um die Sitzung zu beenden.

```java
/*
 * This Java Quick Start uses the jackrabbit-standalone-2.4.0.jar
 * file. See the previous section for the location of this JAR file
 */

import javax.jcr.Repository;
import javax.jcr.Session;
import javax.jcr.SimpleCredentials;
import javax.jcr.Node;

import org.apache.jackrabbit.commons.JcrUtils;
import org.apache.jackrabbit.core.TransientRepository;

public class GetRepository {

public static void main(String[] args) throws Exception {

try {

    //Create a connection to the CQ repository running on local host
    Repository repository = JcrUtils.getRepository("http://localhost:4503/crx/server");

   //Create a Session
   javax.jcr.Session session = repository.login( new SimpleCredentials("admin", "admin".toCharArray()));

  //Create a node that represents the root node
  Node root = session.getRootNode();

  // Store content
  Node adobe = root.addNode("adobe");
  Node day = adobe.addNode("day");
  day.setProperty("message", "Adobe CQ is part of the Adobe Digital Marketing Suite!");

  // Retrieve content
  Node node = root.getNode("adobe/day");
  System.out.println(node.getPath());
  System.out.println(node.getProperty("message").getString());

  // Save the session changes and log out
  session.save();
  session.logout();
  }
 catch(Exception e){
  e.printStackTrace();
  }
 }
}
```

Nach dem Ausführen des vollständigen Codebeispiels und dem Erstellen der Knoten können Sie die neuen Knoten in **[!UICONTROL CRXDE Lite]** anzeigen, wie in der folgenden Illustration veranschaulicht.

![chlimage_1-68](assets/chlimage_1-68a.png)
