# Chhaon (छाँव) – Shade-First Heat Safety for Outdoor Workers

CodeQuest National Tech Hackathon 2026 – prototype submission.

Chhaon scores every road segment for **felt heat** (air temperature, humidity, solar load, building shadows, tree cover), routes workers through shade, and tracks a personal **Heat Dose** that triggers rest before heat illness, with Hindi voice alerts.

## Live demo
[Add your deployment link here – see "Deploy" below]

## Run locally
No build step and no dependencies.

```bash
git clone https://github.com/<your-username>/chhaon.git
cd chhaon
python3 -m http.server 8000   # or just open index.html in a browser
# visit http://localhost:8000
```

## How to use the demo
1. Click the map to set start **A** and destination **B**.
2. Move **Time of day**, **Temperature**, **Humidity** and watch shadows and road heat change.
3. Raise **Shade preference** to trade a little time for much less exposure. Compare the two route cards.
4. Press **Simulate worker shift**: two riders repeat trips; the shortest-route rider hits the Heat Dose limit first and is sent to the nearest water and shade point (optional Hindi voice alert).

## Core features implemented
| Feature | How it works |
|---|---|
| Street-level Feels-Like Load | Steadman apparent temperature + solar term scaled by sun elevation, reduced by shade and tree cover |
| Live sun shadows | Geometric shadow casting from building heights and sun azimuth/elevation |
| Shade-first routing | Dijkstra with cost = distance × (1 + k × heat above coolest road) |
| Heat Dose | Sum of (feels-like − 36 °C) × minutes, with a rest threshold |
| Rest and water-point alerts | Nearest water point, optional Hindi speech (Web Speech API) |

## Prototype scope (honest notes)
- Runs on a **synthetic city grid** so it works offline with zero setup.
- The Heat Dose threshold is illustrative, not clinically validated, and this is not medical advice.

## Roadmap (real data)
1. Load OpenStreetMap buildings and roads for a pilot zone (Delhi-NCR).
2. Add Landsat/Sentinel surface temperature and tree cover; downscale with LightGBM.
3. Swap grid routing for pgRouting/Valhalla with heat-weighted cost.
4. WhatsApp Cloud API bot and Bhashini voice for low-data phones.
5. Validate against handheld street-temperature readings.

## Deploy (free)
Push to GitHub, then Settings → Pages → Deploy from branch `main` / root. The demo link will be `https://<your-username>.github.io/chhaon/`.

## Screenshots
Add 2–3 screenshots to `docs/` and link them here.

## License
MIT
