---
title: JBoss-Domänencontroller kann nicht gestartet werden
description: In AEM Forms 6.5.1 LTS-Cluster-Bereitstellungen mit JBoss EAP 8 kann die Konfigurationsdatei doppelte -Tags enthalten.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
source-git-commit: 259cb81eb9652405dc7270535cbf9deb996ad2ac
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 1%

---


# JBoss-Domänencontroller kann nicht gestartet werden

## Problem

In **AEM Forms 6.5.1 LTS**-Cluster-Bereitstellungen mit **JBoss EAP 8** wird die Konfigurationsdatei
`<JBOSS_HOME>/domain/configuration/domain_oracle.xml` (und datenbankspezifische Varianten) können ein (**öffnendes `<security>`-Tag)**.

Dies führt zu einer **ungültigen XML** Konfiguration, was zu einem **JBoss Domain Controller-Startfehler)** einer erfolgreichen Cluster-Initialisierung führt.

## Gilt für

* **Product:** AEM Forms 6.5.1 LTS
* **Bereitstellungstyp:** Cluster
* **Anwendungsserver:** JBoss EAP 8.x
* **Konfigurationsdateien:**

   * `<JBOSS_HOME>/domain/configuration/domain_oracle.xml`
   * `<JBOSS_HOME>/domain/configuration/domain_mysql.xml`
   * `<JBOSS_HOME>/domain/configuration/domain_mssql.xml`

## Schritte zur Fehlerbehebung

1. Während des Starts des Domain-Controllers können die folgenden Fehler auftreten:

   * `WFLYCTL0198: Unexpected element 'security'`
   * `IJ010061: Unexpected element: security`

2. Öffnen Sie die entsprechende Konfigurationsdatei:

   ```
   <JBOSS_HOME>/domain/configuration/domain_oracle.xml
   (or domain_mysql.xml / domain_mssql.xml)
   ```

3. Suchen Sie das Duplikat `<security>` öffnenden -Tags.

   **Falsche Konfiguration:**

   ```xml
   <security>
       <security>
           <user-name>adobe</user-name>
           <credential-reference store="db-creds" alias="EncryptDBPassword"/>
       </security>
   ```

4. Entfernen Sie das zusätzliche öffnende `<security>`-Tag, damit die Konfiguration wie unten dargestellt korrigiert wird:

   **Korrekte Konfiguration:**

   ```xml
   <security>
       <user-name>adobe</user-name>
       <credential-reference store="db-creds" alias="EncryptDBPassword"/>
   </security>
   ```

5. Speichern Sie die Datei und starten Sie den JBoss Domain Controller.

6. Stellen Sie sicher, dass dieselbe validierte Konfiguration konsistent auf alle Cluster-Knoten angewendet wird.
