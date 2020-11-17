---
title: Lists
permalink: lists

---
# Lists

## Operations on lists of lists:

The following code sample from [this page](https://thispointer.com/python-get-number-of-elements-in-a-list-lists-of-lists-or-nested-list/):
    # List of lists
    listOfElems2D = [ [1,2,3,45,6,7],
                        [22,33,44,55],
                        [11,13,14,15] ]
    # Iterate over the list and add the size of all internal lists 
    count = 0
    for listElem in listOfElems2D:
        count += len(listElem)                    
    print('Total Number of elements : ', count)


This helped point me toward my own code where i wanted to could the longest list in a list of lists in database_load.py


        max = 0
        for e in authors_column:
            if len(e) > 13:
                print(e)
            if max <= len(e): max = len(e)
        print(max)


Which additionally, prints particularly long entries, so I can see if there are problems with the underlying data.    


and then I decided to pad the lists so all the lists would be the same length, this is useful often with bad data in pandas:


    #pad lists so they're all the same length.
    for f in reworked_column:
        while len(f) < max:
            f.append(None)
    '''

## Lists & Sets

Sets are a data type similar in some ways to lists and they appear to often be used in similar ways.

This Stackoverflow question: [Removing Duplicates in lists](https://stackoverflow.com/questions/7961363/removing-duplicates-in-the-lists) serves as an introduction to one use for sets & lists.

Python documentation for sets [here](

## Linked Lists

https://realpython.com/courses/working-linked-lists-python/

# Generators

This is a topic I saw mentioned a lot before I really understood how applicable it was in practice.