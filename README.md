# Cuvis python interface layer (required for using the python wrapper)

This repository contains the python bindings for the Cuvis SDK. 

## Installation

For an easy installtion we provide binaries for Python 3.9, 3.10 and 3.11. These can be installed via

```
pip install cuvis-il
```

## Building
For building the python interface layer *cuvis_pyil*, first clone this git repository and initialize it's submodules recursively

```
git submodule update --init --recursive
```

Next, you need to install the Cuvis C SDK (see https://cloud.cubert-gmbh.de/index.php/s/kKVtx0x2fmYqVgx).

For building the python stubs for wrapping between C libraries and python, you'll need SWIG (see https://www.swig.org/download.html).

Next make sure that your preferred version of numpy is installed. See [here](#dependency-to-numpy)

Then use CMake (see https://cmake.org/download/) to configure and generate your project. CMake will require you to locate the Cuvis C SDK (this should be found automatically, if the Cuvis C SDK is properly installed. Also, you need to point the variable *SWIG_EXECUTABLE* to the path of the *swig.exe*
This project will then generate the `_cuvis_pyil.pyd` and `cuvis_il.py` files needed for running the Cuvis Python SDK wrapper.

## Dependency to numpy
The python interface layer is dependent on numpy. Specifically, this means that we need the c headers of the numpy library.
Notice that NumPy has [backwards compatibility](https://numpy.org/doc/stable/dev/depending_on_numpy.html).
To compile the python interface layer install your preferred version of numpy. For example
```
pip install numpy
```
CMake will try to find the numpy path using the `find_package(Python REQUIRED COMPONENTS Interpreter Development NumPy)`.
To support the usage of a virtual environment, simply set the `Python_ROOT_DIR` variable to the directory containing your virtual environment.