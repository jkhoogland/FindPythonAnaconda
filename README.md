# Handle Anaconda Python in CMake scripts.

The current FindPythonLibs does not handle use of Anaconda Python.

This is some basic code to figure out which version of the Anaconda
Python libs/executables to use.

Adding the following line to your CMakeLists.txt should do the trick.

``` cmake
  # ensure the script is in your cmake module path
  include(FindPythonAnaconda)
```

After running this you should see something along the form of

``` shell
  Found anaconda root directory /Users/Jiri/anaconda
  Using anaconda root environment
  PYTHON_INCLUDE_DIR = /Users/Jiri/anaconda/include/python3.4m
  PYTHON_LIBRARY = /Users/Jiri/anaconda/lib/libpython3.4m.dylib
```

If you switch to a different anaconda env, it should be automatically
picked up, e.g.

``` shell
  $ source activate py27
  discarding /Users/Jiri/anaconda/bin from PATH
  prepending /Users/Jiri/anaconda/envs/py27/bin to PATH
```

When rerunning the cmake script, the new environment is picked up

``` shell
  Found anaconda root directory /Users/Jiri/anaconda
  Using anaconda root environment
  PYTHON_INCLUDE_DIR = /Users/Jiri/anaconda/include/python2.7
  PYTHON_LIBRARY = /Users/Jiri/anaconda/lib/libpython2.7.dylib
```

