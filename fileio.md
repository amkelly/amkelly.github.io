---
permalink: fileio
---
# File I/O

## reading & writing files

 [python.org tutorial: reading & writing files](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files)
 [realpython.com article: Reading and Writing Files in pythong](https://realpython.com/read-write-files-python/#iterating-over-each-line-in-the-file)

## os.path and pathlib

os.path is the older set of methods for OS-independent path manipulations. Path lib provides a more structured, convienent set of methods for these manipulations. 

On pathlib:
> This module offers classes representing filesystem paths with semantics appropriate for different operating systems. Path classes are divided between pure paths, which provide purely computational operations without I/O, and concrete paths, which inherit from pure paths but also provide I/O operations. 

There are a number of useful methods in pathlib, such as [Path.is_file()])https://docs.python.org/3/library/pathlib.html#pathlib.Path.exists() and [Path.iterdir()](https://docs.python.org/3/library/pathlib.html#pathlib.Path.iterdir) 

I've also used Path.is_file() but read instructions for [Path.exists()](https://docs.python.org/3/library/pathlib.html#pathlib.Path.exists) and should be cautious I'm using the correct of these two methods since they will of course produce different outputs. This is especially true when dealing with directories containing subdirectories:

    given a file tree:
    ./subdir
    ./file
    file.txt

where Path.exists('./file') would evaluate as True, this is telling me a course that my directory contains a folder named 'file' not a file named file. Path.is_file(./file) would return False, since it is evaluating the existence of an object and that it is a regular file, not a directory.

### python.org library documentation:
* [os.path](https://docs.python.org/3/library/os.path.html)
* [pathlib](https://docs.python.org/3/library/pathlib.html#module-pathlib)
* [glob](https://docs.python.org/3.6/library/glob.html)

I read about the difference between the existing os.path module and pathlib module in [this article: Why you should be using pathlib] (https://treyhunner.com/2018/12/why-you-should-be-using-pathlib/) (via [pythonbites]) and this straighforward introduction to its usage: https://jefftriplett.com/2017/pathlib-is-wonderful/

When doing a simple operation like:


```
>>> with open('workfile') as f:
    read_data = f.read()
```

I ran into problems as soon as I'd tried to put files in a subdirectory of my script:

``` with open('/data/workfile') as f:
    read_data = f.read() 
```

so, intead I ended up with this by using pathlib:
```
 capstone_metadata = Path('./data/capstone_metadata.txt').read_text(encoding='UTF-8')
```

## glob

Looks like the glob library was introduced at the same time as pathlib 

(and pathlib offers some of the same abstractions of file and path searching. Havne't needed to use glob in work so far. (8/28/2020))

Earlier in August I wrote this code:

```
def file_type_handler(f):
    if ".pdf" in f:
        print("pdf extraction is unavailable")
    elif ".doc" in f:
        extract_doc(f)
    elif ".docx" in f:
        extract_doc(f)
    else:
        print("invalid file")  
```

There are a few optimizations to be made here:
* glob can find files with a given extension
* pathlib can parse a file's location and return the file's suffix:

```
filelocation = '/data/file.txt'
Path(filelocation).suffix
'.txt'
```

## copying files with shutil

[Real Python: Copying files in python](https://realpython.com/working-with-files-in-python/#copying-files-in-python)

[Python Docs: Shutil.copy](https://docs.python.org/3.8/library/shutil.html#shutil.copy)

(see also copy2, which attempts to preserve more file metadata such as modification time and permissions)