# Project: Cmake, Ninja and GCC - build simple C Application 

This project demonstrates how to build a simple C application using Ninja and CMake. 
It is a minimal example for beginners.

## 📑 Table of Contents
1. [Prerequisites](#prerequisites)  
2. [Clone the Project](#clone-the-project)  
3. [Configure and Build](#configure-and-build)  
   - [Option A: Ninja](#option-a-ninja)  
   - [Option B: MinGW Makefiles](#option-b-mingw-makefiles)  
4. [Run the Program](#run-the-program)  
5. [Clean the Build](#clean-the-build)

---

## 1. Prerequisites

Before you start, make sure you have installed:

- **GCC (MinGW-w64)** → the compiler  
- **CMake** → the build system generator  
- **Ninja** (optional but recommended) → fast build tool  

### Check installed tools and versions
Open your terminal (MSYS2 / cmd) and run commands: (If the commands return version numbers, the tools are installed correctly)
- gcc --version
- cmake --version
- ninja --version

If no please run MSYS2 MINGW64 terminal and run:
   
   _pacman -Syu_
   
   _pacman -S mingw-w64-x86_64-gcc mingw-w64-x86_64-cmake_
   
   _pacman -S mingw-w64-x86_64-make_

To install Ninja fast build tool please run:

   _pacman -S mingw-w64-x86_64-ninja_

---

## 2. Clone the Project

Download this repository from GitHub:

   _git clone https://github.com/bartekzone/build_simple_app_cmake.git_

Please check project tree and analyze comments in CMakeLists.txt file
<pre lang="markdown"> <code> ``` 
/project
├── CMakeLists.txt
├── main.c
└── hello/
    ├── hello.c
    └── hello.h
``` </code> </pre>
---

## 3. Configure and Build

First, navigate to the project folder (the one containing CMakeLists.txt):

   _cd reponame_

**Option A**: Configure and Build with Ninja tool

   _cmake -G Ninja -S . -B build -DCMAKE_BUILD_TYPE=Release
   cmake --build build_

Explanation:

cmake -G Ninja → select Ninja as the build generator

-S . → source directory = current folder

-B build → build output in the build/ folder

-DCMAKE_BUILD_TYPE=Release → optimize for release (faster binary)

cmake --build build → compile and link the program


**Option B**: Configure and Build with MinGW Makefiles:

   _cmake -G "MinGW Makefiles" -S . -B build -DCMAKE_BUILD_TYPE=Release_

   _cmake --build build_

Explanation:
Same as above, but instead of Ninja, CMake generates a Makefile
The build will be executed using mingw32-make under the hood

---

## 4. Run the Program
After successful compilation, the program will be located in the build/ folder. Type command:
   
   _./build/main.exe_

---

## 5. Clean the Build
To remove all generated build files, simply delete the build/ folder:

   _rm -rf build_
