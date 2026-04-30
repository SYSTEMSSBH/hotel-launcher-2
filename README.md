# Hotel Operations Launcher — Android App

A custom Android app that hosts all 5 hotel management websites in persistent WebViews,
with session keep-alive and auto-start on reboot.

---

## Features
- ✅ 5 sites in a single app — switch instantly with no reloading
- ✅ Sessions persist for 12+ hours (no timeout)
- ✅ Screen stays on while app is open
- ✅ Auto-launches on tablet reboot
- ✅ Background service keeps sessions alive
- ✅ Back button navigates within pages (won't accidentally close app)

## Sites Included
| Tab | URL |
|-----|-----|
| Property Mgmt | https://visualone.onagilysys.sg/pms/#/login |
| Reservations | https://reserve.onagilysys.sg/login |
| Spa | https://spa.onagilysys.sg/Spa/login |
| Service | https://service.onagilysys.sg/login |
| Sales & Catering | https://salesandcatering.onagilysys.sg/snc/login |

---

## Build Instructions

### Requirements
- Android Studio Hedgehog (2023.1.1) or newer
- JDK 11 or newer
- Android SDK 34

### Steps
1. Open Android Studio
2. Select **File → Open** and choose this `hotel-launcher` folder
3. Wait for Gradle sync to complete (first time downloads dependencies)
4. Connect one of your tablets via USB (enable USB Debugging in Developer Options)
5. Click the green **Run ▶** button
6. To generate an APK for all tablets: **Build → Build Bundle(s)/APK(s) → Build APK(s)**
7. The APK will be at: `app/build/outputs/apk/debug/app-debug.apk`

### Installing on Multiple Tablets (Sideloading)
1. Copy `app-debug.apk` to each tablet (USB, email, or shared drive)
2. On the tablet: **Settings → Security → Allow install from unknown sources**
3. Open the APK file to install
4. Repeat for each tablet

---

## Customisation

### Change the hotel name in the top bar
Edit `app/src/main/res/layout/activity_main.xml` — find the TextView with text `🏨  Hotel Operations`

### Change the colour scheme
Edit `app/src/main/res/values/colors.xml`
- `brand_primary` — top bar and nav background (currently navy blue)
- `brand_accent` — progress bar and active tab (currently gold)

### Change keep-alive interval
Edit `MainActivity.kt` — find `KEEP_ALIVE_MS` (default: 10 minutes)

### Add/remove sites
Edit the `sites` list in `MainActivity.kt` and add/remove corresponding items in
`res/menu/bottom_nav_menu.xml`

---

## Tablet Settings to Configure Alongside the App
- **Display → Sleep → Never** (or 30 min as backup)
- **Developer Options → Stay Awake** — keeps screen on while charging
- Set app as **Default Home App** if you want it to be the only thing on the tablet
