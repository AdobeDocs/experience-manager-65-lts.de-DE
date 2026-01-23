---
title: Versionshinweise für  [!DNL Adobe Experience Manager] .6.5 LTS SP1
description: Hier finden Sie Versionsinformationen, Neuigkeiten, Installationsanleitungen und eine detaillierte Änderungsliste für  [!DNL Adobe Experience Manager] .6.5 LTS SP1
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: 811fccbc-6f63-4309-93c8-13b7ace07925
source-git-commit: c13c6c3d5511a5355570e999e378e4bdf0d7a88f
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 3%

---


# Versionshinweise zu Adobe Experience Manager (AEM) Forms 6.5 LTS SP1 on JEE

## Versionshinweise

| **Produkt** | Adobe Experience Manager Forms |
| -------------------- | ------------------------------------ |
| **Version** | 6.5 LTS SP1 |
| **Typ** | Long-Term Support Service Pack (JEE) |
| **Versionskategorie** | Upgrade-Version |
| **URL herunterladen** | Software Distribution |

## Was in [!DNL Experience Manager] 6.5 LTS SP1 enthalten ist {#what-is-included-in-aem-65ltssp1}

Adobe Experience Manager (AEM) Forms **6.5 LTS SP1 on JEE** bietet neue Funktionen, wichtige von Kundschaft angeforderte Plattformaktualisierungen und allgemeine Fehlerbehebungen, wobei der Schwerpunkt auf Produktstabilität und langfristigem Support liegt.

## Was in AEM Forms 6.5 LTS SP1 enthalten ist

### &#x200B;1. Aktualisierungen der Java-Unterstützung

Unterstützung für neuere Java-Versionen wurde eingeführt:

* **Java™ 17**
* **Java™ 21**

### &#x200B;2. Updates für die Unterstützung des Anwendungsservers

#### JBoss EAP 8-Unterstützung

* Unterstützung für **JBoss EAP 8** wurde hinzugefügt.
* Das alte **PicketBox**-Sicherheits-Framework wurde entfernt.
* **Elytron-basierte Berechtigungsspeicher** werden jetzt für die sichere Verwaltung von Berechtigungen unterstützt.

##### Konfiguration: Berechtigungsspeicher (auf Elytron-Basis)

AEM Forms auf JBoss EAP 8 verwendet Elytron für die Verwaltung sicherer Anmeldeinformationen. Kunden müssen einen auf Elytron basierenden Berechtigungsspeicher konfigurieren, um einen erfolgreichen Serverstart und eine sichere Datenbankauthentifizierung sicherzustellen.

Weitere Informationen zur Konfiguration finden Sie im Installations- und Konfigurationshandbuch.

### &#x200B;3. Änderungen an Plattform und Kompatibilität

#### Unterstützung der Servlet-Spezifikation

* Unterstützung für **Servlet-Spezifikation 5+**
* Auf der Grundlage der **Jakarta EE 9**-Konformität

#### Namespace-Migrationsanforderung

* Jakarta EE 9 führt eine Namespace-Änderung von `javax.*` zu `jakarta.*` ein
* Alle **benutzerdefinierten DSCs** müssen in den `jakarta.*`-Namespace migriert werden
* AEM Forms 6.5 LTS SP1 unterstützt **nur Jakarta EE 9+-basierte Anwendungsserver**

Weitere Informationen finden Sie unter **Migration von Java zum Jakarta-Namespace**.

## Aktualisieren

Detaillierte Aktualisierungsanweisungen finden Sie im [Aktualisierungshandbuch für AEM Forms 6.5 LTS SP1 on JEE](https://experienceleague.adobe.com/en/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade)

## Installation

Informationen zu den Installationsschritten und Voraussetzungen finden Sie im **Installationshandbuch für AEM Forms 6.5 LTS SP1 (JEE)**.

## Unterstützte Plattformen

Eine vollständige Liste der unterstützten Plattformen, Betriebssysteme, Datenbanken und Anwendungs-Server finden Sie unter:

**Matrix der unterstützten Plattformen - AEM Forms 6.5 LTS SP1 (JEE)**

## Veraltete und entfernte Funktionen

* Die Unterstützung für **RDBMK** für die Persistenz des CRX-Repositorys wurde entfernt.
* Für Cluster-Umgebungen wird **nur MongoMK** für die Repository-Persistenz unterstützt.

## Migration von Java zum Jakarta-Namespace

### Migration von `javax` zu `jakarta` Namespace

Ab **AEM Forms 6.5 LTS SP1** werden nur Anwendungsserver unterstützt, die **Jakarta Servlet API 5/6** implementieren. Mit **Jakarta EE 9 und höher** wechselten alle APIs vom `javax.{}`-Namespace zum `jakarta.`.

Daher müssen **benutzerdefinierten DSCs den `jakarta` Namespace verwenden**. Benutzerdefinierte Komponenten, die mit `javax.{}` APIs erstellt wurden **sind mit** unterstützten Anwendungsservern nicht kompatibel.

### Migrationsoptionen für benutzerdefinierte DSCs

Sie können vorhandene benutzerdefinierte DSCs mit einem der folgenden Ansätze migrieren:

#### Option 1: Source-Code-Migration (empfohlen)

* Alle Importanweisungen von `javax.{}` nach `jakarta.` aktualisieren
* Erstellen Sie die benutzerdefinierten DSC-Projekte neu und kompilieren Sie sie erneut
* Stellen Sie die aktualisierten Komponenten erneut auf dem Anwendungsserver bereit

**Vorteile:**

* Stellt langfristige Kompatibilität mit Jakarta EE 9+ sicher
* Am besten geeignet für aktiv gepflegte Projekte

#### Option 2: Binäre Migration mit Eclipse Transformer

* Verwenden Sie das **Eclipse Transformer**-Tool, um kompilierte Binärdateien (`.jar`, `.war`) von `javax` in `jakarta` zu konvertieren
* Keine Quellcodeänderungen oder Neukompilierung erforderlich
* Stellen Sie die umgewandelten Binärdateien erneut auf dem Anwendungsserver bereit

>[!NOTE]
>
> Die Binärtransformation wird auf der **Bytecode-Ebene** durchgeführt.

Beispiele für Importzuordnungen

Im Folgenden finden Sie gängige Beispiele für Namespace-Änderungen, die während der Migration erforderlich sind:

Vorher (javax)    Nach (Jakarta)
javax.servlet.*    jakarta.servlet.*
javax.servlet.http.*    jakarta.servlet.http.*

### Beispiele für Importzuordnungen

Die folgende Tabelle zeigt allgemeine Namespace-Änderungen, die bei der Migration von `javax` zu `jakarta` erforderlich sind:

| Vorher (`javax`) | Nach (`jakarta`) |
| ---------------------- | ------------------------ |
| `javax.servlet.*` | `jakarta.servlet.*` |
| `javax.servlet.http.*` | `jakarta.servlet.http.*` |

Verwenden Sie diese Zuordnungen als Referenz beim Aktualisieren von benutzerdefiniertem DSC-Quell-Code oder beim Überprüfen umgewandelter Binärdateien.

