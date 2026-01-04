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


This past summer, I decided to take a C programming class to sharpen my coding skills.

But as my assignments became more complex, they required multiple header and implementation files. This is where tools known as [build systems](https://en.wikipedia.org/wiki/Build_system_(software_development)) come into play, such [as GNU Make](https://www.gnu.org/software/make/). The problem with C build systems is that there are arguably too many of them, and on top of this, there are what are known as meta [build systems](https://en.wikipedia.org/wiki/Build_system_(software_development)). Which are tools that create build scripts for other build systems.

​After reviewing the laundry list of compiler tools, I settled on [CMake](https://cmake.org/). CMake is a meta build system that can generates `makefiles` tailored for a specific platform and compiler, allowing you to easily cross-compile for different target architectures.

With all this out of the way lets set up a simple C project with CMake!

CMake has many features that I will not be covering here so you many want to [refer to the CMake documentation](https://cmake.org/documentation/)


## Installation

I would recommend following the [official CMake installation](https://cmake.org/download/) guide as this may become out of date!

{{< details summary="Click for Linux instructions" >}}

If you are on a unix/linx system you can install CMake using your systems package manager.

**For Example:**

~~~
sudo apt install make cmake
~~~

{{< /details >}}


{{< details summary="Click for Winows instructions" >}}

Windows Instructions go here!!!

{{< /details >}}


### Project Structure


I am not sure if there is a formal name for this type of project structure, but this is what I have seen used out in the wild most often for C and C++ projects. 
```
Project Name
├── README
├── LICENCE	
├── CMakeLists.txt    // simple CMakeLists.txt
├── build             // Where your build files go
├── include           // header files
├── lib               // external libraries 
└── src               // source code 
    └── main.c
```

### The Simple CMakeLists.txt


~~~CMake
cmake_minimum_required(VERSION 3.24)
set(PROJECTNAME Name)
project(${Name})

set(CMAKE_C_STANDARD 23) 
set(CMAKE_C_STANDARD_REQUIRED ON) 

# list of c files to compile
set(SOURCES
  # Source files go here
)

# gcc compile options
add_compile_options(-Wall -Wextra -save-temps)

add_executable(${PROJECT_NAME} ${SOURCES})

target_include_directories(${Name}
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/include
)
~~~


Above is what I have dubbed the simple CMakeLists.txt
