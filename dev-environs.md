---
permalink: dev-environs
---

# Development Environments & Dependencies
Managing dependencies, python versions and the machine you're developing on which may differ vs. the machine code is deployed to. Important when considering need to maintain code.

## Reading:
 * VS Code documentation: [general python tutorial] (https://code.visualstudio.com/docs/python/python-tutorial) and [python environments docs] (https://code.visualstudio.com/docs/python/environments )

https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/#creating-a-virtual-environment


### Dependency Management Tools & Practices:

* pip manages installation and dependencies for installing and upgrading packages in python.

[pip docs] (https://pip.pypa.io/en/stable/)

virtual environments:
[venv docs] (https://docs.python-guide.org/dev/virtualenvs/)

Appears there are two main competitors:

https://pipenv.pypa.io/en/latest/
https://python-poetry.org/

Look into pip files and requirements.txt, those are parts of managing a given environment.

### python version features and support:

* [python.org: status of python branches] (https://devguide.python.org/#status-of-python-branches)

No one uses python 2, all versions of python 2 have reached end-of-life and are unsupported.

Supported versiosn of python are currently:
    * 3.6 onward
    * 3.8 

Most recent is: 3.8.5 released July 20, 2020.

As of Aug 12, currently working in conda version 3.6.1, should upgrade to 3.8.x ASAP.