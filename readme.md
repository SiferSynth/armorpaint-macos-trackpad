![](https://armorpaint.org/img/git.jpg)

armorpaint
==============

[ArmorPaint](https://armorpaint.org) is a software for 3D PBR texture painting - check out the [manual](https://armorpaint.org/manual).

**Fork note:** this fork of [armory3d/armorpaint](https://github.com/armory3d/armorpaint) adds macOS trackpad gestures for the 3D viewport. Everything else is unchanged and follows upstream.

### macOS trackpad gestures

| Gesture | Action |
|---|---|
| Two-finger drag | Rotate the view |
| Shift + two-finger drag | Pan |
| Ctrl + two-finger drag | Zoom (fingers up zooms in) |
| Alt + two-finger drag | Rotate the environment map |
| Pinch | Zoom |

- Mouse wheel zoom and scrolling the side panels work as before.
- Gestures follow your fingers whatever the "natural scrolling" setting is.
- The view keeps gliding briefly after you lift your fingers (macOS inertia).
- Drag speed: scales with the camera rotation speed in the preferences, and with `CAMERA_TRACKPAD_SCALE` in `paint/sources/camera.c`.
- The default environment map shortcut (`ctrl+middle`) can't be used on a trackpad, because there's no middle button. That is why it is on Alt + two-finger drag here.

Building on macOS is the same as upstream (needs [Xcode](https://developer.apple.com/xcode/resources/)):

```bash
cd paint
../base/make
# Open generated Xcode project at `build/ArmorPaint.xcodeproj`
# Build and run
```

Tested on macOS (Apple Silicon) with Xcode, trackpad only. Other platforms are unaffected: the changes are in `base/sources/backends/macos_system.m`, the shared input code and `paint/sources/camera.c`.

*Note 1: This repository is aimed at developers and may not be stable. Distributed binaries are [paid](https://armorpaint.org/download) to help with the project funding. All of the development is happening here in order to make it accessible to everyone. Thank you for support!*

*Note 2: If you are compiling git version of ArmorPaint, then you need to have a compiler ([Visual Studio with clang tools](https://visualstudio.microsoft.com/downloads/) - Windows, [clang + dependencies](https://github.com/armory3d/armorpaint/blob/main/base/docs/linux_deps.md) - Linux, [Xcode](https://developer.apple.com/xcode/resources/) - macOS / iOS, [Android Studio](https://developer.android.com/studio) - Android) and [git](https://git-scm.com/downloads) installed.*

```bash
git clone https://github.com/armory3d/armorpaint
cd armorpaint/paint
```

**Windows (x64)**
```bash
..\base\make
# Open generated Visual Studio project at `build\ArmorPaint.sln`
# Build and run
```

**Linux (x64)**
```bash
../base/make --run
```

**macOS (arm64)**
```bash
../base/make
# Open generated Xcode project at `build/ArmorPaint.xcodeproj`
# Build and run
```

**Android (arm64)**
```bash
../base/make --target android
# Open generated Android Studio project at `build/ArmorPaint`
# Build for device
```

**iOS (arm64)**
```bash
../base/make --target ios
# Open generated Xcode project `build/ArmorPaint.xcodeproj`
# Build for device
```

**WASM**
```bash
../base/make --target wasm --compile --embed
```

**Embedding data files**
```bash
# Requires compiler with c23 #embed support (clang 19 or newer)
../base/make --embed
```
