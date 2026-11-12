# Around the World Switch
## Material Studies No. 062 — WebGL2 + Web Audio

A single self-contained page: a big pill slider holding a 352×100 pixel-art panorama of the Earth. Drag a capsule of clear jelly glass and the flat Hanoi skyline bends into a globe that rolls west under it, through Japan and France to a starry night over the USA. The knob has no snap: it stays wherever you let go. Open `around-the-world-switch.html` in a WebGL2 browser. No libraries, no assets.

The scene is twice the usual 176×50 density (352×100) so that sixteen landmarks keep their detail. The bezel and knob geometry are unchanged; one bezel unit is two scene pixels.

## Controls

- **Drag** the knob, or drag anywhere on the track, and release at any position.
- **Tap** the track to glide to that longitude.
- **Arrow keys** step one sixteenth (about one landmark). **Page Up / Down** hop to the next or previous country. **Home / End** go to the ends. `role="slider"` with aria values.
- **Sound on/off** button; audio starts on the first touch.
- `#t=0.6` in the URL starts the knob at a position (0–1).

## The journey, by position

| Position | Destination | Local time | Audio | Landmarks |
| --- | --- | --- | --- | --- |
| 0.00–0.24 | Vietnam · Hanoi / Huế / Da Nang / HCMC | 08:00 AM → | Đàn Tranh | Khuê Văn Các, Hồ Chí Minh Mausoleum and its flagpole, Hanoi Flag Tower (set back), Huế's Ngọ Môn gate, Cầu Vàng on the Bà Nà hills, held by two stone hands above the clouds (rises behind the horizon), Dragon Bridge (breathes fire, then water), Saigon Notre-Dame Cathedral, Landmark 81 (set back), Bitexco Tower, a string of lanterns |
| 0.25–0.49 | Japan · Miyajima / Himeji / Osaka / Kyoto / Fuji / Tokyo | → 01:30 PM → | Koto & Flute | Torii in the sea, Himeji Castle (set back), Osaka Castle, Fushimi Inari's gate and torii tunnel, Kinkaku-ji over its mirror pond, Mount Fuji, Sensō-ji's Kaminarimon with its pagoda behind, Tokyo Tower, Skytree (set back), five big cherry trees, petals falling and settling on the grass |
| 0.50–0.74 | France · Paris | → 06:45 PM → | Paris Musette | Arc de Triomphe, Eiffel Tower (sparkles and a sweeping beacon at dusk), Notre-Dame, the Louvre and its pyramid |
| 0.75–1.00 | USA · NYC / D.C. / Rushmore / SF | → 11:30 PM | Midnight Jazz | Statue of Liberty, Empire State Building, Washington National Cathedral, Mount Rushmore rising behind the plains, Golden Gate Bridge |

- **Flat to globe:** at 0.00 the ground is a level strip across the lower third. From 0.01 to 0.12 it bends into a convex arc with an atmospheric rim, and flattens again when the knob returns to 0.00.
- **Sky:** the sun starts high, sinks to the right and sets behind the curve around 0.6. A crescent moon and twinkling stars rise from 0.64. Clouds drift throughout.
- **Lights:** from 0.5 windows, lamps, bridge cables and floodlights switch on one by one.

## How it is built

- **Flat strip, then a polar map.** Everything on the ground is drawn each frame into a flat 384×112 strip: far layer, ground, landmarks, foreground props. Each screen pixel is then mapped back to the strip through an inverse polar transform whose radius goes from infinite (flat) to 500 px (globe), with nearest sampling. The map is cached while the curvature is constant.
- **Parallax, four depths:** far hills, rooftops, skylines and mountains at 0.55×; a back row of landmarks (Hanoi Flag Tower, Landmark 81, Himeji, the Sensō-ji pagoda, Skytree) at 0.82–0.86× with a light haze; the main landmarks at 1×; trees, lamps, lanterns and a taxi at 1.35×. Cầu Vàng, Mount Fuji, Sacré-Cœur and Mount Rushmore rise and sink behind the horizon as their country arrives and leaves.
- **World layout:** the strip is about 2,050 px long. Each country owns a quarter of the track, so the globe turns at a different speed in each one.
- **Petals:** over Japan, 110 petals fall from the cherry trees and ride the globe; a few nearer petals drift across the whole frame in screen space; fallen petals speckle the grass.
- **Sprites:** drawn with rectangles, trapezoids, ellipses and lines, then stamped with an automatic 1-px outline, a light top row and a dark bottom row. Lattices (Eiffel, Tokyo Tower) skip the outline so the sky shows through.
- **Two grades from one albedo:** the track shows the current time of day (seven keyframes from morning to midnight). The glass always shows a golden-hour grade, so at night the loupe reveals the architecture in warm light.
- **Water:** mirrored reflections of whatever stands above, moving ripples, sun glitter by day and moon glitter by night.
- **Sky:** screen space. Gradient shells follow the curve of the Earth; sun and moon have dithered halos.
- **Shader:** one WebGL2 fragment shader. The bezel goes from ivory ceramic to brushed titanium-indigo. The capsule has 1.28× magnification, an RGB split at the rim, a refraction band, a Fresnel tint, two highlights, light at its foot, a shadow below, and latitude/longitude ticks engraved along the rim. It follows a spring, stretches with speed and wobbles.
- **Page colours:** background, text and rules follow the same keyframes, from pale sky blue through gold and dusk violet to midnight navy.
- **Audio:** all synthesised live. 108 BPM, four bars of Cmaj7 · Em7 · Fmaj7 · Gsus4 on one lookahead clock. Four buses crossfade around 0.25, 0.5 and 0.75:
  - Vietnam: bright Karplus–Strong đàn tranh in C pentatonic with pressed bends and glissando runs, breeze and river blips;
  - Japan: koto in E in-sen (a bar of Yo over the Gsus4) with grace notes, a breathy shakuhachi with blooming vibrato, wind chimes;
  - France: valse musette, two bars of three per chord, on three detuned reeds, with brushes;
  - USA: FM Rhodes chords with tremolo, a walking muted upright bass, brushes, soft kick, vinyl hiss and crackle, light swing.

  Switch sounds: glass tink and a double compass click on grab, a cushioned thud on release, a wind whoosh that follows the knob's speed, a four-note chime when a new country reaches the centre and a single soft bell for each landmark.

## Browser support

Needs WebGL2 and Web Audio. Developed against Chrome.
