---
title: Aktivieren eines JSON-Exports für eine Komponente
description: Komponenten können angepasst werden, um einen JSON-Export ihrer Inhalte basierend auf einem Modeler-Framework zu generieren.
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: aeb8e954-dd6c-4e18-bb78-6eaac86fa4b9
source-git-commit: cc96a14ebaf9f895a798b5f4904f5b4769b990bb
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 57%

---

# Aktivieren eines JSON-Exports für eine Komponente{#enabling-json-export-for-a-component}

Komponenten können angepasst werden, um einen JSON-Export ihrer Inhalte basierend auf einem Modeler-Framework zu generieren.

## Überblick {#overview}

Der JSON-Export basiert auf [Sling-Modellen](https://sling.apache.org/documentation/bundles/models.html) und auf dem [Sling Model Exporter](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130)-Framework, das selbst auf [Jackson-Anmerkungen](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) beruht.

Dieser Ansatz bedeutet, dass die Komponente über ein Sling-Modell verfügen muss, wenn sie JSON exportieren muss. Führen Sie daher diese beiden Schritte aus, um den JSON-Export für jede Komponente zu aktivieren.

* [Definieren eines Sling-Modells für die Komponente](/help/sites-developing/json-exporter-components.md#define-a-sling-model-for-the-component)
* [Kommentieren der Sling-Modell-Oberfläche](#annotate-the-sling-model-interface)

## Definieren eines Sling-Modells für die Komponente {#define-a-sling-model-for-the-component}

Zunächst muss ein Sling-Modell für die Komponente definiert werden.

>[!NOTE]
>
>Ein Beispiel für die Verwendung von Sling-Modellen finden Sie unter [Entwickeln von Sling-Modell-Exportern in AEM](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter).

Die Implementierungsklasse des Sling-Modells muss wie folgt kommentiert werden:

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

Dadurch wird sichergestellt, dass Ihre Komponente eigenständig mit dem `.model`-Selektor und der `.json`-Erweiterung exportiert werden kann.

Darüber hinaus gibt sie an, dass die Sling-Modell-Klasse in die `ComponentExporter`-Schnittstelle angepasst werden kann.

>[!NOTE]
>
>Jackson-Anmerkungen werden nicht auf der Ebene der Sling-Modell-Klasse festgelegt, sondern auf der Ebene der Modell-Oberfläche. Dadurch soll sichergestellt werden, dass der JSON-Export als Teil der Komponenten-API betrachtet wird.

>[!NOTE]
>
>Die Klassen `ExporterConstants` und `ComponentExporter` stammen aus dem `com.adobe.cq.export.json`-Paket.

### Mehrere Selektoren verwenden {#multiple-selectors}

Obwohl dies kein Standardnutzungsszenario ist, können zusätzlich zum `model`-Selektor mehrere Selektoren konfiguriert werden.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

In einem solchen Fall muss jedoch der `model` Selektor der erste Selektor sein und die Erweiterung muss `.json` sein.

## Kommentieren der Sling-Modell-Oberfläche {#annotate-the-sling-model-interface}

Damit das JSON Exporter-Framework es verarbeiten kann, muss die Modelloberfläche die `ComponentExporter`-Schnittstelle implementieren (oder für eine Container-Komponente `ContainerExporter`).

Für die entsprechende Sling-Modell-Oberfläche (`MyComponent`) wird in diesem Fall über [Jackson-Anmerkungen](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) definiert, wie sie exportiert (serialisiert) werden soll.

Die Modellschnittstelle muss ordnungsgemäß kommentiert sein, um zu definieren, welche Methoden serialisiert werden. Standardmäßig werden alle Methoden, die die übliche Namenskonvention für Getter einhalten, serialisiert und leiten ihre JSON-Eigenschaftsnamen natürlich von den Getter-Namen ab. Dieser Ansatz kann mithilfe von `@JsonIgnore` oder `@JsonProperty` verhindert oder überschrieben werden, um die JSON-Eigenschaft umzubenennen.

## Beispiel {#example}

Die Kernkomponenten unterstützen den JSON-Export seit der Version [1.1.0 der Kernkomponenten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/introduction). Sie können als Referenz verwendet werden.

Ein Beispiel ist die Sling-Modell-Implementierung der Bild-Kernkomponente und deren kommentierte Oberfläche.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt aem-core-wcm-components auf GitHub](https://github.com/adobe/aem-core-wcm-components)
* Laden Sie das Projekt als [ZIP-Datei](https://codeload.github.com/adobe/aem-core-wcm-components/zip/main) herunter


## Verwandte Dokumentation {#related-documentation}

* Das [Thema „Inhaltsfragmente“ im Assets-Benutzerhandbuch](https://experienceleague.adobe.com/en/docs/experience-manager-64/assets/home#)
* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
* [Bearbeitung mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md)
* [JSON-Exporter für Content Services](/help/sites-developing/json-exporter.md)
* [Kernkomponenten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/introduction) und die [Inhaltsfragmentkomponente](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/wcm-components/content-fragment-component)
