# Chhaon (छाँव): Shade-First Heat Safety for Outdoor Workers

**Team Vanta · Paridhi Jain**
CodeQuest National Tech Hackathon 2026: Final Build & Innovation Showcase

> **Route by how it feels, not how far it is.**

Chhaon scores every road segment for **felt heat** (temperature, humidity, solar load, live building shadows, tree cover) and routes outdoor workers through shade. A personal **Heat Dose** meter tracks cumulative exposure and prompts rest before heat illness, with Hindi voice alerts and WhatsApp sharing.

## Live Demo
**https://paridhijain5.github.io/chhaon/**


## The Problem
Millions of delivery riders, construction workers and street vendors work through heatwaves with no street-level heat information. Heat alerts cover a whole district, navigation apps pick the fastest (often the sunniest) route, and nobody tracks the heat a worker has accumulated.

## Our Solution
1. **Feels-Like Load map:** a street-level heat score for every road segment, updated with time of day and weather.
2. **Shade-first routing:** trades a few minutes for much less sun, compared side by side with the shortest route.
3. **Heat Dose (USP):** a cumulative exposure meter, like a step counter for heat, that prompts rest before illness, not after.
4. **Worker-aware alerts:** Hindi voice prompts and one-tap WhatsApp sharing, sent with the nearest water point.

## Features
| Feature | How it works |
|---|---|
| Live sun shadows | Geometric shadow casting from building heights and sun position across the day |
| Feels-Like Load | Apparent temperature plus a solar term, reduced by shade and tree cover |
| Shade-first routing | Dijkstra with a heat-weighted edge cost and an adjustable shade preference |
| Live weather | Current temperature and humidity from the free Open-Meteo API, with a manual-slider fallback |
| Worker profiles | Delivery rider, construction labourer and street vendor build Heat Dose at different rates |
| Heat Dose shift simulation | Two riders repeat trips; the shortest-route rider reaches the rest limit first |
| Hindi voice alerts | Spoken rest prompts using the Web Speech API (hi-IN) |
| Heat equity map | Highlights the best sites for new water and shade points |
| WhatsApp share | One tap shares a heat alert in English and Hindi |

## Run Locally
```bash
git clone https://github.com/paridhijain5/chhaon.git
cd chhaon
python -m http.server 8000
```
Open **http://localhost:8000** (use `python3` on Mac/Linux). You can also open `index.html` directly. Live weather needs an internet connection and falls back to the manual sliders if unavailable.

## Tech Stack
HTML5, CSS, JavaScript, Canvas, Open-Meteo API, Web Speech API, Geolocation API, GitHub Pages.
Planned for production: Python, GeoPandas, pybdshadow, LightGBM, PostGIS, pgRouting, FastAPI, WhatsApp Cloud API, Bhashini.

## Prototype Scope
- The MVP runs on a **synthetic city grid** so it works with zero setup.
- Heat Dose thresholds are illustrative, not clinically validated. This is not medical advice.

## Roadmap
1. Real-data pilot in Delhi-NCR with OpenStreetMap and satellite heat layers, validated against street-temperature readings.
2. WhatsApp bot with Bhashini voice for low-data phones.
3. Employer rest-scheduling and city heat-equity dashboards.
4. Air-quality-aware routing on the same engine.

## Impact
Safer routes and timely rest for outdoor workers, data-backed rest schedules for platforms and employers, and heat-equity maps that show cities where to add shade and water first. Supports SDG 3, 8, 11 and 13.
