---
id: 2tgrpck8s3fnwbj09h921aq
title: Submodules
desc: ''
updated: 1690759852722
created: 1675919366601
---

## Add submodule into sub-directory
```shell
git submodule add <git@github ...> snipmate-snippets/snippets/
```
[SO-post](https://stackoverflow.com/a/9035930/7858768)

## Submodules to be set to what they were
```shell
git submodule init && git submodule update
```

## To recursively setup submodules
```shell
git submodule update --init --recursive
```
Quite useful when your submodules have submodules, which in turn can have their own submodules.