---
id: ker895h3lpg43ah81gdohvp
title: dont-try-to-OR-after-source
desc: ''
updated: 1676912257248
created: 1676911200619
---


If you have the following example code:
```shell
set -e

failingFunc() {
  echo "failingFunc will return 1"
  return 1
}

failing-main_MAIN() {
  echo "PrintA, will 'return 1', on next line."

  failingFunc

  echo "PrintB, will should NOT be printed. (after 'return 1')"
}

failing-main_MAIN
```

You expect `set -e` to guarantee an exit (Refer to [[tech.bash.best-practices.use-set-e-flag-in-scripts]]) when function returns non 0 return code. Not reaching 'PrintB'. However, if you were to source the file and use '||' operator after the sourcing.

Such as:
```shell
source ./failing-main.sh || echo "Added || after failing main."
```

You would in fact see the following output:

```text
PrintA, will 'return 1', on next line.
failingFunc will return 1
PrintB, will should NOT be printed. (after 'return 1')
```

<details>
<summary>Working example</summary>

```shell
gt.sandbox.checkout.commit.cleanly 7c3b984 \
&& cd shell/bash \
&& source ./failing-main.sh || echo "Added || after failing main."
```
</details>

## Instead 
?? 
