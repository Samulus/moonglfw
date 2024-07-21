# Windows Build Instructions (Conan, VS2022)
```
mkdir build
cd build
conan install .. -s compiler="Visual Studio" -s build_type=Debug -c tools.cmake.cmaketoolchain:generator=Ninja -s compiler.version=17 --build=missing --output-folder=.
cmake .. -DCMAKE_TOOLCHAIN_FILE=(toolchain file path from conan)
```

