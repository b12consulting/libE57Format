

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

## Register FARO LS SDK
Run cmd.exe in admin mode (search for cmd.exe and right click on the search result) 
and execute the following commands:
```
cd C:\Windows\WinSxS\amd64_faro.ls_1d23f5635ba800ab_1.1.701.2_none_3592adf9356a0308
regsvr32 .\iQOpen.dll
regsvr32 .\FARO.LS.SDK.dll
```

To unregister the dll use the command (as admin):
```
cd C:\Windows\WinSxS\amd64_faro.ls_1d23f5635ba800ab_1.1.701.2_none_3592adf9356a0308
regsvr32 .\iQOpen.dll -U
regsvr32 .\FARO.LS.SDK.dll -U
```