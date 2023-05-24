# BLAS-for-apple
tested 3 different flavours of numpy compiled for m1 processer with openblas, accelerate and netlib. Vanilla numpy available on conda-forge is compiled for openblal, it is a safe choice. Apple's accelerate is blazing fast, but numerically unstable, at least until macos 13.3

**apple’s accelerate ```blas=*=accelerate```**

* svd 1.03 sec
* matmuls 20 sec
* ```numpy.test()``` 3 failed, 25083 passed, 393 skipped, 1309 deselected, 44 xfailed, 5 xpassed, 25 warnings in 76.34s (0:01:16)
* ```scipy.test()``` fails at linalg/tests/test_cython_blas.py test, at 20% 

**conda-forge vanilla**

* svd 13.53 sec
* matmuls 44 sec
* ```numpy.test()``` none failed, 25075 passed, 404 skipped, 1309 deselected, 44 xfailed, 5 xpassed, 32 warnings in 69.25s (0:01:09)
* ```scipy.test()``` 7 failed, 37984 passed, 2301 skipped, 12295 deselected, 139 xfailed, 9 xpassed, 72 warnings in 355.99s (0:05:55)

**netlib ```=*=netlib```**

* svd 4.44 sec
* matmuls 330 sec
* numpy 12 failed, 25063 passed, 404 skipped, 1309 deselected, 44 xfailed, 5 xpassed, 24 warnings in 73.60s (0:01:13)
* scipy 153 failed, 37839 passed, 2301 skipped, 12295 deselected, 139 xfailed, 8 xpassed, 86 warnings in 347.62s (0:05:47)

**openblas ```=*=openblas```**

* svd  12.44 sec
* matmuls 45 sec
* ```numpy.test()``` none failed 25075 passed, 404 skipped, 1309 deselected, 44 xfailed, 5 xpassed, 32 warnings in 69.98s (0:01:09)
* ```scipy.test()``` 7 failed, 37984 passed, 2301 skipped, 12295 deselected, 139 xfailed, 9 xpassed, 72 warnings in 356.14s (0:05:56)

## test conditions
Apple M1 Pro 10 cores running Ventura 13.3.1, python 3.10.11, conda 23.3.1, numpy 1.24.3, scipy 1.10.1, libblas 3.9.0, openblas 0.3.21. For Netlib blas was version 2.104, for accelerate, openblas and vanilla it was 2.116.
