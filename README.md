# 🚗 စုံမကား (SoneMaKar) — Myanmar Car Restriction Reminder

## Features
- Add multiple car numbers (supports format like `1H/7123`, `2G/2345`, `3A/1234`)
- Auto-detects **Odd (မ)** or **Even (စုံ)** based on the **starting digit** of the car number
- **Live preview** as you type — instantly shows if the car can go out today
- **Daily notification at 7:00 AM** listing which cars can and cannot go
- Persists across app restarts and device reboots

## How Odd/Even Works
| Car Number | Starting Part | Type |
|---|---|---|
| `1H/7123` | `1` → Odd | မဂ္ဂလာ (Odd Day car) |
| `2G/2345` | `2` → Even | စုံ (Even Day car) |
| `3A/1234` | `3` → Odd | မဂ္ဂလာ (Odd Day car) |
| `10B/5678` | `10` → Even | စုံ (Even Day car) |

Day restriction is based on the **calendar day of the month**:
- Odd day (1, 3, 5...) → Odd cars can go out
- Even day (2, 4, 6...) → Even cars can go out

## Setup in Android Studio
1. Open Android Studio → **File > Open** → Select `SoneMaKar` folder
2. Wait for Gradle sync to finish
3. Click **Run ▶** to install on emulator or real device
4. Android 8.0+ (API 26+) required

## Project Structure
```
app/src/main/
├── java/com/myanmar/sonemakar/
│   ├── MainActivity.kt        ← Main screen logic
│   ├── NotificationHelper.kt  ← Builds and sends notifications
│   ├── NotificationReceiver.kt← Receives daily alarm trigger
│   └── BootReceiver.kt        ← Reschedules alarm after reboot
├── res/
│   ├── layout/
│   │   ├── activity_main.xml  ← Main screen UI
│   │   └── item_car.xml       ← Car list row UI
│   ├── values/
│   │   ├── colors.xml
│   │   ├── strings.xml
│   │   └── themes.xml
│   └── drawable/
│       ├── ic_car.xml
│       └── edit_text_bg.xml
└── AndroidManifest.xml
```
