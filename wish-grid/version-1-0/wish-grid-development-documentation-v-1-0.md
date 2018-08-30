<!-- TITLE: Wish Grid - Development Documentation V1.0 -->
<!-- SUBTITLE: A quick summary of Wish Grid Development Documentation V1.0 -->

# Development Manual for WishGrid

**Development Manual**
Project Name: WishGrid
Version: 1.0
Last Modified date: 08/24/2018

**Purpose**
This document aims to show how the WishGrid software was developed, indicating in broad strokes the technologies implemented.

**System Description**
WishGrid is a software in which users can make suggestions about a company service and can vote in favor of that or another suggestion, so that the company can have comments from its users about its services.

**Glossary, Acronyms and Abbreviations**

### Pre-requisites
a)	Hardware
•	Hard Disk with 6 GB of available space
•	RAM of 2 GB or higher
•	Processor de 2 GHz or higher
•	Internet Connection

b)	Software
•	Microsoft .Net Framework 4.5 o Superior
•	Microsoft .Net Core SDK 2.1.105
•	Microsoft Visual Studio Community 2017 Version 15.6.6
•	Microsoft SQL Server 2017 Developer
•	Node.Js Version 8.11.1

## Technologies used for the WishGrid development


### 1)	Project Creation
Install all the software prerequisites, start Visual Studio and follow the following steps:
1.1.	Click File -> New -> Project.
1.2.	Select Web -> .NET Core -> ASP.NET Core Web Application.
1.3.	Indicate the name of the API project and the name of the Solution.
1.4.	Select API and click OK.
1.5.	Create the models and the DataContext.
1.6.	Click Tools -> NuGet Package Manager -> Package Manager Console and enter the following commands:
1.6.1.	 "Install-Package Microsoft.EntityFrameworkCore.SqlServer"
1.6.2.	 "Install-Package Microsoft.EntityFrameworkCore.Tools"
1.6.3.	 "Add-Migration firstMigration"
1.6.4.	 "Update-Database"
1.7.	 Enter the Node.Js
1.7.1.	 Write the command "npm install -g @angular/cli".
1.7.2.	 Locate in the folder where the SPA project will be created.
1.7.3.	 Write the command "ng new ProjectName".
1.8.	In Visual Studio, right click on the solution, scroll to the option Add and select existing Project... and then select the SPA project.
1.9.	To compile the projects, follow these steps:
1.9.1.	 In Visual Studio press the "Ctrl" + "F5" keys.
1.9.2.	 In Node.Js, locate yourself in the SPA project and execute the command "ng serve --host".



### 2)	Angular Material
Angular Material is a Google team project, with the aim of creating a series of high quality UI components, based on the specifications of Material Design; which is used in many applications inside and outside of Google. This project provides a set of reusable, well-tested and accessible UI components based on the design of materials.
To install it you can follow the following tutorial:
https://v5.material.angular.io/guide/getting-started

![Dm Img 1 Angular Material](/uploads/wish-grid/dm-img-1-angular-material.png "Dm Img 1 Angular Material")
### 3)	Bitbucket Repository
Bitbucket is a web-based hosting service for projects that use the Mercurial and Git version control system. It offers paid and free accounts, with an unlimited number of public and private repositories (where you can have up to five users).
You can access and create your new private repository through the following address:
https://bitbucket.org/product


![Dm Img 2 Bitbucket Repository](/uploads/wish-grid/dm-img-2-bitbucket-repository.png "Dm Img 2 Bitbucket Repository")

### 4)	Git
Git is a version control software for maintaining application versions when they have a large number of source code files. Its purpose is to keep track of changes in computer files and coordinate the work that several people perform on shared files.
To install it you can follow the following tutorial:
https://medium.com/laboratoria-how-to/c%C3%B3mo-instalar-git-368c78187b51
Once you are located inside the project folder, open the git bash and execute commands:
	git init
	git remote add origin “address of your remote repository created in Bitbucket” 
In this case it is: https://Canitron@bitbucket.org/Canitron/wishgrid.git

![Dm Img 3 Git](/uploads/wish-grid/dm-img-3-git.png "Dm Img 3 Git")

### 5)	SourceTree
SourceTree is perhaps one of the best GUI clients to handle git and mercurial repositories that exist today. To install it you can follow the following tutorial:
https://confluence.atlassian.com/get-started-with-sourcetree/install-sourcetree-847359094.html
a.	Enter your Atlassian account.
b.	Skip the configuration in the "Connect an account" step.
c.	Select "I do not want to use Mercurial."
d.	Drag the folder of your project to the SourceTree.
e.	Enter the project and enter your email address.
f.	Click Fetch and then OK.
g.	Enter the password of the account with which was created the Repository in Bitbucket.
h.	Click on Pull, select "master" on "Remote Branch to pull" and then click OK.
The download of all files uploaded to the repository will begin and you will see it as follows:

![Dm Img 4 Sourcetree](/uploads/wish-grid/dm-img-4-sourcetree.png "Dm Img 4 Sourcetree")
### 6)	Postman
Postman is a tool aimed at web developers that allows to make HTTP requests to any API. Postman is very useful when it comes to programming and testing, since it offers the possibility to check the correct performing of developments.

![Dm Img 5 Postman](/uploads/wish-grid/dm-img-5-postman.png "Dm Img 5 Postman")
### 7)	Ngx-Translate
NGX-Translate is an internationalization library for Angular. It allows you to define translations for your content in different languages and switch between them easily. It gives you access to a service, a policy and a conduit to handle any dynamic or static content.
To implement it you can follow the following tutorial:
https://www.codeandweb.com/babeledit/tutorials/how-to-translate-your-angular-app-with-ngx-translate



### 8)	reCaptcha
reCAPTCHA is a free service that protects your website from spam and abuse. reCAPTCHA uses an advanced risk analysis engine and adaptive CAPTCHAs to keep automated software from engaging in abusive activities on your site. It does this while letting your valid users pass through with ease.
reCAPTCHA offers more than just spam protection. Every time our CAPTCHAs are solved, that human effort helps digitize text, annotate images, and build machine learning datasets. This in turn helps preserve books, improve maps, and solve hard AI problems.
To implement it you can follow the following tutorial:
https://github.com/eliasmpw/demo-ng-recaptcha-charla
You must use a site key generated by Google exclusively for your project in:
https://www.google.com/recaptcha

![Dm Img 6 Recaptcha](/uploads/wish-grid/dm-img-6-recaptcha.png "Dm Img 6 Recaptcha")
### 9)	JSON Web Token
JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.
You can get more detail at the following address:
https://jwt.io/introduction/


## Points of Contacts
MegadeV Team: (wishgrid@googlegroups.com)
Miguel Castedo (mcastedo@info-arch.com)
Nathalie Guzmán I. (nguzman@info-arch.com)
Oscar Laura (olaura@info-arch.com)
Oscar Soliz (osoliz@info-arch.com)
Richard Arteaga (rarteaga@info-arch.com)
Wilber Padilla (wpadilla@info-arch.com)
