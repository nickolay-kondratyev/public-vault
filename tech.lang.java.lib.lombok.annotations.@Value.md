---
id: cavzbhk9iw3cs48q0a13zr6
title: Lombok's @Value
desc: ''
updated: 1668782190214
created: 1668205874114
---

https://projectlombok.org/features/Value

> `@Value` is the immutable variant of `@Data`; all fields are made private and final by default, and setters are not generated. The class itself is also made final by default, because immutability is not something that can be forced onto a subclass. Like `@Data`, useful toString(), equals() and hashCode() methods are also generated, each field gets a getter method, and a constructor that covers every argument (except final fields that are initialized in the field declaration) is also generated.

## Testing
Note from the description of value:

>  The class itself is also made final by default

Out of the box Mockito doesn't allow mocking finals. However, there is a straight forward way to get finals to Mock finals with mockito [[tech.lang.java.lib.mockito-how-to.mock-final-class]]