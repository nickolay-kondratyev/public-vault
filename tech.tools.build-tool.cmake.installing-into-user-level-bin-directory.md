---
id: vcoi5keg07i5n13iglvtpjs
title: Installing into User Level Bin Directory cmake install
desc: ''
updated: 1676064639330
created: 1676063715934
---

## About
```shell
cmake install
```

Allows installation of your executable into widely accessible bin folders such as `/usr/local/bin/`

## Live example using "cmake install"
```shell
gt.sandbox.checkout.commit.cleanly 56ae6c2 \
&& cd cpp/trim \
&& (rm -rf ./build; rm /usr/local/bin/trim-example-app; echo "cleaned") \
&& cmake -S . -B ./build \
&& cd build \
&& make install \
&& trim-example-app first second
```

## Sample CMake file with install 
<details>
<summary>Sample CMake with installation</summary>

```cmake

cmake_minimum_required(VERSION 3.0.0)

project(TrimProjectName)

add_executable(trim-example-app main.cpp)

# Just running make will not install the executable.
# You need to run
#
# make install
#
# DESTINATION bin will be written to some system defined directory
# on MAC for me it ended up in
# -- Installing: /usr/local/bin/trim-example-app
install(TARGETS trim-example-app DESTINATION bin)
```
</details>




