---
title: Überlegungen und Anforderungen zum Netzwerk
description: Erörtert Überlegungen zum Netzwerk bei der Planung einer Bereitstellung von [!DNL Adobe Experience Manager Assets] .
contentOwner: AG
role: Architect, Admin
feature: Developer Tools
solution: Experience Manager, Experience Manager Assets
exl-id: bf1dee29-75bb-445b-a661-fc7c52d78b63
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1010'
ht-degree: 100%

---

# Überlegungen zum Netzwerk für [!DNL Assets] {#assets-network-considerations}

Sie müssen Ihr Netzwerk ebenso gut verstehen wie [!DNL Adobe Experience Manager Assets]. Das Netzwerk kann Uploads, Downloads und Benutzererlebnisse beeinflussen. Eine grafische Darstellung Ihrer Netzwerktopologie hilft bei der Erkennung von Engpässen und unzureichend optimierten Bereichen im Netzwerk, die Sie beseitigen bzw. korrigieren müssen, um die Netzwerkleistung und das Benutzererlebnis zu verbessern.

Stellen Sie sicher, dass Sie Folgendes in Ihre Netzwerkgrafik einbeziehen:

* Möglichkeit der Verbindung des Client-Geräts (z. B. Computer, Mobilgerät und Tablet) mit dem Netzwerk.
* Topologie des Unternehmensnetzwerks.
* Uplink zum Internet vom Unternehmensnetzwerk und von der [!DNL Experience Manager]-Umgebung.
* Topologie der [!DNL Experience Manager]-Umgebung.
* Definition gleichzeitiger Verbraucher und Verbraucherinnen der [!DNL Experience Manager]-Netzwerkschnittstelle.
* Definierte Workflows der [!DNL Experience Manager]-Bereitstellung.

## Möglichkeit der Verbindung des Client-Geräts mit dem Unternehmensnetzwerk {#connectivity-from-the-client-device-to-the-corporate-network}

Beginnen Sie, indem Sie die Verbindungsmöglichkeit zwischen den einzelnen Client-Geräten und dem Unternehmensnetzwerk grafisch darstellen. In dieser Phase ermitteln Sie gemeinsam genutzte Ressourcen wie WLAN-Verbindungen, bei denen mehrere Benutzende Zugriff auf denselben Punkt oder Ethernet-Switch haben, wodurch sie Assets hoch- bzw. herunterladen können.

![chlimage_1-353](assets/chlimage_1-353.png)

Client-Geräte stellen auf verschiedene Arten eine Verbindung mit einem Unternehmensnetzwerk her, z. B. über freigegebenes WLAN, Ethernet mit gemeinsam genutztem Switch und VPN. Das Erkennen und Verstehen von Engpässen in diesem Netzwerk ist für die Planung von [!DNL Assets] und für die Netzwerkmodifizierung unerlässlich.

Oben links im Diagramm sind drei Geräte dargestellt, die gemeinsam einen 48 MBit/s schnellen WLAN-Zugangspunkt nutzen. Wenn alle Geräte gleichzeitig etwas hochladen, wird die WLAN-Netzbandbreite von den Geräten gemeinsam genutzt. Im Vergleich zu dem System als Ganzem können Benutzende auf unterschiedliche Engpässe stoßen, die daraus resultieren, dass die drei Clients diesen Kanal gemeinsam nutzen.

Es ist eine Herausforderung, die wahre Geschwindigkeit eines WLAN-Netzes zu messen, weil ein langsames Gerät die Leistung anderer Clients am Zugangspunkt beeinträchtigen kann. Wenn Sie beabsichtigen, WLAN für Asset-Interaktionen zu verwenden, führen Sie einen Geschwindigkeitstest mit mehreren Clients gleichzeitig durch, um den Durchsatz zu bewerten.

Unten links im Diagramm sind zwei Geräte dargestellt, die mit dem Unternehmensnetzwerk über unabhängige Kanäle verbunden sind. Daher kann jedes Gerät eine Mindestgeschwindigkeit von 10 MBit/s und 100 MBit/s nutzen.

Der rechts gezeigte Computer hat einen begrenzten Upstream zum Unternehmensnetzwerk über eine VPN-Verbindung mit einer Geschwindigkeit von 1 MBit/s. Das Benutzererlebnis bei der 1 MBit/s schnellen Verbindung unterscheidet sich erheblich vom Benutzererlebnis bei der 1 GBit/s schnellen Verbindung. Je nach Größe der Assets, mit denen Benutzende interagieren, ist ihr VPN-Uplink für die Aufgabe möglicherweise nicht ausreichend.

## Topologie des Unternehmensnetzwerks  {#topology-of-the-corporate-network}

![chlimage_1-354](assets/chlimage_1-354.png)

Das Diagramm zeigt höhere Uplink-Geschwindigkeiten innerhalb des Unternehmensnetzwerks, als im Allgemeinen üblich sind. Diese Leitungen sind gemeinsam genutzte Ressourcen. Wenn erwartet wird, dass ein freigegebener Switch die Vorgänge von 50 Clients abwickelt, kann es hier möglicherweise zu einem Engpass kommen. Im anfangs gezeigten Diagramm nutzen nur zwei Computer die betreffende Verbindung.

## Uplink zum Internet vom Unternehmensnetzwerk und von der [!DNL Experience Manager]-Umgebung {#uplink-to-the-internet-from-the-corporate-network-and-aem-environment}

![chlimage_1-355](assets/chlimage_1-355.png)

Es ist wichtig, unbekannte Faktoren des Internets und der VPC-Verbindung zu berücksichtigen, da die Bandbreite im Internet durch Spitzenlasten oder umfangreiche Anbieterausfälle verringert werden kann. Im Allgemeinen ist eine Internet-Verbindung zuverlässig. Manchmal kann es allerdings zu Engpässen kommen.

Am Uplink von einem Unternehmensnetzwerk zum Internet kann es sein, dass andere Dienste die Bandbreite nutzen. Es ist wichtig, zu verstehen, wie viel Bandbreite für Assets bereitgestellt oder priorisiert werden kann. Beispielsweise können Sie bei einer 1 GBit/s schnellen Verbindung mit 80 % Auslastung nur maximal 20 % der Bandbreite für [!DNL Experience Manager Assets] zuteilen.

Unternehmens-Firewalls und Proxys können Bandbreite zudem auf vielfältige Weise anpassen. Diese Geräteart kann Bandbreite mithilfe der Dienstgüte, der Bandbreitenbeschränkungen pro Person oder der Bitratenbeschränkungen pro Host priorisieren. Dies sind wichtige Engpässe, die zu untersuchen sind, da sie das [!DNL Assets]-Benutzererlebnis erheblich beeinträchtigen können.

In diesem Beispiel nutzt das Unternehmen einen 10 GBit/s schnellen Uplink. Dieser sollte für mehrere Clients ausreichen. Außerdem beschränkt die Firewall die Host-Geschwindigkeit auf 10 MBit/s. Diese Beschränkung kann den Traffic zu einem einzelnen Host möglicherweise bis auf 10 MBit/s drosseln, obwohl der Uplink zum Internet auf 10 GBit/s ausgelegt ist.

Dies ist der kleinste Engpass in Bezug auf Clients. Sie können jedoch die für die Firewall verantwortliche Netzwerkbetriebsgruppe kontaktieren, um festzustellen, ob eine Änderung oder ein Eintrag in die Zulassungsliste infrage kommt.

Aus den Beispieldiagrammen ist ersichtlich, dass sechs Geräte einen konzeptionellen, 10 MBit/s schnellen Kanal gemeinsam nutzen. Je nach Größe der genutzten Assets reicht dies möglicherweise nicht aus, um die Erwartungen der Benutzenden zu erfüllen.

## Topologie der [!DNL Experience Manager]-Umgebung {#topology-of-the-aem-environment}

![chlimage_1-356](assets/chlimage_1-356.png)

Das Entwerfen der Topologie der [!DNL Experience Manager]-Umgebung erfordert detaillierte Kenntnisse der Systemkonfiguration sowie der Art der Netzwerkverbindung innerhalb der Benutzerumgebung.

Das Beispielszenario umfasst eine Veröffentlichungsfarm mit fünf Servern und einem binären S3-Speicher. Dynamic Media ist ebenfalls konfiguriert.

Der Dispatcher nutzt seine 100 MBit/s schnelle Verbindung gemeinsam mit zwei Entitäten, der Außenwelt und der [!DNL Experience Manager]-Bereitstellung. Für gleichzeitiges Hoch- und Herunterladen sollten Sie diesen Wert durch zwei teilen. Der zugeordnete externe Speicher verwendet eine separate Verbindung.

Die [!DNL Experience Manager]-Bereitstellung nutzt ihre 1 GBit/s schnelle Verbindung mit mehreren Diensten gemeinsam. Aus Sicht der Netzwerktopologie entspricht das der Nutzung eines einzelnen Kanals mit verschiedenen Diensten.

Was das Netzwerk zwischen Client-Gerät und [!DNL Experience Manager]-Bereitstellung angeht, so scheint der kleinste Engpass die Beschränkung auf 10 MBit/s durch die Unternehmens-Firewall zu sein. Sie können diese Werte für die in der [Anleitung zur Dimensionierung in Assets](assets-sizing-guide.md) beschriebenen Größenberechnung verwenden, um das Benutzererlebnis zu bestimmen.

## Definierte Workflows der [!DNL Experience Manager]-Bereitstellung {#defined-workflows-of-the-aem-deployment}

Bei Überlegungen zur Netzwerkleistung ist es möglicherweise wichtig, die Workflows und die im System stattfindenden Veröffentlichungen zu berücksichtigen. Außerdem beanspruchen S3 oder Speicher, der im Netzwerk zugeteilt ist und von Ihnen verwendet wird, und I/O-Anforderungen Netzwerkbandbreite. Daher wird die Leistung selbst in einem voll optimierten Netzwerk durch die Anzahl der Datenträger-I/O beschränkt.

Um Prozesse zu optimieren, die mit der Asset-Aufnahme zu tun haben (insbesondere, wenn eine große Anzahl von Assets hochgeladen wird), untersuchen Sie die Asset-Workflows, um mehr über ihre Konfiguration zu erfahren.

Bei der Untersuchung der internen Workflow-Topologie sollten Sie Folgendes analysieren:

* Verfahren zum Schreiben eines Assets
* Workflows/Ereignisse, die ausgelöst werden, wenn Assets/Metadaten geändert werden
* Verfahren zum Lesen eines Assets

Es folgen einige Punkte, die zu berücksichtigen sind:

* Lesen/Rückgabe von XMP-Metadaten
* Automatische Aktivierung und Replikation
* Wasserzeichen  
* Aufnahme von Unter-Assets/Seitenextraktion
* Überlappende Workflows

Es folgt ein Kundenbeispiel für die Definition eines Asset-Workflows.

![chlimage_1-357](assets/chlimage_1-357.png)
