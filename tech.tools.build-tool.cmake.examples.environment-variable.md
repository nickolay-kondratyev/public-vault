---
id: vvyd64d5gp0avuugy375jqz
title: Environment Variable
desc: ''
updated: 1676785769204
created: 1676785755848
---

> Use the syntax $ENV{VAR} to read environment variable VAR.

https://cmake.org/cmake/help/latest/variable/ENV.html

## Example usage
```cmake
SET(CMAKE_C_COMPILER   $ENV{C_COMPILER_PATH_ANDROID})
```

```cmake
set(my_var "ANDROID_ARCH=$ENV{ANDROID_ARCH}")
```

## To Verify existence
![[tech.tools.build-tool.cmake.examples.environment-variable.verify-existence]]