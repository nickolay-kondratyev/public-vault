---
id: 3skxdwxe3ld9ynnxmeooi2c
title: Extension Methods
desc: ''
updated: 1682889765107
created: 1682888913670
---

```kotlin
// Extension method
fun Student.getAge(): String {
    return this.getName() + " is 20 years old"
}

// Class being extended
class Student {
    fun getName(): String {
        return "John Doe"
    }
}

// Usage
fun main() {
    val student = Student()

    print(student.getAge())
}
```

<details>
<summary>Reproducible Code Example</summary>

## Command to reproduce:
```bash
gt.sandbox.checkout.commit 9d495a9 \
&& cd "${GT_SANDBOX_REPO}/gt-kotlin-sandbox" \
&& cmd.run.announce "gradle run"
```

## Recorded output of command:
```
> Task :app:compileKotlin UP-TO-DATE
> Task :app:compileJava NO-SOURCE
> Task :app:processResources NO-SOURCE
> Task :app:classes UP-TO-DATE

> Task :app:run
John Doe is 20 years old
Deprecated Gradle features were used in this build, making it incompatible with Gradle 9.0.

You can use '--warning-mode all' to show the individual deprecation warnings and determine if they come from your own scripts or plugins.

See https://docs.gradle.org/8.1.1/userguide/command_line_interface.html#sec:command_line_warnings

BUILD SUCCESSFUL in 432ms
2 actionable tasks: 1 executed, 1 up-to-date
```
</details>
