---
id: 8reg69psetyi06q8r2cjzio
title: HelloWorldExample CMakeLists.txt
desc: ''
updated: 1676061721556
created: 1676061637517
---

```cmake
# Min versin cmake check
cmake_minimum_required(VERSION 3.0)

# Project name
project(HelloWorldProjectName)

# Add executable target ${PROJECT_NAME}.executable will be the
# name of the executable.
add_executable(${PROJECT_NAME}.executable hello_world_main.cpp)
```

------------------------------------------------------

## Command to reproduce:
```bash
gt.sandbox.checkout.commit 65d00c5 \
&& cd "${GT_SANDBOX_REPO}/cpp/hello-world" \
&& cmd.run.announce "cmake -S . -B ./build && cd build && make && ./HelloWorldProjectName.executable"
```

## Recorded output of command:
```
-- Configuring done
-- Generating done
-- Build files have been written to: /Users/vintrin/git_repos/glassthought-sandbox/cpp/hello-world/build
[100%] Built target HelloWorldProjectName.executable
Hello World!
```