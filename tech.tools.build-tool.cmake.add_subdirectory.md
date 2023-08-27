---
id: wyor2tmkhkdq2ws3yw2z2kh
title: add_subdirectory
desc: ''
updated: 1676442743305
created: 1676441413486
---


<details>
<summary>Working Example</summary>
```shell
gt.sandbox.checkout.commit.cleanly 9251612 \
&& cd cpp \
&& ./build_run.sh
```
</details>

<details>
<summary>Sample CMakeLists.txt with add_subdirectory that builds submodule that is pulled from github</summary>

```cmake
# Min version cmake check
cmake_minimum_required(VERSION 3.0)

# Project name
project(MyMain)

# This is pointing to submodule dir, and adding this activates
# CMakeLists.txt in that dir. 
add_subdirectory(external/glfw)

# Add executable target ${PROJECT_NAME} (MyMain) will be the name of the executable.
add_executable(${PROJECT_NAME} hi_world.cpp)
```
</details>

