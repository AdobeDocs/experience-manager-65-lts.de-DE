---
title: Verweis auf die ContextHub-JavaScript-API
description: Die ContextHub-JavaScript-API ist für Ihre Skripte verfügbar, wenn die ContextHub-Komponente zur Seite hinzugefügt wurde.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
feature: Context Hub,Developing,Personalization
solution: Experience Manager, Experience Manager Sites
role: Developer
exl-id: 26cc4d84-ed76-44c7-a4e9-73ed48009568
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '4913'
ht-degree: 100%

---

# Verweis auf die ContextHub-JavaScript-API{#contexthub-javascript-api-reference}

Die ContextHub-JavaScript-API ist für Ihre Skripte verfügbar, wenn die [ContextHub-Komponente zur Seite hinzugefügt wurde](/help/sites-developing/ch-adding.md#adding-contexthub-to-a-page-component).

## ContextHub-Konstanten {#contexthub-constants}

Konstante Werte, die von der ContextHub-JavaScript-API definiert werden.

### Ereigniskonstanten {#event-constants}

In der folgenden Tabelle sind die Namen von Ereignissen aufgeführt, die bei ContextHub-Stores auftreten. Siehe auch [ContextHub.Utils.Eventing](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing).

| Konstante | Beschreibung | Wert |
|---|---|---|
| ContextHub.Constants.EVENT_NAMESPACE | Ereignis-Namespace von ContextHub | ch |
| ContextHub.Constants.EVENT_ALL_STORES_READY | Gibt an, dass alle erforderlichen Stores registriert, initialisiert und einsatzbereit sind | all-stores-ready |
| ContextHub.Constants.EVENT_STORES_PARTIALLY_READY | Gibt an, dass nicht alle Stores innerhalb eines bestimmten Timeouts initialisiert wurden | stores-partially-ready |
| ContextHub.Constants.EVENT_STORE_REGISTERED | Wird ausgelöst, wenn ein Store registriert ist | store-registered |
| ContextHub.Constants.EVENT_STORE_READY | Gibt an, dass Stores einsatzbereit sind. Wird sofort nach der Registrierung ausgelöst, außer bei JSONP-Stores, wo es ausgelöst wird, wenn Daten abgerufen werden. | store-ready |
| ContextHub.Constants.EVENT_STORE_UPDATED | Wird ausgelöst, wenn ein Store seine Persistenz aktualisiert | store-updated |
| ContextHub.Constants.PERSISTENCE_CONTAINER_NAME | Name des Persistenz-Containers | ContextHubPersistence |
| ContextHub.Constants.SERVICE_RAW_RESPONSE_KEY | Speichert den spezifischen Namen des Persistenzschlüssels, wenn das unformatierte JSON-Ergebnis gespeichert wird | /_/raw-response |
| ContextHub.Constants.SERVICE_RESPONSE_TIME_KEY | Speichert einen bestimmten Zeitstempel, der angibt, wann JSON-Daten abgerufen wurden | /_/response-time |
| ContextHub.Constants.SERVICE_LAST_URL_KEY | Speichert spezifische URL des JSON-Service, der beim letzten Aufruf verwendet wurde | /_/url |
| ContextHub.Constants.IS_CONTAINER_EXPANDED | Gibt an, ob die Benutzeroberfläche von ContextHub erweitert ist | /_/container-extended |

### Benutzeroberflächen-Ereigniskonstanten {#ui-event-constants}

In der folgenden Tabelle sind die Namen der Ereignisse aufgeführt, die für die ContextHub-Benutzeroberfläche auftreten.

| **Konstante** | **Beschreibung** | **Wert** |
|---|---|---|
| ContextHub.Constants.EVENT_UI_MODE_REGISTERED | Wird ausgelöst, wenn ein Modus registriert wird | ui-mode-registered |
| ContextHub.Constants.EVENT_UI_MODE_UNREGISTERED | Wird ausgelöst, wenn ein Modus deregistriert wird | ui-mode-unregistered |
| ContextHub.Constants.EVENT_UI_MODE_RENDERER_REGISTERED | Wird ausgelöst, wenn ein Modus-Renderer registriert wird | ui-mode-renderer-registered |
| ContextHub.Constants.EVENT_UI_MODE_RENDERER_UNREGISTERED | Wird ausgelöst, wenn ein Modus-Renderer deregistriert wird | ui-mode-renderer-unregistered |
| ContextHub.Constants.EVENT_UI_MODE_ADDED | Wird ausgelöst, wenn ein neuer Modus hinzugefügt wird | ui-mode-added |
| ContextHub.Constants.EVENT_UI_MODE_REMOVED | Wird ausgelöst, wenn ein Modus entfernt wird | ui-mode-removed |
| ContextHub.Constants.EVENT_UI_MODE_SELECTED | Wird ausgelöst, wenn der Benutzer einen Modus auswählt | ui-mode-selected |
| ContextHub.Constants.EVENT_UI_MODULE_REGISTERED | Wird ausgelöst, wenn ein neues Modul registriert wird | ui-module-registered |
| ContextHub.Constants.EVENT_UI_MODULE_UNREGISTERED | Wird ausgelöst, wenn ein Modul deregistriert wird | ui-module-unregistered |
| ContextHub.Constants.EVENT_UI_MODULE_RENDERER_REGISTERED | Wird ausgelöst, wenn ein Modul-Renderer registriert wird | Ui-module-renderer-registered |
| ContextHub.Constants.EVENT_UI_MODULE_RENDERER_UNREGISTERED | Wird ausgelöst, wenn ein Modul-Renderer deregistriert wird | ui-module-renderer-unregistered |
| ContextHub.Constants.EVENT_UI_MODULE_ADDED | Wird ausgelöst, wenn ein neues Modul hinzugefügt wird | ui-module-added |
| ContextHub.Constants.EVENT_UI_MODULE_REMOVED | Wird ausgelöst, wenn ein Modul entfernt wird | ui-module-removed |
| ContextHub.Constants.EVENT_UI_CONTAINER_ADDED | Wird ausgelöst, wenn der UI-Container der Seite hinzugefügt wird | ui-container-added |
| ContextHub.Constants.EVENT_UI_CONTAINER_OPENED | Wird ausgelöst, wenn die ContextHub-Benutzeroberfläche geöffnet wird | ui-container-opened |
| ContextHub.Constants.EVENT_UI_CONTAINER_CLOSED | Wird ausgelöst, wenn die ContextHub-Benutzeroberfläche reduziert wird | ui-container-closed |
| ContextHub.Constants.EVENT_UI_PROPERTY_MODIFIED | Wird ausgelöst, wenn eine Eigenschaft geändert wird | ui-property-modified |
| ContextHub.Constants.EVENT_UI_RENDERED | Wird jedes Mal ausgelöst, wenn die ContextHub-Benutzeroberfläche gerendert wird (z. B. nach einer Eigenschaftsänderung) | ui-gerendert |
| ContextHub.Constants.EVENT_UI_INITIALIZED | Wird ausgelöst, wenn der UI-Container initialisiert wird | ui-initialized |
| ContextHub.Constants.ACTIVE_UI_MODE | Zeigt den aktiven UI-Modus an | /_/active-ui-mode |

## Verweis auf die ContextHub-JavaScript-API {#contexthub-javascript-api-reference-2}

Das ContextHub-Objekt bietet Zugriff auf alle Stores.

### Funktionen (ContextHub) {#functions-contexthub}

#### getAllStores() {#getallstores}

Gibt alle registrierten ContextHub-Stores zurück.

Diese Funktion hat keine Parameter.

**Rückgabe**

Ein Objekt, das alle ContextHub-Stores enthält. Jeder Store ist ein Objekt, das denselben Namen wie der Store verwendet.

**Beispiel**

Im folgenden Beispiel werden alle Stores und anschließend der Geolocation-Store abgerufen:

```
var allStores = ContextHub.getAllStores();
var geoloc = allStores.geolocation
```

#### getStore(name) {#getstore-name}

Ruft einen Store als ein JavaScript-Objekt ab.

**Parameter**

* **name:** Der Name, mit dem der Store registriert wurde.

**Rückgabe**

Ein Objekt, das den Store darstellt.

**Beispiel**

Im folgenden Beispiel wird der Geolocation-Store abgerufen:

```
var geoloc = ContextHub.getStore("geolocation");
```

## ContextHub.SegmentEngine.Segment {#contexthub-segmentengine-segment}

Stellt ein ContextHub-Segment dar. Verwenden Sie ContextHub.SegmentEngine.SegmentManager, um Segmente zu erhalten.

### Funktionen (ContextHub.ContextEngine.Segment) {#functions-contexthub-contextengine-segment}

#### getName() {#getname}

Gibt den Namen des Segments als Zeichenfolgenwert zurück.

#### getPath() {#getpath}

Gibt den Repository-Pfad der Segmentdefinition als Zeichenfolgenwert zurück.

## ContextHub.SegmentEngine.SegmentManager {#contexthub-segmentengine-segmentmanager}

Bietet Zugriff auf ContextHub-Segmente.

### Funktionen (ContextHub.SegmentEngine.SegmentManager) {#functions-contexthub-segmentengine-segmentmanager}

#### getResolvedSegments() {#getresolvedsegments}

Gibt die Segmente zurück, die im aktuellen Kontext aufgelöst werden. Diese Funktion hat keine Parameter.

**Rückgabe**

Ein Array von Objekten des Typs ContextHub.SegmentEngine.Segment.

## ContextHub.Store.Core {#contexthub-store-core}

Die Basisklasse für ContextHub-Stores.

### Eigenschaften (ContextHub.Store.Core) {#properties-contexthub-store-core}

#### Vielseitigkeit {#eventing}

Ein [ContextHub.Utils.Eventing](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing)-Objekt. Verwenden Sie dieses Objekt zum Binden von Funktionen zum Speichern von Ereignissen. Weitere Informationen über den Standardwert und die Initialisierung finden Sie unter [init (name,config)](/help/sites-developing/contexthub-api.md#init-name-config).

#### name {#name}

Der Name des Stores.

#### persistence {#persistence}

Ein Objekt des Typs ContextHub.Utils.Persistence. Weitere Informationen über den Standardwert und die Initialisierung finden Sie unter `[init(name,config)](/help/sites-developing/contexthub-api.md#init-name-config).`

### Funktionen (ContextHub.Store.Core) {#functions-contexthub-store-core}

#### addAllItems(tree, options) {#addallitems-tree-options}

Führt ein Datenobjekt oder ein Array mit den Store-Daten zusammen. Jedes Schlüssel/Wert-Paar im Objekt oder Array wird dem Store hinzugefügt (über die Funktion `setItem`):

* **Objekt:** Schlüssel sind die Eigenschaftsnamen.
* **Array:** Schlüssel sind die Array-Indizes.

Beachten Sie, dass Werte Objekte sein können.

**Parameter**

* **tree:** (Objekt oder Array) Die Daten, die dem Store hinzugefügt werden sollen.
* **options:** (Objekt) Ein optionales Objekt von Optionen, das an die setItem-Funktion übergeben wird. Weitere Informationen finden Sie unter dem `options`-Parameter von [setItem(key,value,options)](/help/sites-developing/contexthub-api.md#setitem-key-value-options).

**Rückgabe**

Ein `boolean`-Wert:

* Der Wert `true` gibt an, dass das Datenobjekt gespeichert wurde.
* Der Wert `false` gibt an, dass der Daten-Store unverändert ist.

#### addReference(key, anotherKey) {#addreference-key-anotherkey}

Erstellt einen Verweis von einem Schlüssel zum anderen. Ein Schlüssel kann sich nicht selbst referenzieren.

**Parameter**

* **key:** Der Schlüssel, der `anotherKey` referenziert.

* **anotherkey:** Der Schlüssel, der durch `key` referenziert wird.

**Rückgabe**

Ein `boolean`-Wert:

* Der Wert `true` gibt an, dass die Referenz hinzugefügt wurde.
* Der Wert `false` gibt an, dass keine Referenz hinzugefügt wurde.

#### announceReadiness() {#announcereadiness}

Löst das `ready`-Ereignis für diesen Store aus. Diese Funktion hat keine Parameter und gibt keinen Wert zurück.

#### clean() {#clean}

Entfernt alle Daten aus dem Store. Die Funktion hat keine Parameter und keinen Rückgabewert.

#### getItem(key)  {#getitem-key}

Gibt den Wert zurück, der einem Schlüssel zugeordnet ist.

**Parameter**

* **key:** (Zeichenfolge) Der Schlüssel, für den der Wert zurückgegeben werden soll.

**Rückgabe**

Ein Objekt, das den Wert für den Schlüssel darstellt.

#### getKeys(includeInternals) {#getkeys-includeinternals}

Ruft die Schlüssel aus dem Store ab. Optional können Sie die Schlüssel abrufen, die intern vom ContextHub-Framework verwendet werden.

**Parameter**

* **includeInternals:** Der Wert `true` umfasst intern verwendete Schlüssel in den Ergebnissen. Diese Schlüssel beginnen mit einem Unterstrich (&quot;_&quot;). Der Standardwert ist `false`.

**Rückgabe**

Ein Array von Schlüsselnamen (`string`-Werte).

#### getReferences() {#getreferences}

Ruft die Referenzen aus dem Store ab.

**Rückgabe**

Ein Array, das Referenzschlüssel als Indizes für die referenzierten Schlüssel verwendet:

* Referenzschlüssel entsprechen dem `key`-Parameter der `addReference`-Funktion.

* Referenzierte Schlüssel entsprechen dem Parameter `anotherKey` der Funktion `addReference`.

#### getTree(includeInternals) {#gettree-includeinternals}

Ruft die Datenstruktur aus dem Store ab. Optional können Sie die Schlüssel-Wert-Paare einbeziehen, die intern vom ContextHub-Framework verwendet werden.

**Parameter**

* `includeInternals:` Der Wert `true` umfasst intern verwendete Schlüssel-Wert-Paare in den Ergebnissen. Die Schlüssel dieser Daten beginnen mit einem Unterstrich (&quot;_&quot;). Der Standardwert ist `false`.

**Rückgabe**

Ein Objekt, das die Datenstruktur darstellt. Die Schlüssel sind die Eigenschaftsnamen des Objekts.

#### init(name, config)  {#init-name-config}

Initialisiert den Store.

* Setzt die Store-Daten auf ein leeres Objekt.
* Setzt die Store-Referenzen auf ein leeres Objekt.
* Der eventChannel ist data:*Name*, wobei *Name* der Storename ist.

* Der storeDataKey ist /store/*name*, wobei *name* der Store-Name ist.

**Parameter**

* **name:** Der Name des Stores.
* **config:** Ein Objekt, das Konfigurationseigenschaften enthält:

   * eventDeferring: Der Standardwert ist 32.
   * eventing: Das [ContextHub.Utils.Eventing](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing)-Objekt für diesen Store. Der Standardwert ist das ContextHub.eventing-Objekt.
   * persistence: Das ContextHub.Utils.Persistence-Objekt für diesen Store. Der Standardwert ist das ContextHub.persistence-Objekt.

#### isEventingPaused() {#iseventingpaused}

Ermittelt, ob das Eventing für diesen Store angehalten wurde.

**Rückgabe**

Ein boolescher Wert:

* `true`: Eventing ist angehalten, sodass keine Ereignisse für diesen Store ausgelöst werden.
* `false`: Eventing ist nicht angehalten, sodass Ereignisse für diesen Store ausgelöst werden.

#### pauseEventing() {#pauseeventing}

Setzt das Eventing für den Store aus, sodass keine Ereignisse ausgelöst werden. Diese Funktion erfordert keine Parameter und gibt keinen Wert zurück.

#### removeItem(key, options)  {#removeitem-key-options}

Entfernt ein Schlüssel/Wert-Paar aus dem Store.

Wenn ein Schlüssel entfernt wird, löst die Funktion das `data`-Ereignis aus. Die Ereignisdaten enthalten den Namen des Stores, den Namen des entfernten Schlüssels, den entfernten Wert, den neuen Wert für den Schlüssel (null) und den Aktionstyp „Entfernen“.

Optional können Sie das Auslösen des Ereignisses `data` verhindern.

**Parameter**

* **key:** (Zeichenfolge) Der Name des zu entfernenden Schlüssels.
* **options:** (Objekt) Ein Objekt von Optionen. Die folgenden Objekteigenschaften sind gültig:

   * silent: Ein Wert `true` verhindert das Auslösen des `data`-Ereignisses. Der Standardwert ist `false`.

**Rückgabe**

Ein `boolean`-Wert:

* Ein Wert `true` zeigt an, dass das Schlüssel/Wert-Paar entfernt wurde.
* Ein Wert `false` gibt an, dass der Daten-Store unverändert ist, da der Schlüssel nicht im Store gefunden wurde.

#### removeReference(key) {#removereference-key}

Entfernt eine Referenz aus dem Store.

**Parameter**

* **key:** Die zu entfernende Schlüsselreferenz. Dieser Parameter entspricht dem `key`-Parameter der `addReference`-Funktion.

**Rückgabe**

Ein `boolean`-Wert:

* Ein Wert `true` zeigt an, dass die Referenz entfernt wurde.
* Ein Wert `false` gibt an, dass der Schlüssel nicht gültig war und der Store unverändert ist.

#### reset(keepRemainingData) {#reset-keepremainingdata}

Setzt die Anfangswerte der persistenten Daten des Stores zurück. Optional können Sie alle anderen Daten aus dem Store entfernen. Das Eventing wird für diesen Store angehalten, während die Anfangswerte zurückgesetzt werden. Diese Funktion gibt keinen Wert zurück.

Anfangswerte werden in der Eigenschaft „initialValues“ des Konfigurationsobjekts bereitgestellt, das zum Instanziieren des Store-Objekts verwendet wird.

**Parameter**

* **keepRemainingData:** (Boolesch) Ein Wert „true“ bewirkt, dass nicht-initial-Daten beibehalten werden. Der Wert „false“ bewirkt, dass alle Daten mit Ausnahme der Anfangswerte entfernt werden.

Setzt die Anfangswerte der persistenten Daten des Stores zurück. Optional können Sie alle anderen Daten aus dem Store entfernen. Das Eventing wird für diesen Store angehalten, während die Anfangswerte zurückgesetzt werden. Diese Funktion gibt keinen Wert zurück.

Anfangswerte werden in der Eigenschaft „initialValues“ des Konfigurationsobjekts bereitgestellt, das zum Instanziieren des Store-Objekts verwendet wird.

**Parameter**

* keepRemainingData: (Boolesch) Ein Wert „true“ bewirkt, dass nicht-initial-Daten beibehalten werden. Der Wert „false“ bewirkt, dass alle Daten mit Ausnahme der Anfangswerte entfernt werden.

#### resolveReference(key, retry) {#resolvereference-key-retry}

Ruft einen referenzierten Schlüssel ab. Optional können Sie die Anzahl der Iterationen angeben, die zur Auflösung der besten Übereinstimmung verwendet werden sollen.

**Parameter**

* **key:** (String) Der Schlüssel, für den die Referenz aufgelöst werden soll. Dieser `key`-Parameter entspricht dem `key`-Parameter der `addReference`-Funktion.

* **retry:** (Zahl) Die Anzahl der zu verwendenden Iterationen.

**Rückgabe**

Ein `string`-Wert, der den referenzierten Schlüssel darstellt. Wenn keine Referenz aufgelöst wird, wird der Wert des `key`-Parameters zurückgegeben.

#### resumeEventing() {#resumeeventing}

Nimmt das Eventing für diesen Store wieder auf, damit Ereignisse ausgelöst werden. Diese Funktion definiert keine Parameter und gibt keinen Wert zurück.

#### setItem(key, value, options)  {#setitem-key-value-options}

Fügt dem Store ein Schlüssel-Wert-Paar hinzu.

Löst das `data`-Ereignis nur aus, wenn der Wert für den Schlüssel sich von dem Wert unterscheidet, der aktuell für den Schlüssel gespeichert ist. Optional können Sie das Auslösen des `data`-Ereignisses verhindern.

Die Ereignisdaten umfassen den Store-Namen, den Schlüssel, den vorherigen Wert, den neuen Wert und den Aktionstyp von `set`.

**Parameter**

* **key:** (Zeichenfolge) Der Name des Schlüssels.
* **options:** (Objekt) Ein Objekt von Optionen. Die folgenden Objekteigenschaften sind gültig:

   * silent: Ein Wert `true` verhindert das Auslösen des `data`-Ereignisses. Der Standardwert ist `false`.

* **value:** (Objekt) Der Wert, der dem Schlüssel zugeordnet werden soll.

**Rückgabe**

Ein `boolean`-Wert:

* Der Wert `true` gibt an, dass das Datenobjekt gespeichert wurde.
* Der Wert `false` gibt an, dass der Daten-Store unverändert ist.

## ContextHub.Store.JSONPStore {#contexthub-store-jsonpstore}

Ein Store, der JSON-Daten enthält. Die Daten werden von einem externen JSONP-Service oder optional von einem Service abgerufen, der JSON-Daten zurückgibt. Geben Sie die Details des Service mithilfe der [`init`](/help/sites-developing/contexthub-api.md#init-name-config)-Funktion an, wenn Sie eine Instanz dieser Klasse erstellen.

Der Speicher verwendet speicherinterne Persistenz (JavaScript-Variable). Speicherdaten sind nur während der Lebensdauer der Seite verfügbar.

ContextHub.Store.JSONPStore erweitert [ContextHub.Store.Core](/help/sites-developing/contexthub-api.md#contexthub-store-core) und übernimmt die Funktionen dieser Klasse.

### Funktionen (ContextHub.Store.JSONPStore) {#functions-contexthub-store-jsonpstore}

#### configureService(serviceConfig, override) {#configureservice-serviceconfig-override}

Konfiguriert die Details für die Verbindung mit dem JSONP-Service, den dieses Objekt verwendet. Sie können entweder die vorhandene Konfiguration aktualisieren oder ersetzen. Diese Funktion gibt keinen Wert zurück.

**Parameter**

* **serviceConfig:** Ein Objekt, das folgende Eigenschaften enthält:

   * host: (Zeichenfolge) Server-Name oder IP-Adresse.
   * jsonp: (Boolesch) Ein Wert „true“ zeigt an, dass der Service ein JSONP-Service ist, andernfalls ist er „false“. Wenn „true“ vorliegt, wird das Objekt {callback: &quot;ContextHub.Callbacks.*Object.name*} dem Objekt service.params hinzugefügt.
   * params: (Object) URL-Parameter, die als Objekteigenschaften dargestellt werden. Parameternamen sind Eigenschaftsnamen und Parameterwerte sind Eigenschaftswerte.
   * path: (Zeichenfolge) Der Pfad zum Dienst.
   * port: (Zahl) Die Port-Nummer des Dienstes.
   * secure: (Zeichenfolge oder Boolescher Wert) Bestimmt das für die Dienst-URL zu verwendende Protokoll:

      * auto: //
      * true: https://
      * false: https://

* **override:** (Boolesch). Ein Wert `true` bewirkt, dass die vorhandene Service-Konfiguration durch die Eigenschaften von `serviceConfig` ersetzt wird. Der Wert `false` bewirkt, dass die vorhandenen Service-Konfigurationseigenschaften mit den Eigenschaften von `serviceConfig` zusammengeführt werden.

#### getRawResponse() {#getrawresponse}

Gibt die unbearbeitete Antwort zurück, die seit dem letzten Aufruf des JSONP-Service zwischengespeichert wurde. Für die Funktion sind keine Parameter erforderlich.

**Rückgabe**

Ein Objekt, das die unformatierte Antwort darstellt.

#### getServiceDetails() {#getservicedetails}

Ruft das Service-Objekt für dieses ContextHub.Store.JSONPStore-Objekt ab. Das Dienstobjekt enthält alle Informationen, die zum Erstellen der Dienst-URL erforderlich sind.

**Rückgabe**

Ein Objekt mit den folgenden Eigenschaften:

* **host:** (Zeichenfolge) Server-Name oder IP-Adresse.
* **jsonp:** (Boolesch) Ein Wert „true“ zeigt an, dass der Dienst ein JSONP-Dienst ist, andernfalls ist er „false“. Wenn „true“ vorliegt, wird das Objekt {callback: &quot;ContextHub.Callbacks.*Object.name*} dem Objekt service.params hinzugefügt.

* **params:** (Object) URL-Parameter, die als Objekteigenschaften dargestellt werden. Parameternamen sind Eigenschaftsnamen und Parameterwerte sind Eigenschaftswerte.
* **path:** (Zeichenfolge) Der Pfad zum Dienst.
* **port:** (Zahl) Die Port-Nummer des Dienstes.
* **secure:** (Zeichenfolge oder Boolescher Wert) Bestimmt das für die Dienst-URL zu verwendende Protokoll:

   * auto: //
   * true: https://
   * false: https://

#### getServiceURL(resolve) {#getserviceurl-resolve}

Ruft die URL des JSONP-Service ab.

**Parameter**

* **resolve:** (Boolesch) Bestimmt, ob aufgelöste Parameter in die URL aufgenommen werden sollen. Ein Wert `true` löst Parameter auf und `false` dagegen nicht.

**Rückgabe**

Ein `string`-Wert, der die Service-URL darstellt.

#### init(name, config)  {#init-name-config-1}

initialisiert das ContextHub.Store.JSONPStore-Objekt.

**Parameter**

* **name:** (Zeichenfolge) Der Name des Stores.
* **config:** (Object) Ein Objekt, das die Service-Eigenschaft enthält. Das JSONPStore-Objekt verwendet die Eigenschaften des `service`objekts, um die URL des JSONP-Service zu erstellen:

   * EventDeferring: 32.
   * eventing: Das ContextHub.Utils.Eventing-Objekt für diesen Store. Der Standardwert ist das `ContextHub.eventing`-Objekt.
   * persistence: Das ContextHub.Utils.Persistence-Objekt für diesen Store. Standardmäßig wird die Speicherpersistenz verwendet (JavaScript-Objekt).
   * service: (Object)

      * host: (Zeichenfolge) Server-Name oder IP-Adresse.
      * jsonp: (Boolesch) Ein Wert „true“ zeigt an, dass der Service ein JSONP-Service ist, andernfalls ist er „false“. Wenn „true“, wird das `{callback: "ContextHub.Callbacks.*Object.name*}`-Objekt `service.params` hinzugefügt.
      * params: (Object) URL-Parameter, die als Objekteigenschaften dargestellt werden. Parameternamen und Werte sind jeweils die Namen und Werte der Objekteigenschaften.
      * path: (Zeichenfolge) Der Pfad zum Dienst.
      * port: (Zahl) Die Port-Nummer des Dienstes.
      * secure: (Zeichenfolge oder Boolescher Wert) Bestimmt das für die Dienst-URL zu verwendende Protokoll:

         * auto: //
         * true: https://
         * false: https://

      * timeout: (Zahl) Die Zeitspanne in Millisekunden, für die auf eine Antwort des JSONP-Dienstes gewartet wird, bevor eine Zeitüberschreitung eintritt.
      * ttl: Die Mindestdauer in Millisekunden, die zwischen Aufrufen an den JSONP-Dienst vergeht. (Siehe [queryService](/help/sites-developing/contexthub-api.md#queryservice-reload) Funktion).

#### queryService(reload) {#queryservice-reload}

Fragt den Remote-JSONP-Service ab und speichert die Antwort zwischen. Wenn die Zeit seit dem letzten Aufruf dieser Funktion kleiner als der Wert von `config.service.ttl` ist, wird der Service nicht aufgerufen und die zwischengespeicherte Antwort wird nicht geändert. Optional können Sie einen Aufruf des Service erzwingen. Die Eigenschaft `config.service.ttl` wird festgelegt, wenn die [init](/help/sites-developing/contexthub-api.md#init-name-config)-Funktion aufgerufen wird, um den Store zu initialisieren.

Löst das bereites Ereignis aus, wenn die Abfrage beendet ist. Wenn die JSONP-Dienst-URL nicht festgelegt ist, bewirkt die Funktion nichts.

**Parameter**

* **reload:** (Boolesch) Der Wert „true“ entfernt die zwischengespeicherte Antwort und erzwingt den Aufruf des JSONP-Dienstes.

#### Zurücksetzen {#reset}

Setzt die Anfangswerte der persistenten Daten des Stores zurück und ruft dann den JSONP-Service auf. Optional können Sie alle anderen Daten aus dem Store entfernen. Eventing wird für diesen Store angehalten, während die Anfangswerte zurückgesetzt werden. Diese Funktion gibt keinen Wert zurück.

Anfangswerte werden in der Eigenschaft „initialValues“ des Konfigurationsobjekts bereitgestellt, das zum Instanziieren des Store-Objekts verwendet wird.

**Parameter**

* **keepRemainingData:** (Boolesch) Ein Wert „true“ bewirkt, dass nicht-initial-Daten beibehalten werden. Der Wert „false“ bewirkt, dass alle Daten mit Ausnahme der Anfangswerte entfernt werden.

#### resolveParameter(f) {#resolveparameter-f}

Löst den angegebenen Parameter auf.

## ContextHub.Store.PersistedJSONPStore {#contexthub-store-persistedjsonpstore}

ContextHub.Store.PersistedJSONPStore erweitert [ContextHub.Store.JSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-jsonpstore) so, dass alle Funktionen dieser Klasse übernommen werden. Die Daten, die vom JSONP-Service abgerufen werden, bleiben jedoch gemäß der Konfiguration der ContextHub-Persistenz bestehen. (Siehe [Persistenzmodi](/help/sites-developing/ch-adding.md#persistence-modes).)

## ContextHub.Store.PersistedStore {#contexthub-store-persistedstore}

ContextHub.Store.PersistedStore erweitert [ContextHub.Store.Core](/help/sites-developing/contexthub-api.md#contexthub-store-core) so, dass alle Funktionen dieser Klasse übernommen werden. Die Daten in diesem Store werden gemäß der Konfiguration der ContextHub-Persistenz beibehalten.

## ContextHub.Store.SessionStore {#contexthub-store-sessionstore}

ContextHub.Store.SessionStore erweitert [ContextHub.Store.Core](/help/sites-developing/contexthub-api.md#contexthub-store-core) so, dass alle Funktionen dieser Klasse übernommen werden. Die Daten in diesem Store werden mithilfe der speicherinternen Persistenz beibehalten (JavaScript-Objekt).

## ContextHub.UI {#contexthub-ui}

Verwaltet Benutzeroberflächenmodule und Benutzeroberflächenmodul-Renderer.

### Funktionen (ContextHub.UI) {#functions-contexthub-ui}

#### registerRenderer(moduleType, renderer, dontRender) {#registerrenderer-moduletype-renderer-dontrender}

Registriert einen UI-Modul-Renderer bei ContextHub. Nachdem der Renderer registriert wurde, kann er verwendet werden, um [UI-Module zu erstellen](ch-configuring.md#adding-a-ui-module). Verwenden Sie diese Funktion, wenn Sie [ContextHub.UI.BaseModuleRenderer](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types) erweitern, um einen benutzerdefinierten Benutzeroberflächenmodul-Renderer zu erstellen.

**Parameter**

* **moduleType:**(String) Die Kennung für den Benutzeroberflächenmodulrenderer. Wenn ein Renderer bereits mit dem angegebenen Wert registriert ist, wird die Registrierung des vorhandenen Renderers aufgehoben, bevor dieser Renderer registriert wird.
* **renderer:** (String) Der Name der Klasse, die das Benutzeroberflächenmodul rendert.
* **dontRender:** (Boolesch) Auf `true` gesetzt, um zu verhindern, dass die ContextHub-Benutzeroberfläche nach der Registrierung des Renderers gerendert wird. Der Standardwert ist `false`.

**Beispiel**

Im folgenden Beispiel wird ein Renderer als contexthub.browserinfo-Modultyp registriert.

```
ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());
```

## ContextHub.Utils.Cookie {#contexthub-utils-cookie}

Eine Service-Programmklasse für die Interaktion mit Cookies.

### Funktionen (ContextHub.Utils.Cookie) {#functions-contexthub-utils-cookie}

#### exists(key) {#exists-key}

Ermittelt, ob ein Cookie vorhanden ist.

**Parameter**

* **key:** Ein `String`, der den Schlüssel des Cookies enthält, für das Sie testen.

**Rückgabe**

Wenn `boolean` den Wert „true“ aufweist, bedeutet das, dass das Cookie vorhanden ist.

**Beispiel**

```
if (ContextHub.Utils.Cookie.exists("name")) {
   // conditionally-executed code
}
```

#### getAllItems(filter) {#getallitems-filter}

Gibt alle Cookies zurück, deren Schlüssel einem Filter entsprechen.

**Parameter**

* (Wahlweise) **filter:** Kriterien für übereinstimmende Cookie-Schlüssel. Um alle Cookies zurückzugeben, geben Sie keinen Wert an. Die folgenden Typen werden unterstützt:

   * Zeichenfolge: Die Zeichenfolge wird mit dem Cookie-Schlüssel verglichen.
   * Array: Jedes Element im Array ist ein Filter.
   * Ein RegExp-Objekt: Die Testfunktion des Objekts wird verwendet, um Cookie-Schlüssel abzugleichen.
   * Eine Funktion: Eine Funktion, die einen Cookie-Schlüssel für eine Übereinstimmung testet. Die Funktion muss den Cookie-Schlüssel als Parameter annehmen und true zurückgeben, wenn der Test eine Übereinstimmung bestätigt.

**Rückgabe**

Ein Objekt von Cookies. Objekteigenschaften sind Cookie-Schlüssel und Schlüsselwerte sind Cookie-Werte.

**Beispiel**

```
ContextHub.Utils.Cookie.getAllItems([/^cq-authoring/, /^cq-editor/])
```

#### getItem(key)  {#getitem-key-1}

Gibt einen Cookie-Wert zurück.

**Parameter**

* **key:** Der Schlüssel des Cookies, für das Sie einen Wert abrufen möchten.

**Rückgabe**

Das Cookie-Wert oder `null`, wenn kein Cookie für den Schlüssel gefunden wurde.

**Beispiel**

```
ContextHub.Utils.Cookie.getItem("name");
```

#### getKeys(filter) {#getkeys-filter}

Gibt ein Array der Schlüssel der vorhandenen Cookies zurück, die mit einem Filter übereinstimmen.

**Parameter**

* **filter:** Kriterien für übereinstimmende Cookie-Schlüssel. Die folgenden Typen werden unterstützt:

   * Zeichenfolge: Die Zeichenfolge wird mit dem Cookie-Schlüssel verglichen.
   * Array: Jedes Element im Array ist ein Filter.
   * Ein RegExp-Objekt: Die Testfunktion des Objekts wird verwendet, um Cookie-Schlüssel abzugleichen.
   * Eine Funktion: Eine Funktion, die einen Cookie-Schlüssel für eine Übereinstimmung testet. Die Funktion muss den Cookie-Schlüssel als Parameter annehmen und `true` zurückgeben, wenn der Test eine Übereinstimmung bestätigt.

**Rückgabe**

Ein Array von Zeichenfolgen, wobei jede Zeichenfolge der Schlüssel eines Cookies ist, das dem Filter entspricht.

**Beispiel**

```
ContextHub.Utils.Cookie.getKeys([/^cq-authoring/, /^cq-editor/])
```

#### removeItem(key, options)  {#removeitem-key-options-1}

Entfernt ein Cookie. Um das Cookie zu entfernen, wird der Wert auf eine leere Zeichenfolge gesetzt, und das Ablaufdatum wird auf den Tag vor dem aktuellen Datum gesetzt.

**Parameter**

* **key:** Ein `String`-Wert, der den Schlüssel des zu entfernenden Cookies darstellt.

* **options:** Ein Objekt, das Eigenschaftswerte zum Konfigurieren der Cookie-Attribute enthält. Siehe ` [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)`-Funktion für Informationen. Die `expires`-Eigenschaft hat keine Auswirkungen.

**Rückgabe**

Diese Funktion gibt keinen Wert zurück.

**Beispiel**

```
ContextHub.Utils.Cookie.vanish([/^cq-authoring/, 'cq-scrollpos']);
```

#### setItem(key, value, options)  {#setitem-key-value-options-1}

Erstellt ein Cookie mit dem angegebenen Schlüssel und Wert und fügt das Cookie zum aktuellen Dokument hinzu. Optional können Sie Optionen angeben, die die Attribute des Cookies konfigurieren.

**Parameter**

* **key:** Eine Zeichenfolge, die den Schlüssel des Cookies enthält.
* **value:** Eine Zeichenfolge, die den Wert des Cookies enthält.
* **options:** (Optional) Ein Objekt, das eine der folgenden Eigenschaften enthält, die die Cookie-Attribute konfigurieren:

   * expires: Ein `date`- oder `number`wert, der angibt, wann das Cookie abläuft. Ein Datumswert gibt die absolute Verfallszeit an. Eine Zahl (in Tagen) legt die Verfallszeit auf die aktuelle Zeit plus die Zahl fest. Der Standardwert ist `undefined`.
   * secure: Ein `boolean` Wert, der das `Secure`-Attribut des Cookies angibt. Der Standardwert ist `false`.
   * path: Ein `String`-Wert, der als `Path`-Attribut des Cookies verwendet wird. Der Standardwert ist `undefined`.

**Rückgabe**

Das Cookie mit dem eingestellten Wert.

**Beispiel**

```
ContextHub.Utils.Cookie.setItem("name", "mycookie", {
    expires: 3,
    domain: 'localhost',
    path: '/some/directory',
    secure: true
});
```

#### vanish(filter, options) {#vanish-filter-options}

Entfernt alle Cookies, die einem gegebenen Filter entsprechen. Cookies werden mithilfe der Funktion „getKeys“ abgeglichen und mithilfe der Funktion „removeItem“ entfernt.

**Parameter**

* **:** Das `filter`filter-Argument, das beim Aufruf der Funktion `[getKeys](/help/sites-developing/contexthub-api.md#getkeys-filter)` verwendet wird.

* **:** Das `options`options-Argument, das beim Aufruf der Funktion `[removeItem](/help/sites-developing/contexthub-api.md#removeitem-key-options)` verwendet wird.

**Rückgabe**

Diese Funktion gibt keinen Wert zurück.

## ContextHub.Utils.Eventing {#contexthub-utils-eventing}

Ermöglicht es Ihnen, Funktionen an ContextHub-Store-Ereignisse zu binden und zu lösen. Greifen Sie auf ContextHub.Utils.Eventing-Objekte für einen Store zu, der die [eventing](/help/sites-developing/contexthub-api.md#eventing)-Eigenschaft des Stores verwendet.

### Funktionen (ContextHub.Utils.Eventing) {#functions-contexthub-utils-eventing}

#### off(name, selector) {#off-name-selector}

Löst eine Funktion von einem Ereignis.

**Parameter**

* **name:** Der [Name des Ereignisses](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing), für das Sie die Bindung der Funktion aufheben.

* **selector:** Der Selektor, der die Bindung identifiziert. (Siehe `selector`-Parameter für die [Ein](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents)-und-[Einmal](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents)-Funktionen).

**Rückgabe**

Diese Funktion gibt keinen Wert zurück.

#### on(name, handler, selector, triggerForPastEvents) {#on-name-handler-selector-triggerforpastevents}

Bindet eine Funktion an ein Ereignis. Die Funktion wird jedes Mal aufgerufen, wenn das Ereignis eintritt. Optional kann die Funktion für Ereignisse aufgerufen werden, die in der Vergangenheit aufgetreten sind, bevor die Bindung hergestellt wurde.

**Parameter**

* **name:** (Zeichenfolge) Der [Name des Ereignisses](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing), an das Sie die Funktion binden.

* **handler:** (Funktion) Die Funktion zum Binden an das Ereignis.
* **selector**: (String) Eine eindeutige Kennung für die Bindung. Sie benötigen den Selektor, um die Bindung zu identifizieren, wenn Sie die `off`-Funktion verwenden möchten, um die Bindung zu entfernen.

* **triggerForPastEvents:** (Boolesch) Gibt an, ob der Handler für Ereignisse ausgeführt werden soll, die in der Vergangenheit aufgetreten sind. Ein Wert `true` ruft den Handler für vergangene Ereignisse auf. Ein Wert `false` ruft den Handler für zukünftige Ereignisse auf. Der Standardwert ist `true`.

**Rückgabe**

Wenn das `triggerForPastEvents`-Argument `true` ist, gibt diese Funktion einen `boolean`-Wert zurück, der angibt, ob das Ereignis in der Vergangenheit aufgetreten ist:

* `true`: Das Ereignis ist in der Vergangenheit aufgetreten und der Handler wird aufgerufen.
* `false`: Das Ereignis ist nicht in der Vergangenheit aufgetreten.

Wenn `triggerForPastEvents` den Wert `false` ergibt, gibt diese Funktion keinen Wert zurück.

**Beispiel**

Im folgenden Beispiel wird eine Funktion an das Datenereignis des Geolocation-Stores gebunden. Die Funktion füllt ein Element auf der Seite mit dem Wert für das Datenelement „Breite“ aus dem Store.

```
<div class="location">
    <p>latitude: <span id="lat"></span></p>
</div>

<script>
    var geostore = ContextHub.getStore("geolocation");
    geostore.eventing.on(ContextHub.Constants.EVENT_DATA_UPDATE,getlat,"getlat");

    function getlat(){
       latitude = geostore.getItem("latitude");
       $("#lat").html(latitude);
    }
</script>
```

#### once(name, handler, selector, triggerForPastEvents) {#once-name-handler-selector-triggerforpastevents}

Bindet eine Funktion an ein Ereignis. Die Funktion wird nur einmal beim ersten Auftreten des Ereignisses aufgerufen. Optional kann die Funktion für das Ereignis aufgerufen werden, das in der Vergangenheit aufgetreten ist, bevor die Bindung hergestellt wurde.

**Parameter**

* **name:** (Zeichenfolge) Der [Name des Ereignisses](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing), an das Sie die Funktion binden.

* **handler:** (Funktion) Die Funktion zum Binden an das Ereignis.
* **selector**: (String) Eine eindeutige Kennung für die Bindung. Sie benötigen den Selektor, um die Bindung zu identifizieren, wenn Sie die `off`-Funktion verwenden möchten, um die Bindung zu entfernen.

* **triggerForPastEvents:** (Boolesch) Gibt an, ob der Handler für Ereignisse ausgeführt werden soll, die in der Vergangenheit aufgetreten sind. Ein Wert `true` ruft den Handler für vergangene Ereignisse auf. Ein Wert `false` ruft den Handler für zukünftige Ereignisse auf. Der Standardwert ist `true`.

**Rückgabe**

Wenn das `triggerForPastEvents`-Argument `true` ist, gibt diese Funktion einen `boolean`-Wert zurück, der angibt, ob das Ereignis in der Vergangenheit aufgetreten ist:

* `true`: Das Ereignis ist in der Vergangenheit aufgetreten und der Handler wird aufgerufen.
* `false`: Das Ereignis ist nicht in der Vergangenheit aufgetreten.

Wenn `triggerForPastEvents` den Wert `false` ergibt, gibt diese Funktion keinen Wert zurück.

## ContextHub.Utils.inheritance {#contexthub-utils-inheritance}

Eine Service-Programmklasse, mit der ein Objekt die Eigenschaften und Methoden eines anderen Objekts übernehmen kann.

### Funktionen (ContextHub.Utils.inheritance) {#functions-contexthub-utils-inheritance}

#### inherit(child, parent) {#inherit-child-parent}

Bewirkt, dass ein Objekt die Eigenschaften und Methoden eines anderen Objekts übernimmt.

**Parameter**

* **child:** (Object) Das Objekt, das übernimmt.
* **parent:** (Object) Das Objekt, das die übernommenen Eigenschaften und Methoden definiert.

## ContextHub.Utils.JSON {#contexthub-utils-json}

Stellt Funktionen zum Serialisieren von Objekten im JSON-Format und zum Deserialisieren von JSON-Strings in Objekten bereit.

### Funktionen (ContextHub.Utils.JSON) {#functions-contexthub-utils-json}

#### parse(data) {#parse-data}

Analysiert einen String als JSON und konvertiert ihn in ein JavaScript-Objekt.

**Parameter**

* **data:** Ein Zeichenfolgenwert im JSON-Format.

**Rückgabe**

Ein JavaScript-Objekt.

**Beispiel**

Der Code `ContextHub.Utils.JSON.parse("{'city':'Basel','country':'Switzerland','population':'173330'}");` gibt das folgende Objekt zurück:

```
Object {
   city: "Basel",
   country: "Switzerland",
   population: 173330
}
```

#### stringify(data) {#stringify-data}

Serialisiert JavaScript-Werte und -Objekte in Zeichenfolgenwerte des JSON-Formats.

**Parameter**

* **data:** Der Wert oder das zu serialisierende Objekt. Diese Funktion unterstützt boolesche Werte, Array-, Zahlen-, String- und Datumswerte.

**Rückgabe**

Der serialisierte String-Wert. Wenn `data` ein R`egExp`-Wert ist, gibt diese Funktion ein leeres Objekt zurück. Wenn `data` eine Funktion ist, wird `undefined` zurückgegeben.

**Beispiel**

Der folgende Code gibt `"{'city':'Basel','country':'Switzerland','population':'173330'}":` zurück.

```
ContextHub.Utils.JSON.stringify({
   city: "Basel",
   country: "Switzerland",
   population: 173330
});
```

## ContextHub.Utils.JSON.tree {#contexthub-utils-json-tree}

Diese Klasse erleichtert die Manipulation von Datenobjekten, die gespeichert oder aus ContextHub-Stores abgerufen werden.

### Funktionen (ContextHub.Utils.JSON.tree) {#functions-contexthub-utils-json-tree}

#### addAllItems() {#addallitems}

Erstellt eine Kopie eines Datenobjekts und fügt die Datenstruktur aus einem zweiten Objekt hinzu. Die Funktion gibt die Kopie zurück und ändert keines der ursprünglichen Objekte. Wenn die Datenbäume der beiden Objekte identische Schlüssel enthalten, überschreibt der Wert des zweiten Objekts den Wert des ersten Objekts.

**Parameter**

* **tree:** Das Objekt, das kopiert wird.
* **secondTree:** Das Objekt, das mit der Kopie des `tree`-Objekts zusammengeführt wird.

**Rückgabe**

Ein Objekt, das die zusammengeführten Daten enthält.

#### cleanup() {#cleanup}

Erstellt eine Kopie eines Objekts, sucht und entfernt Elemente in der Datenstruktur, die keine Werte, Nullwerte oder undefinierten Werte enthalten, und gibt die Kopie zurück.

**Parameter**

* **tree:** Das Objekt zum Bereinigen.

**Rückgabe**

Eine Kopie des Baums, der bereinigt wird.

#### getItem() {#getitem}

Ruft den Wert eines Objekts für den Schlüssel ab.

**Parameter**

* **tree:** Das Datenobjekt.
* **key:** Der Schlüssel für den Wert, den Sie abrufen möchten.

**Rückgabe**

Der Wert, der dem Schlüssel entspricht. Wenn der Schlüssel untergeordnete Schlüssel hat, gibt diese Funktion ein komplexes Objekt zurück. Wenn der Typ des Werts für den Schlüssel `undefined` ist, wird `null` zurückgegeben.

**Beispiel**

Betrachten Sie das folgende JavaScript-Objekt:

```
myObject {
  user: {
    location: {
      city: "Basel",
        details: {
          population: 173330,
          elevation: 260
        }
      }
    }
  }
```

Der folgende Beispiel-Code gibt den Wert `260` zurück.

```
ContextHub.Utils.JSON.tree.getItem(myObject, "/user/location/details/elevation");
```

Der folgende Beispiel-Code ruft den Wert für einen Schlüssel mit untergeordneten Schlüsseln ab:

```
ContextHub.Utils.JSON.tree.getItem(myObject, "/user");
```

Die Funktion gibt das folgende Objekt zurück:

```
Object {
  location: {
    city: "Basel",
    details: {
      population: 173330,
      elevation: 260
    }
  }
}
```

#### getKeys() {#getkeys}

Ruft alle Schlüssel aus der Datenstruktur eines Objekts ab. Optional können Sie nur die Schlüssel der untergeordneten Elemente eines bestimmten Schlüssels abrufen. Sie können auch optional eine Sortierreihenfolge der abgerufenen Schlüssel angeben.

**Parameter**

* **tree:** Das Objekt, von dem die Schlüssel der Datenstruktur abgerufen werden.
* **parent:** (Optional) Der Schlüssel eines Elements in einer Struktur, für das Sie die Schlüssel der untergeordneten Elemente abrufen möchten.
* **order:** (Optional) Eine Funktion, die die Sortierreihenfolge der zurückgegebenen Schlüssel bestimmt. (Siehe [Array.prototype.sort](https://developer.mozilla.org/de-DE/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) im Mozilla Developer Network.)

**Rückgabe**

Ein Array von Schlüsseln.

**Beispiel**

Betrachten Sie das folgende Objekt:

```
myObject {
  location: {
    weather: {
      temperature: "28C",
      humidity: "77%",
      precipitation: "10%",
      wind: "8km/h"
    },
    city: "Basel",
    country: "Switzerland",
    longitude: 7.5925727,
    latitude: 47.557421
  }
}
```

Das Skript `ContextHub.Utils.JSON.tree.getKeys(myObject);` gibt das folgende Array zurück:

```
["/location", "/location/city", "/location/country", "/location/latitude", "/location/longitude", "/location/weather", "/location/weather/humidity", "/location/weather/precipitation", "/location/weather/temperature", "/location/weather/wind"]
```

#### removeItem() {#removeitem}

Erstellt eine Kopie eines bestimmten Objekts, entfernt den angegebenen Zweig aus der Datenstruktur und gibt die geänderte Kopie zurück.

**Parameter**

* tree: Ein Datenobjekt.
* key: Der zu entfernende Schlüssel.

**Rückgabe**

Eine Kopie des ursprünglichen Datenobjekts mit entferntem Schlüssel.

**Beispiel**

Betrachten Sie das folgende Objekt:

```
myObject {
  one: {
    foo: "bar",
    two: {
      three: {
        four: {
          five: 5,
          six: 6
        }
      }
    }
  }
}
```

Das folgende Beispielskript entfernt den Zweig „/one/two/three/four“ aus der Datenstruktur:

```
myObject = ContextHub.Utils.JSON.tree.removeItem(myObject, "/one/two/three/four");
```

Die Funktion gibt das folgende Objekt zurück:

```
myObject {
  one: {
    foo: "bar"
  }
}
```

#### sanitizeKey(key) {#sanitizekey-key}

Bereinigt Stringwerte, um sie als Schlüssel nutzbar zu machen. Um eine Zeichenfolge zu bereinigen, führt diese Funktion die folgenden Aktionen aus:

* Reduziert mehrere aufeinander folgende Schrägstriche zu einem einzigen Schrägstrich.
* Entfernt Leerzeichen vom Anfang und Ende der Zeichenfolge.
* Teilt das Ergebnis in ein Array von Zeichenfolgen, die durch Schrägstriche abgegrenzt werden.

Verwenden Sie das resultierende Array, um einen verwendbaren Schlüssel zu erstellen.  **Parameter**

* **key:** Der zu bereinigende `string`.

**Rückgabe**

Ein Array von `string`-Werten, wobei jeder String der Teil des `key` ist, der durch Schrägstriche abgegrenzt wurde. stellt den bereinigten Schlüssel dar. Wenn das bereinigte Array eine Länge von hat, gibt diese Funktion `null`null zurück.

**Beispiel**

Der folgende Code bereinigt einen String zum Erstellen des Arrays `["this", "is", "a", "path"]` und generiert dann den Schlüssel `"/this/is/a/path"` aus dem Array:

```
var key = " / this////is/a/path ";
ContextHub.Utils.JSON.tree.sanitizeKey(key)
"/" + ContextHub.Utils.JSON.tree.sanitizeKey(key).join("/");
```

#### setItem(tree, key, value) {#setitem-tree-key-value}

Fügt dem Datenbaum einer Kopie eines Objekts ein Schlüssel/Wert-Paar hinzu. Weitere Informationen zu Datenbäumen finden Sie unter [Persistenz](/help/sites-developing/contexthub.md#persistence).

**Parameter**

* tree: Ein Datenobjekt.
* key: Der Schlüssel, der mit dem hinzuzufügenden Wert verknüpft werden soll. Der Schlüssel ist der Pfad zum Element im Datenbaum. Diese Funktion ruft `ContextHub.Utils.JSON.tree.sanitize` auf, um den Schlüssel vor dem Hinzufügen zu bereinigen.
* value: Der Wert, der der Datenstruktur hinzugefügt werden soll.

**Rückgabe**

Eine Kopie des `tree`-Objekts, das das `value`/`key`-Paar enthält.

**Beispiel**

Betrachten Sie den folgenden JavaScript-Code:

```
var myObject = {
     user: {
        location: {
           city: "Basel"
           }
        }
     };

var myKey = "/user/location/details";

var myValue = {
      population: 173330,
      elevation: 260
     };

myObject = ContextHub.Utils.JSON.tree.setItem(myObject, myKey, myValue);
```

Das Objekt myObject hat den folgenden Wert:

## ContextHub.Utils.storeCandidates {#contexthub-utils-storecandidates}

Ermöglicht es Ihnen, Store-Kandidaten zu registrieren und registrierte Store-Kandidaten zu erhalten.

### Funktionen (ContextHub.Utils.storeCandidates) {#functions-contexthub-utils-storecandidates}

#### getRegisteredCandidates(storeType) {#getregisteredcandidates-storetype}

Gibt die Store-Typen zurück, die als Store-Kandidaten registriert sind. Sie können die registrierten Kandidaten entweder eines bestimmten Storetyps oder aller Storetypen abrufen.

**Parameter**

* **storeType:** (Zeichenfolge) Der Name des Store-Typs. Siehe den `storeType`-Parameter der Funktion [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](/help/sites-developing/contexthub-api.md#contexthub-utils-storecandidates).

**Rückgabe**

Ein Objekt von Storetypen. Die Objekteigenschaften sind die Namen des Store-Typs und die Eigenschaftswerte sind ein Array registrierter Store-Kandidaten.

#### getStoreFromCandidates(storeType) {#getstorefromcandidates-storetype}

Gibt einen Store-Typ aus den registrierten Kandidaten zurück. Wenn mehr als ein Store-Typ mit demselben Namen erneut registriert wird, gibt die Funktion den Store-Typ mit der höchsten Priorität zurück.

**Parameter**

* storeType: (String) Der Name des Store-Kandidaten. Siehe den `storeType`-Parameter der Funktion [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](/help/sites-developing/contexthub-api.md#registerstorecandidate-store-storetype-priority-applies).

**Rückgabe**

Ein Objekt, das den registrierten Store-Kandidaten darstellt. Wenn der angeforderte Store-Typ nicht registriert ist, wird ein Fehler ausgegeben.

#### getSupportedStoreTypes() {#getsupportedstoretypes}

Gibt die Namen der Storetypen zurück, die als Storekandidaten registriert sind. Diese Funktion benötigt keine Parameter.

**Rückgabe**

Ein Array von String-Werten, wobei jeder String der Store-Typ ist, mit dem ein Store-Kandidat registriert wurde. Siehe den `storeType`-Parameter der Funktion [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](/help/sites-developing/contexthub-api.md#contexthub-utils-storecandidates).

#### registerStoreCandidate(store, storeType, priority, applies) {#registerstorecandidate-store-storetype-priority-applies}

Registriert ein Store-Objekt als Store-Kandidaten mit einem Namen und einer Priorität.

Die Priorität ist eine Zahl, die die Bedeutung der gleichnamigen Store angibt. Wenn ein Storekandidat unter Verwendung des gleichen Namens wie ein bereits registrierter Storekandidat registriert wird, wird der Kandidat mit der höheren Priorität verwendet. Beim Registrieren eines Store-Kandidaten wird der Store nur registriert, wenn die Priorität höher ist als die von registrierten Store-Kandidaten mit dem gleichen Namen.

**Parameter**

* **store:** (Object) Das Storeobjekt, das als Storekandidat registriert werden soll.
* **storeType:** (String) Der Name des Store-Kandidaten. Dieser Wert wird beim Erstellen einer Instanz des Store-Kandidaten benötigt.
* **priority:** (Number) die Priorität des Storekandidaten.
* **applies:** (Function) Die aufzurufende Funktion wertet die Anwendbarkeit des Stores in der aktuellen Umgebung aus. Die Funktion muss `true` zurückgeben, wenn der Store anwendbar ist, andernfalls `false`. Der Standardwert ist eine Funktion, die „true“ zurückgibt: `function() {return true;}`

**Beispiel**

```
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandiate', 0);
```
