# Debug Build README

## Description

Here you should be able to make the debug build using Cmake. Using Cmake is the best as this will generate the build files and then you can let Cmake evoke (choose) the build tool for you. Below are the commands you will need to do to build using the different OS's 

## ✅ General Build Steps (All OS)

From the root of your project:

```bash
cd build/Debug
cmake ..
cmake --build .
```

Add `-DCMAKE_BUILD_TYPE=Debug`.


### Compile_comands.json
This is a needed when trying to build using Nvim and wxWidgets

``` bash
cmake ../../ -DCMAKE_EXPORT_COMPILE_COMMANDS=ON && cp compile_commands.json ../../
```


---

## 🪟 Windows (MSVC or MinGW)

### 🟦 Option 1: MSVC (Visual Studio)

```bash
cmake .. -G "Visual Studio 17 2022" -A x64
cmake --build . --config Debug
```

- Opens `.sln` file in Visual Studio.
    
- Use `-A Win32` for 32-bit.
    

### 🟨 Option 2: MinGW

```bash
cmake .. -G "MinGW Makefiles" -DCMAKE_BUILD_TYPE=Debug
mingw32-make
```

- Ensure MinGW is in your `PATH`.
    

---

## 🍎 macOS

```bash
cmake .. -DCMAKE_BUILD_TYPE=Debug
cmake --build .
```

- Uses AppleClang.
    
- You may optionally pass `-GXcode` to use Xcode:
    

```bash
cmake .. -G Xcode
open MyWxApp.xcodeproj
```

---

## 🐧 Linux

```bash
cmake .. -DCMAKE_BUILD_TYPE=Debug
cmake --build .
```

- Uses GCC or Clang.
    
- Install dependencies: `sudo apt install libwxgtk3.0-gtk3-dev` (or build from your `lib/wxWidgets`)
    

---

## 💡 Optional: Specify Install Path

```bash
cmake .. -DCMAKE_INSTALL_PREFIX=/your/custom/path
```

Then install:

```bash
cmake --install .
```

---

## ✅ Summary Cheat Sheet

|Platform|Command Example|
|---|---|
|**Linux**|`cmake .. && cmake --build .`|
|**macOS**|`cmake .. && cmake --build .` or `cmake .. -G Xcode`|
|**Windows (MSVC)**|`cmake .. -G "Visual Studio 17 2022" -A x64 && cmake --build . --config Debug`|
|**Windows (MinGW)**|`cmake .. -G "MinGW Makefiles" -DCMAKE_BUILD_TYPE=Debug && mingw32-make`|
