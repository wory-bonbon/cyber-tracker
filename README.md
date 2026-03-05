# Cyber-Tracker HUD

Browser-based AR motion tracking HUD.  
Detects and tracks moving objects in real time via smartphone camera, overlaying a cyberpunk-style UI.

## Live Demo
🔗 [https://wory-bonbon.github.io/cyber-tracker/](https://wory-bonbon.github.io/cyber-tracker/)

## Why Cyber-Tracker?
- ✅ Single HTML file — no build tools, no npm
- ✅ Works on iOS Safari (camera freeze issue solved)
- ✅ Privacy-safe — all processing is local, no data sent

## How to Use
1. Open the demo URL on your smartphone
2. Tap **ACTIVATE CAMERA**
3. Point camera at moving objects → auto-tracking begins
4. Tap screen to manually override target position

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
