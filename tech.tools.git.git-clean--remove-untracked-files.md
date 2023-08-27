---
id: 4nrd9wi53ad1ccc2vf55pja
title: Git Clean  Remove Untracked F
desc: ''
updated: 1675874145438
created: 1675873676535
---

```shell
# Print out the list of files and directories which will be removed (dry run)
git clean -f -x --dry-run
```

```shell
git clean -f -x # To remove ignored and non-ignored file. 
```

> Normally, only files unknown to Git are removed, but if the -x option is specified, ignored files are also removed. This can, for example, be useful to remove all build products. 

## Ref
- [SO post](https://stackoverflow.com/questions/61212/how-do-i-remove-local-untracked-files-from-the-current-git-working-tree)