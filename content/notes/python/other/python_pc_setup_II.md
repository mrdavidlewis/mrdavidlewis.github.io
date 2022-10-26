---
title: "Python_pc_setup_II"
date: 2022-10-19T11:05:22+01:00
draft: false
---

## Install the Python binary
Install the Python binary you want to work with if not already installed.
So for example the last binary I needed to install was the latest Python 3 for windows.
The version was:
`Python 3.6.0 (v3.6.0:41df79263a11, Dec 23 2016, 07:18:10)`.

The default installation location of Python is in the users folder. So it was installed in `%USERPROFILE%\AppData\Local\Programs\Python\Python36-32`

See <https://docs.python.org/3/using/windows.html> for details.

## Install a Python virtual environment using venv
The venv docs are here:
<https://docs.python.org/3/library/venv.html>

Example:
```code
c:\Users\dlewis\AppData\Local\Programs\Python\Python36-32\python -m venv C:\David\Jup
```
Tip: if you user name has a space in you are going to need to use the & and bracket. e.g.
```
& (path with a space in)
```
## Start the virtual environment
You might need to change the ExecutionPolicy in PowerShell to allow the scripts to run:
```code
Set-ExecutionPolicy RemoteSigned
```

## Activate virtual environment
```code
C:\David\Jup\Scripts\Activate.ps1
```
##  Install Jupyter Notebooks

<http://jupyter.readthedocs.io/en/latest/install.html>

Check pip is up-to-date
```
pip3 install --upgrade pip
```

### Install Jupyter
```
pip3 install jupyter
```
### Install pandas and it's dependencies

```
pip3 install pandas
```

### Install matplotlib:

```
pip3 install matplotlib
```

### To install scipy:

- Download relevant wheel
- <http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy>
- Put wheel in a folder

Then install wheel with pip3:
```
pip3 scipy-0.19.0-cp36-cp36m-win32.whl
```

### Reinstall numpy because it is missing mkl:

Download relevant wheel:
- <http://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy>

```
pip3 uninstall numpy
```

```
pip3 install numpy-1.12.1+mkl-cp36-cp36m-win32.whl
```
### Install nose so you can test installation

```
pip3 install nose
```


## Test installation
Start Python in shell.
```
import scipy
scipy.test('full')
```
```output
======================================================================
FAIL: test_decomp_update.TestQRdelete_F.test_delete_last_p_col
----------------------------------------------------------------------
Traceback (most recent call last):
  File "C:\David\Jup\lib\site-packages\nose\case.py", line 198, in runTest
    self.test(*self.arg)
  File "C:\David\Jup\lib\site-packages\scipy\linalg\tests\test_decomp_update.py"
, line 328, in test_delete_last_p_col
    assert_unitary(q1)
  File "C:\David\Jup\lib\site-packages\scipy\linalg\tests\test_decomp_update.py"
, line 21, in assert_unitary
    assert_allclose(aTa, np.eye(a.shape[1]), rtol=rtol, atol=atol)
  File "C:\David\Jup\lib\site-packages\numpy\testing\utils.py", line 1411, in as
sert_allclose
    verbose=verbose, header=header, equal_nan=equal_nan)
  File "C:\David\Jup\lib\site-packages\numpy\testing\utils.py", line 796, in ass
ert_array_compare
    raise AssertionError(msg)
AssertionError:
Not equal to tolerance rtol=0.0001, atol=2.38419e-07

(mismatch 1.3888888888888857%)
 x: array([[  1.000000e+00 +0.000000e+00j,  -4.097819e-08 +2.980232e-08j,
         -2.607703e-08 -1.490116e-08j,   5.587935e-09 -1.490116e-08j,
         -2.235174e-08 -1.862645e-08j,  -2.793968e-09 +2.887100e-08j,...
 y: array([[ 1.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.],
       [ 0.,  1.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.],
       [ 0.,  0.,  1.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.],...

```

```output
======================================================================
FAIL: test_orthogonal.test_roots_gegenbauer
----------------------------------------------------------------------
Traceback (most recent call last):
  File "C:\David\Jup\lib\site-packages\nose\case.py", line 198, in runTest
    self.test(*self.arg)
  File "C:\David\Jup\lib\site-packages\scipy\special\tests\test_orthogonal.py",
line 504, in test_roots_gegenbauer
    vgq(rootf(0.1), evalf(0.1), weightf(0.1), -1., 1., 25, atol=1e-13)
  File "C:\David\Jup\lib\site-packages\scipy\special\tests\test_orthogonal.py",
line 287, in verify_gauss_quad
    assert_allclose(vv, np.eye(N), rtol, atol)
  File "C:\David\Jup\lib\site-packages\numpy\testing\utils.py", line 1411, in as
sert_allclose
    verbose=verbose, header=header, equal_nan=equal_nan)
  File "C:\David\Jup\lib\site-packages\numpy\testing\utils.py", line 796, in ass
ert_array_compare
    raise AssertionError(msg)
AssertionError:
Not equal to tolerance rtol=1e-15, atol=1e-13

(mismatch 5.760000000000005%)
 x: array([[  1.000000e+00,  -1.854755e-17,   7.310015e-14,  -7.627779e-17,
          7.238787e-14,   2.754201e-17,   7.247653e-14,   1.854543e-17,
          6.807551e-14,   1.468432e-16,   6.300386e-14,   3.789022e-16,...
 y: array([[ 1.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,
         0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.],
       [ 0.,  1.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,...

----------------------------------------------------------------------
```

```output
----------------------------------------------------------
Ran 25578 tests in 610.564s

FAILED (KNOWNFAIL=129, SKIP=2117, failures=2)
<nose.result.TextTestResult run=25578 errors=0 failures=2>
----------------------------------------------------------
```

```code
import numpy
numpy.test('full')
```

```output
======================================================================
FAIL: test_default (test_numeric.TestSeterr)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "C:\David\Jup\lib\site-packages\numpy\core\tests\test_numeric.py", line 4
32, in test_default
    under='ignore',
AssertionError: {'divide': 'warn', 'over': 'raise', 'under': 'ignore', 'invalid'
: 'warn'} != {'divide': 'warn', 'invalid': 'warn', 'over': 'warn', 'under': 'ign
ore'}
- {'divide': 'warn', 'invalid': 'warn', 'over': 'raise', 'under': 'ignore'}
?                                                 ^^^^

+ {'divide': 'warn', 'invalid': 'warn', 'over': 'warn', 'under': 'ignore'}
?                                                ++ ^


======================================================================
```

```output
======================================================================
FAIL: test_io.test_load_refcount
----------------------------------------------------------------------
Traceback (most recent call last):
  File "C:\David\Jup\lib\site-packages\nose\case.py", line 198, in runTest
    self.test(*self.arg)
  File "C:\David\Jup\lib\site-packages\numpy\lib\tests\test_io.py", line 2014, i
n test_load_refcount
    assert_(gc.isenabled())
  File "C:\David\Jup\lib\site-packages\numpy\testing\utils.py", line 110, in ass
ert_
    raise AssertionError(smsg)
AssertionError

----------------------------------------------------------------------
```

```output
======================================================================
FAIL: test_io.test_load_refcount
----------------------------------------------------------------------
Traceback (most recent call last):
  File "C:\David\Jup\lib\site-packages\nose\case.py", line 198, in runTest
    self.test(*self.arg)
  File "C:\David\Jup\lib\site-packages\numpy\lib\tests\test_io.py", line 2014, i
n test_load_refcount
    assert_(gc.isenabled())
  File "C:\David\Jup\lib\site-packages\numpy\testing\utils.py", line 110, in ass
ert_
    raise AssertionError(smsg)
AssertionError

----------------------------------------------------------------------
```

## Start Jupyter Notebook

You might need to map a drive first:
```
net use z: \\servername\users\username
```
Activate virtual environment:
```code
C:\David\Jup\Scripts\Activate.ps1
```
Finally start the notebook.
```
jupyter notebook
```
To stop the server `ctrl-C`

To return ExecutionPolicy to the default safe level.
```
Set-ExecutionPolicy Restricted
```

