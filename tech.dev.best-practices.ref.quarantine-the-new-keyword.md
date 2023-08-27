---
id: vybnfa9assgwzeh3910e6d0
title: Quarantine the New Keyword
desc: ''
updated: 1679801566614
created: 1679801566614
---

The new keyword is at times a necessarily evil even in the modern OOP langauges. We can't always have just interfaces. We need to have real implementations come from somewhere. However, a good vocabulary for new keyword is to quarantine it. It's best to use interface factories (not `static getObjectX` factory), such that later you can vary the implementation that gets created for your 

## Relationships:
- [[rel.highly-related-to]]:**[[tech.dev.best-practices.ref.program-to-an-interface-not-to-implementation]]**
- [[rel.highly-related-to]]:**[[tech.dev.best-practices.principles.DIP-dependency-inversion-principle]]**

