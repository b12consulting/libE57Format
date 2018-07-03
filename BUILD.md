

## Build E57Format
cmd command to create vs project
```
cmake -G "Visual Studio 15 2017 Win64" .
cmake --build . --config Release
```

## Build Xerces (Tools)
See https://xerces.apache.org/xerces-c/build-3.html for the dll build. 
Here is a resume:
```
mkdir build
cd build
cmake -G "Visual Studio 15 2017 Win64" -DCMAKE_INSTALL_PREFIX=../libs ..
cmake --build . --config Release --target install 
ctest -V -C Release -j 4
```

Then, open the visual studio project and change dll to lib in the `library/xerces-c` project and compile it again via visual studio. It will produce an additional library `build/src/Release/xerces-c_3_2.lib`. Move it to `libs/lib`.