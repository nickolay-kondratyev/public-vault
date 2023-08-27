---
id: l7lozxe1dj0gdtl0g4zil39
title: DescribeSpec
desc: ''
updated: 1691267049373
created: 1691266803829
---

## Describe runs once:
```kotlin
var counter = 0

class DescribeSpecExample : DescribeSpec({

    describe("Counter example for DescribeSpec") {
        counter++
        println("Counter in describe: $counter")

        it("First IT block") {
            println("Counter in First IT: $counter")
        }

        it("Second IT block") {
            println("Counter in Second IT: $counter")
        }

        describe("Nested Describe") {
            it("Nested IT block") {
                println("Counter in Nested IT: $counter")
            }
        }
    }
})
```
In above example `counter` will always be 1

## If you want code to execute per it() use beforeTest

```kotlin
var counter = 0

class DescribeSpecExample : DescribeSpec({

    describe("Counter example for DescribeSpec") {
        beforeTest {
            counter++
        }

        println("Counter in outer describe: $counter")

        it("First IT block") {
            println("Counter in First IT: $counter")
        }

        it("Second IT block") {
            println("Counter in Second IT: $counter")
        }

        describe("Nested Describe") {
            println("Counter in nested describe: $counter")

            it("Nested IT block-1") {
                println("Counter in Nested IT-1: $counter")
            }

            it("Nested IT block") {
                println("Counter in Nested IT-2: $counter")
            }
        }
    }
})
```

```txt
Counter in outer describe: 0
Counter in First IT: 1
Counter in Second IT: 2
Counter in nested describe: 3
Counter in Nested IT-1: 4
Counter in Nested IT-2: 5
```