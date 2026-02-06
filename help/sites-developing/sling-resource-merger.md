---
title: Verwenden des Sling Resource Merger in AEM
description: Der Sling Resource Merger bietet Dienste für den Zugriff auf Ressourcen und für das Zusammenführen von Ressourcen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 6fb6e522-fb81-4ba2-90b2-aad68f8bfa9e
source-git-commit: 9bc1cad84bb14b7513ede1fff2c1a37768dac442
workflow-type: tm+mt
source-wordcount: '1238'
ht-degree: 39%

---

# Verwenden des Sling Resource Merger in AEM{#using-the-sling-resource-merger-in-aem}

## Zweck {#purpose}

Der Sling Resource Merger bietet Dienste für den Zugriff auf und das Zusammenführen von Ressourcen. Er stellt Differenzierungsmechanismen bereit für:

* **[Überlagerungen](/help/sites-developing/overlays.md)** von Ressourcen unter Verwendung der [konfigurierten Suchpfade](/help/sites-developing/overlays.md#configuring-the-search-paths).

* **Überschreibungen** von Komponentendialogfeldern für die Touch-optimierte Benutzeroberfläche (`cq:dialog`) unter Verwendung der Ressourcentyphierarchie (anhand der Eigenschaft `sling:resourceSuperType`).

Sling Resource Merger kombiniert Überlagerungsressourcen und Überschreibungsressourcen (und ihre Eigenschaften) mit den ursprünglichen Ressourcen und Eigenschaften:

* Der Inhalt der angepassten Definition hat eine höhere Priorität als das Original. Das heißt, sie *überlagert* oder *überschreibt*.

* Wo nötig, geben bei der Anpassung definierte [Eigenschaften](#properties) an, wie aus dem Original zusammengeführte Inhalte zu verwenden sind.

>[!CAUTION]
>
>Der Sling Resource Merger und zugehörige Methoden können nur mit [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/index.html) verwendet werden. Dies bedeutet auch, dass es nur für die standardmäßige Touch-optimierte Benutzeroberfläche geeignet ist. Insbesondere auf diese Weise definierte Überschreibungen sind nur für das Touch-fähige Dialogfeld einer Komponente anwendbar.
>
>Um andere Bereiche (einschließlich anderer Teile einer Touch-optimierten Komponente oder der klassischen Benutzeroberfläche) zu überlagern oder zu überschreiben, kopieren Sie den entsprechenden Knoten und die entsprechende Struktur aus dem Original. Platzieren Sie die Kopie an der Stelle, an der Sie die Anpassung definieren.

### Ziele für AEM {#goals-for-aem}

Die Ziele der Verwendung des Sling Resource Merger in AEM lauten wie folgt:

* Sicherstellen, dass Anpassungsänderungen nicht in `/libs` vorgenommen werden
* Die Struktur reduzieren, die von `/libs` repliziert wird

  Bei Verwendung von Sling Resource Merger wird nicht empfohlen, die gesamte Struktur aus `/libs` zu kopieren. Der Grund dafür ist, dass dies dazu führen würde, dass zu viele Informationen in der Anpassung (normalerweise `/apps`) gespeichert werden. Das unnötige Duplizieren von Informationen erhöht die Wahrscheinlichkeit von Problemen, wenn das System aktualisiert wird.

>[!NOTE]
>
>Überschreibungen sind nicht von den Suchpfaden abhängig. Sie verwenden die Eigenschaft `sling:resourceSuperType` , um die Verbindung herzustellen.
>
>Trotzdem werden Überschreibungen oft unter `/apps` definiert, denn die Best Practice in AEM besteht in der Definition von Anpassungen unter `/apps`. Der Grund dafür ist, dass Sie unter `/libs` nichts ändern dürfen.

>[!CAUTION]
>
>Sie dürfen *keinerlei* Änderungen im Pfad `/libs` vornehmen.
>
>Der Grund dafür ist, dass der Inhalt von `/libs` überschrieben wird, wenn Sie Ihre Instanz das nächste Mal aktualisieren. Es kann auch überschrieben werden, wenn Sie einen Hotfix oder ein Feature Pack anwenden.
>
>Die empfohlene Methode zur Konfiguration und für andere Änderungen sieht wie folgt aus:
>
>1. Erstellen Sie das erforderliche Element unter `/apps` neu (d. h. wie es in `/libs` existiert).
>
>1. Nehmen Sie die gewünschten Änderungen in `/apps` vor.
>

### Eigenschaften {#properties}

Der Resource Merger stellt die folgenden Eigenschaften zur Verfügung:

* `sling:hideProperties` ( `String` oder `String[]`)

  Gibt die Eigenschaft bzw. Liste der Eigenschaften an, die ausgeblendet werden sollen.

  Der Platzhalter `*` blendet alles aus.

* `sling:hideResource` ( `Boolean`)

  Gibt an, ob die Ressourcen vollständig ausgeblendet sind, einschließlich ihrer untergeordneten Elemente.

* `sling:hideChildren` ( `String` oder `String[]`)

  Sie enthält den untergeordneten Knoten bzw. die Liste der untergeordneten Knoten, die ausgeblendet werden sollen. Die Eigenschaften des Knotens werden beibehalten.

  Der Platzhalter `*` blendet alles aus.

* `sling:orderBefore` ( `String`)

  Sie enthält den Namen des gleichrangigen Knotens, vor dem sich der aktuelle Knoten befindet.

Diese Eigenschaften beeinflussen, wie die entsprechenden / ursprünglichen Ressourcen / Eigenschaften (aus `/libs`) von der Überlagerung / Überschreibung (oft in `/apps`) verwendet werden.

### Erstellen der Struktur {#creating-the-structure}

Zum Erstellen einer Überlagerung oder Überschreibung müssen Sie den ursprünglichen Knoten mit der äquivalenten Struktur unterhalb des Ziels (häufig `/apps`) neu erstellen. Beispiel:

* Überlagerung

   * Die Definition des Navigationseintrags für die Sites-Konsole, wie sie in der Leiste angezeigt ist, wird definiert unter:

     `/libs/cq/core/content/nav/sites/jcr:title`

   * Erstellen Sie zum Überlagern den folgenden Knoten:

     `/apps/cq/core/content/nav/sites`

     Aktualisieren Sie dann die Eigenschaft `jcr:title` nach Bedarf.

* Überschreibung

   * Das Touch-optimierte Dialogfeld für die Textkonsole wird wie folgt definiert:

     `/libs/foundation/components/text/cq:dialog`

   * Um dies zu überschreiben, erstellen Sie den folgenden Knoten. Zum Beispiel:

     `/apps/the-project/components/text/cq:dialog`

Um eines von beiden zu erstellen, müssen Sie nur die Skelettstruktur neu erstellen. Um die Neuerstellung der Struktur zu vereinfachen, können alle dazwischenliegenden Knoten vom Typ `nt:unstructured` sein (sie müssen nicht dem ursprünglichen Knotentyp entsprechen). Zum Beispiel in `/libs`.

Im obigen Überlagerungsbeispiel werden daher die folgenden Knoten benötigt:

```shell
/apps
  /cq
    /core
      /content
        /nav
          /sites
```

>[!NOTE]
>
>Bei Verwendung von Sling Resource Merger (d. h. bei Verwendung der standardmäßigen Touch-optimierten Benutzeroberfläche) ist es nicht empfehlenswert, die gesamte Struktur aus `/libs` zu kopieren. Der Grund dafür ist, dass es dazu führen würde, dass zu viele Informationen in `/apps` gespeichert würden. Dies kann zu Problemen führen, wenn das System aktualisiert wird.

### Anwendungsfälle {#use-cases}

Mit der Standardfunktion können Sie in diesen Anwendungsfällen Folgendes tun:

* **Eigenschaft hinzufügen**

  Die Eigenschaft ist nicht in der `/libs` vorhanden, ist aber in der `/apps`-Überlagerung/-Überschreibung erforderlich.

   1. Erstellen Sie den entsprechenden Knoten in `/apps`.
   1. Erstellen Sie die neue Eigenschaft auf diesem Knoten.

* **Eigenschaft neu definieren (nicht automatisch erstellte Eigenschaften)**

  Die Eigenschaft ist in `/libs` definiert, aber für die `/apps`-Überlagerung/-Überschreibung ist ein neuer Wert erforderlich.

   1. Erstellen Sie den entsprechenden Knoten in `/apps`.
   1. Erstellen Sie die entsprechende Eigenschaft auf diesem Knoten (unter `apps`).

      * Die Eigenschaft hat eine Priorität, die auf der Konfiguration des Sling Resource Resolver basiert.
      * Das Ändern des Eigenschaftstyps wird unterstützt.

        Wenn Sie einen Eigenschaftstyp verwenden, der sich von dem in `/libs` verwendeten unterscheidet, wird der von Ihnen definierte Eigenschaftstyp verwendet.

  >[!NOTE]
  >
  >Das Ändern des Eigenschaftstyps wird unterstützt.

* **Automatisch erstellte Eigenschaft neu definieren**

  Standardmäßig unterliegen automatisch erstellte Eigenschaften (z. B. `jcr:primaryType`) keinen Überlagerungen/Überschreibungen, um sicherzustellen, dass der aktuell unter `/libs` befindliche Knotentyp respektiert wird. Um eine Überlagerung/Überschreibung vorzuschreiben, müssen Sie den Knoten in `/apps` neu erstellen, die Eigenschaft explizit ausblenden und neu definieren:

   1. Erstellen Sie den entsprechenden Knoten unter `/apps` mit dem gewünschten `jcr:primaryType`.
   1. Erstellen Sie die Eigenschaft `sling:hideProperties` auf diesem Knoten, wobei der Wert auf den Wert der automatisch erstellten Eigenschaft eingestellt ist, zum Beispiel `jcr:primaryType`.

      Diese Eigenschaft, die unter `/apps` definiert wird, hat jetzt Vorrang vor der Eigenschaft, die unter `/libs` definiert wurde

* **Knoten und zugehörige untergeordnete Elemente neu definieren**

  Der Knoten und seine untergeordneten Elemente sind in `/libs` definiert, aber in der `/apps`-Überlagerung/-Überschreibung wird eine neue Konfiguration benötigt.

   1. Kombinieren Sie folgende Aktionen:

      1. Untergeordnete Elemente eines Knotens ausblenden (wobei die Eigenschaften des Knotens beibehalten werden)
      1. Eigenschaft/Eigenschaften neu definieren

* **Eigenschaft ausblenden**

  Die Eigenschaft ist in `/libs` definiert, ist aber für die `/apps`-Überlagerung/-Überschreibung nicht erforderlich.

   1. Erstellen Sie den entsprechenden Knoten in `/apps`.
   1. Erstellen Sie eine Eigenschaft `sling:hideProperties` vom Typ `String` oder `String[]`. Dient zum Angeben der Eigenschaften, die ausgeblendet/ignoriert werden sollen. Platzhalter können auch verwendet werden. Beispiel:

      * `*`
      * `["*"]`
      * `jcr:title`
      * `["jcr:title", "jcr:description"]`

* **Knoten und zugehörige untergeordnete Elemente ausblenden**

  Der Knoten und seine untergeordneten Elemente sind in `/libs` definiert, aber für die `/apps` Überlagerung/Überschreibung nicht erforderlich.

   1. Erstellen Sie den entsprechenden Knoten unter `/apps`
   1. Erstellen Sie eine Eigenschaft `sling:hideResource`.

      * Typ: `Boolean`
      * Wert: `true`

* **Untergeordnete Elemente eines Knotens ausblenden (wobei die Eigenschaften des Knotens beibehalten werden)**

  Der Knoten, seine Eigenschaften und seine untergeordneten Elemente sind in `/libs` definiert. Der Knoten und seine Eigenschaften sind in der `/apps`-Überlagerung/-Überschreibung erforderlich, aber einige oder alle untergeordneten Knoten sind in der `/apps`-Überlagerung/-Überschreibung nicht erforderlich.

   1. Erstellen Sie den entsprechenden Knoten unter `/apps`
   1. Erstellen Sie die Eigenschaft `sling:hideChildren`:

      * Typ: `String[]`
      * Wert: eine Liste der auszublendenden/zu ignorierenden untergeordneten Knoten (wie in `/libs` definiert)

      Mit dem Platzhalter &ast; können Sie alle untergeordneten Knoten ausblenden oder ignorieren.

* **Knoten neu anordnen**

  Der Knoten und die ihm gleichrangigen Elemente sind in `/libs` definiert. Um die Reihenfolge zu ändern, erstellen Sie den Knoten in der `/apps` Überlagerung oder Überschreibung neu. Definieren Sie seine neue Position, indem Sie auf den entsprechenden gleichrangigen Knoten in `/libs` verweisen.


   * Verwenden Sie die Eigenschaft `sling:orderBefore`:

      1. Erstellen Sie den entsprechenden Knoten unter `/apps`
      1. Erstellen Sie die Eigenschaft `sling:orderBefore`:

         Gibt den Knoten (wie in `/libs`) an, vor dem der aktuelle Knoten positioniert ist:

         * Typ: `String`
         * Wert: `<before-SiblingName>`

### Rufen Sie den Sling Resource Merger aus Ihrem Code auf {#invoking-the-sling-resource-merger-from-your-code}

Der Sling Resource Merger umfasst zwei benutzerdefinierte Ressourcenanbieter – einen für Überlagerungen und einen für Überschreibungen. Jede kann innerhalb Ihres Codes mithilfe eines Bereitstellungspunkts aufgerufen werden:

>[!NOTE]
>
>Beim Zugriff auf die Ressource wird empfohlen, den entsprechenden Einhängepunkt zu verwenden.
>
>Dieser Ansatz ruft den Sling Resource Merger auf und gibt die vollständig zusammengeführte Ressource zurück. Außerdem wird der Umfang der Struktur reduziert, die Sie aus `/libs` kopieren müssen.

* Überlagerung:

   * Zweck: Ressourcen anhand ihrer Suchpfade zusammenführen
   * Einhängepunkt: `/mnt/overlay`
   * Anwendung: `mount point + relative path`
   * Beispiel:

      * `getResource('/mnt/overlay' + '<relative-path-to-resource>');`

* Überschreibung:

   * Zweck: Ressourcen anhand ihrer Supertypen zusammenführen
   * Einhängepunkt: `/mnt/overide`
   * Anwendung: `mount point + absolute path`
   * Beispiel:

      * `getResource('/mnt/override' + '<absolute-path-to-resource>');`

### Anwendungsbeispiel {#example-of-usage}

Einige Beispiele sind enthalten:

* Überlagerung:

   * [Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md)
   * [Anpassung des Seiten-Authorings](/help/sites-developing/customizing-page-authoring-touch.md)

* Überschreibung:

   * [Konfiguration von Seiteneigenschaften](/help/sites-developing/page-properties-views.md#configuring-your-page-properties)
