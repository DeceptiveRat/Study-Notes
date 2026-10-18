- 64-bit windows exe

```sh
x86_64-w64-mingw32-gcc program.c -o program.exe
```

- 32-bit windows exe
 
```sh
i686-w64-mingw32-gcc program.c -o program.exe
```

- 64-bit windows dll

```sh
x86_64-w64-mingw32-gcc -shared -o mydll.dll mydll.c -Wl,--out-implib,libmydll.a
x86_64-w64-mingw32-gcc -shared -o mydll.dll mydll.c -W # works, too..?
```

- using dll to link

```sh
x86_64-w64-mingw32-gcc main.c -o main.exe -L. -lmydll
```

- 64-bit windows C++ exe

```sh
x86_64-w64-mingw32-g++ program.cpp -o program.exe
```

- 32-bit windows C++ exe

```cpp
i686-w64-mingw32-g++ program.cpp -o program.exe
```

- 64-bit windows C++ object

```cpp
x86_64-w64-mingw32-g++ -c mylib.cpp -o mylib.o
```

- 64-bit windows C++ static library

```cpp
x86_64-w64-mingw32-ar rcs libmylib.a mylib.o
```

- 64-bit windows C++ exe with static library linked

```sh
# -L. => use libraries in current directory
# -lmylib => link against libmylib.a
x86_64-w64-mingw32-g++ main.cpp -o myprogram.exe -L. -lmylib

# try this if first doesn't work - check "cpp static compile"
x86_64-w64-mingw32-g++ main.cpp -o program.exe -static -static-libgcc -static-libstdc++ -L. -lmylib

# directly specify filename
x86_64-w64-mingw32-g++ main.cpp mylib.a -o myprogram.exe
```
