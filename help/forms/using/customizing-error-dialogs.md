---
title: Anpassen von Fehlerdialogen
description: Gehen Sie wie folgt vor, um durch Anpassen der Fehlerdialoge von LiveCycle AEM Forms verschiedene Fehlerbeschreibungen hinzuzufügen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 26ae8e19-e998-4c81-a2ec-b25ce94496a4
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 100%

---

# Anpassen von Fehlerdialogen {#customizing-error-dialogs}

AEM Forms Workspace ermöglicht Ihnen, Fehlerdialoge anzupassen. Führen Sie [Generische Schritte zur Anpassung von AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md) durch und anschließend die unten aufgeführten Schritte zum Anpassen von Fehlerdialogen.

## Text anpassen {#customizing-text}

1. Ändern Sie in der Datei `/apps/ws/locales/en-US/translation.json` die Werte von `wserror` auf die benutzerdefinierten Werte. Beispiel:

   ```json
   "wserror" : {
    "message" : "Message:",
    "ComponentUI" : "Component UI:",
    "error" : "Error",
    "ok" : "Ok",
    "ErrorCode" : "Error Code:"
    }
   ```

   To

   ```json
    "wserror" : {
    "message" : "Error Message:",
    "ComponentUI" : "UI Component:",
    "error" : "Something went wrong!!",
    "ok" : "Ok",
    "ErrorCode" : "Error Code:"
    }
   ```

   >[!NOTE]
   >
   >Fügen Sie entsprechende Schlüssel-Wert-Paare für alle unterstützten Sprachen hinzu.

## Anpassen des CSS {#customizing-css}

1. Sie können Dialogfeld, Kopfzeile, Inhaltsbereich, Fußleiste, Fußleisten-Buttons und andere Zusätze ändern, indem Sie das folgende Snippet in der Datei `/apps/ws/css/newStyle.css` hinzufügen:

   ```css
   /*-------- Error Dialog -------------------------------------------------------------------------------------------------------------------*/
   .error-dialog{
       border: 2px solid #DEDEDE;
       width: 540px;
       height: 400px;
       position: absolute;
       z-index: 99999;
       left: 50%;
       margin-left: -271px;
       background:#2b2b2b;
       box-shadow:0px 0px 10px 3px #888;
       display:none;
   }
   .error-dialog .head-bar{
       height: 31px;
       background: url(../images/error.png) no-repeat 7px 10px #DEDEDE;
       color: #2B2B2B;
       font-size: 18px;
       padding-left: 30px;
       padding-top: 7px;
       text-overflow: ellipsis;
       overflow: hidden;
       white-space: nowrap;
   }
   .error-dialog .content-area{
       padding: 20px;
       border-bottom: 1px solid #1B1B1B;
       height: 268px;
   }
   .error-dialog .foot-bar{
       border-top: 1px solid #404040;
       height: 32px;
       padding:10px;
       text-align: right;
   }
   .error-dialog .foot-bar button{
       background: #52a1dc; /* Old browsers */
       background: -moz-linear-gradient(top,  #52a1dc 0%, #2680ce 100%, #207cca 100%, #2989d8 100%, #207cca 100%); /* FF3.6+ */
       background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,#52a1dc), color-stop(100%,#2680ce), color-stop(100%,#207cca), color-stop(100%,#2989d8), color-stop(100%,#207cca)); /* Chrome,Safari4+ */
       background: -webkit-linear-gradient(top,  #52a1dc 0%,#2680ce 100%,#207cca 100%,#2989d8 100%,#207cca 100%); /* Chrome10+,Safari5.1+ */
       background: -o-linear-gradient(top,  #52a1dc 0%,#2680ce 100%,#207cca 100%,#2989d8 100%,#207cca 100%); /* Opera 11.10+ */
       background: -ms-linear-gradient(top,  #52a1dc 0%,#2680ce 100%,#207cca 100%,#2989d8 100%,#207cca 100%); /* IE10+ */
       background: linear-gradient(to bottom,  #52a1dc 0%,#2680ce 100%,#207cca 100%,#2989d8 100%,#207cca 100%); /* W3C */
       filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#52a1dc', endColorstr='#2680ce',GradientType=0 ); /* IE6-9 */
       border: #4F748F;
       height: 30px;
       width: 100px;
       font-size: 18px;
       color: white;
   
   }
   .error-dialog .single-col{
       width: 100%;
       list-style-type: none;
       padding: 0px;
       margin: 0px;
   }
   .error-dialog .single-col li{
       height: 28px;
       font-size:14px;
       color:#bebebe;
       text-overflow: ellipsis;
       overflow: hidden;
       white-space: nowrap;
   }
   .error-dialog .single-col li label{
       height: 28px;
       color:#fff;
       max-width:100px;
       margin-right: 14px;
       text-overflow: ellipsis;
       overflow: hidden;
       white-space: nowrap;
       float: left;
   }
   .error-dialog .double-col{
       width: 100%;
       list-style-type: none;
       padding: 0px;
       margin:0px;
   }
   .error-dialog .double-col li{
       height: 28px;
       font-size:14px;
       color:#bebebe;
       width: 50%;
       float: left;
       text-overflow: ellipsis;
       white-space: nowrap;
       overflow: hidden;
   }
   .error-dialog .double-col li.small{
       width: 30%;
   }
   .error-dialog .double-col li.big{
       width: 70%;
   }
   .error-dialog .double-col li label{
       height: 28px;
       color:#fff;
       max-width:100px;
       margin-right: 14px;
       text-overflow: ellipsis;
       overflow: hidden;
       white-space: nowrap;
       float: left;
   }
   .error-dialog .scroll-content{
       color:#bebebe;
       font-size:12px;
       height:175px;
       overflow-y:scroll;
       overflow-x:hidden;
       width:100%;
   
   }
   
   .error-background, .popup-background, .wsMessageBackGround, .userInfoBackGround, .busyState, .aboutWorkspaceBG {
       width: 100%;
       height: 100%;
       display: none;
       opacity: 0.6;
       background-color: black;
       left: 0px;
       top: 0px;
       position: fixed;
       z-index: 999;
       margin: 0px;
       padding: 0px;
   }
   ```

1. Für den Bereich mit den Fußleisten-Buttons trennen Sie die Button-Bereiche `.error-dialog` und `.foot-bar` von der Composite-Liste. Um diese Änderung vorzunehmen, fügen Sie der Datei „newStyle.css“ Folgendes hinzu:

   ```css
   .browse-btn span, .attachementbtn span, .cancelAttachmentUpdate span, #taskAttachmentsContainer .uploadStatus span, .submitNoteButton span, .updateNoteButton span, .cancelNoteUpdate span,
   #userSearchPopUp #actionbar span, #taskarea .action button span, .error-dialog .foot-bar button span, .oooAction button span, .wsMessageContainerDiv .action button span
   {
       display: block;
       text-overflow: ellipsis;
       white-space: nowrap;
       overflow: hidden;
   }
   ```

   To

   ```css
   .browse-btn span, .attachementbtn span, .cancelAttachmentUpdate span, #taskAttachmentsContainer .uploadStatus span, .submitNoteButton span, .updateNoteButton span, .cancelNoteUpdate span,
   #userSearchPopUp #actionbar span, #taskarea .action button span, .oooAction button span, .wsMessageContainerDiv .action button span
   {
       display: block;
       text-overflow: ellipsis;
       white-space: nowrap;
       overflow: hidden;
   }
   
   /*-------- Customized following Portion --------*/
   .error-dialog .foot-bar button span
   {
       display: block;
       text-overflow: ellipsis;
       text-decoration:underline;
       white-space: wrap;
   }
   ```

>[!NOTE]
>
>Wenn Sie auf weitere Bilder verweisen, fügen Sie sie in der gewünschten Hierarchie unter `/apps/ws/images` hinzu.

## Beispiele {#examples}

* **Um den Fehlerdialog anzupassen, ändern Sie:**

```css
.error-dialog{
    border: 2px solid #DEDEDE;
    width: 540px;
    height: 400px;
    position: absolute;
    z-index: 99999;
    left: 50%;
    margin-left: -271px;
    background:#2b2b2b;
    box-shadow:0px 0px 10px 3px #888;
    display:none;
}
```

To

```css
.error-dialog{
    border: 9px solid #DEDEDE;
    width: 200px;
    height: 200px;
    position: absolute;
    z-index: 99999;
    left: 50%;
    margin-left: -271px;
    background: url(../images/my-error-bg.png) no-repeat 7px 10px #DEDEDE;
    box-shadow:0px 0px 10px 3px #888;
    display:none;
}
```

* **Um die Fehlerdialog-Kopfzeile anzupassen, ändern Sie:**

```css
.error-dialog .head-bar{
    height: 31px;
    background: url(../images/error.png) no-repeat 7px 10px #DEDEDE;
    color: #2B2B2B;
    font-size: 18px;
    padding-left: 30px;
    padding-top: 7px;
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;
}
```

To

```css
.error-dialog .head-bar{
    height: 40px;
    background: url(../images/error.png) no-repeat 7px 10px #DEDEDE;
    color: #FA0E39;
    font-size: 18px;
    padding-left: 30px;
    padding-top: 15px;
}
```
