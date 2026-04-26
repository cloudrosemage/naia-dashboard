# 📖 Data Dictionary — NAIA Air Traffic Dashboard

**Source:** Aviationstack REST API (`/v1/flights`)  
**Airport Filter:** `arr_iata=MNL` (arrivals) · `dep_iata=MNL` (departures)  
**Last Updated:** 2026  

---

## API Response Structure

Each flight record returned by Aviationstack is a JSON object with the following top-level fields. This dictionary documents every field consumed by the dashboard.

---

## 1. `flight_date`

| Property | Detail |
|---|---|
| **Type** | `string` |
| **Format** | `YYYY-MM-DD` |
| **Example** | `"2026-04-25"` |
| **Description** | The scheduled date of the flight in UTC. |
| **Used in dashboard** | Date badge on card headers |
| **Free tier** | ✅ Available |

---

## 2. `flight_status`

| Property | Detail |
|---|---|
| **Type** | `string (enum)` |
| **Example** | `"scheduled"` |
| **Description** | The current operational status of the flight. |
| **Free tier** | ✅ Available |

**Possible values:**

| Value | Meaning | Dashboard display |
|---|---|---|
| `scheduled` | Flight is planned but not yet departed | Blue badge |
| `active` | Flight is currently airborne | Green badge |
| `landed` | Flight has arrived at destination | Grey badge |
| `cancelled` | Flight has been cancelled | Red badge |
| `incident` | Flight experienced an in-air incident | Red badge |
| `diverted` | Flight was redirected to another airport | Amber badge |
| `delayed` | Flight is delayed (used in some responses) | Red badge |
| `unknown` | Status could not be determined | Grey badge |

**Dashboard usage:** KPI on-time rate, delay stats, status distribution bars, flight board badges.

---

## 3. `departure` (object)

| Property | Detail |
|---|---|
| **Type** | `object` |
| **Description** | All data related to the departure end of the flight. |

### Sub-fields:

| Field | Type | Example | Description | Free tier |
|---|---|---|---|---|
| `airport` | string | `"Ninoy Aquino International"` | Full airport name | ✅ |
| `iata` | string | `"MNL"` | IATA airport code (3 letters) | ✅ |
| `icao` | string | `"RPLL"` | ICAO airport code (4 letters) | ✅ |
| `terminal` | string | `"1"` | Departure terminal number | ✅ |
| `gate` | string | `"G12"` | Departure gate identifier | ✅ |
| `scheduled` | string (ISO 8601) | `"2026-04-25T06:00:00+00:00"` | Scheduled departure time | ✅ |
| `estimated` | string (ISO 8601) | `"2026-04-25T06:15:00+00:00"` | Estimated departure time | ✅ |
| `actual` | string (ISO 8601) | `"2026-04-25T06:18:00+00:00"` | Actual departure time | ✅ |
| `estimated_runway` | string (ISO 8601) | `"2026-04-25T06:20:00+00:00"` | Estimated runway-off time | ✅ |
| `actual_runway` | string (ISO 8601) | `"2026-04-25T06:22:00+00:00"` | Actual runway-off time | ✅ |
| `delay` | integer | `18` | Delay in minutes (positive = late) | ✅ |
| `timezone` | string | `"Asia/Manila"` | Timezone of the departure airport | ✅ |

**Dashboard usage:** Route display, scheduled time column in flight board, delay calculation.

---

## 4. `arrival` (object)

| Property | Detail |
|---|---|
| **Type** | `object` |
| **Description** | All data related to the arrival end of the flight. |

### Sub-fields:

| Field | Type | Example | Description | Free tier |
|---|---|---|---|---|
| `airport` | string | `"Changi Airport"` | Full airport name | ✅ |
| `iata` | string | `"SIN"` | IATA airport code | ✅ |
| `icao` | string | `"WSSS"` | ICAO airport code | ✅ |
| `terminal` | string | `"3"` | Arrival terminal number | ✅ |
| `gate` | string | `"A24"` | Arrival gate identifier | ✅ |
| `baggage` | string | `"Belt 4"` | Baggage carousel assignment | ✅ |
| `scheduled` | string (ISO 8601) | `"2026-04-25T10:00:00+00:00"` | Scheduled arrival time | ✅ |
| `estimated` | string (ISO 8601) | `"2026-04-25T10:22:00+00:00"` | Estimated arrival time | ✅ |
| `actual` | string (ISO 8601) | `"2026-04-25T10:28:00+00:00"` | Actual arrival time | ✅ |
| `estimated_runway` | string (ISO 8601) | — | Estimated runway-on time | ✅ |
| `actual_runway` | string (ISO 8601) | — | Actual touchdown time | ✅ |
| `delay` | integer | `28` | Delay in minutes | ✅ |
| `timezone` | string | `"Asia/Singapore"` | Timezone of the arrival airport | ✅ |

**Dashboard usage:** Route display, arrival time column, delay computation.

---

## 5. `airline` (object)

| Field | Type | Example | Description | Free tier |
|---|---|---|---|---|
| `name` | string | `"Philippine Airlines"` | Full airline name | ✅ |
| `iata` | string | `"PR"` | IATA airline code (2 letters) | ✅ |
| `icao` | string | `"PAL"` | ICAO airline code (3 letters) | ✅ |

**Dashboard usage:** Airline share donut chart, airline ranking bars, flight board airline column.

---

## 6. `flight` (object)

| Field | Type | Example | Description | Free tier |
|---|---|---|---|---|
| `number` | string | `"107"` | Flight number (without airline code) | ✅ |
| `iata` | string | `"PR107"` | Full IATA flight identifier | ✅ |
| `icao` | string | `"PAL107"` | Full ICAO flight identifier | ✅ |
| `codeshared` | object/null | `null` | Codeshare partner info, if applicable | ✅ |

**Dashboard usage:** Flight number column in flight board, ticker strip.

---

## 7. `aircraft` (object)

| Field | Type | Example | Description | Free tier |
|---|---|---|---|---|
| `registration` | string | `"RP-C7772"` | Tail number / registration | ⚠️ Paid |
| `iata` | string | `"A321"` | Aircraft IATA type code | ⚠️ Paid |
| `icao` | string | `"A321"` | Aircraft ICAO type code | ⚠️ Paid |
| `icao24` | string | `"7C1234"` | 24-bit ICAO transponder address | ⚠️ Paid |

> ⚠️ **Aircraft fields are restricted on the free Aviationstack tier.** The dashboard displays a fallback message when this data is unavailable.

**Dashboard usage:** Aircraft type grid, aircraft count KPI.

---

## 8. `live` (object)

| Field | Type | Example | Description | Free tier |
|---|---|---|---|---|
| `updated` | string (ISO 8601) | `"2026-04-25T08:14:00+00:00"` | Last ADS-B update timestamp | ⚠️ Paid |
| `latitude` | float | `14.5086` | Current aircraft latitude | ⚠️ Paid |
| `longitude` | float | `121.0194` | Current aircraft longitude | ⚠️ Paid |
| `altitude` | float | `8534.4` | Altitude in meters | ⚠️ Paid |
| `direction` | float | `276.0` | Heading in degrees (0–360) | ⚠️ Paid |
| `speed_horizontal` | float | `829.5` | Ground speed in km/h | ⚠️ Paid |
| `speed_vertical` | float | `0.0` | Vertical speed in m/s | ⚠️ Paid |
| `is_ground` | boolean | `false` | Whether aircraft is on ground | ⚠️ Paid |

> ⚠️ **Live position data requires a paid Aviationstack plan.** The dashboard map uses estimated positions for free-tier users.

**Dashboard usage:** Live aircraft map positions.

---

## Computed / Derived Metrics

These values are not returned directly by the API but are calculated by the dashboard from raw fields:

| Metric | Formula | Notes |
|---|---|---|
| **Total flights** | `arrivals.length + departures.length` | From two API calls |
| **On-time rate** | `(active + landed + scheduled) / total × 100` | Approximation — delayed flights not always flagged |
| **Delay count** | `flights where flight_status === 'delayed' OR departure.delay > 0` | |
| **Airline share %** | `count per airline / total flights × 100` | |
| **Runway utilization** | Estimated from total flight volume as a proportion of NAIA capacity | Not from API; CAAP has no public endpoint |
| **Terminal load** | Estimated from departure terminal field where available | Partial data on free tier |

---

## API Limits — Free Tier

| Limit | Value |
|---|---|
| Monthly API calls | 100 |
| Results per call | 100 |
| Calls per dashboard refresh | 2 (arrivals + departures) |
| Max monthly refreshes | 50 |
| Historical data access | ❌ No |
| Aircraft type fields | ❌ No |
| Live GPS position | ❌ No |

---

## IATA Airport Codes Referenced

| Code | Airport | Country |
|---|---|---|
| MNL | Ninoy Aquino International Airport | Philippines |
| CEB | Mactan-Cebu International Airport | Philippines |
| SIN | Singapore Changi Airport | Singapore |
| HKG | Hong Kong International Airport | Hong Kong |
| ICN | Incheon International Airport | South Korea |
| NRT | Narita International Airport | Japan |
| DXB | Dubai International Airport | UAE |
| SYD | Kingsford Smith International Airport | Australia |
| DOH | Hamad International Airport | Qatar |

---

*Data dictionary based on Aviationstack API v1 documentation. Subject to change with API updates.*
