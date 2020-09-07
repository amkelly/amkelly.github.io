---
permalink: SQL
---

# SQL platforms:

* SQLite

For notes on SQLite usage in python see notes on the sqlite3 library [here](./libraries).

* MSSQL
* MySQL

# CREATE

# INSERT

# ALTER

For instance:

> ALTER TABLE name ADD column text;

See [here](https://docs.microsoft.com/en-us/sql/relational-databases/tables/add-columns-to-a-table-database-engine?view=sql-server-ver15) for similar statement in MSSQL

# DROP

One thing I've discovered is that column cannot be dropped from a SQLite database, you have to copy the table to a temporary one and recreate is.

Official SQLite Documentation [here](https://www.sqlite.org/faq.html#q11) 

# SELECT