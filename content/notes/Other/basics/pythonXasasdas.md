---
title: "Python a slightly longer title"
date: 2022-10-19T11:03:04+01:00
draft: false
---
```Python
# This is to count the number of lines of text files
# in a named folder.
# The following extension qualify a file to be counted:
# tab, txt, csv, py

import os

def file_len(fname):
    i=-1
    with open(fname) as f:
        for i, l in enumerate(f):
            pass
    return i + 1

allowed = ['.tab', '.txt', '.csv', '.py']

#    this is where you name the folder you want to search
folderName = 'Z:\\Documents\\Python'
os.chdir(folderName)


for filename in os.listdir(folderName):    
    filenameOnly, ext = os.path.splitext(filename)
    if ext in allowed: 
        print filename + ' | ' + str(file_len(filename))
        

# report finished    
# count the number newlines with quotes;

```
