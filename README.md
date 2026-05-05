# PuPath

PuPath is a mobile-first campus tour web app for Xi'an Jiaotong-Liverpool University (XJTLU), SIP Campus. It combines map navigation, guided tours, recommendations, check-ins, and story cards into one integrated experience.

- Target users: freshmen, current students, visitors, and staff
- Form: PWA (installable on desktop/mobile)
- Deployment: GitHub Pages

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

## Tech Stack

- **Framework**: React 19 + TypeScript
- **Build tool**: Vite 7
- **Routing**: React Router 7
- **State management**: Zustand
- **i18n**: i18next + react-i18next
- **Map**: AMap JS API (primary) + MapLibre (fallback rendering)
- **Styling**: Tailwind CSS
- **PWA**: vite-plugin-pwa
- **Testing**: Vitest, Playwright

---

## Project Structure

```text
PuPath/
├─ src/
│  ├─ app/                 # App entry and shell
│  ├─ components/          # UI and map components
│  ├─ config/              # Runtime config and campus center
│  ├─ data/                # Local data sources (pois/routes/recommendations/...)
│  ├─ hooks/               # Business hooks (weather, badge auto-unlock, ...)
│  ├─ locales/             # i18n resources (zh/en)
│  ├─ pages/               # Page modules
│  ├─ router/              # Route definitions
│  ├─ services/            # Map and weather services
│  ├─ stores/              # Zustand stores
│  ├─ types/               # TypeScript types
│  └─ utils/               # Utilities (coordinates, storage, progress, ...)
├─ public/                 # Static assets
├─ .github/workflows/      # GitHub Pages workflow
└─ dist/                   # Build output
```

---

## Local Development

### 1. Requirements
- Node.js 20+
- npm 10+

### 2. Install dependencies
```bash
npm install
```

### 3. Configure environment variables
Copy `.env.example` to `.env`:

```env
VITE_MAP_PROVIDER=amap
VITE_AMAP_KEY=
VITE_AMAP_SECURITY_JS_CODE=
VITE_MAPTILER_KEY=
VITE_WEATHER_PROVIDER=openmeteo
```

Notes:
- Recommended map provider: `VITE_MAP_PROVIDER=amap`
- Coordinate system is maintained in **GCJ-02** (aligned with AMap)
- Open-Meteo weather API does not require an API key by default

### 4. Run dev server
```bash
npm run dev
```

### 5. Build and preview
```bash
npm run build
npm run preview
```

---

## NPM Scripts

```bash
npm run dev        # Start development server
npm run build      # Type-check + production build
npm run preview    # Preview production build
npm run typecheck  # TypeScript check only
npm run lint       # Run ESLint
npm run test       # Run Vitest in watch mode
npm run test:run   # Run Vitest once
npm run e2e        # Run Playwright E2E tests
```

---

## Deployment (GitHub Pages)

This repository includes an automated GitHub Pages workflow:
- File: `.github/workflows/deploy.yml`
- Trigger: push to `main`
- Published artifact: `dist/`

### First-time setup
1. Open repository **Settings** → **Pages**
2. Set source to **GitHub Actions**
3. Push to `main` and wait for **Deploy PuPath to GitHub Pages** to complete

### Manual fallback deployment (optional)
If GitHub Actions is unavailable, run `npm run build` locally and deploy the `dist` content manually.

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
