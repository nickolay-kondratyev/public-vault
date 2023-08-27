---
id: aj4lt3gxsnfpkqcalyv4lxa
title: Slice off Prefix String
desc: ''
updated: 1692934451935
created: 1692934416572
---

```shell
  path_with_prefix="package:/data/app/hi"
  echo "path_with_prefix: ${path_with_prefix:?}"

  path_without_prefix="${path_with_prefix#package:}"
  echo "path_without_prefix: ${path_without_prefix:?}"
```