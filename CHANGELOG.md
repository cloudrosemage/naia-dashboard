# 📋 Changelog — NAIA Air Traffic Dashboard

All notable changes to this project are documented here.  
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [2.0.0] — April 2026
### Portfolio Edition — Full Rebuild (Complete)

#### Added
- Complete visual redesign from scratch with editorial aviation aesthetic
- Bebas Neue + DM Mono + Geist font pairing
- Live aircraft map panel with SVG-based MNL airspace visualization
- Animated radar pulse effect on map
- Terminal breakdown panel (T1, T2, T3, Cargo)
- Weekly trend chart panel
- Live ticker strip showing flight numbers and statuses
- Staggered entrance animations on all cards and KPIs
- Micro-interactions on hover for all interactive elements
- Maximum visual flair: animated bar charts, donut, KPI counters
- Responsive layout for tablet and desktop

#### Changed
- Font changed from DM Sans + Syne → Bebas Neue + DM Mono + Geist
- KPI cards redesigned as a unified strip
- Flight board now shows 14 flights (up from 8)
- Donut chart redrawn with smoother canvas rendering
- API key setup screen redesigned with dark full-screen aesthetic

---

## [1.1.0] — April 2026
### Font & Polish Update

#### Changed
- Global font changed from DM Sans + Syne to **Inter** across all elements
- Minor spacing refinements on KPI cards

---

## [1.0.0] — April 2026
### Initial Release — Aviationstack Integration

#### Added
- Aviationstack REST API integration for live MNL arrivals and departures
- Secure API key setup screen (browser-session only, never stored)
- Auto-refresh every 5 minutes
- KPI strip: total flights, arrivals, departures, on-time rate, active aircraft
- Hourly arrivals vs departures bar chart (by flight status)
- Runway utilization panel (4 runways with estimated load)
- Live flight board (8 flights with status badges)
- Airline share donut chart (canvas-based)
- Delay statistics panel with status distribution bars
- Top airlines ranking (horizontal bar chart)
- Aircraft types grid + fleet age distribution
- Arrivals vs departures direction split
- Deployed to GitHub Pages at cloudrosemage.github.io/naia-air-traffic-dashboard
- Change Key button for switching API keys
- Last updated timestamp in header

#### Known Issues
- Aircraft type data unavailable on free Aviationstack tier
- Map panel not yet implemented
- Runway utilization is estimated, not sourced from live data
- Weekly trend requires historical API access

---

## [0.1.0] — April 2026
### Prototype — Static Dashboard

#### Added
- Initial static dashboard with hardcoded/simulated data
- Clean & modern light theme
- 8 data panels: KPIs, bar chart, runway, flight board, donut, delays, airline ranking, aircraft types
- DM Sans + Syne typography
- Deployed as single HTML file
