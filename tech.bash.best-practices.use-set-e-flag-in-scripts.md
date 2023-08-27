---
id: w0018k99xnc2p5uuvp0dq9v
title: Use 'set -e' Flag in Scripts
desc: ''
updated: 1676911980672
created: 1676909944706
---

In scripts, almost always a good idea to set `set -e` flag. 

> The set -e command in Bash enables the "exit immediately" option, which causes the shell to exit as soon as any command it executes returns a non-zero exit status.

<details>

While its great to exit out of the script that is running in another process (`./some-script.sh`), upon encountering a non zero response.

It's rather annoying to get your bash session closed on your from a sourced function that had `source ./some-functions.sh` with `set -e` flag. Hence, avoid setting `set -e` in functions that you source.
</details>


<details>
<summary>Example code</summary>

```shell
set -e

func-which-returns-1() {
  echo "I will return 1"
  return 1
}

set-e-demo_MAIN() {
  func-which-returns-1

  echo "This line will not be printed."
}

set-e-demo_MAIN
```
</details>


<details>
<summary>Working examples</summary>

```shell
gt.sandbox.checkout.commit.cleanly ded1416 \
&& cd shell/bash \
&& ./set-e-demo.sh
```

```shell
gt.sandbox.checkout.commit.cleanly ded1416 \
&& cd shell/bash \
&& ./set-e-demo.sh || echo "OR after running process will be allowed to run."
```
</details>

