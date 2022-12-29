C code (example.c):

```
#include <stdio.h>

int add(int a, int b) {
  return a + b;
}
```
SWIG interface file (example.i):
```
%module example

int add(int a, int b);
```
To generate the Python wrapper code, you can run the following command:

```
swig -python example.i
```
This will generate the file example_wrap.c, which contains the wrapper code. You can then compile the C code and the wrapper code into a shared library using a command like this:

```
gcc -fPIC -c example.c example_wrap.c -I/usr/include/python3.7
gcc -shared example.o example_wrap.o -o _example.so
```
This will create a shared library file _example.so that you can import into Python. You can then call the add function from Python like this:

```
import example

result = example.add(1, 2)
print(result)  # prints 3
```
