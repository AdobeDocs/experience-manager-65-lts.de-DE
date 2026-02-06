---
title: Voraussetzungen für das Integrieren mit Adobe Target
description: Hier finden Sie Informationen über die Voraussetzungen für die Integration mit Adobe Target.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
exl-id: e1771229-b2ce-406a-95a5-99b11fafbe34
source-git-commit: 24bd1f57da3f9ce613ee28276d1ae9465b6dfba6
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 63%

---

# Voraussetzungen für die Integration mit Adobe Target{#prerequisites-for-integrating-with-adobe-target}

Als Teil der [Integration von AEM und Adobe Target](/help/sites-administering/target.md) müssen Sie sich bei Adobe Target registrieren, den Replikationsagenten konfigurieren und Aktivitätseinstellungen auf dem Veröffentlichungsknoten sichern.

## Registrieren bei Adobe Target {#registering-with-adobe-target}

Zur Integration von AEM mit Adobe Target müssen Sie über ein gültiges Adobe Target-Konto verfügen. Dieses Konto muss mindestens über die Berechtigungsstufe einer **Genehmigenden Person** verfügen. Nach der Registrierung bei Adobe Target erhalten Sie einen Clientcode. Dieser Clientcode und Ihr Adobe Target-Anmeldename sowie -Kennwort sind erforderlich, um eine Verbindung zwischen AEM und Adobe Target herzustellen.

Der Clientcode identifiziert das Adobe Target-Kundenkonto beim Aufruf des Adobe Target-Servers.

>[!NOTE]
>
>Das Target-Team muss Ihr Konto für die Verwendung der Integration aktivieren.
>
>Falls dies nicht der Fall ist, wenden Sie sich an die [Kundenunterstützung von Adobe](https://experienceleague.adobe.com/en/docs/target/using/cmp-resources-and-contact-information).

## Aktivieren des Target-Replikationsagenten {#enabling-the-target-replication-agent}

Auf der Autoreninstanz muss der Test-and-Target-[Replikationsagent](/help/sites-deploying/replication.md) aktiviert werden. Dieser Replikationsagent ist standardmäßig deaktiviert, wenn Sie bei der Installation von AEM den Ausführungsmodus [nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) verwendet haben. Weitere Informationen zum Speichern Ihrer Produktionsumgebung finden Sie in der [Sicherheits-Checkliste](/help/sites-administering/security-checklist.md).

1. Klicken Sie auf der AEM-Homepage auf **Tools** > **Bereitstellung** > **Replikation**.
1. Klicken Sie auf **Agenten für Autor**.
1. Klicken Sie auf den **Test &amp; Target**-Replikationsagenten und dann auf **Bearbeiten**.
1. Wählen Sie die Option „Aktiviert“ aus und klicken Sie auf **OK**.

   >[!NOTE]
   >
   >Bei der Konfiguration des Test &amp; Target-Replikationsagenten wird auf der Registerkarte **Transport** für den URI standardmäßig `tnt:///` festgelegt. Ersetzen Sie den URI nicht durch `https://admin.testandtarget.omniture.com`.
   >
   >Wenn Sie versuchen, die Verbindung mit `tnt:///` zu testen, wird ein Fehler angezeigt, der das erwartete Verhalten darstellt. Der Grund dafür ist, dass der URI nur zur internen Verwendung gedacht ist. Verwenden Sie nicht mit **Verbindung**.

## Sichern des Aktivitätseinstellungsknotens {#securing-the-activity-settings-node}

Schützen Sie den Aktivitätseinstellungsknoten **cq:ActivitySettings** auf der Veröffentlichungsinstanz, damit er für normale Benutzer nicht zugänglich ist. Der Aktivitätseinstellungsknoten sollte ausschließlich für den Service zur Verfügung stehen, mit dem die Aktivitätssynchronisierung mit Adobe Target durchgeführt wird.

Der **cq:ActivitySettings**-Knoten ist in CRXDE Lite unter `/content/campaigns/*nameofbrand*`* *unter dem `jcr:content` „activities“ verfügbar. Zum Beispiel: `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Dieser Knoten wird nur erstellt, wenn Sie eine Komponente als Ziel angeben.

Der **cq:ActivitySettings**-Knoten unter dem `jcr:content` der Aktivität wird von den folgenden ACLs geschützt:

* Jedem alles verweigern.
* `jcr:read,rep:write` für `target-activity-authors` zulassen (Autor ist standardmäßig Mitglied dieser Gruppe).
* `jcr:read,rep:write` für `targetservice` zulassen.

Diese Einstellungen gewährleisten, dass normale Benutzende keinen Zugriff auf die Knoteneigenschaften haben. Verwenden Sie dieselben ACLs für „author“ und „publish“. Weitere Informationen finden Sie unter [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md).

## Konfigurieren des AEM Link Externalizer {#configuring-the-aem-link-externalizer}

Beim Bearbeiten einer Aktivität in Adobe Target verweist die URL auf **localhost**, außer Sie ändern die URL auf dem AEM-Autorenknoten. Sie können den AEM-Link-Externalizer konfigurieren, wenn der exportierte Inhalt auf eine bestimmte *Veröffentlichungs*-Domain verweisen soll.

>[!NOTE]
>
>Siehe auch [Hinzufügen der Cloud-Konfiguration](/help/sites-administering/experience-fragments-target.md#add-the-cloud-configuration).

So konfigurieren Sie den AEM Externalizer:

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Externalisieren von URLs](/help/sites-developing/externalizer.md).

1. Navigieren Sie zur OSGi-Web-Konsole unter **https://&lt;server>:&lt;port>/system/console/configMgr**.
1. Suchen Sie nach **Day CQ Link Externalizer** und geben Sie die Domain des Autorenknotens an.

   ![Day CQ Link Externalizer](assets/aem-externalizer-01.png)
