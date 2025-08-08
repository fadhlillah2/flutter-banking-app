# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Flutter banking app template with dark/light theme support. It's a UI-focused mobile banking application that displays transaction history, card information, and provides basic navigation between different screens.

## Development Commands

```bash
# Run the app in debug mode
flutter run

# Run tests
flutter test

# Build for Android
flutter build apk

# Build for iOS
flutter build ios

# Get dependencies
flutter pub get

# Clean build files
flutter clean

# Check for issues
flutter doctor

# Analyze code
flutter analyze
```

## Architecture

### Core Structure
- **main.dart**: App entry point using Provider for state management
- **BottomNav**: Main navigation container with 4 tabs (Home, Wallet, Stats, Profile)
- **ViewModel**: Global state management for dark/light theme using SharedPreferences
- **Repository**: Centralized color/theme management that responds to dark mode state

### Key Patterns
- **Provider Pattern**: Uses `ChangeNotifierProvider` with `ViewModel` for state management
- **Repository Pattern**: `Repository` class provides context-aware styling based on theme state
- **Static Data**: JSON files in `/lib/json/` contain mock data for transactions and shortcuts
- **Theme System**: Dynamic theming through `Repository` static methods that check `ViewModel.isDark`

### State Management
The app uses a simple Provider pattern with a single `ViewModel`:
- Manages `isDark` boolean for theme switching
- Persists theme preference using SharedPreferences
- All UI components get theme colors through `Repository` helper methods

### Custom Assets
- Custom fonts: DMSans family (Regular, Medium, Bold) and Iconly icons
- Card images in `/assets/cards/`
- Memoji avatars in `/assets/memoji/`
- Generated asset constants in `/lib/generated/assets.dart`

### Dependencies
- `provider`: State management
- `shared_preferences`: Theme persistence  
- `fl_chart`: Chart rendering for stats
- `gap`: Spacing widgets
- `cupertino_icons`: iOS-style icons

### Navigation
Uses bottom navigation with 4 main screens. Navigation between screens uses MaterialPageRoute for additional screens like SendMoney and AddCard.

## Testing
Standard Flutter testing with `flutter test`. Widget tests are located in `/test/widget_test.dart`.