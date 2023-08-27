---
id: b53lpjedhkhznyo3vj8yb58
title: Hello world Test Describe Spec Example
desc: ''
updated: 1681701424008
created: 1681701424008
---

## Gradle changes
<details>
<summary>Gradle changes</summary>

```kts
    val kotestVersion = "4.6.3"
    implementation("io.kotest:kotest-framework-engine:$kotestVersion")
    implementation("io.kotest:kotest-assertions-core:$kotestVersion")
    implementation("io.kotest:kotest-runner-junit5:$kotestVersion")
```
</details>


## Code
<details>
<summary>Code</summary>


```kotlin
import io.kotest.core.spec.style.DescribeSpec
import io.kotest.matchers.ints.shouldBeExactly
import io.kotest.matchers.shouldBe

// Test using one of Kotest DSLs.
class HelloKotestTestWorld: DescribeSpec({
    describe("WHEN I land on earth") {
        it("TRUE should be true") {
            true shouldBe true
        }

        describe("AND if I am doing math") {
            val result = 5

            it("THEN 5 should be equal to 3+2") {
                result shouldBeExactly 3 + 2
            }
        }
    }
})

```
</details>
