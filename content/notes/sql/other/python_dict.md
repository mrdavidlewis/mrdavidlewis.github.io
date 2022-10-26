---
title: "Python_dict"
date: 2022-10-19T11:04:09+01:00
draft: false
---

General advice: there is more than one way to do everything. Pick one style.
```python
# For examples I use this list
l = ['one', 'two', 'three', 'four', 'four', 'four', 'one']
```

# The basics

Make a new empty dictionary:
```python
d = dict()
d = {}
```

Add item to a dictionary:
```python
d['a'] = 1
```

Get a value using a key:
```python
myval = d['a']
```

Traverse keys:
```python
for key in d:
    print(key)
```

Traverse keys and values:
```python
for key, value in d.items():
    print('key=', key, ' | ', 'value=', value)
```

The example above is the normal convention but you can traverse the keys and values like this too:
```python
for a in d:
    print ('key=', a, ' | ', 'value=', d[a])
```

# A dictionary counter


Build a dictionary counter (a histogram)
```python
def histogram(c):
    d = {}
    for i in c:
        if not i in d:
            d[i] = 1
        else:
            d[i] += 1
    return d
```
Build a dictionary counter (a histogram) using the default value for ```get```
```python
# From documentation:
# get(key[, default])
# Return the value for key if key is in the dictionary, else default.
# If default is not given, it defaults to None, so that this method
# never raises a KeyError.
#
def histogram1(c):
    d = {}
    for i in c:
         d[i] = d.get(i, 0) + 1
    return d

```

Build a dicionary counter using ```setdefault```.
```python

# From documentation
# setdefault(key[, default])
# If key is in the dictionary, return its value. If not, insert key with
# a value  of default and return default. default defaults to None.

# This works as well but I can't believe it is very efficient?
# Let's step through it:
# l = [
#     'one', one does not exist as a key so it is created.
#            And the default value is returned 0 and 1 is added to that.
#            Finally the key is set again and has the value 1 assigned

#     'two',
#      'three', 'four', 'four', 'four',
#     'one'] 'one' does exist as a key so 1 is returned and 1 is added to is -
#            making two. The key one is reassigned the value 2.

def histogram2(c):
# DO NOT USE  
    d = {}
    for i in c:
         d[i] = d.setdefault(i, 0) + 1
    return d
```

A dictionary with list values

The following examples all build a dictionary like this from the list above - which is repeated here for convenience.

```
l = ['one', 'two', 'three', 'four', 'four', 'four', 'one']

key= one  |  value= ['one', 'one']
key= two  |  value= ['two']
key= three  |  value= ['three']
key= four  |  value= ['four', 'four', 'four']
```

This uses if and else. It's really easy to read.

```python
d2 = {}
for i in l:
    if i not in d2:
        d2[i] = [i]
    else:
        d2[i].append(i)

for key, value in d2.items():
    print('key=', key, ' | ', 'value=', value)

```

This example is just an elaboration of above:

```python
d4 = {}
for i in l:
    if i not in d4:
        d4[i] = [i]
    else:
        # This will get you the list
        print(type(d4[i]))
        print(type(d4[i].append(i)))
        print(type(d4[i]))
        # but you can't do this!!!!
        # d4[i] = d4[i].append(i)
        # because append is not returning the list
        # it is adding to the list and returning none
        for key, value in d4.items():
            print('key=', key, ' | ', 'value=', value)

```

This uses ```get``` but is not adding much to the party as there is still an if-else.

```python
d5 = {}
for i in l:
    if i not in d5:
        d5[i] = [i]
    else:
        d5.get(i).append(i)

for key, value in d5.items():
    print('key=', key, ' | ', 'value=', value)
```


This will set the dictionary up with each key but append returns None and
so all the dictionary values are none.

You can't use ```get``` in one line like this because the append does not return the reference to value which is a list.

```python
# DO NOT USE THIS
d5a = {}
for i in l:
    try:
        d5a[i] = d5a.get(i,[]).append(i)
        print('Here')
    except:
        print('Here 2')

for key, value in d5a.items():
    print('key=', key, ' | ', 'value=', value)
```

This example is also one I would consider using but is less easy to read for a beginner than the if-else construction..

```python
d6 = {}
    for i in l:
        d6.setdefault(i,[]).append(i)    

    for key, value in d5.items():
        print('key=', key, ' | ', 'value=', value)
```


# Invert a dictionary:

```python
def invert_dict(d):
    inverse = {}
    for key in d:
        val = d[key]
        inverse.setdefault(val, []).append(key)
    return inverse
```
Here, we use the method ```setdefault```.

The method ```setdefault``` will return the value if the key exists. Here the returned value will be a list. If the key is not found, a new entry is made with that key and the default value we have set - here, an empty list. Either way, the original key is appended to the list.

Invert a dictionary without using  ```setdefault``` .

```python
def invert_dict1(d):
    inverse = dict()
    for key in d:
        val = d[key]
        if val not in inverse:
            inverse[val] = [key]
        else:
            inverse[val].append(key)
    return inverse
```

# Check a list for duplicates:
(Tip use a set not this technique.)
```python
def has_duplicates(l):
    ''' Check for duplicates in a list using a dictionary
    '''
    d = dict()
    for i in l:
        if i in d:
            return True
        d[i] = 0
    return False
```
