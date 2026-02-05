---
title: Integration der Lösung „Korrespondenz erstellen“ in das benutzerdefinierte Portal
description: Erfahren Sie, wie Sie die Benutzeroberfläche „Korrespondenz erstellen“ in Ihr benutzerdefiniertes Portal integrieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: 496b125b-b091-4843-ba9f-2479dbeba07b
source-git-commit: 16f57ae1663f035d1dc39005d37426c7a0d8dc16
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 46%

---

# Integration der `Create Correspondence` Lösung in Ihr benutzerdefiniertes Portal{#integrating-create-correspondence-ui-with-your-custom-portal}

## Übersicht {#overview}

In diesem Artikel wird beschrieben, wie Sie die `Create Correspondence` Lösung in Ihre Umgebung integrieren können.

## URL-basierter Aufruf {#url-based-invocation}

Eine Möglichkeit, die `Create Correspondence`-Anwendung über ein benutzerdefiniertes Portal aufzurufen, besteht darin, die URL mit den folgenden Anfrageparametern vorzubereiten:

* die Kennung für die Briefvorlage (mithilfe des cmLetterId-Parameters).

* die URL für die XML-Datei, die aus der gewünschten Datenquelle (unter Verwendung des cmDataUrl-Parameters) erfasst wurde

Beispielsweise würde das benutzerdefinierte Portal die URL als\
`https://'[server]:[port]'/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]` vorbereiten, wobei es sich um die href eines Links auf dem Portal handeln könnte.

>[!NOTE]
>
>Den Aufruf auf diese Weise durchzuführen, ist nicht sicher, da die erforderlichen Parameter als GET-Anfrage übergeben werden, indem dieselben (eindeutig sichtbaren) Parameter in der URL offengelegt werden.

>[!NOTE]
>
>Speichern und laden Sie vor dem Aufruf der `Create Correspondence`-Anwendung die Daten, um die `Create Correspondence`-Benutzeroberfläche unter der angegebenen dataURL aufzurufen. Dieser Prozess kann entweder über das benutzerdefinierte Portal selbst oder über einen anderen Back-End-Prozess erfolgen.

## Auf Daten basierter Inline-Aufruf {#inline-data-based-invocation}

Eine weitere, sicherere Möglichkeit, die `Create Correspondence`-Anwendung aufzurufen, besteht darin, zur URL https://&#39;[server]:[port]&#39;/[contextPath]/aem/forms/createcorrespondence.html zu gehen. Führen Sie diese URL aus, während Sie die Parameter und Daten senden, um die `Create Correspondence`-Anwendung als POST-Anfrage aufzurufen, wodurch sie vor dem Endbenutzer versteckt werden. Dieser Workflow bedeutet auch, dass Sie jetzt die XML-Daten für die `Create Correspondence`-Anwendung inline übergeben können (als Teil derselben Anfrage, unter Verwendung des `cmData`-Parameters). Dieser Workflow war beim vorherigen Ansatz nicht möglich oder ideal.

### Parameter für das Festlegen des Briefs {#parameters-for-specifying-letter}

| **Name** | **Typ** | **Beschreibung** |
| --- | --- | --- |
| cmLetterInstanceId | Zeichenfolge | Der Bezeichner für die Briefinstanz. |
| cmLetterId | Zeichenfolge | Der Name der Briefvorlage. |

Die Reihenfolge der Parameter in der Tabelle gibt die Voreinstellungen von Parametern an, die zum Laden des Briefs verwendet werden.

### Parameter für die Angabe der XML-Datenquelle {#parameters-for-specifying-the-xml-data-source}

<table>
 <tbody>
  <tr>
   <td><strong>Name</strong></td> 
   <td><strong>Typ</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr>
  <tr>
   <td>cmDataUrl<br /> </td> 
   <td>URL</td> 
   <td>XML-Daten aus einer Quelldatei unter Verwendung grundlegender Protokolle wie cq, ftp, http oder file.<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Zeichenfolge</td> 
   <td>Verwenden von in der Briefinstanz verfügbaren XML-Daten.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Boolesch</td> 
   <td>So verwenden Sie die an ein Datenwörterbuch angehängten Testdaten erneut.</td> 
  </tr>
 </tbody>
</table>

Die Reihenfolge der Parameter in der Tabelle gibt die Voreinstellungen von Parametern an, die zum Laden der XML-Daten verwendet werden.

### Andere Parameter {#other-parameters}

<table>
 <tbody>
  <tr>
   <td><strong>Name</strong></td> 
   <td><strong>Typ</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr>
  <tr>
   <td>cmPreview<br /> </td> 
   <td>Boolesch</td> 
   <td>„True“, um den Brief im Vorschaumodus zu öffnen.<br /> </td> 
  </tr>
  <tr>
   <td>Willkürlich</td> 
   <td>Zeitstempel</td> 
   <td>Um die Probleme mit dem Browser-Caching zu lösen.</td> 
  </tr>
 </tbody>
</table>

Wenn Sie das HTTP- oder CQ-Protokoll für die `cmDataURL` verwenden, muss die URL von `http/cq` anonym zugänglich sein.
