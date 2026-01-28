---
title: Upgrades von Code und Anpassungen
description: Erfahren Sie mehr über Code-Aktualisierungen und Benutzerdefinitionen in AEM.
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 6b94caf1-97b7-4430-92f1-4f4d0415aef3
source-git-commit: c1935b95d4e9e8e3773f2ff9825c759f97738304
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 48%

---

# Upgrades von Code und Anpassungen{#upgrading-code-and-customizations}

Bei der Planung eines Upgrades müssen die folgenden Bereiche einer Implementierung untersucht und berücksichtigt werden.

* [Upgrade der Code-Basis](#upgrade-code-base)
* [Testverfahren](#testing-procedure)

## Übersicht {#overview}

1. **AEM Analyzer** - Führen Sie AEM Analyzer aus, wie in der Upgrade-Planung und auf der Seite &quot;[&#x200B; der Upgrade-Komplexität mit AEM Analyzer“ &#x200B;](/help/sites-deploying/aem-analyzer.md) beschrieben. Sie erhalten einen AEM Analyzer-Bericht, der weitere Details zu Bereichen enthält, die zusätzlich zu den nicht verfügbaren APIs/Bundles in der Zielversion von AEM behandelt werden müssen. Der AEM Analyzer-Bericht liefert einen Hinweis auf alle Inkompatibilitäten in Ihrem Code. Wenn keine vorhanden ist, ist Ihre -Bereitstellung bereits mit 6.5 LTS kompatibel. Sie können für die Verwendung der 6.5 LTS-Funktionen weiterhin neue Entwicklungsschritte ausführen. Aus bloßen Kompatibilitätsgründen ist dies jedoch nicht erforderlich.
1. **Entwickeln einer Code-Basis für 6.5 LTS**- Erstellen Sie eine dedizierte Verzweigung oder ein dediziertes Repository für die Code-Basis der Zielversion. Nutzen Sie bei der Kompatibilitätsprüfung die vor dem Upgrade erfassten Daten, um die Code-Bereiche zu planen, die aktualisiert werden sollen.
1. **Kompilieren mit 6.5 LTS Uber jar**- Aktualisieren Sie die POMs der Code-Basis, sodass sie auf 6.5 LTS uber jar verweisen, und kompilieren Sie Code dagegen.
1. **Bereitstellung in der 6.5 LTS-Umgebung** - Eine neue Instanz von AEM 6.5 LTS (Autor und Veröffentlichung) sollte in einer Entwicklungs-/QS-Umgebung bereitgestellt werden. Stellen Sie die aktualisierte Code-Basis und ein repräsentatives Inhaltsbeispiel (aus der aktuellen Produktion) bereit.
1. **QS-Validierung und Fehlerbehebung** - Die Anwendung muss auf der Autoren- und Veröffentlichungsinstanz von 6.5 LTS mit QS validiert werden. Alle gefundenen Fehler sollten behoben und in die 6.5 LTS Code-Basis übertragen werden. Wiederholen Sie den Entwicklungszyklus bei Bedarf, bis alle Fehler behoben sind.

Bevor Sie mit dem Upgrade fortfahren, sollten Sie über eine stabile Anwendungs-Code-Basis verfügen, die sorgfältig gegen AEM 6.5 LTS getestet wurde.

## Upgrade der Code-Basis {#upgrade-code-base}

### Erstellen einer dedizierten Verzweigung für 6.5 LTS-Code in der Versionskontrolle {#create-a-dedicated-branch-for-6.5-lts-code-in-version-control}

Sämtlicher Code und alle Konfigurationen, die für Ihre AEM Implementierung erforderlich sind, sollten mit einer Versionskontrolle verwaltet werden. Es sollte eine dedizierte Verzweigung in der Versionskontrolle erstellt werden, um alle Änderungen zu verwalten, die für die Code-Basis in der Zielversion von AEM erforderlich sind. Iterative Tests der Code-Basis mit der Zielversion von AEM und nachfolgenden Fehlerbehebungen werden in dieser Verzweigung verwaltet.

### Aktualisieren der UberJar-Version von AEM {#update-the-aem-uber-jar-version}

AEM-UberJar beinhaltet alle AEM-APIs als einzelne Abhängigkeiten in der Datei `pom.xml` des Maven-Projekts. Es empfiehlt sich immer, das Uber Jar als einzelne Abhängigkeit einzubeziehen, anstatt einzelne AEM API-Abhängigkeiten einzubeziehen. Ändern Sie beim Upgrade der Code-Basis die Version von Uber Jar so, dass sie auf die Version 6.5 LTS von AEM verweist. Aktualisieren Sie alle veralteten APIs oder Methoden, damit sie mit der Zielversion von AEM kompatibel sind. Kompilieren Sie die Code-Basis neu mit der neuen Version von UberJar.

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>Es gibt einen geringfügigen Unterschied beim Verpacken von AEM 6.5- und AEM 6.5 LTS-Uber-Jars. Siehe folgenden Abschnitt:

**Uber Jars für AEM 6.5**

1. `uber-jar-6.5.x.jar` - Enthält alle öffentlichen APIs von AEM 6.5.
1. `uber-jar-6.5.x-apis-with-deprecations.jar` - Enthält sowohl öffentliche als auch veraltete APIs aus AEM 6.5.

**Uber Jars für AEM 6.5 LTS**

Für AEM 6.5 LTS gibt es wieder zwei Arten von Uber Jars:

1. `uber-jar-6.6.x-apis.jar` - Enthält alle öffentlichen APIs von AEM 6.5 LTS.
1. `uber-jar-6.6.x-deprecated-apis.jar` - Enthält nur veraltete APIs aus AEM 6.5 LTS.

**Hauptunterschied: AEM 6.5 vs. AEM 6.5 LTS Uber Jars**

* Wenn in AEM 6.5 sowohl öffentliche als auch veraltete APIs benötigt werden, können Sie eine einzige JAR-Datei zum Einschließen verwenden, die in Ihrer `uber-jar-6.5.x-apis-with-deprecations.jar`-Datei `pom.xml` wird.
* Wenn Sie in AEM 6.5 LTS sowohl öffentliche als auch veraltete APIs benötigen, müssen Sie zwei separate JARs einbeziehen, `uber-jar-6.6.x-apis.jar` für öffentliche APIs und `uber-jar-6.6.x-deprecated-apis.jar` für veraltete APIs.

**Maven-Koordinaten für veraltete APIs in Jar**

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.0</version>
    <classifier>deprecated-apis</classifier>
    <scope>provided</scope>
</dependency>
```

### Hinweise für Entwickler {#developer-notes}

* AEM 6.5 LTS enthält standardmäßig keine Google Guava-Bibliothek. Die erforderliche Version kann je nach Anforderung installiert werden.
* Das Sling-XSS-Bundle verwendet jetzt die Java HTML Sanitizer-Bibliothek. Die Verwendung der `XSSAPI#filterHTML()`-Methode sollte zum sicheren Rendern von HTML-Inhalten und nicht zum Übergeben von Daten an andere APIs verwendet werden.
* Aktualisierung der Apache Felix HTTP-SSL-Filterkonfiguration: In AEM 6.5 LTS wurde das `org.apache.felix.http.sslfilter`-Bundle von Version 1.2.6 auf 2.0.2 aktualisiert. Im Rahmen dieses Upgrades wird die OSGi-Konfigurations-PID `org.apache.felix.http.sslfilter.SslFilter` nicht mehr unterstützt und durch eine neue PID ersetzt: `org.apache.felix.http.sslfilter.Configuration`. Wenn der SSL-Filter in der -Bereitstellung verwendet wird, müssen vorhandene Konfigurationen mithilfe des OSGi Configuration Managers (`/system/console/configMgr`) manuell zur neuen PID migriert werden. Wenn die Konfiguration nicht migriert wird, wird der SSL-Filter möglicherweise nach dem Upgrade nicht wie erwartet angewendet.

## Testverfahren {#testing-procedure}

Zum Testen von Upgrades sollte ein umfassender Testplan erstellt werden. Das Testen der aktualisierten Code-Basis und Anwendung muss zunächst in niedrigeren Umgebungen erfolgen. Alle Fehler müssen iterativ korrigiert werden, bis die Code-Basis stabil ist. Führen Sie erst dann Upgrades für Umgebungen auf höherer Ebene durch.

### Testen des Upgrade-Verfahrens {#testing-upgrade-procedure}

Testen Sie das hier beschriebene Upgrade-Verfahren in Entwicklungs- und QA-Umgebungen, wie im benutzerdefinierten Runbook dokumentiert (siehe [Planung des Upgrades](/help/sites-deploying/upgrade-planning.md)). Das Upgrade-Verfahren muss wiederholt werden, bis alle Schritte im Upgrade-Runbook dokumentiert sind und das Upgrade-Verfahren reibungslos läuft.

### Implementierungstestbereiche  {#implementation-test-areas-}

Im Folgenden sind wichtige Bereiche einer AEM-Implementierung genannt, die vom Testplan abgedeckt sein müssen, sobald die Umgebung upgegradet und die aktualisierte Code-Basis bereitgestellt wurde.

<table>
 <tbody>
  <tr>
   <td><strong>Funktioneller Testbereich</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Veröffentlichte Sites</td>
   <td>Testen der AEM-Implementierung und des zugehörigen Codes auf der Veröffentlichungsebene<br /> über den Dispatcher. Sollte Kriterien für Seitenaktualisierungen und<br /> Cache-Invalidierung enthalten.</td>
  </tr>
  <tr>
   <td>Authoring</td>
   <td>Testen von AEM-Implementierung und zugehörigem Code auf der Autorenschicht. Sollte Seiten-, Komponenten-Authoring- und Dialogfelder enthalten.</td>
  </tr>
  <tr>
   <td>Integrationen mit Experience Cloud-Lösungen</td>
   <td>Validieren von Integrationen mit Produkten wie Analytics.</td>
  </tr>
  <tr>
   <td>Integrationen mit Drittanbietersystemen</td>
   <td>Validieren aller Drittanbieterintegrationen auf der Authoring- und Publishing-Ebene.</td>
  </tr>
  <tr>
   <td>Authentifizierung, Sicherheit und Berechtigungen</td>
   <td>Alle Authentifizierungsmechanismen wie LDAP/SAML sollten überprüft werden.<br /> Berechtigungen und Gruppen sollten sowohl auf der Authoring- als auch auf der Publishing-Ebene<br /> getestet werden.</td>
  </tr>
  <tr>
   <td>Abfragen</td>
   <td>Benutzerdefinierte Indizes und Abfragen sollten zusammen mit der Abfrageleistung getestet werden.</td>
  </tr>
  <tr>
   <td>Benutzeroberflächenanpassungen</td>
   <td>Alle Erweiterungen oder Anpassungen der AEM-Benutzeroberfläche in der Autorenumgebung.</td>
  </tr>
  <tr>
   <td>Workflows</td>
   <td>Benutzerdefinierte und/oder vordefinierte Workflows und Funktionen.</td>
  </tr>
  <tr>
   <td>Leistungstests</td>
   <td>Lasttests sollten sowohl auf der Authoring- als auch auf der Publishing-Ebene durchgeführt werden, um reale Szenarien zu simulieren.</td>
  </tr>
 </tbody>
</table>

### Dokumenttestplan und Ergebnisse {#document-test-plan-and-results}

Es sollte ein Testplan erstellt werden, der die oben genannten Implementierungstestbereiche abdeckt. Oft ist es sinnvoll, den Testplan nach Aufgabenlisten für Authoring- und Publishing-Aufgaben zu trennen. Dieser Testplan muss auf Entwicklungs-, QA- und Staging-Umgebungen ausgeführt werden, bevor Produktionsumgebungen aktualisiert werden. Erfassen Sie die Testergebnisse und Leistungsmetriken aus Umgebungen niedrigerer Ebenen als Referenzwerte für das Upgrade der Staging- und Produktionsumgebungen.
