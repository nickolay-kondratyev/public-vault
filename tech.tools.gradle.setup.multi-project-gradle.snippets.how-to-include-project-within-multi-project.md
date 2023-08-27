---
id: w9bp8lhwlup1nse9bd3naa7
title: How to Include Project within Multi Project
desc: ''
updated: 1683409241128
created: 1683409078288
---

```kts
    sourceSets {
        val commonMain by getting {
            dependencies {
                implementation(project(":myDependencyLib"))
            }
        }
```

Also see [[tech.tools.gradle.setup.multi-project-gradle]]