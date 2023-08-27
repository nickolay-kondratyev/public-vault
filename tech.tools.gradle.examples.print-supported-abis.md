---
id: ufiiua0yrsqjyxfu05x8dlg
title: Print Supported Abi
desc: ''
updated: 1679193666203
created: 1679193666203
---

```kts
task("hi") {
    doLast {
        println("Supported ABIs: ${android.defaultConfig.ndk.abiFilters}")
    }
}
```


```kts
android {
    compileSdk = getAndroidApiVersion()
    sourceSets["main"].manifest.srcFile("src/androidMain/AndroidManifest.xml")
    defaultConfig {
        minSdk = 24
        targetSdk = 32
        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"

        ndk {
            // Specifies the ABI configurations of your native
            // libraries Gradle should build and package with your app.
            abiFilters += listOf("x86_64", "armeabi-v7a", "arm64-v8a")
        }

        externalNativeBuild {
            cmake {
                arguments("-DANDROID_API_LEVEL=${getAndroidApiVersion()}")

                abiFilters("arm64-v8a", "armeabi-v7a", "x86_64")
            }
        }
    }
```