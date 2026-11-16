# Fog Mirror - standalone (GitHub Pages ready)

Static site, no build step, no server code. All processing is on-device:
the camera frame never leaves the page, and hand tracking runs locally
with MediaPipe HandLandmarker (wasm + model loaded from the official
jsDelivr/Google CDNs; the camera frame never leaves the page).

## Run locally
    python3 -m http.server 8000
    open http://localhost:8000

## Deploy to GitHub Pages
Push this folder to a repo, then Settings -> Pages -> deploy from branch.
Camera requires HTTPS (GitHub Pages provides it) and is NOT available
inside sandboxed iframes such as the Instinct Files viewer.

## Modes
- (default)   live front camera, mirrored; wipe fog with your fingertip,
              or drag with touch/mouse. Fog slowly mists back.

The demo/selftest media (a reference reel and extracted frames) is
third-party content and intentionally not included in this public repo;
those query modes show a note instead. Hand tracking was verified during
development with MediaPipe HandLandmarker on real footage: hands found in
8/14 sampled frames (score 0.95-0.998), fog cleared along the fingertip
path.

## Controls
- Turn on the mirror: starts camera + tracker.
- Fog it again: instantly re-mist.
- brush: wipe size.

Built 16 Nov 2026. Not yet deployed - awaiting the owner's approval for
public hosting.
