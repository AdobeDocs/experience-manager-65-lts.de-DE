---
title: Nachhaltige Aktualisierungen
description: Erfahren Sie mehr über nachhaltige Aktualisierungen in Adobe Experience Manager 6.4.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
hide: true
hidefromtoc: true
exl-id: 5a93918b-3b5f-49e0-9283-86776f9d8fb4
source-git-commit: 180fd02df50f84e0d4f9bc01efe56e28d25555e2
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 100%

---

# Nachhaltige Aktualisierungen{#sustainable-upgrades}

## Anpassungs-Framework {#customization-framework}

### Architektur (Funktion/Infrastruktur/Inhalt/Anwendung)  {#architecture-functional-infrastructure-content-application}

Das Anpassungs-Framework hilft Ihnen, Verstöße in nicht erweiterbaren Bereichen des Codes (z. B. APIs) oder des Inhalts (z. B. Überlagerungen) einzuschränken, die Aktualisierungen behindern.

Das Anpassungs-Framework besteht aus zwei Komponenten: **API-Oberfläche** und **Inhaltsklassifizierung**.

#### API-Oberfläche {#api-surface}

In früheren Versionen von Adobe Experience Manager (AEM) wurden viele APIs über das Uber-JAR verfügbar gemacht. Einige dieser APIs waren nicht für die Verwendung durch Kundinnen und Kunden vorgesehen, wurden jedoch bereitgestellt, um AEM-Funktionen in Bundles zu unterstützen. In Zukunft werden Java-APIs als „Öffentlich“ oder „Privat“ gekennzeichnet, damit Kundinnen und Kunden erkennen, welche APIs im Hinblick auf Aktualisierungen sicher verwendet werden können. Weitere Besonderheiten:

* Java™-APIs, die als `Public` gekennzeichnet sind, können durch benutzerdefinierte Implementierungs-Bundles verwendet und referenziert werden.

* Die öffentlichen APIs sind durch die Installation eines Kompatibilitätspakets abwärtskompatibel.
* Das Kompatibilitätspaket enthält ein Uber-JAR für die Kompatibilität, um Abwärtskompatibilität sicherzustellen.
* Java™-APIs, die als `Private` gekennzeichnet sind, sind ausschließlich zur Verwendung durch interne AEM-Pakete vorgesehen und nicht für benutzerdefinierte Bundles.

>[!NOTE]
>
>Das in diesem Kontext verwendete Konzept von `Private` und `Public` darf nicht mit öffentlichen und privaten Java™-Klassen verwechselt werden.

![image2018-2-12_23-52-48](assets/image2018-2-12_23-52-48.png)

#### Inhaltsklassifizierungen {#content-classifications}

AEM hat lange das Prinzip von Überlagerungen und Sling Resource Merger verwendet, um Kundinnen und Kunden die Möglichkeit zu bieten, AEM-Funktionen zu erweitern und anzupassen. Vordefinierte Funktionen für die AEM-Konsolen und die Benutzeroberfläche werden in **/libs** gespeichert. Kundinnen und Kunden sollten niemals Objekte unter **/libs** ändern, konnten aber zusätzliche Inhalte unter **/apps** hinzufügen, um die in **/libs** definierte Funktionalität zu überlagern und zu erweitern. (Weitere Informationen finden Sie im Beitrag zur Entwicklung mit Überlagerungen.) Dies hat bei der Aktualisierung von AEM zu zahlreichen Problemen geführt, weil teilweise der Inhalt in **/libs** geändert wurde, weshalb die Überlagerungsfunktion auf unerwartete Weise fehlschlug. Kundinnen und Kunden konnten AEM-Komponenten außerdem durch Vererbung über `sling:resourceSuperType` oder einfach durch einen Verweis auf eine Komponente in **/libs** direkt über „sling:resourceType“ erweitern. Ähnliche Aktualisierungsprobleme konnten bei Anwendungsfällen mit Verweisen und Außerkraftsetzungen auftreten.

Um dies sicherer zu machen und für Kundinnen und Kunden deutlicher zu kennzeichnen, welche Bereiche von **/libs** sie gefahrlos verwenden können, wurde der Inhalt in **/libs** mit den folgenden Mixins klassifiziert:

* **Öffentlich (granite:PublicArea)**: Definiert einen Knoten als „Öffentlich“, damit er überlagert, vererbt (`sling:resourceSuperType`) oder direkt verwendet (`sling:resourceType`) werden kann. Als „Öffentlich“ gekennzeichnete Knoten unter „/libs“ können sicher aktualisiert werden, indem ein Kompatibilitätspaket hinzugefügt wird. Kundinnen und Kunden sollten grundsätzlich nur Knoten nutzen, die als „Öffentlich“ gekennzeichnet sind. 

* **Abstrakt (granite:AbstractArea)**: Definiert einen Knoten als „Abstrakt“. Knoten können überlagert oder vererbt (`sling:resourceSupertype`), aber nicht direkt verwendet werden (`sling:resourceType`).

* **Endgültig (granite:FinalArea)** – Definiert einen Knoten als „Endgültig“. Als endgültig eingestufte Knoten sollten idealerweise nicht überlagert oder vererbt werden. Endgültige Knoten können direkt über `sling:resourceType` verwendet werden. Unterknoten der endgültigen Knoten werden standardmäßig als intern eingestuft

* ***Intern (granite:InternalArea)*** – Definiert einen Knoten als „Intern“. Als „intern“ klassifizierte Knoten sollten idealerweise nicht überlagert, vererbt oder direkt verwendet werden. Diese Knoten sind ausschließlich für interne Funktionen von AEM vorgesehen.

* **Keine Anmerkung**: Knoten übernehmen die Klassifizierung gemäß der Baumstruktur. Der /-Stamm ist standardmäßig „Öffentlich“. **Knoten mit einem übergeordneten Knoten, der als „Intern“ oder „Endgültig“ klassifiziert ist, werden ebenfalls als „Intern“ behandelt.**

>[!NOTE]
>
>Diese Richtlinien werden nur für Mechanismen erzwungen, die auf dem Sling-Suchpfad basieren. Andere Bereiche von **/libs**, z. B. eine Client-seitige Bibliothek, die als `Internal` gekennzeichnet sind, können jedoch weiterhin mit einem standardmäßigen clientlib-Einschluss verwendet werden. Es ist wichtig, dass Kundinnen und Kunden in diesen Fällen die Klassifizierung „Intern“ beachten.

#### CRXDE Lite-Inhaltstypindikatoren {#crxde-lite-content-type-indicators}

In CRXDE Lite angewendete Mixins zeigen als `INTERNAL` gekennzeichnete Inhaltsknoten und Strukturen abgeblendet (ausgegraut) an. Für `FINAL` wird lediglich das Symbol abgeblendet. Die untergeordneten Elemente dieser Knoten werden ebenfalls abgeblendet angezeigt. Die Überlagerungsknotenfunktion ist in beiden Fällen deaktiviert.

**Öffentlich**

![image2018-2-8_23-34-5](assets/image2018-2-8_23-34-5.png)

**Endgültig** 

![image2018-2-8_23-34-56](assets/image2018-2-8_23-34-56.png)

**Intern**

![image2018-2-8_23-38-23](assets/image2018-2-8_23-38-23.png)

**Konsistenzprüfung des Inhalts**

>[!NOTE]
>
>Ab AEM 6.5 empfiehlt Adobe die Verwendung der Mustererkennung, um Inhaltszugriffsverletzungen zu erkennen. Berichte zur Mustererkennung sind detaillierter, erkennen mehr Probleme und reduzieren die Wahrscheinlichkeit falsch positiver Ergebnisse.
>
>Weitere Informationen finden Sie unter [Bewerten der Aktualisierungskomplexität mit der Mustererkennung](/help/sites-deploying/pattern-detector.md).

AEM 6.5 bietet außerdem eine Konsistenzprüfung, die Kundinnen und Kunden warnt, wenn überlagerter oder referenzierter Inhalt auf eine Weise verwendet wird, die nicht der Inhaltsklassifizierung entspricht.

Die Prüfung des **Sling/Granite-Inhaltszugriffs** ist eine neue Konsistenzprüfung, die das Repository überwacht, um festzustellen, ob der Kunden-Code unzulässig auf geschützte Knoten in AEM zugreift.

Dabei wird **/apps** gescannt. Dies dauert in der Regel einige Sekunden.

Gehen Sie wie folgt vor, um auf diese neue Konsistenzprüfung zuzugreifen:

1. Navigieren Sie auf der AEM-Startseite zu **Tools > Vorgänge > Konsistenzberichte**
1. Klicken Sie auf **Prüfung des Zugriffs auf Sling/Granite-Inhalte**.

   ![screen_shot_2017-12-14at55648pm](assets/screen_shot_2017-12-14at55648pm.png)

Nachdem der Scan abgeschlossen ist, wird eine Liste mit Warnmeldungen angezeigt, welche die Endbenutzenden über den unzulässig referenzierten, geschützten Knoten informiert:

![screen-shot-2018-2-5healthreports](assets/screenshot-2018-2-5healthreports.png)

Nach der Korrektur der Verstöße wird der Zustand wieder grün angezeigt:

![screenshot-2018-2-5healthreports-violations](assets/screenshot-2018-2-5healthreports-violations.png)

Die Konsistenzprüfung zeigt die Informationen an, die von einem Hintergrunddienst gesammelt werden, der asynchron prüft, sobald eine Überlagerung oder ein Ressourcentyp in allen Sling-Suchpfaden verwendet wird. Wenn Content-Mixins nicht korrekt verwendet wurden, wird ein Verstoß gemeldet.
