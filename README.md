# HandGesture-Web

Tiny browser-based hand-tracking sandbox web project driven by hand movements.

Uses MediaPipe Hands (loaded from a CDN, no install required) and draws the
21 hand landmarks plus a small debug HUD: FPS, hand count, recognized
gesture (`open palm`, `fist`, `point`, `peace`, `pinch`), and live pinch
distance.

## Debug shortcuts

- `D` — toggle landmark index numbers on each finger joint
- `S` — log the latest hand state to the browser console

## Spray Wall app — `paint.html`

Open `http://localhost:8000/paint.html` for the interactive spray-paint
wall. Pinch (thumb + index touch) to spray. Move your hand to draw.

Keys:

- `1`–`8` color · `[` `]` brush size · `-` `=` opacity
- `Space` clear · `S` save PNG
- `P` projector mode (hides webcam, black bg only — the layer to send to the
  projector)
- `M` toggle mirror (turn off for real projector setups so right hand maps to
  the right side of the wall)
- `T` cycle trigger: pinch → point → always
- `K` calibrate: click the 4 corners of the projected area on screen in the
  order TL → TR → BR → BL. The painted output is then warped to align with
  the projection. `Esc` cancels.

### Projector setup

1. Aim camera at the same wall the projector lights up. Camera should see
   the entire projected rectangle plus a bit of margin.
2. In Chrome, drag the window onto the projector display and press `F11`
   for fullscreen.
3. Press `M` to turn off mirroring.
4. Press `K` and click the 4 corners of the projection in the camera
   preview, top-left first, going clockwise.
5. Press `P` to hide the HUD and webcam. Now only paint shows on the wall.

## Where to extend

- `classifyGesture(lm)` in `index.html` is where to add new gestures.
- The `draw(results)` function is where to hook visuals/interactions —
  this is the spot to drive a canvas/WebGL/Three.js scene from the hand
  position the way you'd patch a TOP/CHOP in TouchDesigner.
