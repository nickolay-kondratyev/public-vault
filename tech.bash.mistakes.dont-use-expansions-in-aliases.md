---
id: j856ctxo2q396jmxvq7o5jv
title: Dont Use Expansions in Aliases
desc: ''
updated: 1668790079924
created: 1668789456120
---

Don't use expansions within aliases with double quotes `"`.

- `$(function-expansion)`
- `${VARIABLE_EXPANSION}`

Both of these will expand at the time of sourcing the file rather than at the time of execution of this alias. (Hence you will get the working directory when you sourced the files that define these aliases). 

```shell
# WRONG
alias echo.pwd="echo $(pwd)"
```

```shell
# WRONG
alias echo.pwd="echo $PWD"
```

## Single quotes work but NOT recommended
```shell
# WORKS not recommended
alias echo.pwd='echo $(pwd)'
```

## Instead use shell functions. 
Use shell functions when you want to use expansions.

```shell
# RECOMMENDED:
echo.pwd(){
  echo $(pwd)
}
```

To avoid any mistakes of undesired expansions occurring.