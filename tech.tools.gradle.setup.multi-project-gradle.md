---
id: odzmrm6v34w6axkhf9ofdd9
title: Multi Project Gradle
desc: ''
updated: 1685414796880
created: 1683083652370
---

<details>
<summary>Simplified project with 2 dependencies</summary>


```bash
gt.sandbox.checkout.commit 0693fde \
&& cd "${GT_SANDBOX_REPO}/simplified_top_level_project" \
&& idea . &
```

</details>

-------------------------------------------------------

[Building Kotlin Applications with libraries Sample](https://docs.gradle.org/current/samples/sample_building_kotlin_applications_multi_project.html)
<details>
<summary>Build of sample app referenced in above link</summary>

## Command to reproduce:
```bash
gt.sandbox.checkout.commit 26df91a \
&& cd "${GT_SANDBOX_REPO}/sample_building_kotlin_applications_multi_project-kotlin-dsl" \
&& cmd.run.announce "gradle build"
```

## Recorded output of command:
```
> Task :buildSrc:generateExternalPluginSpecBuilders UP-TO-DATE
> Task :buildSrc:extractPrecompiledScriptPluginPlugins UP-TO-DATE
> Task :buildSrc:compilePluginsBlocks UP-TO-DATE
> Task :buildSrc:generatePrecompiledScriptPluginAccessors UP-TO-DATE
> Task :buildSrc:generateScriptPluginAdapters UP-TO-DATE
> Task :buildSrc:compileKotlin UP-TO-DATE
> Task :buildSrc:compileJava NO-SOURCE
> Task :buildSrc:compileGroovy NO-SOURCE
> Task :buildSrc:pluginDescriptors UP-TO-DATE
> Task :buildSrc:processResources UP-TO-DATE
> Task :buildSrc:classes UP-TO-DATE
> Task :buildSrc:jar UP-TO-DATE
> Task :buildSrc:inspectClassesForKotlinIC UP-TO-DATE
> Task :list:compileKotlin UP-TO-DATE
> Task :list:compileJava NO-SOURCE
> Task :utilities:compileKotlin UP-TO-DATE
> Task :utilities:compileJava NO-SOURCE
> Task :app:compileKotlin UP-TO-DATE
> Task :app:compileJava NO-SOURCE
> Task :app:processResources NO-SOURCE
> Task :app:classes UP-TO-DATE
> Task :app:jar UP-TO-DATE
> Task :app:inspectClassesForKotlinIC UP-TO-DATE
> Task :list:processResources NO-SOURCE
> Task :list:classes UP-TO-DATE
> Task :list:jar UP-TO-DATE
> Task :list:inspectClassesForKotlinIC UP-TO-DATE
> Task :utilities:processResources NO-SOURCE
> Task :utilities:classes UP-TO-DATE
> Task :utilities:jar UP-TO-DATE
> Task :utilities:inspectClassesForKotlinIC UP-TO-DATE
> Task :app:startScripts UP-TO-DATE
> Task :app:distTar UP-TO-DATE
> Task :app:distZip UP-TO-DATE
> Task :app:assemble UP-TO-DATE
> Task :app:compileTestKotlin UP-TO-DATE
> Task :app:compileTestJava NO-SOURCE
> Task :app:processTestResources NO-SOURCE
> Task :app:testClasses UP-TO-DATE
> Task :app:test UP-TO-DATE
> Task :app:check UP-TO-DATE
> Task :app:build UP-TO-DATE
> Task :list:assemble UP-TO-DATE
> Task :list:compileTestKotlin UP-TO-DATE
> Task :list:compileTestJava NO-SOURCE
> Task :list:processTestResources NO-SOURCE
> Task :list:testClasses UP-TO-DATE
> Task :list:test UP-TO-DATE
> Task :list:check UP-TO-DATE
> Task :list:build UP-TO-DATE
> Task :utilities:assemble UP-TO-DATE
> Task :utilities:compileTestKotlin NO-SOURCE
> Task :utilities:compileTestJava NO-SOURCE
> Task :utilities:processTestResources NO-SOURCE
> Task :utilities:testClasses UP-TO-DATE
> Task :utilities:test NO-SOURCE
> Task :utilities:check UP-TO-DATE
> Task :utilities:build UP-TO-DATE

BUILD SUCCESSFUL in 476ms
26 actionable tasks: 26 up-to-date
```

</details>

<details>
<summary>Multi project with sub-directory</summary>

## Command to reproduce:
```bash
gt.sandbox.checkout.commit 1def70e \
&& cd "${GT_SANDBOX_REPO}/sample_building_kotlin_applications_multi_project-kotlin-dsl" \
&& cmd.run.announce "gradle build"
```

## Recorded output of command:
```
> Task :buildSrc:generateExternalPluginSpecBuilders UP-TO-DATE
> Task :buildSrc:extractPrecompiledScriptPluginPlugins UP-TO-DATE
> Task :buildSrc:compilePluginsBlocks UP-TO-DATE
> Task :buildSrc:generatePrecompiledScriptPluginAccessors UP-TO-DATE
> Task :buildSrc:generateScriptPluginAdapters UP-TO-DATE
> Task :buildSrc:compileKotlin UP-TO-DATE
> Task :buildSrc:compileJava NO-SOURCE
> Task :buildSrc:compileGroovy NO-SOURCE
> Task :buildSrc:pluginDescriptors UP-TO-DATE
> Task :buildSrc:processResources UP-TO-DATE
> Task :buildSrc:classes UP-TO-DATE
> Task :buildSrc:jar UP-TO-DATE
> Task :buildSrc:inspectClassesForKotlinIC UP-TO-DATE
> Task :list:compileKotlin UP-TO-DATE
> Task :list:compileJava NO-SOURCE
> Task :subDir:utilities:compileKotlin UP-TO-DATE
> Task :subDir:utilities:compileJava NO-SOURCE
> Task :app:compileKotlin UP-TO-DATE
> Task :app:compileJava NO-SOURCE
> Task :app:processResources NO-SOURCE
> Task :app:classes UP-TO-DATE
> Task :app:jar UP-TO-DATE
> Task :app:inspectClassesForKotlinIC UP-TO-DATE
> Task :list:processResources NO-SOURCE
> Task :list:classes UP-TO-DATE
> Task :list:jar UP-TO-DATE
> Task :list:inspectClassesForKotlinIC UP-TO-DATE
> Task :subDir:utilities:processResources NO-SOURCE
> Task :subDir:utilities:classes UP-TO-DATE
> Task :subDir:utilities:jar UP-TO-DATE
> Task :subDir:utilities:inspectClassesForKotlinIC UP-TO-DATE
> Task :app:startScripts UP-TO-DATE
> Task :app:distTar UP-TO-DATE
> Task :app:distZip UP-TO-DATE
> Task :app:assemble UP-TO-DATE
> Task :app:compileTestKotlin UP-TO-DATE
> Task :app:compileTestJava NO-SOURCE
> Task :app:processTestResources NO-SOURCE
> Task :app:testClasses UP-TO-DATE
> Task :app:test UP-TO-DATE
> Task :app:check UP-TO-DATE
> Task :app:build UP-TO-DATE
> Task :list:assemble UP-TO-DATE
> Task :list:compileTestKotlin UP-TO-DATE
> Task :list:compileTestJava NO-SOURCE
> Task :list:processTestResources NO-SOURCE
> Task :list:testClasses UP-TO-DATE
> Task :list:test UP-TO-DATE
> Task :list:check UP-TO-DATE
> Task :list:build UP-TO-DATE
> Task :subDir:utilities:assemble UP-TO-DATE
> Task :subDir:utilities:compileTestKotlin NO-SOURCE
> Task :subDir:utilities:compileTestJava NO-SOURCE
> Task :subDir:utilities:processTestResources NO-SOURCE
> Task :subDir:utilities:testClasses UP-TO-DATE
> Task :subDir:utilities:test NO-SOURCE
> Task :subDir:utilities:check UP-TO-DATE
> Task :subDir:utilities:build UP-TO-DATE

BUILD SUCCESSFUL in 473ms
26 actionable tasks: 26 up-to-date
```

</details>



------------------------------------------------------
[Example from StackOverflow](https://stackoverflow.com/questions/48194556/use-gradle-sub-projects-with-kotlin-multiplatform)


## Related
- [[tech.tools.gradle.setup.multi-project-gradle.snippets.how-to-include-project-within-multi-project]]