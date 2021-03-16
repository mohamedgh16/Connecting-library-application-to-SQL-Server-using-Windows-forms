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

After opening the project first we will work on the main form, As you can see it has 3 buttons, each button for a different operation.

![Mainform](https://github.com/mohamedgh16/Connecting-library-application-to-SQL-Server-using-Windows-forms/blob/main/Mainform.png).


Add a refresh button and 3 more tabs next to the Title tab to use it later, then add 4 more columns to the datagridview to show the data of the library.
Also dont forget to change the colors of the forms & the buttons to what ever that suits your taste.

It should look like this ![Afterformwork](https://github.com/mohamedgh16/Connecting-library-application-to-SQL-Server-using-Windows-forms/blob/main/Afterformwork.png).

### Database connection
In order to connect to SQL server in c# we will be ```c#
using System.Data.SqlClient;
                                         ```
The following code snippet will connect your computer to the database, but note that you need to put your own computer name instead of (HP-PAVILION).                                          
```c#
static SqlConnection connectionString = new SqlConnection(@"Data Source=HP-PAVILION;Initial Catalog=pubs;Integrated Security=True");
```
Each Select Query will be written in a string and get converted to SQL server then back to use it somewhere inside the code. 
```c#
 public static DataTable dataAdapterSelect(string sqlQuery)
        {
            SqlDataAdapter DataAdapter = new SqlDataAdapter(sqlQuery, connectionString);
            DataTable dt = new DataTable();
            DataAdapter.Fill(dt);
            return dt;
        }
```
The following method will be used to Add Edit & delete the information from the database.
```c#
public static void sqlCommandQueryReader(string sqlQuery)
        {
            SqlCommand myCommand = new SqlCommand(sqlQuery, connectionString);
            myCommand.Connection.Open();
            SqlDataReader dr;
            dr = myCommand.ExecuteReader();
            while (dr.Read())
            {
                Console.WriteLine(dr[0]);
                Console.WriteLine(dr[1]);
            }
            myCommand.Connection.Close();
        }
```

 
The following code will use the dataAdapterSelect method to covert the Select string to a Query and display it inside the datagridview.
```c#
 string sqlQuery = "SELECT title_id,title,type,pub_name,price,ytd_sales FROM titles inner join publishers ON titles.pub_id = publishers.pub_id";

            DataTable dt = DataBaseConnection.dataAdapterSelect(sqlQuery);
           
            foreach (DataRow dr in dt.Rows)
            {
                dataGridView1.Rows.Add(dr["title_id"], dr["pub_name"], dr["price"], dr["ytd_sales"], dr["title"],dr["type"]);
            }
```


### Add form 

Adding a new book will require the title id title name title type publisher id publisher date & the price of the book.
We will request the information from the user and insert them into the database using the sqlCommandQueryReader method.
![Addform]().

```c#
 private void addButton_Click(object sender, EventArgs e)
        {   string titleID = titleIDTextBox.Text;
            string titleName = titleNameTextBox.Text;
            string titletype = Titletype.Text;
            string pubid = pubbid.Text;
            string pricee = price.Text;
            string pubbdate = pubdate.Text;

            string insertt = "insert into titles(title_id,title,type,pub_id,price,pubdate)
            values('" + titleID + "','" + titleName + "','" + titletype + "','" + pubid + "','" + pricee + "','" + pubbdate + "');";

            DataBaseConnection.sqlCommandQueryReader(insertt);
            MessageBox.Show("Information inserted!");}
```
### Edit form 

Editing a book will require the title id title name title type publisher id publisher date & the price of the book.
We will request the information from the user and insert them into the database using the sqlCommandQueryReader method.


















### Conclusion
