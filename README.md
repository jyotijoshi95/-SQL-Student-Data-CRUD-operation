# Student Information System (CRUD Operation)

This repository contains SQL scripts for creating a student table, inserting data, and querying information from the table. The data includes student details such as name, gender, class, email, phone number, club name, total grade, and grade status.

## Table of Contents
- [Create Student Table](#create-student-table)
- [Insert Data into Student Table](#insert-data-into-student-table)
- [Select All Student Data](#select-all-student-data)
- [Update Gender and Gradestatus](#update-gender-and-gradestatus)
- [Querying Student Information](#querying-student-information)

## Create Student Table
```sql
/* create student table */
Create table Student(
    Id int identity(1,1) primary key,
    StdName varchar(10),
    Gender char(1),
    Class int,
    EmailId varchar(20),
    Phoneno int,
    Clubname varchar(30),
    Totalgrade float,
    Gradestatus char(1)
)
```

## Insert Data into Student Table
```sql
/* insert data into student table */
insert into student (StdName, gender, class, emailid, phoneno, clubname, totalgrade) values 
    ('Ankita','F',4, 'wer@gmail.com',123653456, 'Red', 34.89 ),
    ('Alex','F',3, 'Alex@gmail.com',456653456, 'Blue', 34.89 ),
    -- Add more data here...
```

## Select All Student Data
```sql
/* select all student data */
Select * From Student
```

## Update Gender and Gradestatus
```sql
/* set Gender value to "F" where clubname is "PINK" */
update Student set gender = 'F' where Clubname = 'pink'

/* set Gradestatus value F, if student totalgrade is below or equal to 40 */
update student set Gradestatus = 'F' where Totalgrade <= 40 

/* set Gradestatus value P, if student totalgrade is above 40 */
update student set Gradestatus = 'P' where Totalgrade > 40 

/* set Gradestatus value P even if it is fail(F), if student class is less than or equal to 6 */
update student set Gradestatus = 'P' where Class <= 6 and Gradestatus = 'F'  
```

## Querying Student Information
```sql
/* get students who belong to the red club and have female gender(F) */
select * from Student where Gender = 'F' and Clubname = 'Red'

/* get students above class 6 with female gender but grade status is fail(F) */
Select * from Student where class > 6 and Gender= 'F' and Gradestatus = 'F' 

/* get students from the Orange club with male gender but grade status is pass */
Select *from Student where Clubname = 'orange' and Gender= 'M' and Gradestatus= 'P'

/* get top 10 students where grade is more than 80 */
select top 10 * from student where Totalgrade < 80 

/* get top 5 female students having grade status F, ordered by ID in descending order */
Select top 5 *from Student where Gradestatus= 'F' order by id desc

/* get top 5 female students having grade status pass (P) and club is red, with ID less than 15 */
Select Top 5*from Student  where Gradestatus= 'P' and Clubname = 'red' and id <15

/* get top 5 students having grade status pass(P) and club is Pink, ordered by ID in descending order */
Select Top 5*from Student where Gradestatus='P' and Clubname = 'pink' order by id desc

/* get top 10 students having grade status F and club is Orange, ordered by Totalgrade in ascending order */
Select Top 10 *from Student where Gradestatus= 'F' and Clubname= 'orange' order by Totalgrade 

/* get top 10 students with class greater than 3 and club is red, ordered by StdName in descending order */
Select Top 10 * from student where class >3 and Clubname = 'red' order by StdName desc 
```
