---
id: c3wmzcdpgk2g40tvpiyyq9j
title: DereferencingVariableInCMakeFunction
desc: ''
updated: 1679179879052
created: 1679179879052
---

```cmake
function(print_var_and_check_file_exists var_name)
  if(NOT EXISTS ${${var_name}})
    # Use fatal error to stop CMake from continuing
    # message(FATAL_ERROR "File ${${var_name}} does NOT exist (defined by ${var_name})")
    message("File ${${var_name}} does NOT exist (defined by ${var_name})")
  endif()

  if(EXISTS ${${var_name}})
    message("File ${${var_name}} exists (defined by ${var_name})")
  endif()
endfunction()

set(non_existent_file "/path/to/my/file.txt")
set(existent_file "/tmp")

print_var_and_check_file_exists("existent_file")
print_var_and_check_file_exists("non_existent_file")
```


## Command to reproduce:
```bash
gt.sandbox.checkout.commit 0afd4b5 \
&& cd "${GT_SANDBOX_REPO}/cpp/dereferencing_variable_name" \
&& cmd.run.announce "./configure_cmake.sh"
```

## Recorded output of command:
```
-- Configuring done
-- Generating done
-- Build files have been written to: /Users/vintrin/git_repos/glassthought-sandbox/cpp/dereferencing_variable_name/build
```