---
id: nz6rwgvgdeo3o9qjtjj6h1x
title: settings.gradle(.kts)
desc: ''
updated: 1683394667863
created: 1683394227284
---

## Notes

```kts
rootProject.name = "demo"
include("app", "list", "utilities")
```

`rootProject.name` assigns a name to the build, which overrides the default behavior of naming the build after the directory it’s in. It’s recommended to set a fixed name as the folder might change if the project is shared - e.g. as root of a Git repository.

`include("app", "list", "utilities")` defines that the build consists of three subprojects in the corresponding folders. More subprojects can be added by extending the list or adding more include(…​) statements. 



## References
- [Building Kotlin Applications with libraries Sample](https://docs.gradle.org/current/samples/sample_building_kotlin_applications_multi_project.html)