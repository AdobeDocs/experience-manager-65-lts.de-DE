---
title: Experience Fragments in der Adobe Experience Manager Sites-Entwicklung
description: Erfahren Sie, wie Sie Experience Fragments für Adobe Experience Manager konfigurieren.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: bc621086-8128-4836-a580-dca99f61c439
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1786'
ht-degree: 100%

---

# Experience Fragments {#experience-fragments}

## Grundlagen {#the-basics}

Ein [Experience Fragment](/help/sites-authoring/experience-fragments.md) ist eine Gruppe aus einer oder mehreren Komponenten (einschließlich Inhalt und Layout), die innerhalb von Seiten referenziert werden können.

Ein primäres Experience Fragment und/oder eine Experience Fragment-Variante verwendet:

* `sling:resourceType`: `/libs/cq/experience-fragments/components/xfpage`

Da es kein `/libs/cq/experience-fragments/components/xfpage/xfpage.html` gibt, wird auf Folgendes zurückgegriffen:

* `sling:resourceSuperType`: `wcm/foundation/components/page`

## Einfache HTML-Ausgabedarstellung {#the-plain-html-rendition}

Mit dem `.plain.`-Selektor in der URL können Sie auf die einfache HTML-Ausgabe zugreifen.

Diese ist über den Browser verfügbar, aber ihr Hauptzweck besteht darin, anderen Anwendungen (beispielsweise Web-Anwendungen von Drittanbietern oder benutzerdefinierten mobilen Implementierungen) direkten Zugriff auf den Experience Fragment-Inhalt zu ermöglichen, und zwar allein über die URL.

Bei der einfachen HTML-Ausgabedarstellung werden das Protokoll, der Host und der Kontextpfad zu Pfaden hinzugefügt, die:

* den folgenden Typ aufweisen: `src`, `href` oder `action`

* oder folgendermaßen enden: `-src` oder `-href`

Zum Beispiel:

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>Links verweisen immer auf die Publishing-Instanz. Sie werden von Dritten verwendet, weswegen der Link immer von der Veröffentlichungsinstanz und nicht von der Autoreninstanz aufgerufen wird.
>
>Weitere Informationen finden Sie unter [Externalisieren von URLs](/help/sites-developing/externalizer.md).

![xf-14](assets/xf-14.png)

Der Selektor für die einfache Ausgabe verwendet einen Transformator im Gegensatz zu zusätzlichen Skripten. Der [Sling Rewriter](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) wird als Transformator verwendet. Dies wird hier konfiguriert

* `/libs/experience-fragments/config/rewriter/experiencefragments`

### Konfigurieren der HTML-Ausgabegenerierung {#configuring-html-rendition-generation}

Die HTML-Ausgabedarstellung wird mit den Sling Rewriter Pipelines erstellt. Die Pipeline ist unter `/libs/experience-fragments/config/rewriter/experiencefragments` definiert. Der HTML-Transformer unterstützt die folgenden Optionen:

* `allowedCssClasses`
   * Ein RegEx-Ausdruck, der den CSS-Klassen entspricht, die in der endgültigen Wiedergabe belassen werden sollen.
   * Dies ist nützlich, wenn kundenseitig einige bestimmte CSS-Klassen entfernt werden sollen.
* `allowedTags`
   * Eine Liste der HTML-Tags, die in der endgültigen Ausgabedarstellung zulässig sein sollen.
   * Standardmäßig sind die folgenden Tags zulässig (keine Konfiguration erforderlich): html, head, title, body, img, p, span, ul, li, a, b, i, em, strong, h1, h2, h3, h4, h5, h6, br, noscript, div, link und script

Es wird empfohlen, den Rewriter mit einer Überlagerung zu konfigurieren. Siehe [Überlagerungen](/help/sites-developing/overlays.md)

## Social-Varianten {#social-variations}

Social-Varianten können in Social Media (Text und Bild) veröffentlicht werden. In Adobe Experience Manager (AEM) können diese Social-Varianten Komponenten enthalten, z. B. Text- oder Bildkomponenten.

Das Bild und der Text für den Social-Beitrag können aus jedem beliebigen Bild- oder Textressourcentyp in beliebiger Tiefe entnommen werden (entweder im Baustein oder im Layout-Container).

Social-Varianten erlauben auch Bausteine und berücksichtigen sie bei Social-Aktionen (in der Veröffentlichungsumgebung).

Um den richtigen Text und das richtige Bild im Social Media-Netzwerk zu veröffentlichen, müssen einige Konventionen beachtet werden, wenn Sie eigene benutzerdefinierte Komponenten entwickeln.

Dazu müssen die folgenden Eigenschaften verwendet werden:

* Zur Extraktion des Bildes

   * `fileReference`
   * `fileName`

* Zur Extraktion des Texts

   * `text`

Komponenten, die diese Konvention nicht verwenden, werden nicht berücksichtigt.

## Vorlagen für Experience Fragments {#templates-for-experience-fragments}

>[!CAUTION]
>
>Für Experience Fragments werden ***nur*** [bearbeitbare Vorlagen unterstützt.](/help/sites-developing/page-templates-editable.md)
>
>Experience Fragments können nur auf Seiten verwendet werden, die auf bearbeitbaren Vorlagen basieren.

Beim Entwickeln einer neuen Vorlage für Experience Fragments können Sie den Standardverfahren für eine [bearbeitbare Vorlage](/help/sites-developing/page-templates-editable.md) folgen.

Um eine Experience Fragment-Vorlage zu erstellen, die vom **Experience Fragment**-Assistenten erstellt wird, müssen Sie einen dieser Regelsätze verfolgen:

1. Beide:

   1. Der Ressourcentyp der Vorlage (der Anfangsknoten) muss erben von:
      `cq/experience-fragments/components/xfpage`

   1. Der Name der Vorlage muss beginnen mit:
      `experience-fragments`
Dadurch können Benutzer Experience Fragments in /content/experience-fragments erstellen, da die `cq:allowedTemplates`-Eigenschaft dieses Ordners alle Vorlagen enthält, deren Namen mit `experience-fragment` beginnen. Kunden können diese Eigenschaft aktualisieren, um ihr eigenes Namensschema oder ihre eigenen Vorlagenspeicherorte einzuschließen.

1. [Zulässige Vorlagen](/help/sites-authoring/experience-fragments.md#configure-allowed-templates-folder) können in der Experience Fragments-Konsole konfiguriert werden.
<!--
1. Add the template details manually in `cq:allowedTemplates` on the `/content/experience-fragment` node.
-->

<!-- >[!NOTE]
>
>[Allowed templates](/help/sites-authoring/experience-fragments.md#configuring-allowed-templates) can be configured in the Experience Fragments console.
-->

## Komponenten für Experience Fragments {#components-for-experience-fragments}

[Die Entwicklung von Komponenten für die Verwendung mit/in Experience Fragments erfolgt gemäß den üblichen Verfahren.](/help/sites-developing/components.md)

Die einzige zusätzliche Konfiguration besteht darin, sicherzustellen, dass die Komponenten [in der Vorlage zulässig sind. Dies wird mit der Inhaltsrichtlinie erreicht](/help/sites-developing/page-templates-editable.md#content-policies).

## Der Experience Fragment Link Rewriter Provider – HTML {#the-experience-fragment-link-rewriter-provider-html}

In AEM können Sie Experience Fragments erstellen. Ein Experience Fragment:

* besteht aus einer Gruppe von Komponenten und einem Layout,
* kann unabhängig von einer AEM-Seite vorhanden sein.

Einer der Anwendungsfälle für solche Gruppen ist das Einbetten von Inhalten in Touchpoints von Dritten, wie z. B. Adobe Target.

### Standardmäßige Link-Umschreibung {#default-link-rewriting}

Mit der Funktion [Nach Target exportieren](/help/sites-administering/experience-fragments-target.md) können Sie:

* ein Experience Fragment erstellen,
* Komponenten hinzufügen,
* und es dann als Adobe Target-Angebot entweder im HTML- oder JSON-Format exportieren.

Diese Funktion kann [in einer Autoreninstanz von AEM aktiviert werden](/help/sites-administering/experience-fragments-target.md#Prerequisites). Sie erfordert eine gültige Adobe Target-Konfiguration und Konfigurationen für den Link Externalizer.

Der Link Externalizer wird verwendet, um die richtigen URLs zu ermitteln, die beim Erstellen der HTML-Version des Target-Angebots erforderlich sind, die anschließend an Adobe Target gesendet wird. Dies ist erforderlich, da Adobe Target erfordert, dass alle Links im Target-HTML-Angebot öffentlich zugänglich sind. Dies bedeutet, dass alle Ressourcen, auf die die Links verweisen, und das Experience Fragment selbst veröffentlicht werden müssen, bevor sie verwendet werden können.

Wenn Sie ein Target-HTML-Angebot erstellen, wird standardmäßig eine Anfrage an einen benutzerdefinierten Sling-Selektor in AEM gesendet. Dieser Selektor heißt `.nocloudconfigs.html`. Wie der Name schon sagt, erstellt er ein einfaches HTML-Rendering eines Experience Fragment, enthält jedoch keine Cloud-Konfigurationen (die überflüssige Informationen wären).

Nachdem Sie die HTML-Seite generiert haben, nimmt die Sling Rewriter-Pipeline Änderungen an der Ausgabe vor:

1. Die Elemente `html`, `head` und `body` werden durch `div`-Elemente ersetzt. Die Elemente `meta`, `noscript` und `title` werden entfernt (sie sind untergeordnete Elemente des ursprünglichen `head`-Elements und werden nicht berücksichtigt, wenn dieses durch das `div`-Element ersetzt wird).

   Dies geschieht, um sicherzustellen, dass das HTML-Target-Angebot in Target-Aktivitäten einbezogen werden kann.

1. AEM ändert alle internen Links im HTML-Code, sodass sie auf eine veröffentlichte Ressource verweisen.

   Um die zu ändernden Links zu bestimmen, folgt AEM diesem Muster für Attribute von HTML-Elementen:

   1. `src`-Attribute
   1. `href`-Attribute
   1. `*-src`-Attribute (wie „data-src“, „custom-src“ usw.)
   1. `*-href`-Attribute (wie `data-href`, `custom-href`, `img-href` usw.)

   >[!NOTE]
   >
   >Die internen Links in der HTML-Datei sind normalerweise relative Links, aber es kann vorkommen, dass benutzerdefinierte Komponenten vollständige URLs im HTML-Code bereitstellen. Standardmäßig ignoriert AEM diese vollständigen URLs und nimmt keine Änderungen vor.

   Die Links in diesen Attributen werden durch den AEM Link Externalizer `publishLink()` geleitet, um die URL so neu zu erstellen, als wäre sie in einer veröffentlichten Instanz und als solche öffentlich verfügbar.

Bei Verwendung einer vordefinierten Implementierung sollte der oben beschriebene Prozess ausreichen, um das Target-Angebot aus dem Experience Fragment zu generieren und es dann in Adobe Target zu exportieren. Es gibt jedoch einige Anwendungsfälle, die in diesem Prozess nicht berücksichtigt werden. Dazu gehören:

* Sling-Zuordnung nur für die Veröffentlichungsinstanz verfügbar
* Dispatcher-Umleitungen

Für diese Anwendungsfälle stellt AEM die Link Rewriter Provider-Schnittstelle bereit.

### Link Rewriter Provider-Schnittstelle {#link-rewriter-provider-interface}

Für kompliziertere Fälle, die nicht vom [Standard](#default-link-rewriting) abgedeckt werden, bietet AEM die Link Rewriter Provider-Schnittstelle. Dies ist eine `ConsumerType`-Schnittstelle, die Sie als Service in Ihren Bundles implementieren können. Sie umgeht die Änderungen, die AEM an internen Links eines HTML-Angebots vornimmt, die aus einem Experience Fragment gerendert wurden. Diese Schnittstelle ermöglicht es Ihnen, das Umschreiben interner HTML-Links an Ihre geschäftlichen Anforderungen anzupassen.

Beispiele für Anwendungsfälle für die Implementierung dieser Schnittstelle als Service:

* Sling-Zuordnungen sind in den Veröffentlichungsinstanzen aktiviert, nicht jedoch in der Autoreninstanz
* Eine Dispatcher- oder ähnliche Technologie wird verwendet, um URLs intern umzuleiten
* Es gibt `sling:alias mechanisms` für Ressourcen

>[!NOTE]
>
>Diese Schnittstelle verarbeitet nur die internen HTML-Links aus dem generierten Target-Angebot.

Die Link Rewriter Provider-Schnittstelle (`ExperienceFragmentLinkRewriterProvider`) lautet wie folgt:

```java
public interface ExperienceFragmentLinkRewriterProvider {

    String rewriteLink(String link, String tag, String attribute);

    boolean shouldRewrite(ExperienceFragmentVariation experienceFragment);

    int getPriority();

}
```

### Verwendung der Link Rewriter Provider-Schnittstelle {#how-to-use-the-link-rewriter-provider-interface}

Um die Schnittstelle zu verwenden, müssen Sie zunächst ein Bundle mit einer neuen Dienstkomponente erstellen, die die Link Rewriter Provider-Schnittstelle implementiert.

Dieser Dienst wird verwendet, um das Umschreiben beim Experience Fragment-Export in Target zu ermöglichen, damit auf die verschiedenen Links zugegriffen werden kann.

Beispiel: `ComponentService`:

```java
import com.adobe.cq.xf.ExperienceFragmentLinkRewriterProvider;
import com.adobe.cq.xf.ExperienceFragmentVariation;
import org.osgi.service.component.annotations.Service;
import org.osgi.service.component.annotations.Component;

@Component
@Service
public class GeneralLinkRewriter implements ExperienceFragmentLinkRewriterProvider {

    @Override
    public String rewriteLink(String link, String tag, String attribute) {
        return null;
    }

    @Override
    public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
        return false;
    }

    @Override
    public int getPriority() {
        return 0;
    }

}
```

Damit der Service funktioniert, müssen jetzt drei Methoden innerhalb des Service implementiert werden:

* ` [shouldRewrite](#shouldrewrite)`
* ` [rewriteLink](#rewritelink)`

   * `rewriteLinkExample2`

* ` [getPriority](#priorities-getpriority)`

#### shouldRewrite {#shouldrewrite}

Sie müssen dem System angeben, ob die Links umgeschrieben werden müssen, wenn für eine bestimmte Experience Fragment-Variante ein Aufruf „In Target exportieren“ aufgerufen wird. Implementieren Sie dazu die folgende Methode:

`shouldRewrite(ExperienceFragmentVariation experienceFragment);`

Beispiel:

```java
@Override
public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
    return experienceFragment.getPath().equals("/content/experience-fragment/master");
}
```

Diese Methode erhält als Parameter die Experience Fragment-Variante, die das System „In Target exportieren“ derzeit umschreibt.

Im obigen Beispiel möchten wir Folgendes umschreiben:

* in `src` vorhandene Links

* nur `href`-Attribute

* für ein bestimmtes Experience Fragment:
  `/content/experience-fragment/master`

Alle anderen Experience Fragments, die das System „In Target exportieren“ durchlaufen, werden ignoriert und sind von den in diesem Service implementierten Änderungen nicht betroffen.

#### rewriteLink {#rewritelink}

Für die Experience Fragment-Variante, die vom Umschreibungsprozess betroffen ist, wird der Service dann die Links umschreiben. Bei jedem Auftreten eines Links im internen HTML-Code wird die folgende Methode aufgerufen:

`rewriteLink(String link, String tag, String attribute)`

Als Eingabe erhält die Methode die folgenden Parameter:

* `link`
Die `String`-Darstellung des Links, der derzeit verarbeitet wird. Dies ist normalerweise eine relative URL, die auf die Ressource in der Autoreninstanz verweist.

* `tag`
Der Name des HTML-Elements, das verarbeitet wird.

* `attribute`
Der genaue Attributname.

Wenn beispielsweise das System „In Target exportieren“ dieses Element verarbeitet, können Sie `CSSInclude` wie folgt definieren:

```java
<link rel="stylesheet" href="/etc.clientlibs/foundation/clientlibs/main.css" type="text/css">
```

Die `rewriteLink()`-Methode wird mithilfe der folgenden Parameter aufgerufen:

```java
rewriteLink(link="/etc.clientlibs/foundation/clientlibs/main.css", tag="link", attribute="href" )
```

Wenn Sie den Dienst erstellen, können Sie Entscheidungen basierend auf der Eingabe treffen und dann den Link entsprechend umschreiben.

In unserem Beispiel möchten wir den `/etc.clientlibs`-Teil der URL entfernen und die entsprechende externe Domain hinzufügen. Um die Dinge einfach zu halten, werden wir in Betracht ziehen, dass wir Zugriff auf einen Resource Resolver für Ihren Service haben, wie in `rewriteLinkExample2`:

>[!NOTE]
>
>Weitere Informationen zum Abrufen eines Ressource Resolver über einen Service-Benutzer finden Sie unter [Service-Benutzer in AEM](/help/sites-administering/security-service-users.md).

```java
private ResourceResolver resolver;

private Externalizer externalizer;

@Override
public String rewriteLink(String link, String tag, String attribute) {

    // get the externalizer service
    externalizer = resolver.adaptTo(Externalizer.class);
    if(externalizer == null) {
        // if there was an error, then we do not modify the link
        return null;
    }

    // remove leading /etc.clientlibs from resource link before externalizing
    link = link.replaceAll("/etc.clientlibs", "");

    // considering that we configured our publish domain, we directly apply the publishLink() method
    link = externalizer.publishLink(resolver, link);

    return link;
}
```

>[!NOTE]
>
>Wenn über die oben beschriebene Methode `null` zurückgegeben wird, belässt das System „In Target exportieren“ den Link unverändert (ein relativer Link zu einer Ressource).

#### Prioritäten – getPriority {#priorities-getpriority}

Es ist nicht ungewöhnlich, dass mehrere Service für verschiedene Arten von Experience Fragments benötigt werden oder dass sogar ein generischer Service vorhanden ist, der die Externalisierung und Zuordnung aller Experience Fragments übernimmt. In diesen Fällen kann es zu Konflikten darüber kommen, welcher Service verwendet werden soll, sodass AEM die Möglichkeit bietet, **Prioritäten** für verschiedene Services festzulegen. Die Prioritäten werden nach folgendem Verfahren festgelegt:

* `getPriority()`

Diese Methode ermöglicht die Verwendung mehrerer Services, bei denen die `shouldRewrite()`-Methode für dasselbe Experience Fragment „true“ zurückgibt. Der Service, der die höchste Zahl aus der `getPriority()`-Methode zurückgibt, ist der Service, der die Experience Fragment-Variante verarbeitet.

Beispielsweise können Sie einen `GenericLinkRewriterProvider`-Service verwenden, der die grundlegende Zuordnung für alle Experience Fragments handhabt und wenn die `shouldRewrite()` Methode für alle Experience-Fragment-Varianten `true` zurückgibt. Für mehrere spezifische Experience Fragments ist möglicherweise eine besondere Behandlung erforderlich. In diesem Fall können Sie also einen `SpecificLinkRewriterProvider`-Service bereitstellen, für den die `shouldRewrite()`-Methode nur für einige Experience Fragment-Varianten „true“ zurückgibt. Um sicherzustellen, dass `SpecificLinkRewriterProvider` für die Verarbeitung dieser Experience Fragment-Varianten ausgewählt wird, muss in der `getPriority()`-Methode eine höhere Zahl zurückgegeben werden als für `GenericLinkRewriterProvider.`
