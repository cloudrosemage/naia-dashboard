# Analytics Dashboard: Live Air Traffic Data Over Ninoy Aquino International Airport (NAIA)

![Status](https://img.shields.io/badge/status-live-brightgreen)
![API](https://img.shields.io/badge/API-AviationStack-blue)
![Deployment](https://img.shields.io/badge/deployed-GitHub%20Pages-black)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

> A real-time, browser-based analytics dashboard that monitors live air traffic activity at **Ninoy Aquino International Airport (NAIA), Manila, Philippines** — built as a portfolio project to demonstrate data analytics, front-end web development, and REST API integration skills.

🔗 **Live Dashboard:** [cloudrosemage.github.io/naia-air-traffic-dashboard](https://cloudrosemage.github.io/naia-air-traffic-dashboard)

📄 **Project Documentation:** (https://www.notion.so/Aviation-Analytics-Dashboard-Live-Air-Traffic-Data-Over-Ninoy-Aquino-International-Airport-NAIA-34dcec93c31b80879fd7e3b197fa0a1f?source=copy_link)

👤 **Author:** John Miguel Co Molina · Remote Operations Support & Junior Data Analyst · [LinkedIn](https://linkedin.com/in/cloudrosemage

---

## 📸 Preview

<img width="1919" height="910" alt="image" src="https://github.com/user-attachments/assets/e013d961-f9be-4690-88c8-2ae09428db96" />


---

## 📋 Project Description

This project is a real-time, browser-based analytics dashboard that monitors live air traffic activity at Ninoy Aquino International Airport (NAIA), Manila, Philippines. It consumes live flight data from the AviationStack REST API and presents it in a visually compelling, management-grade interface covering arrivals, departures, delays, airline breakdown, runway utilization, terminal status, aircraft types, and trend analysis.

The dashboard is built as a single self-contained `index.html` file using vanilla HTML, CSS, and JavaScript — no frameworks, no build tools, no backend required. It is deployed and publicly accessible via GitHub Pages.

---

## 🎯 Project Purpose & Beneficiaries

This project was built with two interlocking purposes. The first is professional: to demonstrate a working command of data analytics, front-end web development, and REST API integration through a single, cohesive artifact. Rather than abstract exercises, the dashboard presents real computed metrics — on-time rates, delay distributions, airline share, and traffic volume — derived from live API data and rendered in a production-grade interface built without any frameworks or third-party libraries. The second purpose is practical: to document the full project lifecycle, from API research and data modeling to deployment and versioning, as a portfolio case study that reflects how real-world data projects are scoped, built, and maintained.

As a secondary objective, this project serves as an exploration of the aviation data landscape available to independent developers in the Philippines — mapping out what is publicly accessible, what requires formal agreements, and where the gaps are — and lays the groundwork for a more advanced version using paid data tiers or an eventual CAAP data-sharing arrangement.

The dashboard is designed to be useful to a range of stakeholders. Airport management at MIAA can use it for a real-time overview of traffic volume, delay patterns, runway load, and airline performance. Airline operations teams benefit from a quick reference for on-time rates and flight statuses. Aviation analysts gain a structured, visual representation of flight data that would otherwise require manual querying. Passengers can use the live flight board to check arrivals and departures at NAIA. For portfolio reviewers and recruiters, the project serves as direct, working evidence of data, front-end, and API skills applied to a locally relevant problem. Finally, the open-source codebase and accompanying documentation offer a practical reference for other developers looking to integrate AviationStack in a Philippine aviation context.

---

## 🧰 Tools & Technology

| Tool / Technology | Purpose |
|---|---|
| HTML5 | Page structure and layout |
| CSS3 | Styling, animations, CSS variables, Grid, Flexbox |
| JavaScript (ES6+) | API calls, DOM manipulation, canvas charts, SVG map |
| Canvas API | Donut chart rendering |
| SVG | Live aircraft map |
| Bebas Neue, DM Mono, Geist | Typography via Google Fonts |
| AviationStack REST API | Live flight data source |
| GitHub Pages | Free static site hosting and deployment |
| Git + GitHub | Version control and repository hosting |
| Notion | Project and process documentation |
| Claude (Anthropic) | AI-assisted code generation, design, and documentation |

---

## 📡 Main Data Source

**AviationStack** — [aviationstack.com](https://aviationstack.com)

AviationStack was selected as the primary data source after evaluating several aviation APIs available to independent developers in the Philippines. FlightRadar24 has no public API and is commercial-only. The Civil Aviation Authority of the Philippines (CAAP) has no public API and requires a formal data-sharing agreement. OpenSky Network is free and open but only provides raw ADS-B transponder data — it lacks flight numbers, airline names, schedules, and flight status, which are essential to this dashboard. AviationStack was the only option that provided all required fields (flight number, airline, route, status, delay, terminal) on a free tier with no credit card required.

| Property | Detail |
|---|---|
| **Base URL** | `https://api.aviationstack.com/v1/` |
| **Endpoint** | `/v1/flights` |
| **Filters used** | `arr_iata=MNL` · `dep_iata=MNL` |
| **Authentication** | API key as `?access_key=YOUR_KEY` |
| **Data format** | JSON |
| **Free tier** | 100 calls/month · 100 results/call · No historical data · No aircraft GPS |

### How to get your free API key

1. Go to [aviationstack.com](https://aviationstack.com) and click **"Get Free API Key"**
2. Fill in your name, email, and a password — no credit card required
3. Verify your email address via the confirmation link sent to your inbox
4. Log in and copy your key from the **"Your API Access Key"** section on the dashboard
5. Open the live dashboard and paste your key into the setup screen
6. Click **"Connect Dashboard"** — the dashboard authenticates and loads live data automatically

> ⚠️ **Free tier limits:** 100 API calls/month · 2 calls per refresh (arrivals + departures) · Auto-refreshes every 5 minutes · Your key is stored in your browser session only and is never transmitted anywhere except AviationStack's servers.

---

## 🚀 Getting Started

### Use the live version
Visit **[cloudrosemage.github.io/naia-air-traffic-dashboard](https://cloudrosemage.github.io/naia-air-traffic-dashboard)**, enter your AviationStack API key, and the dashboard loads immediately.

### Run locally
```bash
git clone https://github.com/cloudrosemage/naia-air-traffic-dashboard.git
cd naia-air-traffic-dashboard
# Open index.html in your browser — no build step required
open index.html
```

---

## 📁 Project Structure

```
naia-air-traffic-dashboard/
│
├── index.html            # Main dashboard (single-file application)
├── README.md             # This file
├── DATA_DICTIONARY.md    # AviationStack field definitions
└── CHANGELOG.md          # Version history
```

---

## 🏗️ Code Structure

The dashboard follows a **linear top-to-bottom architecture** organized into five layers within the single `index.html` file. There are no modules, imports, or build steps.

### Layer 1 — Document Head `<head>`
Declares page metadata and loads the only external dependency: the Google Fonts stylesheet (Bebas Neue, DM Mono, Geist). All other resources are self-contained within the file, making the dashboard fully portable — copying the single file is enough to deploy it anywhere.

### Layer 2 — CSS `<style>`
All styling lives in a single `<style>` block organized into clearly commented sections that mirror the visual layout from top to bottom. Key techniques used:

- **CSS custom properties** — the entire color system, shadows, and spacing are defined in `:root` so the theme can be changed from a single location
- **CSS Grid & Flexbox** — Grid handles the macro panel arrangement; Flexbox manages alignment within each card
- **`@keyframes` animations** — entrance animations, bar chart growth from zero, radar sweep rotation, and aircraft pulse rings
- **`animation-delay`** — staggered delays on cards and KPIs create a cascading reveal effect on load
- **Hover micro-interactions** — `transition` on `transform` and `box-shadow` gives every card, button, and row a tactile hover response
- **`@media` queries** — breakpoints at 1280px and 768px collapse the multi-column layout for tablet and mobile

### Layer 3 — HTML `<body>`
The body contains exactly two mutually exclusive top-level components — only one is visible at a time:

```
<body>
  ├── #setup        → full-screen API key entry (visible on load)
  └── #app          → the dashboard (hidden until key is validated)
        ├── <header>      → sticky navigation, live clock, controls
        ├── .ticker       → scrolling live flight strip
        └── .main         → all dashboard panels in document order
              ├── KPI strip (5 cards)
              ├── Live aircraft map + Status bar chart
              ├── Weekly trend chart
              ├── Live flight board + Runway status
              ├── Airline donut + Delay stats + Aircraft types
              ├── Airline ranking (full width)
              └── Terminal breakdown (4 cards)
```

Dashboard panels are laid out in the HTML in the exact order they appear visually on screen, keeping the document structure and visual layout in sync.

### Layer 4 — JavaScript `<script>`
The script block sits at the bottom of the `<body>`, after all HTML has been parsed, so every `document.getElementById()` call is guaranteed to find its target without needing `DOMContentLoaded` listeners. The logic follows a clear call hierarchy:

```
Constants & state
  └── API_KEY, AIRPORT, COLORS

Setup functions
  ├── toggleVis()     → show/hide API key input
  ├── connect()       → validate key → show dashboard → start data
  └── resetKey()      → clear key → return to setup screen

Initialization (runs once after key is validated)
  ├── initClock()     → 1-second interval clock
  ├── buildTrend()    → static weekly trend chart
  └── loadAll()       → first data fetch

Core data loop (every 5 minutes via setInterval)
  └── loadAll()
        ├── fetchF('arr')         → GET arrivals from AviationStack
        ├── fetchF('dep')         → GET departures from AviationStack
        └── render functions (all receive the same combined data)
              ├── updateKPIs()          → KPI strip + animated fill bars
              ├── buildTicker()         → scrolling flight header strip
              ├── buildBarChart()       → arrivals vs departures by status
              ├── buildFlightBoard()    → live 14-row flight table
              ├── buildAirlineDonut()   → canvas-based donut chart
              ├── buildDelayStats()     → delay mini cards + distribution bars
              ├── buildAircraftTypes()  → aircraft type grid + direction split
              ├── buildAirlineRanking() → top 10 airlines horizontal bars
              ├── buildTerminals()      → terminal load cards
              ├── updateMap()           → SVG aircraft map with pulse rings
              └── updateRunways()       → runway utilization bars

Helper functions
  ├── setKPI()        → reusable KPI value + bar updater
  └── setRwy()        → reusable runway value + bar updater
```

Each render function is **stateless and independent** — it receives data as an argument, computes what it needs, and writes directly to the DOM. No render function calls another, so any panel can be updated, removed, or replaced without affecting the rest.

### Layer 5 — Inline Animation Styles `<style>` *(end of body)*
A small second `<style>` block at the very end declares keyframe animations for the SVG radar sweep and aircraft pulse rings. These are placed after the SVG markup intentionally to avoid rendering inconsistencies in certain browsers where animations referencing SVG elements by class name must be defined after those elements are parsed.

---

## 📊 Dashboard Panels

| Panel | Data Source | Notes |
|---|---|---|
| KPI Strip | AviationStack live | Total flights, arrivals, departures, on-time rate, delays |
| Live Aircraft Map | AviationStack + estimated positions | Free tier lacks GPS; positions estimated around MNL |
| Status Bar Chart | AviationStack live | Arrivals vs departures grouped by `flight_status` |
| Weekly Trend Chart | Estimated | Historical data requires paid AviationStack tier |
| Live Flight Board | AviationStack live | Latest 14 flights with route, airline, time, and status |
| Runway Utilization | Estimated from flight volume | CAAP has no public runway data API |
| Airline Share Donut | AviationStack live | Computed from `airline.name` field |
| Delay Statistics | AviationStack live | Computed from `flight_status` field |
| Aircraft Types | AviationStack (paid) / fallback | Free tier does not return `aircraft.iata` |
| Airline Ranking | AviationStack live | Top 10 airlines by flight count |
| Terminal Breakdown | Partial live + estimated | From `departure.terminal` with proportional fallback |

---

## ⚠️ Known Limitations

- **Free tier cap:** 100 calls/month — monitor usage at [aviationstack.com](https://aviationstack.com)
- **Aircraft positions:** Free tier lacks GPS coordinates; map uses estimated positions relative to MNL
- **Aircraft types:** Only returned on paid AviationStack plans
- **Runway & terminal data:** Not available via any public NAIA or CAAP API; values are estimated
- **Weekly trend:** Requires AviationStack's paid historical data endpoint

---

## 🗺️ Roadmap

- [ ] Integrate OpenSky Network for real GPS aircraft positions on the map
- [ ] Add historical weekly trend using paid API tier
- [ ] Add route map with actual flight paths
- [ ] Expand to other Philippine airports (CEB, DVO, ILO)
- [ ] Add dark mode toggle
- [ ] Add CSV export for management reporting
- [ ] Pursue CAAP data-sharing agreement for official runway and terminal data

---

## 📄 License

MIT License — free to use, modify, and distribute with attribution.

---

*Data provided by AviationStack · Not affiliated with MIAA, CAAP, or any airline*
