---
id: 7pn1o9q31a1u7laaanybkva
title: task<Exec>
desc: ''
updated: 1677988393957
created: 1677988393957
---

Executes some external command.

<details>
<summary>Simple Exec task demo</summary>

## In Kotlin Script (.kts)

```kts
task<Exec>("myTask") {
    // configuration, sets the command line to later be executed.
    commandLine("echo", "Command line: Hello, world!")

    doFirst {
        println("doFirst: Hello, world!")
    }
    doLast {
        println("doLast: Goodbye, world!")
    }
}
```

Running:
```shell
./gradlew myTask
```

Output:
```
> Task :myTask
doFirst: Hello, world!
Command line: Hello, world!
doLast: Goodbye, world!
```

</details>

<details>
<summary>Configuration Stage Demo/commandLine over-write</summary>

```kts
task<Exec>("only-single-command-line-will-run"){
    // These two commandLine are meaningless since they will be overwritten, within
    // doFirst, by the commandLine in doFirst.
    //
    // The Exec task holds a single command line to run. commandLine does not
    // run the command, it sets the command line variable on the Exec instance.
    commandLine("echo", "configuration set echo-1")
    commandLine("echo", "configuration set echo-2")

    println("configuration-printl1")
    println("congiguration-printl2")

    doFirst {
        println("doFirst-printl")

        // This is the only commandLine that matters.
        commandLine("echo", "doFirst commandLine echo-1")
    }

    doLast {
        // doLast is executed after the task action has executed, so setting the
        // command line in here won't do anything useful.
        commandLine("echo", "doLast commandLine echo-1")

        println("doLast printl-1")
        println("doLast printl-2")
    }
}
```

## Command to reproduce:
```bash
gt.sandbox.checkout.commit b971e77 \
&& cd "${GT_SANDBOX_REPO}/build_system/gradle/example" \
&& cmd.run.announce "gradle only-single-command-line-will-run"
```

## Recorded output of command:
```

> Configure project :
configuration-printl1
congiguration-printl2

> Task :only-single-command-line-will-run
doFirst-printl
doFirst commandLine echo-1
doLast printl-1
doLast printl-2

BUILD SUCCESSFUL in 590ms
1 actionable task: 1 executed
```

</details>



<details>
<summary>Example running HelloWorld shell script</summary>


## Command to reproduce:
```bash
gt.sandbox.checkout.commit 9178a8b \
&& cd "${GT_SANDBOX_REPO}/build_system/gradle/example_shell_script_taskExec" \
&& cmd.run.announce "gradle runScript"
```

## Recorded output of command:
```

> Task :runScript
Hello from shell script.

BUILD SUCCESSFUL in 942ms
1 actionable task: 1 executed
```
</details>

<details>
<summary>afterEvaluate is in Configuration stage</summary>

## Command to reproduce:
```bash
gt.sandbox.checkout.commit 931385e \
&& cd "${GT_SANDBOX_REPO}/build_system/gradle/example" \
&& cmd.run.announce "gradle afterEvaluate-is-in-config-stage"
```

## Recorded output of command:
```

> Configure project :
configuration-printl1
congiguration-printl2
afterEvaluate-printl1

> Task :afterEvaluate-is-in-config-stage
doFirst-printl
commandLine-setBy-doFirst
doLast printl-1
doLast printl-2

BUILD SUCCESSFUL in 537ms
1 actionable task: 1 executed
```

</details>
