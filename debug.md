---
title: Debugging
permalink: debug
---

# Debugging:

## Print:

Like most other beginning developers, I use print statements often to help me to debug code as I'm writing it, though I should learn more about VS-Code's debugging and linting tools so I can get a good sense of how those work and speed up debugging. It is better, ultimatly to use tests where you can, instead of just print statements to debug code, especially as it gets more complex.

watching my code loop this morning and print out a long series of values I wondered about how much these statements slow down the actual execution of the code and found [this](https://stackoverflow.com/questions/13288185/performance-effect-of-using-print-statements-in-python-script) stack overflow answer.

It's also useful to use [pretty formatting](https://docs.python.org/3/tutorial/inputoutput.html#fancier-output-formatting) when using print statements to debug or output values to the terminal.

The link above to current (3.9) python practice, reccomends the newest, most compact syntax for string formatting using 'f-strings'.

    name = 'andy'
    print (f'Hello,{name}')

The distinction between the various available string formatting methods wasn't clear to me, so I think early code may not use one method consisently. 

[This] chart is useful in determining how best to choose one string formatting technique over another. 

* [Real Python -- String Modulo Operator](https://realpython.com/python-input-output/#the-string-modulo-operator) -- the oldest, most backward compatible method
* [Real Python -- A Guide to the Newer Python String Format Techniques](https://realpython.com/python-formatted-output/#the-python-string-format-method) -- where newer means python 3.0+

## VS Code's Debugger

I've encounted some issues with VS Code having permissions to run scripts to either run the debugger or activate a virtual enrvironment. 

There are stack overflow questions which address these issues [here]() and [here](), respectivly. 

## Test driven development

## Benchmarking execution time

The python standard library has [timeit]() which allows for small parts of code to be timed.

As an example, I wanted to try two different ways of finding duplicate lines in text files.

The naieve approach would be to loop through each line of the file and compare it to each line in the file. This is of course a fairly slow operation.

