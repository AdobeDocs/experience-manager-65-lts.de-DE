---
title: Erweiterte Systemattribute konfigurieren
description: Sie können auf der Seite „Erweiterte Systemattribute konfigurieren“ bestimmte Einstellungen in der Konfigurationsdatei ändern, ohne die Datei exportieren, bearbeiten und importieren zu müssen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: f1a68461-c66a-4ea4-902b-644c620ea3f6
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 100%

---

# Erweiterte Systemattribute konfigurieren {#configure-advanced-system-attributes}

Sie können auf der Seite „Erweiterte Systemattribute konfigurieren“ bestimmte Einstellungen in der Konfigurationsdatei ändern, ohne die Datei exportieren, bearbeiten und importieren zu müssen. (Siehe [Importieren und Exportieren der Konfigurationsdatei](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file).)

1. Klicken Sie in der Administration-Console auf **[!UICONTROL „Einstellungen“ > „User Management“ > „Konfiguration“ > „Erweiterte Systemattribute konfigurieren“]**.
1. (Optional) Ändern Sie folgende Sitzungsattribute:

   **Sitzungszeitlimit-Grenzwert (Minuten):** Der Zeitraum in Minuten, nach dem ein Benutzer automatisch vom System abgemeldet wird. Standardmäßig beträgt das Zeitlimit von AEM Forms-Komponenten wie Workbench, unabhängig von Aktivität bzw. Inaktivität, zwei Stunden. Der Benutzer muss sich dann erneut anmelden. Gültig sind Werte von `1` bis `1440`. Der Standardwert ist `120` (2 Stunden). Diese Einstellung aktualisiert den Eintragsschlüssel `SAML/Producer/assertionValidityInMinutes` in der Konfigurationsdatei.

   >[!NOTE]
   >
   >Setzen Sie den Sitzungszeitlimit-Grenzwert nicht auf unter 10 Minuten, da dies zu Fehlern im System führen kann. Der empfohlene Wert beträgt 10 – 120 (Minuten).

   **Assertionsschwellenwert (Sekunden):** Dieser Wert gibt einen Pufferzeitraum an, um den Verzögerungen aufgrund von Systemzeitdifferenzen zwischen AEM Forms-Anwendungsservern in einem Cluster versetzt werden sollen. AEM Forms datiert die Anmeldezeit eines Benutzers um den in dieser Eigenschaft angegebenen Zeitraum (in Sekunden) zurück. Gültig sind Werte von `0` bis `3600`. Der Standardwert ist `60`. Diese Einstellung aktualisiert den Eintragsschlüssel `SAML/Producer/assertionThresholdInSeconds` in der Konfigurationsdatei.

   **Maximal zulässige Anzahl von Erneuerungen einer Assertion:** Die maximale Anzahl, wie oft die Sitzung eines Benutzers transparent erneuert werden kann, ohne dass eine erneute Anmeldung erforderlich wird. Gültig sind Werte von `0` bis `9999`. Der Wert `0` bedeutet, dass die Assertionen nicht erneuert werden. Der Standardwert ist 10. Diese Einstellung aktualisiert den Eintragsschlüssel `SAML/Producer/maxAssertionRenewalCount` in der Konfigurationsdatei.

1. (Optional) Ändern Sie folgende Ordnersynchronisierungsattribute:

   **Protokollierung der Synchronisationsstatistiken:** Gibt an, ob User Management während des Synchronisationsprozesses detaillierte Statistiken protokolliert. (Siehe [Detaillierte Protokollierung während der Synchronisierung aktivieren oder deaktivieren](/help/forms/using/admin-help/synchronizing-directories.md#enable-or-disable-detailed-logging-during-synchronization).)

   **Synchronisations-Finisher Cron Expression:** Das Intervall, in dem User Management fehlgeschlagene Synchronisationen wiederholt. (Siehe [Wiederholungsoptionen für die Ordnersynchronisierung konfigurieren](/help/forms/using/admin-help/synchronizing-directories.md#configure-the-directory-synchronization-retry-option).)

   **Cluster Job Lock Timeout In Minutes:** Wird in Clusterumgebungen verwendet. Wenn die Synchronisation auf einem Knoten fehlschlägt und die Clustersperre nicht beendet wurde, gibt dieser Wert die Anzahl der Minuten an, die ein anderer Knoten wartet, bevor er die Sperre erzwingt. Der Standardwert ist `15` Minuten. Gültig sind Werte von `1` bis `1440` Minuten.

1. (Optional) Ändern Sie folgende Attribute und klicken Sie dann auf **[!UICONTROL OK]**:

   **User Manager-Ereignisprüfung:** Wählen Sie diese Option, um die Prüfung von Ordnersynchronisierungsereignissen sowie von Authentifizierungsereignissen wie Erfolg, Fehler und Sperrung zu aktivieren. Standardmäßig ist diese Option nur aktiviert, wenn eine Komponente installiert ist, die Prüfungen erfordert, z. B Rights Management. Diese Einstellung aktualisiert den Eintragsschlüssel `APSAuditService` in der Konfigurationsdatei.

   **Automatische Erstellung einer dynamischen Gruppe:** Aktiviert die automatische Erstellung dynamischer Gruppen auf Basis von E-Mail-Domains. (Siehe [Dynamische Gruppe erstellen](/help/forms/using/admin-help/creating-configuring-groups.md#create-a-dynamic-group).)

Sie können auch die ursprünglichen User Management-Einstellungen wiederherstellen, indem Sie auf „Neu laden“ klicken.
