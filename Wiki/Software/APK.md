---
aliases: [apk, android-package, android-app]
tags: [software, apk, android, mobile]
cssclass: wiki
---
# How APK Works

## Overview
APK (Android Package Kit) is the file format for **distributing Android apps**.

## What's Inside an APK
```
app.apk
├── classes.dex        (compiled Java/Kotlin code)
├── AndroidManifest.xml (permissions, components)
├── res/               (layouts, strings, drawables)
├── lib/               (native libraries)
├── assets/            (raw files)
└── META-INF/          (signatures)
```

## How It Works
1. Developer builds the app → generates APK
2. APK is signed with a **keystore**
3. User downloads APK (from Play Store or sideloaded)
4. Android **Package Manager** verifies the signature
5. App is installed: DEX files optimized → app ready to run

## Related
- [[Wiki\Security\Application Signing|Application Signing]]
