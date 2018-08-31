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

# Troubleshooting
### Scenario 1
Scenario and how to fix  it
Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text 
### Scenario 2
Scenario and how to fix  it
Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text 

# Points of Contacts
Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text Sample Text 
