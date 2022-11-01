---
title: "Python in SQL"
date: 2022-10-19T11:05:53+01:00
draft: false
---


## This script mines timings from a log file
It finds the text 'iteration' every thousand records and extracts the time

```Python
from sys import argv
from os.path import exists
import re
import time

script, log_file = argv

timestr = time.strftime("%Y%m%d%H%M%S")

print log_file
count_file = open('scrape_log_%s_%s.txt' % (log_file, timestr), 'w') 


if exists(log_file):
    f = open(log_file)
    txt = f.read()
    f.close()

    pattern_1 = re.compile(r"Iteration : (1).+?(\d\d-...-\d\d\d\d \d\d:\d\d:\d\d?)", re.DOTALL)
    mo_01 = pattern_1.search(txt)
    if mo_01 != None:
        print mo_01.group(1), '\t', mo_01.group(2)
        count_file.write(mo_01.group(1) + '\t' +  mo_01.group(2) + '\n')

    for i in range(1, 20):
        pattern_1 = re.compile(r"Iteration : (%i\d\d\d).+?(\d\d-...-\d\d\d\d \d\d:\d\d:\d\d)" % i, re.DOTALL)  
        mo_01 = pattern_1.search(txt)
        if mo_01 != None:
            print mo_01.group(1), '\t', mo_01.group(2)
            count_file.write(mo_01.group(1) + '\t' +  mo_01.group(2) + '\n')

count_file.close()

```
