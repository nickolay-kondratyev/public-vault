---
id: 3dgux2ejdd4wtx3a4bb4gbv
title: Recursive Functions Should Be Static
desc: ''
updated: 1691259056847
created: 1691258968830
---

In typical cases recursive functions should be static, so that we don't accidentally take the state from the wrong instance of the object.

Having the function be static prevents it from accidentally grabbing an instance variable from an object at different level of recursion. 