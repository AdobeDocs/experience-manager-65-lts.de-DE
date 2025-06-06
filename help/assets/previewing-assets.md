---
title: Vorschau von Assets
description: Erfahren Sie, wie Sie in Dynamic Media eine Vorschau von Assets wie Videos und Bildern anzeigen können, indem Sie Bild- und Anzeigevorgaben anwenden.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
feature: Asset Management
role: User, Admin
solution: Experience Manager, Experience Manager Assets
exl-id: af2673d9-780c-44bf-9c75-4b908cca4e98
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1381'
ht-degree: 100%

---

# Asset-Vorschau über die Software-Oberfläche {#previewing-assets}

Mit der Vorschau können Sie prüfen, wie ein von Ihnen hochgeladenes digitales Asset aussieht, wenn es von einem Kunden im eigenen Webbrowser angezeigt wird. Die Vorschau erfolgt über den eingebetteten, geräteübergreifenden Standard-Viewer, der dem Asset zugewiesen ist.

Ein Viewer ist eine Sammlung verschiedener Einstellungen oder *Vorgaben*, wie die Anzeigegröße des Viewers, das Zoomverhalten, Farbschemata, Rahmen und Schriftarten. Diese Vorgaben bestimmen, wie Benutzer Rich-Media-Assets auf ihren Computer-Bildschirmen und Mobilgeräten angezeigt bekommen.

Sie können die dedizierte Vorschaufunktion für Videos, Rotationssets und Bildsets verwenden, Assets aber auch über von Ihnen erstellte Viewer-Vorgaben in der Vorschau anzeigen. Alternativ dazu können Sie auch Bildvorgaben verwenden, um Ausgabedarstellungen von Bildern anzuzeigen.

* [Anwenden von Bildvorgaben](/help/assets/image-presets.md)
* [Anwenden von Viewer-Vorgaben](/help/assets/viewer-presets.md)

>[!NOTE]
>
>Wenn Sie sich auf einer Web-Seite (Sites) in Adobe Experience Manager befinden, können Sie Assets im **Bearbeitungsmodus** nicht in der Vorschau anzeigen. Sie müssen in den Vorschaumodus wechseln, indem Sie oben rechts auf der Seite auf **[!UICONTROL Vorschau]** klicken.

Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

**So zeigen Sie eine Vorschau von Assets über die Software-Oberfläche an:**

1. Klicken Sie in **[!UICONTROL Adobe Experience Manager]** auf der Seite **[!UICONTROL Navigation]** auf **[!UICONTROL Assets]** und dann auf **[!UICONTROL Dateien]**, um auf Assets zuzugreifen.
1. Wählen Sie rechts oben auf der Seite in der Dropdown-Liste **[!UICONTROL Ansicht]** die Option **[!UICONTROL Listenansicht]** aus.
1. (Optional) Sortieren Sie in der Spalte **[!UICONTROL Typ]** die Assets nach dem Typ, den Sie in einer Vorschau anzeigen möchten.
1. Klicken Sie in der Spalte **[!UICONTROL Titel]** auf den Namen des Titels (nicht auf das Miniaturbild) des Assets, das Sie in der Vorschau anzeigen möchten.
1. Gehen Sie je nach ausgewähltem Asset wie folgt vor:


   <table>
    <tbody>
      <tr>
      <td><strong>Per Klick ausgewählter Asset-Typ</strong><br /> </td>
      <td><strong>Asset-Vorschau in bestimmter Ausgabedarstellung möglich?</strong></td>
      <td><strong>Asset-Vorschau in einem Viewer möglich?</strong></td>
      <td> </td>
      </tr>
      <tr>
      <td><p>3D</p> </td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines 3D-Assets im Dimensional-Viewer</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie in der Liste <strong>Viewer</strong> aus und wählen Sie dann den Dimensional-Viewer aus.</li>
      <li>Klicken Sie auf <strong>Zurücksetzen</strong>, wenn Sie das Bild zum ursprünglichen Zoom zurückführen möchten.</li>
      <li>Klicken Sie auf <strong>Vollbild</strong>, um den Viewer auf dem Anzeigegerät zu maximieren.</li>
      </ul>
      <p><strong>Navigieren in der 3D-Szene</strong></p>
      <ul>
      <li><p><strong>3D-Kamera drehen</strong>: Drehen Sie Ihre Ansicht in der 3D-Szene um die Objekte herum.</p> Maus: Klicken und ziehen Sie mit der linken Maustaste </p> Touchscreen: Drücken und ziehen Sie</p></li>
      <li><p><strong>Kamera schwenken</strong>: Schwenken Sie die Ansicht nach links, rechts, oben und unten.</p> Maus: Klicken und ziehen Sie mit der rechten Maustaste </p> Touchscreen: Drücken und ziehen Sie mit zwei Fingern</p></li>
      <li><p><strong>Kamera zoomen</strong>: Zoomen Sie Ihre Kamera, um sich in Bereiche in der 3D-Szene hinein- und herauszubewegen.</p> Maus: Scrollen Sie mit dem Mausrad </p> Touchscreen: Führen Sie mit den Fingern Pinch-Gesten aus</p></li>
      <li><p><strong>Kamera neu zentrieren</strong>: Drehen Sie Ihre Ansicht in der 3D-Szene um die Objekte herum.</p> Maus: Doppelklick </p> Touchscreen: Doppeltippen</li></ul></td>
      </tr>
      <tr>
      <td><p>Bild</p> </td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmter Ausgabedarstellung</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabedarstellungen</strong> und wählen Sie dann die Ausgabedarstellung, die Sie in einer Vorschau anzeigen möchten.</li>
      </ul> <p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie in der Liste <strong>Viewers</strong> den Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>–</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, wenn Sie das Bild zum ursprünglichen Zoom zurückführen möchten.<br /> Auf einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreichen, wählen Sie erneut das Bild doppelt aus, um den Zoom-Status zurückzusetzen. Ziehen Sie den Cursor über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Multimedia</td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmter Ausgabedarstellung</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabedarstellungen</strong> und wählen Sie dann die Ausgabedarstellung, die Sie in einer Vorschau anzeigen möchten.</li>
      </ul> <p>Wenn Sie eine Videoausgabedarstellung mit einer höheren Auflösung für die Vorschau auswählen, kann das Video abgeschnitten werden. Dies liegt daran, dass in der Vorschau der Ausgabedarstellung die genaue Auflösung angezeigt wird, die auch die Kunden sehen, und zwar im Kontext des eingebetteten Viewers, über den die Vorschau erfolgt.</p> <p>Wenn Sie die Vorschau eines adaptiven Videosets auf Asset-Ebene anzeigen, werden die Ausgabedarstellungen in ein Wiedergabeerlebnis zusammengefasst. Das heißt, das adaptive Video wird entsprechend für die Anzeige skaliert und mit der optimalen Auflösung im Kontext des Anzeigegeräts und der Verbindungsgeschwindigkeit wiedergegeben.<br /> </p> <p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie in der Liste <strong>Viewers</strong> den Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> </td>
      </tr>
      <tr>
      <td>Bildset</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie in der Liste <strong>Viewer</strong> aus. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>–</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, wenn Sie das Bild zum ursprünglichen Zoom zurückführen möchten.<br /> Auf einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreichen, wählen Sie erneut das Bild doppelt aus, um den Zoom-Status zurückzusetzen. Ziehen Sie den Cursor über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Rotationsset</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie in der Liste <strong>Viewers</strong> den Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>–</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, wenn Sie das Bild zum ursprünglichen Zoom zurückführen möchten.<br /> Auf einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreichen, wählen Sie erneut das Bild doppelt aus, um den Zoom-Status zurückzusetzen. Ziehen Sie den Cursor über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Gemischter Mediensatz</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie in der Liste <strong>Viewers</strong> den Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>–</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, wenn Sie das Bild zum ursprünglichen Zoom zurückführen möchten.<br /> Auf einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreichen, wählen Sie erneut das Bild doppelt aus, um den Zoom-Status zurückzusetzen. Ziehen Sie den Cursor über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Karussellsatz</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> </td>
      </tr>
      <tr>
      <td>360-Grad-Video<br /> </td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmter Ausgabedarstellung</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, sodass die Dropdown-Liste angezeigt wird. Wählen Sie <strong>Ausgabedarstellungen</strong> und dann die Ausgabedarstellung aus, die Sie in der Vorschau anzeigen möchten.</li>
      </ul> <p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, sodass die Dropdown-Liste angezeigt wird. Wählen Sie <strong>Viewer</strong> und dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>–</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, wenn Sie das Bild zum ursprünglichen Zoom zurückführen möchten.<br /> Auf einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreichen, wählen Sie erneut das Bild doppelt aus, um den Zoom-Status zurückzusetzen. Ziehen Sie den Cursor über das Bild, um es zu schwenken.</p> </td>
      </tr>
    </tbody>
    </table>

## Asset-Vorschau über eine Tastatur {#keyboard-navigation-asset-preview}

1. Navigieren Sie in der Assets-Benutzeroberfläche zu einem Ordner, der ein Asset enthält, das Sie in der Vorschau anzeigen möchten.

1. Drücken Sie im Ordner die Taste `<Tab>` oder Pfeiltasten auf der Tastatur, um das Asset auszuwählen.

1. Drücken Sie die `<Enter>`-Taste, um das ausgewählte Asset im Vorschaumodus zu öffnen.

1. Führen Sie einen der folgenden Schritte aus:

   * Drücken Sie zum Einzoomen die Taste `<Tab>`, um den Fokus auf das Zoom-Symbol (+) zu verschieben, und drücken Sie dann einmal oder mehrere Male die `<Enter>`-Taste, um schrittweise einzuzoomen.
   * Um herauszuzoomen, drücken Sie die Taste `<Tab>`, um den Fokus auf das Symbol zum Verkleinern (-) zu verschieben, und drücken Sie dann einmal oder mehrere Male die `<Enter>`-Taste, um schrittweise herauszuzoomen.
   * Um die Ansicht eines *gezoomten* Assets horizontal oder vertikal zu verschieben, drücken Sie die entsprechenden Pfeiltasten.
   * Drücken Sie `<Shift>` + `<Tab>`, um die Ansicht zurückzusetzen und den Fokus wieder auf das Asset zu legen.
