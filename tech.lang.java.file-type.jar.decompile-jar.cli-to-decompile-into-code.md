---
id: x63stukjm273hbpbf7izeft
title: CLI to Decompile into Code
desc: ''
updated: 1692766550274
created: 1692766533576
---



## Sage post
https://stackoverflow.com/a/647140/7858768

## Steps
### Build fernflower
```shell
git clone https://github.com/fesh0r/fernflower.git
cd fernflower
./gradlew build && echo "ls build/libs/"
```

### Use fernflower jar
```shell
java -jar fernflower.jar JAR_TO_DECOMPILE.jar ./dir-where-to-place-decompiled
```