# Fog Mirror - standalone (GitHub Pages ready)

Static site, no build step, no server code. All processing is on-device:
the camera frame never leaves the page, hand tracking runs locally with
MediaPipe HandLandmarker (wasm + model loaded from the official
jsDelivr/Google CDNs), and the mic is only used for live loudness
analysis - nothing is recorded or sent anywhere.

## Run locally
    python3 -m http.server 8000
    open http://localhost:8000

## Deploy to GitHub Pages
Push this folder to a repo, then Settings -> Pages -> deploy from branch.
Camera requires HTTPS (GitHub Pages provides it) and is NOT available
inside sandboxed iframes such as the Instinct Files viewer.

## Modes
- (default)   live front camera, mirrored; wipe fog with your fingertip,
              or drag with touch/mouse. Wiped areas stay clear until you
              blow into the mic - a blow fogs the glass again. The mic is
              only analysed live in the page (loudness over time); audio
              is never recorded, stored or uploaded.

The demo/selftest media (a reference reel and extracted frames) is
third-party content and intentionally not included in this public repo;
those query modes show a note instead. Hand tracking was verified during
development with MediaPipe HandLandmarker on real footage: hands found in
8/14 sampled frames (score 0.95-0.998), fog cleared along the fingertip
path.

## Controls
- Turn on the mirror: starts camera + tracker, then asks for the mic
  (blow detection). If mic is denied, the button below still re-fogs.
- Blow into the mic: fogs the glass again (sustained loud sound).
- Fog it again: manual re-mist button.
- brush: wipe size.

Built 16 Nov 2026. Deployed with the owner's approval at
https://urjaswitpatel-ctrl.github.io/fog-mirror/
