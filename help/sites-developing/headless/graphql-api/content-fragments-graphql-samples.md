---
title: Erfahren Sie, wie Sie GraphQL mit AEM verwenden – Beispielinhalt und Abfragen
description: Erfahren Sie, wie Sie GraphQL mit AEM verwenden, um „headless“-Inhalte bereitzustellen, indem Sie Beispielinhalte und Abfragen untersuchen.
feature: Content Fragments,GraphQL API
solution: Experience Manager, Experience Manager Sites
role: Developer
exl-id: 9a953caa-47d3-4e06-a27d-2a0c3fc72597
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1588'
ht-degree: 100%

---

# Verwenden von GraphQL mit AEM – Beispielinhalt und Abfragen {#learn-graphql-with-aem-sample-content-queries}

Erfahren Sie, wie Sie GraphQL mit AEM verwenden, um „headless“-Inhalte bereitzustellen, indem Sie Beispielinhalte und Abfragen untersuchen.

>[!NOTE]
>
>Diese Seite sollte zusammen mit folgenden Themen gelesen werden:
>
>* [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md)
>* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
>* [AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md)

Für den Einstieg in GraphQL-Abfragen und deren Verwendung mit AEM-Inhaltsfragmenten sind einige praktische Beispiele hilfreich.

Sehen Sie dazu:

* eine [Beispielstruktur für Inhaltsfragmente](#content-fragment-structure-graphql)

* und einige [GraphQL-Beispielabfragen](#graphql-sample-queries), die auf der Beispielstruktur für Inhaltsfragmente basieren (Inhaltsfragmentmodelle und verwandte Inhaltsfragmente).


## GraphQL – Beispielabfragen unter Verwendung der Beispielstruktur für Inhaltsfragmente {#graphql-sample-queries-sample-content-fragment-structure}

In diesen Beispielabfragen wird das Erstellen von Abfragen zusammen mit Beispielergebnissen veranschaulicht.

>[!NOTE]
>
>Abhängig von Ihrer Instanz können Sie direkt auf die in der [AEM-GraphQL-API enthaltene GraphiQL-Schnittstelle](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#graphiql-interface) zugreifen, um Abfragen zu senden und zu testen.
>
>Beispiel: `http://localhost:4502/content/graphiql.html`

>[!NOTE]
>
>Die Beispielabfragen basieren auf der [Beispielstruktur für Inhaltsfragmente zur Verwendung mit GraphQL](#content-fragment-structure-graphql).

### Beispielabfrage – Alle verfügbaren Schemata und Datentypen {#sample-all-schemes-datatypes}

Diese Beispielabfrage gibt alle `types` für alle verfügbaren Schemata zurück.

**Beispielabfrage**

```graphql
{
  __schema {
    types {
      name
      description
    }
  }
}
```

**Beispielergebnis**

```json
{
  "data": {
    "__schema": {
      "types": [
        {
          "name": "AdventureModel",
          "description": null
        },
        {
          "name": "AdventureModelArrayFilter",
          "description": null
        },
        {
          "name": "AdventureModelFilter",
          "description": null
        },
        {
          "name": "AdventureModelResult",
          "description": null
        },
        {
          "name": "AdventureModelResults",
          "description": null
        },
        {
          "name": "AllFragmentModels",
          "description": null
        },
        {
          "name": "ArchiveRef",
          "description": null
        },
        {
          "name": "ArrayMode",
          "description": null
        },
        {
          "name": "ArticleModel",
          "description": null
        },

...more results...

        {
          "name": "__EnumValue",
          "description": null
        },
        {
          "name": "__Field",
          "description": null
        },
        {
          "name": "__InputValue",
          "description": null
        },
        {
          "name": "__Schema",
          "description": "A GraphQL Introspection defines the capabilities of a GraphQL server. It exposes all available types and directives on the server, the entry points for query, mutation, and subscription operations."
        },
        {
          "name": "__Type",
          "description": null
        },
        {
          "name": "__TypeKind",
          "description": "An enum describing what kind of type a given __Type is"
        }
      ]
    }
  }
}
```

### Beispielabfrage – Alle Informationen zu allen Städten {#sample-all-information-all-cities}

Um alle Informationen zu allen Städten abzurufen, können Sie die grundlegende Abfrage verwenden:
**Beispielabfrage**

```graphql
{
  cityList {
    items
  }
}
```

Wenn die Abfrage ausgeführt wird, erweitert das System sie automatisch, um alle Felder einzuschließen:

```graphql
{
  cityList {
    items {
      _path
      name
      country
      population
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "_path": "/content/dam/sample-content-fragments/cities/basel",
          "name": "Basel",
          "country": "Switzerland",
          "population": 172258
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/berlin",
          "name": "Berlin",
          "country": "Germany",
          "population": 3669491
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/bucharest",
          "name": "Bucharest",
          "country": "Romania",
          "population": 1821000
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/san-francisco",
          "name": "San Francisco",
          "country": "USA",
          "population": 883306
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/san-jose",
          "name": "San Jose",
          "country": "USA",
          "population": 1026350
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/stuttgart",
          "name": "Stuttgart",
          "country": "Germany",
          "population": 634830
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/zurich",
          "name": "Zurich",
          "country": "Switzerland",
          "population": 415367
        }
      ]
    }
  }
}
```

### Beispielabfrage – Namen aller Städte {#sample-names-all-cities}

Diese Beispielabfrage ist eine unkomplizierte Abfrage, um den `name`aller Einträge im `city`-Schema zurückzugeben.

**Beispielabfrage**

```xmgraphqll
query {
  cityList {
    items {
      name
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Basel"
        },
        {
          "name": "Berlin"
        },
        {
          "name": "Bucharest"
        },
        {
          "name": "San Francisco"
        },
        {
          "name": "San Jose"
        },
        {
          "name": "Stuttgart"
        },
        {
          "name": "Zurich"
        }
      ]
    }
  }
}
```

### Beispielabfrage – ein Einzelstadtfragment {#sample-single-specific-city-fragment}

Diese Beispielabfrage ist eine Abfrage, um die Details eines einzelnen Fragmenteintrags an einem bestimmten Speicherort im Repository zurückzugeben.

**Beispielabfrage**

```graphql
{
  cityByPath (_path: "/content/dam/sample-content-fragments/cities/berlin") {
    item {
      _path
      name
      country
      population
     categories
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityByPath": {
      "item": {
        "_path": "/content/dam/sample-content-fragments/cities/berlin",
        "name": "Berlin",
        "country": "Germany",
        "population": 3669491,
        "categories": [
          "city:capital",
          "city:emea"
        ]
      }
    }
  }
}
```

### Beispielabfrage – alle Städte mit einer gegebenen Variante {#sample-cities-named-variation}

Wenn Sie eine Variante mit dem Namen „Berlin Centre“ (`berlin_centre`) für `city` Berlin erstellen, können Sie eine Abfrage verwenden, um Details zur Variante zurückzugeben.

**Beispielabfrage**

```graphql
{
  cityList (variation: "berlin_center") {
    items {
      _path
      name
      country
      population
      categories
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "_path": "/content/dam/sample-content-fragments/cities/berlin",
          "name": "Berlin",
          "country": "Germany",
          "population": 3669491,
          "categories": [
            "city:capital",
            "city:emea"
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage – Namen aller Städte, die als Städtereisen markiert sind {#sample-names-all-cities-tagged-city-breaks}

Wenn Sie:

* eine Vielzahl von Tags namens `Tourism` erstellen: `Business`, `City Break`, `Holiday`
* und sie diese Tags der übergeordneten Variante verschiedener `City`-Instanzen zuweisen

Dann können Sie eine Abfrage verwenden, um Details zu `name` und `tags` aller Einträge mit dem Tag „Städtereisen“ im Schema `city` herauszugeben.

**Beispielabfrage**

```graphql
query {
  cityList(
    includeVariations: true,
    filter: {_tags: {_expressions: [{value: "tourism:city-break", _operator: CONTAINS}]}}
  ){
    items {
      name,
      _tags
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Berlin",
          "_tags": [
            "tourism:city-break",
            "tourism:business"
          ]
        },
        {
          "name": "Zurich",
          "_tags": [
            "tourism:city-break",
            "tourism:business"
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage – Vollständige Details des CEO und der Mitarbeiter einer Firma {#sample-full-details-company-ceos-employees}

Unter Verwendung der Struktur der verschachtelten Fragmente gibt diese Abfrage die vollständigen Details des CEO eines Unternehmens und aller seiner Mitarbeiter zurück.

**Beispielabfrage**

```graphql
query {
  companyList {
    items {
      name
      ceo {
        _path
        name
        firstName
        awards {
        id
          title
        }
      }
      employees {
       name
        firstName
       awards {
         id
          title
        }
      }
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "Apple Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/steve-jobs",
            "name": "Jobs",
            "firstName": "Steve",
            "awards": []
          },
          "employees": [
            {
              "name": "Marsh",
              "firstName": "Duke",
              "awards": []
            },
            {
              "name": "Caulfield",
              "firstName": "Max",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                }
              ]
            }
          ]
        },
        {
          "name": "Little Pony, Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/adam-smith",
            "name": "Smith",
            "firstName": "Adam",
            "awards": []
          },
          "employees": [
            {
              "name": "Croft",
              "firstName": "Lara",
              "awards": [
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            },
            {
              "name": "Slade",
              "firstName": "Cutter",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                },
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            }
          ]
        },
        {
          "name": "NextStep Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/steve-jobs",
            "name": "Jobs",
            "firstName": "Steve",
            "awards": []
          },
          "employees": [
            {
              "name": "Smith",
              "firstName": "Joe",
              "awards": []
            },
            {
              "name": "Lincoln",
              "firstName": "Abraham",
              "awards": []
            }
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage – Alle Personen mit dem Namen „Jobs“ oder „Smith“ {#sample-all-persons-jobs-smith}

Diese Beispielabfrage filtert alle `persons` nach allen, die den Namen `Jobs` oder `Smith` haben.

**Beispielabfrage**

```graphql
query {
  personList(filter: {
    name: {
      _logOp: OR
      _expressions: [
        {
          value: "Jobs"
        },
        {
          value: "Smith"
        }
      ]
    }
  }) {
    items {
      name
      firstName
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "personList": {
      "items": [
        {
          "name": "Smith",
          "firstName": "Adam"
        },
        {
          "name": "Smith",
          "firstName": "Joe"
        },
        {
          "name": "Jobs",
          "firstName": "Steve"
        }
      ]
    }
  }
}
```

### Beispielabfrage – Alle Personen, die nicht den Namen „Jobs“ haben  {#sample-all-persons-not-jobs}

Diese Beispielabfrage filtert alle `persons` nach allen, die den Namen `Jobs` oder `Smith` haben.

**Beispielabfrage**

```graphql
query {
  personList(filter: {
    name: {
      _expressions: [
        {
          value: "Jobs"
          _operator: EQUALS_NOT
        }
      ]
    }
  }) {
    items {
      name
      firstName
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "personList": {
      "items": [
        {
          "name": "Lincoln",
          "firstName": "Abraham"
        },
        {
          "name": "Smith",
          "firstName": "Adam"
        },
        {
          "name": "Slade",
          "firstName": "Cutter"
        },
        {
          "name": "Marsh",
          "firstName": "Duke"
        },
        {
          "name": "Smith",
          "firstName": "Joe"
        },
        {
          "name": "Croft",
          "firstName": "Lara"
        },
        {
          "name": "Caulfield",
          "firstName": "Max"
        }
      ]
    }
  }
}
```

### Beispielabfrage – Alle Abenteuer, deren `_path` mit einem bestimmten Präfix beginnt {#sample-wknd-all-adventures-cycling-path-filter}

Alle `adventures`, bei denen `_path` mit einem bestimmten Präfix (`/content/dam/wknd/en/adventures/cycling`) beginnt.

**Beispielabfrage**

```graphql
query {
  adventureList(
    filter: {
      _path: {
        _expressions: [
        {
          value: "/content/dam/wknd/en/adventures/cycling"
         _operator: STARTS_WITH
        }]
       }
    })
    {
    items {
      _path
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "adventureList": {
      "items": [
        {
          "_path": "/content/dam/wknd/en/adventures/cycling-southern-utah/cycling-southern-utah"
        },
        {
          "_path": "/content/dam/wknd/en/adventures/cycling-tuscany/cycling-tuscany"
        }
      ]
    }
  }
}
```

### Beispielabfrage – Alle Städte in Deutschland oder der Schweiz mit einer Einwohnerzahl zwischen 400.000 und 999.999 {#sample-all-cities-d-ch-population}

Hier wird nach einer Kombination von Feldern gefiltert. Ein `AND` (implizit) wird verwendet, um den `population`-Bereich auszuwählen, während ein `OR` (explizit) zur Auswahl der erforderlichen Städte verwendet wird.

**Beispielabfrage**

```graphql
query {
  cityList(filter: {
    population: {
      _expressions: [
        {
          value: 400000
          _operator: GREATER_EQUAL
        }, {
          value: 1000000
          _operator: LOWER
        }
      ]
    },
    country: {
      _logOp: OR
      _expressions: [
        {
          value: "Germany"
        }, {
          value: "Switzerland"
        }
      ]
    }
  }) {
    items {
      name
      population
      country
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Stuttgart",
          "population": 634830,
          "country": "Germany"
        },
        {
          "name": "Zurich",
          "population": 415367,
          "country": "Switzerland"
        }
      ]
    }
  }
}
```

### Beispielabfrage – Alle Städte mit SAN im Namen, unabhängig von der Groß-/Kleinschreibung {#sample-all-cities-san-ignore-case}

Diese Abfrage durchsucht alle Städte mit `SAN` im Namen, unabhängig von der Groß-/Kleinschreibung.

**Beispielabfrage**

```graphql
query {
  cityList(filter: {
    name: {
      _expressions: [
        {
          value: "SAN"
          _operator: CONTAINS
          _ignoreCase: true
        }
      ]
    }
  }) {
    items {
      name
      population
      country
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA"
        },
        {
          "name": "San Jose",
          "population": 1026350,
          "country": "USA"
        }
      ]
    }
  }
}
```

### Beispielabfrage – Filtern eines Arrays nach einem Element, das mindestens einmal vorkommen muss {#sample-array-item-occur-at-least-once}

Diese Abfrage filtert ein Array nach einem Element (`city:na`), das mindestens einmal vorkommen muss.

**Beispielabfrage**

```graphql
query {
  cityList(filter: {
    categories: {
      _expressions: [
        {
          value: "city:na"
          _apply: AT_LEAST_ONCE
        }
      ]
    }
  }) {
    items {
      name
      population
      country
      categories
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA",
          "categories": [
            "city:beach",
            "city:na"
          ]
        },
        {
          "name": "San Jose",
          "population": 1026350,
          "country": "USA",
          "categories": [
            "city:na"
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage – Filtern nach einem exakten Array-Wert {#sample-array-exact-value}

Diese Abfrage filtert nach einem exakten Array-Wert.

**Beispielabfrage**

```graphql
query {
  cityList(filter: {
    categories: {
      _expressions: [
        {
          values: [
            "city:beach",
            "city:na"
          ]
        }
      ]
    }
  }) {
    items {
      name
      population
      country
      categories
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA",
          "categories": [
            "city:beach",
            "city:na"
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage für verschachtelte Inhaltsfragmente – Alle Unternehmen mit mindestens einem Mitarbeiter mit dem Namen „Smith“  {#sample-companies-employee-smith}

Diese Abfrage veranschaulicht die Filterung nach `person` von `name` „Smith“, wobei Informationen aus zwei verschachtelten Fragmenten – `company` und `employee` – zurückgegeben werden.

**Beispielabfrage**

```graphql
query {
  companyList(filter: {
    employees: {
      _match: {
        name: {
          _expressions: [
            {
              value: "Smith"
            }
          ]
        }
      }
    }
  }) {
    items {
      name
      ceo {
        name
        firstName
      }
      employees {
        name
        firstName
      }
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "NextStep Inc.",
          "ceo": {
            "name": "Jobs",
            "firstName": "Steve"
          },
          "employees": [
            {
              "name": "Smith",
              "firstName": "Joe"
            },
            {
              "name": "Lincoln",
              "firstName": "Abraham"
            }
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage für verschachtelte Inhaltsfragmente – Alle Unternehmen, bei denen alle Mitarbeiter die Auszeichnung „Gamestar“ erhalten haben {#sample-all-companies-employee-gamestar-award}

Diese Abfrage veranschaulicht die Filterung von drei verschachtelten Fragmenten – `company`, `employee` und `award`.

**Beispielabfrage**

```graphql
query {
  companyList(filter: {
    employees: {
      _apply: ALL
      _match: {
        awards: {
          _match: {
            id: {
              _expressions: [
                {
                  value: "GS"
                  _operator:EQUALS
                }
              ]
            }
          }
        }
      }
    }
  }) {
    items {
      name
      ceo {
        name
        firstName
      }
      employees {
        name
        firstName
        awards {
          id
          title
        }
      }
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "Little Pony, Inc.",
          "ceo": {
            "name": "Smith",
            "firstName": "Adam"
          },
          "employees": [
            {
              "name": "Croft",
              "firstName": "Lara",
              "awards": [
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            },
            {
              "name": "Slade",
              "firstName": "Cutter",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                },
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            }
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage für Metadaten – Liste der Metadaten für Auszeichnungen mit dem Titel „GB“ {#sample-metadata-awards-gb}

Diese Abfrage veranschaulicht die Filterung von drei verschachtelten Fragmenten – `company`, `employee` und `award`.

**Beispielabfrage**

```graphql
query {
  awardList(filter: {
      id: {
        _expressions: [
          {
            value:"GB"
          }
        ]
    }
  }) {
    items {
      _metadata {
        stringMetadata {
          name,
          value
        }
      }
      id
      title
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "awardList": {
      "items": [
        {
          "_metadata": {
            "stringMetadata": [
              {
                "name": "title",
                "value": "Gameblitz Award"
              },
              {
                "name": "description",
                "value": ""
              }
            ]
          },
          "id": "GB",
          "title": "Gameblitz"
        }
      ]
    }
  }
}
```

## Beispielabfragen unter Verwendung des WKND-Projekts {#sample-queries-using-wknd-project}

Diese Beispielabfragen basieren auf dem WKND-Projekt. Es umfasst Folgendes:

* Inhaltsfragmentmodelle verfügbar unter:
  `http://<hostname>:<port>/libs/dam/cfm/models/console/content/models.html/conf/wknd`

* Inhaltsfragmente (und anderere Inhalte) verfügbar unter:
  `http://<hostname>:<port>/assets.html/content/dam/wknd/en`

>[!NOTE]
>
>Da die Ergebnisse sehr umfangreich sein können, werden sie hier nicht wiedergegeben.

### Beispielabfrage für alle Inhaltsfragmente eines bestimmten Modells mit den angegebenen Eigenschaften {#sample-wknd-all-model-properties}

Diese Beispielabfrage untersucht:

* Alle Inhaltsfragmente vom Typ `article`
* Mit den Eigenschaften `path`und `author`.

**Beispielabfrage**

```graphql
{
  articleList {
    items {
      _path
      author
    }
  }
}
```

### Beispielabfrage für Metadaten {#sample-wknd-metadata}

Diese Abfrage untersucht:

* Alle Inhaltsfragmente vom Typ `adventure`
* Metadaten

**Beispielabfrage**

```graphql
{
  adventureList {
    items {
      _path,
      _metadata {
        stringMetadata {
          name,
          value
        }
        stringArrayMetadata {
          name,
          value
        }
        intMetadata {
          name,
          value
        }
        intArrayMetadata {
          name,
          value
        }
        floatMetadata {
          name,
          value
        }
        floatArrayMetadata {
          name,
          value
        }
        booleanMetadata {
          name,
          value
        }
        booleanArrayMetadata {
          name,
          value
        }
        calendarMetadata {
          name,
          value
        }
        calendarArrayMetadata {
          name,
          value
        }
      }
    }
  }
}
```

### Beispielabfrage für ein einzelnes Inhaltsfragment eines bestimmten Modells {#sample-wknd-single-content-fragment-of-given-model}

Diese Beispielabfrage untersucht:

* Ein einzelnes Inhaltsfragment vom Typ `article` an einem bestimmten Pfad
   * innerhalb dieses Pfades alle Formate des Inhalts:
      * HTML
      * Markdown
      * Nur Text
      * JSON

**Beispielabfrage**

```graphql
{
  articleByPath (_path: "/content/dam/wknd/en/magazine/alaska-adventure/alaskan-adventures") {
    item {
        _path
        author
        main {
          html
          markdown
          plaintext
          json
        }
    }
  }
}
```

### Beispielabfrage für ein Inhaltsfragmentmodell anhand eines Modells {#sample-wknd-content-fragment-model-from-model}

Diese Beispielabfrage untersucht:

* Für ein einzelnes Inhaltsfragment
   * Details des zugrunde liegenden Inhaltsfragmentmodells

**Beispielabfrage**

```graphql
{
  adventureByPath(_path: "/content/dam/wknd/en/adventures/riverside-camping-australia/riverside-camping-australia") {
    item {
      _path
      adventureTitle
      _model {
        _path
        title
      }
    }
  }
}
```

### Beispielabfrage für ein verschachteltes Inhaltsfragment – Typ mit einem einzigen Modell{#sample-wknd-nested-fragment-single-model}

Diese Abfrage untersucht:

* Ein einzelnes Inhaltsfragment vom Typ `article` an einem bestimmten Pfad
   * innerhalb dieses Pfades, den Pfad und die Autorin bzw. der Autor des referenzierten (verschachtelten) Fragments

>[!NOTE]
>
>Das Feld `referencearticle` hat den Datentyp `fragment-reference`.

**Beispielabfrage**

```graphql
{
  adventureByPath(_path: "/content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van") {
    item {
      _path
      title
      _model {
        _path
        title
      }
    }
  }
}
```

### Beispielabfrage für ein verschachteltes Inhaltsfragment – Typ mit mehreren Modellen{#sample-wknd-nested-fragment-multiple-model}

#### Einzelner referenzierter Modelltyp

Diese Abfrage untersucht:

* Mehrere Inhaltsfragmente vom Typ `bookmark`
   * Mit Fragmentverweisen auf andere Fragmente des spezifischen Modelltyps `Article`

>[!NOTE]
>
>Das Feld `fragments` hat den Datentyp `fragment-reference`, wobei das Modell `Article` ausgewählt wurde. Die Abfrage liefert `fragments` als ein Array von `[Article]`.

```graphql
{
  bookmarkList {
    items {
        fragments {
          _path
          author
        }
     }
  }
}
```

#### Mehrere referenzierte Modelltypen

Diese Abfrage untersucht:

* Mehrere Inhaltsfragmente vom Typ `bookmark`
   * Mit Fragmentreferenzen auf andere Fragmente der spezifischen Modelltypen `Article` und `Adventure`

>[!NOTE]
>
>Das Feld `fragments` hat den Datentyp `fragment-reference`, wobei die Modelle `Article`, `Adventure` ausgewählt sind. Die Abfrage liefert `fragments` als ein Array von `[AllFragmentModels]`, das mit Vereinigungstyp dereferenziert wird.

```graphql
{
  bookmarkList {
    items {
        fragments {
          ... on ArticleModel {
            _path
            author
          }
          ... on AdventureModel {
            _path
            adventureTitle
          }
        }
     }
  }
}
```

### Beispielabfrage für ein Inhaltsfragment eines bestimmten Modells mit Inhaltsreferenzen{#sample-wknd-fragment-specific-model-content-reference}

Es gibt zwei Varianten dieser Abfrage:

1. Zurückgeben aller Inhaltsreferenzen.
1. Zurückgeben der spezifischen Inhaltsreferenzen vom Typ `attachments`.

Diese Abfragen untersuchen:

* Mehrere Inhaltsfragmente vom Typ `bookmark`
   * Mit Inhaltsreferenzen auf andere Fragmente.

#### Beispielabfrage für mehrere Inhaltsfragmente mit vorab abgerufenen Verweisen {#sample-wknd-multiple-fragments-prefetched-references}

Die folgende Abfrage gibt alle Inhaltsreferenzen mit `_references` zurück:

```graphql
{
  bookmarkList {
     _references {
         ... on ImageRef {
          _path
          type
          height
        }
        ... on MultimediaRef {
          _path
          type
          size
        }
        ... on DocumentRef {
          _path
          type
          author
        }
        ... on ArchiveRef {
          _path
          type
          format
        }
    }
    items {
        _path
    }
  }
}
```

#### Beispielabfrage für mehrere Inhaltsfragmente mit Anhängen {#sample-wknd-multiple-fragments-attachments}

Die folgende Abfrage gibt alle `attachments` zurück – ein bestimmtes Feld (Untergruppe) vom Typ `content-reference`:

>[!NOTE]
>
>Das Feld `attachments` hat den Datentyp `content-reference`, wobei verschiedene Formen ausgewählt sind.

```graphql
{
  bookmarkList {
    items {
      attachments {
        ... on PageRef {
          _path
          type
        }
        ... on ImageRef {
          _path
          width
        }
        ... on MultimediaRef {
          _path
          size
        }
        ... on DocumentRef {
          _path
          author
        }
        ... on ArchiveRef {
          _path
          format
        }
      }
    }
  }
}
```

### Beispielabfrage für ein einzelnes Inhaltsfragment mit RTE-Inline-Verweis {#sample-wknd-single-fragment-rte-inline-reference}

Diese Abfrage untersucht:

* Ein einzelnes Inhaltsfragment vom Typ `bookmark` an einem bestimmten Pfad
   * Darin die RTE-Inline-Verweise

>[!NOTE]
>
>Die RTE-Inline-Verweise werden in `_references` realisiert.

**Beispielabfrage**

```graphql
{
  bookmarkByPath(_path: "/content/dam/wknd/en/bookmarks/skitouring") {
    item {
      _path
      description {
        json
      }
    }
    _references {
      ... on ArticleModel {
        _path
      }
      ... on AdventureModel {
        _path
      }
      ... on ImageRef {
        _path
      }
      ... on MultimediaRef {
        _path
      }
      ... on DocumentRef {
        _path
      }
      ... on ArchiveRef {
        _path
      }
    }
  }
}
```

### Beispielabfrage für eine einzelne Variante eines Inhaltsfragments eines bestimmten Modells {#sample-wknd-single-fragment-given-model}

Diese Abfrage untersucht:

* Ein einzelnes Inhaltsfragment vom Typ `article` an einem bestimmten Pfad
   * innerhalb dieses Pfades die Daten, die sich auf die folgende Variante beziehen: `variation1`

**Beispielabfrage**

```graphql
{
  articleByPath (_path: "/content/dam/wknd/en/magazine/alaska-adventure/alaskan-adventures", variation: "variation1") {
    item {
      _path
      author
      main {
        html
        markdown
        plaintext
        json
      }
    }
  }
}
```

### Beispielabfrage für eine gegebene Variante mehrerer Inhaltsfragmente eines bestimmten Modells {#sample-wknd-variation-multiple-fragment-given-model}

Diese Abfrage untersucht:

* Inhaltsfragmente vom Typ `article` mit einer bestimmten Variante: `variation1`

**Beispielabfrage**

```graphql
{
  articleList (variation: "variation1") {
    items {
      _path
      author
      main {
        html
        markdown
        plaintext
        json
      }
    }
  }
}
```

### Beispielabfrage für mehrere Inhaltsfragmente und deren Varianten eines bestimmten Modells {#sample-wknd-multiple-fragment-variations-given-model}

Diese Abfrage untersucht:

* für Inhaltsfragmente vom Typ `article` und alle Varianten

**Beispielabfrage**

```graphql
query {
  articleList(
    includeVariations: true  ){
    items {
      _variation
      _path
      _tags
      _metadata {
        stringArrayMetadata {
          name
          value
        }
      }
    }
  }
}
```

### Beispielabfrage für Inhaltsfragmentvarianten eines bestimmten Modells, an das ein bestimmtes Tag angehängt ist{#sample-wknd-fragment-variations-given-model-specific-tag}

Diese Abfrage untersucht:

* für Inhaltsfragmente vom Typ `article` mit einer oder mehreren Varianten mit dem Tag `WKND : Activity / Hiking`

**Beispielabfrage**

```graphql
{
  articleList(
    includeVariations: true,
    filter: {_tags: {_expressions: [{value: "wknd:activity/hiking", _operator: CONTAINS}]}}
  ){
    items {
      _variation
      _path
      _tags
      _metadata {
        stringArrayMetadata {
          name
          value
        }
      }
    }
  }
}
```

### Beispielabfrage für mehrere Inhaltsfragmente eines bestimmten Gebietsschemas {#sample-wknd-multiple-fragments-given-locale}

Diese Abfrage untersucht:

* Inhaltsfragmente vom Typ `article` innerhalb des Gebietsschemas `fr`

**Beispielabfrage**

```graphql
{ 
  articleList (_locale: "fr") {
    items {
      _path
      author
      main {
        html
        markdown
        plaintext
        json
      }
    }
  }
}
```

## Die Struktur des Beispielinhaltsfragments (verwendet mit GraphQL) {#content-fragment-structure-graphql}

Die Abfragen basieren auf der folgenden Struktur, die Folgendes verwendet:

* Ein oder mehrere [Beispielmodelle für Inhaltsfragmente](#sample-content-fragment-models-schemas) bilden die Grundlage für die GraphQL-Schemata

* [Beispielinhaltsfragmente](#sample-content-fragments) basierend auf den oben genannten Modellen

### Beispielmodelle für Inhaltsfragmente (Schemata) {#sample-content-fragment-models-schemas}

Für die Beispielabfragen verwenden wir die folgenden Inhaltsmodelle und ihre Wechselbeziehungen (Verweise ->):

* [Unternehmen](#model-company)
> [Person](#model-person)
> [Auszeichnung](#model-award)

* [Stadt](#model-city)

#### Unternehmen {#model-company}

Die grundlegenden Felder, die das Unternehmen definieren, sind:

| Feldname | Datentyp | Verweis |
|--- |--- |--- |
| Unternehmensname | Einzeiliger Text | |
| CEO | Fragmentreferenz (Einzelfeld) | [Person](#model-person) |
| Mitarbeiter | Fragmentreferenz (Mehrfeld) | [Person](#model-person) |

#### Person {#model-person}

Die Felder, die eine Person definieren, die auch ein Mitarbeiter sein kann:

| Feldname | Datentyp | Verweis |
|--- |--- |--- |
| Name | Einzeiliger Text | |
| Vorname | Einzeiliger Text | |
| Auszeichnungen | Fragmentreferenz (Mehrfeld) | [Auszeichnung](#model-award) |

#### Auszeichnung {#model-award}

Die Felder, die eine Auszeichnung definieren, sind:

| Feldname | Datentyp | Verweis |
|--- |--- |--- |
| Kürzel/Kennung | Einzeiliger Text | |
| Titel | Einzeiliger Text | |

#### Stadt {#model-city}

Die Felder zur Definition einer Stadt sind:

| Feldname | Datentyp | Verweis |
|--- |--- |--- |
| Name | Einzeiliger Text | |
| Land | Einzeiliger Text | |
| Einwohnerzahl | Zahl | |
| Kategorien | Tags | |

### Beispielinhaltsfragmente {#sample-content-fragments}

Die folgenden Fragmente werden für das entsprechende Modell verwendet.

#### Unternehmen {#fragment-company}

| Unternehmensname | CEO | Mitarbeiter |
|--- |--- |--- |
| Apple | Steve Jobs | Duke Marsh<br>Max Caulfield |
|  Little Pony Inc. | Adam Smith | Lara Croft<br>Cutter Slade |
| NextStep Inc. | Steve Jobs | Joe Smith<br>Abe Lincoln |

#### Person {#fragment-person}

| Name | Vorname | Auszeichnungen |
|--- |--- |--- |
| Lincoln |  Abe | |
| Smith | Adam |   |
| Slade |  Cutter |  Gameblitz<br>Gamestar |
| Marsh |  Duke |   |   |
|  Smith |  Joe |   |
| Croft |  Lara | Gamestar |
| Caulfield |  Maximal |  Gameblitz |
|  Aufträge |  Steve |   |

#### Auszeichnung {#fragment-award}

| Kürzel/Kennung | Titel |
|--- |--- |
| GB | Gameblitz |
|  GS | Gamestar |
|  OSC | Oscar |

#### Stadt {#fragment-city}

| Name | Land | Einwohnerzahl | Kategorien |
|--- |--- |--- |--- |
| Basel | Schweiz | 172258 | city:emea |
| Berlin | Deutschland | 3669491 | city:capital<br>city:emea |
| Bukarest | Rumänien | 1821000 |  city:capital<br>city:emea |
| San Francisco |  USA |  883306 |  city:beach<br>city:na |
| San José |  USA |  102635 |  city:na |
| Stuttgart |  Deutschland |  634830 |  city:emea |
|  Zürich |  Schweiz |  415367 |  city:capital<br>city:emea |
