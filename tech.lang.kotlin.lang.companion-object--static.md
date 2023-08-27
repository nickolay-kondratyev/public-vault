---
id: ck9evh5s16f9mi57qnf8av8
title: Companion Object  Static
desc: ''
updated: 1679766188905
created: 1679766188905
---

Very similar to `static` in java.

```kotlin
class MyClass {
    companion object {
        fun myStaticMethod() {
            // implementation here
        }
    }
}
```


<details>
<summary>Differences between statics #chatgpt</summary>


*   Access control: Companion object members have the same visibility as regular class members, whereas static members in Java can be accessed from anywhere in the same package or even outside the package if they are public.
    
*   Polymorphism: Companion objects can implement interfaces, which allows you to define static methods that conform to an interface. In Java, you would have to define the same static method separately for each class.
    
*   Name: In Kotlin, you can give the companion object a custom name instead of relying on the default `Companion` name.
    
*   Extension Functions: In Kotlin, you can define extension functions for companion objects.
    
*   Object Expressions: In Kotlin, you can create anonymous objects (called object expressions) that can extend a class or implement an interface. You can define properties and methods for these objects, and they behave like companion objects in that they are associated with the class they extend or implement.
    
*   Initialization: In Kotlin, a companion object can be initialized just like a regular object. In Java, static fields and methods are not associated with a specific instance of the class and cannot be initialized in the same way.
    
*   Inheritance: Companion objects can be inherited from parent classes or interfaces, just like regular classes or objects. In Java, static fields and methods are not inherited and cannot be overridden.
    
*   Visibility from Java: If you want to access a companion object from Java code, you need to use the `@JvmStatic` annotation to mark the companion object's members as static. This is because Java doesn't have the concept of companion objects, so they need to be compiled into static fields and methods that Java can understand.
    

</details>
