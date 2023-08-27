---
id: 0i68ba39n3sby0uwac63yzc
title: Gradle
desc: ''
updated: 1692978562765
created: 1673126925099
---

> Gradle is an example of dependency based programming: you define tasks and dependencies between tasks. Gradle guarantees that these tasks execute in the order of their dependencies.

## Build commands
Default build
```shell
./gradlew build
```
Build without tests
```shell
./gradlew build -x test
```

## Reference
- [Build Script Basics](https://docs.gradle.org/current/userguide/tutorial_using_tasks.html)
  - [Step by Step Samples](https://docs.gradle.org/current/userguide/getting_started.html#try_gradle)
- [Gradle Tutorial for Beginners](https://tomgregory.com/gradle-tutorial-for-complete-beginners/)


## Simple Gradle build script

This dependency is used by the application.
Define the main class for the application.

```kts
plugins {
    // Apply the application plugin to add support for building a CLI application in Java.
    application 
}

repositories {
    // Use Maven Central for resolving dependencies.
    mavenCentral() 
}

dependencies {
    // Use JUnit Jupiter for testing.
    testImplementation("org.junit.jupiter:junit-jupiter:5.9.1") 

    // 	This dependency is used by the application.
    implementation("com.google.guava:guava:31.1-jre") 
}

application {
    // Define the main class for the application.
    mainClass.set("demo.App") 
}

tasks.named<Test>("test") {
    useJUnitPlatform() 
}
```

[reference](https://docs.gradle.org/current/samples/sample_building_java_applications.html)