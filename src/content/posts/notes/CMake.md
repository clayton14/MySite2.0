---
title: "My Simple CMake Setup"
date: 2025-09-01T16:51:28-04:00
draft: false
searchHidden: false
ShowToc: true
author: Clayton Easley
tags: 
    - References
    - CMake
description: 
categories: ["Software"]
cover:
    image:

editPost:
    URL: https://github.com/clayton14/MySite2.0
    Text: "Suggest Changes"
---

{{< figure 
    src="/img/cmake_logo_dark.png" 
    alt="CMake logo" >}}



In my summer semester of 2025 I decided to take a C programming class to sharpen my coding skills. But, as my assignments became more complex, they required multiple header and implementation files. This is where tools known as [build systems](https://en.wikipedia.org/wiki/Build_system_(software_development)) come into handy, such [as GNU Make](https://www.gnu.org/software/make/). The problem with C build systems is that there are arguably too many of them, and on top of this, there are what are known as meta [build systems](https://en.wikipedia.org/wiki/Build_system_(software_development)). Meta build systems are tools that create build scripts for other build systems.

After reviewing the laundry list of compiler tools, I settled on [CMake](https://cmake.org/). CMake is a meta build system that can generates `makefiles` tailored for a specific platform and compiler, allowing you to easily [cross-compile](https://en.wikipedia.org/wiki/Cross_compiler) for different target architectures.

With all this out of the way lets set up a simple C project with CMake!

CMake has many features that I will not be covering here so you many want to [refer to the CMake documentation](https://cmake.org/documentation/)


## Installation

I would recommend following the [official CMake installation](https://cmake.org/getting-started/) guide as this may become out of date! On top of this, I have not tested my CMakeLists.txt file on Windows and recommend using [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install) unless you are devloping applications specificly for Windows.


{{< details summary="Click for Linux instructions" >}}

---

If you are on a unix/linx system you can install CMake using your systems package manager.

**For Example:**

~~~
sudo apt install cmake
~~~

Once installed you can check with

~~~
cmake --version
~~~

{{< /details >}}

<br><br>

{{< details summary="Click for Winows instructions" >}}

---

Windows now has a package manager similar to what is found on UNIX systems. [Windows Package Manager (winget)](https://github.com/microsoft/winget-cli) can be used to install CMake just like `apt` with the lovely UAC prompt. 

**In a PowerShell terminal run:**

~~~
winget install cmake
~~~

**NOTE:** CMake is not a compiler and if you are on Windows you will need to install a C/C++ compiler such as [MSVC](https://visualstudio.microsoft.com/downloads/)


{{< /details >}}



## Project Structure


I am not sure if there is a formal name for this type of project structure, but this is what I have seen used out in the wild most often for C and C++ projects and what I prefer to use.
```
Project Name
├── README
├── LICENCE	
├── CMakeLists.txt    // simple CMakeLists.txt
├── build             // Where your build files go
├── include           // header files
├── lib               // external libraries (.so or .dll)
└── src               // source code 
    └── main.c
```

## Basic CMakeLists {#config}

Here is a basic simple CMakeLists.txt to get a C or C++ project started. In your projects root directory copy this into your `CMakeLists.txt` file. 

Make sure to replace anything you see in `<>` such as `<Name>` without the brackets.

~~~CMake
cmake_minimum_required(VERSION 3.24)
set(PROJECT_NAME <Name>)
project(${PROJECT_NAME})

set(CMAKE_C_STANDARD 23) 
set(CMAKE_C_STANDARD_REQUIRED ON) 

# list of c files to compile
set(SOURCES
  # Source files go here
  # src/main.c
  <add files here>
)

# gcc compile options (Optional)
# add_compile_options(-Wall -Wextra -save-temps)

add_executable(${PROJECT_NAME} ${SOURCES})

target_include_directories(${PROJECT_NAME}
  PRIVATE
        ${PROJECT_SOURCE_DIR}/include
)
~~~

## Build and Run

Once you have copied and edited your `CMakeLists.txt` you need to run `cmake` to generate the lower level build scripts for your project. 

In your `build` directory run:

~~~
cmake ..
~~~

Running this command will generate a `Makefile` in your project's `build` directory.

Once your build scripts are generated run `make` in the `build` directory to compile your project.

~~~
make
~~~

Doing so will create a compiled binary in your `build` directory that you run using `./<project-name>`

