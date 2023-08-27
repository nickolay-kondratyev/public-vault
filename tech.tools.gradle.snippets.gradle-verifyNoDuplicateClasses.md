---
id: 4bmbebyl1znc8l7s61qo09d
title: gradle-verifyNoDuplicateClasses
desc: ''
updated: 1682738875247
created: 1682738866362
---

```kts
 tasks.register("verifyNoDuplicateClasses") {
        group = "verification"
        description = "Checks the project for duplicate classes across all dependencies."

        doLast {
            val classFileNames = mutableSetOf<String>()
            val duplicatesClassFileNames = mutableSetOf<String>()
            val classFileNamesToJars = mutableMapOf<String, MutableList<String>>()

            configurations.runtimeClasspath.get().resolvedConfiguration.resolvedArtifacts.forEach { artifact ->
                val jarFile = JarFile(artifact.file)
                jarFile.entries().iterator()
                    .forEach { entry ->
                        if (entry.name.endsWith(".class")
                            && entry.name.endsWith("module-info.class").not()
                        ) {
                            val classFileName = entry.name

                            classFileNamesToJars.getOrPut(classFileName) { mutableListOf() }
                                .add(artifact.file.name)

                            if (classFileNames.contains(classFileName)) {
                                duplicatesClassFileNames.add(classFileName)
                            } else {
                                classFileNames.add(classFileName)
                            }
                        }
                    }
                jarFile.close()
            }

            if (duplicatesClassFileNames.isNotEmpty()) {
                println("Found duplicate classes:")
                duplicatesClassFileNames.forEach { duplicate ->
                    println("- $duplicate is in ${classFileNamesToJars[duplicate]}")
                }
                throw GradleException("${duplicatesClassFileNames.size} Duplicate classes found. Refer to output to see more details. You can run 'gradle dependencies' to have more details on the dependencies.")
            } else {
                println("No duplicate classes found.")
            }
        }
    }
```