---
title: "SQL Procedures in Alteryx"
thumbnailImagePosition: left
thumbnailImage: /img/sqlalteryx.png
author: "Ainize Cidoncha"
date: 2017-07-18T21:13:14-05:00
categories: ["Alteryx"]
tags: ["Alteryx", "analytics","SQL","Temp Tables"]
---


Do you love Alteryx but have already complex SQL queries that you would like to use as your input data?

Alteryx is great and it is usually my go to point when I need to manipulate data. However, in the team we also use SQL quite often, for instance, there are some pre-defined queries that make it easier for us to get the output we want. 

In some cases, I want to develop further manipulation or analysis on those tables connecting them directly to Alteryx. When the SQL does not use temporary tables everything is fine and you only need to paste your query on the SQL editor of the Input Tool.

But...

What if your SQL uses temporary tables? Alteryx doesn't like it and would show an error.

An option for this is recreating the SQL in Alteryx which an be too much work in some cases. Fortunately there is another workaround to it:

STORED PROCEDURES

Although this solves the problem it is not straightforward how to call stored procedures on Alteryx. When I first tried to do this I encountered several problems configuration the Alteryx input tool.

But let's first of all create a stored procedure and discuss the Alteryx error afterwards.


1.Create a stored procedure on SQL which creates a Global Temporary Table

All you need to is use the SQL code:

```SQL
create procedure schema_name.procedure_name (@parameter1,@parameter2,..)
as
--insert your SQL here
``` 

Make sure you last select statement is creating a global temporary table using ##. This would allow your temporary table to be visible in all environments.

```sql
Select *
From #Temp
Into ##Data
``` 

Once you execute it you will see there is a new procedure on your database.

2.Imputing the stored procedure into Alteryx

The first instinct I have was to use the Store Procedures option when connecting to a database:
![](/img/storedprocedure_bad.png)

But that wouldn't work. There was no way to enter the parameters and even for a procedure without parameters I would get the error:

<span style="color:red">No columns returned</span>


After some research and unsuccessful attempts (using Dynamic Input tool, for instance) I made it work! The main point is **use of the Pre SQL Statement option** in the Tool Configuration.

The way of doing it is the following, we need to open the Pre SQL option and type:

```SQL'
exec schema_name.procedure_name parameter1,parameter2,...
``` 

Then, go to the Table or Query option and select the temporary table your stored procedure creates.

```SQL
Select * from ##Data
``` 

Your Configuration Tool should look like this:

![](/img/Alteryx store procedure.png)

Click run and your workflow should return you SQL query!


