---
title: Java API-Schnellstart (SOAP) für den Task Manager-Dienst
description: Verwenden Sie den Task-Manager-Dienst, um Aufgaben zuzuweisen, Aufgaben zu sperren, den Benutzern zugewiesene Aufgaben abzurufen, Formulardaten aus Aufgaben abzurufen, Formulardaten zu ändern, Dateianhänge abzurufen und Aufgabeninformationen abzurufen.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, APIs & Integrations,AEM Forms on JEE
hide: true
hidefromtoc: true
exl-id: e319bb36-d32b-4535-8bdd-33afec822fc9
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 100%

---

# Task-Manager-Dienst Java API Schnellstart (SOAP) {#task-manager-service-java-api-quickstart-soap}

Für den Task-Manager-Dienst sind folgende Schnellstarts verfügbar.

[Schnellstart (SOAP-Modus): Zuweisung von Aufgaben mit der Java-API](task-manager-service-java-api.md#quick-start-soap-mode-assigning-tasks-using-the-java-api)

[Schnellstart (SOAP-Modus): Sperren von Aufgaben mit der Java-API](task-manager-service-java-api.md#quick-start-soap-mode-locking-tasks-using-the-java-api)

[Schnellstart (SOAP-Modus): Abrufen von Benutzern zugewiesenen Aufgaben mit der Java-API](task-manager-service-java-api.md#quick-start-soap-mode-retrieving-tasks-assigned-to-users-using-the-java-api)

[Schnellstart (SOAP-Modus): Abrufen von Formulardaten aus Aufgaben mit der Java-API](task-manager-service-java-api.md#quick-start-soap-mode-retrieving-form-data-from-tasks-using-the-java-api)

[Schnellstart (SOAP-Modus): Ändern von Formulardaten mit der Java-API](task-manager-service-java-api.md#quick-start-soap-mode-modifying-form-data-using-the-java-api)

[Schnellstart (SOAP-Modus): Abrufen von Dateianhängen aus Aufgaben mit der Java-API](task-manager-service-java-api.md#quick-start-soap-mode-retrieving-file-attachments-from-tasks-using-the-java-api)

[Schnellstart (SOAP-Modus): Abrufen von Aufgabeninformationen mit der Java-API](task-manager-service-java-api.md#quick-start-soap-mode-retrieving-task-information-using-the-java-api)

AEM Forms-Vorgänge können mit der stark typisierten AEM Forms-API ausgeführt werden, und der Verbindungsmodus sollte auf SOAP festgelegt werden.

>[!NOTE]
>
>Mit der Webdienst-API können Sie nicht nach Aufgaben suchen, die Benutzern zugewiesen wurden. Der Grund, warum Sie die Methode `taskList` nicht aufrufen können, liegt darin, dass sie ein notwendiger Methodenaufruf ist, um diese Aufgabe auszuführen.

>[!NOTE]
>
>Der Schnellstart in „Programmieren mit AEM Forms“ basiert auf dem Formular-Server-Betriebssystem. Wenn Sie jedoch ein anderes Betriebssystem, z. B. UNIX, verwenden, ersetzen Sie die Windows-spezifischen Pfade durch Pfade, die von dem jeweiligen Betriebssystem unterstützt werden. Wenn Sie einen anderen J2EE-Anwendungs-Server verwenden, müssen Sie ebenfalls sicherstellen, dass Sie gültige Verbindungseigenschaften angeben. Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Schnellstart (SOAP-Modus): Zuweisung von Aufgaben mit der Java-API {#quick-start-soap-mode-assigning-tasks-using-the-java-api}

Das folgende Java-Codebeispiel weist einem Benutzer namens „Tony Blue“ eine Aufgabe zu.

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-taskmanager-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
    * 4. activation.jar (required for SOAP mode)
    * 5. axis.jar (required for SOAP mode)
    * 6. commons-codec-1.3.jar (required for SOAP mode)
    * 7. commons-collections-3.2.jar  (required for SOAP mode)
    * 8. commons-discovery.jar (required for SOAP mode)
    * 9. commons-logging.jar (required for SOAP mode)
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode)
    * 12. jaxrpc.jar (required for SOAP mode)
    * 13. log4j.jar (required for SOAP mode)
    * 14. mail.jar (required for SOAP mode)
    * 15. saaj.jar (required for SOAP mode)
    * 16. wsdl4j.jar (required for SOAP mode)
    * 17. xalan.jar (required for SOAP mode)
    * 18. xbean.jar (required for SOAP mode)
    * 19. xercesImpl.jar (required for SOAP mode)
     * 20. adobe-workflow-client-sdk.jar
     *
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to
     * your local development environment and then include the 3 JBoss JAR files in your class path
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     *
     * <install directory>/jboss/bin/client
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files in the following
     * path
     * <install directory>/sdk/client-libs/thirdparty
     *
     * For information about the SOAP
     * mode and the additional JAR files that need to be included,
     * see "Setting connection properties" in Programming
     * with AEM Forms
     *
     * For complete details about the location of the AEM Forms JAR files,
     * see "Including AEM Forms Java library files" in Programming
     * with AEM Forms
     */
 
 import java.util.*;
 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.idp.taskmanager.dsc.client.task.TaskManager;
 import com.adobe.idp.taskmanager.dsc.client.*;
 import com.adobe.idp.um.api.infomodel.PrincipalSearchFilter;
 import com.adobe.idp.um.api.infomodel.User;
 import com.adobe.livecycle.usermanager.client.DirectoryManagerServiceClient;
 
 public class AssignTask {
 
     public static void main(String[] args) {
 
         try{
         //Set connection properties required to invoke AEM Forms
         Properties connectionProps = new Properties();
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "tblue");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
         //Create a ServiceClientFactory object
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
         //Create a TaskManager object
         TaskManager myTaskManager = TaskManagerClientFactory.getTaskManager(myFactory);
 
         //Get the user identifer by calling
         //a user-defined method
         String userID = getUserId(myFactory);
 
         //Forward task to another user
         myTaskManager.forwardTask(343,userID);
         }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 
 
     //This method returns the identifier value of tony blue
      static private String getUserId(ServiceClientFactory myFactory){
       String oid = "";
       try{
 
           //Create a DirectoryManagerServiceClient object
           DirectoryManagerServiceClient dirClient = new DirectoryManagerServiceClient(myFactory);
 
          //Find a local user
          PrincipalSearchFilter psf = new PrincipalSearchFilter();
          psf.setUserId("tblue");
          List principalList = dirClient.findPrincipals(psf);
          Iterator pit = principalList.iterator();
 
          User testUser = null;
          if (pit.hasNext())
          {
              //Obtain the principals object identifier
              testUser = (User)(pit.next());
          }
          oid = testUser.getOid();
          }
 
           catch(Exception e)
           {
               e.printStackTrace();
           }
               return oid;
       }
 }
 
 
 
```

## Schnellstart (SOAP-Modus): Sperren von Aufgaben mit der Java-API {#quick-start-soap-mode-locking-tasks-using-the-java-api}

Das folgende Java-Codebeispiel sperrt eine Aufgabe, die dem Aufgabenkennungswert 2 entspricht.

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-taskmanager-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
    * 4. activation.jar (required for SOAP mode)
    * 5. axis.jar (required for SOAP mode)
    * 6. commons-codec-1.3.jar (required for SOAP mode)
    * 7. commons-collections-3.2.jar  (required for SOAP mode)
    * 8. commons-discovery.jar (required for SOAP mode)
    * 9. commons-logging.jar (required for SOAP mode)
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode)
    * 12. jaxrpc.jar (required for SOAP mode)
    * 13. log4j.jar (required for SOAP mode)
    * 14. mail.jar (required for SOAP mode)
    * 15. saaj.jar (required for SOAP mode)
    * 16. wsdl4j.jar (required for SOAP mode)
    * 17. xalan.jar (required for SOAP mode)
    * 18. xbean.jar (required for SOAP mode)
    * 19. xercesImpl.jar (required for SOAP mode)
     * 20. adobe-workflow-client-sdk.jar
     *
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to
     * your local development environment and then include the 3 JBoss JAR files in your class path
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     *
     * <install directory>/jboss/bin/client
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files in the following
     * path
     * <install directory>/sdk/client-libs/thirdparty
     *
     * For information about the SOAP
     * mode and the additional JAR files that need to be included,
     * see "Setting connection properties" in Programming
     * with AEM Forms
     */
 
 import java.util.*;
 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.idp.taskmanager.dsc.client.task.TaskManager;
 import com.adobe.idp.taskmanager.dsc.client.*;
 
 public class LockTask {
 
     public static void main(String[] args) {
 
     try{
         //Set connection properties required to invoke AEM Forms
         Properties connectionProps = new Properties();
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "tblue");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
         //Create a ServiceClientFactory object
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
         //Create a TaskManager object
         TaskManager myTaskManager = TaskManagerClientFactory.getTaskManager(myFactory);
 
         //Lock the task that corresponds to task identifier 2
         myTaskManager.lockTask(2);
         }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
 
```

## Schnellstart (SOAP-Modus): Abrufen von Benutzern zugewiesenen Aufgaben mit der Java-API {#quick-start-soap-mode-retrieving-tasks-assigned-to-users-using-the-java-api}

Das folgende Java-Codebeispiel ruft alle Aufgaben ab, die einem Benutzer namens *tony blue* zugewiesen sind. Beachten Sie, dass dieser Benutzer in den Verbindungseigenschaften angegeben ist. Es werden Informationen zu den zurückgegebenen Aufgaben angezeigt, wie beispielsweise ihr Kennungswert und ihre Beschreibung.

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-taskmanager-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
    * 4. activation.jar (required for SOAP mode)
    * 5. axis.jar (required for SOAP mode)
    * 6. commons-codec-1.3.jar (required for SOAP mode)
    * 7. commons-collections-3.2.jar  (required for SOAP mode)
    * 8. commons-discovery.jar (required for SOAP mode)
    * 9. commons-logging.jar (required for SOAP mode)
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode)
    * 12. jaxrpc.jar (required for SOAP mode)
    * 13. log4j.jar (required for SOAP mode)
    * 14. mail.jar (required for SOAP mode)
    * 15. saaj.jar (required for SOAP mode)
    * 16. wsdl4j.jar (required for SOAP mode)
    * 17. xalan.jar (required for SOAP mode)
    * 18. xbean.jar (required for SOAP mode)
    * 19. xercesImpl.jar (required for SOAP mode)
     * 20. adobe-workflow-client-sdk.jar
     *
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to
     * your local development environment and then include the 3 JBoss JAR files in your class path
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     *
     * <install directory>/jboss/bin/client
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files in the following
     * path
     * <install directory>/sdk/client-libs/thirdparty
     *
     * For information about the SOAP
     * mode and the additional JAR files that need to be included,
     * see "Setting connection properties" in Programming
     * with AEM Forms
     */
 
 import java.util.*;
 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.idp.taskmanager.dsc.client.query.StatusFilter;
 import com.adobe.idp.taskmanager.dsc.client.query.TaskFilter;
 import com.adobe.idp.taskmanager.dsc.client.query.TaskRow;
 import com.adobe.idp.taskmanager.dsc.client.*;
 
 public class RetrieveTaskInfo {
 
     public static void main(String[] args) {
 
         try{
              //Set connection properties required to invoke AEM Forms
               Properties connectionProps = new Properties();
               connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
      connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
               connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
               connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
               connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a TaskManagerQueryService object
             TaskManagerQueryService queryManager = TaskManagerClientFactory.getQueryManager(myFactory);
 
             //Define search criteria by performing a search on
             //Assigned tasks (tasks assigned to the user specified
             //in connection properties)
             TaskFilter filter = queryManager.newTaskFilter();
             StatusFilter sf = filter.newStatusFilter();
             sf.addStatus(StatusFilter.assigned);
             filter.setStatusFiltering(sf);
 
             //Perform the search
             List result = queryManager.taskList(filter);
 
             //Create an Iterator object and iterate through
             //the List object
             Iterator iter = result.iterator();
             int i = 0 ;
 
             while (iter.hasNext()) {
 
                 TaskRow myTask = (TaskRow)iter.next();
 
                 //Get the task identifier value
                 long taskId = myTask.getTaskId();
 
                 //Get the status of the task
                 long taskStatus = myTask.getTaskStatus();
 
                 //Get the name of process on which this task is based
                 String processName = myTask.getProcessName();
 
                 //Get the task description
                 String taskDes = myTask.getDescription();
 
                 System.out.println("The task identifier is "+taskId +"\n"+
                  "The status of the task is "+taskStatus +"\n"+
                  "The name of the process on which the task is based is "+processName +"\n"+
                  "The task description is "+taskDes);
                  i++ ;
                  }
             }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
```

## Schnellstart (SOAP-Modus): Abrufen von Formulardaten aus Aufgaben mit der Java-API {#quick-start-soap-mode-retrieving-form-data-from-tasks-using-the-java-api}

Das folgende Java-Codebeispiel ruft Formulardaten von einer Aufgabe mit dem Kennungswert 304 ab. Die Formulardaten werden in eine XML-Datei namens *FormData.xml* geschrieben, die sich unter „C:\Adobe“ befindet.

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-taskmanager-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
    * 4. activation.jar (required for SOAP mode)
    * 5. axis.jar (required for SOAP mode)
    * 6. commons-codec-1.3.jar (required for SOAP mode)
    * 7. commons-collections-3.2.jar  (required for SOAP mode)
    * 8. commons-discovery.jar (required for SOAP mode)
    * 9. commons-logging.jar (required for SOAP mode)
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode)
    * 12. jaxrpc.jar (required for SOAP mode)
    * 13. log4j.jar (required for SOAP mode)
    * 14. mail.jar (required for SOAP mode)
    * 15. saaj.jar (required for SOAP mode)
    * 16. wsdl4j.jar (required for SOAP mode)
    * 17. xalan.jar (required for SOAP mode)
    * 18. xbean.jar (required for SOAP mode)
    * 19. xercesImpl.jar (required for SOAP mode)
      * 20. adobe-workflow-client-sdk.jar
     *
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to
     * your local development environment and then include the 3 JBoss JAR files in your class path
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     *
     * <install directory>/jboss/bin/client
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files in the following
     * path
     * <install directory>/sdk/client-libs/thirdparty
     *
     * For information about the SOAP
     * mode and the additional JAR files that need to be included,
     * see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.io.File;
 import java.util.*;
 
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 
 import com.adobe.idp.taskmanager.dsc.client.*;
 import com.adobe.idp.taskmanager.dsc.client.task.FormInstance;
 import com.adobe.idp.taskmanager.dsc.client.task.TaskInfo;
 import com.adobe.idp.taskmanager.dsc.client.task.TaskManager;
 
 public class RetrieveFormData {
 
     public static void main(String[] args) {
 
         try{
              //Set connection properties required to invoke AEM Forms
               Properties connectionProps = new Properties();
               connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
      connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
               connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
               connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
               connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a TaskManager object
             TaskManager myTaskManager = TaskManagerClientFactory.getTaskManager(myFactory);
 
             //Retrieve information about task 304
             long taskId = 304;
             TaskInfo tInfo = myTaskManager.getTaskInfo(taskId);
 
             //Retrieve the form instance associated with task 304
             FormInstance[] fi = tInfo.getTaskItems();
             long formInstanceId = fi[0].getFormInstanceId();
             FormInstance newfi = myTaskManager.getFormInstanceForTask(taskId, formInstanceId, true);
 
             //Get data in the form and
             //write the data to FormData.xml
             Document doc = newfi.getDocument();
             File myTestFile = new File("C:\\Adobe\FormData.xml");
             doc.copyToFile(myTestFile);
             }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
 
 
```

## Schnellstart (SOAP-Modus): Ändern von Formulardaten mit der Java-API {#quick-start-soap-mode-modifying-form-data-using-the-java-api}

Das folgende Java-Code-Beispiel aktualisiert ein Formular mit Daten, die sich in der Datei *FormData.xml* befinden.

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-taskmanager-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
    * 4. activation.jar (required for SOAP mode)
    * 5. axis.jar (required for SOAP mode)
    * 6. commons-codec-1.3.jar (required for SOAP mode)
    * 7. commons-collections-3.2.jar  (required for SOAP mode)
    * 8. commons-discovery.jar (required for SOAP mode)
    * 9. commons-logging.jar (required for SOAP mode)
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode)
    * 12. jaxrpc.jar (required for SOAP mode)
    * 13. log4j.jar (required for SOAP mode)
    * 14. mail.jar (required for SOAP mode)
    * 15. saaj.jar (required for SOAP mode)
    * 16. wsdl4j.jar (required for SOAP mode)
    * 17. xalan.jar (required for SOAP mode)
    * 18. xbean.jar (required for SOAP mode)
    * 19. xercesImpl.jar (required for SOAP mode)
      * 20. adobe-workflow-client-sdk.jar
     *
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to
     * your local development environment and then include the 3 JBoss JAR files in your class path
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     *
     * <install directory>/jboss/bin/client
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files in the following
     * path
     * <install directory>/sdk/client-libs/thirdparty
     *
     * For information about the SOAP
     * mode and the additional JAR files that need to be included,
     * see "Setting connection properties" in Programming
     * with AEM Forms
     */
 
 import java.io.FileInputStream;
 import java.io.InputStream;
 import java.util.*;
 
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 
 import com.adobe.idp.taskmanager.dsc.client.*;
 import com.adobe.idp.taskmanager.dsc.client.task.FormInstance;
 import com.adobe.idp.taskmanager.dsc.client.task.SaveTaskResult;
 import com.adobe.idp.taskmanager.dsc.client.task.TaskManager;
 
 public class SetFormData {
 
     public static void main(String[] args) {
     try{
         //Set connection properties required to invoke AEM Forms
         Properties connectionProps = new Properties();
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "tblue");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
         //Create a ServiceClientFactory object
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
         //Create a TaskManager object
         TaskManager myTaskManager = TaskManagerClientFactory.getTaskManager(myFactory);
 
         //Specify form data that is used to update the form
         FileInputStream myData = new FileInputStream("C:\\Adobe\FormData.xml");
         Document doc = new Document(myData);
         InputStream in = doc.getInputStream();
         byte[] formarray = new byte[in.available()];
         in.read(formarray);
 
         //Get an empty form instance
         FormInstance newForm = myTaskManager.getEmptyForm();
         newForm.setTemplatePath("C:\\Adobe\Mortgage.xdp");
         newForm.setXFAData(formarray);
         newForm.setDocument(doc);
 
         //Save the modified form
         SaveTaskResult result = myTaskManager.save(4, newForm);
         System.out.println("ActionFromData= "+result.getActionFromData());
         System.out.println("task id= "+result.getTaskId());
         }
 
     catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
 
 
```

## Schnellstart (SOAP-Modus): Abrufen von Dateianhängen aus Aufgaben mit der Java-API {#quick-start-soap-mode-retrieving-file-attachments-from-tasks-using-the-java-api}

Das folgende Java-Codebeispiel ruft Dateianhänge ab. Jeder Dateianhang wird als TXT-Datei gespeichert.

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-taskmanager-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
    * 4. activation.jar (required for SOAP mode)
    * 5. axis.jar (required for SOAP mode)
    * 6. commons-codec-1.3.jar (required for SOAP mode)
    * 7. commons-collections-3.2.jar  (required for SOAP mode)
    * 8. commons-discovery.jar (required for SOAP mode)
    * 9. commons-logging.jar (required for SOAP mode)
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode)
    * 12. jaxrpc.jar (required for SOAP mode)
    * 13. log4j.jar (required for SOAP mode)
    * 14. mail.jar (required for SOAP mode)
    * 15. saaj.jar (required for SOAP mode)
    * 16. wsdl4j.jar (required for SOAP mode)
    * 17. xalan.jar (required for SOAP mode)
    * 18. xbean.jar (required for SOAP mode)
    * 19. xercesImpl.jar (required for SOAP mode)
     * 20. adobe-workflow-client-sdk.jar
     *
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to
     * your local development environment and then include the 3 JBoss JAR files in your class path
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     *
     * <install directory>/jboss/bin/client
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files in the following
     * path
     * <install directory>/sdk/client-libs/thirdparty
     *
     * For information about the SOAP
     * mode and the additional JAR files that need to be included,
     * see "Setting connection properties" in Programming
     * with AEM Forms
     */
 
 import java.io.File;
 import java.util.*;
 
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.idp.taskmanager.dsc.client.*;
 import com.adobe.idp.taskmanager.dsc.client.task.TaskManager;
 
 public class RetrieveFileAttachments
     {
 
     public static void main(String[] args) {
 
         try{
              //Set connection properties required to invoke AEM Forms
               Properties connectionProps = new Properties();
               connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
      connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
               connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
               connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
               connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a TaskManager object
             TaskManager myTaskManager = TaskManagerClientFactory.getTaskManager(myFactory);
 
             //Retrieve file attachments associated with the task
             List fileAttachments = myTaskManager.getAttachmentListForTask(322);
 
             //Create an Iterator object and iterate through
             //the List object
             Iterator iter = fileAttachments.iterator();
             int i = 0 ;
             while (iter.hasNext()) {
                  Document fileAttachment= (Document)iter.next();
                  File myFile = new File("C:\\FileAtt" +i+".txt");
                  fileAttachment.copyToFile(myFile);
                   i++ ;
               }
             }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
 
 
```

## Schnellstart (SOAP-Modus): Abrufen von Aufgabeninformationen mit der Java-API {#quick-start-soap-mode-retrieving-task-information-using-the-java-api}

Das folgende Java-Codebeispiel ruft alle Aufgaben ab, die auf einem Prozess namens *MortgageLoan - Prebuilt* basieren. Der Status jeder zurückgegebenen Aufgabe wird überprüft, um sicherzustellen, dass es sich um eine abgeschlossene Aufgabe handelt. Informationen wie der Name des Benutzers, der die Aufgabe abgeschlossen hat, und das Datum, an dem die Aufgabe abgeschlossen wurde, werden abgerufen und angezeigt.

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-taskmanager-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
    * 4. activation.jar (required for SOAP mode)
    * 5. axis.jar (required for SOAP mode)
    * 6. commons-codec-1.3.jar (required for SOAP mode)
    * 7. commons-collections-3.2.jar  (required for SOAP mode)
    * 8. commons-discovery.jar (required for SOAP mode)
    * 9. commons-logging.jar (required for SOAP mode)
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode)
    * 12. jaxrpc.jar (required for SOAP mode)
    * 13. log4j.jar (required for SOAP mode)
    * 14. mail.jar (required for SOAP mode)
    * 15. saaj.jar (required for SOAP mode)
    * 16. wsdl4j.jar (required for SOAP mode)
    * 17. xalan.jar (required for SOAP mode)
    * 18. xbean.jar (required for SOAP mode)
    * 19. xercesImpl.jar (required for SOAP mode)
     * 20. adobe-workflow-client-sdk.jar
     *
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to
     * your local development environment and then include the 3 JBoss JAR files in your class path
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     *
     * <install directory>/jboss/bin/client
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files in the following
     * path
     * <install directory>/sdk/client-libs/thirdparty
     *
     * For information about the SOAP
     * mode and the additional JAR files that need to be included,
     * see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.util.*;
 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.idp.taskmanager.dsc.client.query.TaskRow;
 import com.adobe.idp.taskmanager.dsc.client.query.TaskSearchFilter;
 import com.adobe.idp.taskmanager.dsc.client.task.ParticipantInfo;
 import com.adobe.idp.taskmanager.dsc.client.task.TaskInfo;
 import com.adobe.idp.taskmanager.dsc.client.task.TaskManager;
 import com.adobe.idp.taskmanager.dsc.client.*;
 import com.adobe.idp.um.api.infomodel.Principal;
 import com.adobe.livecycle.usermanager.client.DirectoryManagerServiceClient;
 
 public class RetrievingTasks {
 
     public static void main(String[] args) {
 
         try{
             //Set connection properties required to invoke AEM Forms
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
      connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a TaskManagerQueryService object
             TaskManagerQueryService queryManager = TaskManagerClientFactory.getQueryManager(myFactory);
 
             //Create a TaskManager object
             TaskManager taskManager = TaskManagerClientFactory.getTaskManager(myFactory);
 
             //Define search criteria by performing a search on
             //completed tasks
             TaskSearchFilter filter = new TaskSearchFilter();
             filter.setServiceName("MortgageLoan - Prebuilt");
             filter.setAdminIgnoreAllAcls(true);
 
             //Perform the search on tasks
             List result = queryManager.taskSearch(filter);
 
             //Create an Iterator object and iterate through
             //the List object
             Iterator iter = result.iterator();
             int i = 0 ;
             while (iter.hasNext()) {
                 TaskRow myTask = (TaskRow)iter.next();
 
                 //Make sure that the task is completed- 100 represents
                 //a completed task
                 if (myTask.getTaskStatus()== 100)
                 {
                     //Get the name of the user who completed the task
                     long taskId = myTask.getTaskId();
                     TaskInfo taskInfo= taskManager.getTaskInfo(taskId);
                     ParticipantInfo user = taskInfo.getAssignedTo();
                     String userId = user.getSpecifiedUserId();
                     String userName = getUserName(myFactory, userId);
 
                     //Get the name of the process
                     String processName = myTask.getProcessName();
 
                     //Get the completion time
                     Date completionTime = myTask.getCompleteTime();
 
                     //Display task information
                      System.out.println("The task identifier is "+taskId +"\n"+
                     "The name of the user who completed the task is "+ userName +"\n"+
                     "The name of the process on which the task is based is "+ processName+"\n"+
                      "The completion time is "+ completionTime.getDate());
                      i++ ;
                     }
                  }
             }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 
 
     //This method accepts a user Id and returns the corresponding user name
     static private String getUserName(ServiceClientFactory myFactory, String userId){
          String userName = "";
          try{
              //Create a DirectoryManagerServiceClient object
              DirectoryManagerServiceClient dirClient = new DirectoryManagerServiceClient(myFactory);
 
             //Find a local user
             Principal prin = dirClient.findPrincipal(userId);
             userName = prin.getCanonicalName();
             }
          catch(Exception e)
          {
              e.printStackTrace();
          }
          return userName;
       }
     }
 
```
