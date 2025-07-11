---
title: Einrichten des Visual Studio-Projekts und Erstellen der Windows-App
description: Erfahren Sie, wie Sie ein Visual Studio-Projekt einrichten können, um die AEM Forms-App für Windows-Mobilgeräte zu erstellen.
topic-tags: forms-app
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: c2e9200f-a4b7-46fc-9dde-425329e5365d
source-git-commit: b8576049fba41b3bec16046316938274a5046513
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 100%

---

# Einrichten des Visual Studio-Projekts und Erstellen des Windows-Programms{#set-up-the-visual-studio-project-and-build-the-windows-app}

In AEM Forms wird der vollständige Quell-Code des AEM Forms-Programms bereitgestellt. Die Quelle enthält alle Komponenten, die für ein benutzerdefiniertes Arbeitsbereich-Programm erforderlich sind. Das Quell-Code-Archiv `adobe-lc-mobileworkspace-src-<version>.zip` ist Bestandteil des `adobe-aemfd-forms-app-src-pkg-<version>.zip`-Pakets auf Software Distribution.

Um die Quelle des AEM Forms-Programms zu erhalten, führen Sie die folgenden Schritte aus:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Wählen Sie im Kopfzeilenmenü **[!UICONTROL Adobe Experience Manager]** aus.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** aus.
   2. Wählen Sie die Version aus und geben Sie sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Wählen Sie den für Ihr Betriebssystem zutreffenden Paketnamen, dann **[!UICONTROL EULA-Bedingungen akzeptieren]** und dann **[!UICONTROL Herunterladen]** aus.
1. Öffnen Sie [Package Manager](/help/sites-administering/package-manager.md) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um das Quell-Code-Archiv herunterzuladen, öffnen Sie `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` in Ihrem Browser.\
   Das Quellpaket wird auf Ihr Gerät heruntergeladen.

Die folgende Abbildung zeigt den extrahierten Inhalt von `adobe-lc-mobileworkspace-src-<version>.zip`.

![mws-content-1](assets/mws-content-1.png)

Die folgende Abbildung zeigt die Verzeichnisstruktur des Ordners `windows` im Ordner `src` an.

![win-dir](assets/win-dir.png)

## Einrichten der Umgebung {#setting-up-the-environment}

Für Windows-Geräte benötigen Sie Folgendes:

* Microsoft Windows 8.1 oder Windows 10
* Microsoft® Visual Studio 2015
* Microsoft® Visual Studio-Tools für Apache Cordova

## Einrichten des Visual Studio-Projekts für die AEM Forms-App {#setting-up-visual-studio-project-for-aem-forms-app}

Führen Sie folgende Schritte aus, um das AEM Forms-App-Projekt in Visual Studio einzurichten:

1. Kopieren Sie das Archiv `adobe-lc-mobileworkspace-src-<version>.zip` in den Ordner `%HOMEPATH%\Projects` auf dem Windows 8.1- oder Windows 10-Gerät mit installiertem und konfiguriertem Visual Studio 2015.
1. Entpacken Sie das Archiv in das Verzeichnis `%HOMEPATH%\Projects\MobileWorkspace`.
1. Wechseln Sie in das Verzeichnis `%HOMEPATH%\Projects\MobileWorkspace\adobe-lc-mobileworkspace-src-[versionsrc]\windows`.
1. Öffnen Sie die Datei `CordovaApp.sln` in Visual Studio 2015 und erstellen Sie das AEM Forms-Programm.

## Erstellen der AEM Forms-App {#build-aem-forms-app}

Führen Sie die folgenden Schritte aus, um die AEM Forms-App zu erstellen und bereitzustellen.

>[!NOTE]
>
>Im Windows-Dateisystem für die AEM Forms-App gespeicherte Daten werden nicht verschlüsselt. Es wird empfohlen, zum Verschlüsseln von Festplattendaten ein Tool eines Drittanbieters, wie etwa die BitLocker-Laufwerkverschlüsselung von Windows, zu verwenden.

1. Wählen Sie in der Visual Studio-Standardsymbolleiste in der Dropdown-Liste für den Build-Modus die Option **Release** aus.

1. Wählen Sie je nach Ihrer Plattform „Windows-AnyCPU“, „Windows-x64“ oder „Windows-x86“ aus. Empfohlen wird „Windows-AnyCPU“.
1. Klicken Sie im Visual Studio Solution Explorer mit der rechten Maustaste auf das Projekt **CordovaApp.Windows** und wählen Sie **Store > Create AppPackages**.

   ![createappackages](assets/createapppackages.png)

   Der Assistent zum Erstellen der Programmpakete wird angezeigt.

   Die Installationsprogrammdatei CordovaApp.Windows_3.0.2.0_anycpu.appx wird im Ordner platforms\windows\AppPackages\CordovaApp.Windows_3.0.2.0_anycpu_Test erstellt.

   Wenn der Fehler `Retarget to windows 8.1 required` auftritt, klicken Sie mit der rechten Maustaste auf den Fehler und wählen Sie im Popup-Menü **Neu auf Windows 8.1** aus.

   ![retarget-solution](assets/retarget-solution.png)

1. Wählen Sie im Assistenten zum Erstellen von Programmpaketen, ob Sie Ihr Programm in den Windows Store hochladen möchten, und klicken Sie dann auf **Weiter**.

   ![createapppackageswizard1](assets/createapppackageswizard1.png)

1. Nehmen Sie Änderungen an den Parameter wie der Version und dem Ausgabespeicherort des Programm-Builds vor wie benötigt.

   ![createapppackageswizard2](assets/createapppackageswizard2.png)

1. Nach Erstellung des Projekts können Sie die App mit folgenden Programmen installieren:

   * Windows PowerShell
   * Visual Studio

   Das `.appx`-Paket erfordert für eine erfolgreiche Installation folgende Elemente:

   1. WinJS-Bibliothek
   1. Stellen Sie sicher, dass das Paket mit einem selbstsignierten Zertifikat oder einem von einer vertrauenswürdigen Stelle signierten öffentlichen Zertifikat, wie etwa VeriSign, geliefert wird.
   1. Entwicklerlizenz

   Der Ordner „Platforms\windows\AppPackages\CordovaApp.Windows_3.0.2.0_anycpu_Test“ enthält vier Hauptkomponenten:

   1. Datei `.appx`
   1. Zertifikat (derzeit ein selbstsigniertes Zertifikat von Apache Cordova)
   1. Abhängigkeitsordner
   1. PowerShell-Datei (.ps1-Erweiterung)

## Bereitstellen einer App mit Windows PowerShell {#deploying-an-app-using-windows-powershell}

Es gibt zwei Möglichkeiten zum Installieren der Anwendung auf einem Windows-Gerät.

### Erwerb der Entwicklerlizenz {#by-acquiring-the-developer-license}

1. Klicken Sie mit der rechten Maustaste auf die PowerShell-Datei (`Add-AppDevPackage.ps1)` und wählen Sie **Ausführen mit PowerShell**.

1. Bei der Einrichtung werden Sie dazu aufgefordert, eine Entwicklerlizenz zu erwerben.  Verwenden Sie die Microsoft-Kontoanmeldeinformationen zum Erwerben der Entwicklerlizenz.\
   Diese Lizenz ist für 30 Tage gültig und Sie können Sie kostenlos verlängern.
1. Wenn Sie die Entwicklerlizenz erwerben, installiert das Setup-Programm das selbstsignierte Zertifikat auf dem System und die Anwendung wird erfolgreich installiert.

### Verwenden von unternehmenseigenen Geräten {#by-using-enterprise-owned-devices}

Für unternehmenseigene Geräte, die in die Unternehmens-Domain eingebunden sind, ist der Erwerb einer Entwicklerlizenz nicht erforderlich.

Unternehmenseigene Geräte verwenden die Professional und Enterprise Edition von Windows.

Microsoft empfiehlt das Installieren eines von einer vertrauenswürdigen Stelle ausgestellten öffentlichen Zertifikats, wie etwa VeriSign.

So stellen Sie das Programm bereit:

* Stellen Sie sicher, dass das Gerät in die Unternehmens-Domain eingebunden ist.
* Aktivieren Sie die Gruppenrichtlinien-Einstellung.

**So aktivieren Sie die Gruppenrichtlinien-Einstellung:**

1. Führen Sie auf Ihrem Gerät `gpedit.msc` aus.
1. Navigieren Sie zu **Computerkonfiguration > Administrative Vorlagen > Windows-Komponente > Bereitstellung von App-Paketen**.
1. Klicken Sie mit der rechten Maustaste auf **Installation aller vertrauenswürdigen Apps zulassen**.
1. Klicken Sie auf **Bearbeiten** und wählen Sie **Aktiviert**.

1. Klicken Sie auf **OK**.

Bearbeiten Sie das von Visual Studio generierte PowerShell-Skript, um zu verhindern, dass eine Entwicklerlizenz erworben wird.

Legen Sie die Variable im PowerShell-Skript wie folgt fest: `$NeedDeveloperLicense = $false`.

Für Geräte, die nicht in die Domain eingebunden sind, ist ein Querladen des Produktaktivierungsschlüssels erforderlich. Diesen können Sie von einem Windows-Fachhändler erwerben.

Für die Windows 8.1 Home Edition gibt es keine Gruppenrichtlinie, ein Querladen innerhalb des Unternehmens ist nicht zulässig und Sie können sie nicht in die Unternehmens-Domain einbinden. Stellen Sie die App mithilfe der Entwicklerlizenz auf einem Gerät mit Windows 8.1 Home Edition bereit.

Klicken Sie [hier](https://blogs.msdn.com/b/mvpawardprogram/archive/2014/03/24/side-loading-deployment-of-windows-store-apps-in-enterprises-step-by-step.aspx), um weitere Informationen zu erhalten.

## Bereitstellen einer App mit Visual Studio {#deploying-an-app-using-visual-studio}

Installieren der App mit Visual Studio unter Windows:

1. Verbinden Sie das Gerät mithilfe des Remote-Debuggers.\
   Weitere Informationen finden Sie unter [Ausführen von Windows Store-Apps auf einem Remote-Computer](https://docs.microsoft.com/de-de/visualstudio/debugger/run-windows-store-apps-on-a-remote-machine).

1. Wählen Sie, während Sie die App in Visual Studio geöffnet haben, in der Liste der Lösungsplattformen Windows-x64, Windows-x86 oder Windows-AnyCPU und anschließend **Remotecomputer** aus.
1. Ihre App wird auf dem Remote-Computer bereitgestellt.
