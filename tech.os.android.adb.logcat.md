---
id: avars663j0rczby1w4rmn93
title: Logcat
desc: ''
updated: 1692679375563
created: 1682483611909
---

To filter logs for particular application you can use run (using application id):
```bash
adb logcat | grep com.example.androidapp
```

applicationId can be within gradle build file or AndroidManifest.xml

```kts
android {
    defaultConfig {
        applicationId "com.example.androidapp"
```

## WARNINGs and above
```shell
# Warnings and above
adb logcat *:W

# Errors and above
adb logcat *:E
```
