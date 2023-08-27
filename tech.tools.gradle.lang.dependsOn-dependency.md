---
id: doaudeabgmy3rbie05htzqm
title: dependsOn-dependency
desc: ''
updated: 1677962375349
created: 1677962375349
---


```kts
tasks.register("hello") {
    doLast {
        println("Hello world!")
    }
}
tasks.register("task-depends-on-hello") {
    dependsOn("hello")
    doLast {
        println("I'm Gradle")
    }
}
```

## Command to reproduce:
```bash
gt.sandbox.checkout.commit edae3e8 \
&& cd "${GT_SANDBOX_REPO}/build_system/gradle/task_dependency_eg" \
&& cmd.run.announce "gradle -q task-depends-on-hello"
```

## Recorded output of command:
```
Hello world!
I'm Gradle
```

