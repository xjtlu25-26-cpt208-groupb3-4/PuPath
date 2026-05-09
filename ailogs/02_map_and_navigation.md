# 02 - Map & Navigation Core

## Primary Prompt A
Integrate map and touring behavior so that:
- Home/Tours can start navigation and jump to Map.
- Route navigation and direct point-to-point navigation are separated.
- Route state supports: progress, next stop, manual check-in, return to tours page, end navigation.

## Primary Prompt B
Switch map provider to AMap and keep campus navigation working.  
Requirements:
- Keep campus POI overlay.
- Use AMap route planning for realistic walking paths (not only straight lines).
- Preserve UI style.

## Primary Prompt C
Implement cross-campus routing strategy with underground passage priority:
- Support north/south campus crossing via defined tunnel entries/exits.
- Add transition segments from south underground exit to ground routes.
- Handle re-routing robustness when GPS is unstable underground.

## Primary Prompt D
Map UX adjustments:
- Return-to-current-location behavior improvements on mobile/WeChat.
- Keep map controls aligned in one row with horizontal scrolling if needed.
- Keep category toggles consistent in both Chinese and English UI.
