# Cyber-Tracker HUD

Browser-based AR motion tracking HUD.
Detects and tracks moving objects in real time via smartphone camera, overlaying a cyberpunk-style UI.

**Long Range mode** — an experiment in tracking birds across the sky with just a phone camera. No ML, no cloud, just pixel-diff and math. Still early, still rough, but it works.

## Live Demo

| Mode | Link | What it's chasing |
|------|------|-------------------|
| Near Range | [Launch](https://wory-bonbon.github.io/cyber-tracker/) | People, hands, objects at 1–3m |
| Long Range | [Launch](https://wory-bonbon.github.io/cyber-tracker/long.html) | Birds in flight, aircraft, distant motion at 10m+ |

> Best on **iOS Safari** with rear camera. Also works on desktop with webcam.

## Why Cyber-Tracker?

- ✅ Single HTML file — no build tools, no npm
- ✅ Works on iOS Safari (camera freeze issue solved)
- ✅ Privacy-safe — all processing is local, no data sent

## How to Use

1. Open the demo URL on your smartphone
2. Tap **ACTIVATE CAMERA**
3. Point camera at moving objects → auto-tracking begins
4. Tap screen to manually override target position

## Near Range vs Long Range

The original near-range version was built for close targets — people walking, hands waving.
But what about a bird crossing the sky? At 48×48 detection resolution, it's invisible. That's why Long Range exists.

| | Near Range (`index.html`) | Long Range (`long.html`) |
|---|---|---|
| Camera | 640×480 | 1280×720 |
| Detection grid | 48×48 | 128×128 |
| Diff threshold | > 25 | > 8 |
| Noise filtering | — | Temporal accumulation (3-frame) |
| Lost target | Immediate unlock | Inertial coasting (15 frames) |
| Tracking | Simple lerp | Predictive (velocity vector) |
| Color scheme | Green (#00ffcc) | Blue (#00ccff) |

### What Long Range adds

- **Temporal accumulation** — stacks 3 frames of diff data to separate real motion from sensor noise
- **Inertial coasting** — keeps tracking for 15 frames after target loss (bird behind a cloud, etc.)
- **Predictive tracking** — uses velocity vector to aim ahead of fast-moving targets
- **Weighted centroid** — stronger diff values pull the reticle harder, improving lock on small targets

### What's still rough

- Wind-blown trees can trigger false locks
- Very small / very distant birds may still be missed
- Tuning is ongoing — threshold and accumulation values are not final

## Requirements

- iOS Safari / Android Chrome
- Smartphone with camera recommended
- No install, no app required

## Tech Stack

- WebRTC (camera capture)
- Canvas API pixel-diff (motion detection)
- Three.js r170 + UnrealBloomPass (3D HUD rendering)
- Single HTML file — zero dependencies

## Author

[wory-bonbon](https://github.com/wory-bonbon)
Built with Gemini 3.1 Pro & Claude Opus 4.6

## License

MIT License — feel free to use, modify, and distribute.
