---
title: Entwickeln von Formularen (klassische Benutzeroberfläche)
description: Erfahren Sie, wie Sie Formulare für die klassische Benutzeroberfläche von Adobe Experience Manager entwickeln.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: d1475168-6625-4d27-9c3b-01e415c2f398
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '1930'
ht-degree: 99%

---

# Entwickeln von Formularen (klassische Benutzeroberfläche){#developing-forms-classic-ui}

Die grundlegende Struktur eines Formulars sieht wie folgt aus:

* Beginn des Formulars
* Elemente des Formulars
* Ende des Formulars

All diese Teile werden mit einer Reihe standardmäßiger [Formularkomponenten](/help/sites-authoring/default-components.md#form) realisiert, die in einer Standard-AEM-Installation verfügbar sind.

Neben der [Entwicklung neuer Komponenten](/help/sites-developing/developing-components-samples.md) für Ihre Formulare ist auch Folgendes möglich:

* [Ein Formular vorab mit Werten ausfüllen](#preloading-form-values)
* [(Bestimmte) Felder mit mehreren Werten vorab ausfüllen ](#preloading-form-fields-with-multiple-values)
* [Neue Aktionen entwickeln](#developing-your-own-form-actions)
* [Neue Einschränkungen entwickeln](#developing-your-own-form-constraints)
* [Bestimmte Formularfelder ein- oder ausblenden](#showing-and-hiding-form-components)

[Skripte verwenden](#developing-scripts-for-use-with-forms), um die Funktionalität bei Bedarf zu erweitern.

>[!NOTE]
>
>Dieses Dokument befasst sich hauptsächlich mit der Entwicklung von Formularen über die [Foundation-Komponenten](/help/sites-authoring/default-components-foundation.md) in der klassischen Benutzeroberfläche. Adobe empfiehlt, bei der Formularentwicklung in der Touch-optimierten Benutzeroberfläche die neuen [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) und [Ausblende-Bedingungen](/help/sites-developing/hide-conditions.md) zu nutzen.

## Vorabladen von Formularwerten {#preloading-form-values}

Die Formular-Start-Komponente stellt ein Feld für den **Ladepfad** bereit. Dies ist ein optionaler Pfad, der auf einen Knoten im Repository verweist.

Der Ladepfad ist der Pfad zu den Knoteneigenschaften, mit dem vordefinierte Werte in mehrere Felder im Formular geladen werden.

Dies ist ein optionales Feld, das den Pfad zu einem Knoten im Repository angibt. Wenn dieser Knoten Eigenschaften hat, die den Feldnamen entsprechen, werden die jeweiligen Felder im Formular vorab mit den Werten dieser Eigenschaften ausgefüllt. Wenn keine Übereinstimmung besteht, steht im Feld der Standardwert.

>[!NOTE]
>
>Eine [Formularaktion](#developing-your-own-form-actions) kann auch festlegen, von welcher Ressource die Anfangswerte geladen werden. Dies erfolgt mit `FormsHelper#setFormLoadResource` in `init.jsp`.
>
>Nur wenn dies nicht festgelegt ist, wird das Formular über den Pfad, den die Autorin oder der Autor in der Formular-Start-Komponente festgelegt hat, ausgefüllt.

### Vorabladen von Formularfeldern mit mehreren Werten {#preloading-form-fields-with-multiple-values}

Einige Formularfelder verfügen auch über einen **Element-Ladepfad**. Dies ist ein weiterer optionaler Pfad, der auf einen Knoten im Repository verweist.

Der **Element-Ladepfad** ist der Pfad zu Knoteneigenschaften, mit dem vordefinierte Werte in dieses Formularfeld geladen werden – z. B. eine [Dropdown-Liste](/help/sites-authoring/default-components-foundation.md#dropdown-list), eine [Gruppe von Kontrollkästchen](/help/sites-authoring/default-components-foundation.md#checkbox-group) oder eine [Gruppe von Optionsfeldern](/help/sites-authoring/default-components-foundation.md#radio-group).

#### Beispiel: Vorabladen einer Dropdown-Liste mit mehreren Werten {#example-preloading-a-dropdown-list-with-multiple-values}

Eine Dropdown-Liste kann mit Ihren zur Auswahl stehenden Werten konfiguriert werden.

Mit dem **Element-Ladepfad** kann auf eine Liste aus einem Ordner im Repository zugegriffen werden, die in das Feld geladen wird:

1. Erstellen Sie einen Sling-Ordner (`sling:Folder`),
z. B. `/etc/designs/<myDesign>/formlistvalues`.

1. Fügen Sie eine neue Eigenschaft (z. B. `myList`) des Typs mehrwertige Zeichenfolge (`String[]`) hinzu, die eine Liste der Dropdown-Elemente enthält. Sie können auch mithilfe eines Skripts Inhalte importieren, z. B. mit einem JSP-Skript oder cURL in einem Shell-Skript.

1. Verwenden Sie den vollständigen Pfad im Feld **Element-Ladepfad**.
Zum Beispiel `/etc/designs/geometrixx/formlistvalues/myList`

Hinweis: Wenn die Werte im `String[]` wie folgt formatiert sind:

* `AL=Alabama`
* `AK=Alaska`

generiert AEM die Liste wie folgt:

* `<option value="AL">Alabama</option>`
* `<option value="AK">Alaska</option>`

Diese Funktion kann beispielsweise in einer mehrsprachigen Umgebung nützlich sein.

### Entwickeln eigener Formularaktionen {#developing-your-own-form-actions}

Für ein Formular ist eine Aktion erforderlich. Die Aktion bestimmt den Vorgang, der ausgeführt wird, wenn das Formular mit Benutzerdaten übermittelt wird.

Mit einer AEM-Standardinstallation stehen verschiedene Aktionen zur Verfügung. Sie finden diese unter:

`/libs/foundation/components/form/actions`

und in der **Action Type**-Liste der **Formular**-Komponente:

![chlimage_1-8](assets/chlimage_1-8.png)

Dieser Abschnitt erläutert, wie Sie Ihre eigene Formularaktion entwickeln und zu dieser Liste hinzufügen können.

Sie können Ihre eigene Aktion wie folgt unter `/apps` hinzufügen:

1. Erstellen Sie einen Knoten des Typs `sling:Folder`. Geben Sie einen Namen an, der der zu implementierenden Aktion entspricht.

   Beispiel:

   `/apps/myProject/components/customFormAction`

1. Definieren Sie in diesem Knoten die folgenden Eigenschaften und klicken Sie anschließend auf **Alle speichern**, um Ihre Änderungen zu speichern:

   * `sling:resourceType`: als `foundation/components/form/action` festlegen

   * `componentGroup`: als `.hidden` definieren

   * Optional:

      * `jcr:title`: Geben Sie einen Titel Ihrer Wahl an, der in der Dropdown-Auswahlliste angezeigt wird. Wenn Sie dies nicht festlegen, wird der Name des Knotens angezeigt

      * `jcr:description`: Geben Sie eine Beschreibung Ihrer Wahl ein

1. Erstellen Sie im Ordner einen Dialogfeldknoten:

   1. Fügen Sie Felder hinzu, damit der Autor bzw. die Autorin das Formular-Dialogfeld bearbeiten kann, nachdem die Aktion ausgewählt wurde.

1. Im Ordner erstellen Sie entweder:

   1. Ein Postskript.
Der Name des Skripts lautet `post.POST.<extension>`, z. B. `post.POST.jsp`
Das Postskript wird aufgerufen, wenn ein Formular eingereicht wird, und verarbeitet es. Es enthält den Code, der die Daten aus dem Formular `POST` verarbeitet.

   1. Fügen Sie ein Weiterleitungsskript hinzu, das aufgerufen wird, wenn das Formular eingereicht wird.
Der Name des Skripts lautet `forward.<extension`>, z. B. `forward.jsp`
Dieses Skript kann einen Pfad definieren. Die aktuelle Anfrage wird dann an den angegebenen Pfad weitergeleitet.

   Der erforderliche Aufruf ist `FormsHelper#setForwardPath` (2 Varianten). Ein typischer Anwendungsfall besteht darin, eine Validierung oder Logik auszuführen, um den Zielpfad zu finden, und anschließend zu diesem Pfad weiterzuleiten. Dabei wird die Speicherung in JCR dem standardmäßigen Sling-POST-Servlet überlassen.

   Es kann auch ein weiteres Servlet verwendet werden, das die eigentliche Verarbeitung übernimmt. In diesem Fall stellen die Formularaktion und `forward.jsp` nur die Verbindung dar. Ein Beispiel dafür ist die E-Mail-Aktion unter `/libs/foundation/components/form/actions/mail`, die Details an `<currentpath>.mail.html` weiterleitet, wo sich ein E-Mail-Servlet befindet.

   Das bedeutet:

   * Ein `post.POST.jsp` eignet sich für kleine Vorgänge, die vollständig von der Aktion selbst ausgeführt werden.
   * `forward.jsp` ist hingegen hilfreich, wenn nur Delegation erforderlich ist.

   Die Skripte werden in folgender Reihenfolge ausgeführt:

   * Nach dem Rendering des Formulars ( `GET`):

      1. `init.jsp`
      1. Für alle Feldeinschränkungen: `clientvalidation.jsp`
      1. validationRT des Formulars: `clientvalidation.jsp`
      1. Das Formular wird über eine Laderessource geladen, wenn dies festgelegt ist
      1. `addfields.jsp` während des Renderings von `<form></form>`

   * Nach der Verarbeitung eines Formular-`POST`:

      1. `init.jsp`
      1. Für alle Feldeinschränkungen: `servervalidation.jsp`
      1. validationRT des Formulars: `servervalidation.jsp`
      1. `forward.jsp`
      1. Wenn ein Weiterleitungspfad festgelegt wurde (`FormsHelper.setForwardPath`), leiten Sie die Anfrage weiter und rufen Sie anschließend `cleanup.jsp` auf

      1. Wenn kein Weiterleitungspfad festgelegt wurde, rufen Sie `post.POST.jsp` auf (der Vorgang ist hier beendet, `cleanup.jsp` wird nicht aufgerufen)

1. Auch hier können Sie optional Folgendes zum Ordner hinzufügen:

   1. Ein Skript für das Hinzufügen von Feldern.
Der Name des Skripts lautet `addfields.<extension>`, z. B. `addfields.jsp`
Ein `addfields`-Skript wird unmittelbar nach dem Schreiben der HTML für den Formularstart aufgerufen. Dadurch kann die Aktion benutzerdefinierte Eingabefelder oder sonstigen HTML-Code in das Formular einfügen.

   1. Ein Initialisierungsskript.
Der Name des Skripts lautet `init.<extension>`, z. B. `init.jsp`
Dieses Skript wird aufgerufen, wenn das Formular gerendert wird. Es kann zur Initialisierung von handlungsspezifischen Elementen verwendet werden.

   1. Ein Bereinigungsskript.
Der Name des Skripts lautet `cleanup.<extension>`, z. B. `cleanup.jsp`
Dieses Skript kann für die Bereinigung verwendet werden.

1. Verwenden Sie die **Formularkomponente** in einem Absatzsystem. Das Dropdown-Menü **Aktionstyp** enthält nun Ihre neue Aktion.

   >[!NOTE]
   >
   >So zeigen Sie weitere Standardaktionen an, die im Produkt inbegriffen sind:
   >
   >
   >`/libs/foundation/components/form/actions`

### Entwicklung Ihrer eigenen Formulareinschränkungen {#developing-your-own-form-constraints}

Einschränkungen können auf zwei Ebenen angewendet werden:

* Für [einzelne Felder (siehe nachfolgendes Verfahren)](#constraints-for-individual-fields)
* als [globale Validierung für das Formular](#form-global-constraints)

#### Einschränkungen für einzelne Felder {#constraints-for-individual-fields}

Sie können wie folgt Ihre eigenen Einschränkungen für ein einzelnes Feld hinzufügen (unter `/apps`):

1. Erstellen Sie einen Knoten des Typs `sling:Folder`. Geben Sie einen Namen an, der der zu implementierenden Einschränkung entspricht.

   Beispiel:

   `/apps/myProject/components/customFormConstraint`

1. Definieren Sie in diesem Knoten die folgenden Eigenschaften und klicken Sie anschließend auf **Alle speichern**, um Ihre Änderungen zu speichern:

   * `sling:resourceType`: auf `foundation/components/form/constraint` festlegen

   * `constraintMessage`: Eine individuelle Nachricht, die beim Übermitteln des Formulars angezeigt wird, wenn das Feld gemäß der Einschränkung nicht gültig ist.

   * Optional:

      * `jcr:title`: Geben Sie einen Titel Ihrer Wahl an, der in der Auswahlliste angezeigt wird. Wenn Sie dies nicht festlegen, wird der Name des Knotens angezeigt
      * `hint`: zusätzliche Informationen für den Benutzer zur Verwendung dieses Felds

1. In diesem Ordner benötigen Sie möglicherweise auch die folgenden Skripte:

   * Ein Client-Validierungsskript:
Der Name des Skripts lautet `clientvalidation.<extension>`, z. B. `clientvalidation.jsp`.
Dieses Skript wird aufgerufen, wenn das Formularfeld gerendert wird. Es kann verwendet werden, um Client-JavaScript zur Validierung des Felds im Client zu erstellen.

   * Ein Server-Validierungsskript:
Der Name des Skripts lautet `servervalidation.<extension>`, z. B. `servervalidation.jsp`.
Dieses Skript wird beim Übermitteln des Formulars aufgerufen. Es kann verwendet werden, um das Feld auf dem Server zu validieren, nachdem das Formular übermittelt wurde.

>[!NOTE]
>
>Sie finden einige Beispiele für Einschränkungen unter:
>
>`/libs/foundation/components/form/constraints`

#### Globale Formulareinschränkungen {#form-global-constraints}

Legen Sie die globale Validierung eines Formulars fest, indem Sie einen Ressourcentyp in der Start-Formularkomponente angeben ( `validationRT`). Beispiel:

`apps/myProject/components/form/validation`

Anschließend können Sie Folgendes definieren:

* ein `clientvalidation.jsp`, das nach den Client-Validierungsskripten des Felds eingefügt wird
* und ein `servervalidation.jsp`, das auch nach den einzelnen Feld-Servervalidierungen bei einem `POST` aufgerufen wird.

### Ein- und Ausblenden von Formularkomponenten {#showing-and-hiding-form-components}

Sie können das Formular so konfigurieren, dass Formularkomponenten abhängig vom Wert anderer Formularfelder ein- oder ausgeblendet werden.

Das Ändern der Sichtbarkeit eines Formularfelds ist nützlich, wenn das Feld nur unter besonderen Bedingungen erforderlich ist. Auf einem Feedback-Formular werden Kunden beispielsweise gefragt, ob ihnen Produktinformationen per E-Mail zugesendet werden sollen. Nach der Auswahl von „Ja“ wird ein Textfeld eingeblendet, damit die Person die eigene E-Mail-Adresse eingeben kann.

Legen Sie mit dem Dialogfeld **Einblenden-/Ausblenden-Regeln bearbeiten** die Bedingungen fest, unter denen eine Formularkomponente ein- oder ausgeblendet wird.

![showhideeditor](assets/showhideeditor.png)

Legen Sie mit den Feldern, die im Dialogfeld oben sind, die folgenden Informationen fest:

* ob Sie Bedingungen zum Aus- oder Einblenden der Komponente festlegen
* ob eine oder alle Bedingungen erfüllt sein müssen, um die Komponente ein- oder auszublenden

Eine oder mehrere Bedingungen werden unter diesen Feldern eingeblendet. Eine Bedingung vergleicht den Wert einer anderen Formularkomponente (auf dem gleichen Formular) mit einem Wert. Wenn der tatsächliche Wert im Feld die Bedingung erfüllt, wird die Bedingung als wahr ausgewertet. Bedingungen enthalten die folgenden Informationen:

* den Titel des Formularfeldes, das geprüft wird
* einen Operator
* einen Wert, mit dem der Feldwert verglichen wird

Beispiel: eine Optionsfeldgruppen-Komponente mit dem Titel `Receive email notifications?`* * enthält die Optionsfelder `Yes` und `No`. Eine Textfeld-Komponente mit dem Titel `Email Address` verwendet die folgende Bedingung, damit sie sichtbar wird, wenn `Yes` ausgewählt wird:

![showhidecondition](assets/showhidecondition.png)

In JavaScript verweisen Bedingungen mit dem Wert der Eigenschaft „Elementname“ auf Felder. Im vorigen Beispiel ist `contact` der Wert der Eigenschaft „Elementname“ der Optionsfeldgruppen-Komponente. Der folgende Code entspricht dem JavaScript-Code für dieses Beispiel:

`((contact == "Yes"))`

**Ein- oder Ausblenden einer Formular-Komponente:**

1. Bearbeiten Sie die entsprechende Formular-Komponente.

1. Wählen Sie **Einblenden/Ausblenden** aus, um das Dialogfeld **„Regeln einblenden/ausblenden“ bearbeiten** zu öffnen:

   * Wählen Sie in der ersten Dropdown-Liste entweder **Einblenden** oder **Ausblenden** aus, um anzugeben, ob die Bedingungen das Einblenden oder das Ausblenden der Komponente bestimmen.

   * Wählen Sie in der Dropdown-Liste am Ende der obersten Zeile Folgendes aus:

      * **Alle**: Wenn alle Bedingungen wahr sein müssen, um die Komponente ein- oder auszublenden.
      * **Beliebig**: Wenn nur eine oder mehrere Bedingungen wahr sein müssen, um die Komponente ein- oder auszublenden.

   * Wählen Sie in der Bedingungszeile (als Standard wird nur eine gezeigt) eine Komponente und einen Operator aus und geben Sie einen Wert an.
   * Klicken Sie bei Bedarf auf **Bedingung hinzufügen**, um weitere Bedingungen hinzuzufügen.

   Beispiel:

   ![chlimage_1-9](assets/chlimage_1-9.png)

1. Klicken Sie auf **OK**, um die Definition zu speichern.

1. Nachdem Sie Ihre Definition gespeichert haben, wird in den Eigenschaften der Formularkomponente der Link **Regeln bearbeiten** neben der Option **Einblenden/Ausblenden** angezeigt. Klicken Sie auf diesen Link, um das Dialogfeld **Einblenden-/Ausblenden-Regeln bearbeiten** zu öffnen, damit Sie Änderungen vornehmen können.

   Klicken Sie auf **OK**, um alle Änderungen zu speichern.

   ![chlimage_1-10](assets/chlimage_1-10.png)

   >[!CAUTION]
   >
   >Sie können die Auswirkungen von Ein-/Ausblendedefinitionen überprüfen und testen:
   >
   >* im **Vorschaumodus** in der Autorenumgebung (Sie müssen die Seite neu laden, wenn Sie zum ersten Mal zur Vorschau wechseln)
   >
   >* in der Veröffentlichungsumgebung

#### Behandlung von nicht mehr gültigen Komponentenverweisen {#handling-broken-component-references}

Einblenden/Ausblenden-Bedingungen verweisen mit dem Wert der Eigenschaft „Elementname“ auf andere auf dem Formular befindliche Komponenten. Die Einblenden/Ausblenden-Konfiguration ist ungültig, wenn eine der Bedingungen auf eine Komponente verweist, die gelöscht oder bei der die Eigenschaft „Elementname“ geändert wurde. In diesen Fällen müssen Sie die Bedingungen manuell aktualisieren. Anderenfalls tritt beim Laden des Formulars ein Fehler auf.

Wenn die Einblenden/Ausblenden-Konfiguration ungültig ist, wird die Konfiguration nur als JavaScript-Code bereitgestellt. Bearbeiten Sie den Code, um die Probleme zu beheben. Der Code verwendet die Eigenschaft „Elementname“, mit der ursprünglich auf die Komponenten verwiesen wurde.

### Entwicklung von Skripten zur Verwendung mit Formularen {#developing-scripts-for-use-with-forms}

Weitere Informationen über die API-Elemente, die Sie zur Erstellung von Skripten verwenden können, finden Sie in den [javadocs zu Formularen](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/foundation/forms/package-summary.html).

Sie können dies z. B. verwenden, um einen Dienst aufzurufen, bevor das Formular übermittelt wird, und den Dienst abbrechen, wenn es fehlschlägt:

* Validierungs-Ressourcentyp definieren
* Aufnehmen eines Skripts zur Überprüfung:

   * Rufen Sie in der JSP den Webdienst auf und erstellen Sie ein Objekt `com.day.cq.wcm.foundation.forms.ValidationInfo` mit den Fehlermeldungen. Wenn Fehler auftreten, werden die Formulardaten nicht ausgegeben.
