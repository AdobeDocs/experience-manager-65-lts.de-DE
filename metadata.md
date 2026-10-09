---
product: adobe experience manager
description: Dokumentation zu Adobe Experience Manager 6.5 LTS.
git-repo: https://github.com/AdobeDocs/experience-manager-65-lts.en
index: true
type: Documentation
solution: Experience Manager, Experience Manager 6.5 LTS
nudge: 'yes'
usetq: true
landing-page-name: experience-manager-65-lts
landing-page-breadcrumb-title: AEM 6.5 LTS
version: Experience Manager 6.5 LTS
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
cloud: Experience Cloud
recommendations: noDisplay
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: ae206583-dab1-444b-b978-a37aad4a988c
    internal-label: Experience Manager 6.5 LTS
source-git-commit: 58a193a94397bae99fec88ee9353c415d374912a
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 2%
---

# Metadaten für die interne Verwendung

Metadaten im GitHub-Authoring-System sind hierarchisch und werden in den folgenden zunehmenden Präzedenzfällen definiert.

1. metadata.md
1. toC
1. Artikel

Metadaten, die in der Datei „metadata.md“ definiert sind, gelten für das gesamte Repository, können jedoch auf der Inhaltsverzeichnis- und Artikelebene überschrieben werden. Jede Überschreibung der Metadaten sollte auf der niedrigstmöglichen Ebene erfolgen.

Die Metadaten im Repository experience-manager-cloud-service.en sind das erforderliche Minimum.

metadata.md

* `product`
* `git-repo`
* `index`
* `solution-title`
* `solution-hub-url`
* `getting-started-title`
* `getting-started-url`
* `tutorials-title`
* `tutorials-url`

toCS

* `sub-product`
* `user-guide-title`

Artikel

* `title`
* `description`
* `contentOwner` (nur auf Asset-Kerninhalte unter `/help/assets`)
