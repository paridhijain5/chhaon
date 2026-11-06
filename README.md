# Chhaon (छाँव) – Shade-First Heat Safety for Outdoor Workers

**CodeQuest National Tech Hackathon 2026 – Prototype Submission**

Chhaon scores every road segment for **felt heat** (air temperature, humidity, solar load, building shadows, tree cover) and routes workers through shade. It also tracks a personal **Heat Dose** that triggers rest before heat illness, with Hindi voice alerts.

> **Route by how it feels, not how far it is.**

## Live Demo
**https://paridhijain5.github.io/chhaon/**

Demo video: [add link here]

## The Problem
Millions of delivery riders, construction workers and street vendors work through heatwaves with no street-level heat information. Heat alerts cover a whole district, navigation apps pick the fastest (often sunniest) route, and nobody tracks cumulative heat exposure.

## Our Solution
1. **Feels-Like Load map**: a street-level heat score for every road segment.
2. **Shade-first routing**: trades a few minutes for much less sun exposure and suggests water and shade stops.
3. **Heat Dose (USP)**: a cumulative exposure meter, like a step counter for heat, that prompts rest before illness, not after.
4. **Hindi voice alerts**: low-friction guidance for workers.

## How to Use the Demo
1. Click the map to set start **A** and destination **B**.
2. Move **Time of day**, **Temperature** and **Humidity** to see shadows and road heat change.
3. Raise **Shade preference** and compare the Shortest route and Chhaon route cards.
4. Press **Simulate worker shift**. Two riders repeat trips, and the shortest-route rider reaches the Heat Dose limit first and is sent to the nearest water and shade point. Tick **Hindi voice alert** to hear the prompt.

## Core Features Implemented
| Feature | How it works |
|---|---|
| Street-level Feels-Like Load | Steadman apparent temperature plus a solar term scaled by sun elevation, reduced by shade and tree cover |
| Live sun shadows | Geometric shadow casting from building heights and sun azimuth/elevation |
| Shade-first routing | Dijkstra with cost = distance × (1 + k × heat above the coolest road) |
| Heat Dose | Sum of (feels-like − 36 °C) × minutes, with a rest threshold |
| Rest and water-point alerts | Nearest water point, optional Hindi speech (Web Speech API) |

## Run Locally
No dependencies and no build step.

```bash
git clone https://github.com/paridhijain5/chhaon.git
cd chhaon
python -m http.server 8000
```
Then open **http://localhost:8000** (on Mac/Linux use `python3`). You can also just double-click `index.html`.

## Tech Stack
HTML5 Canvas, vanilla JavaScript, Web Speech API, GitHub Pages.
Planned for the full version: Python, GeoPandas, pybdshadow, LightGBM, PostGIS, pgRouting/Valhalla, FastAPI, WhatsApp Cloud API, React PWA.

## Prototype Scope
- The MVP runs on a **synthetic city grid** so it works offline with zero setup.
- The Heat Dose threshold is illustrative and not clinically validated. This is not medical advice.

## Roadmap
1. Load OpenStreetMap buildings and roads for a pilot zone in Delhi-NCR.
2. Add Landsat/Sentinel surface temperature and tree cover, then downscale with LightGBM.
3. Replace grid routing with pgRouting/Valhalla using heat-weighted cost.
4. Add a WhatsApp bot and Bhashini voice for low-data phones.
5. Validate predictions against handheld street-temperature readings.

## Impact
Safer routes and timely rest for outdoor workers, data-backed rest schedules for platforms and employers, and heat-equity maps that show cities where to add shade and water points first. Supports SDG 3, 8, 11 and 13.

## Team
Vanta · Paridhi Jain · Symbiosis International University

## License
MIT
