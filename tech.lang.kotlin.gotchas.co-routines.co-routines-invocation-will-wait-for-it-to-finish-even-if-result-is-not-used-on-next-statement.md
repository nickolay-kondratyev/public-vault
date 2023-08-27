---
id: 6wwfoc349e4qegm8dvbizq9
title: >-
  Co routines invocations will wait for the background thread to finish even if
  result is not used right away.
desc: ''
updated: 1679770739870
created: 1679770739870
---

To me co-routines resembled async/await by their description. Hence I expected the thread that is calling the co-routine to be able to keep going if the result of the thread is not used yet. However, Thus far it when I used just plain co-routine function from `main`, `main` would hand off work to the background thread and then wait for the background thread to finish before proceeding to the next step. 


<details>
<summary>Code Example using plain co-routine</summary>

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
        val result1 = performLongRequest("1st-request")
        ThreadUtils.printWithThreadInfo("print within main thread right after 1st-network request.")
        val result2 = performLongRequest("2nd-request")
        ThreadUtils.printWithThreadInfo(result1)
        ThreadUtils.printWithThreadInfo(result2)
        ThreadUtils.printWithThreadInfo(
            "Total time taken: " +
                    (System.currentTimeMillis() - mainMillisStamp) + "ms")
    }
}
```

## Command to reproduce:
```bash
gt.sandbox.checkout.commit df593bf \
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
[2023-03-27 07:14:35.791][main-1][36ms] WarmUpStatement: Example showing main thread waiting for co-routine to finish before moving on to the next statement.
[2023-03-27 07:14:35.791][main-1][0ms] within main() before runBlocking {}
[2023-03-27 07:14:35.849][main-1][58ms] 1st print within runBlocking{}
[2023-03-27 07:14:35.849][main-1][0ms] 2nd print within runBlocking{}
[2023-03-27 07:14:35.863][DefaultDispatcher-worker-1-20][14ms] Within withContext{} (before sleep) input: 1st-request
[2023-03-27 07:14:36.381][main-1][518ms] print within main thread right after 1st-network request.
[2023-03-27 07:14:36.381][DefaultDispatcher-worker-1-20][0ms] Within withContext{} (before sleep) input: 2nd-request
[2023-03-27 07:14:36.886][main-1][505ms] MessageResultAfterBlockingOperation for [1st-request]
[2023-03-27 07:14:36.886][main-1][1ms] MessageResultAfterBlockingOperation for [2nd-request]
[2023-03-27 07:14:36.887][main-1][0ms] Total time taken: 1096ms

BUILD SUCCESSFUL in 1s
2 actionable tasks: 1 executed, 1 up-to-date
```

</details>

------

Adding async/await allows us to execute the requests without blocking. 

<details>
<summary>Code Example as above but with async/await.</summary>

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




