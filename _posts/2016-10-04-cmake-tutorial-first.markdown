---
layout: post
title:  "Cmake - Hello World"
date:   2016-10-03 16:46:42 +0900
categories: update
---
{% highlight sh %}
cmake
cmake_minimum_required(VERSION 3.6)
project(cmake)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(SOURCE_FILES main.cpp)
add_executable(hello ${SOURCE_FILES})
{% endhighlight %}

{% highlight cpp %}
main.cpp
#include <iostream>

int main(void)
{
    cout << "Hello World" << endl;
    return 0;
}
{% endhighlight %}

![kind-screenshot]({{ site.uri }}/downloads/cmake1_01.png)

cmake .

make

./hello

