---
title: Verwenden des Rich-Text-Editors zum Erstellen von Inhalten
description: Verwenden des Rich-Text-Editors zum Erstellen von Inhalten in Adobe Experience Manager 6.5 LTS.
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
exl-id: 01c2a67a-7168-4362-ad7d-f4990ea43ed8
source-git-commit: 7fcb784124027df87bf41cc6169815d755cea6d7
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 94%

---

# Verwenden des Rich-Text-Editors zum Erstellen von Inhalten {#use-rich-text-editor-to-author-content}

Der Rich-Text-Editor (RTE) ist ein grundlegender Baustein für die Eingabe von Textinhalten in AEM. Er bildet die Grundlage für verschiedene Komponenten, darunter:

* [Text](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/wcm-components/text)
* [Tabelle](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/wcm-components/text#table)

## Bearbeiten im Kontext {#in-place-editing}

Bei der Auswahl einer textbasierten Komponente durch einen einfachen Klick wird, wie bei Komponenten üblich, die [Komponenten-Symbolleiste](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste) geöffnet.

![screen_shot_2018-03-21at163054](assets/screen_shot_2018-03-21at163054.png)

Wenn Sie erneut klicken oder die Komponente anfangs mit einem langsamen Doppelklick auswählen, wird die Funktion zur Bearbeitung im Kontext geöffnet, die über eine eigene Symbolleiste verfügt. Hier können Sie den Inhalt bearbeiten und grundlegende Formatierungsänderungen vornehmen.

![screen_shot_2018-03-21at163214](assets/screen_shot_2018-03-21at163214.png)

Diese Symbolleiste beinhaltet die folgenden Optionen:

* **Format**: Wählen Sie die Optionen „Fett“, „Kursiv“ und „Unterstrichen“ aus.
* **Listen**: Erstellen Sie Stichpunkt- oder Aufzählungslisten oder legen Sie einen Einzug fest.
* **Hyperlink**
* **Verknüpfung aufheben**
* **Vollbild**
* **Schließen**
* **Speichern**

## Bearbeitung im Vollbildmodus {#full-screen-editing}

Bei textbasierten Komponenten wird durch Antippen des Vollbildmodus in der Symbolleiste ![Vollbildbearbeitungsmodus](do-not-localize/screen_shot_2018-03-21at163236.png) der Rich-Text-Editor geöffnet und der restliche Seiteninhalt ausgeblendet.

Im Vollbildmodus werden alle konfigurierten Optionen angezeigt, die Sie zum Bearbeiten verwenden können. Die Verfügbarkeit der Optionen [hängt von der Konfiguration ab](/help/sites-administering/rich-text-editor.md).

![screen_shot_2018-03-21at163248](assets/screen_shot_2018-03-21at163248.png)

Zusätzliche Optionen für den Rich-Text-Editor sind:

* **Anker**: Erstellen Sie einen Anker im Text, zu dem Sie später eine Verknüpfung/einen Verweis herstellen können.
* **Text links ausrichten**
* **Text zentrieren**
* **Text rechts ausrichten**

Den Vollbildmodus schließen Sie, indem Sie auf das Symbol zum Minimieren klicken.

![screen_shot_2018-03-21at163323](assets/screen_shot_2018-03-21at163323.png)

>[!NOTE]
>
>Das Kopieren verschachtelter Listen aus Microsoft Word in den RTE kann zu inkonsistenten Ergebnissen führen und erfordert möglicherweise eine manuelle Anpassung, nachdem der Text in den RTE eingefügt wurde.
