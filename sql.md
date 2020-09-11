---
permalink: Databases & SQL
---

# SQL platforms:

* SQLite

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

* MSSQL

## pyodbc

Works in a similar was as SQLite driver above. 

See Microsoft documentation and quickstart guide [here](https://docs.microsoft.com/en-us/sql/connect/python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc?view=sql-server-ver15)

The machine running the python script must have a driver installed through which pyodbc functions to send commands to the given server.
The current version for MSSQL Server is available [here](https://docs.microsoft.com/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server?view=sql-server-ver15) 

More information on troubleshooting this problem was found [here](https://github.com/mkleehammer/pyodbc/wiki/Connecting-to-SQL-Server-from-Windows)


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