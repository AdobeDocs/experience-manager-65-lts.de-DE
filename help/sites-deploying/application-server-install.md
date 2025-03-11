---
title: Installation des Anwendungs-Servers
description: Erfahren Sie, wie Sie Adobe Experience Manager mit einem Anwendungs-Server installieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: 09d54b52-485a-453c-a2d0-535adead9e6c
source-git-commit: 5f968f5dc0696a683cc063d330c8edfba05f11ab
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 42%

---

# Installation des Anwendungs-Servers{#application-server-install}

>[!NOTE]
>
>`JAR` und `WAR` sind die Dateitypen, in denen Adobe Experience Manager (AEM) veröffentlicht wird. Diese Formate unterliegen einer Qualitätssicherung, mit der die von Adobe zugesicherten Unterstützungsebenen sichergestellt werden.
>

In diesem Abschnitt erfahren Sie, wie Sie Adobe Experience Manager (AEM) mit einem Anwendungs-Server installieren. Lesen Sie den Abschnitt [Unterstützte Plattformen](/help/sites-deploying/technical-requirements.md#servlet-engines-application-servers), um mehr über die spezifischen Unterstützungsebenen für die einzelnen Anwendungs-Server zu erfahren.

Es werden die Installationsschritte der folgenden Anwendungs-Server beschrieben:

* [WebSphere](#websphere)
* [Tomcat 11.0.x](#tomcat)

Lesen Sie die entsprechende Anwendungsserverdokumentation, um weitere Informationen über das Installieren von Webanwendungen, Serverkonfigurationen und darüber zu erhalten, wie der Server gestartet und angehalten wird.

<!-- >[!NOTE]
>
>If you are using Dynamic Media in a WAR deployment, see [Dynamic Media documentation](/help/assets/config-dynamic.md#enabling-dynamic-media). -->

## Allgemeine Beschreibung {#general-description}

### Standardverhalten beim Installieren von AEM auf einem Anwendungsserver {#default-behaviour-when-installing-aem-in-an-application-server}

AEM wird als eine einzelne bereitzustellende WAR-Datei geliefert.

Nach der Bereitstellung geschieht standardmäßig Folgendes:

* Der Ausführungsmodus ist `author`
* Die Instanz (Repository, Felix OSGi-Umgebung, Bundles usw.) wird in `${user.dir}/crx-quickstart` installiert, wobei `${user.dir}` das aktuelle Arbeitsverzeichnis ist. Dieser Pfad zu crx-quickstart wird als `sling.home` bezeichnet

* Der Kontextstamm ist der Name der WAR-Datei. Zum Beispiel: `aem-65-lts`.

#### Konfiguration {#configuration}

Sie können das Standardverhalten wie folgt ändern:

* Ausführungsmodus: Konfigurieren Sie den Parameter `sling.run.modes` in der Datei `WEB-INF/web.xml` der AEM-WAR-Datei vor der Bereitstellung.

* sling.home: Konfigurieren Sie den `sling.home` in der `WEB-INF/web.xml` der AEM-WAR-Datei vor der Bereitstellung

* Kontextstamm: Benennen Sie die AEM-WAR-Datei um.

#### Installationsveröffentlichung {#publish-installation}

Um eine Veröffentlichungsinstanz bereitzustellen, müssen Sie den Ausführungsmodus auf „publish“ (veröffentlichen) festlegen:

* Entpacken Sie die `WEB-INF/web.xml` aus der AEM-WAR-Datei
* Ändern `sling.run.modes` Veröffentlichungsparameters
* Packen Sie `web.xml` Datei erneut in die AEM-WAR-Datei.
* Stellen Sie die AEM-WAR-Datei bereit.

#### Installationsprüfung {#installation-check}

Um zu überprüfen, ob alles installiert ist, können Sie:

* Untersuchen der Datei `error.log`, um anzuzeigen, ob der gesamte Inhalt installiert ist.
* Überprüfen in `/system/console`, ob alle Bundles installiert sind

#### Zwei Instanzen auf demselben Anwendungs-Server {#two-instances-on-the-same-application-server}

Zu Demonstrationszwecken kann es sinnvoll sein, sowohl die Autoren- als auch die Veröffentlichungsinstanz auf einem Anwendungs-Server zu installieren. Um dies zu erreichen, müssen Sie:

1. Ändern `sling.home` Variablen und `sling.run.modes` Variablen der Veröffentlichungsinstanz
1. Entpacken Sie die `WEB-INF/web.xml` aus der AEM-WAR-Datei
1. Ändern Sie den `sling.home` Parameter in einen anderen Pfad (absolute und relative Pfade sind möglich)
1. Ändern Sie `sling.run.modes` für die Veröffentlichungsinstanz in `publish` .
1. `web.xml` neu packen
1. Benennen Sie die WAR-Dateien um, damit sie verschiedene Namen aufweisen. Benennen Sie beispielsweise eine in `aemauthor.war` und die andere in `aempublish.war` um
1. Verwenden Sie die Einstellungen für den höheren Arbeitsspeicher. Beispielsweise verwenden AEM-Standardinstanzen `-Xmx3072m`.
1. Bereitstellen der beiden Web-Anwendungen
1. Nach der Bereitstellung stoppen Sie die beiden Web-Anwendungen
1. Stellen Sie sowohl in der Autoren- als auch in der Veröffentlichungsinstanz sicher, dass in der `sling.properties`-Datei die Eigenschaft `felix.service.urlhandlers` auf `false` gesetzt ist. (Der Standardwert lautet, dass er auf `true` festgelegt ist.)
1. Starten Sie die zwei Web-Anwendungen erneut.

## Installationsverfahren für Anwendungs-Server {#application-servers-installation-procedures}

### WebSphere® 24.0.0.7 {#websphere}

Lesen Sie oben „Allgemeine [&quot; vor ](#general-description) Bereitstellung.

**Vorbereitung des Servers**

* So lassen Sie Standard-Authentifizierungs-Header durchlaufen:

   * Eine Möglichkeit, AEM die Authentifizierung eines Benutzers zu ermöglichen, besteht darin, die globale administrative Sicherheit des WebSphere®-Servers zu deaktivieren. Wechseln Sie dazu zu **Sicherheit > Globale Sicherheit** und deaktivieren Sie das Kontrollkästchen **Enable administrative security**, speichern Sie den Server und starten Sie ihn neu.

* `"JAVA_OPTS= -Xmx2048m"`
* Wenn Sie AEM mithilfe des Kontextstamms = / installieren möchten, ändern Sie den Kontextstamm der vorhandenen standardmäßigen Web-Anwendung.

**Bereitstellen der AEM-Web-Anwendung**

* Herunterladen der AEM-WAR-Datei
* Nehmen Sie bei Bedarf Konfigurationen in der `web.xml` vor. Weitere Informationen finden Sie oben unter [Allgemeine Beschreibung](#general-description).

   * Entpacken Sie die `WEB-INF/web.xml`
   * Ändern Sie den `sling.run.modes` Parameter in `publish`
   * Entfernen Sie den Kommentar für den anfänglichen `sling.home` und legen Sie diesen Pfad nach Bedarf fest
   * Packen Sie die `web.xml` erneut.

* Bereitstellen der AEM-WAR-Datei

   * Wählen Sie einen Kontextstamm aus. Wenn Sie die Sling-Ausführungsmodi festlegen möchten, müssen Sie die detaillierten Schritte des Bereitstellungsassistenten auswählen und sie dann in Schritt 6 des Assistenten angeben.

* Starten der AEM-Webanwendung

#### Tomcat 11.0.x {#tomcat}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

* **Tomcat-Servervorbereitung**

   * Erhöhen Sie den für die virtuelle Maschine eingestellten Arbeitsspeicherwert:

      * Fügen Sie in `bin/catalina.bat` (bzw. `catalina.sh` unter UNIX®) die folgende Einstellung hinzu:

        ```
        set "JAVA_OPTS= -Xmx2048m`
        ```

   * Tomcat aktiviert bei der Installation keinen Admin- oder Managerzugriff. Daher müssen Sie `tomcat-users.xml` manuell bearbeiten, um den Zugriff für diese Konten zuzulassen:

      * Bearbeiten Sie `tomcat-users.xml`, um den Zugriff für Admin und Managerin bzw. Manager einzuschließen. Die Konfiguration sollte dem folgenden Beispiel ähneln:

        ```xml
        <?xml version='1.0' encoding='utf-8'?>
        <tomcat-users>
        role rolename="manager"/>
        role rolename="tomcat"/>
        <role rolename="admin"/>
        <role rolename="role1"/>
        <role rolename="manager-gui"/>
        <user username="both" password="tomcat" roles="tomcat,role1"/>
        <user username="tomcat" password="tomcat" roles="tomcat"/>
        <user username="admin" password="admin" roles="admin,manager-gui"/>
        <user username="role1" password="tomcat" roles="role1"/>
        </tomcat-users>
        ```

   * Wenn Sie AEM mit dem Kontextstamm „/“ bereitstellen möchten, müssen Sie den Kontextstamm der vorhandenen „ROOT webapp“ (Stamm-Web-Anwendung) ändern:

      * Beenden und Aufheben der Bereitstellung der ROOT-Web-App
      * Benennen Sie den `ROOT.war` Ordner im Ordner „webapps“ von Tomcat um.
      * Starten Sie die Web-App erneut

   * Wenn Sie die AEM-Web-Anwendung über die manager-gui installieren, müssen Sie die maximale Größe einer hochgeladenen Datei erhöhen, da die Standardeinstellung nur eine Upload-Größe von 50 MB zulässt. Öffnen Sie dazu die `web.xml` der Manager-Web-Anwendung:

     `webapps/manager/WEB-INF/web.xml`

     und erhöhen Sie die `max-file-size` und `max-request-size` auf mindestens 500 MB. Siehe die folgenden `multipart-config` in einer `web.xml`-Beispieldatei unten:

     ```xml
     <multipart-config>
     <!-- 500MB max -->
     <max-file-size>524288000</max-file-size>
     <max-request-size>524288000</max-request-size>
     <file-size-threshold>0</file-size-threshold>
     </multipart-config>
     ```

* **Bereitstellen der AEM-Web-Anwendung**

   * Laden Sie die AEM-WAR-Datei herunter.
   * Nehmen Sie bei Bedarf Konfigurationen in der `web.xml` vor.

      * Entpacken Sie die `WEB-INF/web.xml`
      * Ändern Sie den `sling.run.modes` Parameter in `publish`
      * Entfernen Sie den Kommentar für den anfänglichen `sling.home` und legen Sie diesen Pfad nach Bedarf fest
      * Packen Sie die `web.xml` erneut.

   * Benennen Sie die AEM-WAR-Datei in `ROOT.war` um, wenn Sie sie als Root-Web-App bereitstellen möchten. Benennen Sie ihn in `aemauthor.war` um, wenn Sie `aemauthor` als Kontextstamm haben möchten.
   * Kopieren Sie es in den Ordner „webapps“ von Tomcat
   * Warten Sie, bis AEM installiert ist.
