---
id: muuab6k26r20j848r6znup3
title: Usage of Libraries with CMake
desc: ''
updated: 1676388961231
created: 1676351185432
---

## Links
- [add_library documentation](https://cmake.org/cmake/help/latest/command/add_library.html)
- [CMake Tutorial - Libraries Video Timestamp](https://youtu.be/DDHCEE_PHOU?t=688)

## Command in CMake
<details>
<summary>add_library</summary>

```
add_library(<name> [STATIC | SHARED | MODULE]
            [EXCLUDE_FROM_ALL]
            [<source>...])
```

[add_library documentation](https://cmake.org/cmake/help/latest/command/add_library.html)
</details>

## Example CMakeLists.txt for library
<details>
<summary>CMakeLists.txt</summary>

```cmake
cmake_minimum_required(VERSION 3.0)

project(mymath)

add_library(mymath adder.cpp)
```
</details>


## Working Example
<details>
<summary>Working Example</summary>

```shell
gt.sandbox.checkout.commit.cleanly 9671ea2 \
&& cd "$GT_SANDBOX_REPO/cpp/LibProducer" \
&& cmake -S . -B ./build \
&& cd build \
&& make \
&& cd "$GT_SANDBOX_REPO/cpp/LibConsumer" \
&& cmake -S . -B ./build \
&& cd build \
&& make \
&& echo "Running ./LibConsumer" \
&& ./LibConsumer
```
</details>


<details>
<summary>Output of building library</summary>

```out
...
[ 50%] Building CXX object CMakeFiles/mymath.dir/adder.cpp.o
[100%] Linking CXX static library libmymath.a
[100%] Built target mymath
```

note `lib` prefix is added and `.a` suffix is added. 

The default output of `add_library` is static library of `.a`. 

[[tech.file-type.dot-a]] will contain the definitions. But will still need the declaration (the header file).
</details>



