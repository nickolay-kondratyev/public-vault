---
id: 9r1no89w2s87bkwbzds6l9u
title: Install Local Dependency to Local Repo
desc: ''
updated: 1654066871646
created: 1652650295052
---

## Example

```shell
# Install the graphml4j into maven dependency.

mvn install:install-file \
  -Dfile=/usr/local/workplace/graphml4j/build/libs/graphml4j-1.0-SNAPSHOT.jar \
  -DgroupId=com.glassthought.graphml4j \
  -DartifactId=Graphml4J \
  -Dversion=1.0-SNAPSHOT \
  -Dpackaging=jar
```

Use as regular dependency
```xml
   <dependency>
            <groupId>com.github.fritaly.graphml4j</groupId>
            <artifactId>Graphml4J</artifactId>
            <version>1.0-SNAPSHOT</version>
<!--            <scope>system</scope>-->
<!--            <systemPath>${project.basedir}/../graphml4j/build/libs/graphml4j-1.0-SNAPSHOT.jar</systemPath>-->
   </dependency>
```


mvn install:install-file \
  -Dfile=/Users/vintrin/yed-jar-raw/yed.jar \
  -DgroupId=com.yed \
  -DartifactId=yed \
  -Dversion=1.0 \
  -Dpackaging=jar