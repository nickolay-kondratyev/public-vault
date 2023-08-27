---
id: gtfaxg6vtm3pekcxekht7ja
title: Compiled with g++ directly
desc: ''
updated: 1676043972788
created: 1675999939160
---

## Compile it with g++
```shell
g++ main.cpp -o out_runnable
```

## Run it:
```shell
./out_runnable
```

## Example Commit:
```shell
gt.sandbox.checkout.commit.cleanly df75277 \
&& cd cpp/hello-world \
&& file.execute.announce ./build.sh \
&& file.execute.announce ./run.sh
```