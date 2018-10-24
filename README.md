Documentation for Bulk-api-v2 setup instructions in Windows
-

### Prerequisites

- JDK 
- Apache Tomcat
- postgreSQL
- pgAdmin4
- Spring Tool Suite 3.9.6
- Maven 3.3.X

Download JDK for Windows
-

-  To download JDK in windows, Open this link https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html in Chrome and Enter
- Here Accept the license and click on Windows x64 jdk link, it starts downloading.

 
-  Go to downloads and double click on jdk-8u161-windows-x64.exe, Pop-up window will open which ask for Do you want to allow this app to make changes to your PC?, Click Yes, just give next next, it will install and finally give close after installation.
- Now go to C Drive, go to Program Files then java, here we can find both jdk and jre installed files.

	Verifying jdk installation
	-
	-  In Command Prompt type java -version
```
	C:\Users\it-su>java -version
	java version "1.8.0_161"
	Java(TM) SE Runtime Environment (build 1.8.0_161-b12)
	Java HotSpot(TM) 64-Bit Server VM (build 25.161-b12, mixed mode)
```
Setting JAVA_HOME and JRE_HOME
-

-  Right click on This PC which is in Desktop, click Properties, the pop-window opens, here click on Advances system settings, Go to Advances, click Environment Variables.
In System variables, double click on path, Here we can Edit
Click on new and paste bin path of jdk and again click on new and paste bin path of jre 
```
C:\Program Files\Java\jdk1.8.0_161\bin
C:\Program Files\Java\jre1.8.0_161\bin
```
In User variables, click on New and set JAVA_HOME press OK , again New for JRE_HOME and click OK
```
Variable Name	JAVA_HOME
Variable Value   C:\Program Files\Java\jdk1.8.0_161

Variable Name	JRE_HOME
Variable Value   C:\Program Files\Java\jre1.8.0_161
```

Download and Install Apache Tomact 
-
Open the Web browser say Chrome to download Apache Tomcat 9.0.8 with link given below	
https://tomcat.apache.org/download-90.cgi
- Download the 64-bit Windows zip (pgp, sha512) file of Apache tomcat.
- Go To Downloads, unzip apache-tomcat-8.0.53-windows-x64.zipin Apache Software Foundation in Program Files. 
- Open Command Prompt by typing cmd in Search option in Windows button. Type below commands each and enter.
```
cd C:\Program Files\Apache Software Foundation\apache-tomcat-8.0.53\bin\catalina run
```
-  Now Open Chrome and type http://localhost:8080/ to open Tomcat home Page, this verifies Tomcat is running successfully in our machine.
--------------------------------------------------------------------------------------------------------------------------------------

Download And Install PostgresSQL and pgAdmin4 for Windows
-

-  To Download go to the link https://www.enterprisedb.com/downloads/postgres-postgresql-downloads give Postgre version and Operating System and click on Downloads. 
- Go to Downloads double click on PostgreSQL exe file, it asks Dou you want to allow this app to make changes to your pc? Give Yes, keep on clicking on Next, set  password as postgres again keep giving Next
- A new pop-up window will open, here select postgresql and click Next, so now installation process is complete
How to Open pgAdmin 4  
-  Go to C- Drive, In Programming File, Open PostgreSQL, click on 10, then click on pgAdmin 4, click on bin, here double click on pgAdmin.exe

--------------------------------------------------------------------------------------------------------------------------------------

To Import Database into pgAdmin4
-

-  Open pgAdmin4
To Create Database
- Click on Server then click on PostgreSQL 10 then right click on Database, here click Create then click on Database  
- A pop-up window will open, give Database name as bulkdataclient and Save.
Now to Import Database
-  Open Command Prompt in Administrator mode and go set parh to bin folder of postgre and type below command then enter.
psql -h localhost -d bulkdataclient -U postgres -f " C:\bulkdata.sql"
Below is the output from command prompt:

```
	C:\Program Files\PostgreSQL\10\bin>psql -h localhost -d bulkdataclient -U postgres -f "C:\bulkdata.sql"
	Password for user postgres: XYZ
	
	SET
	
	CREATE
	...
```

Spring Tool Suite Installation
-

Download and Run Spring Tool Suite
Download STS for Linux or Windows from below link
- https://spring.io/tools3/sts/all (Download From this)
- Go to Downloads, then Unzip, spring-tool-suite-3.9.6.RELEASE-e4.9.0-win32-x86_64.zip, and now STS is ready to use
To Open STS
- Go to Downloads , then open sts-3.9.6.RELEASE , then double click on STS.exe

Built Application 
-
Run Maven build to build application war file. 
```
$ mvn clean install 
```
This will generate a war file under target/{application-name}.war. Copy this to your tomcat webapp directory for deployment.

To Add Server in STS
--

- In Quick Access Type Server and enter
	- Right Click on blank white space, Then New , and Server
	- If we don't find Tomcat Server then follow below steps
	  - Go to Help in menu bar click on Eclipse Market Place
	  - Here type Eclipse JST Server Adapter and install, now it asks for Restart click on it
	- Apache, here Tomcat v8.0 Server then Next
	- In next window, browse the Tomcat path and give finish.

To Import Bulk-api-v2 project from existing location in to sts ide
--
-  In STS, Click on File in menu bar, click on import then in Maven Projects, click on Existing Maven Projects. Click on Next. Pop-up 	window appears, Click on browse and search the path of bulk-api-v2 project and finally finish

	To Run Bulk-api-v2 Project
	--
	
	- Right Click on bulk-api-v2 then Click Run AS and Run on Server, a pop-up window opens
	- Select Pivotal or Apache Tomcat Server then Finish
	- Output is shown in console output with local url http://localhost:8080/bulk-data-api/ 
	
	Client Registration
	--

	-  After running above project, we have to do client registration with local url http://localhost:9090/bulk-data-api/view/clients.html  with following details
	- Registring New Client 
	```
		UserName 	abc123
		Email    	abc123@gmail.com
		Full Name 	abcdefg
		Password 	abcxyz
	```
	-  Then give OK, inside this another web page opens, click on Register Backend Client with public der file, check for both system and user.
	```
	Backend Client Registration
		Client App Name       bulk data api
		Organization	      Xyram
		Client Issuer URL     http://localhost:8080/bulk-data-api/
		Public Key            Upload Public Key
		Scope		      Check both system and user	
	```

	- After registration it generate ClientID and token URL as follows
	```
	Client ID :     bulk data apiVxAHtrAqt1
	Token URL :  http://localhost:9090/bulk-data-api/token
	```
