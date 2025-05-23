---
title: Fehlerbehebung in AEM während des Authorings
description: Der folgende Abschnitt beschäftigt sich mit einigen Problemen, auf die Sie bei der Arbeit mit AEM stoßen können, und liefert entsprechende Lösungsvorschläge.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
exl-id: be4397d1-0680-4b44-bdd2-825b521a44d6
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 100%

---

# Fehlerbehebung in AEM beim Authoring{#troubleshooting-aem-when-authoring}

Der folgende Abschnitt beschäftigt sich mit einigen Problemen, auf die Sie bei der Arbeit mit AEM stoßen können, und liefert entsprechende Lösungsvorschläge.

>[!NOTE]
>
>Wenn Probleme auftreten, sollten Sie auch die Liste der [bekannten Probleme](/help/release-notes/release-notes.md) für Ihre Instanz (Version und Service Packs) prüfen.

>[!NOTE]
>
>Benutzer mit Administratorrechten, die Probleme in AEM beheben möchten, können die unter [Fehlerbehebung in AEM (für Administratoren)](/help/sites-administering/troubleshoot.md) beschriebenen Lösungen nutzen. Wenn Sie nicht über ausreichende Rechte verfügen, wenden Sie sich bezüglich der Problembehebung in AEM an Ihre Admins.

## Alte Seitenversion wird weiterhin auf der veröffentlichten Website angezeigt {#old-page-version-still-on-published-site}

* **Problem**:

   * Sie haben Änderungen an einer Seite vorgenommen und die Seite auf die Veröffentlichungs-Site repliziert, aber auf der Veröffentlichungs-Site wird immer noch die *alte* Version der Seite angezeigt.

* **Grund**:

   * Dies kann verschiedene Gründe haben. Meist liegt es am Cache (entweder dem Ihres lokalen Browsers oder dem des Dispatchers), gelegentlich kann es sich jedoch auch um ein Problem mit der Replikations-Warteschlange handeln.

* **Lösungen**:

   * Hier gibt es mehrere Möglichkeiten:
   * Überprüfen Sie, ob die Seite korrekt repliziert wurde. Überprüfen Sie den Seitenstatus und ggf. den Status der Replikations-Warteschlange.
   * Löschen Sie den Cache des lokalen Browsers und rufen Sie die Seite erneut auf.
   * Fügen Sie dem Ende der Seiten-URL `?` hinzu:

     `http://localhost:4502/sites.html/content?`

     Dadurch wird die Seite direkt von AEM abgerufen und der Dispatcher wird umgangen. Wenn die aktualisierte Seite angezeigt wird, ist dies ein Hinweis darauf, dass Sie den Dispatcher-Cache löschen müssen.

   * Wenden Sie sich an den Systemadministrator, wenn Probleme mit den Replikationswarteschlangen vorliegen.

## Sidekick wird nicht angezeigt {#sidekick-not-visible}

* **Problem**:

   * Beim Bearbeiten einer Inhaltsseite in der Authoring-Umgebung wird der Sidekick nicht angezeigt.

* **Grund**:

   * In seltenen Fällen kann es vorkommen, dass Sie die Kopfzeile des Sidekicks außerhalb des aktuellen Fensterbereichs platziert haben. Das bedeutet, dass Sie sie nicht neu platzieren können.

* **Lösung**:

   * Melden Sie sich bei Ihrer aktuellen Sitzung ab und melden Sie sich erneut an. Der Sidekick wird wieder an der Standardposition angezeigt.

## Suchen und Ersetzen: nicht alle Vorkommen werden ersetzt {#find-replace-not-all-instances-are-replaced}

* **Problem:**

   * Beim Verwenden der Option **Suchen und Ersetzen** kann es passieren, dass nicht alle Vorkommen des `find`-Begriffs auf einer Seite ersetzt werden.

* **Grund**:

   * Die ordnungsgemäße Funktion von **Suchen und Ersetzen** ist davon abhängig, wie der Inhalt gespeichert wurde und ob er durchsucht werden kann. Beispiel: Ein Blog-Text wird in der Eigenschaft `jcr:text` gespeichert, die der Konfiguration entsprechend nicht durchsucht werden kann. Der Standardbereich für das Servlet „Suchen und Ersetzen“ deckt die folgenden Eigenschaften ab:

      * `jcr:title`
      * `jcr:description`
      * `jcr:text`
      * `text`

* **Lösung**:

   * Diese Definitionen können mit der Konfiguration für **Day CQ WCM Find Replace Servlet** geändert werden, indem z. B. die **Web-Konsole** verwendet wird:

     `http://localhost:4502/system/console/configMgr`
