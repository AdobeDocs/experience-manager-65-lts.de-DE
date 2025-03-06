---
title: Aktualisieren von Inhaltsfragmenten für optimierte GraphQL-Filterung
description: Erfahren Sie, wie Sie Ihre Inhaltsfragmente für optimierte GraphQL-Filterung in Adobe Experience Manager für die Bereitstellung von Headless-Inhalten aktualisieren.
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
exl-id: 40211033-7084-4117-a3e2-73e504283266
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 95%

---

# Aktualisieren von Inhaltsfragmenten für optimierte GraphQL-Filterung {#updating-content-fragments-for-optimized-graphql-filtering}

Um die Leistung Ihrer GraphQL-Filter zu optimieren, führen Sie eine Prozedur aus, um Ihre Inhaltsfragmente zu aktualisieren.

>[!NOTE]
>
>Nach dem Aktualisieren Ihrer Inhaltsfragmente können Sie den Empfehlungen zum [Optimieren von GraphQL-Abfragen](/help/sites-developing/headless/graphql-api/graphql-optimization.md) folgen.

## Voraussetzungen {#prerequisites}

Stellen Sie sicher, dass Sie mindestens über die 6.5.17.0 Version von AEM verfügen.

## Aktualisieren von Inhaltsfragmenten {#updating-content-fragments}

Gehen Sie wie folgt vor, um die Prozedur auszuführen:

1. [Konfigurieren Sie die OSGi-Einstellungen](/help/sites-deploying/configuring-osgi.md) für die **Konfiguration des Inhaltsfragmentmigrationsauftrags**:

   ![OSGi-Konfiguration für den Inhaltsfragmentmigrationsauftrag](assets/cfm-graphql-update-01.png "OSGi-Konfiguration für den Inhaltsfragmentmigrationsauftrag")

1. Legen Sie diese beiden Parameter wie folgt im Dialogfeld fest:

   * **ContentFragmentMigration:Enabled** : `1`
   * **ContentFragmentMigration:Enforce** : `1`

1. **Speichern** Sie die Spezifikationen – die Aktualisierung beginnt.

1. Warten Sie, bis der Vorgang abgeschlossen ist. Der Vorgang ist abgeschlossen, wenn unter `/content/dam` die Eigenschaft `cfGlobalVersion` erscheint und auf `1` festgelegt ist.

1. Kehren Sie zur OSGi-Konfiguration zurück, um den Vorgang zu deaktivieren.

   Legen Sie diese beiden Parameter im Dialogfeld für die **Konfiguration des Inhaltsfragmentmigrationsauftrags** wie folgt fest:

   * **ContentFragmentMigration:Enabled** : `0`
   * **ContentFragmentMigration:Enforce** : `0`

## Einschränkungen {#limitations}

Beachten Sie die folgenden Einschränkungen:

* Die Leistungsoptimierung von GraphQL-Filtern ist erst nach einer vollständigen Aktualisierung aller Ihrer Inhaltsfragmente möglich (erkennbar am Vorhandensein der Eigenschaft `cfGlobalVersion` für den JCR-Knoten `/content/dam`)

* Wenn Inhaltsfragmente aus einem Inhaltspaket (mit `crx/de`) importiert werden, nachdem das Aktualisierungsverfahren ausgeführt wurde, werden diese Inhaltsfragmente erst dann in den GraphQL-Abfrageergebnissen berücksichtigt, wenn das Aktualisierungsverfahren erneut ausgeführt wird.
