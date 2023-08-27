---
id: dj6nlh442fy10q6kjmqfek1
title: Program to an Interface Not to Implementation
desc: ''
updated: 1679800652569
created: 1679800652569
---

To follow this well you should be using interfaces. 

You should start by creating an interface and writing out how you want the interface to look like without being bogged down by implementation details yet. 

Even when it seems like the interface is not needed yet and there will be just one implementation, creating an interface switches our mind into a different mindset. 

Creating an interface forces us to scope down what the object is allowed to do. 

Creating an interfaces makes it easy to see what is the object allowed to do. 

Creating an interface makes it more likely that some javadoc documentation is written.

<details>
<summary>However, Sometimes POJOs is all you need.</summary>

There is some cost to creation of the interface. Not just in a manner of creating initially (hint: lower this cost by using intellij `extract interface` functionality to speed up creation of interfaces from classes that already exist). But more so later to hop from interface down to implementation. 

Hence, at times it makes sense just to create a data object holding data without making an interface to it for the sake of [[tech.dev.best-practices.principles.KISS]]. 
</details>

This is largely related to [[tech.dev.best-practices.principles.DIP-dependency-inversion-principle]]