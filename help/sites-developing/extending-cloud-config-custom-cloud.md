---
title: Erstellen eines individuellen Cloud-Services
description: Die standardmäßigen Cloud-Services können durch benutzerdefinierte Cloud-Service-Typen erweitert werden
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 7ae41982-8438-41a6-91f9-3b3b6755a39b
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 100%

---

# Erstellen eines individuellen Cloud-Services{#creating-a-custom-cloud-service}

Die standardmäßigen Cloud-Services können durch benutzerdefinierte Cloud-Service-Typen erweitert werden. So können Sie auf strukturierte Weise benutzerdefiniertes Markup in die Seite einfügen. Dies ist hauptsächlich für externe Analyseanbieter hilfreich, z. B. Google Analytics, Chartbeat usw. Cloud-Services werden von übergeordneten Seiten auf untergeordnete Seiten übernommen. Dabei kann die Übernahme auf einer beliebigen Ebene unterbrochen werden.

>[!NOTE]
>
>In dieser Schritt-für-Schritt-Anleitung zum Erstellen eines Cloud-Service wird Google Analytics als Beispiel verwendet. Einiges trifft auf Ihren Anwendungsfall möglicherweise nicht zu.

1. Erstellen Sie in CRXDE Lite einen Knoten unter `/apps`:

   * **Name**: `acs`
   * **Typ**: `nt:folder`

1. Erstellen Sie einen Knoten unter `/apps/acs`:

   * **Name**: `analytics`
   * **Typ**: `sling:Folder`

1. Erstellen Sie zwei Knoten unter `/apps/acs/analytics`:

   * **Name**: components
   * **Typ**: `sling:Folder`

   und

   * **Name**: templates
   * **Typ**: `sling:Folder`

1. Klicken Sie mit der rechten Maustaste auf `/apps/acs/analytics/components`. Wählen Sie **Erstellen…** und dann **Komponente erstellen…** aus. Im Dialogfeld, das sich öffnet, können Sie Folgendes angeben:

   * **Bezeichnung**: `googleanalyticspage`
   * **Titel**: `Google Analytics Page`
   * **Supertyp**: `cq/cloudserviceconfigs/components/configpage`
   * **Gruppe**: `.hidden`

1. Klicken Sie zweimal auf **Weiter** und geben Sie Folgendes an:

   * **Zugelassene übergeordnete Elemente:** `acs/analytics/templates/googleanalytics`

   Klicken Sie zweimal auf **Weiter** und anschließend auf **OK**.

1. Fügen Sie `googleanalyticspage` eine Eigenschaft hinzu:

   * **Name:** `cq:defaultView`
   * **Wert:** `html`

1. Erstellen Sie unter `/apps/acs/analytics/components/googleanalyticspage` eine Datei mit dem Namen `content.jsp` und dem folgenden Inhalt:

   ```xml
   <%@page contentType="text/html"
               pageEncoding="utf-8"%><%
   %><%@include file="/libs/foundation/global.jsp"%><div>
   
   <div>
       <h3>Google Analytics Settings</h3>
       <ul>
           <li><div class="li-bullet"><strong>accountID: </strong><br><%= xssAPI.encodeForHTML(properties.get("accountID", "")) %></div></li>
       </ul>
   </div>
   ```

1. Erstellen Sie einen Knoten unter `/apps/acs/analytics/components/googleanalyticspage/`:

   * **Name**: `dialog`
   * **Typ**: `cq:Dialog`
   * **Eigenschaften**:

      * **Name**: `title`
      * **Typ**: `String`
      * **Wert**: `Google Analytics Config`
      * **Name**: `xtype`
      * **Typ**: `String`
      * **Wert**: `dialog`

1. Erstellen Sie einen Knoten unter `/apps/acs/analytics/components/googleanalyticspage/dialog`:

   * **Name**: `items`
   * **Typ**: `cq:Widget`
   * **Eigenschaften**:

      * **Name**: `xtype`
      * **Typ**: `String`
      * **Wert**: `tabpanel`

1. Erstellen Sie einen Knoten unter `/apps/acs/analytics/components/googleanalyticspage/dialog/items`:

   * **Name**: `items`
   * **Typ**: `cq:WidgetCollection`

1. Erstellen Sie einen Knoten unter `/apps/acs/analytics/components/googleanalyticspage/dialog/items/items`:

   * **Name**: tab1
   * **Typ**: `cq:Panel`
   * **Eigenschaften**:

      * **Name**: `title`
      * **Typ**: `String`
      * **Wert**: `Config`

1. Erstellen Sie einen Knoten unter `/apps/acs/analytics/components/googleanalyticspage/dialog/items/items/tab1`:

   * **Name**: items
   * **Typ**: `nt:unstructured`
   * **Eigenschaften**:

      * **Name**: `fieldLabel`
      * **Typ**: Zeichenfolge
      * **Wert**: Konto-ID

      * **Name**: `fieldDescription`
      * **Typ**: `String`
      * **Wert**: `The account ID assigned by Google. Usually in the form UA-NNNNNN-N`

      * **Name**: `name`
      * **Typ**: `String`
      * **Wert**: `./accountID`
      * **Name**: `validateOnBlur`
      * **Typ**: `String`
      * **Wert**: `true`
      * **Name**: `xtype`
      * **Typ**: `String`
      * **Wert**: `textfield`

1. Kopieren Sie `/libs/cq/cloudserviceconfigs/components/configpage/body.jsp` nach `/apps/acs/analytics/components/googleanalyticspage/body.jsp`, ändern Sie `libs` in Zeile 34 in `apps` und ändern Sie die Skriptreferenz in Zeile 79 in einen vollständig qualifizierten Pfad.
1. Erstellen Sie eine Vorlage unter `/apps/acs/analytics/templates/`:

   * **Ressourcentyp** = `acs/analytics/components/googleanalyticspage`
   * **Titel** = `googleanalytics`
   * **Titel**= `Google Analytics Configuration`
   * **allowedPath** = `/etc/cloudservices/googleanalytics(/.*)?`
   * **allowedChildren** = `/apps/acs/analytics/templates/googleanalytics`
   * **sling:resourceSuperType** = `cq/cloudserviceconfigs/templates/configpage` (im Vorlagenknoten, nicht im jcr:content-Knoten)
   * **cq:designPath** = `/etc/designs/cloudservices/googleanalytics` (in jcr:content)

1. Erstellen Sie eine Komponente: `/apps/acs/analytics/components/googleanalytics`.

   Fügen Sie den folgenden Inhalt zu `googleanalytics.jsp` hinzu:

   ```xml
   <%@page import="org.apache.sling.api.resource.Resource,
                   org.apache.sling.api.resource.ValueMap,
                   org.apache.sling.api.resource.ResourceUtil,
                   com.day.cq.wcm.webservicesupport.Configuration,
                   com.day.cq.wcm.webservicesupport.ConfigurationManager" %>
   <%@include file="/libs/foundation/global.jsp" %><%
   
   String[] services = pageProperties.getInherited("cq:cloudserviceconfigs", new String[]{});
   ConfigurationManager cfgMgr = resource.getResourceResolver().adaptTo(ConfigurationManager.class);
   if(cfgMgr != null) {
       String accountID = null;
       Configuration cfg = cfgMgr.getConfiguration("googleanalytics", services);
       if(cfg != null) {
           accountID = cfg.get("accountID", null);
       }
   
       if(accountID != null) {
       %>
   <script type="text/javascript">
   
     var _gaq = _gaq || [];
     _gaq.push(['_setAccount', '<%= accountID %>']);
     _gaq.push(['_trackPageview']);
   
     (function() {
       var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
       ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'https://www') + '.google-analytics.com/ga.js';
       var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
     })();
   
   </script><%
       }
   }
   %>
   ```

   Dadurch sollte das benutzerdefinierte Markup basierend auf den Konfigurationseigenschaften ausgegeben werden.

1. Navigieren Sie zu `http://localhost:4502/miscadmin#/etc/cloudservices` und erstellen Sie eine Seite:

   * **Titel**: `Google Analytics`
   * **Name**: `googleanalytics`

   Gehen Sie in CRXDE Lite zurück und fügen Sie unter `/etc/cloudservices/googleanalytics` folgende Eigenschaft zu `jcr:content` hinzu:

   * **Name**: `componentReference`
   * **Typ**: `String`
   * **Wert**: `acs/analytics/components/googleanalytics`

1. Navigieren Sie zu der neu erstellten Service-Seite (`http://localhost:4502/etc/cloudservices/googleanalytics.html`) und klicken Sie auf **+**, um eine Konfiguration zu erstellen:

   * **Übergeordnete Konfiguration**: `/etc/cloudservices/googleanalytics`
   * **Titel:**  `My First GA Config`

   Wählen Sie **Google Analytics Configuration** und klicken Sie auf **Erstellen**.

1. Geben Sie eine **Konto-ID** ein, z. B. `AA-11111111-1`. Klicken Sie auf **OK**.
1. Navigieren Sie zu einer Seite und fügen Sie die neu erstellte Konfiguration in den Seiteneigenschaften unter der Registerkarte **Cloud-Services** hinzu.
1. Das benutzerdefinierte Markup wird der Seite hinzugefügt.
