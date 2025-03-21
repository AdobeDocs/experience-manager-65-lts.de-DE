---
title: Konfigurieren der Speicherorte für Forms
description: Erfahren Sie, wie Sie einen Speicherort für AEM Forms konfigurieren. Sie können die Dateispeicherorte des Attributs, den Speicherort des Formulars, die Seed-PDF-Datei und den Cache-Speicherort angeben.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 49e815e9-2087-4a42-b481-dc66de787d67
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 100%

---

# Konfigurieren der Speicherorte für Forms {#configuring-locations-for-forms}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Sie können die URL-, URI- und Dateispeicherorte von Attributen wie dem Web-Stamm sowie den Speicherort der abzurufenden Formulare und die bei PDF-Transformationen verwendete Seed-PDF-Datei und den Cache-Speicherort angeben.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Formulare“.
1. Geben Sie unter „Speicherorte“ die entsprechenden Optionen an. Die Optionen werden nachfolgend beschrieben.
1. Klicken Sie auf Speichern.

## Speicherorteinstellungen {#locations-settings}

**Basis-URL:** Die Basis-URL, an der sich Formularressourcen, z. B. Bilder und Skripte, befinden. Dieser Wert ist für HTML-Transformationen erforderlich, die HREF-Verweise auf externe Abhängigkeiten enthalten, wie z. B. Bilder oder Skripte. Ein solches Skript ist „xfasubset.js“, das erforderlich ist, damit HTML-Formulare intelligente XFA-Funktionen ausführen können. Dieser Wert muss die HTTP-Entsprechung des Inhaltsstamm-URI sein.

>[!NOTE]
>
>Basis-URL unterstützt nur HTTP- oder Repository-Protokolle. Protokolle wie „file:///“ werden nicht unterstützt. Wenn Sie auf eine Ressource wie ein benutzerdefiniertes CSS oder ein URI für eine digitale Signatur zugreifen müssen, verwenden Sie den entsprechenden API-Parameterwert zur Angabe des absoluten Speicherorts.

Wenn ein Abhängigkeitspfad absolut ist, wird der Basis-URL-Wert ignoriert. Andernfalls wird der Abhängigkeitspfad mit der Basis-URL kombiniert.

 Der Standardwert ist eine leere Zeichenfolge.

Das folgende Beispiel verweist auf denselben Inhalt (unter Verwendung des Inhaltsstamm-URI und der Basis-URL):

`(ContentRootURI)/subdir/image1.jpg`

`(BaseURL)/subdir/image1.jpg`

**FS-Webstamm-URI:** Die URL der Forms-Webanwendung. Sie können dieses Feld leer lassen, wenn die Forms-Web-Anwendung und die Client-Anwendung auf demselben Anwendungs-Server bereitgestellt werden. Die Web-Stamm-URL der Forms-API wird verwendet.

Wenn die Forms-Web-Anwendung und die Client-Anwendung nicht auf demselben Anwendungs-Server bereitgestellt werden, geben Sie die URL für die Forms-Web-Anwendung in dieses Feld ein, wie im folgenden Beispiel gezeigt:

`https://<host name>:<port>/FormServer`

 `host name`und `port` sind der Server-Name bzw. die Port-Nummer des Servers, der als Host der Forms-Webanwendung dient.

 Der Standardwert ist eine leere Zeichenfolge.

**Webstamm-URI:** Der Webstamm des Programms. Dieser Wert wird mit dem sTargetURL-Parameter (wenn sTargetURL relativ angegeben ist) kombiniert, der über das AEM Forms SDK angegeben wird, um eine absolute URL für den Zugriff auf anwendungsspezifische Webinhalte zu erzeugen.

 Der Standardwert ist eine leere Zeichenfolge.

**Inhaltsstamm-URI:** Der URI oder der absolute Speicherort, von dem Formulare abgerufen werden. Dieser Wert wird mit dem sFormQuery-Parameter kombiniert, der über die API angegeben wird, um den absoluten Pfad zu dem Formular zu erzeugen, das abgerufen wird. Dieser Wert kann auf einen Ordner oder einen Web-Speicherort verweisen, auf den über HTTP zugegriffen werden kann.

 Der Standardwert ist eine leere Zeichenfolge.

**XCI-Konfigurationsdatei-URI:** Der relative oder absolute Speicherort, an dem sich die für die Wiedergabe verwendete XCI-Konfigurationsdatei befindet. Bei einem relativen Wert wird vorausgesetzt, dass sich die XCI-Datei in der bereitstellbaren AEM Forms-EAR-Datei befindet. 

Der Standardwert ist `com/adobe/formServer/PA/pa.xci`.

**Schriftzuordnungs-URI:** Der relative oder absolute Speicherort der Schriftzuordnungsdatei. Bei einem relativen Wert wird vorausgesetzt, dass sich diese Datei in der von AEM Forms bereitstellbaren EAR-Datei befindet.

Die Schriftzuordnungsdatei wird verwendet, um benutzerdefinierte Schriftartzuordnungen für HTML-Transformationen in Formularen zu erstellen. Auf diese Weise können Sie angeben, welche Schriftart ersetzt wird, wenn eine Schriftart auf dem Client-Computer nicht verfügbar ist.

Der Standardwert ist `com/adobe/formServer/client-font-map.properties`.

Im Folgenden finden Sie ein Beispiel für einen Eintrag in der Schriftartzuordnungsdatei: 

`Arial=Arial,Helvetica,sans-serif`

**Seed-PDF-Datei:** Die anfängliche PDF-Datei, die bei einer PDFForm-Transformation zur Optimierung der Übermittlung verwendet wird. Die Seed-PDF-Datei gibt eine angepasste PDF-Datei an (die nur XFA-Stream-, Bild- und Schriftartressourcen enthält), die an den Formularentwurf und die Daten angehängt wird. Das Formular wird von Acrobat 7 oder höher wiedergegeben und gilt für die PDFForm-Transformation.

Der Standardwert ist eine leere Zeichenfolge.

**Cache-Speicherort:** Gibt den Speicherort des Forms-Datenträger-Cache an. Nachdem Sie diese Einstellung geändert haben, werden alle vorhandenen Cache-Informationen am aktuellen Speicherort zurückgesetzt und es wird ein neuer Cache am neuen Speicherort erstellt. Wählen Sie eine der folgenden Optionen aus:

**Standardspeicherort:** Dies ist die Standardauswahl. Wenn diese Option ausgewählt ist, wird der Zwischenspeicher an einem Speicherort erstellt, der von dem von Ihnen verwendeten Anwendungsserver abhängig ist:

* **JBoss:** [JBoss-Startseite]\server\[install type]\svcdata\FormServer\Cache
* **WebLogic:** [WebLogic-Startseite]\user_projects\domains\[AEM Forms-Domain-Name]\adobe\[Name des Formular-Servers]\FormServer\Cache
* **WebSphere:** [IBM Home]\WebSphere\AppServer\installedApps\adobe\server1\FormServer\Cache

**Temporärer LC-Ordner:** Der Zwischenspeicher wird in einem Unterordner des temporären Ordners von AEM Forms erstellt, der in der Administration-Console unter „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“ > „Speicherort des temporären Verzeichnisses“ angegeben ist. Der Unterordner heißt adobeform_[Servername].

>[!NOTE]
>
>Wenn Sie ein Bereinigungsprogramm für temporäre Dateien verwenden, hat das Löschen dieser Ordner zwar keine Auswirkungen auf die Funktionalität, die Leistung kann jedoch kurzzeitig erheblich beeinträchtigt werden, bis der neue Cache erstellt wurde. Um dieses Problem zu vermeiden, sollten Sie diese Ordner nicht löschen, während die temporären Ordner von AEM Forms gelöscht werden.
