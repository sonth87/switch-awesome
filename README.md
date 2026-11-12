# Material Studies

Open `index.html` — it is the entry point and links to every study.

```
index.html                       gallery (entry point, with "Copy prompt" buttons)
assets/                          screenshots used by the gallery
daybreak-switch/
  daybreak-switch.html           No. 062, the study itself (single file, no libraries)
  README.md  BRIEF.md            its notes and the original prompt
neon-coast-switch/
  neon-coast-switch.html         No. 066, the study itself (single file, no libraries)
  README.md  BRIEF.md            its notes and the original prompt
pharaohs-dusk-switch/
  pharaohs-dusk-switch.html      No. 062, the study itself (single file, no libraries)
  README.md  BRIEF.md            its notes and the original prompt
east-blue-duel-switch/
  east-blue-duel-switch.html     No. 062, the study itself (single file, no libraries)
  README.md  BRIEF.md            its notes and the original prompt
bear-cave-solstice-switch/
  bear-cave-solstice-switch.html No. 062, the study itself (single file, no libraries)
  README.md  BRIEF.md            its notes and the original prompt
around-the-world-switch/
  around-the-world-switch.html   No. 062, the study itself (single file, no libraries)
  README.md  BRIEF.md            its notes and the original prompt
```

To add a study: give it its own folder, put a screenshot in `assets/`, and add a card in `index.html`.

---

# Daybreak Switch
## Material Studies No. 062 — WebGL2 + Web Audio

A single self-contained page: a night-to-morning toggle switch in original style. Drag a jelly-glass knob across a pixel-art room that wakes from dusk through dawn to daytime party, with synthesised live music and sound design.

### Features

**The Switch**
- A pill-shaped switch in a moulded bezel (graphite by night, white by day)
- Inside: a 176×50 pixel-art room rendered every frame on the CPU, displayed at nearest sampling
- Knob: a vertical capsule of clear jelly glass drawn in WebGL2 that magnifies, bends and refracts the scene beneath it, with Fresnel highlights and focus lighting

**The Room** (cosy, original palette)
- Butter-yellow diamond wallpaper, teal wainscot, plank floor, striped rug
- Window with curtains over a town; sky transitions from night (navy, stars, moon, lit town windows) through dawn (violet to peach) to day (blue, sun, drifting clouds)
- Shelves of jelly jars and books, potted plant, brass floor lamp
- Red boombox on wooden cabinet, framed shark picture, round wall clock, blue door
- String of coloured bulbs sagging across the ceiling
- Purple pet bed under the window

**Light and Animation**
- The knob drags the dawn across the room: left of it is day, right of it still night
- Window sky and light shafts follow the knob's position
- Ceiling bulbs light as the knob passes them
- An orange tabby cat: asleep (with rising z's) → waking → sitting → walking → dancing in sunglasses
- A white puppy waits outside late in the morning, knocks, and comes in when the knob reaches full day
- Disco ball descends and confetti sparkles during the party phase
- Crescent echoes (coral to pink) trail behind the moving knob

**Sound** (all synthesised live with Web Audio, original composition)
- 100 BPM, four-bar loop in F major (Fmaj7 · Am7 · Dm7 · B♭maj7), lookahead-scheduled with swing
- Layers fade in by knob position: crickets & wind → music box → lo-fi beat → pads & lead → full party
- Switch sounds: glass tink & jelly blop on grab, plop on release, drag rub, bulb plucks, lamp click, cat's "mrrp", party riser & crash
- Puppy knock: three heavy hits with knuckle clicks, deep thump and overtones; music ducks under each hit
- Audio starts on first touch; Sound on/off button to toggle

**Readouts**
- Clock (02:00–10:00)
- Light (Night / First light / Sunrise / Morning / Party)
- Music (Crickets / Music box / Beat / Band / Party)

### Controls

- **Drag** the knob or drag anywhere on the track
- **Tap** to toggle to the other end (travels there on its spring)
- **Arrow keys** (← → ↑ ↓), **Home** / **End**, **Space** / **Enter** to move the knob
- **Role:** `role="slider"` with ARIA values for accessibility

### Layout

- Editorial: small "Material Studies / No. 062" kicker, italic serif title, one-line caption
- Switch centred and large
- Readouts and hint line below
- Sound on/off button
- Works at phone width (no horizontal scroll)

### Colours

Background and text follow the switch from dark dusk-indigo at night (23, 21, 43) to pale lavender-grey by day (228, 226, 236).

### Technical

- **One file:** `daybreak-switch.html` (~49 KB)
- **No libraries:** raw WebGL2, Web Audio API, plain JavaScript
- **Rendering:** 176×50 CPU room rendered every frame, upscaled with integer scaling
- **Shader:** Full-canvas fragment shader for the knob (magnification, refraction, Fresnel, lighting, shadow)
- **Physics:** Spring-damped knob lag, stretch and wobble on drag speed
- **Audio:** Lookahead-scheduled Web Audio synthesis (oscillators, filters, convolver, noise, saturation, dynamic compression)

### Browser Support

Requires WebGL2 and Web Audio API. Tested in Chrome.

### URL Parameters

Add `#t=<value>` (0–1) to start the knob at a specific position:
- `#t=0` — night, 02:00
- `#t=0.5` — middle of the transition
- `#t=1` — full day, party

### To Use

1. Open `daybreak-switch.html` in a WebGL2-capable browser
2. Drag the knob or tap to flip it
3. Use arrow keys or Home/End to navigate
4. Click "Sound on" to enable audio (starts on first interaction)
5. Watch the room light up and listen to the music evolve

---

**Original design brief:** Material Studies material, a night-to-morning toggle. All the specific details about the room, the cat, the puppy, the light transitions, the sound layers, and the jelly-glass knob were from the brief. Built as a single self-contained page with no external libraries or assets.
