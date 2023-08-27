---
id: 79G9njwvNStMJFutXOp5L
title: check-if-directory-exists-or-does-NOT-exist
desc: ''
updated: 1676001426072
created: 1629394214730
---

## Directory Exists
```shell
if [[ -d /tmp ]]
then
	echo "Directory /tmp does exists."
fi
```

```shell
[ -d "./target" ] && echo 'Target directory exists'
```

## Directory does not exist
```shell
if [[ ! -d /tmp2 ]]
then
	echo "Directory /tmp2 does NOT exists."
  return 1
fi
```


