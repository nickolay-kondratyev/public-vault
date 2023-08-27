---
id: bbznc5lgg2v206vqe3epqdb
title: Kover-code-coverage
desc: ''
updated: 1682210510098
created: 1682210510098
---

## GitHub Link
- [GitHub Link](https://github.com/Kotlin/kotlinx-kover).

## To Generate HTML report:
To generate HTML report:
```shell
gradle koverHtmlReport
```

## To Add to build.gradle.kts
```kts
plugins {
    //...
    id("org.jetbrains.kotlinx.kover") version "0.7.0-Beta"
}
```

## Kover Commands:
```shell
mac> gradle.list.tasks.all | grepmine kover
--------------------------------------------------------------------------------
koverHtmlReport
koverVerify
koverXmlReport
koverFindJar
koverGenerateArtifact
```
