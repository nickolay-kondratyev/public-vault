---
id: 43p7vwnmyzzf9xxx0e6mfbn
title: Makefile
desc: ''
updated: 1676063113151
created: 1675997937799
---

## Naming 
By convention its named `Makefile` but lowercase `makefile` should work fine as well. 

## About
Makefile just runs commands commands in your terminal.
## HelloWorld make file
/dir/makefile:
```makefile
default:
	echo hi
```

in /dir/ run
```shell
make
```

to execute the file.

## Basic of Makefile
Just runs whatever command you tell it to run.

## Notes  
Does not accept spaces at the front of the command, needs to be a tab.

## Example Commit
```shell
gt.sandbox.checkout.commit.cleanly dc41a95 \
&& cd cpp/hello-world \
&& make \
&& ./out_runnable
```