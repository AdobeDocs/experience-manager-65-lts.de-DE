---
title: Konfigurieren des Asset-Tagging mit dem Smart Content Service
description: Erfahren Sie, wie Sie in  [!DNL Adobe Experience Manager] Smart-Tagging und optimierte Smart-Tags mit dem Smart Content Service konfigurieren.
role: Admin
feature: Tagging,Smart Tags
solution: Experience Manager, Experience Manager Assets
exl-id: be7c294c-149b-4825-8376-573f9e2987e2
source-git-commit: 1cedead501597fb655c2c7b87336b29cbf048294
workflow-type: tm+mt
source-wordcount: '1896'
ht-degree: 97%

---

# Vorbereiten von [!DNL Assets] für Smart-Tagging {#configure-asset-tagging-using-the-smart-content-service}

Bevor Sie mit dem Tagging Ihrer Assets per Smart Content Services beginnen können, integrieren Sie [!DNL Experience Manager Assets] in die Adobe Developer Console, um den Smart-Service von [!DNL Adobe Sensei] zu nutzen. Trainieren Sie den Service nach der Konfiguration mit einigen Bildern und einem Tag.
Bevor Sie den Smart Content Service verwenden, führen Sie Folgendes aus:

* [Integrieren Sie ihn mit der Adobe Developer Console](#integrate-adobe-io).
* [Trainieren Sie den Smart Content Service](#training-the-smart-content-service).
* Installieren Sie die neueste Version des [[!DNL Experience Manager] Service Pack](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de).

>[!IMPORTANT]
>
>Informationen zur [ von Smart-Tags in AEM 6.5 finden Sie ](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/assets/administer/config-smart-tagging) „Vorbereiten von Assets für Smart Tagging“.

**Neue Benutzende**

Smart Content Services ist für neue On-Premise-Benutzende von [!DNL Experience Manager Assets] nicht mehr verfügbar. 

**Vorhandene Benutzende**

Vorhandene On-Premise-Benutzende, die diese Funktion bereits aktiviert haben, können Smart Content Services weiterhin nutzen.

## Integrieren mit der Adobe Developer Console {#integrate-adobe-io}

Bei der Integration mit der Adobe Developer Console authentifiziert der [!DNL Experience Manager]-Server Ihre Service-Anmeldedaten beim Adobe Developer Console-Gateway, bevor er Ihre Anfrage an den Smart Content Service weiterleitet. Zur Integration benötigen Sie ein Adobe ID-Konto mit Administratorrechten für die für Ihr Unternehmen erworbene und aktivierte Smart Content Service-Lizenz.

Gehen Sie wie folgt vor, um den Smart Content Service zu konfigurieren:

1. Erstellen Sie eine Integration in [Adobe Developer Console](#create-adobe-io-integration).

1. Erstellen Sie eine [Konfiguration des technischen IMS-Kontos](#create-ims-account-config) mithilfe des API-Schlüssels und der anderen Anmeldedaten aus der Adobe Developer Console.

1. [Konfigurieren Sie den Smart Content Service](#configure-smart-content-service).

1. [Testen Sie die Konfiguration](#validate-the-configuration).

### Erstellen einer Integration in der Adobe Developer Console {#create-adobe-io-integration}

Um die Smart Content Service-APIs zu verwenden, erstellen Sie eine Integration in der Adobe Developer Console, um den [!UICONTROL API-Schlüssel] (der im Feld [!UICONTROL CLIENT-ID] der Adobe Developer Console-Integration generiert wird), die [!UICONTROL ORGANISATIONS-ID] und das [!UICONTROL CLIENT-GEHEIMNIS] für die [!UICONTROL Smart Tagging Service-Einstellungen für Assets] der Cloud-Konfiguration in [!DNL Experience Manager] zu erhalten.

1. Rufen Sie [https://developer.adobe.com](https://developer.adobe.com/) in einem Browser auf. Wählen Sie das entsprechende Konto aus und vergewissern Sie sich, dass die zugehörige Organisationsrolle **Systemadministrator** ist.

1. Erstellen Sie ein Projekt mit einem beliebigen Namen. Klicken Sie auf **[!UICONTROL API hinzufügen]**.

1. Wählen Sie auf der Seite **[!UICONTROL API hinzufügen]** die Option **[!UICONTROL Experience Cloud]** und dann **[!UICONTROL Smart Content]** aus. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie **[!UICONTROL OAuth Server-to-Server]** aus. Klicken Sie auf **[!UICONTROL Weiter]**.
Weitere Informationen zu dieser Konfiguration finden Sie in der Dokumentation zur Developer Console, abhängig von Ihren Anforderungen:

   * Übersicht:
      * [Server-zu-Server-Authentifizierung](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

   * Erstellen von neuen OAuth-Anmeldedaten:
      * [OAuth-Implementierungshandbuch für Server-zu-Server-Anmeldedaten](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)

   * Migration von vorhandenen JWT-Anmeldedaten zu OAuth-Anmeldedaten:
      * [Migration von JWT-Anmeldedaten (Service Account) zu OAuth-Server-zu-Server-Anmeldedaten](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration)


1. Wählen Sie auf der Seite **[!UICONTROL Produktprofile auswählen]** die Option **[!UICONTROL Smart Content Services]** aus. Klicken Sie auf **[!UICONTROL Konfigurierte API speichern]**.

   Auf einer Seite werden weitere Informationen zur Konfiguration angezeigt. Lassen Sie diese Seite geöffnet, um diese Werte zu kopieren und in den [!UICONTROL Einstellungen des Smart Tagging Service für Assets] in der Cloud-Konfiguration in [!DNL Experience Manager] zuzufügen, um Smart Tags zu konfigurieren.

   ![OAuth-Anmeldedaten in der Developer Console](assets/ims-configuration-developer-console.png)

### Erstellen der Konfiguration des technischen IMS-Kontos {#create-ims-account-config}

Sie müssen die Konfiguration des technischen IMS-Kontos mithilfe der folgenden Schritte erstellen:

1. Rufen Sie in der [!DNL Experience Manager]-Benutzeroberfläche **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]** auf.

1. Klicken Sie auf **[!UICONTROL Erstellen]**.

1. Verwenden Sie im Dialogfeld „Konfiguration des technischen IMS-Kontos“ die folgenden Werte:

   ![Fenster „Adobe IMS-Konfiguration“](assets/adobe-ims-config.png)

   | Feld | Beschreibung |
   | -------- | ---------------------------- |
   | Cloud-Lösung | Wählen Sie aus dem Dropdown-Menü **[!UICONTROL Smart-Tags]** aus. |
   | Titel | Fügen Sie den Titel des konfigurierenden IMS-Kontos hinzu. |
   | Autorisierungs-Server | Fügen Sie `https://ims-na1.adobelogin.com` hinzu. |
   | Client-ID | Wird über die [Adobe Developer Console](https://developer.adobe.com/console/) bereitgestellt. |
   | Client-Geheimnis | Wird über die [Adobe Developer Console](https://developer.adobe.com/console/) bereitgestellt. |
   | Anwendungsbereich | Wird über die [Adobe Developer Console](https://developer.adobe.com/console/) bereitgestellt. |
   | Organisations-ID | Wird über die [Adobe Developer Console](https://developer.adobe.com/console/) bereitgestellt. |

1. Wählen Sie die von Ihnen erstellte Konfiguration aus und klicken Sie auf **[!UICONTROL Konsistenz prüfen]**.

1. Bestätigen Sie das Dialogfeld „Konsistenz prüfen“ und klicken Sie auf „Schließen“, sobald die Konfiguration im konsistenten Status ist.

### Erstellen einer neuen Konfiguration {#configure-smart-content-service}

Verwenden Sie zum Konfigurieren der Integration die Werte der Felder [!UICONTROL ID DES TECHNISCHEN KONTOS], [!UICONTROL ORGANISATIONS-ID], [!UICONTROL CLIENT-GEHEIMNIS] und [!UICONTROL CLIENT-ID] aus der Adobe Developer Console-Integration. Das Erstellen einer Smart-Tags-Cloud-Konfiguration ermöglicht die Authentifizierung von API-Anfragen aus der [!DNL Experience Manager]-Bereitstellung.

1. Navigieren Sie in [!DNL Experience Manager] zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Smart-Tag]**, um die [!UICONTROL Smart-Tag-Konfigurationen] zu öffnen.

1. Klicken Sie auf **[!UICONTROL Erstellen]**, um eine neue Konfiguration zu erstellen. Klicken Sie andernfalls auf **[!UICONTROL Eigenschaften]**, um die vorhandene Konfiguration zu aktualisieren.

1. Füllen Sie die folgenden Felder aus:

   ![Konfiguration von Smart-Tags](assets/smart-tags-config.png)

   | Feld | Beschreibung |
   | -------- | ---------------------------- |
   | Titel | Fügen Sie den Titel des konfigurierenden IMS-Kontos hinzu. |
   | Verknüpfte Adobe IMS-Konfiguration | Wählen Sie die Konfiguration aus dem Dropdown-Menü aus. |
   | Service-URL | `https://smartcontent.adobe.io/<region where your Experience Manager author instance is hosted>`. Beispiel: `https://smartcontent.adobe.io/apac`. Sie können `na`, `emea` oder `apac` als die Regionen angeben, in denen Ihre Experience Manager-Autoreninstanz gehostet wird. |

   >[!NOTE]
   >
   >Wenn der Experience Manager Managed Service vor dem 1. September 2022 bereitgestellt wurde, verwenden Sie die folgende Service-URL:
   >`https://mc.adobe.io/marketingcloud/smartcontent`

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

### Überprüfen der Konfiguration {#validate-the-configuration}

Nachdem Sie die Konfiguration abgeschlossen haben, können Sie die Konfiguration mit einem JMX MBean überprüfen. Führen Sie zum Überprüfen die folgenden Schritte aus.

1. Greifen Sie unter `https://[aem_server]:[port]` auf Ihren [!DNL Experience Manager]-Server zu.

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**, um die OSGi-Konsole zu öffnen. Klicken Sie auf **[!UICONTROL Main] > [!UICONTROL JMX]**.

<!--
1. Click `com.day.cq.dam.similaritysearch.internal.impl`. It opens **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.-->

1. Klicken Sie auf `com.day.cq.dam.similaritysearch.internal.impl (SCS)`.

   ![MBean-Fenster](assets/mbean.png)

1. Klicken Sie auf `validateConfigs()`. Klicken Sie im Dialogfeld **[!UICONTROL Konfigurationen prüfen]** auf **[!UICONTROL Aufrufen]**.

Das Überprüfungsergebnis wird im selben Dialogfeld angezeigt.

### Aktivieren der Smart-Tagging-Funktion im Workflow [!UICONTROL DAM Update Asset] (optional) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Gehen Sie in [!DNL Experience Manager] zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.

1. Wählen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** das Workflow-Modell **[!UICONTROL DAM Update Asset]** aus.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

1. Erweitern Sie das Seitenbedienfeld, um die Schritte anzuzeigen. Ziehen Sie den Schritt **[!UICONTROL Asset intelligent taggen]**, der im Abschnitt „DAM-Workflow“ verfügbar ist, und platzieren Sie ihn nach dem Schritt **[!UICONTROL Prozessminiaturansichten]**.

   ![Schritt des Hinzufügens von Smart-Tag-Assets nach dem Schritt des Verarbeitens von Miniaturansichten im Workflow „DAM-Update-Asset“](assets/smart-tag-in-dam-update-asset-workflow.png)

1. Öffnen Sie die Eigenschaften des Schritts, um die Details zu ändern. Stellen Sie unter **[!UICONTROL Erweiterte Einstellungen]** sicher, dass die Option **[!UICONTROL Handler-Erweiterung]** ausgewählt ist.

   ![Konfigurieren des Workflows „DAM-Update-Asset“ und Hinzufügen des Schritts „;Smart-Tag“](assets/smart-tag-step-properties-workflow1.png)

1. Wählen Sie auf der Registerkarte **[!UICONTROL Argumente]** die Option **[!UICONTROL Fehler ignorieren]**, wenn der Workflow auch dann abgeschlossen werden soll, falls der automatische Tag-Schritt fehlschlägt.

   Um Assets unabhängig davon mit Tags zu versehen, ob die Smart-Tagging-Funktion für Ordner aktiviert ist, wählen Sie **[!UICONTROL Smart-Tag-Markierung ignorieren]** aus.

   ![Konfigurieren des Workflows „DAM Update Asset“, um den Schritt „Smart-Tag“ hinzuzufügen und den erweiterten Handler-Modus auszuwählen](assets/smart-tag-step-properties-workflow2.png)

1. Klicken Sie auf das Symbol ![Fertig](assets/do-not-localize/check-ok-done-icon.png), um den Prozessschritt zu schließen.

1. Klicken Sie auf **[!UICONTROL Synchronisieren]**, um den Workflow zu speichern.

## Trainieren des Smart Content Service {#training-the-smart-content-service}

Damit der Smart Content Service die Taxonomie Ihres Unternehmens erkennen kann, sollten Sie den Dienst auf einen Asset-Satz ausführen, der bereits für Ihr Unternehmen relevante Tags enthält. Damit Sie Ihre Markenbilder effektiv mit Tags versehen können, müssen die zum Trainieren des Smart Content Service verwendeten Bilder bestimmten Richtlinien entsprechen. Nach dem Training kann der Dienst dieselbe Taxonomie auf einen ähnlichen Satz von Assets anwenden.

Sie können den Dienst mehrmals trainieren, um die Fähigkeit zu verbessern, relevante Tags anzuwenden. Führen Sie nach jedem Trainings-Zyklus einen Tagging-Workflow aus und überprüfen Sie, ob Ihre Assets mit den richtigen Tags versehen sind.

Sie können den Smart Content Service regelmäßig oder bei Bedarf trainieren.

>[!NOTE]
>
>Der Trainings-Workflow wird nur für Ordner ausgeführt.

### Richtlinien für das Training {#guidelines-for-training}

Für optimale Ergebnisse sollten Bilder im Trainingssatz folgende Richtlinien einhalten:

**Menge und Größe:** Mindestens 30 Bilder pro Tag. Mindestens 500 Pixel auf der längeren Seite.

**Kohärenz**: Bilder, die für ein bestimmtes Tag verwendet werden, sind optisch ähnlich.

So ist es beispielsweise nicht empfehlenswert, all diese Bilder mit dem Tag `my-party` zu versehen (zu Trainings-Zwecken), da sie einander visuell nicht ähnlich sind.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/coherence.png)

**Abdeckung:** Bei den Trainings-Bildern muss eine ausreichende Vielfalt vorhanden sein. Der Grundgedanke ist, einige Beispiele bereitzustellen, die jedoch verhältnismäßig vielfältig sind, sodass Experience Manager lernt, sich auf die richtigen Dinge zu konzentrieren. Wenn Sie dasselbe Tag auf visuell unähnliche Bilder anwenden, schließen Sie mindestens fünf Beispiele für jeden Typ ein.

Beispiel: Schließen Sie für das Tag *model-down-pose* mehr Trainings-Bilder ein, die dem hervorgehobenen Bild unten ähnlich sind, sodass der Service ähnliche Bilder beim Hinzufügen von Tags genauer identifizieren kann.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/coverage_1.png)

**Ablenkung/Verdeckung**: Der Service kann besser mit Bildern trainieren, die weniger Ablenkungen enthalten (hervorgehobenen Hintergründe oder Elemente ohne Bezug wie Objekte/Personen neben dem Hauptsubjekt).

Beispiel: Für das Tag *casual-shoe* ist das zweite Bild kein guter Kandidat für das Training.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/distraction.png)

**Vollständigkeit:** Wenn ein Bild für mehr als ein Tag qualifiziert ist, fügen Sie alle entsprechenden Tags hinzu, bevor Sie das Bild für eine Schulung hinzufügen. Beispiel: Fügen Sie im Falle von Tags wie `raincoat` und `model-side-view` beide Tags zum entsprechenden Asset hinzu, bevor Sie dieses für Trainingszwecke verwenden.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/completeness.png)

>[!NOTE]
>
>Die Fähigkeit des Smart Content Service, aus Ihren Tags zu lernen und diese Tags auf andere Bilder anzuwenden, hängt von der Qualität der für das Training verwendeten Bilder ab. Um die bestmöglichen Ergebnisse zu erzielen, empfiehlt Adobe die Verwendung visuell ähnlicher Bilder, um den Service für die einzelnen Tags zu trainieren.

### Regelmäßiges Training {#periodic-training}

Sie können festlegen, dass der Smart Content Service regelmäßig mit den Assets und zugewiesenen Tags in einem Ordner trainiert wird. Öffnen Sie die Seite [!UICONTROL Eigenschaften] Ihres Asset-Ordners, wählen Sie **[!UICONTROL Smart-Tags aktivieren]** in der Registerkarte **[!UICONTROL Details]** aus und speichern Sie die Änderungen.

![enable_smart_tags](assets/enable_smart_tags.png)

Wenn Sie diese Option für einen Ordner auswählt haben, führt [!DNL Experience Manager] automatisch einen Trainings-Workflow aus, um den Smart Content Service mit den Assets im Ordner und deren Tags zu trainieren. Standardmäßig wird der Trainings-Workflow wöchentlich samstags um 12 :30 ausgeführt.

### Training bei Bedarf {#on-demand-training}

Sie können den Smart Content Service bei Bedarf über die Workflow-Konsole trainieren.

1. Gehen Sie in der [!DNL Experience Manager]-Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** den Workflow **[!UICONTROL Smart-Tags-Training]** aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Workflow starten]**.
1. Suchen Sie im Dialogfeld **[!UICONTROL Workflow ausführen]** nach dem Payload-Ordner, der die mit Tags versehenen Assets für das Trainieren des Services enthält.
1. Geben Sie einen Titel für den Workflow an und fügen Sie einen Kommentar hinzu. Klicken Sie dann auf **[!UICONTROL Ausführen]**. Die Assets und Tags werden für das Training übermittelt.

   ![workflow_dialog](assets/workflow_dialog.png)

>[!NOTE]
>
>Wenn die Assets in einem Ordner für das Training verarbeitet wurden, werden für zukünftige Trainingszyklen nur die modifizierten Assets verarbeitet.

### Anzeigen von Trainings-Berichten {#viewing-training-reports}

Um sicherzustellen, dass der Smart Content Service auf Ihre Tags im Asset-Trainingssatz trainiert ist, überprüfen Sie den Bericht zum Trainings-Workflow über die Berichte-Konsole.

1. Gehen Sie in der [!DNL Experience Manager]-Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Berichte]**.
1. Klicken Sie auf der Seite **[!UICONTROL Asset-Berichte]** auf **[!UICONTROL Erstellen]**.
1. Wählen Sie den Bericht **[!UICONTROL Smart-Tags-Training]** aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Weiter]**.
1. Geben Sie einen Titel und eine Beschreibung für den Bericht an. Lassen Sie unter **[!UICONTROL Berichtplanen]** die Option **[!UICONTROL Jetzt]** aktiviert. Wenn Sie den Bericht für einen späteren Zeitpunkt planen möchten, wählen Sie **[!UICONTROL Später]** und geben Sie ein Datum und eine Uhrzeit an. Klicken Sie dann in der Symbolleiste auf **[!UICONTROL Erstellen]**.
1. Wählen Sie auf der Seite **[!UICONTROL Asset-Berichte]** den erstellten Bericht aus. Um den Bericht anzuzeigen, klicken Sie in der Symbolleiste auf **[!UICONTROL Ansicht]**.
1. Prüfen Sie die Details des Berichts.

   Der Bericht zeigt den Trainings-Status der von Ihnen trainierten Tags an. Grün gibt in der Spalte **[!UICONTROL Trainingsstatus]** an, dass der Smart Content Service für das Tag trainiert wird. Gelb bedeutet, dass der Service für ein bestimmtes Tag nicht vollständig trainiert ist. Fügen Sie in diesem Fall weitere Bilder mit dem jeweiligen Tag hinzu und führen Sie den Trainings-Workflow aus, um den Service vollständig für das Tag zu trainieren.

   Wenn Ihre Tags nicht in diesem Bericht angezeigt werden, führen Sie den Trainings-Workflow für diese Tags erneut aus.

1. Um den Bericht herunterzuladen, wählen Sie ihn aus der Liste aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Herunterladen]**. Der Bericht kann als Microsoft Excel-Tabellenkalkulation heruntergeladen werden.

## Beschränkungen {#limitations}

* Optimiertes Smart-Tagging basiert auf Lernmodellen von Bildern und den zugehörigen Tags. Diese Modelle können Tags nicht immer perfekt identifizieren. Bei der aktuellen Version des Smart Content Service bestehen folgende Einschränkungen:

   * Subtile Unterschiede in Bildern können nicht erkannt werden. Beispiel: T-Shirts mit schmalem oder normalem Schnitt.
   * Tags können nicht anhand von winzigen Mustern oder Teilen eines Bildes identifiziert werden. Beispiel: Logos auf T-Shirts.
   * Tagging wird in den Gebietsschemata unterstützt, in denen [!DNL Experience Manager] unterstützt wird.

* Verwenden Sie [!DNL Assets]-OmniSearch (Volltextsuche), um nach Assets mit Smart-Tags (normal oder erweitert) zu suchen. Es gibt kein separates Suchprädikat für Smart-Tags.

>[!MORELIKETHIS]
>
>* [Überblick über Smart Tags und deren Training](enhanced-smart-tags.md)
>* [Fehlerbehebung für Smart-Tags hinsichtlich OAuth-Anmeldedaten](config-oauth.md)
>* [Video-Tutorial zu Smart-Tags](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html?lang=de)
