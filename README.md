# PuPath

PuPath is a mobile-first campus tour web app for Xi'an Jiaotong-Liverpool University (XJTLU), SIP Campus. It combines map navigation, guided tours, recommendations, check-ins, and story cards into one integrated experience.

- Target users: freshmen, current students, visitors, and staff
- Form: PWA (installable on desktop/mobile)
- Deployment: GitHub Pages
- Live URL: [https://xjtlu25-26-cpt208-groupb3-4.github.io/PuPath/](https://xjtlu25-26-cpt208-groupb3-4.github.io/PuPath/)

---

## Key Features

### 1. Map & Navigation
- AMap (Gaode) base map and location services
- Layered campus POIs (Study / Service / Leisure / Cat / Flower)
- Tap-to-navigate from map markers
- Cross-campus routing with underground-passage priority (including south-exit connector)
- Browser-based voice guidance (Web Speech API)

### 2. Tours
- Core tours, theme tours, and custom tours
- Route details, progress tracking, and manual stop check-in
- Tour page and map page linkage

### 3. Discover & Place Detail
- Category-based recommendations (food, photography, campus cats, flowers, museum, etc.)
- Place detail pages (images, opening time, tags, related routes)
- Story cards (place narrative + tailored recommendations)

### 4. Check-in & Collectibles
- Location-based check-in (once per day)
- Virtual collectibles (Captain Bird / XJTLU Bear, Blue/Purple/Gold rarity)
- Badge system with auto-unlock rules

### 5. Profile & Accessibility
- Favorites, wishlist, visited, and recent views
- Accessibility options (font size levels, high contrast, screen-reader support)
- Clear local records (global local data reset)

---

## Playful Features (Core Feature Set)

The system includes more than 3 must-have playful features:

1. **Location Check-in + Random Collectibles** (`/scan`)  
   Users can check in once per day inside the campus area and receive a random virtual collectible (Captain Bird / XJTLU Bear, Blue/Purple/Gold rarity).

2. **Badge Unlock System** (`/my`)  
   Interaction milestones (exploration, check-in progress, behavior completion) unlock visual badges and earned-time records.

3. **Story Cards for POIs** (`/tours`, `/map`)  
   Contextual story cards provide place narratives and tailored recommendations by POI type (study, food, cat, flower, etc.).

4. **Theme-based Exploration Layers** (`/map`, `/discover`)  
   Users can explore campus by themed categories (Cat, Flower, Photography, Museum, Food) with linked detail and navigation actions.

---

## Tech Stack

- **Frontend runtime**: static web app (deployed build)
- **Source project stack**: React + TypeScript + Vite
- **Map**: AMap (Gaode) JS API
- **Weather**: Open-Meteo
- **PWA artifacts**: `manifest.webmanifest`, `registerSW.js`, `sw.js`, `workbox-*.js`

---

## Project Structure

```text
PuPath/
├─ ailogs/                 # AI prompts used for core components
├─ assets/                 # Bundled JS/CSS assets
├─ badges/                 # Badge images
├─ icons/                  # App icons and PWA icons
├─ images/
│  └─ pois/                # POI images
├─ treasures/              # Treasure collectible images
├─ README.md
├─ data-handling.md        # Data handling evidence for submission
├─ index.html
├─ manifest.webmanifest
├─ registerSW.js
├─ sw.js
└─ workbox-*.js
```

---

## AI Logs

This project includes an `/ailogs` folder containing the primary prompts used in AI-assisted coding for core components (Vibe Coding Logs).

---

## Data Handling

Data handling evidence is documented in:

- [data-handling.md](./data-handling.md)

---

## Deployment (GitHub Pages)

This repository is the **public deployment repository** and can be hosted directly with GitHub Pages.

### Recommended Pages settings
1. Open repository **Settings** → **Pages**
2. Set source to **Deploy from a branch**
3. Select branch `main`, folder `/ (root)`
4. Save and wait for the site URL to become active

### Updating this repository after new builds

When you produce a new build from your development workspace, copy updated static files to this repository root:
- `index.html`
- `assets/`
- `icons/`
- `images/`
- `badges/`
- `treasures/`
- `manifest.webmanifest`
- `registerSW.js`
- `sw.js`
- `workbox-*.js`

Then commit and push to `main`.

### Minimal setup / update checklist

1. Build the latest production output from your development workspace.
2. Replace root static files/folders in this repository with the latest build artifacts.
3. Commit and push to `main`.
4. Open the live URL and verify:
   - home page loads without console errors
   - map renders and recenter works
   - at least one route can start navigation
   - check-in page is reachable

---

## Performance Notes

Current optimizations include:
- Map styles are loaded on demand (only when map-related pages are opened)
- PWA precache excludes heavy map bundles to reduce first-install and first-load size

---

## Pre-release Checklist (Recommended)

- Location, recenter, and cross-campus underground routing
- Full bilingual verification (labels, story cards, recommendation text)
- Daily check-in limit and collectible/badge linkage
- Compatibility in WeChat in-app browser (iOS/Android)
- GitHub Pages cache/version update behavior

---

## Disclaimer

This project is built for course and demo scenarios. Map data, routing logic, and POI content will continue to evolve.
