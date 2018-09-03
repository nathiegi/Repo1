<!-- TITLE: Wish Grid - Implementation Manual V1.0 -->
<!-- SUBTITLE: A quick summary of Wish Grid Implementation Manual V1.0 -->

# Implementation Manual
### Project Name: WishGrid
### Version: 1.0
### Last Modified date: 08/24/2018


## Purpose
This document aims to show how the WishGrid software was implemented, indicating in broad strokes the technologies used.
## System Description
WishGrid is a software in which users can make suggestions about a company service and can vote in favor of that or another suggestion, so that the company can have comments from its users about its services.

## Glossary, Acronyms and Abbreviations

# Pre-requisites

## Hardware
•	Hard Disk with 6 GB of available space
•	RAM of 2 GB or higher
•	Processor de 2 GHz or higher
•	Internet Connection
 

## Software
•	Microsoft .Net Framework 4.5 o Superior
•	Microsoft .Net Core SDK 2.1.105
•	Microsoft Visual Studio Community 2017 Version 15.6.6
•	Microsoft SQL Server 2017 Developer
•	Node.Js Version 8.11.1



# Implementation - 1.	Windows and IIS

## Microsoft SQL Server 2017 EXPRESS Edition
### Microsoft SQL Installation
Once we have the SQL Server 2017 installer we start:
•	Double Click on the installer setup
 ![Im 1 Setup Installer](/uploads/wish-grid/im-1-setup-installer.png "Im 1 Setup Installer")

•	Open the installation screen, click on "Installation" (a) and Click on "New Sql Server stand-alone installation or add features to an existing installation" (b).
![Im 2 Sql Server Installation Center](/uploads/wish-grid/im-2-sql-server-installation-center.png "Im 2 Sql Server Installation Center")

•	Verify if your system fulfills with the global installation rules.
![Im 3 Global Rules](/uploads/wish-grid/im-3-global-rules.png "Im 3 Global Rules")

•	Select if you want to download Microsoft Updates, click on next.
![Im 4 Microsoft Update](/uploads/wish-grid/im-4-microsoft-update.png "Im 4 Microsoft Update")

•	Rules for the installation, (verify that the Firewall is disabled, otherwise there will be no impact on the installation).
![Im 5 Install Rules](/uploads/wish-grid/im-5-install-rules.png "Im 5 Install Rules")

•	Type of Installation, we select the first "Perform a new installation of SQL Server 2017".
![Im 6 Installation Type](/uploads/wish-grid/im-6-installation-type.png "Im 6 Installation Type")

•	Select the Edition that we are going to use, in this case "Express".
![Im 7 Product Key And Selection Edition Sql Server](/uploads/wish-grid/im-7-product-key-and-selection-edition-sql-server.png "Im 7 Product Key And Selection Edition Sql Server")

•	We accept the Terms of the License.
![Im 8 License Terms](/uploads/wish-grid/im-8-license-terms.png "Im 8 License Terms")

•	Select the characteristics, functions and specifications of the destination folders for the root instance and the shared functions (Select the views in the image).
![Im 9 Feature Selection](/uploads/wish-grid/im-9-feature-selection.png "Im 9 Feature Selection")

•	We specify the name of the Instance (We can leave it Default).
![Im 10 Instance Configuration](/uploads/wish-grid/im-10-instance-configuration.png "Im 10 Instance Configuration")

•	Specify the services of the accounts and their configurations, select the check for the necessary privileges
![Im 11 Server Configuration](/uploads/wish-grid/im-11-server-configuration.png "Im 11 Server Configuration")

•	We configure the Authentication Form, through Windows Authentication or SQL Server Authentication by entering a password, and add a User account.
![Im 12 Database Engine Configuration](/uploads/wish-grid/im-12-database-engine-configuration.png "Im 12 Database Engine Configuration")

•	Download and install the necessary requirements within R Open and Python, click on the "Accept" button.
![Im 13 Consent To Install Microsoft R Open](/uploads/wish-grid/im-13-consent-to-install-microsoft-r-open.png "Im 13 Consent To Install Microsoft R Open")

![Im 14 Consent To Install Python](/uploads/wish-grid/im-14-consent-to-install-python.png "Im 14 Consent To Install Python")

•	The wizard shows everything that will be installed, click on the "Install" button and then it will show us the progress of the Installation (this takes a few minutes).
![Im 15 Ready To Install](/uploads/wish-grid/im-15-ready-to-install.png "Im 15 Ready To Install")

![Im 16 Installation Progress](/uploads/wish-grid/im-16-installation-progress.png "Im 16 Installation Progress")

Once completed it will show a box telling the installation is complete.

### Configuration with in the Database

Enter SQL Server 2017 Express Edition, and execute the following Script:

•	BaseDatosWishGrid.sql (Creation of Database and its Tables).
•	PerfilSendMail.sql (Profile in which the mailings will be executed).                                                
•	ProcedimientosAlmacenados.sql (All procedures for Sending Post).
Since the application is a multi-tenant application, you need to configure the tenants (web pages domains) that the API will be able to consume, to do that you follow steps below:

Once the WishGrid script has been executed, the following steps will be followed:
•	Within SQL Server 2017 Express Edition display the "Databases" folder.

![Im 17 Databases In Sql Server](/uploads/wish-grid/im-17-databases-in-sql-server.png "Im 17 Databases In Sql Server")

•	Inside the folder "Databases", look for the WishGrid Database and display it.

![Im 18 Databases Wishgrid](/uploads/wish-grid/im-18-databases-wishgrid.png "Im 18 Databases Wishgrid")

•	Deploy the WishGrid Database, inside you will find the tables of the database where the information will be stored. Secondary click on the "dbo.Tenant" table and select "Edit Top 200 Rows".
![Im 19 Insert Data In The Table Tenant](/uploads/wish-grid/im-19-insert-data-in-the-table-tenant.png "Im 19 Insert Data In The Table Tenant")

•	The tenant is the WishGrid service, where the information of the people or companies that require it is stored, to start using the application.
The WishGrid team performs the entire procedure to add the Tenant; otherwise, the team can enter the data to add it as follows:
![Im 20 Table Tenant](/uploads/wish-grid/im-20-table-tenant.png "Im 20 Table Tenant")

a)	Address of the person or company that owns the Tenant.
b)	Name of the person or company that will be the owner of the Tenant.
c)	NIT of the person or company that owns the Tenant.
d)	Landline or mobile phone of the person or company that owns Tenant.
e)	State of the Tenant (True so that it is activated, otherwise it can not be used).
f)	Address given by WishGrid (domain for the Tenant).
g)	Moderation of Tenant (if the suggestion needs to be moderated).
h)	Address of the logo of the Person or Company owner of the Tenant (You can save the image inside the folder of the web page deployed, in this case, enter the address of the image, example in the box above).
i)	Address of the main page of the person or company that owns Tenant.

•	Once the Tenant is created, from the Application create a user account from the address that WishGrid provided (URLOrigin field in the "Tenant" table).

![Im 21 Create User In Wishgrid](/uploads/wish-grid/im-21-create-user-in-wishgrid.png "Im 21 Create User In Wishgrid")

Within the Database, in the table "dbo.User" select "Edit Top 200 Rows", and modify the following data:
![Im 22 Table User](/uploads/wish-grid/im-22-table-user.png "Im 22 Table User")

a)	Modify the RoleId field of 4 by 2 (Administrator), we recommend creating a single "Administrator" to control the application and delegate "Moderator" (Explained in the Implementation Manual).
b)	All Users created in the Tenant of the people or companies within WishGrid, are created as "False" for the respective validation of the account (Explained in the Implementation Manual). You can modify from the Database and write "True" in the field "Validation", to skip the step of the Implementation Manual.

Once all the steps mentioned above have been completed, you can enter as a WishGrid administrator to start using the application.

## Deployment of the API
Since the application is multi-tenant, you will have a single API in which the pages are consuming the services of this API, so you must implement the deployment of our API and our pages separately.

### Install Net Core
Download .NET Core 2.0 SDK, double-click on the exe, and start the installation process.
![Im 23 Netcore Setup](/uploads/wish-grid/im-23-netcore-setup.png "Im 23 Netcore Setup")

Once this process ends, it will show the following window.
![Im 24 Netcore Setup Finished](/uploads/wish-grid/im-24-netcore-setup-finished.png "Im 24 Netcore Setup Finished")

### Install Net Core Windows Hosting
Since the application is made in .NetCore, it runs on a kestrel server and can’t be deployed in an IIS server, but you can use IIS to proxy it to our application, to do so you must install net core windows hosting.
First double-click the .net core Windows server hosting and start the installation process, once finished, it will show next window
![Im 25 Netcore Windows Hosting](/uploads/wish-grid/im-25-netcore-windows-hosting.png "Im 25 Netcore Windows Hosting")

We create a folder in the local machine. Within that folder, we will place all our files for implementation. Then, right click on the name of the Project and click Publish option 
![Im 26 Project Publish 1](/uploads/wish-grid/im-26-project-publish-1.png "Im 26 Project Publish 1")

In the next window you will create the production files and place them in the folder that we created
![Im 27 Project Publish 2](/uploads/wish-grid/im-27-project-publish-2.png "Im 27 Project Publish 2")

The production files in the folder will be the following:
![Im 28 Project Publish 3](/uploads/wish-grid/im-28-project-publish-3.png "Im 28 Project Publish 3")

### Datasource
In order to make the API communicate with the database we must indicate to the database that we want to locate, for that you must configure the appsettings.json located in the folder where we have published the project:

![Im 29 Datasource](/uploads/wish-grid/im-29-datasource.png "Im 29 Datasource")
Now we write the database that we want to enter modifying the data source in the following way: 
Server=SERVERNAMEORUSER;Database=WISHGRIDDATABASE;Trusted_Connection=True;MultipleActiveResultSets=true;Integrated Security=true;
Where the “server” is the windows user and the database is the database of our application

### IIS setup and deployment of API
If you do not have IIS installed on the machine, you must install it by opening Control Panel and then Programs and Features: 

![Im 30 Iis Setup 1](/uploads/wish-grid/im-30-iis-setup-1.png "Im 30 Iis Setup 1")

After pressing OK it should start the IIS.
![Im 31 Iis Setup 2](/uploads/wish-grid/im-31-iis-setup-2.png "Im 31 Iis Setup 2")

Once the IIS installation finishes, open the run window (Windows key + R) and type inetmgr to open the IIS Manager:
![Im 32 Iis Exec](/uploads/wish-grid/im-32-iis-exec.png "Im 32 Iis Exec")

Now we can create a new application:
![Im 33 Publish To Iis Server 1](/uploads/wish-grid/im-33-publish-to-iis-server-1.png "Im 33 Publish To Iis Server 1")

We enter the data in the following window:
![Im 34 Publish To Iis Server 2](/uploads/wish-grid/im-34-publish-to-iis-server-2.png "Im 34 Publish To Iis Server 2")

After this step, we will have our site in the "Sites" folder in the IIS administrator. We choose the port (a free port) that we want our application to occupy and accept.
![Im 35 Publish To Iis Server 3](/uploads/wish-grid/im-35-publish-to-iis-server-3.png "Im 35 Publish To Iis Server 3")

The IIS by Default blocks the http requests Edit and Delete, as well as the requests of url that have symbols either ^, &, *,:, so we manually have to add the permissions for these types of requests configuring the web.config located in our folder to which we have published our application:

![Im 36 Web Config Permisions 1](/uploads/wish-grid/im-36-web-config-permisions-1.png "Im 36 Web Config Permisions 1")

Then we add the following lines in our web.config:

![Im 37 Web Config Permisions 2](/uploads/wish-grid/im-37-web-config-permisions-2.png "Im 37 Web Config Permisions 2")

1 This line indicates the blocks of symbols in the request of the url, if we want to block some type of symbol in the request we simply add the symbols that we want to block separated by commas.
2 This line indicates the blocks of http request in our application, if we want to block some type of http request, we simply add the http request that we want to block separated by commas. 

## 	Deployment of the webpage(SPA)
The implementation of the web page is easier, just like our API we will start doing the deployment of our website, using the Node.Js command prompt.
### 	Deployment of the website
First we open the Node.js command prompt:

![Im 38 Node Exec](/uploads/wish-grid/im-38-node-exec.png "Im 38 Node Exec")

Once we open our command prompt, what should be done is to locate where the project is in which we have developed the application using the command: 
cd “ProjectRoute”

![Im 39 Node Project Location](/uploads/wish-grid/im-39-node-project-location.png "Im 39 Node Project Location")

Then we execute the command:
 ng build –prod
this command will give us our project published, these files will be created in a folder called dist located in the same folder with the following files:


![Im 40 Webpage Publish](/uploads/wish-grid/im-40-webpage-publish.png "Im 40 Webpage Publish")

Now we can create a new application:

![Im 41 Publish To Iis Server 1](/uploads/wish-grid/im-41-publish-to-iis-server-1.png "Im 41 Publish To Iis Server 1")

We enter the data in the following window:

![Im 42 Publish To Iis Server 2](/uploads/wish-grid/im-42-publish-to-iis-server-2.png "Im 42 Publish To Iis Server 2")

After this step, you will have the site in the "Sites" folder in the IIS administrator. We choose the port (a free port) that we want our application to occupy and accept.

![Im 43 Publish To Iis Server 3](/uploads/wish-grid/im-43-publish-to-iis-server-3.png "Im 43 Publish To Iis Server 3")

### Consuming services of the API
The API and the website are separated into 2 different projects, so you have to indicate to the website where the API is located in order to consume the services of this one. There are 2 ways to be able to locate this domain, through the project before compressing in production, such as after deployment in production mode.
### Through the Project before compressing in production
In our project we are located on the route. \ WGViewA5 \ src \
In this folder we will find 2 files: environment.ts and environment.prod.ts, in development mode the environment.ts is used and in production the environment.prod.ts, since we want to deploy our project in production mode we open the envionrment .prod.ts.
Here we see there are variables, among these is the domain of the API. Here you put the domain of the API so you can consume the services of this in the variable apiURL:

![Im 44 Environment Prod Ts](/uploads/wish-grid/im-44-environment-prod-ts.png "Im 44 Environment Prod Ts")

Once this is finished, we save the changes and can continue with the steps of deployment of the web page detailed above.
### Through the Project deployed in production
Once we perform the command ng build -prod the node.js is responsible for compressing our project in production mode, minifying it, however it does not mean that we cannot find our environment, we must first locate our deployed project and open the main file:

![Im 45 Webpage Folder](/uploads/wish-grid/im-45-webpage-folder.png "Im 45 Webpage Folder")

This file contains all our typescripts, which we have developed but minified so that the application is fast, however the variables keep their names so we can search the variable apiURL and change it so that it consumes the correct service:

![Im 46 Main Js](/uploads/wish-grid/im-46-main-js.png "Im 46 Main Js")

Once finished it is recommend to restart the IIS.
## Posible problems
Windows can cause a problem that does not find the database, this is because it tries to enter the database with a non-existent Login, to fix this problem we should do the following steps:
1.- identify the non-existent login: in order to identify the non-existent login we must first try to make some kind of request in our application, once we try this, and fail, Windows will register this event, so what we have to do is watch this event using the Windows viewer event:

![Im 47 Event Viewer](/uploads/wish-grid/im-47-event-viewer.png "Im 47 Event Viewer")

Once we find our request that we made to he SQL server, which is located in Windows logs applications, we can see the user to whom we want to connect and copy it, now we have to create the same user in our SQL server with the same name and permissions
In the Database Manager, in this case SQL Server Management Studio, in the Object Explorer, in search for the "Security" folder, when displaying in the "Logins" folder, secondary click

![Im 48 New Login 1](/uploads/wish-grid/im-48-new-login-1.png "Im 48 New Login 1")


![Im 49 New Login 2](/uploads/wish-grid/im-49-new-login-2.png "Im 49 New Login 2")

Where it says login name copy the user that tried to enter the application and where it says default database chose the database of the application. Then verify that the other checks are equal:

![Im 50 New Login 3](/uploads/wish-grid/im-50-new-login-3.png "Im 50 New Login 3")


![Im 51 New Login 4](/uploads/wish-grid/im-51-new-login-4.png "Im 51 New Login 4")


![Im 52 New Login 5](/uploads/wish-grid/im-52-new-login-5.png "Im 52 New Login 5")

Once you finish creating the Login click Ok.
If the steps were followed correctly you should be able to access the application without problems.


# CentOS and Apache using Docker

For the deployment of the Project in CentOs we are going to use Docker, which is a tool designed to make easier to create, deploy, and run applications by using containers. Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and ship it all out as one package. By doing so, thanks to the container, the developer can rest assured that the application will run on any other Linux machine regardless of any customized settings that machine might have that could differ from the machine used for writing and testing the code.
## Docker
In a way, Docker is a bit like a virtual machine. But unlike a virtual machine, rather than creating a whole virtual operating system, Docker allows applications to use the same Linux kernel as the system that they're running on and only requires applications be shipped with things not already running on the host computer. This gives a significant performance boost and reduces the size of the application.

### Docker in our application
In the project, since the application is a multi-tenant application we are going to use 2 docker containers, in 1 container we will have our DB + API in an apache server and in the other we will have just an apache server with the websites to consume services from the first container, since the project will have the containers ready, we will explain how to setup docker and how to setup and start the containers which has the projects, also where to make the small modification to change the domains.
### Docker Installation using the repository
1.	Install required packages. yum-utils provides the yum-config-manager utility, and device-mapper-persistent-data and lvm2 are required by the devicemapper storage driver.

![Im 57 Code 1](/uploads/wish-grid/im-57-code-1.png "Im 57 Code 1")

2.	Use the following command to set up the stable repository. You always need the stable repository, even if you want to install builds from the edge or test repositories as well.

![Im 58 Code 2](/uploads/wish-grid/im-58-code-2.png "Im 58 Code 2")

3.	Optional: Enable the edge and test repositories. These repositories are included in the docker.repo file above but are disabled by default. You can enable them alongside the stable repository.

![Im 59 Code 3](/uploads/wish-grid/im-59-code-3.png "Im 59 Code 3")

You can disable the edge or test repository by running the yum-config-manager command with the --disableflag. To re-enable it, use the --enable flag. The following command disables the edge repository.

![Im 60 Code 4](/uploads/wish-grid/im-60-code-4.png "Im 60 Code 4")

Note: Starting with Docker 17.06, stable releases are also pushed to the edge and test repositories.

INSTALL DOCKER CE
1.	Install the latest version of Docker CE, or go to the next step to install a specific version:

![Im 61 Code 5](/uploads/wish-grid/im-61-code-5.png "Im 61 Code 5")

If prompted to accept the GPG key, verify that the fingerprint matches060A 61C5 1B55 8A7F 742B 77AA C52F EB6B 621E 9F35, and if so, accept it.
If you have multiple Docker repositories enabled, installing or updating without specifying a version in the yum install or yum update command always installs the highest possible version, which may not be appropriate for your stability needs.
Docker is installed but not started. The docker group is created, but no users are added to the group.
2.	To install a specific version of Docker CE, list the available versions in the repo, then select and install:
a. List and sort the versions available in your repo. This example sorts results by version number, highest to lowest, and is truncated:

![Im 62 Code 6](/uploads/wish-grid/im-62-code-6.png "Im 62 Code 6")

The list returned depends on which repositories are enabled, and is specific to your version of CentOS (indicated by the .el7 suffix in this example).
b. Install a specific version by its fully qualified package name, which is the package name (docker-ce) plus the version string (2nd column) up to the first hyphen, separated by a hyphen (-), for example,docker-ce-18.03.0.ce.

![Im 63 Code 7](/uploads/wish-grid/im-63-code-7.png "Im 63 Code 7")

Docker is installed but not started. The docker group is created, but no users are added to the group.
3.	Start Docker.
![Im 64 Code 8](/uploads/wish-grid/im-64-code-8.png "Im 64 Code 8")

4.	Verify that docker is installed correctly by running the hello-world image.

![Im 65 Code 9](/uploads/wish-grid/im-65-code-9.png "Im 65 Code 9")

This command downloads a test image and runs it in a container. When the container runs, it prints an informational message and exits.
Docker CE is installed and running. You need to use sudo to run Docker commands.

### Mount the docker images containers
After we successfully installed docker now we must mount our images containers to our docker, these containers will be provided by the development Team:
wishgridapi.tar
wishgridspa.tar
After we transfer our containers to our CentOS where we installed docker we can mount our images, lets say we put our containers in the /root directory, when we open the command prompt and execute the command “ls” it will show us that our containers are in there.

![Im 53 Centos Ls Command](/uploads/wish-grid/im-53-centos-ls-command.png "Im 53 Centos Ls Command")

Now we execute the command “docker import nameofcontainer.tar tagnameforimage”

![Im 54 Docker Import](/uploads/wish-grid/im-54-docker-import.png "Im 54 Docker Import")

where nameofcontainer.tar is the container wishgridapi.tar or wishgridspa.tar and tagnameforimage is a name we can give to the docker image, it could be wishgridapiv1.0. after we execute the command we wait until it finishes to mount the image and to check if the image was successfully mounted we execute the command “docker images”.
After we’ve done the import we exec the command “docker images” to see our images:

![Im 55 Docker Images](/uploads/wish-grid/im-55-docker-images.png "Im 55 Docker Images")

Now that we have the images of our API and webpage we can start the image executing the command:
“docker run -ti -p domain:portthatwewanttouse:80 -p domain:portthatwewanttouse:22 –privileged nameofimage /sbin/init”
What we do here is start our container and proxy our apache port to an unused port of our CentOS.
Where domain is the domain that we are using,porthatwewant to use is an unused port that will proxy our apache server of our container, 80 is the port where our container runs apache, 22 is the port of the ssh so we can access to the ssh, nameofimage is the name of our image and –privileged is to have all access to the container. Repeat the process for the API and SPA so we can start both images.
If done correctly after we execute the command “docker ps” we will see our containers running as follow:

![Im 56 Docker Ps](/uploads/wish-grid/im-56-docker-ps.png "Im 56 Docker Ps")

now we want to start the apache server on each container to do so in a new terminal window we exec the command “docker exec -ti containercode bash” where containercode is the container ID that was generated when we started the container. This code will take us inside the container, the team will perform the changes so that the only thing that is needed is to start the apache server, to do so inside the container we exec the command: systemctl start httpd, this will start the apache server for the container. Repeat the process for the API/SPA.
If done successfully we should be able to start our application with the port that we assigned in our PC.

### Configuring domains.

Since we have an API and a SPA separately, we must indicate how are these 2 project going to communicate, to do so we must do changes in the, database, API and SPA.

### Changes in the SQLServer.
In the database we must indicate the domain of the webpage we are trying to access, to do so we go:
•	Inside the folder "Databases", we look for the WishGrid Database and we display it.

![Im 18 Databases Wishgrid](/uploads/wish-grid/im-18-databases-wishgrid.png "Im 18 Databases Wishgrid")

Case we do not have the database we follow the steps detailed in 1.1.1.

•	We deploy the "WishGrid" Database, inside we will find the tables of the database where the information will be stored. Secondary click on the "dbo.Tenant" table and select "Edit Top 200 Rows".


![Im 19 Insert Data In The Table Tenant](/uploads/wish-grid/im-19-insert-data-in-the-table-tenant.png "Im 19 Insert Data In The Table Tenant")

•	The tenant is the WishGrid service, where the information of the people or companies that require it is stored, to start using the application.
The WishGrid team performs the entire procedure to add the Tenant; otherwise, the team can enter the data to add it as follows:


![Im 20 Table Tenant](/uploads/wish-grid/im-20-table-tenant.png "Im 20 Table Tenant")

a)	Address of the person or company that owns the Tenant.
b)	Name of the person or company that will be the owner of the Tenant.
c)	NIT of the person or company that owns the Tenant.
d)	Landline or mobile phone of the person or company that owns Tenant.
e)	State of the Tenant (True so that it is activated, otherwise it can not be used).
f)	Address given by WishGrid (domain for the Tenant).
g)	Moderation of Tenant (if the suggestion needs to be moderated).	
h)	Address of the logo of the Person or Company owner of the Tenant (You can save the image inside the folder of te web page deployed, in this case, enter the address of the image, example in the box above).
i)	Address of the main page of the person or company that owns Tenant.

•	 Once the Tenant is created, from the Application create a user account from the address that WishGrid provided (URLOrigin field in the "Tenant" table), this step can be done after we configure the Database, API and web page.

![Im 21 Create User In Wishgrid](/uploads/wish-grid/im-21-create-user-in-wishgrid.png "Im 21 Create User In Wishgrid")

Within the Database, in the table "dbo.User" we select "Edit Top 200 Rows", and modify the following data:

![Im 22 Table User](/uploads/wish-grid/im-22-table-user.png "Im 22 Table User")

c)	Modify the RolId field of 4 by 2 (Administrator), we recommend creating a single "Administrator" to control the application and delegate "Moderator" (Explained in the Implementation Manual).
d)	All Users created in the Tenant of the people or companies within WishGrid, are created as "False" for the respective validation of the account (Explained in the Implementation Manual). You can modify from the Database and write "True" in the field "Validation", to skip the step of the Implementation Manual.

Once all the steps mentioned above have been completed, you can enter as a WishGrid administrator to start using the application.

### Changes in the API.

In order to make our API communicate with our database we must indicate to the database that we want to locate, for that you must configure the appsettings.json located in the folder where we have published the project /var/wishgrid:

![Im 29 Datasource](/uploads/wish-grid/im-29-datasource.png "Im 29 Datasource")

Now we write the database that we want to enter modifying the data source in the following way: 
"DefaultConnection": "Data Source=IPOFMSSQLSERVER;Database=wishgrid;User ID=sa;Password=123abc.-"

Where the datasource is the ip where our SQL server is running in this case the same ip of the docker that contains the API, User ID the system admin user, and password the password of SA.

### Changes in the webpage (WishgridSPA).
Repeat the process of 1.3.2. Consuming services from the API. Most specifically 1.3.2.2.
The webpage published is located in /var/www/wishgrid2.com/htdocs inside the docker container.

### Posible problems
For some reason the license of SQL server is lost when you start the docker container of our API, so we must check if the sql is running, to check it we exec the command: 
Systemctl status mssql-server
This will tell us if the sqlserver is running if we have an error that sqlserver couldn’t start we exec the command:
Sudo /opt/mssql/bin/mssql-conf setup
Then we get asked which license we want, we choose the Express option, give a password for our sa and exec the command:
Systemctl start mssql-server
If the service couldn’t start or the conf setup couldn’t start, it’s because it tried too many times to start and we must wait some time before trying again.


# Points of Contacts
**MegadeV Team: (wishgrid@googlegroups.com)**
Miguel Castedo (mcastedo@info-arch.com)
Nathalie Guzmán I. (nguzman@info-arch.com)
Oscar Laura (olaura@info-arch.com)
Oscar Soliz (osoliz@info-arch.com)
Richard Arteaga (rarteaga@info-arch.com)
Wilber Padilla (wpadilla@info-arch.com)
