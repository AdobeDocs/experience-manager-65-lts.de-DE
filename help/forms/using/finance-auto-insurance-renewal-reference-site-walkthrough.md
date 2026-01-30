---
title: Anleitung zur Erneuerung der Kfz-Versicherung auf der Referenz-Site von We.Finance
description: Erfahren Sie mehr über die Referenz-Website „We.Finance“ zur Erneuerung der Kfz-Versicherung, indem Sie eine exemplarische Vorgehensweise durchführen.
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Foundation Components
role: User, Developer
exl-id: 3f9f1a20-9029-4e30-9c9d-ef452512f7e9
source-git-commit: c0bf6864bb344e582c4f88371c892d401ce2827c
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 48%

---

# Referenz-Website zur Erneuerung der `We.Finance`-Kfz-Versicherung - Anleitung{#we-finance-auto-insurance-renewal-reference-site-walkthrough}

## Szenario `We.Finance` Referenz-Website  {#we-finance-reference-site-scenario}

Die `We.Finance`-Website ist eine Website für Finanzdienstleistungen, auf der Sie die interaktiven Kommunikationsfunktionen von AEM Forms kennenlernen können.

Lesen Sie eine detaillierte Anleitung eines Anwendungsfalls zur `We.Finance` Kfz-Versicherung, die zeigt, wie AEM Forms und seine Integration mit Microsoft® Dynamics dazu beitragen, das Kundenerlebnis in einem Finanzdienstleistungsunternehmen zu personalisieren. Die interaktive Anleitung hat das Ziel, die Implementierung komplexer digitaler Transaktionen und Kundenkommunikationen in einem Finanzunternehmen zu erleichtern.

**Das Ganze beginnt mit dem Benutzerszenario:** 

Sarah Rose ist bereits `We.Finance` Kunde und hat eine Kfz-Versicherungspolice erworben. Nun ist es wie jedes Jahr an der Zeit, dass Sarah ihre Versicherungspolice erneuert. Gloria Rios ist ihre Versicherungsagentin. Die `We.Finance`-Website sendet eine E-Mail, die Sarah an die Erneuerung ihrer Police erinnert. Sarah befolgt die Anweisungen in der E-Mail und schließt den Prozess erfolgreich ab.

## Anleitung für einen Antrag auf eine Kfz-Versicherung {#auto-insurance-application-walkthrough}

Das Szenario des Antrags auf `We.Finance` Kfz-Versicherung ist eine visuelle Schilderung für den Benutzer und basiert auf zwei Rollen:

* Sarah Rose, eine `We.Finance`
* Gloria Rios, Versicherungsagentin, `We.Finance`

### Gloria sendet eine Mitteilung zur Erneuerung der Versicherungspolice von `We.Finance` {#gloria-sends-an-insurance-policy-renewal-communication-from-we-finance}

Gloria meldet sich bei der AEM-Instanz an, klickt auf **Erneuerung der Kfz-Versicherung** und dann auf **Agent-Benutzeroberfläche öffnen**. Durch das Klicken wird das Versicherungsdokument mit den Vertragsdetails von Sarah Rose vorausgefüllt. Gloria klickt auf **Absenden** und auf dem Bildschirm wird die Meldung „Absenden eingeleitet“ und dann nach einigen Sekunden „Erfolgreich abgesendet“ angezeigt.

Sarah erhält eine E-Mail mit dem Betreff „Erneuerung Ihrer Kfz-Versicherung“.

![Agent-Benutzeroberfläche](assets/agent_ui_email_new.png)

#### Sehen Sie selbst {#see-it-yourself}

Wechseln Sie zu **Adobe Experience Manager** > **Forms** > **Forms und Dokumente** > **`We.Finance`** > **Kfz**. Wählen Sie die **interaktive Kommunikation** „Erneuerung der Kfz-Versicherung“ und klicken Sie auf **Agent-Benutzeroberfläche öffnen**. Die interaktive Kommunikation wird in der Agent UI geöffnet. Geben Sie eine gültige E-Mail-Adresse ein, um die E-Mail mit der angehängten Police zu erhalten, und klicken Sie auf „Absenden“.

Sie können direkt unter `https://[authorHost]: authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal.` auf die interaktive Kommunikation zur Erneuerung der Kfz-Versicherung zugreifen und sie dort überprüfen.

### Sarah erhält eine Mitteilung zur Erneuerung der Versicherungspolice von `We.Finance` und entscheidet sich für eine Verlängerung. {#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah erhält eine E-Mail mit einem Anhang von `We.Finance`, die Sarah daran erinnert, dass ihre Kfz-Versicherungspolice bald abläuft. Der Anhang ist die Druckversion des Briefs zu Sarahs Kfz-Versicherung.

Sarah klickt auf die Option **Jetzt erneuern** und wird zur Web-Version des Schreibens zu ihrer Kfz-Versicherung weitergeleitet. Oben im Brief stellt Sarah fest, wie viel Zeit noch in der Police verbleibt, bevor sie abläuft. Die Seite bietet einen Überblick über die Versicherungspolice. Sie enthält Details zu Richtliniennummer, fälligem Betrag, Rabattangeboten und Treueprämien. **Jetzt erneuern** wird am Ende der Police angeklickt.

![ref1](assets/ref1.png)

#### Funktionsweise {#how-it-works}

Die Web- und Druckausgabe Ihres Schreibens zur Kfz-Versicherung wird mithilfe der Mehrkanalfunktionen der interaktiven Kommunikation erstellt.

Die Schaltfläche „Jetzt erneuern“ in der E-Mail ist mit dem Antrag „Erneuerung der Kfz-Versicherung“ verknüpft, bei dem es sich um eine interaktive Kommunikation in einer Veröffentlichungsinstanz handelt.

#### Sehen Sie selbst {#see-it-yourself-1}

Sie müssen eine E-Mail mit einem angehängten PDF-Dokument erhalten haben. Die PDF-Datei ist eine Druckversion dieses Schreibens zur Kfz-Versicherung. Klicken Sie auf **Jetzt erneuern**, um zur Web-Version der Police zu gelangen. Überprüfen Sie Ihre persönlichen Daten und Details der Police und klicken Sie auf **Jetzt erneuern**, um zu einer anderen interaktiven Kommunikation zu gelangen.

Die Schaltfläche **Jetzt erneuern** in der E-Mail leitet Sarah zur Police im Web weiter. Sie können folgende URL aufrufen:

`https://[authorServer]:[authorPort]/content/document.html?schema=fdm&documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&customerId=1`

Sie können die detaillierte Zusammenfassung der Erneuerung Ihrer Kfz-Versicherung überprüfen und auf **Jetzt erneuern** unten auf der Seite klicken.

### Sarah wird auf die Zahlungsseite geleitet. {#sarah-reaches-the-payment-page}

Die `We.Finance`-Website führt Sarah zur Zahlungsseite. Sarah vergleicht ihre Police-Nummer und das Ablaufdatum mit ihren Unterlagen. Rechts auf der Seite prüft Sarah die Zahlungszusammenfassung ihrer Erneuerung mit 10 % Prämienrabatt auf den Gesamtbetrag.

#### Funktionsweise {#how-it-works-1}

Die Schaltfläche „Jetzt erneuern“ leitet Sarah auf die Zahlungsseite. Die Zahlungsseite ist ein adaptives Formular.

#### Sehen Sie selbst {#see-it-yourself-2}

Klicken Sie auf **Jetzt erneuern**, um zur Zahlungsseite zu gelangen. Geben Sie Ihre Kreditkarteninformationen ein und klicken Sie auf **Zahlung ausführen**.

Sie werden zur Zahlungsseite in der Authoring-Instanz geleitet:

`https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&schema=fdm&customerId=1`

### Sarah nimmt die Zahlung vor und schließt den Prozess ab. {#sarah-makes-the-payment-and-completes-the-process}

Sarah gibt ihre Kreditkartendetails ein und klickt auf **Zahlung ausführen**.

#### Funktionsweise {#how-it-works-2}

Wenn Sarah die Kreditkartendetails ausfüllt und auf Senden klickt, wird ihre Kreditkartenzahlung verarbeitet und eine im adaptiven Formular konfigurierte Dankesnachricht wird auf dem Bildschirm angezeigt.

#### Sehen Sie selbst {#see-it-yourself-3}

Sie können die Bestätigungsmeldung anzeigen, nachdem Sie auf „Zahlung ausführen“ geklickt haben

`https://[authorServer]:[authorPort]/content/forms/af/we-finance/credit-card/ccbillpayment/jcr:content/guideContainer.guideThankYouPage.html?owner=admin&status=Submitted`
