---
id: 65hokrbecpev38ceyy4x59e
title: Rg Ripgrep
desc: ''
updated: 1691342944899
created: 1679584546512
---

<details>
<summary>find, piped to rg, piped to fzf</summary>

## Command to reproduce:
```bash
gt.sandbox.checkout.commit e631ea5 \
&& cd "${GT_SANDBOX_REPO}/dir-with-files" \
&& cmd.run.announce "touch first_file && find . -mmin -10 -type f -print0 | xargs -0 rg . | fzf"
```


```
find . -mmin -10 -type f -print0 | xargs -0 rg . --hidden --with-filename --line-number --follow | fzf
```
</details>

![[tech.bash.commands.rg-ripgrep.types]]


