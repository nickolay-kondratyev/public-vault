---
id: 170f23k9bebvsinf7r4myiu
title: time-milliseconds-of-a-block-of-code-measureTimeMillis
desc: ''
updated: 1687482995760
created: 1687482939191
---

```kotlin
measureTimeMillis()
```

Example:
```kotlin
  val millis = measureTimeMillis {
        val results = threader().runInParallel(
            listOf(
                SleepyCallableReturns1(5),
                SleepyCallableReturns1(5),
            )
        )

        results shouldBe listOf(1, 1)
    }
```