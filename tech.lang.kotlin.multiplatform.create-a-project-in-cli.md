---
id: dga5des0okfyhz1xu92zwew
title: Create a Project in CLI
desc: ''
updated: 1679250083233
created: 1679250083233
---

### ChatGpt Approach
<details>
<summary>ChatGPT4 approach</summary>

> Is there a command line way to generate kotlin multiplatform library, so its more setup out of the box? 

#chatgpt4: Yes, you can create a Kotlin Multiplatform Library using the command line with the help of the `kotlin-multiplatform` Gradle plugin. Here's how to do it:

1.  Make sure you have JDK 1.8 or later, Gradle 6.0 or later, and Kotlin CLI tools installed on your system.
    
2.  Create a new directory for your project and navigate to it in the terminal or command prompt:
    

bash

```bash
mkdir MyMultiplatformLibrary
cd MyMultiplatformLibrary
```

3.  Create a `settings.gradle.kts` file to set up the project:

bash

```bash
touch settings.gradle.kts
```

Add the following content to `settings.gradle.kts`:

kotlin

```kotlin
rootProject.name = "MyMultiplatformLibrary"
```

4.  Create a `build.gradle.kts` file to set up the build configuration:

bash

```bash
touch build.gradle.kts
```

Add the following content to `build.gradle.kts`:

kotlin

```kotlin
plugins {
    kotlin("multiplatform") version "1.6.0"
}

group = "com.example"
version = "1.0.0"

kotlin {
    /* Targets */
    jvm()
    js {
        browser()
    }
    ios()

    /* Source Sets */
    sourceSets {
        val commonMain by getting {
            dependencies {
                implementation(kotlin("stdlib-common"))
            }
        }

        val commonTest by getting {
            dependencies {
                implementation(kotlin("test-common"))
                implementation(kotlin("test-annotations-common"))
            }
        }

        val jvmMain by getting {
            dependencies {
                implementation(kotlin("stdlib-jdk8"))
            }
        }

        val jvmTest by getting {
            dependencies {
                implementation(kotlin("test-junit"))
            }
        }

        val jsMain by getting {
            dependencies {
                implementation(kotlin("stdlib-js"))
            }
        }

        val jsTest by getting {
            dependencies {
                implementation(kotlin("test-js"))
            }
        }

        val iosMain by getting
        val iosTest by getting
    }
}
```

5.  Create the source directories for the common and platform-specific code:

bash

```bash
mkdir -p src/commonMain/kotlin \
&& mkdir -p src/commonTest/kotlin \
&& mkdir -p src/jvmMain/kotlin \
&& mkdir -p src/jvmTest/kotlin \
&& mkdir -p src/jsMain/kotlin \
&& mkdir -p src/jsTest/kotlin \
&& mkdir -p src/iosMain/kotlin \
&& mkdir -p src/iosTest/kotlin \
&& echo 'done with dir creation'
```

6.  Now you can add your common and platform-specific Kotlin code to the respective source directories.
    
7.  Build the project using the command:
    

bash

```bash
./gradlew build
```

With this approach, you've created a Kotlin Multiplatform Library project from the command line. You can now edit the source code and build configurations using a text editor or an IDE like IntelliJ IDEA or Android Studio.

------------------------------------------------------
Will also need kotlin gradle git ignore
[[tech.lang.kotlin.multiplatform.gitignore]]

------------------------------------------------------

Note also had to remove the js related build target and add maven repository to get gradle to build.


```
--- a/MyMultiplatformLibrary/build.gradle.kts
+++ b/MyMultiplatformLibrary/build.gradle.kts
@@ -7,10 +7,11 @@ version = "1.0.0"

 kotlin {
     /* Targets */
-    jvm()
-    js {
-        browser()
+    repositories {
+        mavenCentral()
     }
+
+    jvm()
     ios()

     /* Source Sets */
@@ -40,18 +41,6 @@ kotlin {
             }
         }

-        val jsMain by getting {
-            dependencies {
-                implementation(kotlin("stdlib-js"))
-            }
-        }
-
-        val jsTest by getting {
-            dependencies {
-                implementation(kotlin("test-js"))
-            }
-        }
-
```
</details>

### Sandbox Replication

<details>
<summary>Sandbox Replication (Builds without source files)</summary>

## Command to reproduce:
Builds without source files:
```bash
gt.sandbox.checkout.commit b387a31 \
&& cd "${GT_SANDBOX_REPO}/MyMultiplatformLibrary" \
&& cmd.run.announce "gradle build"
```

## Recorded output of command:
```

> Configure project :
Kotlin Multiplatform Projects are an Alpha feature. See: https://kotlinlang.org/docs/reference/evolution/components-stability.html. To hide this message, add 'kotlin.mpp.stability.nowarn=true' to the Gradle properties.


> Task :compileKotlinIosArm64 NO-SOURCE
> Task :compileKotlinIosX64 NO-SOURCE
> Task :compileKotlinJvm NO-SOURCE
> Task :jvmProcessResources NO-SOURCE
> Task :jvmMainClasses UP-TO-DATE
> Task :jvmJar UP-TO-DATE
> Task :compileKotlinMetadata NO-SOURCE
> Task :metadataMainClasses UP-TO-DATE
> Task :metadataJar UP-TO-DATE
> Task :assemble UP-TO-DATE
> Task :iosX64ProcessResources NO-SOURCE
> Task :iosX64MainKlibrary UP-TO-DATE
> Task :compileTestKotlinIosX64 NO-SOURCE
> Task :linkDebugTestIosX64 NO-SOURCE
> Task :iosX64Test SKIPPED
> Task :compileTestKotlinJvm NO-SOURCE
> Task :jvmTestProcessResources NO-SOURCE
> Task :jvmTestClasses UP-TO-DATE
> Task :jvmTest NO-SOURCE
> Task :allTests UP-TO-DATE
> Task :check UP-TO-DATE
> Task :build UP-TO-DATE

Deprecated Gradle features were used in this build, making it incompatible with Gradle 8.0.

You can use '--warning-mode all' to show the individual deprecation warnings and determine if they come from your own scripts or plugins.

See https://docs.gradle.org/7.6/userguide/command_line_interface.html#sec:command_line_warnings

BUILD SUCCESSFUL in 696ms
3 actionable tasks: 3 up-to-date
```


</details>
