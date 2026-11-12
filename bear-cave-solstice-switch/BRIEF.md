# Bear Cave Solstice Switch — Design Brief

Make "Bear Cave Solstice Switch", No. 062 in a series of web material studies: an autumn-to-winter woodland toggle featuring three bear brothers in its own original style, as a single self-contained page (no libraries; raw WebGL2 + Web Audio + a 2D pixel buffer). Editorial layout: a small "Material Studies / No. 062 · WebGL + Web Audio" kicker, an italic serif title "Bear Cave Solstice Switch.", a one-line caption; the switch centred and large; below it readouts (Season, Weather, Audio), a hint line and a "Sound on/off" button. The whole page's colours (background, text, lines) follow the switch from warm sunlit autumn ochre and amber by the left end to crisp twilight snow-slate and frost blue at the right end. Works at phone width.

## THE SWITCH

A pill-shaped switch in a moulded bezel: warm birch-bark cream in autumn, frosted pine-slate in winter. A soft drop shadow falls on the page and fades to nothing before the canvas edge, with a slight inner shadow along the top of the track.

Inside, a 176×50 pixel-art forest clearing, redrawn every frame on the CPU and shown with nearest sampling, never smoothed. Whole device pixels per scene pixel where there is room.

The knob is a vertical capsule of clear jelly glass (tinted like warm amber honey on the left, cool ice crystal on the right), a little taller than the track, drawn in one full-canvas WebGL2 fragment shader:

- it magnifies (~1.28×) and bends the pixels under it;
- it splits R/G/B at its rim, with a darker refraction band, a bright edge and a Fresnel tint;
- two highlights: a long soft streak at the upper left and a small dot at the lower right;
- light focused toward its foot, and a soft shadow on the forest floor.

The knob lags the finger on a spring, stretches horizontally with speed (squashing vertically to keep its volume), and wobbles on a damped spring fed by its acceleration.

Inside the knob the scene is always rendered in crisp golden autumn sunshine: the glass carries the warmth of fall into the winter chill.

Controls: drag the knob or drag anywhere on the track; tap to toggle to the other end (it travels there on its spring); arrow keys, Home/End, Space/Enter; role="slider" with aria values.

## THE SCENE (We Bare Bears-inspired woodland clearing, cosy pixel palette)

Built from filled shapes stamped with an automatic 1-px outline and a light top / dark bottom, so every object reads as a crisp pixel sprite:

- a grassy-and-mossy forest clearing framed by tall maple, oak, and pine trees with rich crimson, burnt-orange, and golden foliage;
- The Cave House built into a grassy hillside on the right—designed just like in We Bare Bears, complete with a rounded wooden front door, a small curtained glass window, a stone chimney, and a tiny wooden post/hook outside;
- Grizzly (Brown Bear) lounging back in a striped folding deck chair on the left, wearing dark sunglasses and basking in the sun rays;
- Ice Bear (White Bear) standing beside a smoking charcoal kettle grill near the centre, flipping sizzling meat skewers with a spatula;
- Panda (Giant Panda) standing outside the cave holding a smartphone/camera up, snapping photos of his brothers with occasional tiny white camera flashes;
- small songbirds occasionally gliding across the upper sky between the treetops.

## LIGHT AND THE SEASONAL SHIFT (0.0 Autumn → 1.0 Winter)

- The knob drags winter across the forest: left of the knob is snow-covered winter, right of it still golden autumn. The boundary dissolves in a 4×4 Bayer dither, with a crisp frosted-gold transition band right behind the knob.
- Sky & Lighting: transitions from warm afternoon sunbeams slanting through crimson trees (0.0) to overcast pale periwinkle and deep dusk winter blue (1.0).
- Foliage & Snow Accumulation: as the knob advances past the trees, autumn leaves detach and flutter down to the ground, branches become bare, and thick layers of white-and-ice-blue snow progressively blanket the tree boughs, the cave roof, the abandoned folding chair, the grill, and the forest floor.
- Snowfall: gentle pixel snowflakes begin drifting down around 0.35, thickening into a peaceful, swirling snowfall by 0.75–1.00.
- Cave Window Glow: once winter takes hold and the bears retreat indoors, the cave's little window lights up with a warm, cosy golden fireplace glow against the blue snow.

## THE STORY, BY POSITION (0.0 → 1.0)

- Sunny Autumn (0.00–0.28): Grizzly lounges motionless in his deck chair soaking up the sun; Ice Bear tends the smoking barbecue grill; Panda snaps photos outside the cave with periodic camera flashes; birds glide across the clear sky.
- First Chill & Falling Leaves (0.29–0.52): Leaves shed in gusts; Grizzly lowers his sunglasses and shivers slightly; Ice Bear packs up the grill; Panda sneezes/rubs his paws as the first snowflakes touch his nose, while the birds fly off toward the horizon.
- Heading Indoors (0.53–0.78): One by one (Grizzly folding his chair, Ice Bear carrying the grill, Panda trotting last), the three bears walk single-file or stacked up to the cave front door and step inside.
- Hibernation Mode (0.79–1.00): The wooden cave door swings firmly shut; a small wooden "CLOSED" sign hangs down outside the door; snow piles up across the entire clearing, deck chair, and roof, while warm golden light glows cozily through the cave window and gentle smoke curls from the stone chimney.

## SOUND — all synthesised live with Web Audio, original cosy acoustic-lo-fi score

96 BPM, a warm four-bar loop in C major / A minor (Cmaj7 · Am7 · Fmaj7 · G6), on one lookahead-scheduled clock with a gentle swing.

Layers crossfade smoothly from crisp autumn acoustic to cosy winter chill:

0. Autumn (0.0): rustling dry leaves (band-passed noise), gentle breeze, and cheerful melodic bird chirps (FM sine sweeps).
1. Warm acoustic guitar / ukulele fingerpicking pattern (Karplus-Strong plucked strings) and subtle grill sizzle.
2. Soft brushed snare, mellow kick, and a warm upright bassline.
3. Winter transition (0.5–0.8): whistling winter wind, delicate celesta / music-box bell arpeggios, and muffled indoor bass.
4. Deep Winter (0.8–1.0): the music filters down into a warm, muffled low-pass (sounding like it's playing cozily inside the closed cave) paired with soft crackling fireplace embers and quiet snowy wind outside.

Switch & scene sounds:

- a warm wooden knock + jelly blop when grabbed, a soft snow-crunch plop when released;
- a crisp leaf-rustle / snow-brush noise following drag speed;
- a tiny camera shutter click-flash when passing Panda;
- a soft wooden door creak and firm latch thud + swinging sign clack around 0.80 when the bears close up the cave;
- a cosy chime when the cave window lights up.

Audio starts on the first touch; a Sound on/off button.

Readouts: Season (Golden Autumn / Crisp Breeze / First Frost / Snowfall / Hibernation), Weather (24°C Sunny → -4°C Snow), Audio (Birdsong / Ukulele / Breeze / Celesta / Fireside).
