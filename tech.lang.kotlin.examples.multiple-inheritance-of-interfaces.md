---
id: woy6biu5kpce6sw11ywot1d
title: Multiple Inheritance of Interfaces
desc: ''
updated: 1682722028380
created: 1682722028380
---

## Code
<details>
<summary>Code example</summary>

```kotlin
interface A {
    fun foo()
}

interface B {
    fun bar()
}

interface C : A, B

fun example(c: C) {
    c.foo()
    c.bar()
}

fun main() {
    example(object : C {
        override fun foo() {
            println("foo")
        }

        override fun bar() {
            println("bar")
        }
    })
}
```
</details>

## Command to reproduce:
```bash
gt.sandbox.checkout.commit b9ff972 \
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
foo
bar

BUILD SUCCESSFUL in 808ms
2 actionable tasks: 1 executed, 1 up-to-date
```