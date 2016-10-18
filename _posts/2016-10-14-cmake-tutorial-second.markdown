---
layout: post
title:  "Cmake - 프로젝트 삘좀 내보자"
date:   2016-10-14 20:11:12 +0900
categories: update
---

{% highlight cpp %}
./include/myMath.h
#pragma once
namespace Mathlib
{
    class MyMath
    {
    public:
        MyMath();
        ~MyMath();
        int add(int a, int b);
    private:
    };
}
{% endhighlight %}

{% highlight cpp %}
./src/myMath.cpp
#include "myMath.h"
namespace Mathlib
{
    MyMath::MyMath()  {}
    MyMath::~MyMath() {}
    int MyMath::add(int a, int b)
    {
        return a + b;
    }
}
{% endhighlight %}

{% highlight sh %}
./CMakeList.txt
#cmake info
cmake_minimum_required(VERSION 3.5)
project(cmake)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set (LIBRARY_OUTPUT_PATH lib)
# === myMath
set(MYMATH_INCLUDE_DIRS ${CMAKE_CURRENT_SOURCE_DIR}/include)
set(MYMATH_LIBRARIES mylibs)
# === include path
include_directories(${MYMATH_INCLUDE_DIRS})
# == execute src
set(SOURCE_FILES main.cpp)
add_executable(main ${SOURCE_FILES})
# == link
target_link_libraries(main ${MYMATH_LIBRARIES})
add_subdirectory(./src)
{% endhighlight %}

{% highlight sh %}
./src/CMakeList.txt
cmake_minimum_required(VERSION 3.5)
project(cmake)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set (LIBRARY_OUTPUT_PATH ../lib)
set (LIBSRCS
        myMath.cpp)
# === myMath
set(MYMATH_LIBRARIES mylibs)
# === include path
add_library(mylibs STATIC ${LIBSRCS})
include_directories(../include)
{% endhighlight %}

![kind-screenshot]({{ site.uri }}/downloads/cmake2_01.png)

cmake .

make

./main