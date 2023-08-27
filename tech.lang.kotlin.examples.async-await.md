---
id: oyu6ku4d2arr78x7psnijti
title: Async Await
desc: ''
updated: 1679846151837
created: 1679846151837
---

It is quite interesting that the async/await can still run on the same thread, but does not block the thread

<details>
<summary>Code Example: async/await running on main thread</summary>

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {

    val mainMillisStamp = System.currentTimeMillis()

    val promise1 = async {
        ThreadUtils.printWithThreadInfo("print within 1st async {}")
        delay(500L) // simulate some long-running computation
        ThreadUtils.printWithThreadInfo("print after sleep 1st async {}")
        "1st async result"
    }

    val promise2 = async {
        ThreadUtils.printWithThreadInfo("print after sleep 2nd async {}")
        delay(500L)
        ThreadUtils.printWithThreadInfo("print after sleep 2nd async {}")
        // e some long-running computation
        "2nd async result"
    }

    println(promise1.await())
    println(promise2.await())

    println("Elapsed time: ${System.currentTimeMillis() - mainMillisStamp} ms")
}
```

## Command to reproduce:
```bash
gt.sandbox.checkout.commit 5b041d8 \
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
[2023-03-27 06:51:37.374][main-1][29ms] print within 1st async {}
[2023-03-27 06:51:37.376][main-1][2ms] print after sleep 2nd async {}
[2023-03-27 06:51:37.879][main-1][503ms] print after sleep 1st async {}
[2023-03-27 06:51:37.881][main-1][2ms] print after sleep 2nd async {}
1st async result
2nd async result
Elapsed time: 544 ms

BUILD SUCCESSFUL in 1s
2 actionable tasks: 1 executed, 1 up-to-date
```

</details>



<details>
<summary>Code Example: async/await running on background thread.</summary>

```kotlin

import kotlinx.coroutines.*


suspend fun performLongRequest(msg:String): String {
    return withContext(Dispatchers.IO) {
        ThreadUtils.printWithThreadInfo("Within withContext{} (before sleep) input: " + msg)
        ThreadUtils.sleep(500)

        String.format("MessageResultAfterBlockingOperation for [%s]", msg)
    }
}

fun main() {

    ThreadUtils.printWithThreadInfo("WarmUpStatement: Example showing main thread waiting for co-routine to finish before moving on to the next statement.")

    val mainMillisStamp=System.currentTimeMillis();

    ThreadUtils.printWithThreadInfo("within main() before runBlocking {}")

    runBlocking {
        ThreadUtils.printWithThreadInfo("1st print within runBlocking{}")
        ThreadUtils.printWithThreadInfo("2nd print within runBlocking{}")

        val promise1 = async { performLongRequest("1st-request")}
        ThreadUtils.printWithThreadInfo("print within main thread right after 1st-network request.")
        val promise2 = async {performLongRequest("2nd-request")}

        ThreadUtils.printWithThreadInfo(promise1.await())
        ThreadUtils.printWithThreadInfo(promise2.await())
        ThreadUtils.printWithThreadInfo(
            "Total time taken: " +
                    (System.currentTimeMillis() - mainMillisStamp) + "ms")
    }
}
```
## Command to reproduce:
```bash
gt.sandbox.checkout.commit 480ae13 \
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
[2023-03-27 07:17:54.235][main-1][35ms] WarmUpStatement: Example showing main thread waiting for co-routine to finish before moving on to the next statement.
[2023-03-27 07:17:54.236][main-1][1ms] within main() before runBlocking {}
[2023-03-27 07:17:54.301][main-1][65ms] 1st print within runBlocking{}
[2023-03-27 07:17:54.301][main-1][0ms] 2nd print within runBlocking{}
[2023-03-27 07:17:54.303][main-1][2ms] print within main thread right after 1st-network request.
[2023-03-27 07:17:54.322][DefaultDispatcher-worker-1-20][19ms] Within withContext{} (before sleep) input: 1st-request
[2023-03-27 07:17:54.322][DefaultDispatcher-worker-2-21][0ms] Within withContext{} (before sleep) input: 2nd-request
[2023-03-27 07:17:54.841][main-1][519ms] MessageResultAfterBlockingOperation for [1st-request]
[2023-03-27 07:17:54.841][main-1][0ms] MessageResultAfterBlockingOperation for [2nd-request]
[2023-03-27 07:17:54.841][main-1][0ms] Total time taken: 605ms

BUILD SUCCESSFUL in 1s
2 actionable tasks: 1 executed, 1 up-to-date
```

</details>




