# Timezone World Board

A single self-contained webpage for seeing the time around the world and
converting a reference time (e.g. "12 PM ET tomorrow") into every location's
local time — no more manual timezone math.

## Usage

Open `index.html` in any browser. That's it — no build step, no server, and it
works offline.

When deploying (hosted at `https://n2g.dev/timezone/`), upload `og-card.png`
alongside `index.html` so the social/Slack preview image resolves. The Open
Graph URLs in `index.html` point at that path — update them if the host changes.

## What it does

- **Now (live)** — every location ticks in real time.
- **Reference time** — enter a time, a date (Today / Tomorrow / pick), and the
  zone it's in (type `ET`, `PT`, `Tokyo`, an IANA name, …). The whole board
  recomputes to show that single instant everywhere.
- **World map** with a pin per location, colored by working / awake / asleep,
  plus day/night shading that tracks the displayed time.
- **Timezone regions** — faint offset bands on the map; hover one to see its
  current (DST-aware) offset and time. Toggle with the "Timezone zones" checkbox.
- **City cards** — 12- and 24-hour time, date, timezone abbreviation, UTC
  offset, and a work/sleep status, sorted west → east.
- **Editable locations** — add any of ~170 cities (or any IANA zone), remove
  with the ✕, "Reset to defaults" restores the starting set. Your list and
  preferences are saved in the browser (`localStorage`).

## How it works

All timezone math uses the browser's built-in `Intl` API, so DST, abbreviations,
and offsets are always correct without any bundled timezone database. The map is
inline SVG; cities are projected by latitude/longitude, and the day/night
terminator is computed from the sun's position at the displayed instant.

## Notes

- Timezone bands are the cartographic offset regions (generalized shapes). The
  per-city **cards** are the source of truth for an exact location.
- Everything lives in `index.html` — geometry and data are embedded.

## Credits

Map and timezone geometry from
[Natural Earth](https://www.naturalearthdata.com/) (public domain).
