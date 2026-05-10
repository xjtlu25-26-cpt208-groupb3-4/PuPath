# Data Handling (System Evidence)

This document summarizes how PuPath handles user input and interaction states in the live system.

## 1. Input Sources

- **Map interactions**: marker tap, map tap, recenter action, route start/end, manual arrival check-in.
- **Tour interactions**: start tour, preview route, custom route point selection, audio toggle.
- **Discover/Place interactions**: category filter, add to route, favorite/want-to-go/been-there.
- **Check-in interactions**: location-based daily check-in and collectible generation.
- **Profile/Settings interactions**: accessibility options, clear local records, language/identity switching.

## 2. State Management

PuPath uses **Zustand** for app state.

- `userStore`
  - identity, language
  - accessibility preferences
  - favorites / want-to-go / been-there
  - unlocked badges + unlock timestamps
  - recent views
  - treasure inventory
  - check-in date records
- `tourStore`
  - current route, preview route
  - checked stops and progress
  - custom route draft points
  - audio guidance toggle
- `appStore`
  - app-level UI/session state used across pages

## 3. Persistence

- User-related states are persisted locally (browser storage) through Zustand `persist`.
- Language preference is synchronized and restored on reload.
- State survives refresh and revisits unless manually cleared.

## 4. Data Processing Rules

- **Navigation**
  - route mode and direct point-to-point mode are separated.
  - cross-campus routing prioritizes predefined underground passage strategy.
- **Check-in**
  - position validation against configured campus area.
  - one successful check-in per day.
  - collectible rarity logic: Blue 70% / Purple 20% / Gold 10%.
- **Badges**
  - auto-unlock based on interaction milestones (e.g., service visits, photo favorites, cat exploration, check-in count).

## 5. Output Binding

State changes immediately update UI across pages:

- Home, Map, Tours, Discover, Place Detail, Scan, My, Accessibility.
- Examples:
  - adding a POI to route in Discover updates custom route draft in Tours;
  - check-in result updates treasure backpack and related badge conditions in My;
  - accessibility settings affect global rendering through the app shell.

## 6. Data Reset

- “Clear local records” performs global local reset of user interaction data and related route/app session states.
- After reset, personalization and progress indicators return to initial defaults.

