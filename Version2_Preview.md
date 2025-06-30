# Version 2.0 – Study Sprint Co-Pilot

**Target Release:** Q4 2025  
**Repository Branch:** `v2.0-scope`  

---

## 1. Vision & Goals

In v2.0 we evolve Study Sprint Co-Pilot from a single-user focus timer into a lightweight, social, and deeply customizable productivity companion—while preserving the minimal, distraction-free core.  

- **Enhance Focus** with inline task management, quick-extend controls, and pre-break warnings.  
- **Automate & Schedule** timers by calendar integration so sessions start on your chosen cadence.  
- **Deepen Engagement** via home-screen widgets, simple analytics, and optional co-study rooms.  
- **Polish UI/UX** with progressive disclosure, subtle animations, and theme support.  
- **Maintain Minimalism**: every new feature is opt-in, tucked away until needed, and toggleable in Settings.

---

## 2. Feature Inventory

### 2.1 Task & To-Do Integration  
- **Inline Task Panel**  
  - A “Tasks” handle beneath the ring toggles a sliding bottom sheet.  
  - Users can add, check off, or delete items without leaving the Timer screen.  
  - Tasks persist per preset; completed tasks optionally archive on session end.  
- **Quick-Add Button**  
  - A “＋ Task” icon in the panel header for one-tap task creation.  

### 2.2 Quick-Extend Controls  
- **+5m / –5m Buttons**  
  - Two small icon buttons adjacent to the Play/Pause control.  
  - Default hidden; tap the ring to reveal them for on-the-fly adjustments.  
- **Long-Press Gesture**  
  - Long-press Play to open a contextual menu: Extend +5, Extend +10, End Session.

### 2.3 Pre-Break Warning  
- **Silent Notification**  
  - One minute before each scheduled break, send a silent badge + in-app ring pulse.  
  - Optionally configurable in Settings (on/off).  

### 2.4 Calendar-Scheduled Timers  
- **Session Scheduler**  
  - In a new “Schedule” tab, users pick a preset, day(s) of week, and start time.  
  - Schedules persist in a Calendar-style list (edit/delete).  
- **Automatic Launch**  
  - At the scheduled time, app fires a local notification prompting “Start ‘Deep Work’?”  
  - If accepted, the session auto-begins; if ignored, it snoozes or cancels.  
- **Calendar Sync**  
  - (Optional) Add scheduled sessions as events in the native iOS Calendar.

### 2.5 Home-Screen Widgets  
- **“Current Session” 2×2 Widget**  
  - Displays session title, live countdown, and phase icon.  
  - Tapping opens the app to the Timer view.  
- **“Quick Start” 2×1 Widget**  
  - Shows up to three favorite presets as buttons.  
  - Tapping immediately launches that preset.

### 2.6 Co-Study & Social (Opt-In)  
- **Co-Study Rooms**  
  - Create/join via 6-digit code or link.  
  - All participants share synchronized timers.  
- **Reactions & Chat**  
  - In-session chat sidebar for quick 👍, 💡 reactions.  
- **Leaderboards & Challenges**  
  - Optional weekly “most minutes” leaderboard among friends.  

### 2.7 Analytics & Gamification  
- **Dashboard Screen**  
  - Bar chart of daily study vs breaks over the past week.  
  - Heatmap showing your most productive hours.  
- **Goals & Badges**  
  - Pre-defined challenges (e.g. “5 sprints/day”) and custom goals.  
  - Earn badges and see celebratory confetti on completion.  
- **Export Data**  
  - CSV/PDF export of session logs and task completion.

### 2.8 Personalization & Theming  
- **Accent Color Picker**  
  - Choose from curated palettes (Sunset, Ocean, Forest).  
- **Dark-Mode Tweaks**  
  - Fine-tune background brightness and contrast.  
- **Subtle Animations**  
  - Ring pulses on break transitions, button micro-animations on taps.

### 2.9 Siri, Shortcuts & HealthKit  
- **Siri Shortcuts**  
  - “Hey Siri, start my Writing Sprint” → launches a chosen preset.  
- **HealthKit Integration**  
  - Log completed focus sessions as “Mindful Session” entries.  

---

## 3. UI/UX Principles

1. **Progressive Disclosure**  
   - Only surface new controls on explicit user action (tap, long-press).  
2. **Minimalist Aesthetic**  
   - Restrained color usage, icon-first buttons, unobtrusive text labels.  
3. **Settings Toggles**  
   - Every major v2 feature has an opt-in switch under Settings → Advanced.  
4. **Accessibility & Feedback**  
   - High-contrast modes, VoiceOver labels, haptic feedback on key interactions.

---

## 4. Prioritization & Roadmap

| Sprint | Milestones                                                     |
|--------|----------------------------------------------------------------|
| **1**  | • Inline Task Panel & Quick-Add<br>• Pre-Break Warning toggle |
| **2**  | • Quick-Extend Controls (+5/–5, long-press menu)<br>• Settings toggles |
| **3**  | • Calendar-Scheduled Timers UI & launch flow<br>• Widget prototypes |
| **4**  | • Home-Screen Widgets implementation<br>• Accent & theme picker |
| **5**  | • Analytics Dashboard & Goals screen<br>• CSV export          |
| **6**  | • Co-Study room MVP (local network)<br>• Siri Shortcut intents |
| **7**  | • HealthKit export<br>• Final polish, accessibility audit      |

---

## 5. User Stories

- **As a student**, I want to attach a checklist to my sprint so I can tick off tasks as I go.  
- **As a professional**, I need to extend my focus by 5 minutes without navigating menus.  
- **As a planner**, I’d like my app to remind me to start sessions at scheduled times.  
- **As a power user**, I want a home-screen widget to launch my Daily Deep Work preset in one tap.  
- **As a remote study group**, we want synchronized sprints so we can keep each other accountable.

---

## 6. Technical Considerations

- **Data Model**: Extend `FocusTime` to include `[TaskItem]` and `[ScheduleEntry]`.  
- **Notifications**: Add new category/actions for “Extend” & “Skip” and pre-break triggers.  
- **Widgets**: Use WidgetKit with `TimelineProvider` for live updates every second/minute.  
- **Networking**: Co-study via MultipeerConnectivity or lightweight WebSocket server.  
- **Persistence**: Migrate `FocusTimeStore` to support tasks, schedules, and theme preferences.  
- **Permissions**: Request Calendar access (for Event sync) and HealthKit if enabled.  

---

## 7. Next Steps

1. **Design Workshop**: Create Figma mockups for Task Panel, Scheduler UI, and Widgets.  
2. **Prototype Key Flows**: Build a SwiftUI proof-of-concept for inline tasks and calendar scheduling.  
3. **User Validation**: Conduct a small-batch beta test to refine feature scope and UI friction points.  
4. **Development Kickoff**: Merge `v2.0-scope` branch, set up feature flags, and begin Sprint 1.

> _With this comprehensive v2.0 blueprint, we balance meaningful new capabilities with a clean, distraction-free interface—positioning Study Sprint Co-Pilot to compete and delight users._  
