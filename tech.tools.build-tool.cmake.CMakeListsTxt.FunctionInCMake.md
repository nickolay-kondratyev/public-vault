---
id: asfilyp84bo3q80v9rdmkmi
title: FunctionInCMak
desc: ''
updated: 1679179149005
created: 1679179149005
---

```cmake
function(my_function arg1 arg2)
    message("arg1: ${arg1} arg2: ${arg2}")
endfunction()

my_function("value1" "value2")
```

## Command to reproduce:
```bash
gt.sandbox.checkout.commit d065588 \
&& cd "${GT_SANDBOX_REPO}/cpp/function-in-cmake" \
&& cmd.run.announce "cmake -S . -B ./build"
```

## Recorded output of command:
```
-- Configuring done
-- Generating done
-- Build files have been written to: /Users/vintrin/git_repos/glassthought-sandbox/cpp/function-in-cmake/build
```