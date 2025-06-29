# Version 1.0 – Study Sprint Co-Pilot

**Release Date:** June 30, 2025  
**Repository Tag:** `v1.0`

---

## 1. Overview

Study Sprint Co-Pilot v1.0 is a SwiftUI-based productivity timer app designed to help users structure focused work (or study) sessions with automatic, scheduled breaks. Built as my first end-to-end iOS project, it showcases:

- Custom “Focus Time” presets with arbitrary study durations and multiple breaks  
- A clean, intuitive timer UI with a circular progress ring  
- Local notifications for break start, break end, and session completion  
- Live Activity on the Lock Screen/Dynamic Island for a live countdown  
- Persistent history logging completed and paused sessions  
- Settings for notifications, haptics, and alert sounds  
- Onboarding flow that explains purpose, features, and usage  

---

## 2. Key Features

| Feature                      | Description                                                                                 |
|------------------------------|---------------------------------------------------------------------------------------------|
| **Focus Time Presets**       | Users can create/edit multiple presets, each with its own study duration and break blocks. |
| **Automatic Breaks**         | Breaks trigger automatically at configured minutes—even when the app is backgrounded.      |
| **Local Notifications**      | Alerts fire at break start, break end, and session complete, with custom sounds & haptics. |
| **Live Activities**          | Real-time countdown lives on the Lock Screen and in the Dynamic Island (iOS 16.1+).        |
| **History Logging**          | Completed and paused sessions are stored and viewable in the History tab.                  |
| **Settings**                 | Toggle notifications, choose alert sounds, and enable/disable haptic feedback.             |
| **Onboarding**               | A multi-page, swipeable introduction explains app purpose, features, and usage.            |

---

## 3. UI & Flow

1. **Onboarding**  
   - Swipeable pages guide new users through purpose, creator background, core features, and a “Get Started” button.  

2. **Focus Times Tab**  
   - Empty state: prompt to add first preset  
   - List view: shows all presets, supports add/edit/delete via a modal editor  

3. **Timer Tab**  
   - Empty or unselected state: prompts to add/select a preset  
   - Active state:  
     - Circular progress ring showing study vs break progress  
     - Center countdown label (MM:SS)  
     - Status text below (“Studying: [title]” or “On break: [type]”)  
     - Upcoming-break card during study phase  
     - Play/Pause and Reset controls  
     - Live hint (“Tap play to start” or “Session complete – tap reset”)  

4. **Settings Tab**  
   - Toggle switches for Notifications and Haptics  
   - Picker for Alert Sound  
   - “Reset All Settings” button  

5. **History Tab**  
   - Lists past sessions with title, duration, and status  

---

## 4. Technical Architecture

- **SwiftUI** for declarative UI across all screens  
- **Combine** `Timer.publish` for 1-second ticks driving session logic  
- **NotificationManager** singleton wrapping `UNUserNotificationCenter`  
- **LiveActivityManager** using ActivityKit to manage Lock Screen/Dynamic Island activities  
- **SessionManager**: `ObservableObject` orchestrating phases (study, break, ended), notification scheduling, haptic feedback, and logging  
- **FocusTimeStore**: simple persistence layer (e.g. UserDefaults or local file) for presets and session history  
- **OnboardingView**: a custom PageTabViewStyle carousel with gradient background  

---

## 5. Strengths & Achievements

- Delivered a **fully functional**, multi-screen SwiftUI app from scratch  
- Seamless **automatic break** scheduling even when the app is backgrounded  
- Integrated **Live Activities**, a cutting-edge iOS 16.1 feature  
- Clean, user-friendly **empty states** to guide first-time users  
- Modular architecture with well-encapsulated managers and view models  
- Comprehensive **Settings** and **History** support  

---

## 6. Lessons Learned

- **Live Activities** require careful entitlement and App Store Connect setup  
- Managing **local notifications** in tandem with timer logic can be tricky—cancellation and rescheduling must be precise  
- **Empty-state UIs** are crucial for first-run user guidance  
- SwiftUI’s **PageTabViewStyle** makes onboarding carousels trivial, but edge-case layout tweaks are needed for different device sizes  
- Persisting and refreshing an active session after editing a preset demands a clear “refresh” API  

---

## 7. Known Limitations (v1.0)

- No **widget** support on the Home Screen  
- Fixed break-start notifications; no “pre-break warning”  
- Limited analytics—only raw session logs, no charts or goals  
- No **iPad** or **Apple Watch** support (iPhone-only)  
- Settings do not persist across devices (no iCloud sync)  

---

## 8. Next Steps (v2.0 Preview)

- Home-screen **widgets** for quick start and progress glance  
- **Adaptive** break placement based on user performance  
- **Analytics dashboard** with charts, streaks, and goals  
- **Siri shortcuts** and **Calendar integration**  
- Enhanced **notification actions** (“Skip break”, “Extend focus”)  
- Dark-mode theming and custom accent colors  

---

_End of Version 1.0 Documentation_  
