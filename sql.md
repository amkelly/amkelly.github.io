---
title: Databases & SQL
permalink: sql
---

# SQL platforms:

## SQLite

* [python standard library docs: sqlite](https://docs.python.org/2/library/sqlite3.html)

A common data-persistence solution without all the weight of a full MSSQL or MySQL server. 
Likely that my current projects wouldn't require anything so large, but not sure about limitations, presumably tied to table size and avaialble RAM.

The following article ["Appropriate Uses for SQLite"](https://sqlite.org/whentouse.html) appears to allay the size concerns, at least for this project. Seems as though there are few downsides to using SQLite as long as you're not designing a client-server system. (which, I'm not at the database level.)

worth looking into for prototyping DB schema/parsing and benchmarking/testing against suggested MSSQL server on College server which is available.
(does an aplication's DB & schema usually live in or outside of version control? where is line there between application data and application itself?)

ran into problems getting the python sqlite library (ie: import sqlite3) working in anaconda on windows. Found [this](https://stackoverflow.com/questions/54876404/unable-to-import-sqlite3-using-anaconda-python) stackoverflow question which fixed issue. (copied the sqlite3 dll to C:\Users\myusername\Local\Continuum\Anaconda3\DLLs)

ran into a sytax error with the following statement:

> c.execute('ALTER TABLE bibtex ADD COLUMN (?, ?);', (entry, 'text'))

Table names cannot be parameterized, so that won't work as above. See Stackoverflow answer [here](https://stackoverflow.com/questions/18159352/python-sqlite-near-syntax-error) 

### Datatypes in SQLite:

There are only 5: NULL, INTERGER, REAL, TEXT, BLOB. I've used 'text' or 'int' for all the data inputs in the python code I've written for SQLite, given the huge amount of variablility in the incoming data. See official SQLite Docs [here](https://www.sqlite.org/datatype3.html) for more information and notes below on MSSQL datatypes. 

## MSSQL

### pyodbc

Works in a similar way as SQLite driver above. 

See Microsoft documentation and quickstart guide [here](https://docs.microsoft.com/en-us/sql/connect/python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc?view=sql-server-ver15). Offical documentation for the library itself is [here](https://github.com/mkleehammer/pyodbc/wiki) with information about the module's objects [here](https://github.com/mkleehammer/pyodbc/wiki/Objects).

The machine running the python script must have a driver installed through which pyodbc functions to send commands to the given server.
The current version for MSSQL Server is available [here](https://docs.microsoft.com/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server?view=sql-server-ver15) 

More information on troubleshooting this problem was found [here](https://github.com/mkleehammer/pyodbc/wiki/Connecting-to-SQL-Server-from-Windows)

### Creating an account with required permissions in MSSQL:

You must creat a user and then a login, first a the server level and then a login for a given database. I changes the password policies away from the default, since my python script will not interactively changes or update it's password. 

An account that creates tables in addition to read & write permissions. More information on [this](https://dba.stackexchange.com/questions/225359/sql-server-database-level-roles-for-creating-tables) Stackoverflow question and corresponding Official MS documentation [here](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/database-level-roles?view=sql-server-2017).

I ended up granting slightly more permissions than I might like to the login, but it only has these permissions on this database on this server. I granted: db_datawriter, db_datareader, and db_ddladmin.

### Backing up / exporting the SQL Server data

This is something to look into, is there an equivalent of SQLDump? Putting this file, or similar into DVC, if that seems a good route to go? Or export the SQL data as dataframe object? Is there canonical way to store such an object on disk? I think there may likely be. 

(what's advantage of the SQL DB given the small size of the dataset? I guess it's interoperability with PowerBI.)

SQL Server's Import & Export Wizard documentation [here](https://docs.microsoft.com/en-us/sql/integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard?view=sql-server-ver15)

### Working with column data types

In initially creating the tables in the MSSQL database, I ended up just copying the datatype 'text' from SQLite without giving it much thought, but SQLite has a much smaller number of column data types and 'text' in SQLite is not equivalent to 'text' in MSSQL.  (In fact, 'text' is being deprecated in future versions of MSSQL Server. See documentation [here](https://docs.microsoft.com/en-us/sql/t-sql/data-types/ntext-text-and-image-transact-sql?view=sql-server-ver15)) It is being replaced with varchar(max), that holds text objects of the same size as the 'text' data type. [This](https://www.mssqltips.com/sqlservertip/4485/comparison-of-the-varcharmax-and-varcharn-sql-server-data-types/) article provides a good summary of the difference between and tradeoffs in using varchar(1-8000) and varchar(max).

Documentation on numeric types (INT, etc) [here]() and datetime types [here]()

One of the difficult things to determine in making a table (with it's corresponding Data Definition) is of course determining how best of use the given data types, especially in cases like varchar where you must declare a maximum length for the values in the given data you'll be inputting. For example, I don't know the maximum length of an article title or a person's name in the data I'm loading into the database, so I should take a guess as to a reasonable maximum. 

### Primary & Foreign Keys

Documentation on Primary Key creation [here](https://docs.microsoft.com/en-us/sql/relational-databases/tables/create-primary-keys?view=sql-server-ver15)

* MySQL

Not used in current Sabbatical project, but widely used DB in many other applications and other organizations. 

# SQL Syntax:

## CREATE

## INSERT

## ALTER

For instance:

> ALTER TABLE name ADD column text;

See [here](https://docs.microsoft.com/en-us/sql/relational-databases/tables/add-columns-to-a-table-database-engine?view=sql-server-ver15) for similar statement in MSSQL

## DROP

One thing I've discovered is that column cannot be dropped from a SQLite database, you have to copy the table to a temporary one and recreate is.

Official SQLite Documentation [here](https://www.sqlite.org/faq.html#q11) 

## SELECT

## UPDATE 



## COUNT

    SELECT COUNT(DISTINCT bibtex.entrytype)
	FROM bibtex;

in this case, allows me to see how many distinct entries exist in the values of the column 'entrytype'.

## VARIOUS:

    SELECT MAX(DATALENGTH(entrytype))
        FROM bibtex

This helped me to determine the needed length of a given column's datatype's length, mostly in case there were some major outliers I was missing. In my data set for instance, the 'title' field in the bibtex table returns a max datalength of 1982, which seems very large number of characters. The Transact SQL documentation calrifies that DATALENGTH is not the same as LEN:

> Use the LEN to return the number of characters encoded into a given string expression, and DATALENGTH to return the size in bytes for a given string expression.

Which brings me back to the issuses I've had with my inadvetant, poor use of data typing when I created the tables. 