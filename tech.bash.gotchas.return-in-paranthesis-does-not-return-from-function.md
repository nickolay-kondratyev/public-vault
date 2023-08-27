---
id: w4nvctdc0p46ug48qr4kgq5
title: Return in Paranthesis Does Not Return from Functio
desc: ''
updated: 1674144665670
created: 1674144626770
---

```shell
hi() {
  # Return wont work as expected since it will exit out of parenthesis 
  # and not the hi function. Allowing this method to continue further.
  echo "blah" | grep o1 || (echo "nope"; return 1)

  echo "FINISHED in HI"
}

hi
```