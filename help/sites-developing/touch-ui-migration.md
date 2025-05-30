---
title: Migration zur Touch-optimierten Benutzeroberfläche
description: Erfahren Sie mehr über die Migration von Adobe Experience Manager zur Touch-optimierten Benutzeroberfläche und darüber, wie sich dies auf Sie auswirkt.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: introduction
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: e9b26de3-6e14-4187-8f25-6e56ee3092a7
source-git-commit: 013c9155817811913963ca514f7a6369b338d487
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 100%

---

# Migration zur Touch-optimierten Benutzeroberfläche{#migration-to-the-touch-ui}

Mit der Version 6.0 führte Adobe Experience Manager (AEM) eine neue Benutzeroberfläche ein, die als *Touch-optimierte Benutzeroberfläche* (auch einfach *Touch-Benutzeroberfläche* genannt) bezeichnet wird. Sie ist an Adobe Experience Cloud und die allgemeinen Richtlinien für die Benutzeroberflächen von Adobe angepasst. Dies ist inzwischen die Standard-Benutzeroberfläche in AEM. Die veraltete, Desktop-orientierte Benutzeroberfläche wird *klassische Benutzeroberfläche* genannt.

Wenn Sie AEM mit der klassischen Benutzeroberfläche verwendet haben, ergreifen Sie Maßnahmen, um Ihre Instanz zu migrieren. Diese Seite soll als Sprungbrett dienen, indem Links zu einzelnen Ressourcen bereitgestellt werden.

>[!NOTE]
>
>Ein solches Migrationsprojekt kann erhebliche Auswirkungen auf Ihre Instanz haben. Siehe [Verwalten von Projekten – Best Practices](/help/managing/best-practices.md) für empfohlene Richtlinien.

## Grundlagen {#the-basics}

Beachten Sie bei der Migration die folgenden wichtigen Unterschiede zwischen der klassischen und der Touch-optimierten Benutzeroberfläche:

<table>
 <tbody>
  <tr>
   <td>Klassische Benutzeroberfläche</td>
   <td>Touch-optimierte Benutzeroberfläche</td>
  </tr>
  <tr>
   <td>Wird im JCR-Repository als Knotenstruktur beschrieben. Jeder Knoten, der ein Element der Benutzeroberfläche darstellt, wird als <em>ExtJS-Widget</em> bezeichnet und Client-seitig von <code>ExtJS</code> gerendert.</td>
   <td>Wird im JCR-Repository ebenfalls als Knotenstruktur beschrieben. In diesem Fall bezieht sich jedoch jeder Knoten auf einen Sling-Ressourcentyp (Sling-Komponente), der für das Rendering zuständig ist. Die Benutzeroberfläche wird daher (im Grunde) Server-seitig gerendert.</td>
  </tr>
  <tr>
   <td><p><code>sling:resourceType</code></p>
    <ul>
     <li>nicht verwendet</li>
    </ul> </td>
   <td><code>sling:resourceType</code>
    <ul>
     <li>verwendet</li>
     <li>Beispiel<br /> <code>cq/gui/components/authoring/dialog</code><br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Dialogknoten:</p>
    <ul>
     <li>Name: <code>dialog</code></li>
     <li><code>jcr:primaryType</code>: <code>cq:Dialog</code></li>
    </ul> </td>
   <td><p>Dialogknoten:</p>
    <ul>
     <li>Name: <code>cq:dialog</code></li>
     <li><code>jcr:primaryType</code>: <code>nt:unstructured</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>JavaScript-Speicherort:</p>
    <ul>
     <li>Imperative Teile werden direkt mithilfe von Listenern eingebettet oder in Client-Bibliotheken verwaltet.</li>
    </ul> </td>
   <td><p>JavaScript-Speicherort:</p>
    <ul>
     <li>Imperative Teile können nicht in die Dialogfelddefinition eingebettet werden. Aufgabentrennung.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Ereignisverarbeitung:</p>
    <ul>
     <li>Dialogfeld-Widgets verweisen direkt auf JavaScript-Code.</li>
    </ul> </td>
   <td><p>Ereignisverarbeitung:</p>
    <ul>
     <li>JavaScript beobachtet Dialogfeldereignisse.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Rendering durch den Client:
    <ul>
     <li>Der Client erstellt dynamisch die Komponenten der Benutzeroberfläche.</li>
     <li>Komponentendefinition für Client-Anfragen (Pull) (als JSON) vom Server.</li>
    </ul> </td>
   <td>Vom Server durchgeführtes Rendering:
    <ul>
     <li>Der Client fragt Seiten zusammen mit der zugehörigen Benutzeroberfläche an.</li>
     <li>Der Server sendet (Push) die Benutzeroberfläche als HTML-Dokumente unter Verwendung von Coral-UI-Komponenten.<br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Das heißt, dass die Migration eines Bereichs Ihrer Benutzeroberfläche von der klassischen Benutzeroberfläche zur Touch-optimierten Benutzeroberfläche die Portierung eines *ExtJS-Widgets* zu einer *Sling-Komponente* bedeutet. Um dies zu vereinfachen, basiert die Touch-optimierte Benutzeroberfläche auf dem Granite-UI-Framework, das bereits einige Sling-Komponenten für die Benutzeroberfläche bereitstellt (als Granite-UI-Komponenten bezeichnet).

Die Grundlagen der Entwicklung der Touch-optimierten Benutzeroberfläche bieten ein solides Fundament:

* [Konzepte der Touch-optimierten Benutzeroberfläche von AEM](/help/sites-developing/touch-ui-concepts.md)
* [Struktur der Touch-optimierten Benutzeroberfläche von AEM](/help/sites-developing/touch-ui-structure.md)

## Migrieren der Seitenbearbeitung {#migrating-page-authoring}

Dialoge sind bei der Migration Ihrer Komponenten ein wichtiger Faktor:

* [Entwickeln von AEM Komponenten](/help/sites-developing/developing-components.md) (mit der Touch-optimierten Benutzeroberfläche)
* [Migration von einer klassischen Komponente](/help/sites-developing/developing-components.md#migrating-from-a-classic-component)
* [AEM Modernisierungs-Tools](/help/sites-developing/modernization-tools.md): helfen Ihnen, die Dialoge Ihrer klassischen Benutzeroberflächenkomponenten in die Touch-optimierte Benutzeroberfläche umzuwandeln

   * In der Touch-optimierten Benutzeroberfläche gibt es eine Kompatibilitätsebene, um ein Dialogfeld der klassischen Benutzeroberfläche in einem „Touch-UI-Wrapper“ zu öffnen. Dies ist jedoch mit einer eingeschränkten Funktionalität verbunden und wird für eine langfristige Nutzung nicht empfohlen.

* [Anpassen von Dialogfeldern in der Touch-optimierten Benutzeroberfläche](https://helpx.adobe.com/de/experience-manager/kt/eseminars/gems/aem-customizing-dialog-fields-in-touch-ui.html)
* [Erstellen einer neuen Feld-Komponente in der Granite-Benutzeroberfläche](/help/sites-developing/granite-ui-component.md)
* [Anpassen der Seitenbearbeitung](/help/sites-developing/customizing-page-authoring-touch.md) (mit der Touch-optimierten Benutzeroberfläche)

## Migrieren von Konsolen {#migrating-consoles}

Sie können auch die Konsolen anpassen:

* [Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md) (für die Touch-optimierte Benutzeroberfläche)

## Verwandte Aspekte {#related-considerations}

Obwohl dies nicht direkt mit einer Migration zur Touch-optimierten Benutzeroberfläche in Zusammenhang steht, sollten gleichzeitig auch verwandte Probleme in Betracht gezogen werden, da dies ebenfalls empfohlen wird:

* [Vorlagen](/help/sites-developing/templates.md) – [Bearbeitbare Vorlagen](/help/sites-developing/page-templates-editable.md)
* [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)
* [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de)

>[!NOTE]
>
>Siehe auch [Entwicklung – Best Practices](/help/sites-developing/best-practices.md).

## Weitere Ressourcen {#further-resources}

Umfassende Informationen zur Entwicklung von AEM finden Sie in der Sammlung von Ressourcen unter:

* [Benutzerhandbuch für Entwickler](/help/sites-developing/getting-started.md)
* [Dokumentation zur Granite-Benutzeroberfläche](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)
* [Tutorials und Videos zu AEM 6.5 Sites](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/overview.html?lang=de)
* [Erste Schritte bei der Entwicklung von AEM Sites – WKND-Tutorial](/help/sites-developing/getting-started.md)
* [AEM Gems](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/overview.html?lang=de)
* [AEM-Modernisierungs-Tools](https://opensource.adobe.com/aem-modernize-tools/)

>[!CAUTION]
>
>Die AEM-Modernisierung-Tools werden von der Community zusammengestellt, Adobe bietet keinerlei Unterstützung oder Garantie dafür.
