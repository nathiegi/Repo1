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







# Troubleshooting
### Scenario 1
Scenario and how to fix  it
Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text 
### Scenario 2
Scenario and how to fix  it
Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text 

# Points of Contacts
Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text 
