---
id: xr174bah1bp2ruogb179pjd
title: CMake
desc: ''
updated: 1676390827534
created: 1675917148955
---
> [CMake](https://cmake.org/) is a versatile tool that helps you build C/C++ projects on just about any platform you can think of. 

Running CMake does not build your software. You typically need to run [[tech.tools.build-tool.makefile]]

## Main Options
```shell
cmake [options] -S <path-to-directory-where-root-CMakeLists.txt-file-is> -B <path-to-build>
```

## Example C++

<details>
<summary>Working Example</summary>

```shell
gt.sandbox.checkout.commit.cleanly b22d565 \
&& cd "$GT_SANDBOX_REPO/cpp/hello-world" \
&& cmake -S . -B ./build \
&& cd build \
&& make \
&& ./HelloWorldProjectName.executable
```
</details>



<details>
<summary>HelloWorld Example CMakeLists.txt</summary>

![[tech.tools.build-tool.cmake.CMakeListsTxt.HelloWorldExample]]
</details>


## Relationships
- [[rel.relies-on]]:**[[tech.tools.build-tool.cmake.CMakeListsTxt]]**
- [[rel.cmake-generates-your-makefile]]:**[[tech.tools.build-tool.makefile]]**

## Files Generates by CMake

[Files Generates by CMake Video Ref Timestamp](https://youtu.be/nlKcXPUJGwA?t=533)

Don't modify files generated by CMake within your ./build path directory. Instead modify: [[tech.tools.build-tool.cmake.CMakeListsTxt]].

<details>
<summary>Example Files Generated By CMake</summary>

```shell
mac> cd "$GT_SANDBOX_REPO/cpp/hello-world/build" && tree
.
├── CMakeCache.txt
├── CMakeFiles
│   ├── 3.25.2
│   │   ├── CMakeCCompiler.cmake
│   │   ├── CMakeCXXCompiler.cmake
│   │   ├── CMakeDetermineCompilerABI_C.bin
│   │   ├── CMakeDetermineCompilerABI_CXX.bin
│   │   ├── CMakeSystem.cmake
│   │   ├── CompilerIdC
│   │   │   ├── CMakeCCompilerId.c
│   │   │   ├── CMakeCCompilerId.o
│   │   │   └── tmp
│   │   └── CompilerIdCXX
│   │       ├── CMakeCXXCompilerId.cpp
│   │       ├── CMakeCXXCompilerId.o
│   │       └── tmp
│   ├── CMakeDirectoryInformation.cmake
│   ├── CMakeError.log
│   ├── CMakeOutput.log
│   ├── CMakeScratch
│   ├── HelloWorldProjectName.executable.dir
│   │   ├── DependInfo.cmake
│   │   ├── build.make
│   │   ├── cmake_clean.cmake
│   │   ├── compiler_depend.make
│   │   ├── compiler_depend.ts
│   │   ├── depend.make
│   │   ├── flags.make
│   │   ├── link.txt
│   │   └── progress.make
│   ├── Makefile.cmake
│   ├── Makefile2
│   ├── TargetDirectories.txt
│   ├── cmake.check_cache
│   ├── pkgRedirects
│   └── progress.marks
├── Makefile
└── cmake_install.cmake

10 directories, 29 files
```

</details>



## Reference
- [CMake Tutorial EP 1 | Understanding The Basics](https://www.youtube.com/watch?v=nlKcXPUJGwA)
- [how-to-build-a-cmake-based-project](https://preshing.com/20170511/how-to-build-a-cmake-based-project/)


## More in depth

<details>
<summary>Using CMake to install into user level bin directory.</summary>


![[tech.tools.build-tool.cmake.installing-into-user-level-bin-directory]]
</details>

<details>
<summary>Using libraries with CMake</summary>

![[tech.tools.build-tool.cmake.libraries]]
</details>
