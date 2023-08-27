---
id: helt03yyxe2uk3nn3yfjyca
title: Remove Exclude Duplicate Some Package
desc: ''
updated: 1692575374982
created: 1692575349700
---

## Groovy Example
```
/**
 * > A failure occurred while executing com.android.build.gradle.internal.tasks.CheckDuplicatesRunnable
 * > Duplicate class org.apache.commons.logging.Log found in modules commons-logging-1.2
 *   (commons-logging:commons-logging:1.2) and jcl-over-slf4j-1.7.33 (org.slf4j:jcl-over-slf4j:1.7.33)
 *
 * GPT recommended to go with slfj4
 *
 * > It's generally a good idea to exclude commons-logging in favor of jcl-over-slf4j,
 * as SLF4J is considered more modern and flexible. The exclusion should be applied
 * to the dependencies that include commons-logging.
 */
configurations {
    implementation.exclude group: 'commons-logging', module: 'commons-logging'
}

dependencies {
  //...
}
```