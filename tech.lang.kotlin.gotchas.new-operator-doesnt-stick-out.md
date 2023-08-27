---
id: t5a5onwhsfp9zivhazdushi
title: New Operator Doesnt Stick Out
desc: ''
updated: 1686979599729
created: 1686978381069
---

## Alignment on new usage
Firstly, lets align that we should [[tech.dev.best-practices.guidance.isolate-the-necessary-evil-of-new-operator]] to follow [[tech.dev.best-practices.principles.DIP-dependency-inversion-principle]].

## Kotlin hides new

Now let's talk about `new` operator in Kotlin.

`new` operator is still around there in kotlin, its just hidden away like a rogue that has cloaked itself away.

In java when you use new operator it sticks out at you with highlighted new operator.

![img](/assets/images/Screenshot_2023-06-16_at_10.14.48_PM.png){max-width: 400px, display: block, margin: 0 auto}

However, in Kotlin they decided it's not needed and the language can look cleaner without it. Well we are still creating new instances of objects, but now it doesn't stick out as much with default color schemas.


![img](/assets/images/Screenshot_2023-06-16_at_10.15.58_PM.png){max-width: 300px, display: block, margin: 0 auto}

With default color schema in Intellij the constructor call doesn't stick out at you anymore since the `new` operator is gone and the default color schema for Constructor is just inheriting from function call. Letting the constructor hide like a good old function call while its binding us to particular instance.

![img](/assets/images/Screenshot_2023-06-16_at_10.16.38_PM.png){max-width: 500px, display: block, margin: 0 auto}


We can try to modify the color schema, but that might be a bit too disruptive to how code looks like, given that things like `DescribeSpec` are constructors.

![img](/assets/images/Screenshot_2023-06-16_at_10.17.51_PM.png){max-width: 500px, display: block, margin: 0 auto}