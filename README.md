# NeuroScreen Pro

Mobile motor screening and kinematics analysis tool built with client-side computer vision.

## Overview
NeuroScreen Pro performs on-device assessment of motor patterns using MediaPipe HandLandmarker. It evaluates finger tapping cadence, amplitude decrement, postural tremor frequencies, and bimanual coordination directly inside modern web browsers.

## Key Capabilities
- **Tapping Cadence & Decay**: Quantitative measurement of tapping frequency (Hz) and fatigue over 15 seconds.
- **Bilateral Comparison**: Sequential assessment of right and left hands to compute an asymmetry index.
- **Postural Tremor Analysis**: Discrete Fourier Transform analysis of normalized 2D displacement in static hold.
- **Dual-Task Test**: Bimanual prompt response and reaction time measurements.
- **Privacy Preserving**: All vision processing executes locally inside the browser. No video is recorded or sent to servers.
- **PWA Ready**: Works offline via Service Worker caching.

## How to Deploy on GitHub Pages
1. Go to your repository **Settings** tab.
2. Under the **Pages** menu on the left, set source branch to `main` (folder `/root`).
3. Click **Save** to enable HTTPS hosting.

## Files
- `index.html` - Core application interface and processing logic.
- `manifest.json` - PWA configuration.
- `sw.js` - Service worker for offline caching.
- `README.md` - Documentation.
