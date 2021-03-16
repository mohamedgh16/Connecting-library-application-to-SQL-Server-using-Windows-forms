# Connecting-library-application-to-SQL-Server-using-Windows-forms

### Introduction

windows forms is one of the best tools used in making applications.
With windows forms, you can make a variety of applications, from a mini calculator to a library application that connects to a database. In this tutorial, we will connect a library application using Windows forms to a database using SQL Server.

In this tutorial, we will use a windows forms project and work on it, we will add new forms that will add edit & delete books from the library, we will also manage the authors, the stores & the publishers stored in the database. We will display the information of each attribute & refresh it each time a change accrues.

### Prerequisites

Before we begin, it would help you as the reader to have the following:

- A basic understanding of C# programming language.
- A basic understanding of Windows forms.
- Visual studio installed on your system.
- SQL server installed on your system.

If you don’t have Visual Studio installed on your computer, you can check this article on how to set up the C# environment in Visual Studio [here](https://www.geeksforgeeks.org/setting-environment-c-sharp/), and for SQL server you can download it from [here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads). If you are new to Windows forms you can check this tutorial that would help you understand The basics of it [here](https://www.section.io/engineering-education/getting-started-with-windows-forms-using-c-sharp/).


### Creating the pubs database

First of all you should create the pubs database Query in SQL server so it can be later connected to the application.
You can find the pubs database [here](https://github.com/microsoft/sql-server-samples/blob/master/samples/databases/northwind-pubs/instpubs.sql).

After copying the database paste it in a new Query and excute it, you should be able to see the the name of the database "pubs" to the left of your screen.

![CreatingPubs](https://github.com/mohamedgh16/Connecting-library-application-to-SQL-Server-using-Windows-forms/blob/main/CreatingPubs.png).

### Application main form

We will use a project that has a main form & add another 3 forms that would add edit & delete books from the database.
You can download the project from [here](https://github.com/mohamedgh16/Library-app-code-in-windowsforms).

### Add form

After opening the project first we will work on the Add form, As you can see it has 3 buttons, each button for a different operation.

![Mainform](https://github.com/mohamedgh16/Connecting-library-application-to-SQL-Server-using-Windows-forms/blob/main/Mainform.png).

double click 






















### Conclusion
