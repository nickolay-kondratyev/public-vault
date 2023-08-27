---
id: ytc5e1c7isxixpvncbx5o4i
title: Avoid Statics but Allow Usage of Extension Methods
desc: ''
updated: 1686965660698
created: 1686964922284
---

Well here is a conundrum, that needs further reconciliation. I can easily get behind the idea of abandoning static methods like we do in Java. 

However, there are times where extension methods make your code so much neater that I don't want to give up extension method ability. 

Now extension methods is just syntax sugar on top of a static method. Therefore I am both stating that in most cases static methods should be abandoned and at the same time advocating the use of static methods, by means of extension methods.

Now when and what type of extension methods are allowed. 

A definition of rules needs to be put forth to keep extension methods sane, rather than making them into 
maintenance burden.

## Rule 1: No External State
Rule 1: extension methods should not hard code state into them. The extension method should not be hardcoding things like `/tmp` directory or any other state as such, they shall only use the state that is coming from the object or collection of objects that they are operating on.

## Rule 2: No External Side Effects.
As a hard rule the extension method shall not interact with some external static classes making side effects. 

(Logging can be an exception to this)

Extension methods should not have unintended consequences outside of their own execution scope. This aids in keeping them clean, easy to understand, and predictable.


