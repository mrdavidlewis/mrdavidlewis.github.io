---
title: "Python PC Setup III"
date: 2022-10-19T11:05:30+01:00
draft: false
---

## Install the Python binary
Install the Python binary you want to work with if not already installed.

The default installation location of Python 3 is in the users folder.

So it will be installed somewhere like this:

```powershell
%USERPROFILE%\AppData\Local\Programs\Python\Python36-32
```

See <https://docs.python.org/3/using/windows.html> for details.

Example:
```powershell
c:\Users\dlewis\AppData\Local\Programs\Python\Python36-32\python -m venv C:\David\Jup
```
Tip: if you user name has a space in you are going to need to use the & and bracket. e.g.

```powershell
& (path with a space in)
&("C:\Users\David Lewis\AppData\Local\Programs\Python\Python36-32\python") -m venv d:\fast\mypy\ds
```
## Start the virtual environment
You might need to change the ExecutionPolicy in PowerShell to allow the scripts to run:
```powershell
Set-ExecutionPolicy RemoteSigned
```
## Activate virtual environment
```powershell
C:\David\Jup\Scripts\Activate.ps1
D:\fast\mypy\ds\Scripts\activate.ps1

```

## Check pip is up-to-date
```powershell
pip3 install --upgrade pip
```
## Install numpy from wheel

http://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy

- Download the wheel &mdash; to match the Python version

```powershell
set-location "C:\Users\David Lewis\Downloads"
pip3 install numpy-1.13.1+mkl-cp36-cp36m-win32.whl
```
## Install scipy from wheel:

- Download the wheel &mdash; to match the Python version

http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy


Then install wheel with pip3:
```powershell
pip3 install scipy-0.19.1-cp36-cp36m-win32.whl
```

## Install Jupyter Notebooks

```shell
pip3 install jupyter
```

## Install pandas and it's dependencies

```shell
pip3 install pandas
```

## Install matplotlib:

```shell
pip3 install matplotlib
```

## Install nose

```shell
pip3 install nose
```

## Test installation

- Start Python in shell.

```shell
import scipy
scipy.test('full')
```


```shell
import numpy
numpy.test('full')
```

You can then contemplate whether the log output is significant.
