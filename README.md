# amkelly.github.io
## Python & programming notes

A repository for organizing and publishing notes as I work to learn and understand python and computer science in both professional and personal projects. Writing about something as I'm learning it helps me understand it better.

I bought a recent humble bundle of python training resources here and have been working my way through How to Think like a computer science.

Working on some python exercises occasionally too on codewars.io, [pythonmorsels] and [Reuven Lerner's Weekly Python Exercises](https://lerner.co.il)

## Notes Pages:

* [Development Environments](./dev-environs)
* [Debugging, Benchmarking, and Test-Driven Development](./debug)
* [File I/O](./fileio)
* [Looping (draft)](./looping)
* [Regular Experssions](./regex) 
* [Libraries](./libraries)
* [Databases & SQL](./sql)
* [Lists](./lists)
* [Object Oriented Programming](./oop)
* [Related Software](./related)
* [PowerBI](./powerbi)

## General Python Resources:

### General Docs & Guides:

* [Zen of Python (PEP 20)](https://www.python.org/dev/peps/pep-0020/)
* [Real Python: How to Write Beautiful Python Code With PEP 8](https://realpython.com/python-pep8/)

Article and underlying PEP look like good places to go for general style information. The more of a handle I get on syntax, the more it becomes clear that there is of course more than one way to do any given operation, syntactically and stylistically. Working to understand the notion of some code being more or less 'pythonic' and therefore more or less, what?, elegant?, performant?, syntactially compact? It's a notion worth continuing to think through.

* [Python Code Cleanup for beginners] (https://imankulov.name/posts/python-cleanup/)

Seems to have a number of good suggestions on style, readability and maintainability. 

* [Exceptions as flow control](https://blog.cerebralab.com/Exceptions_as_control_flow)

## Unsorted notes & questions:

### Variables & Assignment:

[This article](https://treyhunner.com/2018/03/tuple-unpacking-improves-python-code-readability/) on multi-assignment and tuple packing/unpacking is very detailed and interesting. Seems like a very good feature of the language, especially beyond tuples such as:
    (a, b) = (b, a)

### Functions:
If you have a function with several arguments, it might make sense to have a list where each item is one of those arguments, how do you pass these items into the fuction?

```
def triangle_sides(a, b, c):
    return(sum(a, b, c))

triangle1 = [2, 2, 3]
triangle2 = [3, 4, 5]

```
since the fucntion is set up to take 3 arguments, it won't accept a single argument.
you could rewrite the function so that it accepts a list or tuple with 3 items though. I believe you can use the function's docstring to help document what the incoming parameter's of a function are.

* Functions and Docstings:

See: [PEP ](https://www.python.org/dev/peps/pep-0257/)

### modules & function notes for refactoring:

at end of week two of my sabbatical, I see there's lots of code getting reused, I see I'm writing two scripts each of which have to open a folder and iterate over contents with a function. I likely can and should extract those sorts of functions to a module as part of later refactoring. Can and should generalize the handling of the /data directories and writing files to / from them across the whole pipeline of processing the various files etc. Again a good thing to do when refactoring the code itself. 

in Sabbatical repo, most of the anystyle_helper.py file is recapitulating a slighly more complex set of processes in a previously-written script, so that 2nd one could have been much shorter, overall and reduce much of the complexity and redundancy of the second script. Would be good to make it signifigantly smaller. Worth thinking more about how to refactor and better document the code I'm writing so I am learning and adopting best practices around style and documentation as I go.

### data structures:

* [Real Python: Data Structures](https://realpython.com/python-data-structures/)

#### dictionaries: 

* [Real Python: Data Structures: Dictionaries](https://realpython.com/python-data-structures/#dictionaries-maps-and-hash-tables)
* [Official Python Docs](https://docs.python.org/3.8/tutorial/datastructures.html#dictionaries)

#### JSON:

While it's not a python data-structure, it's a common way to store and exchage data.

* [python docs: JSON library](https://docs.python.org/3/library/json.html)

Making use of constructing JSON files for DVC metrics by creating a dictionary which is converted to JSON using the library's json.dumps() method.