---
title: Anpassen der Auflistung von Prozessinstanzen
description: Erfahren Sie, wie Sie die Eigenschaften anpassen, die in der Prozessinstanz in AEM Forms Workspace angezeigt werden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 7ffde604-2f56-4b53-88ab-5fac321e4753
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 100%

---

# Anpassen der Auflistung von Prozessinstanzen {#customizing-the-listing-of-process-instances}

Die Prozessinstanzliste wird auf der Registerkarte „Tracking“ von AEM Forms Workspace angezeigt.

In der Prozessinstanzliste zeigt AEM Forms Workspace für jede Prozessinstanz einige Eigenschaften dieser Instanz. Die folgenden Eigenschaften sind für jede Prozessinstanz verfügbar. Diese Eigenschaften werden als Attribute im Prozessinstanz-Komponentenmodell gespeichert und sind in dessen Ansicht und Vorlage verfügbar.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td>description</td>
   <td>Beschreibung der Prozessinstanz.</td>
  </tr>
  <tr>
   <td>initiator</td>
   <td>Name der Initiatorin bzw. des Initiators der Prozessinstanz.</td>
  </tr>
  <tr>
   <td>initiatorId</td>
   <td>ID der Initiatorin bzw. des Initiators der Prozessinstanz.</td>
  </tr>
  <tr>
   <td>processCompleteTime</td>
   <td>Zeitstempel zum Zeitpunkt, zu dem der Prozess abgeschlossen wurde.</td>
  </tr>
  <tr>
   <td>processInstanceId</td>
   <td>ID der Prozessinstanz.</td>
  </tr>
  <tr>
   <td>processInstanceStatus</td>
   <td>0 = Initiiert<br /> 1 = Wird ausgeführt<br /> 2 = Abgeschlossen<br /> 3 = Wird abgeschlossen<br />4 = Beendet<br /> 5 = Wird beendet<br /> 6 = Ausgesetzt<br /> 7 = Wird ausgesetzt<br /> 8 = Aussetzen wird aufgehoben</td>
  </tr>
  <tr>
   <td>processName</td>
   <td>Name des Prozesses.</td>
  </tr>
  <tr>
   <td>processStartTime</td>
   <td>Zeitstempel zum Zeitpunkt, als der Prozess gestartet wurde.</td>
  </tr>
  <tr>
   <td>processVariables</td>
   <td>Array von Objekten aus Prozessvariablen. Jedes Objekt einer Prozessvariable enthält <strong>name</strong> (den Namen der Prozessvariable), <strong>value</strong> (den Wert der Prozessvariable) und <strong>type</strong> (den Typ der Prozessvariable).</td>
  </tr>
 </tbody>
</table>

**Beispiel:**

Um die Eigenschaft `description` der Prozessinstanz auf der Prozessinstanzkarte anzuzeigen, führen Sie die folgenden Schritte aus.

1. Befolgen Sie die [generischen Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Gehen Sie folgendermaßen vor:

   1. Kopieren Sie /libs/ws/js/runtime/templates/processinstance.html nach /apps/ws/js/runtime/templates/, wenn es nicht existiert. Klicken Sie auf **Alle speichern**.
   1. Fügen Sie die Prozessbeschreibung div mit class = „processDescription“ in processinstance.html hinzu.

   ```jsp
   <div class="processDescription" title="<%= description%>"><%= description%></div>
   ```

1. Gehen Sie folgendermaßen vor:

   1. Öffnen Sie /apps/ws/js/registry.js zur Bearbeitung.
   1. Suchen und Ersetzen `text!/lc/libs/ws/js/runtime/templates/processinstance.html`mit `text!/lc/`**apps**/ws/js/runtime/templates/processinstance.html

1. Die oben genannten Änderungen erfordern möglicherweise ein Update der CSS-Datei, indem Sie wie folgt einen Eintrag im Stylesheet /apps/ws/css/newStyle.css hinzufügen:

   ```css
   .processinstance .processDescription {
    <!--Dummy values, need to be configured by user as per requirement and user can add or delete any property depending upon requirement-->
       width : 250px;
       font-size : 11pt;
       padding : 2px;
   }
   ```
