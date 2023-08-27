---
id: ehzpzfzu046hrsds2919jrn
title: Verify Existence
desc: ''
updated: 1678045746396
created: 1678045746396
---

# Verify environment variables are set:
```cmake
if(NOT DEFINED ENV{C_COMPILER_PATH_ANDROID})
    message(FATAL_ERROR "You must set C_COMPILER_PATH_ANDROID environment variable")
endif()
```
