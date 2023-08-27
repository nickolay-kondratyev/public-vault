---
id: qanytiitsbhfydgxfkcgi0i
title: Configuration
desc: ''
updated: 1678066862048
created: 1678066862048
---
> Q: Do configuration stage of all task get executed.
> 
> A: Yes, during the configuration phase of the Gradle build, the configuration blocks of all tasks and other components defined in the build script are executed, regardless of whether they are included in the task graph for execution.
The configuration phase is used to determine the relationships between tasks, set up inputs and outputs for tasks, define properties and settings, and perform other actions needed to prepare for the execution phase. #chatgpt

## .kts
```kts
task("hello") {
    println("hello config stage")

    doLast {
        println("Executing hello task")
    }
}
```