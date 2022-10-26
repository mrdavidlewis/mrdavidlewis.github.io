---
title: "Python_pc_setup_IV"
date: 2022-10-19T11:05:39+01:00
draft: false
---


## Install the Python binary you want to work with

In my case Python 2 is installed here:
```powershell
c:\Python27\
```

Check virtual env is installed
```powershell
c:\Python27\python -m pip install virtualenv
```


Create a virtual environvent
```powershell
c:\Python27\python -m virtualenv d:\fast\mypy\genpy27
```


Activate the environment
```powershell
D:\fast\mypy\genpy27\Scripts\activate.ps1
```

## Check pip is up-to-date

```powershell
pip install --upgrade pip
```

## Install numpy from wheel including mkl &mdash; to match the Python version
Download relevant wheel:

```powershell
set-location C:\Users\David Lewis\Downloads
```

```powershell
pip install numpy-1.14.0+mkl-cp27-cp27m-win_amd64.whl
```

## Install scipy from wheel &mdash; to match the Python version:

```powershell
pip install scipy-1.0.0-cp27-cp27m-win_amd64.whl
```

## Install jupyter
```shell
pip install jupyter
```

## Install pandas and it's dependencies

```shell
pip install pandas
```

## Install matplotlib:

```shell
pip install matplotlib
```

## Install nose:
```shell
pip install nose
```

## Install pytest
```shell
pip install -U pytest
```

```shell
pytest --version
```
