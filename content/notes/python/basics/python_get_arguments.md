---
title: "Python Get Arguments"
date: 2022-10-19T11:04:21+01:00
draft: false
---

## Get the arguments from the comand line

```Python
from sys import argv

thefile, first_arg, second_arg, third_arg = argv

print ("The file is called:", thefile)
print ("Your first arg is:", first_arg)
print ("Your second arg is:", second_arg)
print ("Your third arg is:", third_arg)

```