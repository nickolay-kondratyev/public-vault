---
id: wz9i8gnhdvxl4x6rneppam0
title: Benchmarking against Thread Pool
desc: ''
updated: 1686883801567
created: 1686883693492
---


<details>
<summary>Kotlin Code example</summary>

```kotlin
package com.asgard.sandbox

import com.asgard.core.out.Out
import kotlinx.coroutines.coroutineScope
import kotlinx.coroutines.*
import java.util.concurrent.ForkJoinPool
import java.util.concurrent.TimeUnit
import kotlin.system.measureTimeMillis

class BenchmarkOfDifferentThreadingOptions(private val out: Out) {

    companion object {
        const val LOOP_COUNT = 100000
        const val BATCH_SIZE = 100
    }

    val threadCounter = mutableMapOf<String, MutableSet<String>>()

    fun cpuLoadTask(caseString: String) {
        if (!threadCounter.containsKey(caseString)) {
            threadCounter[caseString] = mutableSetOf()
        }
        val set = threadCounter[caseString]!!
        set.add(Thread.currentThread().id.toString())

        for (i in 0 until 1000) {

            Math.pow(3.0, 3.0)
        }
    }

    /** Case one just going to loop.  */
    private fun case1_noThreading() {
        for (i in 0 until LOOP_COUNT) {
            cpuLoadTask("case1_noThreading")
        }
    }

    suspend fun case2_coroutineTask_noAsync() {
        for (i in 0 until LOOP_COUNT) {
            coroutineScope {
                cpuLoadTask("case2_coroutineTask_noAsync")
            }
        }
    }

    suspend fun case3_coroutineThatHaveBatchesSentToIT_NoAsync() {
        for (i in 0 until (LOOP_COUNT / BATCH_SIZE)) {
            coroutineScope {
                for (j in 0 until BATCH_SIZE) {
                    cpuLoadTask("case3_coroutineThatHaveBatchesSentToIT_NoAsync")
                }
            }
        }
    }

    var threadPool = ForkJoinPool(Runtime.getRuntime().availableProcessors())

    fun initThreadPool() {
        threadPool = ForkJoinPool(Runtime.getRuntime().availableProcessors())
    }

    fun case4_threadingWithThreadPool() {

        for (i in 0 until LOOP_COUNT) {
            threadPool.execute { cpuLoadTask("case4_threadingWithThreadPool") }
        }
        waitForThreadPoolTasksToFinish()
    }

    fun case5_threadingWithBatchesSentToThreadPool() {


        for (i in 0 until (LOOP_COUNT / BATCH_SIZE)) {
            threadPool.execute {
                for (j in 0 until BATCH_SIZE) {
                    cpuLoadTask("case5_threadingWithBatchesSentToThreadPool")
                }
            }
        }
        waitForThreadPoolTasksToFinish()
    }


    private fun waitForThreadPoolTasksToFinish() {
        threadPool.shutdown()
        threadPool.awaitTermination(100, TimeUnit.SECONDS)
    }


    fun case6a_threadingWithDefaultParallelStreams() {
        (0 until LOOP_COUNT).toList()
            .parallelStream()
            .forEach { cpuLoadTask("case6a_threadingWithDefaultParallelStreams") }
    }

    /** Initializing outside the function for initialization of thread pool
     * to not affect our timing. */
    private val case6ThreadPoolWithDoubledThreads =
        ForkJoinPool(Runtime.getRuntime().availableProcessors() * 2)

    fun case6b_threadingWithCustomThreadPoolWithDoubleThreadsOfProcessors() {

        case6ThreadPoolWithDoubledThreads.submit {
            (0 until LOOP_COUNT).toList()
                .parallelStream()
                .forEach {
                    cpuLoadTask("case6b_threadingWithCustomThreadPoolWithDoubleThreadsOfProcessors")
                }
        }.get() // get() will ensure the main thread waits for the task to complete
    }

    // WHY is 7a still has a single thread id?
    suspend fun case7a_coroutineTask_WithAsync() =
        coroutineScope {
            val tasks = List(LOOP_COUNT) {
                async {
                    cpuLoadTask("case7a_coroutineTask_WithAsync")
                }
            }

            tasks.forEach { it.await() }
        }

    suspend fun case7b_coroutineDispatchersIO_withAsync() {
        coroutineScope {
            val tasks = List(LOOP_COUNT) {
                async(Dispatchers.IO) {
                    cpuLoadTask("case7b_coroutineDispatchersIO_withAsync")
                }
            }

            tasks.forEach { it.await() }
        }
    }

    suspend fun case8_coroutineDispatchersIO_BatchesSentToIt_withAsync() {
        coroutineScope {
            val tasks = List(LOOP_COUNT / BATCH_SIZE) {
                async(Dispatchers.IO) {
                    for (j in 0 until BATCH_SIZE) {
                        cpuLoadTask("case8_coroutineDispatchersIO_BatchesSentToIt_withAsync")
                    }
                }
            }
            tasks.forEach { it.await() }
        }
    }


    /** There are multiple cases we want to compare
     * 1) no threading.
     *
     * 2) co-routines (without async usage).
     * 3) batched co-routines (without async usage).
     *
     * 4) threading with java thread pool.
     * 5) threading with java batched thread pool.
     * 6) threading with parallel streams.
     *
     * 7a) co-routines (with async usage)
     * 7b) co-routines with dispatcher IO (with async usage):
     *
     * 8) co-routines with dispatcher IO, batches of work (with async usage):
     *
     * By batches of work I mean instead of invoking a new thread per a single function
     * call we will invoke a thread to process some batch of function calls.
     *
     * The method that we will use will go as follows.
     *
     * We will create a function that will execute a loop of a given number of times,
     * to simulate a CPU heavy workload and prevent and disk caching from affecting
     * our benchmarking.
     *
     * Then we will run this function a million times through the different scenarios
     * described above, timing how long it took using milliseconds.
     *
     * The goal is to find out which threading option is the fastest.
     * */
    fun go() {
        out.info("--------------------------------------------------------------------------------")

        out.info("Starting benchmark of different threading options.")
        out.info(
            "1) no threading time: " +
                    "${measureTimeMillis { case1_noThreading() }} ms"
        )

        out.info(
            "2) co-routines (without async usage): " +
                    "${measureTimeMillis { runBlocking { case2_coroutineTask_noAsync() } }} ms"
        )


        out.info(
            "3) co-routines that have batches sent to it (without async usage): " +
                    "${measureTimeMillis { runBlocking { case3_coroutineThatHaveBatchesSentToIT_NoAsync() } }} ms"
        )

        initThreadPool()
        out.info(
            "4) threading with thread pool: " +
                    "${measureTimeMillis { case4_threadingWithThreadPool() }} ms"
        )

        initThreadPool()
        out.info(
            "5) threading with batches sent to thread pool: " +
                    "${measureTimeMillis { case5_threadingWithBatchesSentToThreadPool() }} ms"
        )

        out.info(
            "6a) threading with default parallel streams: " +
                    "${measureTimeMillis { runBlocking { case6a_threadingWithDefaultParallelStreams() } }} ms"
        )

        out.info(
            "6a) threading with custom parallel streams that have double the default thread count (double processor count): " +
                    "${measureTimeMillis { runBlocking { case6b_threadingWithCustomThreadPoolWithDoubleThreadsOfProcessors() } }} ms"
        )

        out.info(
            "7a) co-routines (with async usage): " +
                    "${measureTimeMillis { runBlocking { case7a_coroutineTask_WithAsync() } }} ms"
        )

        out.info(
            "7b) co-routines with dispatcher IO (with async usage): " +
                    "${measureTimeMillis { runBlocking { case7b_coroutineDispatchersIO_withAsync() } }} ms"
        )

        out.info(
            "8) co-routines with dispatcher IO, batches of work (with async usage): " +
                    "${measureTimeMillis { runBlocking { case8_coroutineDispatchersIO_BatchesSentToIt_withAsync() } }} ms"
        )

        out.info("--------------------------------------------------------------------------------")
        printAsJson(threadCounter)
    }


    private fun printAsJson(threadCounter: MutableMap<String, MutableSet<String>>) {
        threadCounter.keys.forEach() { key ->
            out.info("$key used ${threadCounter[key]?.size} threads.")
        }
    }
}
```
</details>


<details>
<summary>Output:</summary>

```txt
[INFO] Starting benchmark of different threading options. []
[INFO] 1) no threading time: 3232 ms []
[INFO] 2) co-routines (without async usage): 3276 ms []
[INFO] 3) co-routines that have batches sent to it (without async usage): 3288 ms []
[INFO] 4) threading with thread pool: 579 ms []
[INFO] 5) threading with batches sent to thread pool: 558 ms []
[INFO] 6a) threading with default parallel streams: 584 ms []
[INFO] 6a) threading with custom parallel streams that have double the default thread count (double processor count): 565 ms []
[INFO] 7a) co-routines (with async usage): 3551 ms []
[INFO] 7b) co-routines with dispatcher IO (with async usage): 814 ms []
[INFO] 8) co-routines with dispatcher IO, batches of work (with async usage): 558 ms []
[INFO] -------------------------------------------------------------------------------- []
[INFO] case1_noThreading used 1 threads. []
[INFO] case2_coroutineTask_noAsync used 1 threads. []
[INFO] case3_coroutineThatHaveBatchesSentToIT_NoAsync used 1 threads. []
[INFO] case4_threadingWithThreadPool used 10 threads. []
[INFO] case5_threadingWithBatchesSentToThreadPool used 9 threads. []
[INFO] case6a_threadingWithDefaultParallelStreams used 10 threads. []
[INFO] case6b_threadingWithCustomThreadPoolWithDoubleThreadsOfProcessors used 20 threads. []
[INFO] case7a_coroutineTask_WithAsync used 1 threads. []
[INFO] case7b_coroutineDispatchersIO_withAsync used 78 threads. []
[INFO] case8_coroutineDispatchersIO_BatchesSentToIt_withAsync used 64 threads. []
```
</details>


<details>
<summary>ChatGPT Answer: why is case 7a not using more than 1 thread</summary>


In the case7a_coroutineTask_WithAsync, you are using the async function within a coroutine, but you are not specifying a particular dispatcher for it to use. In Kotlin, when you use async (or launch, runBlocking, etc.) without specifying a dispatcher, it uses the Dispatchers.Default dispatcher.

The Dispatchers.Default dispatcher is backed by a shared pool of threads on the JVM. So, when using async in a coroutine without specifying the dispatcher, the coroutine will run on one of these shared pool threads, potentially reusing the same thread for multiple coroutines if the operations are suspendable. This is why you see only one thread being used in this case.

The reason that your coroutines in case7a_coroutineTask_WithAsync are all running on the same thread is likely because each coroutine's work is relatively short and doesn't block the thread for a long time, allowing the next coroutine to use the same thread almost immediately.

The execution of your async coroutines is likely overlapping, but the work they are doing is so short that by the time the next coroutine starts, the previous one has already finished and freed up the thread.

To truly get parallelism with coroutines, you would need to use a dispatcher that provides multiple threads, like Dispatchers.IO as you have used in case7b_coroutineDispatchersIO_withAsync. The Dispatchers.IO dispatcher is designed for offloading blocking IO tasks to a shared pool of on-demand created threads.

In short, the coroutine context defines the thread that is used, and if you don't specify one using a dispatcher, the default one used can end up running all your tasks on the same thread if they are short enough.
</details>
