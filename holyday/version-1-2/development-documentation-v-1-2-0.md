<!-- TITLE: Development Guide V1.2 -->
<!-- SUBTITLE: HolyDay  -->


# Introduction
Holyday is a vacation manager that aims to make easy the requests process of absences, provide employees information and notify the status of it.
In this document HolyDay structured is detailed, what technologies were used to carry out this project, and the definitions of each diagram implemented.
# Used Technologies

![Img 1](/uploads/holyday/img-1.png "Technologies")

In this application, some technologies were used to help facilitate the stages of development, implementation and documentation.

## Visual Studio
Microsoft Visual Studio is an integrated development environment (IDE) from Microsoft. It is used to develop computer programs, as well as websites, web apps, web services and mobile apps. Visual Studio uses Microsoft software development platforms such as Windows API, Windows Forms, Windows Presentation Foundation, Windows Store and Microsoft Silverlight. It can produce both native code and managed code.
 
## TFS
Team Foundation Server (commonly abbreviated to TFS) is a Microsoft product that provides source code management (either with Team Foundation Version Control or Git), reporting, requirements management, project management (for both agile software development and waterfall teams), automated builds, lab management, testing and release management capabilities. It covers the entire application lifecycle, and enables DevOps capabilities. TFS can be used as a back-end to numerous integrated development environments (IDEs) but is tailored for Microsoft Visual Studio and Eclipse on all platforms.

## SQL Server
Microsoft SQL Server is a relational database management system developed by Microsoft. As a database server, it is a software product with the primary function of storing and retrieving data as requested by other software applications—which may run either on the same computer or on another computer across a network (including the Internet).

## Balsamiq Wireframes
Balsamiq Mockups is a graphical user interface mockup and website wireframe builder application. It allows the designer to arrange pre-built widgets using a drag-and-drop WYSIWYG editor. The application is offered in a desktop version as well as a plug-in for Google Drive, Confluence and JIRA.

## Enterprise Architect
Sparx Systems Enterprise Architect is a visual modeling and design tool based on the OMG UML. The platform supports: the design and construction of software systems; modeling business processes; and modeling industry-based domains. It is used by businesses and organizations to not only model the architecture of their systems, but to process the implementation of these models across the full application development life-cycle.

# System Models

## Domain Model

### **Description**
A domain model is a structural model of basic domain concepts and the relationships between them. A domain model may contain domain objects, conceptual classes, associations, or attributes.

### **Diagram**

![Img 2](/uploads/holyday/img-2.png "Domain Model")

## Database Model

### **Description**
The database diagram was made with a conceptual design, this makes a high-level description of the structure of the database. Its purpose is to describe the information content of the database and not the storage structures that will be needed to handle that information.

### **Diagram**

![Database Diagram](/uploads/holy-day-development-documentation-v-1-2-0/database-diagram.jpg "Database Diagram")

![Database Diagram 2](/uploads/holy-day-development-documentation-v-1-2-0/database-diagram-2.jpg "Database Diagram 2")

## Component Model

### **Description**
A component diagram shows the parts of a design for a software system. A component diagram helps you visualize the high-level structure of the system and the service behavior that those pieces provide and consume through interfaces.
**Component. -** A reusable piece of system functionality. A component provides and consumes behavior through interfaces and can use other components.

### **Diagrams**

![Img 4](/uploads/holyday/img-4.png "Component Model")

### **Main components diagram**

![Img 5](/uploads/holyday/img-5.png "Main Components Diagram")

### **Model component diagram**

![Img 6](/uploads/holyday/img-6.png "Model Component Diagram")

### **Controller component diagram**

![Img 7](/uploads/holyday/img-7.png "Controller Component Diagram")

### **View Components diagram**

![Img 8](/uploads/holyday/img-8.png "View Component Diagram")

## Architecture Model

### **Description**
The physical view depicts the system from a system engineer's point-of-view. It is concerned with the topology of software components on the physical layer, as well as the physical connections between these components. This view is also known as the deployment view. UML Diagrams used to represent physical view include the Deployment diagram.

### **Diagram**

![Architecture Moden](/uploads/holy-day-development-documentation-v-1-2-0/architecture-moden.jpg "Architecture Model")