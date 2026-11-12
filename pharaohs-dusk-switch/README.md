# Pharaoh's Dusk Switch
## Material Studies No. 062 — WebGL2 + Web Audio

A single self-contained page: a big pill switch holding a 176×50 pixel-art Nile at Giza. Drag a capsule of jelly crystal from a scorching 14:00 afternoon to midnight; night sweeps in behind the glass, the lanterns catch one by one, the Sphinx wakes up and puts on shades, and the Great Pyramid turns into a disco beacon. Open `pharaohs-dusk-switch.html` in a WebGL2 browser. No libraries, no assets.

## Controls

- **Drag** the knob, or drag anywhere on the track. **Tap** to send it to the other end on its spring.
- Arrow keys, Page Up / Down, Home / End; Space or Enter flips it. `role="slider"` with aria values.
- **Sound on/off** button; audio starts on the first touch.
- `#t=0.8` in the URL starts the knob at a position (0–1).

## Story, by position

| Clock | Light | Music | What happens |
| --- | --- | --- | --- |
| 14:00 | High Noon | Desert Wind | Glaring sun, heat shimmer, sunbeams. The Sphinx squints, eyes shut, heat lines rising off its back. Hawks and cicadas. |
| ~15:30 | Golden Hour | Oud Plucks | One stone eye cracks open, a lappet of the nemes twitches. Lanterns start to catch behind the glass. |
| ~17:30 | Sunset | Darbuka | The Sphinx lifts a paw and nods to the dum-tek. The sun sinks behind the far pyramid. |
| ~19:40 | Starlight | Mizmar Band | Stone-grinding rumble and a brass chord: the Sphinx sits up on its haunches in shutter shades, bobbing. |
| ~22:30 | | | A camel walks in on the far bank and a jackal hound stands on the felucca; it barks. |
| ~23:00 → 00:00 | Pyramid Disco | Nile Rave | Riser and crash. The capstone sparkles like a disco ball and throws cyan, magenta and gold lasers across the sky and Nile; disco spots, neon glints, sand-glitter, scarabs zipping on each bar. The Sphinx raves with gold and cyan ghost trails. |

The glass always shows the midnight party, whatever the time outside it. Turquoise-to-gold crescent echoes trail a fast knob. Hieroglyphs and notes float off the capstone once the beat is in.

## How it is built

- **Pixel buffer:** CPU albedo with a per-pixel kind (sky, emissive, water, lantern flame, sand, gold capstone). Sprites are stamped with an automatic 1-px outline, a light top row and a dark bottom row. Two sky buffers are drawn every frame: the current afternoon (sun, glare, rays) and midnight (stars, the Sah / Orion figure, crescent moon).
- **Light:** each pixel is lit twice, once as full night party (for the glass) and once for the page: night left of a Bayer-dithered edge near the knob, with a crimson-violet band just behind it, and day to the right (noon → golden → sunset tint, heat shimmer row offsets, sunbeams, an obelisk shadow). Night adds lapis ambient, moonlit skyline edges, lantern pools, laser beams from the capstone, disco spots and neon water glints.
- **Shader:** one WebGL2 fragment shader draws the moulded bezel (alabaster sandstone by day, obsidian basalt at night, with a faint grain), the page shadow and the capsule knob: 1.28× magnification, RGB split at the rim, refraction band, Fresnel tint (amber by day, lapis by night), two highlights, light focused at its foot and a shadow on the desert floor. The knob follows a spring, stretches with speed and wobbles.
- **Audio:** all synthesised live. 118 BPM, four bars in D Hijaz (D · E♭ · F♯m · Gm/D) on one lookahead clock. Layers by knob position: pink-noise wind, cicadas and hawk cries → Karplus–Strong oud/qanun arpeggios with a canyon delay → darbuka maqsum (dum-tek) and a gliding fretless bass → detuned pads and a formant-filtered mizmar with scoops and vibrato → the Nile Rave (four-on-the-floor kick, claps, hats, sub bass, sidechain pump). The music sits behind a low-pass that opens with the night, about 5 dB under the switch sounds: crystal clink and jelly blop, stone thud-plop, a sand rub following the drag, a Hijaz pluck per lantern, the Sphinx rumble and brass chord, riser and crash, tape brake, the jackal's bark.

## Browser support

Needs WebGL2 and Web Audio. Developed against Chrome.
