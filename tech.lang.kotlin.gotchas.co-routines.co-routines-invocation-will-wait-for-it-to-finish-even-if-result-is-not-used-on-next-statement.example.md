---
id: uferncopycsrdk9vig13sev
title: Example
desc: ''
updated: 1679771535116
created: 1679771535116
---

## Command to reproduce:
```bash
gt.sandbox.checkout.commit c93335f \
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
[2023-03-26 22:53:42.142][main-1][38ms] WarmUpStatement: Example showing main thread waiting for co-routine to finish before moving on to the next statement.
[2023-03-26 22:53:42.143][main-1][1ms] within main() before runBlocking {}
[2023-03-26 22:53:42.212][main-1][69ms] 1st print within runBlocking{}
[2023-03-26 22:53:42.212][main-1][0ms] 2nd print within runBlocking{}
[2023-03-26 22:53:42.227][DefaultDispatcher-worker-1-20][15ms] Within withContext{} (before sleep) input: 1st-request
[2023-03-26 22:53:42.747][main-1][520ms] print within main thread right after 1st-network request.
[2023-03-26 22:53:42.748][DefaultDispatcher-worker-1-20][1ms] Within withContext{} (before sleep) input: 2nd-request
[2023-03-26 22:53:43.249][main-1][501ms] MessageResultAfterBlockinOperation for [1st-request]
[2023-03-26 22:53:43.250][main-1][1ms] MessageResultAfterBlockinOperation for [2nd-request]
[2023-03-26 22:53:43.250][main-1][0ms] Total time taken: 1107ms

BUILD SUCCESSFUL in 1s
2 actionable tasks: 1 executed, 1 up-to-date
```
