---
id: ajyw3r03qs49f7cjcw615sp
title: Check If Directory Is Empty
desc: ''
updated: 1676843907161
created: 1676843895957
---


```shell
if [[ "$(ls -A /tmp)" ]]; then
  echo "Directory is not empty"
else
  echo "Directory is empty OR does not exist."
fi
```