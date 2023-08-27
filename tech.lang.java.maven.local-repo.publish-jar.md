---
id: cdqvgltasuxq0rdwlvh5mod
title: Publish Jar To Local Maven
desc: ''
updated: 1693092855391
created: 1693092168641
---

[Stack Overflow Answer](https://stackoverflow.com/a/4955695/7858768)

```shell
mvn install:install-file \
   -Dfile=<path-to-file> \
   -DgroupId=<group-id> \
   -DartifactId=<artifact-id> \
   -Dversion=<version> \
   -Dpackaging=<packaging> \
   -DgeneratePom=true
```

<details>
<summary>Example (build succeeded)</summary>

```
mvn install:install-file -Dfile=/Users/nickolaykondratyev/git_repos/texophen-lucene-android/lucene-7.3.0/build/core/lucene-core-7.3.0-SNAPSHOT.jar -DgroupId=org.apache.lucene -DartifactId=lucene-core -Dversion=7.3.0-SNAPSHOT -Dpackaging=jar -DgeneratePom=true
```

output:
```
[INFO] ------------------< org.apache.maven:standalone-pom >-------------------
[INFO] Building Maven Stub Project (No POM) 1
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] --- install:3.1.1:install-file (default-cli) @ standalone-pom ---
[INFO] pom.xml not found in lucene-core-7.3.0-SNAPSHOT.jar
[INFO] Installing /Users/nickolaykondratyev/git_repos/texophen-lucene-android/lucene-7.3.0/build/core/lucene-core-7.3.0-SNAPSHOT.jar to /Users/nickolaykondratyev/.m2/repository/org/apache/lucene/lucene-core/7.3.0-SNAPSHOT/lucene-core-7.3.0-SNAPSHOT.jar
[INFO] Installing /var/folders/t3/4h_q4whx30qgckyh7wnr78jc0000gn/T/mvninstall5153596156937935477.pom to /Users/nickolaykondratyev/.m2/repository/org/apache/lucene/lucene-core/7.3.0-SNAPSHOT/lucene-core-7.3.0-SNAPSHOT.pom
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.147 s
[INFO] Finished at: 2023-08-26T16:33:31-07:00
[INFO] ------------------------------------------------------------------------
```
</details>
