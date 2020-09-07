---
permalink: libraries
---

# Python Libraries & modules

A collection of the python libraries I've used and notes about their usage or performance.

## notes on the built-in/standards libraries
(that I haven't written about elsewhere)

See [fileio](./fileio) for information on pathlib, glob, open, write, etc.

### regular expressions

* [re docs](https://docs.python.org/3/library/re.html)
* [Regular Expressions in Python (realpython.com)](https://realpython.com/regex-python/)
a detailed article that scaffolds a bit fast, but has a lot of detail. Useful to have the same complex topic explained twice.

#### replace: 
* [re.sub docs](https://docs.python.org/3/library/re.html#re.sub)
* [re.sub howto](https://docs.python.org/3/howto/regex.html#search-and-replace) 

### subproccess

* [subprocess docs](https://docs.python.org/3/library/subprocess.html)

An important note on passing arguments (ie, the command itself and it's arguments) to subproccess.run() and associated functions like lower-level subpross.popen()

> args is required for all calls and should be a string, or a sequence of program arguments. Providing a sequence of arguments is generally preferred, as it allows the module to take care of any required escaping and quoting of arguments (e.g. to permit spaces in file names). If passing a single string, either shell must be True (see below) or else the string must simply name the program to be executed without specifying any arguments. quote from [here](https://docs.python.org/3.6/library/subprocess.html#frequently-used-arguments) 

I thought the note above helps to explain why a command I'm trying to use, structured as a single string returns an error:
> FileNotFoundError: [WinError 2] The system cannot find the file specified

but that appears to be associated more with Windows understanding paths and scripts than it does the structure of the agruments passed to subprocess.
Once I passed the arguments as a list to the subprocess module it worked:

> subprocess.run(
>                args=['anystyle', '-f', 'bib', 'parse', ('.\\' + str(f))],
>               shell=True, 
>               stdout=text_contents
>                )

The key thing here appears, in windows, though it's a security risk, is the 'shell=True' flag, which appears to have allowed the command to be processed or run correctly by the underlying system.

A couple of stackoverflow questions I referenced in working with this module [here](https://stackoverflow.com/questions/37238645/how-to-open-external-programs-in-python
and [here](https://stackoverflow.com/questions/89228/calling-an-external-command-from-python)

### sqlite

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

## external libraries & modules
* [requests](https://2.python-requests.org/en/master/)

Gernally useful guide: [Real Python: Python Requests Library Guide](https://realpython.com/python-requests/)
[https://realpython.com/python-requests/#ssl-certificate-verification](https://realpython.com/python-requests/#ssl-certificate-verification)

* [docx2text](https://github.com/ankushshah89/python-docx2txt)

Installed on dev system and planning to use for some text extraction. see sabbatical/plaintext-extract.py

* [click](https://palletsprojects.com/p/click/)

Library for constructing command line interfaces, makes help dialogs automatically. Considering for tieing the scripts together into a single cli utility.

* [dvc - data version control](https://pypi.org/project/dvc/)

see realpython article about using this utility [here](https://realpython.com/python-data-version-control/)
This sounds like an emerging set of tools & best pracites that are worth adopting. Wonder about it's use with, say, pandas for data shaping and cleanup, presumably this is exactly the usecase, so you can better track data science work in normalization or cleanup like you're so often doing in pandas before analysis & visualization.

* PDFminer.six

A module for processing and handling PDF documents. I was mostly interested in its ability to extract plaintext from PDF documents for my sabbatical project. It did this well enough for general use but the original document's formatting prevents the extraction from being good enough for my purposes. I'm relying instead on extraction with the 