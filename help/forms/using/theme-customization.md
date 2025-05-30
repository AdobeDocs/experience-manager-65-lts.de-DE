---
title: Anpassung des Designs
description: Erfahren Sie, wie Sie das Design der AEM Forms-Anwendung anpassen können. Sie können den HTML-Code und die CSS-Datei anpassen, um ein organisationsspezifisches Look-and-Feel zu ermöglichen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 5765b456-c6e8-4498-ade0-b36c95aadd71
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 100%

---

# Design-Anpassung {#theme-customization}

Sie können den HTML-Code und die CSS-Datei anpassen, um der AEM Forms-App ein unverwechselbares, organisationsspezifisches Erscheinungsbild zu geben. Sie können beispielsweise die Hintergrundfarbe und die Höhe von Aufgaben oder Startpunkten ändern. Das folgende Beispiel enthält hierzu Anweisungen:

* Anweisungen statt Beschreibungen anzeigen
* Anzahl der Anzeigewege
* Hintergrundverlaufsfarbe

## Schritte {#steps}

1. Öffnen Sie Ihr Projekt.

   * In iOS öffnen Sie `Capture.xcodeproj` in Xcode
   * In Android öffnen Sie das Android-Projekt in Eclipse.
   * In Windows öffnen Sie `MWSWindows.sln` in Visual Studio.

1. Navigieren Sie zum Ordner „templates“.

   * In Xcode navigieren Sie zum Ordner **Capture > www > wsmobile > js > runtime > templates**.
   * In Eclipse navigieren Sie zum Ordner **assets > www > wsmobile > js > runtime > templates**.
   * In Visual Studio navigieren Sie zum Ordner **MWSWindows > www > wsmobile > js > runtime > templates**.

1. Öffnen Sie die Datei „`template.html`“, um sie zu bearbeiten.
1. Suchen Sie die folgende Zeichenfolge:

   ```jsp
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else
   ```

   Ersetzen Sie sie durch `<%`.

1. Suchen Sie den folgenden Code in der Datei `template.html`:

   ```jsp
   <ul id="task_menu_list">
                                   <li class="approve" title="<%= task.availableCommands.directCommands[0]%>" data-routename="<%= task.availableCommands.directCommands[0]%>">
                                       <%= task.availableCommands.directCommands[0]%>
                                   </li>
                                   <li class="reject last" title="<%= task.availableCommands.directCommands[1]%>" data-routename="<%= task.availableCommands.directCommands[1]%>">
                                       <%= task.availableCommands.directCommands[1]%>
                                   </li>
   ```

1. Geben Sie die folgende Zeile ein und speichern Sie die Datei.

   ```jsp
   task.availableCommands.directCommands[1]%>">
   <%= task.availableCommands.directCommands[1]%>
   </li>
   ```

1. Navigieren Sie zum Ordner „css“.

   * In Xcode navigieren Sie zu **Capture > www > wsmobile > css**.
   * In Eclipse navigieren Sie zu **assets > www > wsmobile > css**.
   * In Visual Studio navigieren Sie zu **MWSWindows > www > wsmobile > css**.

1. Öffnen Sie die Datei „`_style.css`“, um sie zu bearbeiten.
1. Ändern Sie für das Hintergrundbild `#323232` auf `#fff`.
1. Speichern Sie die Änderungen und schließen Sie die Datei `_style.css`.
1. Öffnen Sie die AEM Forms-App.

   Die AEM Forms-App zeigt jetzt Anweisungen anstelle einer Beschreibung an.
