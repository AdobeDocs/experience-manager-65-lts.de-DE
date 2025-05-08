---
title: Upgrade auf AEM 6.5 Forms LTS unter OSGi
description: Sie können direkt von AEM 6.5.22.0 Forms auf AEM 6.5 Forms LTS aktualisieren.
content-type: reference
role: Admin, User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, AEM Forms on OSGi, AEM Forms Upgrade
exl-id: 9233d4b7-441c-4cbd-86f8-2c52b99c3330
source-git-commit: dd45dfe953a111ccbbc71e8e25a8a2577037587a
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 81%

---

# Upgrade auf AEM 6.5 Forms LTS unter OSGi {#upgrade-to-aem-forms-osgi}

Um [von AEM 6.5 auf AEM 6.5 LTS](/help/sites-deploying/upgrade.md) zu aktualisieren, führen Sie ein Upgrade auf AEM 6.5.22.0 Forms oder höher durch. Ein direktes Upgrade von AEM 6.5.22.0 auf AEM 6.5 Forms LTS wird unterstützt.

Wenn Sie AEM 6.0 Forms, AEM 6.1 Forms, AEM 6.2 Forms, AEM 6.3 Forms, AEM 6.4 Forms oder AEM 6.5 Forms verwenden, ist kein direktes Upgrade auf AEM 6.5 Forms LTS verfügbar. Ausführliche Informationen zu Upgrade-Pfaden finden Sie in der [Upgrade-Pfade](/help/forms/using/upgrade.md).

Führen Sie nach dem Upgrade auf das Service Pack AEM Forms 6.5.22.0 die folgenden Schritte aus, um auf AEM 6.5 LTS Forms zu aktualisieren:

1. Installieren des AEM Forms-Add-on-Pakets. Die Schritte sind hier aufgeführt:

   1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
   1. Wählen Sie im Kopfzeilenmenü **[!UICONTROL Adobe Experience Manager]** aus.
   1. Im Abschnitt **[!UICONTROL Filter]**:
      1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** aus.
      1. Wählen Sie die Version aus und geben Sie sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
   1. Wählen Sie den für Ihr Betriebssystem zutreffenden Paketnamen, dann **[!UICONTROL EULA-Bedingungen akzeptieren]** und dann **[!UICONTROL Herunterladen]** aus.
   1. Öffnen Sie [Package Manager](/help/sites-administering/package-manager.md) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
   1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

      Sie können das Paket auch über den direkten Link herunterladen, der im Artikel [AEM Forms-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) aufgeführt ist.

      Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Halten Sie den Server nicht sofort an.** Warten Sie vor dem Anhalten des AEM Forms-Servers, bis die Meldungen „ServiceEvent REGISTERED“ und „ServiceEvent UNREGISTERED“ nicht mehr in der Datei &lt;crx-repository>/error.log angezeigt werden und das Protokoll stabil ist. Beachten Sie außerdem, dass einige Pakete im installierten Zustand verbleiben können. Sie können den Status dieser Pakete ignorieren.


      **Starten Sie die AEM-Instanz mit den folgenden zusätzlichen JVM-Befehlszeilenparametern neu**:
      `--add-opens java.base/java.util=ALL-UNNAMED --add-exports=java.xml/com.sun.org.apache.xml.internal.serialize=ALL-UNNAMED`

      Wenn der Server über ein Skript oder einen Service gestartet wird, aktualisieren Sie ihn entsprechend, um die oben genannten einzuschließen, damit diese auch nach nachfolgenden Neustarts wirksam werden.

      >[!NOTE]
      >
      > Es wird empfohlen, den Befehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

1. Führen Sie nach der Installation folgende Aktivitäten durch.

   * **Ausführen des Migrationsdienstprogramms**

     Das Migrationsdienstprogramm macht die adaptiven Formulare und Korrespondenzmanagement-Assets aus früheren Versionen kompatibel mit AEM 6.5 Forms. Sie können das Dienstprogramm von der AEM Software Distribution herunterladen. Informationen in Einzelschritten zur Konfiguration und Verwendung des Migrationsdienstprogramms finden Sie in der Dokumentation zum [Migrationsdienstprogramm](../../forms/using/migration-utility.md).

     Wenn Sie [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) mit der Datenbank verwenden und von einer früheren Version aktualisieren, führen Sie nach der Aktualisierung die folgenden SQL-Abfragen aus:

     ```sql
     UPDATE metadata m, additionalmetadatatable am
     SET m.dataType = am.value
     WHERE m.id = am.id
     AND am.key = 'dataType'
     ```

     ```sql
     DELETE from additionalmetadatatable
     WHERE `key` = 'dataType'
     ```

   * **(Nur wenn Sie von AEM 6.2 Forms oder früheren Versionen aktualisieren) Konfigurieren Sie Adobe Sign neu**

     Wenn Sie Adobe Sign in der vorherigen Version von AEM Forms konfiguriert haben, konfigurieren Sie Adobe Sign über AEM Cloud Services neu. Weitere Informationen finden Sie unter [Adobe Sign mit AEM Forms integrieren](../../forms/using/adobe-sign-integration-adaptive-forms.md).

   * **Unterstützung für jQuery**

     In AEM 6.5 Forms wird die jQuery-Version auf 3.2.1 aktualisiert und die jQuery-UI-Version wird auf 1.12.1 aktualisiert. AEM Form verwendet JQuery im **noConflict**-Modus. Wenn Sie also eine andere jQuery-Version verwenden, werden bei der Durchführung eines Upgrades keine Probleme angezeigt. Wenn Sie jedoch auf AEM 6.5 Forms aktualisieren:

      * Stellen Sie sicher, dass Ihre benutzerdefinierten Komponenten, falls vorhanden, mit unterstützten jQuery-Versionen kompatibel sind.
      * Entfernen Sie nicht unterstützte APIs aus den benutzerdefinierten Komponenten. Siehe [Upgrade-Handbuch](https://jquery.com/upgrade-guide/3.0/) für die Liste der entfernten APIs. Beispielsweise wird die Unterstützung für die APIs load(), .unload() und .error() entfernt. Verwenden Sie die Methode .on() anstelle der oben genannten APIs. Ändern Sie beispielsweise $(&quot;img&quot;).load(fn) to $(&quot;img&quot;).on(&quot;load&quot;, fn).

   * **(Nur wenn Sie von AEM 6.2 Forms oder früheren Versionen aktualisieren) Konfigurieren Sie Analysen und Berichte neu**

     In AEM 6.4 Forms sind keine Traffic-Variablen für Quelle und Erfolgsereignis für Impressionen verfügbar. Wenn Sie von AEM 6.2 Forms oder vorherigen Versionen aktualisieren, sendet AEM Forms daher keine Daten mehr an den Adobe Analytics-Server und es stehen keine Analyseberichte für adaptive Formulare zur Verfügung. Darüber hinaus führt AEM 6.4 Forms Traffic-Variablen für die Version der Formularanalyse und das Erfolgsereignis für die auf einem Feld verbrachte Zeit ein. Konfigurieren Sie daher die Analyse und die Berichte für Ihre AEM Forms-Umgebung neu. Ausführliche Anweisungen finden Sie unter [Konfigurieren von Analysen und Berichten](../../forms/using/configure-analytics-forms-documents.md).

1. Vergewissern Sie sich, dass der Server erfolgreich aktualisiert und alle Daten migriert wurden und dass der Server einwandfrei funktioniert.

   * **Überprüfen Sie den Status der Pakete:** Stellen Sie sicher, dass alle Pakete sich im aktiven Status befinden.
   * **Überprüfen Sie die Replikation und Rückwärtsreplikation:** Veröffentlichen Sie einige migrierte Formulare, füllen Sie sie aus und senden Sie sie. Überprüfen Sie auch die gesendeten Daten.
   * **Überprüfen Sie den Zugriff auf die Administrator- und Entwicklerbenutzeroberflächen:** Melden Sie sich über ein Administratorkonto bei der AEM-Instanz an und stellen Sie sicher, dass Sie Zugriff auf die folgenden URLs haben:

      * `https://'[server]:[port]'/crx/packmgr`
      * `https://'[server]:[port]'/crx/de`
      * `https://'[server]:[port]'/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   >
   >In AEM 6.4 Forms hat sich die Struktur des crx-Repository geändert. Verwenden Sie nach dem Upgrade auf AEM 6.5 Forms die geänderten Pfade für die Anpassung, die Sie neu erstellen. Sie finden die vollständige Liste der geänderten Pfade unter [Forms Repository-Restrukturierung in AEM](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/deploying/restructuring/forms-repository-restructuring-in-aem-6-5).
