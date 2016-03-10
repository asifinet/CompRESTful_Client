Angular-JS-RESTfull-Java-App
Angular Js RESTfull -Server and Client Full Master Detail using HTML5,CSS3,JQuery,Angular Js, Java, RESTFull Services Author - Asif Muhammad

RESTFull Service API and Angular JS Client (A Web based Java CRUD Application)
Intro :-

Java CRUD based RESTfull Web Server API and Web Service Client have been developed to provide the client software an ability to retrive,Maniuplate e.g INSERT,UPDATE, DELETE , Query the company and owner related data stored on the MySQL database server through the use of RESTfull Web Service end-points architecture style, which they may be located somewhere in remote location.

    TOC
    ------------------------------------
    A. Technology Stack.
    B. App Components.
    C. System Requirements.
    D. HTTP Web service API CRUD Endpoints Matrix.
    E. Installation Instructions.
    F. App Folder Structure.
    G. Java Core Web API depended Libraries.
    H. Database Name.
    I. Database Connectivity.
    J. Deployment class and web files.
    K. Database tables.
    L. Database Creation Schema Script.
    M. Tables Structure.
    N. Mapped endpoint Java Functions and Parameters.
    O. JSON Output Test Results with SOAP UI.
A. Technology Stack

1. Web Server API.
     a.Java
     b.Spring 4.05
     c.Jackson/ JSON.
     d.POJO classes.
     e.Hibernate/JPA 4.3.5.Final
     f.JDBC
     j.log4j  1.2.17


2.Angular JS Client Technologies.
      a.JRE 1.8
      b.HTML5/DHTML
      c.Angular JS 1.2
      d.CSS3
      e.JavaScript
      f.jQuery
      g.bootstrap
      h.Ionic
      i.JQuery-UI
      j.JSP

3.  Build Configuration using Maven pom.xml
B. App Components

    1. RESTfull Server Java Web API
       a. This Server is build and tested with the below client.
       b. Company RESTfull Server Web API does not provide security to the webservice, Which can be easily achive 
           providing the Spring Root Context using Spring Security feature of 4.0.5
    2. RESTfull Angular JS Client 
       a. The Client is build and tested on Chrome and IE Explore version 10. 
       b. To run the App need to point the URL to http://localhost:8080/CompRESTful_Client/
C. System Requirements.

    1.JDK 1.7, JRE 1.8 
    2.MySQL 5.7 Database
    3.Tomcat Server 7.5
    4.Eclipse Version: Mars.1 Release (4.5.1)   
    5.Chrome Browser/IE above 8
    6.SOAP UI/Curl for testing URI web service endpoints.
D. HTTP Web service API CRUD Endpoints Matrix.

    Sno. URI                                               Function Area  Opperation       By ID   HTTP Method      
    =================================================================================================================
    1.  http://localhost:8080/CompRESTful/company/              Company   Add/Query/Delete compid  GET,POST,DELETE 
    2.  http://localhost:8080/CompRESTful/company/update/       Company   Update           compid  PUT                  3.  http://localhost:8080/CompRESTful/company/owner/        Owner     Add/Query        compid  POST,GET     
    4.  http://localhost:8080/CompRESTful/company/owner/del/    Owner     Delete           compid  DELETE       
    5.  http://localhost:8080/CompRESTful/company/owner/        Owner     Delete           ownerId DELETE       
    6.  http://localhost:8080/CompRESTful/company/owner/update/ Owner      Update          ownerId PUT   

    Sno. URI                                                   Input           Output
    =============================================================================================================
    1.  http://localhost:8080/CompRESTful/company/             ID/JSON Array   JSON Array, HTTP Response 200/500  
    2.  http://localhost:8080/CompRESTful/company/update/      ID/JSON Array   HTTP Response 200/500               
    3.  http://localhost:8080/CompRESTful/company/owner/       ID/JSON Array   JSON Array, HTTP Response 200/500 
    4.  http://localhost:8080/CompRESTful/company/owner/del/   ID              HTTP Response 200/500            
    5.  http://localhost:8080/CompRESTful/company/owner/       ID/JSON Array   HTTP Response 200/500
E. Installation Instructions.

1. Extract the AsifWorkspace.rar file in your c: drive
2. Open the Eclipse Mars ver.1 
3. Switch Workspace from file menu to open AsifWorkspace folder.
4. Go to server panel in eclipse and Start the Server.
5. Make sure there is no Errors in Error Logs.
6. Make Clean build from the Project Main Menu and do Clean Build (optional)
7. Check the URL http://localhost:8080/CompRESTful_Client/ to see if application works perfectly.
F. App Folder Structure.

    1. Web Server API    - CompRESTful
    2. Angular JS Client - CompRESTful_Client


    C:\AsifWorkspace
    |               
    +---CompRESTful
    |   |   .classpath
    |   |   .project
    |   |   pom.xml
    |   |   
    |   +---.settings
    |   |       .jsdtscope
    |   |       org.eclipse.jdt.core.prefs
    |   |       org.eclipse.wst.common.component
    |   |       org.eclipse.wst.common.project.facet.core.xml
    |   |       org.eclipse.wst.jsdt.ui.superType.container
    |   |       org.eclipse.wst.jsdt.ui.superType.name
    |   |       
    |   +---src
    |   |   \---main
    |   |       +---java
    |   |       |   \---com
    |   |       |       \---company
    |   |       |           +---controller
    |   |       |           |       RestController.java
    |   |       |           |       
    |   |       |           +---dao
    |   |       |           |       DataDao.java
    |   |       |           |       DataDaoImpl.java
    |   |       |           |       
    |   |       |           +---model
    |   |       |           |       Company.java
    |   |       |           |       Owner.java
    |   |       |           |       Status.java
    |   |       |           |       
    |   |       |           \---services
    |   |       |                   DataServices.java
    |   |       |                   DataServicesImpl.java
    |   |       |                   
    |   |       +---resources
    |   |       |       log4j.properties
    |   |       |       
    |   |       \---webapp
    |   |           \---WEB-INF
    |   |               \---classes
    |   |                       index.jsp
    |   |                       
    |   +---target
    |   |   \---classes
    |   |       |   log4j.properties
    |   |       |   
    |   |       +---com
    |   |       |   \---company
    |   |       |       +---controller
    |   |       |       |       RestController.class
    |   |       |       |       
    |   |       |       +---dao
    |   |       |       |       DataDao.class
    |   |       |       |       DataDaoImpl.class
    |   |       |       |       
    |   |       |       +---model
    |   |       |       |       Company.class
    |   |       |       |       Owner.class
    |   |       |       |       Status.class
    |   |       |       |       
    |   |       |       \---services
    |   |       |               DataServices.class
    |   |       |               DataServicesImpl.class
    |   |       |               
    |   |       \---WEB-INF
    |   |           \---classes
    |   |                   index.jsp
    |   |                   
    |   \---WebContent
    |       +---META-INF
    |       |       MANIFEST.MF
    |       |       
    |       \---WEB-INF
    |           |   index.jsp
    |           |   spring-config.xml
    |           |   web.xml
    |           |   
    |           \---lib
    |                   antlr-2.7.7.jar
    |                   aopalliance-1.0-sources.jar
    |                   commons-logging-1.1.3.jar
    |                   dom4j-1.6.jar
    |                   gson-2.2.2.jar
    |                   hibernate-commons-annotations-4.0.4.Final.jar
    |                   hibernate-core-4.3.5.Final.jar
    |                   hibernate-entitymanager-4.3.5.Final.jar
    |                   hibernate-jpa-2.1-api-1.0.0.Final.jar
    |                   jackson-core-asl-1.9.10.jar
    |                   jackson-mapper-asl-1.9.10.jar
    |                   jandex-1.1.0.Final.jar
    |                   javassist-3.18.1-GA.jar
    |                   javax.servlet.jar
    |                   jboss-logging-3.1.3.GA.jar
    |                   jboss-logging-annotations-1.2.0.beta1.jar
    |                   jboss-transaction-api_1.2_spec-1.0.0.Final.jar
    |                   jstl-1.2.jar
    |                   log4j-1.2.17.jar
    |                   mysql-connector-java-5.1.6-bin.jar
    |                   spring-aop-4.0.5.RELEASE.jar
    |                   spring-beans-4.0.5.RELEASE.jar
    |                   spring-context-4.0.5.RELEASE.jar
    |                   spring-core-4.0.5.RELEASE.jar
    |                   spring-expression-4.0.5.RELEASE.jar
    |                   spring-jdbc-4.0.5.RELEASE.jar
    |                   spring-orm-4.0.5.RELEASE.jar
    |                   spring-tx-4.0.5.RELEASE.jar
    |                   spring-web-4.0.5.RELEASE.jar
    |                   spring-webmvc-4.0.5.RELEASE.jar
    |                   xml-apis-1.0.b2.jar
    |                   
    +---CompRESTful_Client
    |   |   .classpath
    |   |   .project
    |   |   
    |   +---.settings
    |   |       .jsdtscope
    |   |       org.eclipse.jdt.core.prefs
    |   |       org.eclipse.wst.common.component
    |   |       org.eclipse.wst.common.project.facet.core.xml
    |   |       org.eclipse.wst.jsdt.ui.superType.container
    |   |       org.eclipse.wst.jsdt.ui.superType.name
    |   |       org.eclipse.wst.ws.service.policy.prefs
    |   |       
    |   +---build
    |   |   \---classes
    |   +---src
    |   \---WebContent
    |       |   index.jsp
    |       |   
    |       +---css
    |       |       bootstrap.min.css
    |       |       bootstrap.min.css.map
    |       |       ionicons.css
    |       |       ionicons.min.css
    |       |       main.css
    |       |       
    |       +---fonts
    |       |       glyphicons-halflings-regular.eot
    |       |       glyphicons-halflings-regular.svg
    |       |       glyphicons-halflings-regular.ttf
    |       |       glyphicons-halflings-regular.woff
    |       |       glyphicons-halflings-regular.woff2
    |       |       ionicons.eot
    |       |       ionicons.svg
    |       |       ionicons.ttf
    |       |       ionicons.woff
    |       |       
    |       +---js
    |       |       angular-resource.min.js
    |       |       angular-resource.min.js.map
    |       |       angular.min.js
    |       |       angular.min.js.map
    |       |       appevents.js
    |       |       bootstrap.min.js
    |       |       controller.js
    |       |       jquery-1.9.1.min.js
    |       |       jquery-ui.min.js
    |       |       npm.js
    |       |       services.js
    |       |       
    |       +---META-INF
    |       |       MANIFEST.MF
    |       |       
    |       \---WEB-INF
    |           |   web.xml
    |           |   
    |           \---lib
    |                   javax.servlet.jar
    |                   
    +---RemoteSystemsTempFiles
    |       .project
    |       
    \---Servers
        |   .project
        |   
        +---.settings
        |       org.eclipse.wst.server.core.prefs
        |       
        \---Tomcat v7.0 Server at localhost-config
                catalina.policy
                catalina.properties
                context.xml
                server.xml
                tomcat-users.xml
                web.xml
G. Java Core Web API dependend Libraries

    1. antlr-2.7.7.jar
    2. aopalliance-1.0-sources.jar
    3. commons-logging-1.1.3.jar
    4. dom4j-1.6.jar
    5. gson-2.2.2.jar
    6. hibernate-commons-annotations-4.0.4.Final.jar
    7. hibernate-core-4.3.5.Final.jar
    8. hibernate-entitymanager-4.3.5.Final.jar
    9. hibernate-jpa-2.1-api-1.0.0.Final.jar
    10. jackson-core-asl-1.9.10.jar
    11. jackson-mapper-asl-1.9.10.jar
    12. jandex-1.1.0.Final.jar
    13. javassist-3.18.1-GA.jar
    14. javax.servlet.jar
    15. jboss-logging-3.1.3.GA.jar
    16. jboss-logging-annotations-1.2.0.beta1.jar
    17. jboss-transaction-api_1.2_spec-1.0.0.Final.jar
    18. jstl-1.2.jar
    19. log4j-1.2.17.jar
    20. mysql-connector-java-5.1.6-bin.jar
    21. spring-aop-4.0.5.RELEASE.jar
    22. spring-beans-4.0.5.RELEASE.jar
    23. spring-context-4.0.5.RELEASE.jar
    24. spring-core-4.0.5.RELEASE.jar
    25. spring-expression-4.0.5.RELEASE.jar
    26. spring-jdbc-4.0.5.RELEASE.jar
    27. spring-orm-4.0.5.RELEASE.jar
    28. spring-tx-4.0.5.RELEASE.jar
    29. spring-web-4.0.5.RELEASE.jar
    30. spring-webmvc-4.0.5.RELEASE.jar
    31. xml-apis-1.0.b2.jar
H. Database Name.

    company_db
I. Database Connectivity.

    UserID: root
    Password: *****
    JDBC URL: jdbc:mysql://localhost:3306/company_db
J. Deployment class and web files.

    \---company
    |   |       |       +---controller
    |   |       |       |       RestController.class
    |   |       |       |       
    |   |       |       +---dao
    |   |       |       |       DataDao.class
    |   |       |       |       DataDaoImpl.class
    |   |       |       |       
    |   |       |       +---model
    |   |       |       |       Company.class
    |   |       |       |       Owner.class
    |   |       |       |       Status.class
    |   |       |       |       
    |   |       |       \---services
    |   |       |               DataServices.class
    |   |       |               DataServicesImpl.class
    |   |       |               
    |   |       \---WEB-INF
    |   |           \---classes
    |   |                   index.jsp
also all the dependend liabrary as above in G.

K. Database tables.

1. Company
2. comp_owner
L. Database Creation Schema Script.

        /*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;  
        /*!40101 SET NAMES utf8 */;  
        /*!40014 SET FOREIGN_KEY_CHECKS=0 */;  

        -- Dumping database structure for employee_db  
        CREATE DATABASE IF NOT EXISTS `company_db` /*!40100 DEFAULT CHARACTER SET latin1 */;  
        USE `company_db`;  


        -- Dumping structure for table company_db.company  
        CREATE TABLE IF NOT EXISTS `company` (  
          `comp_id` bigint(20) NOT NULL AUTO_INCREMENT,  
          `comp_name` varchar(45) NOT NULL,  
          `comp_address` varchar(500) NOT NULL, 
           `city` varchar(45) NOT NULL,  
           `country` varchar(45) NOT NULL,  
          `email` varchar(45) DEFAULT NULL,  
          `phone` varchar(45) DEFAULT NULL,  
          PRIMARY KEY (`comp_id`)  
        ) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=latin1;  

        -- Dumping data for table company_db.company: ~1 rows (approximately)  
        /*!40000 ALTER TABLE `company` DISABLE KEYS */;  
        INSERT INTO `company` (`comp_id`, `comp_name`, `comp_address`,`city`,`country`, `email`, `phone`) VALUES  
         (2, 'ViaBill', 'Søndergade 2', 'Aarhus C', 'Denmark', 'hl@viabill.com', '90908989899');  
        /*!40000 ALTER TABLE `company` ENABLE KEYS */;  
        /*!40014 SET FOREIGN_KEY_CHECKS=1 */;  
        /*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */; 

        select * from company; 
        DROP TABLE company_owner;
        -- Dumping structure for table comp_db  
        CREATE TABLE IF NOT EXISTS `comp_owner` (  
          `owner_id` bigint(20) NOT NULL AUTO_INCREMENT,  
          `owner_Name` varchar(45) NOT NULL,  
          `owner_Address` varchar(500) NOT NULL, 
          `owner_City` varchar(45) NOT NULL,  
          `owner_Country` varchar(45) NOT NULL,  
          `owner_Email` varchar(45) DEFAULT NULL,  
          `owner_Phone` varchar(45) DEFAULT NULL,  
          `comp_id` varchar(45)  NOT NULL,
          PRIMARY KEY (`owner_id`)  
        ) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=latin1;  

        -- Dumping data for table company_db.company: ~1 rows (approximately)  
        /*!40000 ALTER TABLE `comp_owner` DISABLE KEYS */;  
        INSERT INTO `comp_owner` (`owner_id`, `owner_Name`, `owner_Address`,`owner_City`,`owner_Country`, `owner_Email`, `owner_Phone`,`comp_id`) VALUES  
         (1, 'Muhammad Asif', 'Teknokrate 3 , Jln Persarian', 'CyberJaya', 'Selangor', 'info@viabill.com', '90908989899',2);  
        /*!40000 ALTER TABLE `comp_owner` ENABLE KEYS */;  
        /*!40014 SET FOREIGN_KEY_CHECKS=1 */;  
        /*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */; 

        select * from comp_owner; 
M. Tables Structure.

1. Company
# Field,                    Type,           Null, Key, Default, Extra
    comp_id,                bigint(20),  NO,     PRI,    , auto_increment
    comp_name,              varchar(45), NO, , , 
    comp_address,               varchar(500), NO, , , 
    city,                   varchar(45), NO, , , 
    country,                varchar(45), NO, , , 
    email,                  varchar(45), YES, , , 
    phone,                  varchar(45), YES, , , 


2.comp_owner
  # Field,              Type,           Null, Key, Default, Extra
    owner_id            bigint(20)  NO  PRI     auto_increment
    owner_Name          varchar(45) NO          
    owner_Address           varchar(500)    NO          
    owner_City          varchar(45) NO          
    owner_Country           varchar(45) NO          
    owner_Email         varchar(45) YES         
    owner_Phone         varchar(45) YES         
    comp_id             varchar(45) YES         
N. Mapped Endpoint Java Functions and Parameters.

    Mapped "{[/company/owner],methods=[GET],com.company.controller.RestController.getOwner()
    Mapped "{[/company],methods=[POST]com.company.controller.RestController.addCompany(com.company.model.Company)
    Mapped "{[/company/owner/{ownerid}],methods=[DELETE],com.company.model.Status com.company.controller.RestController.deleteOwner(long)
    Mapped "{[/company/owner/{compid}],methods=[GET],com.company.controller.RestController.getOwner2(long)
    Mapped "{[/company/owner/],methods=[POST],com.company.controller.RestController.addOwner(com.company.model.Owner)
    Mapped "{[/company/{compid}],methods=[DELETE],com.company.controller.RestController.deleteCompany(long)
    Mapped "{[/company/owner/update/{ownerId}],methods=[PUT],com.company.controller.RestController.updateMyCompany(com.company.model.Owner,long)
    Mapped "{[/company/update/{compid}],methods=[PUT],com.company.controller.RestController.updateMyCompany(com.company.model.Company,long)
    Mapped "{[/company],methods=[GET]com.company.controller.RestController.getCompany()
    Mapped "{[/company/{compid}],methods=[GET],com.company.model.Company com.company.controller.RestController.getCompany(long)
    Mapped "{[/company/owner/del/{compid}],methods=[DELETE],com.company.controller.RestController.deleteOwnerById(long)
O. JSON Output Test Results with SOAP UI

All companies

Request - http://localhost:8080/CompRESTful/company/ 

Output  - [{"compName":"ASIF","compAddress":"asif_inet@hotmail.com","cityName":"Kuala Lumpur","countryName":"Malaysia","email":"asif_inet@hotmail.com","phone":"0176205744","compId":26}]
Selected Company

Request - http://localhost:8080/CompRESTful/company/48
Output  -{"compName":"faizan","compAddress":"bukit","cityName":"kl","countryName":"my","email":"asif_inet@yahoo.com","phone":"1234567","compId":48}
All owners

Request -http://localhost:8080/CompRESTful/company/owner/
Output  -[{"ownerId":157,"ownerName":"Iftikhar Ahmed Bajwa","ownerAddress":"12-3-3 Condo","ownerCityName":"Karachi ","ownerEmail":"asif@hotmailcom","ownerPhone":"934923033","ownerCompid":19,"ownerCountryName":"Pakistan"}]
Selected Owners by Company ID

Request - http://localhost:8080/CompRESTful/company/owner/26 --Company Id
Output  -[{"ownerId":184,"ownerName":"sfdfd","ownerAddress":"dfd","ownerCityName":"dfdf","ownerEmail":"asif_inet@hotmail.com","ownerPhone":"34332343","ownerCompid":26,"ownerCountryName":"dfdf"},{"ownerId":187,"ownerName":"dfdf","ownerAddress":"dfdf","ownerCityName":"dfdf","ownerEmail":"asif_iinet@hotmail.com","ownerPhone":"sdfdf","ownerCompid":26,"ownerCountryName":"dfdf"},{"ownerId":188,"ownerName":"dfdf","ownerAddress":"dfdf","ownerCityName":"dfdf","ownerEmail":"asif_inet@hotmail.com","ownerPhone":"234234234","ownerCompid":26,"ownerCountryName":"dfdf"},{"ownerId":191,"ownerName":"dfdf","ownerAddress":"dfdf","ownerCityName":"dfdf","ownerEmail":"asif_inet@hotmai.com","ownerPhone":"3434","ownerCompid":26,"ownerCountryName":"df"}]
Update the company

Request -   http://localhost:8080/CompRESTful/company/update/48 --Company Id
PUT Method
Input
Output  -   {"compName":"faizan","compAddress":"bukit","cityName":"kl","countryName":"my","email":"kashif@yahoo.com","phone":"1234567","compId":48}

output
{
   "code": 1,
   "message": "Company added Successfully !"
}
DELETE Owner by Id

Request - http://localhost:8080/CompRESTful/company/owner/del/148   --Owner ID
DELETE Method
Output
{
   "code": 1,
   "message": "Owner deleted Successfully !"
}
Update Owner by Owner Id

Request - http://localhost:8080/CompRESTful/company/owner/update/
PUT Method
from :-  {"ownerId":184,"ownerName":"sfdfd","ownerAddress":"dfd","ownerCityName":"dfdf","ownerEmail":"asif_inet@hotmai          l.com","ownerPhone":"34332343","ownerCompid":26,"ownerCountryName":"dfdf"},

to   :- {"ownerId":184,"ownerName":"Muhammad 
    Asif","ownerAddress":"dfd","ownerCityName":"dfdf","ownerEmail":"asif_inet@hotmail.com","ownerPhone":"34332343"
    ,"ownerCompid":26,"ownerCountryName":"dfdf"},

Output
{
"code": 1,
"message": "Owner Updated Successfully !"
}
Note:

     Required liabraries are bundeled into the package in WEB-INF\lib folder in the RESTful_Server WebAPI folder.
!End of the Document

Any query suggestion and improvement w.r.t.o the Readme Document, Please send it to asif_inet@hotmail.com
