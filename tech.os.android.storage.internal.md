---
id: ae4jxue76kdr0vsel5vv31q
title: Internal
desc: ''
updated: 1682479278544
created: 1682479278544
---

## Notes
- can only be accessed by your app.
- Accessed through [[tech.os.android.apis.Context]]
  - [getFilesDir() - persistent files directory](https://developer.android.com/reference/android/content/Context#getFilesDir())
  - [getCacheDir() - cache files directory](https://developer.android.com/reference/android/content/Context#getCacheDir())

## Internal Storage Directory Documentation:
> Internal storage directories: These directories include both a dedicated location for storing persistent files, and another location for storing cache data. The system prevents other apps from accessing these locations, and on Android 10 (API level 29) and higher, these locations are encrypted. These characteristics make these locations a good place to store sensitive data that only your app itself can access. - [android training](https://developer.android.com/training/data-storage/app-specific)
