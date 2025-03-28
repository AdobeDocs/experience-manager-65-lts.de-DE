---
title: Integrieren von AEM Forms Workspace-Komponenten in Web-Anwendungen
description: Wiederverwenden von AEM Forms Workspace-Komponenten in Ihren eigenen Web-Anwendungen, um Funktionen zu nutzen und eine enge Integration zu ermöglichen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
exl-id: 62f70650-71bc-4c16-a947-f3a137ffc4df
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 100%

---

# Integrieren von AEM Forms Workspace-Komponenten in Web-Anwendungen {#integrating-aem-forms-workspace-components-in-web-applications}

Sie können AEM Forms Workspace-[Komponenten](/help/forms/using/description-reusable-components.md) in Ihrer eigenen Web-Anwendung verwenden. In der folgenden Beispielimplementierung werden Komponenten aus einem AEM Forms-Workspace-Entwicklungspaket genutzt, das auf einer CRX™-Instanz installiert ist, um eine Web-Anwendung zu erstellen. Passen Sie die unten gezeigte Lösung an Ihre Anforderungen an. In der Beispielimplementierung werden die Komponenten `UserInfo`, `FilterList` und `TaskList` innerhalb eines Webportals wiederverwendet.

1. Melden Sie sich in der CRXDE Lite-Umgebung unter `https://'[server]:[port]'/lc/crx/de/` an. Stellen Sie sicher, dass AEM Forms Workpace Dev-Paket installiert ist.
1. Erstellen Sie einen Pfad `/apps/sampleApplication/wscomponents`.
1. Kopieren Sie CSS, Bilder, js/libs, js/runtime und js/registry.js

   * von `/libs/ws`
   * zu `/apps/sampleApplication/wscomponents`.

1. Erstellen Sie eine Datei „demomain.js“ im Ordner /apps/sampleApplication/wscomponents/js. Kopieren Sie den Code aus /libs/ws/js/main.js in „demomain.js“.
1. Entfernen Sie in „demomain.js“ den Code zum Initialisieren des Routers und fügen Sie den folgenden Code hinzu:

   ```javascript
   require(['initializer','runtime/util/usersession'],
       function(initializer, UserSession) {
           UserSession.initialize(
               function() {
                   // Render all the global components
                   initializer.initGlobal();
               });
       });
   ```

1. Erstellen Sie einen Knoten unter „/content“ mit dem Namen `sampleApplication` und dem Typ `nt:unstructured`. Fügen Sie in den Eigenschaften dieses Knotens `sling:resourceType` vom Typ String und dem Wert `sampleApplication` hinzu. Fügen Sie der Zugriffsteuerungsliste dieses Knotens den Eintrag `PERM_WORKSPACE_USER` hinzu, um jcr:read-Zugriff zuzulassen. Fügen Sie außerdem in der Zugriffssteuerungsliste von `/apps/sampleApplication` einen Eintrag für `PERM_WORKSPACE_USER` hinzu, der „jcr:read privileges“ erlaubt.
1. Aktualisieren Sie in `/apps/sampleApplication/wscomponents/js/registry.js` die Pfade `/lc/libs/ws/` zu `/lc/apps/sampleApplication/wscomponents/` für die Vorlagenwerte.
1. Fügen Sie in die JSP-Datei Ihrer Portal-Startseite unter `/apps/sampleApplication/GET.jsp` den folgenden Code ein, um die erforderlichen Komponenten innerhalb des Portals aufzunehmen.

   ```jsp
   <script data-main="/lc/apps/sampleApplication/wscomponents/js/demomain" src="/lc/apps/sampleApplication/wscomponents/js/libs/require/require.js"></script>
   <div class="UserInfoView gcomponent" data-name="userinfo"></div>
   <div class="filterListView gcomponent" data-name="filterlist"></div>
   <div class="taskListView gcomponent" data-name="tasklist"></div>
   ```

   Schließen Sie auch die CSS-Dateien ein, die für die AEM Forms Workspace-Komponenten erforderlich sind.

   >[!NOTE]
   >
   >Jede Komponente wird beim Rendern zum Komponenten-Tag (mit Klasse „gcomponent“) hinzugefügt. Stellen Sie sicher, dass Ihre Startseite diese Tags enthält. Weitere Informationen zu diesen Basissteuerungstags finden Sie in der Datei von AEM Forms Workspace `html.jsp`.

1. Um die Komponenten anzupassen, können Sie die vorhandenen Ansichten für die erforderliche Komponente wie folgt erweitern:

   ```javascript
   define([
       'jquery',
       'underscore',
       'backbone',
       'runtime/views/userinfo'],
       function($, _, Backbone, UserInfo){
           var demoUserInfo = UserInfo.extend({
               //override the functions to customize the functionality
               render: function() {
                   UserInfo.prototype.render.call(this); // call the render function of the super class
                   …
                   //other tasks
                   …
               }
           });
           return demoUserInfo;
   });
   ```

1. Ändern Sie das Portal-CSS, um das Layout, die Positionierung und den Stil der erforderlichen Komponenten im Portal zu konfigurieren. Sie möchten beispielsweise die Hintergrundfarbe für dieses Portal schwarz halten, um die Komponente „userInfo“ gut sichtbar darzustellen. Sie können dies tun, indem Sie die Hintergrundfarbe in `/apps/sampleApplication/wscomponents/css/style.css` wie folgt ändern:

   ```css
   body {
       font-family: "Myriad pro", Arial;
       background: #000;    //This was origianlly #CCC
       position: relative;
       margin: 0 auto;
   }
   ```
