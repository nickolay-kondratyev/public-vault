---
id: gkq6z7p4lluj8nkzzxhnqqa
title: Check If File Does Not Exist
desc: ''
updated: 1676853417815
created: 1674057651432
---

```shell
if [[ ! -f /tmp/file12 ]]
then
  echo "File not found, (or something is found but 	its not a file Eg. its a directory)"
else
  echo "File found"
fi
```