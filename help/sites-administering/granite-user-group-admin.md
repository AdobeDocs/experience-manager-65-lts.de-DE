---
title: Granite-Vorgänge – Benutzer- und Gruppenverwaltung
description: Erfahren Sie mehr über die Benutzer- und Gruppenverwaltung in Granite.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
feature: Security
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: ba02f9d4-5286-41d6-995c-307d6e13431b
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 100%

---

# Granite-Vorgänge – Benutzer- und Gruppenverwaltung{#granite-operations-user-and-group-administration}

Da Granite die CRX-Repository-Implementierung der JCR-API-Spezifikation enthält, verfügt es über eine eigene Benutzer- und Gruppenverwaltung.

Diese Konten bilden die Grundlage der [AEM-Konten](/help/sites-administering/security.md). Sämtliche in der Granite-Verwaltung durchgeführten Kontoänderungen werden widergespiegelt, falls/wenn auf die Konten über die [AEM-Benutzerkonsole](/help/sites-administering/security.md#accessing-user-administration-with-the-security-console) (z. B. `http://localhost:4502/useradmin`) zugegriffen wird. In der AEM-Benutzerkonsole können Sie auch die Berechtigungen und andere AEM-Eigenschaften verwalten.

Die Konsolen für die Benutzer- und Gruppenverwaltung sind jeweils über die **[Tools](/help/sites-administering/tools-consoles.md)**-Konsole der Touch-optimierten Benutzeroberfläche verfügbar:

![Tools-Konsole](assets/chlimage_1-72a.png)

Durch Auswahl von **Benutzer** oder **Gruppen** in der Tools-Konsole wird die entsprechende Konsole geöffnet. In beiden können Sie Aktionen durchführen, indem Sie entweder das Kontrollkästchen und dann Aktionen aus der Symbolleiste verwenden oder indem Sie die Kontodetails über den Link unter **Name** aufrufen.

* [Benutzerverwaltung](#user-administration)

  ![chlimage_1-73](assets/chlimage_1-73a.png)

  In der **Benutzerkonsole** finden Sie:

   * den Benutzernamen;
   * den Anmeldenamen (Kontonamen) des Benutzers;
   * Titel, die dem Konto zugewiesen wurden.

* [Gruppenverwaltung](#group-administration)

  ![Benutzerverwaltungskonsole](assets/chlimage_1-74a.png)

  In der **Gruppenkonsole** finden Sie:

   * den Gruppennamen;
   * die Gruppenbeschreibung;
   * die Anzahl der Benutzenden/Gruppen in der Gruppe.

## Benutzerverwaltung {#user-administration}

### Hinzufügen von neuen Benutzenden {#adding-a-new-user}

1. Verwenden Sie das Symbol **Benutzer hinzufügen**:

   ![Symbol „Benutzer hinzufügen“](do-not-localize/chlimage_1-1.png)

1. Das Formular **Benutzer erstellen** wird geöffnet:

   ![Formular „Benutzerdetails“](assets/chlimage_1-75a.png)

   Hier können Sie die Benutzerdetails für das Konto eingeben (die meisten entsprechen dem Standard und sind selbsterklärend):

   * **ID**

     Dies ist die eindeutige Kennung des Benutzerkontos. Diese Angabe ist obligatorisch und darf keine Leerzeichen enthalten.

   * **E-Mail-Adresse**
   * **Kennwort**

     Ein Kennwort muss angegeben werden.

   * **Kennwortwdh.**

     Diese zur Bestätigung des Kennworts erforderliche Angabe ist obligatorisch.

   * **Vorname**
   * **Nachname**
   * **Telefonnummer**
   * **Berufsbezeichnung**
   * **Straße**
   * **Mobilgerät**
   * **Stadt**
   * **Postleitzahl**
   * **Land**
   * **Status**
   * **Titel**
   * **Geschlecht**
   * **Info**
   * **Kontoeinstellungen**

      * **Status**
Sie können das Konto sowohl als **aktiv** als auch als **inaktiv** markieren.

   * **Foto**

     Hier können Sie ein Foto für einen Avatar hochladen.

     Akzeptierte Dateitypen: `.jpg .png .tif .gif`

     Bevorzugte Größe: `240x240px`

   * **Benutzer zu Gruppen hinzufügen**

     Wählen Sie über die Auswahl-Dropdown-Liste die Gruppen aus, denen der Benutzer als Mitglied angehören soll. Vor dem Speichern können Sie ggf. eine getroffene Auswahl mit dem **X** neben dem Namen aufheben.

   * **Gruppen**

     Eine Liste der Gruppen, in denen der Benutzer derzeit Mitglied ist. Verwenden Sie das **X** neben dem Namen, um die Auswahl vor dem Speichern aufzuheben.

1. Wenn Sie das Benutzerkonto definiert haben, verwenden Sie:

   * **Abbrechen** zum Abbruch der Registrierung.
   * **Speichern**, um die Registrierung abzuschließen. Die Erstellung des Benutzerkontos wird mit einer Meldung bestätigt.

### Bearbeiten vorhandener Benutzer {#editing-an-existing-user}

1. Rufen Sie die Benutzerdetails über den Link unterhalb des Benutzernamens in der Benutzer-Konsole auf.

1. Sie können nun die Details wie unter [Hinzufügen neuer Benutzer](#adding-a-new-user) bearbeiten.

1. Rufen Sie die Benutzerdetails über den Link unterhalb des Benutzernamens in der Benutzer-Konsole auf.

1. Sie können nun die Details wie unter [Hinzufügen neuer Benutzer](#adding-a-new-user) bearbeiten.

### Ändern von Kennwörtern vorhandener Benutzer {#changing-the-password-for-an-existing-user}

1. Rufen Sie die Benutzerdetails über den Link unterhalb des Benutzernamens in der Benutzer-Konsole auf.

1. Sie können nun die Details wie unter [Hinzufügen neuer Benutzer](#adding-a-new-user) bearbeiten. Unter **Kontoeinstellungen** ist ein Link **Kennwort ändern** vorhanden.

   ![Dialogfeld „Konto-Einstellungen“](assets/chlimage_1-76a.png)

1. Das Dialogfeld **Kennwort ändern** wird geöffnet. Geben Sie das neue Kennwort, die Kennwortwiederholung und Ihr Kennwort ein. Bestätigen Sie die Änderungen mit **OK**.

   ![Dialog „Kennwort ändern“.](assets/chlimage_1-77a.png)

   Über eine Meldung wird bestätigt, dass das Kennwort geändert wurde.

### Schnelle Gruppenzuweisung {#quick-group-assignment}

1. Verwenden Sie das Kontrollkästchen, um einen oder mehrere Benutzende zu kennzeichnen.
1. Verwenden Sie das Symbol **Gruppen**:

   ![Verwenden des Gruppensymbols](do-not-localize/chlimage_1-2.png)

   Hierdurch wird die Dropdown-Liste für die Gruppenauswahl geöffnet:

   ![Gruppenauswahl](assets/chlimage_1-78a.png)

1. Im Auswahlfeld können Sie per Aus-/Abwahl festlegen, welchen Gruppen das Benutzerkonto angehören soll.

1. Wählen Sie eine der folgenden Optionen aus, nachdem Sie die Gruppen zugewiesen oder deren Zuweisung aufgehoben haben:

   * **Abbrechen** zum Verwerfen der Änderungen
   * **Speichern** zum Bestätigen der Änderungen

### Löschen vorhandener Benutzerdetails {#deleting-existing-user-details}

1. Verwenden Sie das Kontrollkästchen, um einen oder mehrere Benutzende zu kennzeichnen.
1. Löschen Sie Benutzerdetails mit dem Symbol **Löschen**:

   ![Löschen vorhandener Benutzerdetails](do-not-localize/chlimage_1-3.png)

1. Sie werden zum Bestätigen des Löschvorgangs aufgefordert. Daraufhin wird durch eine Meldung bestätigt, dass der Löschvorgang tatsächlich durchgeführt wurde.

## Gruppenverwaltung {#group-administration}

### Hinzufügen einer neuen Gruppe {#adding-a-new-group}

1. Verwenden Sie das Symbol „Gruppe hinzufügen“:

   ![Neue Gruppe hinzufügen](do-not-localize/chlimage_1-4.png)

1. Das Formular **Gruppe erstellen** wird geöffnet:

   ![Formular „Gruppendetails“](assets/chlimage_1-79a.png)

   Hier können Sie die Gruppendetails eingeben:

   * **ID**

     Dies ist die eindeutige Kennung der Gruppe. Diese Angabe ist obligatorisch und darf keine Leerzeichen enthalten.

   * **Name**

     Der Name für die Gruppe; dieser wird in der Gruppenkonsole angezeigt.

   * **Beschreibung**

     Eine Beschreibung der Gruppe.

   * **Mitglieder zu Gruppe hinzufügen**

     Wählen Sie über die Auswahl-Dropdown-Liste die Benutzer aus, die der Gruppe hinzugefügt werden sollen. Vor dem Speichern können Sie ggf. eine getroffene Auswahl mit dem **X** neben dem Namen aufheben.

   * **Gruppenmitglieder**

     Eine Liste der Benutzer in der Gruppe. Verwenden Sie das **X** neben dem Namen, um die Auswahl vor dem Speichern aufzuheben.

1. Wenn Sie die Gruppe definiert haben, verwenden Sie:

   * **Abbrechen** zum Abbruch der Registrierung.
   * **Speichern**, um die Registrierung abzuschließen. Die Erstellung der Gruppe wird mit einer Meldung bestätigt.

### Bearbeiten vorhandener Gruppen {#editing-an-existing-group}

1. Rufen Sie die Gruppendetails über den Link unterhalb des Gruppennamens in der Gruppenkonsole auf.

1. Sie können nun die Details wie unter [Hinzufügen neuer Gruppen](#adding-a-new-group) bearbeiten.

### Kopieren einer bestehenden Gruppe {#copying-an-existing-group}

1. Verwenden Sie das Kontrollkästchen, um eine Gruppe zu kennzeichnen.
1. Kopieren Sie Gruppendetails mit dem Symbol **Kopieren**:

   ![Kopieren einer bestehenden Gruppe](do-not-localize/chlimage_1-5.png)

1. Das Formular **Gruppeneinstellungen bearbeiten** wird geöffnet.

   Die Gruppenkennung entspricht der ursprünglichen, vorangestellt ist allerdings der Hinweis `Copy of`. Bearbeiten Sie diese ID, da sie keine Leerzeichen enthalten darf. Alle anderen Details bleiben gegenüber dem Original unverändert.

   Sie können nun die Details wie unter [Hinzufügen neuer Gruppen](#adding-a-new-group) bearbeiten.

### Löschen einer vorhandenen Gruppe {#deleting-an-existing-group}

1. Verwenden Sie das Kontrollkästchen, um eine oder mehrere Gruppen zu kennzeichnen.
1. Löschen Sie Gruppendetails mit dem Symbol **Löschen**:

   ![Löschen einer vorhandenen Gruppe](do-not-localize/chlimage_1-6.png)

1. Sie werden zum Bestätigen des Löschvorgangs aufgefordert. Daraufhin wird durch eine Meldung bestätigt, dass der Löschvorgang tatsächlich durchgeführt wurde.
