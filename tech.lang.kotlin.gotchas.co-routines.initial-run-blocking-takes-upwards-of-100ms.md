---
id: e31x1mvbpd8u5vzghnhrnnv
title: Initial Run Blocking Takes Upwards of 100ms
desc: ''
updated: 1679770394089
created: 1679770394089
---

The initial switch to start using `runBlocking{}` takes upwards of 100ms

<details>
<summary>Code example</summary>

Look at code example in 
![[tech.lang.kotlin.gotchas.co-routines.co-routines-invocation-will-wait-for-it-to-finish-even-if-result-is-not-used-on-next-statement.example]]

And pay more attention to seconds elapsed of 86ms between a print in the main() and the first print in the main() function that is within runBlocking{}

```
[2023-03-25 11:52:12.540][main-1][86ms] 1st print within runBlocking{}
[2023-03-25 11:52:12.540][main-1][1ms] 2nd print within runBlocking{}
```

</details>
