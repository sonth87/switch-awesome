# Bear Cave Solstice Switch
## Material Studies No. 062 — WebGL2 + Web Audio

A single self-contained page: a big pill switch holding a 176×50 pixel-art forest clearing with a cave house in the hill. Drag a capsule of honey-to-ice jelly glass from golden autumn to a snowy winter dusk. Winter spreads behind the glass while the three bear brothers pack up and go home. Open `bear-cave-solstice-switch.html` in a WebGL2 browser. No libraries, no assets.

Fan study after *We Bare Bears* (characters © Cartoon Network). The pixel sprites and the score are drawn and synthesised from scratch.

## Controls

- **Drag** the knob, or drag anywhere on the track. **Tap** to send it to the other end on its spring.
- Arrow keys, Page Up / Down, Home / End; Space or Enter flips it. `role="slider"` with aria values.
- **Sound on/off** button; audio starts on the first touch.
- `#t=0.8` in the URL starts the knob at a position (0–1).

## Story, by position

| Position | Season | Weather | Audio | What happens |
| --- | --- | --- | --- | --- |
| 0.00–0.20 | Golden Autumn | 24°C Sunny | Birdsong → Ukulele | Grizzly lounges in a striped deck chair in shades; Ice Bear flips skewers on a smoking kettle grill; Panda snaps photos with little flashes; songbirds glide over. |
| 0.20–0.53 | Crisp Breeze → First Frost | ~15°C Breezy → 1°C Frost | Ukulele → Breeze | Leaves come down in gusts. Grizzly lowers his shades and shivers, the grill lid goes on, Panda sneezes and rubs his paws, the birds fly off. Snow begins at 0.35. |
| 0.53–0.79 | Snowfall | 1°C → −2°C Snow | Celesta | Single file to the cave: Grizzly (chair left folded against the maple), Ice Bear carrying the grill, Panda last. Warm light spills from the open door. |
| 0.79–1.00 | Hibernation | −4°C Snow | Fireside | Door creaks shut with a latch thud; a CLOSED sign drops and swings; the window glows gold and chimes; smoke curls from the chimney; the music muffles as if playing inside. |

Passing the glass over Panda fires his camera: a flash and a shutter click.

## How it is built

- **Pixel buffer:** CPU albedo with a per-pixel kind (sky, particles, distant crowns, near canopy, ground, bears). Sprites get an automatic outline, a light top row and a dark bottom row. The background behind the near canopies is saved each frame, and a separate twig mask holds bare branches. That lets the trees go bare only on the winter side.
- **Winter, per pixel:** each solid pixel knows how far it sits below open sky. In winter the top 1–3 rows of everything turn to snow (boughs, pine tiers, the roof, chair, chimney, sign, ground). Bears never collect snow. The canopy shows snow clumps and twigs over the saved background. Flakes are a per-frame mask that thickens from 0.35. The sky fades from periwinkle to dusk blue, and the window and doorway throw dithered warm pools onto the snow.
- **Light:** autumn on the right gets a warm grade and slanting sunbeams. The winter side starts just behind the knob at a 4×4 Bayer-dithered edge, with a frosted-gold band behind the glass. The glass always samples the autumn render.
- **Shader:** one WebGL2 fragment shader. The bezel goes from birch-bark cream with dark lenticel dashes to frosted pine-slate with ice speckle. The capsule knob has 1.28× magnification, an RGB split at the rim, a refraction band, a Fresnel tint from honey to ice, two highlights, light at its foot and a shadow on the floor. It follows a spring, stretches with speed and wobbles.
- **Audio:** all synthesised live. 96 BPM with swing, four bars of Cmaj7 · Am7 · Fmaj7 · G6. Layers by position:
  - leaf rustle, breeze and FM bird chirps;
  - Karplus–Strong ukulele fingerpicking and grill sizzle;
  - brushes, a mellow kick and upright bass;
  - celesta arpeggios and a wandering whistle of wind;
  - fireplace crackle as a low-pass closes over the music.

  Switch sounds: wooden knock and blop on grab, a snow-crunch plop on release, a rustle on drag, the camera shutter, the door creak, latch thud and sign clacks, and the window chime.

## Browser support

Needs WebGL2 and Web Audio. Developed against Chrome.
