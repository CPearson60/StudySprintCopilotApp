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
