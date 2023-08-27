---
id: mkefd1yb5o9wu93sny36cfi
title: Examine Symbols Objectdump Too
desc: ''
updated: 1679167043485
created: 1679167043485
---

```shell
 objdump -t <library_file.a>
```

------------------------------------------------------
Model: Default (GPT-3.5) #chatgpt

> Is there a tool to examine what objects are defined in .a file (c++ library file)

Yes, there are various tools you can use to examine what objects are defined in a C++ library file (.a file). Here are a few options:

1.  objdump: This is another command-line tool available on Unix-based systems that provides detailed information about the contents of object files and libraries. You can use the following command to list the symbols in a .a file:
    
    
    ```bash
    objdump -t <library_file.a>
    ```
    
    The `-t` option tells `objdump` to display the symbol table for the library.

2.  nm: This is a command-line tool available on Unix-based systems (including macOS and Linux) that displays the symbols (i.e., functions, variables, etc.) defined in an object file or library. You can use the following command to list the symbols in a .a file:
    
    
    ```bash
    nm -g <library_file.a>
    ```
    
    The `-g` option tells `nm` to display only global (i.e., externally visible) symbols.
    

    
3.  readelf: This is a command-line tool available on Unix-based systems that displays information about ELF (Executable and Linkable Format) files, including object files and libraries. You can use the following command to list the symbols in a .a file:
    
    
    ```bash
    readelf -s <library_file.a>
    ```
    
    The `-s` option tells `readelf` to display the symbol table for the library.
    

All of these tools should give you similar information about the symbols defined in a C++ library file.