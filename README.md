# amkelly.github.io
## Python & programming notes

A repository for organizing and publishing notes as I work to learn and understand python and computer science in both professional and personal projects. Writing about something as I'm learning it helps me understand it better.

I bought a recent humble bundle of python training resources here and have been working my way through How to Think like a computer science.

Working on some python exercises occasionally too on codewars.io, pythonmorsels and 

## Notes Pages:

* [Development Environments](./dev-environs)
* [File I/O](./fileio)
* [Looping (draft)](./looping)
* [Regular Experssions](./regex) 
* [Libraries](./libraries)
* [Databases & SQL](./sql)

## General Python Resources:

### General Docs & Guides:

* [Zen of Python (PEP 20)](https://www.python.org/dev/peps/pep-0020/)
* [Real Python: How to Write Beautiful Python Code With PEP 8](https://realpython.com/python-pep8/)

Article and underlying PEP look like good places to go for general style information. The more of a handle I get on syntax, the more it becomes clear that there is of course more than one way to do any given operation, syntactically and stylistically. Working to understand the notion of some code being more or less 'pythonic' and therefore more or less, what?, elegant?, performant?, syntactially compact? It's a notion worth continuing to think through.

## Unsorted notes & questions:

### Print:

Like most other beginning developers, I use print statements often to help me to debug code as I'm writing it, though I should learn more about VS-Code's debugging and linting tools so I can get a good sense of how those work and speed up debugging.

watching my code loop this morning and print out a long series of values I wondered about how much these statements slow down the actual execution of the code and found [this](https://stackoverflow.com/questions/13288185/performance-effect-of-using-print-statements-in-python-script) stack overflow answer.

### Functions:
If you have a function with several arguments, it might make sense to have a list where each item is one of those arguments, how do you pass these items into the fuction?

```
def triangle_sides(a, b, c):
    return(sum(a, b, c))

triangle1 = [2, 2, 3]
triangle2 = [3, 4, 5]

```
since the fucntion is set up to take 3 arguments, it won't accept a single argument. python won't go look inside the list to get the three variables.
you could rewrite the function so that it accepts a library with 3 arguments though (?)

* Functions and Docstings:

See: [PEP ](https://www.python.org/dev/peps/pep-0257/)

### modules & function notes for refactoring:

at end of week two of my sabbatical, I see there's lots of code getting reused, I see I'm writing two scripts each of which have to open a folder and iterate over contents with a function. I likely can and should extract those sorts of functions to a module as part of later refactoring. Can and should generalize the handling of the /data directories and writing files to / from them across the whole pipeline of processing the various files etc. Again a good thing to do when refactoring the code itself. 

in Sabbatical repo, most of the anystyle_helper.py file is recapitulating a slighly more complex set of processes in a previously-written script, so that 2nd one could have been much shorter, overall and reduce much of the complexity and redundancy of the second script. Would be good to make it signifigantly smaller. Worth thinking more about how to refactor and better document the code I'm writing so I am learning and adopting best practices around style and documentation as I go.

### data structures:

* [Real Python: Data Structures](https://realpython.com/python-data-structures/)

## Other software:

* Currently using Visual Studio Code as my IDE
* using git and github for version control, though being a single developer working on one project I'm not using many of it's features.

see realpyon overview of git [here](https://realpython.com/python-git-github-intro/) as well as the canonical, comprehensive reference & introduction to git [here](https://git-scm.com/book/en/v2)

Thinking about how often or when to commit code to a repository. This matters less a a solo developer but this stack overflow question is a good one:

[How often to commit changes to source control?](https://stackoverflow.com/questions/107264/how-often-to-commit-changes-to-source-control)

along with [this](https://blog.codinghorror.com/check-in-early-check-in-often/) article that articulates some more of the ideas underlying the answers above.

>  "You commit when you have reached a codebase state you want to remember."

and

> "I like to think of coding as rock climbing in this context. You climb a bit, and then you put an anchor in the rock. Should you ever fall, the last anchor you planted is the point that secures you, so you'll never fall more than a few meters. Same with source control; you code a bit, and when you reach a somewhat stable position, you commit a revision. "

Quotes above from this other SO question here[here](https://softwareengineering.stackexchange.com/questions/83837/when-to-commit-code)

### Citation Sabbatical Project specific software:

The project includes, at this stage the following dependencies:

* [anystyle](https://github.com/inukshuk/anystyle)
* [anysytle-cli](https://github.com/inukshuk/anystyle-cli)
* [pdftotext](https://www.xpdfreader.com/pdftotext-man.html) utility which is part of larger opensource xpdfreader project [here](https://www.xpdfreader.com/index.html)

The sabbatical project is in the first two phases is a series of processing scripts on top of these other utilities to manage files through a pipline from richtext in pdf and docx format to BibTex files. These two peices of software both seem to work very well and the project would not be possible at this scale without them.