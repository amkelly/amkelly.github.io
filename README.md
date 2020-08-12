# amkelly.github.io
## Python & programming notes

A repository for organizing and publishing notes as I work to learn and understand python and computer science in both professional and personal projects. Writing about something as I'm learning it helps me understand it better.

I bought a recent humble bundle of python training resources here and have been working my way through How to Think like a computer science.

Working on some python exercises occasionally too on codewars.io, pythonmorsels and 

## Notes Pages:

* [File I/O](./fileio)
* [Looping (draft)](./looping)
* [Regular Experssions](./regex) 
* [Libraries](./libraries)


## Unsorted notes & questions:

If you have a function with several arguments, it might make sense to have a list where each item is one of those arguments, how do you pass these items into the fuction?

```
def triangle_sides(a, b, c):
    return(sum(a, b, c))

triangle1 = [2, 2, 3]
triangle2 = [3, 4, 5]

```
since the fucntion is set up to take 3 arguments, it won't accept a single argument. python won't go look inside the list to get the three variables.
you could rewrite the function so that it accepts a library with 3 arguments though (?)