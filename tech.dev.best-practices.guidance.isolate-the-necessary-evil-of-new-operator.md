---
id: j0fvvyah9qzsned0dmbmqrd
title: Isolate the Necessary Evil of New Operator
desc: ''
updated: 1686979344732
created: 1686977755957
---

In [[_.oop]] `new` operator creates new instances of some class. 

`new` operator is the necessary evil within [[_.oop]]. 

Why is it evil? Because: It violates the [[tech.dev.best-practices.principles.DIP-dependency-inversion-principle]] since it binds us not just to a particular class implementation of an interface. Worse off it binds us to particular instantiation of a class. We should isolate it from being spread around in the code, since it ties us to particular implementation.

[[_.IoC-DI-container]] can greatly help with centralizing all the instance creations to a single area within the DI container realm. However, in liu of DI container we should still be diligent of centralizing away the creation of objects away from the places where the objects are used.

[[tech.design-pattern.factory]]
