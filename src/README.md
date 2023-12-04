# Laboratory #6 - DB Access with Python

## Description
In this lab we will develop a web-based application that generates reports by reading objects from a relational database
in MySQL. 

The problem at hand is a simplified version of the University scenario we handled several times. 
The main body of the classes are already provided for you.  

### To-Dos
Follow the `#TODO` list provided on the PyCharm project.

## Flask
[Flask](https://palletsprojects.com/p/flask/) is a Python framework that allows to set up a *HTTP server* by just 
creating an application and defining the Python code associated with the http `routes`.
A `route` corresponds to the requested "page" in the server. 
For instance if our server is `https://university.com` 

- the *home* route is `/` corresponding to `https://university.com/`
- the *login* route is `/login` corresponding to `https://university.com/login` 
- and so on so forth.

The main files when you create a PyCharm Flask Project are:

- `app.py`: where we define the routes and the associated code to each one. 
- `templates`: here we define the way to present the information.

In a template, we define blocks. For instance we define the general layout and another page that will list students by 
receiving a `list` of students. 
By doing this, you can always display the student list in the same way, and if you need to modify how to display students,
by modifying a single file we will change all students lists, which is great for re-usability. 

**Most *flask* code in this Lab has been provided to you. Please review it!** 

## Classes
### University
Implements a reduced version of the university, which in this case is just a standpoint to access the system. 

### Course
Represents a course. Will be responsible to load all objects from the database.

### Student
Represents a student, which will have a standing such as UNDERGRADUATE, GRADUATE, etc.
As this is a simplified version, we will not implement inheritance today.   

This class will be responsible to load all objects from the database.

## Database
### Credentials
The following dictionary has all the credentials to connect to the database.
```
{
"hostname": "cse-mllab-pastorino.ucdenver.pvt", 
"port": 3399, 
"user": "guest", 
"passwd": "guest",
"database": "university"
}
```

### Schema
The database for the university will have two tables:

#### Table: `university.course`
The `course` table stores the course objects.

|Attribute | Type |
| --- | ---|
|subject | integer|
|number| integer|
|title | string |

The **Primary Key** is **(subject,number)**. So, you will need both attributes to identify a course row in the table.

#### Table: `university.student`
The `student` table stores the student objects.

|Attribute | Type |
| --- | ---|
| id| string |
| name| string |
| email| string |
| standing| string |
| gpa| decimal(3,2)|

The **Primary Key** is **(id)**.

### Hints: SQL Queries

* **Course Queries**  
    - `SELECT subject, number, title FROM university.course`
        + Retrieve all courses.
    - `SELECT subject, number, title FROM university.course WHERE upper(subject) like "%CSCI%"`
        + Retrieve courses with 'CSCI' in the subject.
    - `SELECT subject, number, title FROM university.course WHERE subject = "CSCI" and number = 3920`
        + Retrieve the course CSCI3920.
* **Student Queries**
    - `SELECT id, name, email, standing, gpa FROM university.student`
        + Retrieve all students.
    - `SELECT id, name, email, standing, gpa FROM university.student WHERE id = "0010"`
        +  Retrieve the student with student's id "0010".
    - `SELECT id, name, email, standing, gpa FROM university.student WHERE upper(name) like "%JOHN%"`
        + Retrieve the students with "JOHN" in the student's name.
 