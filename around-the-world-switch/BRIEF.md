Make "Around the World Switch", No. 062 in a series of web material studies: an interactive continuous-scrubbing global horizon slider in its own original style, as a single self-contained page (no libraries; raw WebGL2 + Web Audio + a 2D pixel buffer). Editorial layout: a small "Material Studies / No. 062 · WebGL + Web Audio" kicker, an italic serif title "Around the World Switch.", a one-line caption; the switch centred and large; below it readouts (Destination, Local Time, Audio), a hint line and a "Sound on/off" button. The whole page's colours (background, text, lines) smoothly shift along with the globe's day-to-night cycle—from bright sunlit morning sky at Vietnam (0.0) through golden afternoon in Japan and twilight dusk in France to deep starry midnight in the USA (1.0). Works at phone width.

THE SWITCH

A pill-shaped switch in a moulded bezel: warm ivory ceramic at dawn/day, gradually shifting into deep aerospace titanium-indigo as the globe rotates into night. A soft drop shadow falls on the page and fades to nothing before the canvas edge, with a slight inner shadow along the top of the track.

Inside, a 352×100 pixel-art world panorama (twice the usual 176×50 density, to fit sixteen landmarks), redrawn every frame on the CPU and shown with nearest sampling, never smoothed. Whole device pixels per scene pixel where there is room.

The knob is a vertical capsule of clear jelly glass, a little taller than the track, drawn in one full-canvas WebGL2 fragment shader:

it magnifies (~1.28×) and bends the pixels under it like an optical atlas loupe;

it splits R/G/B at its rim, with a darker refraction band, a bright edge and a Fresnel tint;

two highlights: a long soft streak at the upper left and a small dot at the lower right;

light focused toward its foot, and a soft shadow on the horizon below.

Continuous Free-Position Scrubbing: unlike a binary two-state toggle, this slider has no forced snap to the ends—dragging and releasing lets the knob settle smoothly on its spring at any arbitrary position (0.00–1.00) along the track so the user can pause and admire any country or time zone (tapping on the track glides smoothly to that clicked longitude; arrow keys step smoothly across countries). role="slider" with aria-valuemin="0", aria-valuemax="100", aria-valuenow.

The knob lags the finger on a spring, stretches horizontally with speed (squashing vertically to keep its volume), and wobbles on a damped spring fed by its acceleration.

Inside the knob the scene reveals crisp golden-hour architectural detail and subtle latitude/longitude coordinate ticks along the glass rim.

FLAT-TO-GLOBE CURVATURE & CELESTIAL CYCLE (0.0 → 1.0)

Flat-to-Spherical Horizon Morph:

At the start (0.00, Vietnam), the ground sits as a flat horizontal skyline across the lower third of the frame.

As soon as the user begins dragging the knob (0.01 → 0.12), the flat ground smoothly bends upward at the centre and curves downward at both edges into a rotating convex Earth arc (with subtle atmospheric rim glow and ocean/land curvature), rotating westward continuously in sync with the knob's position! (Returning back to 0.00 smoothly flattens the horizon back into a level panorama).

Sun & Moon Orbital Arc:

At 0.00 (Vietnam), a bright morning sun hangs high in a clear azure sky with drifting white clouds.

As the knob moves rightward across longitudes, the sun arcs steadily downward toward the western horizon, painting the sky in warm golden-hour amber and coral-violet over France, before dipping below the Earth's curve as a glowing crescent moon and twinkling stars rise into a deep midnight sky over the USA (1.00).

As night falls, city windows, bridge cables, and monument floodlights automatically switch on with warm dithered glows.

THE FOUR COUNTRIES ALONG THE GLOBE (crisp 1-px outlined pixel sprites)
Each landmark rises organically along the rotating Earth curve with layered foreground/background parallax:

Vietnam (0.00–0.24 — Bright Morning):

Khuê Văn Các (crimson-and-gold pavilion roof over white brick arches);

Hanoi Flag Tower (Cột cờ Hà Nội) (tiered ochre bastion topped with a fluttering red-and-yellow star flag);

Bitexco Financial Tower (sleek glass skyscraper with its signature protruding helipad);

Dragon Bridge of Da Nang (Cầu Rồng) (arched yellow steel dragon spanning river ripples, puffing tiny pixel fire/water sparks).

Japan (0.25–0.49 — Golden Afternoon):

Torii Gate (vermilion Shinto gate standing in shimmering coastal water);

Himeji Castle (layered white-plastered tiered roofs and stone keep);

Mount Fuji (symmetrical indigo cone crowned with a crisp white snowcap and drifting cloud ring);

Tokyo Skytree / Tokyo Tower (tall lattice spire rising into the afternoon sky, plus tiny cherry blossom petals drifting by).

France (0.50–0.74 — Sunset & Dusk):

Arc de Triomphe (grand limestone arch anchored at the avenue);

Eiffel Tower (intricate wrought-iron lattice silhouette, sparkling with golden lights as dusk deepens);

Notre-Dame Cathedral (twin Gothic bell towers and central rose window);

Louvre Pyramid (faceted translucent glass pyramid glowing warmly in the courtyard).

USA (0.75–1.00 — Starry Night):

Statue of Liberty (verdigris-green Lady Liberty holding aloft a flickering golden torch);

Empire State Building (Art Deco limestone tower with illuminated spire);

Washington National Cathedral (soaring Neo-Gothic twin towers and flying buttresses in Washington, D.C.);

Golden Gate Bridge (international-orange suspension towers and glowing cable lights spanning dark bay waters).

SOUND — all synthesised live with Web Audio, original globetrotting score

108 BPM, an uplifting four-bar chord progression (Cmaj7 · Em7 · Fmaj7 · Gsus4) on one lookahead-scheduled clock, smoothly morphing its lead instrumentation to match whichever country is currently centred on the globe:

Vietnam (0.00–0.24): bright pentatonic Đàn Tranh (zither) plucks (Karplus-Strong bright string synthesis) over gentle morning breeze and distant river ripples.

Japan (0.25–0.49): expressive Koto & Shakuhachi flute intervals (In-sen / Yo scale ornaments with breathy vibrato) and delicate wind chimes.

France (0.50–0.74): romantic French Accordion / Musette chords (detuned warm reed oscillators with gentle vibrato) and brushed waltz-tinged percussion.

USA (0.75–1.00): smooth late-night New York Lo-Fi Jazz (warm Rhodes electric piano chords, muted upright bass, soft vinyl crackle, and relaxed snare brushes).

Switch & atmospheric sounds:

a tactile glass tink + soft compass click when grabbed, a cushioned detent thud when released anywhere along the track;

a subtle rushing stratospheric wind whoosh proportional to globe rotation speed;

soft melodic landmark chimes as each country's skyline crests the centre of the Earth arc.

Audio starts on the first touch; a Sound on/off button.

Readouts: Destination (Vietnam · Hanoi / HCMC / Da Nang → Japan · Himeji / Fuji / Tokyo → France · Paris → USA · NYC / D.C. / SF), Local Time (08:00 AM → 01:30 PM → 06:45 PM → 11:30 PM), Audio (Đàn Tranh / Koto & Flute / Paris Musette / Midnight Jazz).
