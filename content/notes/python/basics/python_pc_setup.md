---
title: "Python PC Setup"
date: 2022-10-19T11:05:10+01:00
draft: false
---



## Install the Python binary you want to work with

So for example the last binary I needed to install was the latest Python 3 for windows.
The version was:

```shell
Python 3.6.0 (v3.6.0:41df79263a11, Dec 23 2016, 07:18:10)
```

The default ```installation``` location of Python is in the users folder. So it goes 

```powershell
%USERPROFILE%\AppData\Local\Programs\Python\Python36-32
```

See https://docs.python.org/3/using/windows.html for details.


## Set up a virtual environment
Use venv:

```powershell
c:\Python35\python -m venv c:\path\to\myenv
```

If you have spaces and are working is PS:

```powershell
&("C:\Users\Your Name\AppData\Local\Programs\Python\Python36-32\python") -m venv d:\fast\mypy\genpy
```


```powershell
c:\Python35\python -m venv c:\path\to\myenv
c:\Python35\python -m venv c:\path\to\myenv
```


## Start the virtual environment
```powershell
D:\fast\mypy\genpy\Scripts\activate.ps1
D:\fast\mypy\dcldoc\Scripts\activate.ps1
set-location D:\fast\mypy\dcldoc\webdev\output
```


## Pelican quickstart
### Start Server
Navigate to the folder you want to server
```powershell
set-location D:\fast\mypy\dcldoc\webdev\output
python -m pelican.server
```
Navigate to ```http://localhost:8000/```

### Publish content
```powershell
set-location D:\fast\mypy\dcldoc\webdev
pelicon content
pelican content -s publishconf.py
```
