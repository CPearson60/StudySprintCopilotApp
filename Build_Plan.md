# Study Sprint Co-Pilot v2.0 📚

A serious, structured academic study companion designed to help students and professionals study more effectively by combining guided study sessions, resource management, and spaced repetition review — all offline, ensuring complete privacy.

## 🎯 Core Philosophy

**Study Sprint Co-Pilot** emphasizes clarity, guidance, and accessibility without gamification. Instead of points, streaks, or playful graphics, it focuses on effective study methods, minimal distractions, and a clean, academic visual tone.

## ✨ Key Features

### 🧠 Guided Study Modes
- **Built-in Methods**: Active Recall, Feynman Technique, Problem Sets, Read→Recall, Outline→Drill
- **Structured Phases**: Warm-Up, Deep Work, Recall, Review, Break with timers and prompts
- **Custom Workflows**: Save personal study modes to match your workflow

### 📅 Session Planning
- **Topic Selection**: Choose subject or chapter
- **Method Selection**: Pick study mode
- **Goal Setting**: Define what to achieve
- **Duration Planning**: Set total time
- **Resource Attachment**: Add PDFs, images, web links via UIDocumentPicker + QuickLook
- **Calendar Integration**: Import deadlines and class schedules (EventKit)

### 💡 Mid-Session Prompts
- **Local JSON Prompt Packs**: Structured prompts triggered at specific checkpoints
- **Automatic & Manual**: Timed prompts or user-triggered guidance
- **Mode-Specific**: Tailored prompts for each study method
- **Examples**:
  - Active Recall: "Close your notes. Write down three key facts from memory."
  - Feynman: "Explain the last concept in one sentence as if teaching a beginner."

### ✅ Checkpoints & Reflection
- **Active Engagement**: Mini-tasks during sessions (summarizing, recalling terms)
- **Post-Session Reflection**:
  - What stuck?
  - What needs review?
  - Difficulty rating (easy → hard)
- **Automatic Review Scheduling**: Creates ReviewTasks with spaced intervals (1, 3, 7, 14 days)

### 🔄 Spaced Review System
- **Review Notifications**: Reminders for upcoming review tasks
- **Review Screen Features**:
  - Flashcards (manual or imported)
  - Past checkpoints from previous sessions
- **Adaptive Intervals**: Completion and difficulty feedback adjust future review timing

### 📚 Resource Drawer
- **Topic-Specific Library**: PDFs, images, links organized by subject
- **PencilKit Integration**: Scratch pad for diagrams and handwritten notes
- **Session Integration**: Accessible during study via slide-in overlay
- **Never Leave Session**: All resources available without interruption

### 🃏 Flashcards
- **Manual Creation**: Build cards directly in-app
- **Import Formats**: CSV, TXT, JSON with field mapping
- **Media Support**: Optional ZIP bundles for images/audio
- **Export Options**: CSV + optional media ZIP for backups or sharing

### 📊 Insights Dashboard
- **Visual Progress Tracking**: Swift Charts integration
- **Key Metrics**:
  - Total focused time
  - Sessions by topic/mode
  - Review completion rates
  - Topics needing most review
- **Local Data**: Stored locally, visualized accessibly and minimally

## 🏗️ Technical Architecture

### Frameworks
- **SwiftUI**: Cross-platform UI framework
- **Core Data**: On-device storage with optional iCloud sync
- **UserNotifications**: Review reminders and session alerts
- **ActivityKit**: Live Activities for timers
- **WidgetKit**: Home screen widgets for upcoming reviews/sessions
- **EventKit**: Calendar import and integration
- **QuickLook**: Resource previews
- **UIDocumentPicker**: File import/export
- **PencilKit**: Drawing and sketching in Resource Drawer
- **Swift Charts**: Insights visualizations

### Constraints
- **Offline-First**: All functionality available without internet
- **Privacy-Focused**: All data stored locally; cloud sync is optional and user-controlled
- **Multi-Platform**: iOS 17+, iPadOS 17+, macOS 14+ (Catalyst)
- **No Gamification**: No points, streaks, or game-like rewards
- **Accessibility**: VoiceOver support, Dynamic Type, haptics, color-blind safe

## 🎨 Design System

### Brand Theme
```swift
enum Theme {
    static let primary = Color(hex: "745DD0")      // Royal Purple
    static let secondary = Color(hex: "7D98D3")    // Periwinkle
    static let bgMain = Color(hex: "F3F1F8")      // Soft Lavender Gray
    static let textMain = Color(hex: "080709")     // Near-black
    static let canvas = Color(hex: "FDFDFE")       // Paper White
    static let onPrimary = Color.white
}
```

### Visual Style
- **Cards & Panels**: Rounded corners (20–24pt), `.ultraThinMaterial` for overlays, subtle shadows
- **Spacing**: Base 16pt, consistent grid alignment
- **Typography**: Large, bold, readable titles with comfortable line height
- **Color Usage**: Backgrounds in `bgMain`, content surfaces in `canvas`, CTAs in `primary`
- **Animations**: Minimal, fast (150–220ms easeInOut)
- **Accessibility**: High-contrast text, VoiceOver labels, tap targets ≥44×44pt

## 📱 App Structure

### Main Navigation Tabs
1. **Home**: Today's plan, quick start, upcoming reviews
2. **Sessions**: Start new session, session history
3. **Reviews**: Pending reviews, flashcards, checkpoints
4. **Resources**: Per-topic resource library
5. **Insights**: Analytics and charts

### Data Model
- **Topic**: Name, resources
- **StudySession**: Mode, topic, start/end, phases, notes
- **Checkpoint**: Text, timestamp, linked to session
- **ReviewTask**: Topic, due date, status
- **Flashcard**: Front, back, tags, deck
- **Prompt**: Text, mode(s), phase(s), elapsed time range

## 🚀 Development Approach

### Vertical Slices
Build in vertical slices, completing one end-to-end feature before moving on:
1. App shell, theme, and navigation
2. Session engine + prompt delivery
3. Resource Drawer integration
4. Flashcard CRUD + import/export
5. Insights dashboard + charts
6. Reflection + spaced review scheduling

### Priorities
- **Stability and accessibility** over new features
- **Consistent design** across platforms
- **Performance optimization** for smooth user experience

## 👥 User Scenarios

### Scenario 1: Exam Prep (Emma, College Student)
**Goal**: Prepare for biology midterm using Active Recall
1. **Home Tab**: Sees today's plan with suggested session
2. **Session Planning**: Mode, topic, duration, goal, adds lecture PDF
3. **During Session**: Timer, phase indicators, timed prompts
4. **Break & Reflection**: Post-session reflection, review scheduling
5. **Review Day**: Widget notifications, flashcard review

### Scenario 2: Research Paper (David, Law Student)
**Goal**: Draft legal ethics paper outline using Feynman Technique
1. **Session Planning**: Feynman mode, 40 minutes, case ruling PDF
2. **During Session**: Phase-based prompts, checkpoint creation
3. **Reflection**: Difficulty rating, review scheduling

### Scenario 3: Daily Vocabulary (Sara, High School Student)
**Goal**: Keep up with Spanish vocabulary using flashcards
1. **Review Tab**: Shows due cards, difficulty rating
2. **Import**: CSV from teacher via Document Picker
3. **Spaced Review**: Adaptive intervals based on performance

### Scenario 4: Engineering Study (Leo, Engineering Student)
**Goal**: Study circuit theory with diagrams and annotations
1. **Session Planning**: Problem Sets mode, schematic diagram
2. **Resource Integration**: PencilKit scratch pad for annotations
3. **Checkpoint Creation**: Review needs identification

## 🔧 Technical Requirements

### Performance Targets
- **Launch Time**: <2 seconds cold start
- **UI Updates**: <100ms response time
- **Memory Usage**: Under 200MB for 1000+ flashcards
- **Battery**: Minimal background activity, idle CPU under 5%

### Data Privacy & Export
- **Local-Only Default**: Explicit opt-in for iCloud sync
- **Export Options**: Sessions (CSV/JSON), Flashcards (CSV/ZIP), Resources (ZIP)
- **Privacy Note**: "We never collect your study data"

### Error Handling
- **File Import**: Clear error messages with template offers
- **Empty States**: Friendly placeholders for each tab
- **Notifications**: Graceful permission denial handling
- **Data Conflicts**: User prompts for duplicate imports

## 🧪 Testing & Quality

### Testing Requirements
- **Unit Tests**: PromptEngine filtering, ReviewTask scheduling, import parsing
- **UI Tests**: Complete user flows, flashcard review, resource import
- **Performance Tests**: Load 1000+ flashcards under 200ms, CSV import within 3s

### Accessibility & Localization
- **VoiceOver**: Full descriptions for all interactive elements
- **Dynamic Type**: Test at XXL sizes without layout breaks
- **High Contrast**: Mode adjustments
- **Localization**: Future multi-language support preparation

## 🔮 Future Enhancements

### Version 2+ Features
- **Audio Notes**: Recording inside sessions
- **Advanced Search**: Filter across topics/resources
- **Review Algorithms**: Leitner, SM-2 scheduling
- **Exam Templates**: SAT, MCAT, LSAT preparation
- **Collaboration**: Local AirDrop sharing of decks/resources

## 📋 Release Checklist

Before shipping updates:
1. ✅ Pass all unit/UI/performance tests
2. ✅ Validate Core Data migrations
3. ✅ Confirm icons, launch screens, widgets work on all devices
4. ✅ Update App Store metadata/screenshots
5. ✅ Verify privacy policy in settings

## 🤝 Contributing

We welcome contributions focused on stability, accessibility, and academic effectiveness. Please see our contributing guidelines for more information.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

**Study Sprint Co-Pilot v2.0** - Transform your study habits with proven academic methods and structured learning! 📚✨ 


# Study Sprint Co-Pilot v2.0 - BUILD PLAN

## 🎯 Project Overview
**Study Sprint Co-Pilot** is a serious, structured academic study companion designed to help students and professionals study more effectively by combining guided study sessions, resource management, and spaced repetition review — all offline, ensuring complete privacy.

The app emphasizes clarity, guidance, and accessibility without gamification. Instead of points, streaks, or playful graphics, it focuses on effective study methods, minimal distractions, and a clean, academic visual tone.

## 🏗️ Architecture & Constraints

### Technology Stack
- **Apple Frameworks Only**: SwiftUI, CoreData, UserNotifications, ActivityKit, WidgetKit, EventKit, QuickLook, UIDocumentPicker, PencilKit, Swift Charts
- **No Third-Party Dependencies**: All features must work offline
- **Multi-Platform**: iOS 17+, iPadOS 17+, macOS 14+ (Catalyst)
- **Accessibility**: VoiceOver, Dynamic Type, haptics compliance

### Core Principles
- **Offline-first architecture**: All functionality available without internet
- **Privacy-focused**: All data stored locally; cloud sync is optional and user-controlled
- **Academic tone**: Serious, structured learning without gamification
- **Accessibility compliance**: Full VoiceOver support, Dynamic Type, haptics
- **Responsive design**: Consistent experience across iPhone, iPad, and Mac
- **Performance optimization**: Launch <2 seconds, UI updates <100ms

## 📁 Module Breakdown & File Structure

### 1. App Foundation
```
StudySprintCoPilot/
├── StudySprintCoPilotApp.swift          # Main app entry point
├── App/
│   ├── AppDelegate.swift                # App lifecycle management
│   ├── SceneDelegate.swift              # Scene management
│   └── AppConfiguration.swift           # App-wide configuration
```

### 2. Core Data Models
```
Models/
├── CoreData/
│   ├── StudySprintCoPilot.xcdatamodeld/ # Data model
│   ├── PersistenceController.swift      # Core Data stack
│   └── DataModels/
│       ├── Topic.swift                  # Study topics and subjects
│       ├── StudySession.swift           # Study session entity
│       ├── StudyMode.swift              # Study method definitions
│       ├── Checkpoint.swift             # Session checkpoints
│       ├── ReviewTask.swift             # Spaced review tasks
│       ├── Flashcard.swift              # Flashcard system
│       ├── Prompt.swift                 # Study prompts
│       ├── Resource.swift               # Study resources (PDFs, images, links)
│       └── UserProfile.swift            # User preferences
```

### 3. Business Logic Layer
```
Managers/
├── SessionManager.swift                  # Timer & session management
├── StudyModeManager.swift               # Study method management
├── PromptManager.swift                  # Prompt delivery system
├── CheckpointManager.swift              # Checkpoint creation & tracking
├── ReviewManager.swift                  # Spaced review scheduling
├── ResourceManager.swift                # Resource management
├── FlashcardManager.swift               # Flashcard CRUD operations
├── NotificationManager.swift            # Review reminders
├── CalendarManager.swift                # EventKit integration
├── ImportExportManager.swift            # File import/export
└── SettingsManager.swift                # App settings
```

### 4. UI Components
```
Views/
├── Core/
│   ├── MainTabView.swift                # Main tab navigation
│   ├── ContentView.swift                # Root content view
│   └── LoadingView.swift                # Loading states
├── Home/
│   ├── HomeView.swift                   # Today's plan, quick start
│   ├── TodayPlanCard.swift              # Today's study plan
│   ├── QuickStartCard.swift             # Quick session start
│   └── UpcomingReviewsCard.swift        # Due reviews display
├── Sessions/
│   ├── SessionListView.swift            # Session history
│   ├── SessionDetailView.swift          # Session details
│   ├── SessionPlanningView.swift        # New session planning
│   ├── ActiveSessionView.swift          # Active study session
│   ├── TimerView.swift                  # Session timer
│   ├── PhaseIndicator.swift             # Study phase display
│   ├── PromptOverlay.swift              # Mid-session prompts
│   └── ReflectionView.swift             # Post-session reflection
├── Reviews/
│   ├── ReviewListView.swift             # Pending reviews
│   ├── ReviewSessionView.swift          # Active review session
│   ├── FlashcardReviewView.swift        # Flashcard review
│   ├── CheckpointReviewView.swift       # Checkpoint review
│   └── ReviewHistoryView.swift          # Review completion history
├── Resources/
│   ├── ResourceLibraryView.swift        # Topic resource library
│   ├── ResourceDrawer.swift             # Session resource overlay
│   ├── ResourceDetailView.swift         # Resource preview
│   ├── PencilKitView.swift              # Drawing/annotation
│   └── ResourceImportView.swift         # Resource import
├── Insights/
│   ├── InsightsView.swift               # Analytics dashboard
│   ├── StudyTimeChart.swift             # Time tracking charts
│   ├── SessionChart.swift               # Session analytics
│   ├── ReviewChart.swift                # Review completion charts
│   └── TopicChart.swift                 # Topic performance
└── Settings/
    ├── SettingsView.swift               # Main settings
    ├── NotificationSettingsView.swift    # Notification preferences
    ├── AppearanceSettingsView.swift      # UI customization
    ├── DataSettingsView.swift            # Data management
    ├── PrivacySettingsView.swift         # Privacy controls
    └── AboutView.swift                   # App information
```

### 5. Shared Components
```
Components/
├── UI/
│   ├── CustomButton.swift               # Reusable buttons
│   ├── CustomTextField.swift            # Text input components
│   ├── CustomCard.swift                 # Card containers
│   ├── CustomProgressBar.swift          # Progress indicators
│   ├── CustomAlert.swift                # Alert dialogs
│   └── CustomModal.swift                # Modal presentations
├── Charts/
│   ├── StudyTimeChart.swift             # Time tracking charts
│   ├── SessionChart.swift               # Session analytics
│   ├── ReviewChart.swift                # Review completion
│   └── TopicChart.swift                 # Topic performance
└── Utilities/
    ├── Extensions/
    │   ├── Color+Extensions.swift       # Color utilities
    │   ├── Date+Extensions.swift        # Date formatting
    │   ├── View+Extensions.swift        # View modifiers
    │   └── String+Extensions.swift      # String utilities
    ├── Helpers/
    │   ├── TimeFormatter.swift          # Time formatting
    │   ├── HapticManager.swift          # Haptic feedback
    │   ├── AccessibilityHelper.swift    # Accessibility support
    │   ├── ValidationHelper.swift       # Input validation
    │   └── FileHelper.swift             # File operations
    └── Constants/
        ├── AppConstants.swift            # App-wide constants
        ├── ColorConstants.swift          # Color definitions
        ├── LayoutConstants.swift         # Layout values
        ├── TextConstants.swift           # Text content
        └── StudyModes.swift             # Study method definitions
```

### 6. Resources
```
Resources/
├── Assets.xcassets/                     # App icons, colors, images
├── PromptPacks/                         # JSON prompt collections
├── Localizable.strings                  # Localization files
├── Info.plist                           # App configuration
└── Entitlements.plist                   # App capabilities
```

## 🚀 Vertical Slice Milestones

### Phase 1: Foundation & App Shell (Weeks 1-2)
**Goal**: Basic app structure with navigation and theming

#### Milestone 1.1: Project Setup
- [ ] Create new Xcode project with proper configuration
- [ ] Set up Core Data model for basic entities (Topic, StudySession, StudyMode)
- [ ] Implement app navigation structure (5 main tabs)
- [ ] Create brand theme system with specified colors

#### Milestone 1.2: Core UI Framework
- [ ] Implement responsive layout for different screen sizes
- [ ] Create reusable UI components (buttons, cards, modals)
- [ ] Set up accessibility support (VoiceOver, Dynamic Type)
- [ ] Implement dark mode support

#### Milestone 1.3: Basic Data Layer
- [ ] Set up Core Data stack with PersistenceController
- [ ] Create basic data models and relationships
- [ ] Implement basic CRUD operations for topics and sessions
- [ ] Set up data import/export foundation

### Phase 2: Session Engine & Study Modes (Weeks 3-4)
**Goal**: Core study session functionality with guided modes

#### Milestone 2.1: Study Mode System
- [ ] Implement built-in study methods (Active Recall, Feynman, Problem Sets, etc.)
- [ ] Create study mode configuration and customization
- [ ] Build phase-based session structure (Warm-Up, Deep Work, Recall, Review, Break)
- [ ] Implement session planning flow

#### Milestone 2.2: Session Management
- [ ] Create SessionManager with timer functionality
- [ ] Implement session state machine (enum SessionPhase)
- [ ] Add session persistence and history
- [ ] Create session planning interface

#### Milestone 2.3: Basic Timer & Phases
- [ ] Implement session timer with phase transitions
- [ ] Add phase indicators and progress tracking
- [ ] Create session completion handling
- [ ] Add basic session controls (start, pause, stop)

### Phase 3: Prompts & Checkpoints (Weeks 5-6)
**Goal**: Mid-session guidance and active engagement

#### Milestone 3.1: Prompt System
- [ ] Design prompt pack JSON structure
- [ ] Implement PromptManager for prompt delivery
- [ ] Create automatic and manual prompt triggers
- [ ] Add mode-specific prompt filtering

#### Milestone 3.2: Checkpoint System
- [ ] Implement checkpoint creation during sessions
- [ ] Create checkpoint tracking and management
- [ ] Add checkpoint types (summarizing, recalling, etc.)
- [ ] Implement checkpoint persistence

#### Milestone 3.3: Session Enhancement
- [ ] Integrate prompts into active sessions
- [ ] Add prompt overlay and interaction
- [ ] Create session flow with prompts and checkpoints
- [ ] Implement session reflection system

### Phase 4: Resource Management (Weeks 7-8)
**Goal**: Study resource library and integration

#### Milestone 4.1: Resource System
- [ ] Implement resource management (PDFs, images, links)
- [ ] Create topic-specific resource organization
- [ ] Add resource import via UIDocumentPicker
- [ ] Implement QuickLook integration for previews

#### Milestone 4.2: Resource Drawer
- [ ] Create slide-in resource overlay
- [ ] Implement PencilKit integration for annotations
- [ ] Add resource search and filtering
- [ ] Create resource detail views

#### Milestone 4.3: Session Integration
- [ ] Integrate resources into study sessions
- [ ] Add resource access during active sessions
- [ ] Implement resource annotation during study
- [ ] Create resource export functionality

### Phase 5: Spaced Review & Flashcards (Weeks 9-10)
**Goal**: Review system and flashcard management

#### Milestone 5.1: Review System
- [ ] Implement spaced review scheduling (1, 3, 7, 14 days)
- [ ] Create ReviewManager for task management
- [ ] Add review notifications and reminders
- [ ] Implement review completion tracking

#### Milestone 5.2: Flashcard System
- [ ] Create flashcard CRUD operations
- [ ] Implement flashcard import (CSV, TXT, JSON)
- [ ] Add media support for flashcards
- [ ] Create flashcard review interface

#### Milestone 5.3: Review Integration
- [ ] Integrate checkpoints into review system
- [ ] Create combined review sessions
- [ ] Implement difficulty-based interval adjustment
- [ ] Add review history and analytics

### Phase 6: Analytics & Insights (Weeks 11-12)
**Goal**: Data visualization and progress tracking

#### Milestone 6.1: Data Collection
- [ ] Implement comprehensive session tracking
- [ ] Add review completion analytics
- [ ] Create topic performance metrics
- [ ] Implement data aggregation and processing

#### Milestone 6.2: Charts & Visualization
- [ ] Integrate Swift Charts for data visualization
- [ ] Create study time charts and analytics
- [ ] Add session and review completion charts
- [ ] Implement topic performance visualization

#### Milestone 6.3: Insights Dashboard
- [ ] Build comprehensive insights dashboard
- [ ] Add progress tracking and trends
- [ ] Create actionable study recommendations
- [ ] Implement data export functionality

### Phase 7: Advanced Features & Polish (Weeks 13-14)
**Goal**: Live Activities, widgets, and final polish

#### Milestone 7.1: Live Activities & Widgets
- [ ] Implement ActivityKit for session timers
- [ ] Create Dynamic Island support
- [ ] Add home screen widgets for reviews
- [ ] Implement background updates

#### Milestone 7.2: Platform Optimization
- [ ] Optimize for iPad layouts and interactions
- [ ] Implement macOS Catalyst support
- [ ] Add keyboard shortcuts and trackpad gestures
- [ ] Optimize for different screen sizes

#### Milestone 7.3: Final Polish
- [ ] Performance optimization and testing
- [ ] Accessibility refinement and testing
- [ ] Cross-platform consistency verification
- [ ] Final testing and bug fixes

## 🎨 Design System

### Brand Colors (Updated)
- **Primary**: Royal Purple (#745DD0)
- **Secondary**: Periwinkle (#7D98D3)
- **Background**: Soft Lavender Gray (#F3F1F8)
- **Text**: Near-black (#080709)
- **Canvas**: Paper White (#FDFDFE)
- **On Primary**: White

### Visual Style
- **Cards & Panels**: Rounded corners (20–24pt), `.ultraThinMaterial` for overlays
- **Spacing**: Base 16pt, consistent grid alignment
- **Typography**: Large, bold, readable titles with comfortable line height
- **Animations**: Minimal, fast (150–220ms easeInOut)
- **Accessibility**: High-contrast text, VoiceOver labels, tap targets ≥44×44pt

## 🔧 Technical Implementation

### Core Data Schema
- **Topic**: Core study subjects with resource relationships
- **StudySession**: Session data with mode, topic, phases, and checkpoints
- **StudyMode**: Study method definitions and configurations
- **Checkpoint**: Session checkpoints with timestamps and content
- **ReviewTask**: Spaced review scheduling with adaptive intervals
- **Flashcard**: Flashcard system with import/export support
- **Prompt**: Study prompts with mode and phase filtering
- **Resource**: Study materials (PDFs, images, links) with topic organization

### State Management
- **ObservableObject**: For view models and managers
- **@StateObject**: For persistent objects and managers
- **@EnvironmentObject**: For app-wide state (settings, user profile)
- **Core Data**: For persistent storage with background save queues

### Performance Considerations
- **Launch Time**: <2 seconds cold start
- **UI Updates**: <100ms response time
- **Memory Usage**: Under 200MB for 1000+ flashcards
- **Battery**: Minimal background activity, idle CPU under 5%

## 📱 Platform-Specific Features

### iOS
- **Dynamic Island**: Live Activities integration for session timers
- **Haptic Feedback**: Rich tactile experiences for interactions
- **VoiceOver**: Full accessibility support
- **Background App Refresh**: Timer continuation and notifications

### iPad
- **Split View**: Multi-pane interfaces for resource management
- **Drag & Drop**: Intuitive file and resource interactions
- **Apple Pencil**: Note-taking and annotation integration
- **Large Screen Optimization**: Enhanced layouts and navigation

### macOS
- **Keyboard Shortcuts**: Power user features and navigation
- **Menu Bar**: Quick access to app functions
- **Window Management**: Multiple window support for multitasking
- **Trackpad Gestures**: Natural navigation and interaction

## 🚀 Success Metrics

### Technical Goals
- **Performance**: <2 second app launch time
- **Reliability**: 99.9% timer accuracy and data persistence
- **Accessibility**: 100% VoiceOver compliance and Dynamic Type support
- **Cross-Platform**: Consistent experience across all target devices

### User Experience Goals
- **Academic Focus**: Serious, structured learning without distractions
- **Accessibility**: Inclusive design for all users and abilities
- **Privacy**: Complete data control and local storage
- **Effectiveness**: Improved study retention and organization

## 🔮 Future Considerations

### Version 2+ Enhancements
- **Audio Notes**: Recording inside study sessions
- **Advanced Search**: Filter across all topics and resources
- **Review Algorithms**: Leitner, SM-2 scheduling systems
- **Exam Templates**: SAT, MCAT, LSAT preparation workflows
- **Collaboration**: Local AirDrop sharing of decks and resources

---

**Next Steps**: Await further instructions before proceeding with implementation. This plan provides the foundation for building a serious, academic-focused study companion that meets all specified requirements for offline privacy and structured learning. 
