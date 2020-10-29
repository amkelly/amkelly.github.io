---
title: Related Software
permalink:
---

# Related software

This page is to write about software that isn't directly related to python.

There's a seperate page on Databases & SQL [here](./sql) and another for [Microsoft PowerBI](./powerbi.md)


## IDEs, text editors

* Currently using Visual Studio Code as my IDE, not set up well for debugging or automated tests as of Sept 2020.

## git & github
* using git for version control and github for a remote repo, though being a single developer working on one project I'm not using many of it's features.

see realpyon overview of git [here](https://realpython.com/python-git-github-intro/) as well as the canonical, comprehensive reference & introduction to git [here](https://git-scm.com/book/en/v2)

Thinking about how often or when to commit code to a repository. This matters less a a solo developer but this stack overflow question is a good one:

[How often to commit changes to source control?](https://stackoverflow.com/questions/107264/how-often-to-commit-changes-to-source-control)

along with [this](https://blog.codinghorror.com/check-in-early-check-in-often/) article that articulates some more of the ideas underlying the answers above.

>  "You commit when you have reached a codebase state you want to remember."

and

> "I like to think of coding as rock climbing in this context. You climb a bit, and then you put an anchor in the rock. Should you ever fall, the last anchor you planted is the point that secures you, so you'll never fall more than a few meters. Same with source control; you code a bit, and when you reach a somewhat stable position, you commit a revision. "

Quotes above from this other SO question here[here](https://softwareengineering.stackexchange.com/questions/83837/when-to-commit-code)

## Citation Sabbatical Project specific software:

The project includes, at this stage the following dependencies:

* [anystyle](https://github.com/inukshuk/anystyle)
* [anysytle-cli](https://github.com/inukshuk/anystyle-cli)
* [pdftotext](https://www.xpdfreader.com/pdftotext-man.html) utility which is part of larger opensource xpdfreader project [here](https://www.xpdfreader.com/index.html)

The sabbatical project is in the first two phases is a series of processing scripts on top of these other utilities to manage files through a pipline from richtext in pdf and docx format to BibTex files. These two peices of software both seem to work very well and the project would not be possible at this scale without them.

