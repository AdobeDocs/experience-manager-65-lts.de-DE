---
title: Ändern der Schriftart auf der Benutzeroberfläche
description: Selektives Ändern der Schriftarten auf der Benutzeroberfläche.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: e27ff9df-41d0-4eef-b04e-a3eefea3c9ab
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 100%

---

# Ändern der Schriftart auf der Benutzeroberfläche{#changing-the-font-on-the-interface}

Sie können die Schriftart ändern, die in AEM Forms Workspace angezeigt wird.  Schriftarten, die in einem bestimmten Bereich der Benutzeroberfläche verwendet werden, werden im entsprechenden Abschnitt des Stylesheets definiert.  Sie können die Schriftarten auf der Benutzeroberfläche selektiv ändern.

Führen Sie die Anweisungen unter [Generische Schritte zur Anpassung von AEM Forms Workspace](../../forms/using/generic-steps-html-workspace-customization.md) aus. Befolgen Sie bei Bedarf außerdem die Schritte zum Anpassen von CSS, HTML oder beidem.

1. Ändern Sie die Schriftfamilie in einem vorhandenen Stil oder fügen Sie sie hinzu.
1. Ändern Sie die Schriftfamilie inline für das HTML-Element oder fügen Sie sie hinzu.
1. Fügen Sie einen Stil hinzu und verwenden Sie ihn für das HTML-Element.

Um beispielsweise die Schriftart für den Anker-Text in der Navigationsleiste oben in Courier New zu ändern, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei CRXDE Lite an, indem Sie auf `https://'[server]:[port]'/lc/crx/de/index.jsp` zugreifen.
1. Führen Sie einen der folgenden Schritte aus:

   1. Um die Schriftfamilie in einem vorhandenen Stil zu ändern, fügen Sie Folgendes in der Datei „newStyle.css“ bei „/apps/ws/css“ hinzu.

      ```css
      #topnav a {
         font-family: "Courier New";
      }
      ```

   1. Um die Schriftfamilie für das HTML-Element inline hinzuzufügen, kopieren Sie die Datei `/libs/ws/js/runtime/templates/appnavigation.html` nach`/apps/ws/js/runtime/templates/appnavigation.html`.

      aktualisieren Sie die Datei „/apps/ws/js/runtime/templates/appnavigation.html“ wie folgt:

      ```jsp
      <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
      <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.todo.name')%></a></li>
      <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
      <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
      ```

      Öffnen Sie die Datei „/apps/ws/js/registry.js“ zur Bearbeitung und ersetzen Sie `text!/lc/libs/ws/js/runtime/templates/appnavigation.html` durch `text!/lc/apps/ws/js/runtime/templates/appnavigation.html`.

   1. Um einen Stil hinzuzufügen, der die Schriftfamilie definiert, fügen Sie Folgendes in der Datei „newStyle.css“ bei „/apps/ws/css“ hinzu.

      ```css
      .myNewFontStyle a {
         font-family: "Courier New";
      }
      ```

      Um die Schriftfamilie für das HTML-Element inline hinzuzufügen, fügen Sie Folgendes in der Datei „appnavigation.html“ bei „/apps/ws/js/runtime/templates“ hinzu.

      ```jsp
      <div id="topnav" class="myNewFontStyle">
          <ul>
              <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
              <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>"><%= $.t('index.header.topnav.todo.name')%></a></li>
              <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
              <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
          </ul>
      </div>
      ```

1. Starten Sie Workspace neu und löschen Sie den Browsercache, damit die Änderungen sichtbar werden.

![change_font_before](assets/change_font_before.png)

Obere Navigationsleiste vor Schriftartanpassung

![change_font_after](assets/change_font_after.png)

Obere Navigationsleiste nach der Schriftartanpassung
