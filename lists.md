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