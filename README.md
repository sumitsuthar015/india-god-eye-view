<div align="center">

# 🌐 God's Eye View

### A spy-satellite simulator in your browser — then you realize the sources are public and the data is real.

Photorealistic 3D globe. Live aircraft, ships, satellites, earthquakes, traffic, and public cameras. Hands-free voice control powered by a realtime AI agent.

*No place left behind.*
⚡ **Start without API keys.** Clone [India God's Eye View](https://github.com/sumitsuthar015/india-god-eye-view) or run it locally from the terminal. Add optional keys inside the app. **[→ Quick Start](#-quick-start)**

</div>

## 🌍 Why This Exists

God's Eye View brings public signals into one explorable globe. Track the world live. Talk to it. Break it. Extend it.

Flight transponders, ship beacons, orbital elements, seismographs, and public cameras already tell us a lot about the world. God's Eye View puts them in the same place, so you can move between a global picture and an individual aircraft, ship, or street. It runs locally in your browser, with source code you can inspect and extend.

> Half the magic is that it looks like a forbidden cockpit. The other half is that every line of code is inspectable.

Most feeds are live or regularly refreshed. Traffic is simulated along real
roads using aggregate location data. CCTV camera poses and rocket launch
trajectories are coarse estimates.

Start with the included data sources, then add your own. Each layer is a separate module.

---

## 🎛️ What This Thing Does

- **🛩️ Cockpit view:** Ride inside a tracked flight — the camera holds the terrain under you all the way down.
- **📡 Contacts:** A 250 km roster of everything near your target — step through live aircraft and drop into any cockpit.
- **🎯 Click-to-track anything:** Camera locks on, draws a fading trail, surfaces full metadata — and a tracked fire or vessel hands you off to the nearest live camera in one click.
- **🖊️ Voice whiteboard:** Speak annotations onto the world — real boundary polygons, marks, and routes.
- **🛫 3D hangar:** Real per-class aircraft models — 787, ATR-72, Citation, Bell 206, MQ-9 — and a tracked contact swaps from glyph to 3D model as you close in.
- **🎨 Reskin reality:** GLSL sensor looks over the normal globe — CRT, NVG, FLIR/thermal, Noir, Snow.
- **🟩 Detection overlay:** Screen-space bounding boxes and IDs on everything in view.
- **🎖️ Military HUD:** Tactical heads-up display with intelligence-style telemetry.
- **🌐 Global Context:** Stage the full situational picture with one switch — and get your exact view back when you leave.
- **🎥 Scene director:** Capture cinematic camera tours for clips and demos.
- **🔗 Share Links:** Camera, style, layers, and even one tracked target serialize into a URL — a live target is a handoff, not a bookmark.
- **🏠 Reset Globe:** One control — or one sentence — back to the full Earth.

---


## ⚡ Quick Start

**Start without an account or API keys.** Both paths open the same app with
Esri satellite imagery and keyless terrain. OSM is the fallback if Esri is
unreachable. Flights, military traffic, satellites, earthquakes, public
cameras, radio, and launches are available without keys.

For photorealistic 3D, add a **Cesium ion token** for eligible personal,
non-commercial use, or a **Google Maps key** for the direct, metered route and
in-app place search. Provider terms and quotas apply. Add keys through the
app's **POWER UP** panel; [Keys & Costs](#-api-keys) explains the options.

### Path 1 — One click, no terminal

1. Install or update [Pinokio](https://desktop.pinokio.co/) to **8.2 or later**.
2. Open the [India God's Eye View repository](https://github.com/sumitsuthar015/india-god-eye-view).
3. Click **Install**, then **Start**.

Available on **Windows, macOS, and Linux**. The Pinokio maintainer reports
cross-platform testing of the fixed installer. The launcher installs the
locked dependencies, finds a free local port, and opens the app.

**Tried before and installation failed?** Update Pinokio and try again.
Version 8.2 fixes the launcher installation issue;
[details from the Pinokio maintainer](https://pinokio.co/posts/01m1m4p9xxm3qw7dnnpj2wr93g).

### Path 2 — Terminal / coding agent

Use **Node.js 24.x (24.14.0 or later) or 26.x**. The setup doctor warns about
Node 25, which is end-of-life.

```bash
git clone https://github.com/sumitsuthar015/india-god-eye-view.git
cd india-god-eye-view
npm ci
npm run doctor
npm run dev
```

Open **`http://localhost:4173`**. Choose **Live Contacts**, **Space Missions**,
**Environmental**, or **Explore Manually** from the first-run panel.

<details>
<summary>Startup performance</summary>

A point-in-time M5/Chrome capture measured a median 1.86-second cold start.
This is a comparison baseline, not a guarantee for your machine or connection.
See [docs/PERFORMANCE.md](docs/PERFORMANCE.md).

</details>

**macOS shortcut:** `./scripts/dev-fresh.sh` clears the Vite cache and pulls any
configured keys straight from the Keychain. It starts keyless too.

### Then power it up — in the app, not in a file

Keys are upgrades, not prerequisites. When you want one, click the **POWER UP**
chip in the bottom-right corner: Provider Settings lists every supported key,
what it switches on, and where to get it. Paste, hit **SAVE KEYS**, and the app
restarts itself with the new capability on. Once everything is configured the
chip reads **POWERED UP** — and if a compact layout hides it, `?setup=1`
reopens the same panel.

- **Where keys land:** Pinokio → the app's ignored `pinokio/ENVIRONMENT`; a
  terminal clone → the repo-root `.env`. Either file is made owner-only
  *before* a secret is written into it. These are local plaintext files,
  excluded from Git; the app uses your keys to contact the providers.
- **Keys you already have stay yours:** values from your shell or the macOS
  Keychain show as *configured externally* and are read-only to the panel.
- **What to get first:** the free [Cesium ion](https://cesium.com/ion) token
  (eligible personal, non-commercial use; current terms and quotas apply) for
  photorealistic 3D and world terrain; a Google Maps key only for the
  billing-enabled, metered route + place search; OpenAI when you want to talk
  to the world. Full map, costs included, in [Keys & Costs](#-api-keys).

<details>
<summary>Older Pinokio versions and credential storage</summary>

Do not enter credentials in Pinokio 8.0.40's native **Configure** panel: that
release does not save this nested app file correctly, and it logs submitted
values. Use **POWER UP → Provider Settings** inside GEV instead. The Pinokio
8.2 announcement fixes installation; it does not establish that this separate
Configure issue is resolved. On macOS, the Keychain via
`./scripts/dev-fresh.sh` remains the stronger storage option.

</details>

The server binds to **localhost** on both paths, and Provider Settings answers
requests only from your machine. Browser-side keys (Google Maps, Cesium ion)
must be restricted at their providers — [SECURITY.md](SECURITY.md) shows how,
and it carries the LAN-sharing rules alongside [Keys & Costs](#-api-keys).

---
