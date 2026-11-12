# Pharaoh's Dusk Switch — Design Brief

Make "Pharaoh's Dusk Switch", No. 062 in a series of web material studies: a scorching-day to neon-desert-party toggle in its own original style, as a single self-contained page (no libraries; raw WebGL2 + Web Audio + a 2D pixel buffer). Editorial layout: a small "Material Studies / No. 062 · WebGL + Web Audio" kicker, an italic serif title "Pharaoh's Dusk Switch.", a one-line caption; the switch centred and large; below it readouts (Clock, Light, Music), a hint line and a "Sound on/off" button. The whole page's colours (background, text, lines) follow the switch from a warm sandstone-cream by day to a deep midnight-lapis indigo at night. Works at phone width.

## THE SWITCH

A pill-shaped switch in a moulded bezel: warm alabaster sandstone by day, dark obsidian basalt at night. A soft drop shadow falls on the page and fades to nothing before the canvas edge, with a slight inner shadow along the top of the track.

Inside, a 176×50 pixel-art Egyptian landscape, redrawn every frame on the CPU and shown with nearest sampling, never smoothed. Whole device pixels per scene pixel where there is room.

The knob is a vertical capsule of clear jelly glass (tinted faintly like amber/lapis crystal), a little taller than the track, drawn in one full-canvas WebGL2 fragment shader:

- it magnifies (~1.28×) and bends the pixels under it;
- it splits R/G/B at its rim, with a darker refraction band, a bright edge and a Fresnel tint;
- two highlights: a long soft streak at the upper left and a small dot at the lower right;
- light focused toward its foot, and a soft shadow on the desert floor.

The knob lags the finger on a spring, stretches horizontally with speed (squashing vertically to keep its volume), and wobbles on a damped spring fed by its acceleration.

Inside the knob the scene is always shown in full neon-night party mode: the glass carries the midnight rave into the day.

Controls: drag the knob or drag anywhere on the track; tap to toggle to the other end (it travels there on its spring); arrow keys, Home/End, Space/Enter; role="slider" with aria values.

## THE SCENE (original, sun-baked & jewel-toned Egyptian palette)

Built from filled shapes stamped with an automatic 1-px outline and a light top / dark bottom, so every object reads as a crisp pixel sprite:

- sky backdrop spanning the dunes, distant palm silhouettes, and the flowing Nile river across the foreground;
- three terraced limestone pyramids on the left/centre bank with weathered stone block textures and glowing golden capstones (pyramidions);
- the Great Sphinx resting prominently on the right bank facing the Nile, with detailed nemes headdress, paws, and stone masonry;
- lush papyrus reeds and date palms swaying along the riverbank, a small felucca sailboat on the water, and sandstone obelisks etched with tiny pixel hieroglyphs;
- a string of tiny ancient torches/lanterns along the river promenade.

## LIGHT AND THE NIGHTFALL

- The knob drags the dusk across Egypt: as you drag left-to-right, night sweeps across the desert (left of the knob is midnight party, right of it still sunny day). The edge dissolves in a 4×4 Bayer dither, with a rich crimson-violet sunset band just behind the knob.
- The desert sky runs from blazing noon (azure blue, glaring sun, heat shimmer) through sunset (amber, burnt orange, magenta, sun sinking behind the pyramids) to midnight (deep lapis navy, twinkling constellations, a glowing crescent moon).
- Harsh golden sunbeams and pyramid shadows by day; cool silver moonlight and neon laser beams at night.
- At night, the Great Pyramid transforms into a giant disco beacon: its golden capstone spins/pulses like a disco ball, firing sweeping cyan, magenta, and gold laser beams and disco spots down onto the Nile.
- The Nile river shifts from sunlit turquoise with gentle ripples by day to dark indigo water covered in shimmering, sparkling neon reflections and dancing disco glints at night.
- The promenade lanterns ignite one by one as the knob passes them, casting warm dithered glows.
- The sundial/cosmic clock runs from 14:00 (2 PM) to 00:00 (Midnight).

## THE STORY, BY POSITION

The Great Sphinx:

- by day (far left): completely still, stoic, eyes closed or squinting in the sun, faint heat-wave lines rising off its stone back;
- late afternoon: one stone eye cracks open, ears/headdress twitching slightly;
- sunset: lifts one giant stone paw and nods its head to the emerging rhythm;
- dusk: stands up on its haunches, wearing pixelated shutter-shades/sunglasses, bobbing its head and paws;
- at the midnight party (far right): full-on raving—bouncing on its stone paws, throwing paws in the air to the beat, with neon cyan & gold ghost trails behind its movements.

The palm trees and papyrus reeds sway to the tempo, and tiny pixel hieroglyphs/music notes float up from the pyramid's glowing peak.

The pyramid capstone blasts rotating disco beams across the sky and onto the sparkling Nile; golden sand-glitter/confetti sparkles fall through the night air.

Glowing turquoise-and-gold crescent echoes trail behind the moving knob.

Near the end (from about 22:30 on the clock), a small jackal/Anubis-hound silhouette and a camel appear on the opposite riverbank/felucca boat bobbing to the beat, and stone scarabs with glowing wings zip across the foreground in sync with the drops.

## SOUND — all synthesised live with Web Audio, original Pharaonic-electronic music

118 BPM, a four-bar loop in D Hijaz / Phrygian Dominant (D · E♭ · F♯m · Gm / D), on one lookahead-scheduled clock with a hypnotic Middle Eastern groove.

Layers fade in by the knob's position:

0. Day: dry desert wind (band-passed pink noise) and distant cicadas/hawks.
1. An oud / qanun pluck arpeggiating the Hijaz scale (Karplus-Strong / filtered triangle plucks with short desert canyon delay).
2. Hand percussion (darbuka / doumbek "dum-tek" synthesised with pitched membrane thumps and crisp rim snaps) and a warm fretless bass.
3. Shimmering synth pads and a reedy mizmar / flute lead with expressive pitch-bend vibrato.
4. The Nile Disco Party: heavy four-on-the-floor club kick, crisp claps, shimmering disco hi-hats, sub bass, and sidechain pumping across the oud and pads.

The music sits behind a low-pass filter that opens wide as night falls, and ~5 dB under the switch's own tactile sounds.

Switch sounds:

- a crystal/sandstone clink plus a jelly blop when grabbed, a soft stone thud-plop when released;
- a fine shifting-sand noise rub following the drag speed;
- a Hijaz-scale harp/oud pluck for every lantern lit along the Nile (a cascading glissando when you sweep across), lower and softer when extinguished;
- a deep stone-grinding rumble + triumphant brass/synth chord when the Sphinx wakes up and puts on its sunglasses;
- a sweeping wind-riser and cymbal crash into the pyramid disco drop, and a vinyl/tape brake when dragging back into daytime;
- a playful bark/yip from the river jackal when it joins the party at the end.

Audio starts on the first touch; a Sound on/off button.

Readouts: Clock (14:00–00:00), Light (High Noon / Golden Hour / Sunset / Starlight / Pyramid Disco), Music (Desert Wind / Oud Plucks / Darbuka / Mizmar Band / Nile Rave).
