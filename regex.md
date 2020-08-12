---
permalink: regex
---

# Regular Expressions

## General regex docs:
* [python library: regex](https://docs.python.org/3/library/re.html)
* [python howto: regex](https://docs.python.org/3/howto/regex.html#regular-expression-howto)
* [realpython.com: Regular Expressions in python](https://realpython.com/regex-python/)
Good to have two different explanations complex topics.

re.compile:

module methods 
>    Should you use these module-level functions, or should you get the pattern and call its methods yourself? If you’re accessing a regex within a loop, pre-compiling it will save a few function calls. 

so, you can do:
```
r = re.compile('[0-9]+)
r.match('sting to mactch against')
```
or call the module-level function:
```
re.match('pattern', 'pattern to match against')
```


re.search() vs. re.match():

## re.search
* [python docs](https://docs.python.org/3/howto/regex.html#search-and-replace)

this takes 