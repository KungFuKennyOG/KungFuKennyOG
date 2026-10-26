# Last Call VR

A gory nightclub wave shooter for Meta Quest 3, built with WebXR and three.js. Dual pistols, verlet ragdolls, headshots that take heads off, severable limbs, blood pools, kill streaks and slow-mo.

**Play:** https://kungfukennyog.github.io/last-call-vr/ in the Quest browser, then hit **Enter VR**.

## Controls

| Input | Action |
|---|---|
| Trigger | Fire (one pistol per hand) |
| Point a gun at the floor | Twirl reload |
| Lean | Dodge red tracers (near misses trigger slow-mo) |
| Shoot a tracer | Deflect it |

Browser mode (no headset): click to lock aim, mouse to look, click to shoot, `R` to reload.

## Install on the Quest

**Easiest:** open the Play link in the Quest browser and tap **Install** in the address bar. It lands in your app library.

**As a sideloaded APK** (needs the Android SDK and Meta's `ovr-platform-util`):

```bash
ovr-platform-util create-pwa \
  -o LastCall.apk \
  --android-sdk "$ANDROID_HOME" \
  --manifest-content-file manifest.json \
  --package-name com.kungfukennyog.lastcall

adb install -r LastCall.apk
# flags vary a little between versions: check `ovr-platform-util create-pwa --help`
```

The APK runs on the Quest browser engine (the only runtime on the headset with WebXR) and loads the game from the Pages URL, then caches it for offline play.

## Local testing over USB

```bash
python -m http.server 8000
adb reverse tcp:8000 tcp:8000
# then open http://localhost:8000 in the Quest browser
```
