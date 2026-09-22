---
title: Hotfixes für Adobe Experience Manager Forms 6.5 LTS
description: Enthält Informationen zum Herunterladen und Installieren eines Hotfixes für AEM Forms 6.5 LTS. Informationen zu AEM 6.5 (nicht-LTS) finden Sie im Artikel AEM 6.5 Forms Hotfixes .
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: e485100f-3e16-4fd4-a8ce-af771d765dd1
source-git-commit: 989d83cfc56f7a7d4e2aea5a7ac1ca444d505859
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 11%
---
# Hotfixes für Adobe Experience Manager Forms 6.5 LTS{#aem-form-hotfix}

In diesem Artikel werden die wichtigen Korrekturen aufgeführt, die implementiert wurden, um bekannte Probleme zu beheben, die Systemstabilität zu verbessern und die Gesamtleistung von AEM Forms 6.5 LTS zu verbessern.


Dieser Artikel gilt für AEM Forms 6.5 LTS. Informationen zu AEM 6.5-Bereitstellungen (nicht LTS) finden Sie unter [Adobe Experience Manager Forms Hotfixes](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/release-notes/aem-forms-hotfix).

>[!NOTE]
>
> Die Hotfixes sind kumulativ konzipiert und umfassen alle vorherigen Fehlerbehebungen. Wenn Sie das neueste Hotfix auf eine Version anwenden, wird nicht nur das jüngste Problem behoben, sondern das Hotfix enthält auch alle vorherigen Fehlerbehebungen und Verbesserungen.

## Hotfixes für AEM Forms 6.5 LTS {#hotfix-for-aem-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Datum</strong></td>
    <td><strong>Hotfix-Downloadlink (AEM Software Distribution-Link)</strong></td>
    <td><strong>Behobene Probleme</strong></td>
  </tr>
  <tr>
    <td>
      <strong>21. September 2026</strong><br>
      <em>Gilt für:</em> AEM Forms 6.5 LTS Service Pack 2 JEE-Bereitstellungen (JBoss, WebLogic, WebSphere)<br>
    </td>
    <td>
    <p><strong>Um diesen Hotfix zu installieren, führen Sie die folgenden Schritte in der richtigen Reihenfolge aus:</strong></p>
    <p><strong>Schritt 1: Patch installieren</strong></p>
    <ul>
    <strong>JBoss:</strong>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/jboss/adobe-aem-forms-jee-hotfix-6.5.LTS.2-win-jboss.zip">Hotfix für AEM Forms 6.5 LTS SP2 unter Windows für JBoss JEE-Server</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/jboss/adobe-aem-forms-jee-hotfix-6.5.LTS.2-linux-jboss.tar.gz">Hotfix für AEM Forms 6.5 LTS SP2 unter Linux für JBoss JEE-Server</a></li>
    <strong>WebLogic:</strong>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/weblogic/adobe-aem-forms-jee-hotfix-6.5.LTS.2-win-weblogic.zip">Hotfix für AEM Forms 6.5 LTS SP2 unter Windows für Weblogic JEE-Server</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/weblogic/adobe-aem-forms-jee-hotfix-6.5.LTS.2-linux-weblogic.tar.gz">Hotfix für AEM Forms 6.5 LTS SP2 unter Linux für Weblogic JEE-Server</a></li>
    <strong>WebSphere:</strong>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/websphere/adobe-aem-forms-jee-hotfix-6.5.LTS.2-win-websphere.zip">Hotfix für AEM Forms 6.5 LTS SP2 unter Windows für Websphere JEE Server</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/websphere/adobe-aem-forms-jee-hotfix-6.5.LTS.2-linux-websphere.tar.gz">Hotfix für AEM Forms 6.5 LTS SP2 unter Linux für Websphere JEE Server</a></li>
    </ul>
    <p>Installieren Sie den Patch mit dem standardmäßigen Patch-Installationsverfahren für AEM Forms on JEE. <!-- TODO: link to the 6.5 LTS JEE patch installation instructions once available --></p>
    <p><strong>Schritt 2: Installieren des Pakets mit der Schwachstellenbehebung</strong></p>
    <ul>
    <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/SP2LTSBundles_VULN-36670.zip">Fehlerbehebungspaket für AEM Forms 6.5 LTS SP2</a></li>
    </ul>
    <ol>
    <li>Öffnen Sie die OSGi-Konsole unter <code>http://&lt;host&gt;:&lt;port&gt;/lc/system/console/bundles</code>.</li>
    <li>Klicken Sie <strong>Installieren/Aktualisieren</strong>.</li>
    <li>Aktivieren Sie die Kontrollkästchen <strong>Bundle starten</strong> und <strong>Pakete aktualisieren</strong>.</li>
    <li>Klicken Sie <strong>Datei auswählen</strong> und laden Sie dann das heruntergeladene Bundle hoch.</li>
    <li>Warten Sie, bis sich das Protokoll gelegt hat und das Bundle als "<strong>" </strong>.</li>
    </ol>
    <p><strong>Schritt 3: Aktualisieren des AEM Forms Workbench-Installationsprogramms</strong></p>
    <p>Sie müssen auf das neueste AEM Forms Workbench-Installationsprogramm aktualisieren. Sie kann vom <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/fd/workbench/6-5-0-20260902-1-45/Workbench_DVD.zip">AEM Forms Workbench-Installationsprogramm heruntergeladen </a>.</p>
    <p><strong>Schritt 4: Client-Bibliotheksdateien aktualisieren (Entwickler)</strong></p>
    <p>Dieser Patch enthält ein wichtiges Update der SDK-Client-<code>adobe-livecycle-client.jar</code> (siehe <a href="/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files">Einbeziehen von AEM Forms Java-Bibliotheksdateien</a>). Wenn Ihr Projekt diese JAR-Datei verwendet, aktualisieren Sie <code>adobe-livecycle-client.jar</code> im Klassenpfad Ihres Projekts, nachdem Sie den Hotfix installiert haben. Die neueste Version ist unter <code>&lt;AEM_Forms_Installation_dir&gt;\sdk\client-libs\common\adobe-livecycle-client.jar</code> verfügbar.</p>
    <p>Der Hotfix ist kumulativ und kann daher auf AEM Forms 6.5 LTS Service Pack 2 oder ein früheres Service Pack angewendet werden, ohne dass zunächst Service Pack 2 installiert werden muss.</p>
    </td>
    <td>
    <ul>
    <li><b>FORMS-26818</b> Nach der Aktualisierung von Apache Shiro auf Version 2.1.0 kann AEM Forms on JEE kein Bootstrapping mit einer <code>NoClassDefFoundError</code> für den Shiro-Sicherheits-Manager durchführen. Dieser Hotfix stellt erfolgreiches Bootstrapping wieder her.</li>
    <li><b>FORMS-26819</b> AEM Forms on JEE schlägt mit dem Fehler „Keine Klasse gefunden“ für <code>org.owasp.esapi.reference.JavaLogFactory</code> fehl. Dieses Hotfix löst die fehlende Klasse auf.</li>
    <li><b>FORMS-26584, FORMS-26589</b> Nach dem Upgrade auf AEM Forms 6.5 LTS werden TaskManager-Endpunkte entfernt. Dieses Hotfix stellt die TaskManager-Endpunkte wieder her.</li>
    <li><b>FORMS-26569</b> Bei JEE schlägt der Schritt „Configuration Manager MergeEars“ aufgrund des sicheren XML-Builders mit einem DOCTYPE-Deklarationsfehler (<code>ALC-LCM-010-200</code>) fehl. Mit diesem Hotfix kann der MergeEars-Schritt abgeschlossen werden.</li>
    <li><b>FORMS-25063</b> Protokolle auf Anwendungsebene fehlen in IBM WebSphere Liberty-Bereitstellungen. Dieser Hotfix stellt die Protokollierung auf Anwendungsebene wieder her.</li>
    <li><b>FORMS-24892</b> Bei JBoss schlägt die E-Mail mit „IMAPProvider ist kein Untertyp“ fehl. Dieser Hotfix stellt die E-Mail-Funktionalität auf JBoss wieder her.</li>
    <li><b>FORMS-24692</b> Bei WebSphere Liberty Profile (WLP) schlägt die E-Mail mit „Socket konnte nicht in TLS konvertiert werden“ fehl. Dieser Hotfix stellt E-Mail über TLS auf WLP wieder her.</li>
    <li><b>FORMS-26688</b> Aktualisiert die Gibson-Bibliothek auf Version 6.0.29665850.</li>
    <li><b>FORMS-25222</b> Backports für Verbesserungen bei der SAML-Bestätigungsvalidierung.</li>
    <li><b>FORMS-26733, FORMS-26734</b> hat Apache Log4j auf Version 2.25.5 aktualisiert.</li>
    <li>Dieses Hotfix enthält auch Sicherheitskorrekturen.</li>
    </ul>
    <p><strong>Build:</strong> AEMForms-6.6.0-0008</p>
    </td>
  </tr>
  <tr>
    <td>
      <strong>9. September 2025</strong><br>
    <td>
    <ul>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[…]1-hotfix-on-add-on/adobe-aemfd-win-pkg-6.1.176-RHF-002.zip">Hotfix2 für AEM Service Pack 6.5 LTS unter Windows</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[…]hotfix-on-add-on/adobe-aemfd-linux-pkg-6.1.176-RHF-002.zip">Hotfix2 für AEM Service Pack 6.5 LTS unter Linux</a></li>
     <li>MacOS- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[…]1-hotfix-on-add-on/adobe-aemfd-osx-pkg-6.1.176-RHF-002.zip">Hotfix2 für AEM Service Pack 6.5 LTS auf MacOS</a></li>
    <td>
    <ul>
    <li>Die Zuverlässigkeit der Formularübermittlung wurde verbessert, indem ein Problem behoben wurde, bei dem Übermittlungen fehlschlagen können, wenn die Server-seitige Validierung (SSV) aktiviert war. Wenn Probleme auftreten, wenden Sie sich an den [Adobe Experience Manager Forms-Support](https://business.adobe.com/in/support/main.html).
    </li>
    </ul>
    </td>    
  </tr>
    </ul>
    </td>    
  </tr>
  <tbody>
</table>

## Herunterladen und Installieren eines OSGi-Hotfixes {#download-install-hotfix}

Führen Sie die folgenden Schritte aus, um das Hotfix herunterzuladen und zu installieren:

1. Laden Sie das [Hotfix](#hotfix-for-adaptive-forms) über den Software Distribution-Link herunter.
1. Extrahieren Sie die Hotfix-Archivdatei, damit Sie ein Experience Manager-Paket (.zip) und Bundle-Dateien (.jar) abrufen können.
1. Laden Sie das Paket (.zip) über den [Paket-Manager](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=de#accessing) hoch und installieren Sie es.
1. Öffnen Sie die Pakete des Konfigurations-Managers `https://server:host/system/console/bundles`, laden Sie sie hoch und installieren Sie das Paket (.jar). Das Hotfix wird installiert.
