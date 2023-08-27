---
id: hf0qy6zw7jxuhs7lnaprjxe
title: When Switch Like
desc: ''
updated: 1678070450334
created: 1678070450334
---

```kts
    val toolchain = when {
        currentOs.isLinux -> "linux-x86_64"
        currentOs.isMacOsX -> "darwin-x86_64"
        else -> error("No Android toolchain defined for this OS: $currentOs")
    }
```