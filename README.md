CFFI - mem dlopen
====

Based on [CFFI](https://github.com/cffi/cffi)

Foreign Function Interface for Python calling C code.
Please see the [Documentation](http://cffi.readthedocs.org/) or uncompiled
in the doc/ subdirectory.

# Features

This code has been modified to allow for accessing functions from dlls which have been loaded via MemoryModule

# How to use

Simply compile the code with setup.py and take the resulting _cffi_backend binary and replace the corresponding file in the normal cffi package

# Misc

This was achieved by adding MemoryModule to the project and then converting the dlsym function in misc_win32.c to wrap MemoryModule's MemoryGetProcAddress function. This allows you to use cffi.dlopen with a memory-resident dll. 

I have created this to be used with my [od_importer](https://github.com/rkbennett/od_importer) repo. This also requires my [py3memimporter](https://github.com/rkbennett/py3memimporter) repo which leverages a modified _memimporter binary that adds a dlopen function that does the memory mapping of a dll.
