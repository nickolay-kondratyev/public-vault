---
id: fovdtl8gug540qs0kpyamfh
title: Gradle File
desc: ''
updated: 1673365404952
created: 1673365369491
---
 
https://gist.github.com/damienstanton/fb7c608e9883d57da34d4238b0ecaabf


build.gradle:
```txt
// just Java 8 and JUnit

apply plugin: 'java'
sourceCompatibility = 1.8
version = '0.1.0' 

repositories {
    mavenCentral()
}

dependencies {
  testCompile 'junit:junit:4.12'
}
```