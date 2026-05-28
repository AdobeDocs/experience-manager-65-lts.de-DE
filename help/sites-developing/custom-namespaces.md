---
title: Benutzerdefinierte Namespaces
description: Erfahren Sie, wie Sie benutzerdefinierte Namespaces definieren und für AEM 6.5 LTS bereitstellen.
solution: Experience Manager, Experience Manager Sites
feature: Developing,JCR
role: Developer
source-git-commit: 475a77e8e4ff0ecd19a939fd3b3c9294adf24997
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 66%

---


# Benutzerdefinierte Namespaces{#custom-namespaces}

Erfahren Sie, wie Sie benutzerdefinierte [ (Namespaces) definieren und ](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/1.0/4.5_Namespaces.html) AEM 6.5 LTS bereitstellen.

Benutzerdefinierte Namespaces sind der optionale Teil einer JCR-Eigenschaft vor einem Doppelpunkt (`:`). AEM verwendet verschiedene Namespaces, z. B.:

+ `jcr` für JCR-Systemeigenschaften
+ `cq` für AEM-Eigenschaften (ehemals Adobe CQ)
+ `dam` für DAM-Assets-spezifische AEM-Eigenschaften
+ `dc` für Dublin Core-Eigenschaften

… und viele mehr

Namespaces können verwendet werden, um den Umfang und den Zweck einer Eigenschaft zu kennzeichnen. Durch die Erstellung eines benutzerdefinierten Namespace, häufig Ihres Unternehmensnamens, können Knoten oder Eigenschaften, die für Ihre AEM-Implementierung spezifisch sind, eindeutig identifiziert werden und unternehmensbezogene Daten enthalten.

Benutzerdefinierte Namespaces werden in [Sling Repository Initialization (repoinit)](https://sling.apache.org/documentation/bundles/repository-initialization.html)-Skripten verwaltet und als OSGi-Konfigurationen im Konfigurationspaket Ihres Projekts bereitgestellt (z. B. `ui.config`).

## Ressourcen {#resources}

+ [Dokumentation zur Sling Repository-Initialisierung (repoinit)](https://sling.apache.org/documentation/bundles/repository-initialization.html#repoinit-parser-test-scenarios)

## Code {#code}

Der folgende Code wird zum Konfigurieren eines `wknd`-Namespace verwendet.

### RepositoryInitializer-OSGi-Konfiguration

`/ui.config/src/main/content/jcr_root/apps/wknd-examples/osgiconfig/config/org.apache.sling.jcr.repoinit.RepositoryInitializer~wknd-examples-namespaces.cfg.json`

```json
{
    "scripts": [
        "register namespace (wknd) https://site.wknd/1.0"
    ]
}
```

Dadurch können benutzerdefinierte Eigenschaften, die den `wknd`-Namespace verwenden, wie mit dem ersten Parameter nach der `register namespace` angegeben, in AEM verwendet werden. Erweiterte Skriptdefinitionen finden Sie in den Beispielen in der [Dokumentation zur Initialisierung des Sling-Repositorys (repoinit)](https://sling.apache.org/documentation/bundles/repository-initialization.html#repoinit-parser-test-scenarios).
