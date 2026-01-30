---
title: Query Builder-Prädikatsreferenz
description: Vollständiger Prädikatsverweis für die Query Builder-API.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
solution: Experience Manager, Experience Manager Sites
feature: Developing,Search,Query Builder
role: Developer
exl-id: c044d541-24d6-4975-9b38-6a4317a16358
source-git-commit: a85b54d5a7c3b00f95f439941a390dcfee883187
workflow-type: tm+mt
source-wordcount: '2291'
ht-degree: 65%

---

# Query Builder-Prädikatsreferenz{#query-builder-predicate-reference}

>[!CAUTION]
>
>Die Informationen auf dieser Seite erheben keinen Anspruch auf Vollständigkeit.
>
>Umfassende Informationen finden Sie in der Liste unter **Verfügbare Eigenschaften** in der Debugger-Konsole von Query Builder, zum Beispiel unter:
>* [http://localhost:4502/libs/cq/search/content/querydebug.html](http://localhost:4502/libs/cq/search/content/querydebug.html)
>
>Ein Beispiel finden Sie unter:
>
>* [http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29](http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29)

## Allgemein {#general}

* [root](#root)
* [group](#group)
* [orderby](#orderby)

## Prädikate {#predicates}

* [boolproperty](/help/sites-developing/querybuilder-predicate-reference.md#boolproperty)
* [contentfragment](/help/sites-developing/querybuilder-predicate-reference.md#contentfragment)
* [dateComparison](/help/sites-developing/querybuilder-predicate-reference.md#datecomparison)
* [daterange](/help/sites-developing/querybuilder-predicate-reference.md#daterange)
* [excludepaths](/help/sites-developing/querybuilder-predicate-reference.md#excludepaths)
* [fulltext](/help/sites-developing/querybuilder-predicate-reference.md#fulltext)
* [hasPermission](/help/sites-developing/querybuilder-predicate-reference.md#haspermission)
* [language](/help/sites-developing/querybuilder-predicate-reference.md#language)
* [mainasset](/help/sites-developing/querybuilder-predicate-reference.md#mainasset)
* [memberOf](/help/sites-developing/querybuilder-predicate-reference.md#memberof)
* [nodename](/help/sites-developing/querybuilder-predicate-reference.md#nodename)
* [notexpired](/help/sites-developing/querybuilder-predicate-reference.md#notexpired)
* [path](/help/sites-developing/querybuilder-predicate-reference.md#path)
* [property](/help/sites-developing/querybuilder-predicate-reference.md#property)
* [rangeproperty](/help/sites-developing/querybuilder-predicate-reference.md#rangeproperty)
* [relativedaterange](/help/sites-developing/querybuilder-predicate-reference.md#relativedaterange)
* [savedquery](/help/sites-developing/querybuilder-predicate-reference.md#savedquery)
* [similar](/help/sites-developing/querybuilder-predicate-reference.md#similar)
* [tag](/help/sites-developing/querybuilder-predicate-reference.md#tag)
* [tagid](/help/sites-developing/querybuilder-predicate-reference.md#tagid)
* [tagsearch](/help/sites-developing/querybuilder-predicate-reference.md#tagsearch)
* [Typ](/help/sites-developing/querybuilder-predicate-reference.md#type)

### `boolproperty` {#boolproperty}

Übereinstimmung mit JCR BOOLEAN-Eigenschaften. Akzeptiert nur die Werte &quot;`true`&quot; und &quot;`false`&quot;. Ist hierfür &quot;`false`&quot; festgelegt, liegt eine Übereinstimmung vor, wenn die Eigenschaft über den Wert &quot;`false`&quot; verfügt oder überhaupt nicht vorhanden ist. Dies ist nützlich, um auf boolesche Flags zu prüfen, die nur gesetzt werden, wenn sie aktiviert sind.

Der übernommene Parameter „`operation`“ hat keine Bedeutung.

Unterstützt die Facettenextraktion. Erstellt für jeden Wert (`true` oder `false`) einen Bucket, allerdings nur für vorhandene Eigenschaften.

#### Eigenschaften {#properties}

* **boolproperty**
Relativer Pfad der Eigenschaft, z. B. `myFeatureEnabled` oder `jcr:content/myFeatureEnabled`.

* **value**
Wert, auf den die Eigenschaft überprüft werden soll, &quot;`true`&quot; oder &quot;`false`&quot;.

### `contentfragment` {#contentfragment}

Beschränkt das Ergebnis auf Inhaltsfragmente.

Filtern wird nicht unterstützt.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-1}

* **contentfragment** Kann mit jedem Wert verwendet werden, um auf Inhaltsfragmente zu prüfen.

### `dateComparison` {#datecomparison}

Vergleicht zwei JCR DATE-Eigenschaften miteinander. Sie können testen, ob sie gleich, ungleich, größer oder größer-oder-gleich sind.

Ein reines Filterprädikat, das keinen Suchindex verwenden kann.

#### Eigenschaften {#properties-2}

* **property1**

  Pfad zur Eigenschaft mit dem ersten Datum.

* **property2**

  Pfad zur Eigenschaft mit dem zweiten Datum.

* **operation**

  „`equals`“ für genaue Übereinstimmung, „`!=`“ für unterschiedliche Werte, „`greater`“, wenn property1 größer ist als property2, „`>=`“, wenn property1 größer oder gleich property2 ist. Der Standardwert lautet &quot;`equals`.“

### `daterange` {#daterange}

Gleicht JCR DATE-Eigenschaften mit einem Datums- und Zeitintervall ab. Verwendet ISO8601
-Format für Datums- und Uhrzeitangaben (`YYYY-MM-DDTHH:mm:ss.SSSZ`) und ermöglicht auch partielle Darstellungen, z. B. `YYYY-MM-DD`. Alternativ kann der Zeitstempel als Anzahl von Millisekunden seit 1970 in der UTC-Zeitzone, dem UNIX®-Zeitformat, angegeben werden.

Sie können nach allen Elementen zwischen zwei Zeitstempeln suchen, nach allem, was neuer oder älter als ein jeweiliges Datum ist, und aus inklusiven oder offenen Intervallen auswählen.

Unterstützt die Facettenextraktion. Stellt die Buckets „heute“, „diese Woche“, „diesen Monat“, „letzte 3 Monate“, „dieses Jahr“, „letztes Jahr“ und „früher als letztes Jahr“ bereit.

Filtern wird nicht unterstützt.

#### Eigenschaften {#properties-3}

* **property**

  Relativer Pfad zu einer `DATE`-Eigenschaft, z. B. `jcr:lastModified`.

* **lowerBound**

  Untere Datumsgrenze, auf welche die Eigenschaft überprüft werden soll, z. B. `2014-10-01`

* **lowerOperation**

  „`>`“ (neuer) oder „`>=`“ (gleich alt oder neuer), gilt für `lowerBound`. Der Standardwert lautet &quot;`>`.“

* **upperBound**

  Obere Datumsgrenze, auf welche die Eigenschaft überprüft werden soll, z. B. `2014-10-01T12:15:00`.

* **upperOperation**

  „`<`“ (älter) oder „`<=`“ (gleich alt oder älter), gilt für `upperBound`. Der Standardwert lautet &quot;`<`.“

* **timeZone**

  Kennung der Zeitzone, die verwendet werden soll, wenn keine ISO-8601-Datumszeichenfolge angegeben wird. Der Standardwert ist die standardmäßige Zeitzone des Systems.

### `excludepaths` {#excludepaths}

Schließt Knoten aus dem Ergebnis aus, wenn ihr Pfad mit einem regulären Ausdruck übereinstimmt.

Ein reines Filterprädikat, das keinen Suchindex verwenden kann.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-4}

* **excludepaths**

  Regulärer Ausdruck, der anhand von Ergebnispfaden ausgewertet wird, wobei übereinstimmende Vorkommen aus dem Ergebnis ausgeschlossen werden.

### `fulltext` {#fulltext}

Sucht nach Ausdrücken im Volltextindex.

Filtern wird nicht unterstützt.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-5}

* **fulltext**

  Die Volltext-Suchbegriffe.

* **relPath**

  Der relative Pfad, der in der Eigenschaft oder dem Unterknoten durchsucht werden soll. Diese Eigenschaft ist optional.

### `group` {#group}

Ermöglicht das Erstellen verschachtelter Bedingungen. Gruppen können verschachtelte Gruppen enthalten. Alles in einer Query Builder-Abfrage gehört implizit zu einer Stammgruppe, die auch die Parameter `p.or` und `p.not` aufweisen kann.

Beispiel für die Zuordnung einer von zwei Eigenschaften anhand eines Werts:

```
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Konzeptionell `(1_property` ODER `2_property)`.

Beispiel für verschachtelte Gruppen:

```
fulltext=Management
group.p.or=true
group.1_group.path=/content/geometrixx/en
group.1_group.type=cq:Page
group.2_group.path=/content/dam/geometrixx
group.2_group.type=dam:Asset
```

Sucht nach dem Begriff &quot;**Management** innerhalb von Seiten in `/content/geometrixx/en` oder in Assets in `/content/dam/geometrixx`.

Konzeptionell `fulltext AND ( (path AND type) OR (path AND type) )`. Solche ODER-Verknüpfungen sind aus Leistungsgründen auf gute Indizes angewiesen.

#### Eigenschaften {#properties-6}

* **p.or**

  Ist hierfür &quot;`true`&quot; festgelegt, muss nur ein Prädikat in der Gruppe übereinstimmen. Standardmäßig ist &quot;`false`&quot; festgelegt, was bedeutet, dass alle übereinstimmen müssen.

* **p.not**

  Ist hierfür &quot;`true`&quot; festgelegt, wird die Gruppe nicht beachtet (standardmäßig &quot;`false`„).

* **&lt;predicate>**

  Fügt verschachtelte Prädikate hinzu.

* **N_&lt;predicate>**

  Fügt mehrere verschachtelte Prädikate gleichzeitig hinzu, z. B. `1_property, 2_property, ...`.

### hasPermission {#haspermission}

Beschränkt das Ergebnis auf Elemente, bei denen die aktuelle Sitzung die angegebenen [JCR-Privilegien](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges) aufweist.

Ein reines Filterprädikat, das keinen Suchindex verwenden kann. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-7}

* **hasPermission**

  Kommagetrennte JCR-Berechtigungen, die die aktuelle Benutzersitzung für den jeweiligen Knoten ALLE aufweisen muss. Zum Beispiel, `jcr:write`, `jcr:modifyAccessControl`.

### `language` {#language}

Findet CQ-Seiten in einer bestimmten Sprache. Hierbei wird sowohl die Spracheigenschaft der Seite als auch der Seitenpfad betrachtet, der häufig die Sprache oder das Gebietsschema in einer Site-Struktur der obersten Ebene enthält.

Ein reines Filterprädikat, das keinen Suchindex verwenden kann.

Unterstützt die Facettenextraktion. Stellt Buckets für jeden eindeutigen Sprach-Code zur Verfügung.

#### Eigenschaften {#properties-8}

* **language**

  ISO-Sprach-Code, z. B. &quot;`de`.“

### `mainasset` {#mainasset}

Prüft, ob ein Knoten ein DAM-Haupt-Asset und kein Unter-Asset ist. Im Prinzip befindet sich jeder Knoten nicht in einem „Unter-Assets“-Knoten. Es wird nicht auf den `dam:Asset` Knotentyp geprüft. Um dieses Prädikat zu verwenden, setzen Sie &quot;`mainasset=true`&quot; oder &quot;`mainasset=false`&quot;, es gibt keine weiteren Eigenschaften.

Ein reines Filterprädikat, das keinen Suchindex verwenden kann.

Es unterstützt die Facettenextraktion und bietet zwei Buckets für Haupt- und Unter-Assets.

#### Eigenschaften {#properties-9}

* **mainasset**

  Boolean, „`true`“ für Haupt-Assets, „`false`“ für Unter-Assets.

### memberOf {#memberof}

Sucht Objekte, die Mitglieder einer bestimmten [Sling-Ressourcensammlung](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) sind.

Ein reines Filterprädikat, das keinen Suchindex verwenden kann. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-10}

* **memberOf**

  Pfad der Sling-Ressourcensammlung.

### `nodename` {#nodename}

Sucht nach Namen von JCR-Knoten.

Unterstützt die Facettenextraktion. Stellt Buckets für alle eindeutigen Knotennamen (Dateinamen) zur Verfügung.

#### Eigenschaften {#properties-11}

* **nodename**

  Knotennamenmuster, das Platzhalter ermöglicht: `*` = beliebiges oder kein Zeichen, `?` = beliebiges Zeichen, `[abc]` = nur Zeichen in eckigen Klammern.

### `notexpired` {#notexpired}

Wertet Elemente aus, indem überprüft wird, ob eine JCR DATE-Eigenschaft größer oder gleich der aktuellen Server-Zeit ist. Kann verwendet werden, um eine Datumseigenschaft wie &quot;`expiresAt`&quot; zu überprüfen und das Ergebnis auf diejenigen zu beschränken, die noch nicht abgelaufen sind ( `notexpired=true`) bzw. bereits abgelaufen sind ( `notexpired=false`).

Filtern wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie das Prädikat „daterange“.

#### Eigenschaften {#properties-12}

* **notexpired**

  Boolescher Wert, „`true`“ für noch nicht abgelaufen (Datum in der Zukunft oder gleich), „`false`“ für abgelaufen (Datum in der Vergangenheit) (erforderlich).

* **property**

  Relativer Pfad zur zu überprüfenden `DATE`-Eigenschaft (erforderlich).

### `orderby` {#orderby}

Sortiert die Ergebnisse. Wenn nach mehreren Eigenschaften sortiert werden muss, muss dieses Prädikat unter Verwendung des numerischen Präfixes mehrfach hinzugefügt werden, z. B. `1_orderby=first`, `2_oderby=second`.

#### Eigenschaften {#properties-13}

* **orderby**

  Entweder der JCR-Eigenschaftsname, angezeigt durch ein vorangestelltes „@“, z. B. `@jcr:lastModified` bzw. `@jcr:content/jcr:title`, oder ein anderes Prädikat in der Abfrage, z. B. `2_property`, nach dem sortiert werden soll.

* **sort**

  Sortierrichtung, entweder „`desc`“ für absteigend oder „`asc`“ für aufsteigend (Standard).

* **case**

  Wird hierfür `ignore` festgelegt, wird die Groß-/Kleinschreibung nicht beachtet, „a“ kommt also vor „B“. Wird dies leer- oder ausgelassen, wird bei der Sortierung die Groß-/Kleinschreibung beachtet, „B“ kommt also vor „a“

### `path` {#path}

Sucht innerhalb eines angegebenen Pfads.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-14}

* **path**

  Pfadmuster. Wenn `exact=false` (Standard), stimmt die Suche mit dem gesamten Teilbaum unter dem angegebenen Pfad überein - ähnlich wie beim Anhängen von `//*` in XPath, wobei der Basispfad selbst nicht einbezogen wird. Wenn `exact=true`, stimmt die Suche nur mit dem exakten Pfad überein, der `*` Platzhalter enthalten kann. Wenn `self` festgelegt ist, umfasst die Suche den Basisknoten und die gesamte Unterstruktur.


* **exact**

  Wenn `exact` den Wert „true“ hat (aktiviert), muss der exakte Pfad übereinstimmen, darf aber bestimmte einfache Platzhalter ( `*`) enthalten, die Namen entsprechen, aber nicht &quot;`/`&quot;. Wenn der Wert „false“ ist (Standard), werden alle untergeordneten Elemente berücksichtigt (optional).

* **flat**

  Durchsucht nur die direkt untergeordneten Elemente (wie wenn in `/*` &quot;`xpath`&quot; angehängt wird). Wird nur verwendet, wenn &quot;`exact`&quot; nicht „true“ ist (optional).

* **self**

  Durchsucht die Unterstruktur, aber bezieht den als Pfad angegebenen Basisknoten mit ein (keine Platzhalter).

### `property` {#property}

Führt einen Abgleich von JCR-Eigenschaften und ihren Werten durch.

Unterstützt die Facettenextraktion. Stellt für jeden eindeutigen Eigenschaftswert in den Ergebnissen Buckets zur Verfügung.

#### Eigenschaften {#properties-15}

* **property**

  Relativer Pfad zur Eigenschaft, z. B. `jcr:title`.

* **value**

  Wert, auf den die Eigenschaft geprüft werden soll. Folgt dem JCR-Eigenschaftstyp bei der Konvertierung von Zeichenfolgen.

* **N_value**

  Verwenden Sie `1_value`, `2_value`, …, um auf mehrere Werte zu prüfen (standardmäßig kombiniert mit `OR`, mit `AND`, wenn „and=true“) (seit 5.3).

* **and**

  Legen Sie hierfür „true“ fest, um mehrere Werte (`N_value`) mit AND zu kombinieren (seit 5.3).

* **operation**

  Verwenden Sie `equals` für eine exakte Übereinstimmung (Standard) und `unequals` für einen Ungleichheitsvergleich. Verwenden Sie `like`, um die optionale XPath-Funktion `jcr:like` anzuwenden. Verwenden Sie `not` für keine Übereinstimmung (z. B. `not(@prop)` in XPath). In diesem Fall wird der `value` ignoriert. Verwenden Sie `exists`, um zu überprüfen, ob eine Eigenschaft vorhanden ist: `true` (Standard) erfordert die Eigenschaft und `false` entspricht `not`.

* **depth**

  Eine Reihe von Platzhalterebenen, unter denen die Eigenschaft und der relative Pfad vorhanden sein können. `property=size depth=2` überprüft beispielsweise Knoten und Größe, Knoten/&amp;ast;/size und Knoten/&amp;ast;/&amp;ast;/size.

### `rangeproperty` {#rangeproperty}

Ordnet eine JCR-Eigenschaft einem Intervall zu. Gilt für Eigenschaften mit linearen Typen wie `LONG`, `DOUBLE` und `DECIMAL`. Details zu `DATE` finden Sie im Abschnitt zum Prädikat „daterange“, das für Eingaben im Datumsformat optimiert wurde.

Sie können eine untere Grenze und eine obere Grenze oder nur eine von beiden definieren. Die Operation (z. B. „lesser than“ oder „lesser or equals“) kann auch einzeln für die untere und obere Grenze festgelegt werden.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-16}

* **property**

  Relativer Pfad zur Eigenschaft.

* **lowerBound**

  Untere Grenze, auf die „property“ geprüft werden soll.

* **lowerOperation**

  &quot;`>`&quot; (Standard) oder &quot;`>=`&quot;, gilt für die `lowerValue`

* **upperBound**

  Obere Grenze, auf die „property“ geprüft werden soll.

* **upperOperation**

  &quot;`<`&quot; (Standard) oder &quot;`<=`&quot;, gilt für die `lowerValue`

* **decimal**

   „`true`“, wenn die aktivierte Eigenschaft vom Typ „Decimal“ ist.

### `relativedaterange` {#relativedaterange}

Gleicht `JCR DATE` Eigenschaften anhand von Zeit-Offsets, die relativ zur aktuellen Serverzeit sind, mit einem Datums- und Zeitintervall ab. Sie können `lowerBound` und `upperBound` entweder mit einem Millisekundenwert oder dem `1s 2m 3h 4d 5w 6M 7y` der Bugzilla-Syntax angeben. Mit dem Präfix „`-`“ geben Sie einen negativen Offset vor der aktuellen Zeit an. Wenn Sie nur `lowerBound` oder `upperBound` angeben, wird für die jeweils andere Grenze standardmäßig „0“ festgelegt (bedeutet die aktuelle Zeit).

Beispiel:

* `upperBound=1h` (und keine `lowerBound`) wählt alles in der folgenden Stunde aus.
* `lowerBound=-1d` (und keine `upperBound`) wählt alles in den vergangenen 24 Stunden aus.
* `lowerBound=-6M` und `upperBound=-3M` wählt alles aus, was zwischen sechs und drei Monaten alt ist.
* `lowerBound=-1500` und `upperBound=5500` wählt alles aus, was im Zeitraum zwischen einschließlich 1500 Millisekunden in der Vergangenheit und einschließlich 5500 Millisekunden in der Zukunft liegt. 
* `lowerBound=1d` und `upperBound=2d` wählt alles am übernächsten Tag aus.

Schaltjahre werden nicht berücksichtigt, und alle Monate haben 30 Tage.

Filtern wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie das Prädikat „daterange“.

#### Eigenschaften {#properties-17}

* **upperBound**

  Obere Datumsgrenze in Millisekunden oder `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) relativ zur aktuellen Server-Zeit. Verwenden Sie „-“ für einen negativen Offset.

* **lowerBound**

  Untere Datumsgrenze in Millisekunden oder `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) relativ zur aktuellen Server-Zeit. Verwenden Sie „-“ für einen negativen Offset.

### `root` {#root}

Stammprädikatgruppe. Es unterstützt alle Funktionen einer Gruppe und ermöglicht das Festlegen globaler Abfrageparameter.

Der Name „root“ wird in Abfragen nie verwendet, er ist implizit.

#### Eigenschaften {#properties-18}

* **p.offset**

  Zahl, die den Anfang der Ergebnisseite anzeigt, d. h., wie viele Elemente übersprungen werden sollen.

* **p.limit**

  Zahl, die die Seitengröße angibt.

* **p.guessTotal**

  Um die Kosten für die Berechnung des vollständigen Ergebnisses zu vermeiden, zählen Sie nicht alle Übereinstimmungen. Legen Sie stattdessen einen maximalen Gesamtwert fest, der bis gezählt werden soll (z. B. `1000`), um Benutzern eine ungefähre Größe und exakte Gesamtwerte für kleinere Ergebnisse zu liefern. Oder setzen Sie sie auf `true` , um nur bis zum erforderlichen Minimum zu zählen: `p.offset + p.limit`.


* **p.excerpt**

  Ist hierfür &quot;`true`&quot; festgelegt, wird dem Ergebnis ein Volltextauszug hinzugefügt.

* **p.hits**

   (nur für das JSON-Servlet) Legt fest, wie Treffer als JSON geschrieben werden. Folgende Standardmethoden stehen zur Auswahl (erweiterbar über den Dienst „ResultHitWriter“):

   * **einfach**:

     Minimale Elemente wie `path`, `title`, `lastmodified`, `excerpt` (falls festgelegt).

   * **vollständig**:

     Die Ergebnisse werden für jeden Knoten als Sling-JSON gerendert, wobei `jcr:path` den Trefferpfad anzeigt. Standardmäßig umfasst die Antwort nur die direkten Eigenschaften des Knotens. Verwenden Sie `p.nodedepth=N`, um tiefere Inhalte einzuschließen, wobei `0` die gesamte Unterstruktur zurückgibt. Legen Sie `p.acls=true` fest, um die JCR-Berechtigungen der aktuellen Sitzung für jedes Element einzuschließen (`create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).


   * **selective**:

     Die Antwort enthält nur die in `p.properties` aufgelisteten Eigenschaften. Dabei handelt es sich um eine durch Leerzeichen getrennte Liste relativer Pfade (`+` in URLs). Wenn ein relativer Pfad eine Tiefe größer als 1 hat, wird er von der Ausgabe als untergeordnete Objekte verschachtelt. Die `jcr:path`-Eigenschaft enthält immer den Trefferpfad.


### `savedquery` {#savedquery}

Sie schließt alle Prädikate einer beständigen Query Builder-Abfrage als Untergruppenprädikat in die aktuelle Abfrage ein.

Es wird keine zusätzliche Abfrage ausgeführt, sondern die aktuelle Abfrage erweitert.

Abfragen können programmgesteuert anhand von `QueryBuilder#storeQuery()` persistiert werden. Das Format kann entweder eine String-Eigenschaft mit mehreren Zeilen oder ein `nt:file`-Knoten sein, der die Abfrage als Textdatei im Java™-Eigenschaftsformat enthält.

Die Facettenextraktion wird für die Prädikate der gespeicherten Abfrage nicht unterstützt.

#### Eigenschaften {#properties-19}

* **savedquery**

  Pfad zur gespeicherten Abfrage (String-Eigenschaft oder `nt:file`-Knoten).

### `similar` {#similar}

Ähnlichkeitssuche mithilfe der `rep:similar()` () von JCR XPath.

Filtern wird nicht unterstützt. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-20}

* **similar**
Absoluter Pfad zum Knoten, für den ähnliche Knoten gefunden werden sollen.

* **local**
Ein relativer Pfad zu einem untergeordneten Knoten oder `.` für den aktuellen Knoten (optional; der Standard lautet `.`).

### `tag` {#tag}

Sucht nach Inhalten mit Tags, indem Tag-Titelpfade angegeben werden.

Unterstützt die Facettenextraktion. Stellt Buckets für jedes einzigartige Tag bereit. Dazu wird jeweils der aktuelle Tag-Titelpfad verwendet.

#### Eigenschaften {#properties-21}

* **tag**

  Tag-Titelpfad, nach dem gesucht werden soll, z. B. „Asset-Eigenschaften: Ausrichtung/Querformat“.

* **N_value**

  Verwenden Sie `1_value`, `2_value` …, um auf mehrere Tags zu prüfen (standardmäßig kombiniert mit `OR`; wenn and=true, dann mit `AND`) (seit 5.6).

* **property**

  Eigenschaft (bzw. relativer Pfad zur Eigenschaft), die betrachtet werden soll (Standard: `cq:tags`)

### `tagid` {#tagid}

Dieses Prädikat sucht nach Inhalten mit Tags, indem Tag-IDs angegeben werden.

Unterstützt die Facettenextraktion. Stellt Buckets für jedes einzigartige Tag bereit. Dazu wird jeweils die aktuelle Tag-ID verwendet.

#### Eigenschaften {#properties-22}

* **tagid**

  Tag-ID, sodass Sie z. B. nach &quot;`properties:orientation/landscape`&quot; suchen können.

* **N_value**

  Verwenden Sie `1_value`, `2_value`, …, um auf mehrere `tagids` zu prüfen (standardmäßig kombiniert mit `OR`, `AND` wenn and=„true“, dann mit ) (seit 5.6).

* **property**

  Eigenschaft (bzw. relativer Pfad zur Eigenschaft), die betrachtet werden soll (Standard: `cq:tags`).

### `tagsearch` {#tagsearch}

Dieses Prädikat sucht nach Inhalten mit Tags, indem Keywords angegeben werden. Sucht zuerst nach Tags, die diese Keywords in ihren Titeln enthalten, und beschränkt das Ergebnis dann auf Elemente mit Tags.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#Properties-1}

* **tagsearch**

  Suchbegriff, nach dem in Tag-Titeln gesucht werden soll.

* **property**

  Eigenschaft (bzw. relativer Pfad zur Eigenschaft), die betrachtet werden soll (Standard: `cq:tags`).

* **lang**

  Zum Suchen nur in einem bestimmten lokalisierten Tag-Titel (z. B. `de`).

* **all**

  (bool) Suchen im gesamten Tag-Volltext, d. h. alle Titel, Beschreibungen usw. hat Vorrang vor „l `ang`&quot;.

### `type` {#type}

Beschränkt Ergebnisse auf einen bestimmten JCR-Knotentyp, sowohl auf den primären Knotentyp als auch auf den Mixin-Typ, und findet Untertypen dieses Knotentyps. Die Indizes der Repository-Suche müssen die Knotentypen abdecken, um eine effiziente Ausführung zu gewährleisten.

Unterstützt die Facettenextraktion. Stellt Buckets für jeden eindeutigen Typ in den Ergebnissen bereit.

#### Eigenschaften {#Properties-2}

* **Typ**

  Knotentyp bzw. Mixin-Name, nach dem gesucht werden soll, z. B. `cq:Page`.
