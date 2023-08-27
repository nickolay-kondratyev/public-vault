---
id: 1lg6k9fazmmmm21tlzdlhsu
title: Build from CLI Exampl
desc: ''
updated: 1692767999925
created: 1692767963034
---

```shell
main() {
  START_DIRECTIVE="com.example.androidapp/com.example.androidapp.MainActivity"

  ./gradlew assembleDebug \
  && adb install app/build/outputs/apk/debug/app-debug.apk \
  && echo Install success \
  && adb shell am start -n "${START_DIRECTIVE:?}" || return 1
}

main || exit 1
```