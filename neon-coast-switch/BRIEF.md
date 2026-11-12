Build a single-file web page called "Neon Coast Switch" (Material Studies No. 066, WebGL + Web Audio). It is a big horizontal pill-shaped toggle switch. Inside it is a 176×50 pixel-art scene of a sun-soaked beach town on a coast road, in a crime-thriller mood: golden hour, pastel art deco, neon, palms, fast cars, police. The knob is a capsule of amber-gradient glass, like an aviator lens. No libraries. Everything original: invented names, no real brands. English UI.

SCENE
Rendering: CPU pixel buffers for albedo and emission. Sprites get an automatic dark outline, a lighter top row and a darker bottom row. Painting a pixel clears its glow, so things hide the light behind them.

Left, the beach:
- the sun, banded at the bottom, sinking into the sea, with glitter on the water and surf on the sand;
- a teal lifeguard tower with a pink roof and a red flag;
- a striped umbrella, a surfboard, a palm, a low sea wall.

Then a boulevard, in front of far blue towers with rows of windows and blinking antenna lights:
- a pink hotel "CORAL" with teal ledges, rows of windows and a roof sign;
- an all-night store with a "MART" fascia, a "24H" sign on a post, and a glass front with shelves;
- a mint-and-chrome diner with "OPEN" and a neon palm on its roof;
- a lavender deco club with a "SUNSET" roof sign and a neon flamingo on its wall;
- palms with swaying fronds, and four street lamps;
- a pavement, a kerb, and a two-lane road with yellow dashes.

Sky: golden-hour blue and peach, then magenta dusk, then night with a moon and stars. Gulls fly over the beach while it is light.

Neon: tubes are drawn from a tiny 3×5 pixel font and simple line shapes. Off, they are dark glass. On, they glow with a halo. Each sign flickers as it catches. Late at night the SUNSET letters chase on the beat.

LIGHT
- Ambient light moves from golden hour to dusk to night.
- Behind the knob the street comes on, all with 4×4 Bayer-dithered edges:
  - windows light up: warm, pink, cool, fluorescent in the store, some left dark;
  - street lamps pool orange sodium light;
  - each neon sign spills its colour.
- A bright dithered rim trails the knob.
- Also lit: headlight beams on the road, red and blue police-light pools, a helicopter searchlight cone and its pool, and muzzle flashes lighting their surroundings.

THE CONVERTIBLE
- A coral convertible with a white stripe and chrome follows the knob on a spring in the near lane. Its wheels turn.
- A dog in sunglasses drives; his ears flap back and his tongue hangs out at speed. A white cat in sunglasses rides in the back, and her lenses glint.
- Effects: exhaust puffs when accelerating, speed lines when fast, brake lights, tyre smoke and a squeal on hard reversals.
- The glass lens magnifies the car. Sample slightly low so the whole car shows.

STREET LIFE
- Traffic drives left in the far lane: sedans, coupes, vans, a yellow taxi. Lights come on at night.
- After dark, driving fast brings a black-and-white police car onto your tail with flashing lights. Slow down and it gives up, swings out, overtakes and leaves; the dog barks.
- A helicopter arrives at night, with a blinking beacon and a flickering rotor. It sweeps a searchlight and follows the chase.

THE HOLD-UP
It happens late at night once the far lane is clear, or earlier if the store is tapped three times after dark. It plays out to the left of the knob.
1. The store window shatters and an alarm flashes. Two masked figures in teal jackets, one carrying a sack, run out and crouch behind a yellow muscle car.
2. A police car slides to a stop, and two officers in blue crouch behind it.
3. For about five seconds both sides fire from cover: muzzle flashes, sparks and glass off the car bodies, ricochets, the scene flashing with each shot.
4. The two dive into their car and peel off left in tyre smoke. The police jump in and give chase.
5. The dog and the cat duck down in the convertible during the shooting.
Keep it stylised and bloodless; nobody is hit. The helicopter's light follows the action.

TAPPING THE SCENE
Each tap has its own synthesised sound. Hovering highlights what can be tapped. Touches on the knob always mean the car.
- The knob: the convertible hops on its hydraulics (air hiss, clunk, springs squeaking as it bounces) and honks. The H key does the same.
- The road: the car drives to that spot.
- Palms: the fronds shake and rustle and a coconut falls, knocking hollowly on the pavement. If the car is underneath, it bonks the dog on the head: a cartoon bonk and boing, a yelp, stars circling his head.
- Hotel windows: three knocks on the glass. The room lights up, a silhouette crosses it, a muffled "hey!" sounds and a "!" pops up above the window.
- The store: the door chime, the door slides open, the clerk waves. Three taps after dark start the hold-up.
- The diner: the order bell rings, and a carhop on roller skates (wheel rumble, clicks on the paving seams) rolls a milkshake out to the car. The dog drinks it with straw slurps and floating hearts, and she skates back.
- Neon signs: they short out with sparks, crackles and a stuttering buzz.
- The sea: a dolphin leaps with a splash, clicks and a whistle.
- The lifeguard tower: a trilled whistle, and the flag flaps.
- Traffic cars: they honk back, each at its own pitch, and flash their lights.
- The police car: a bullhorn yelp and radio chatter.
- The helicopter: a radio squelch, and its searchlight swings onto you.
- The sky: at night a shooting star with a chime; by day a gull flies in, crying.

IDLE
- Stop for a few seconds and the dog drums on the door in time with the music: soft knocks, the backbeat harder. The cat bobs her head.
- After a while he leans on the horn and barks.

GLASS (one WebGL2 fragment shader)
- A moulded bezel with a soft shadow; the scene sampled with nearest filtering.
- A capsule knob that magnifies (0.78) a fully lit render, with:
  - RGB-split refraction near the rim;
  - a Fresnel edge;
  - light focused at its foot;
  - highlights;
  - an amber aviator-gradient tint, darker at the top.
- The bezel is cream by day and dark plum at night.

INTERACTION
- The knob follows on a spring, stretches with speed and wobbles when it stops.
- Arrow keys, Home and End move it; Enter or Space sends it to the far end with a double honk; role="slider".
- The page colours follow the evening from peach to a deep night purple.
- Readouts:
  - Clock: 18:30 → 23:30.
  - Speed: in mph.
  - Status: Cruising / Speeding / Pursuit / Lost them / Alarm / Shots fired / Getaway.
- A Sound on/off button; the sound starts with the first touch.

AUDIO
All synthesised with Web Audio at 100 BPM: an original four-bar eighties synth-pop song in A minor over Am · F · C · G. Keep the music quiet, about 5 dB under the effects. Use a compressor, a reverb, and a dotted-eighth echo.

Layers, by knob position:
1. The coast: surf swells, gulls by day, a city hum at night.
2. A pumping detuned-saw pad and a filtered square arpeggio.
3. A gated snare, a short kick, hats, and an octave saw bass.
4. A detuned lead with glide and late vibrato.
5. Late at night: FM bells, toms and a crash.

During a chase or the hold-up, the bass doubles to sixteenths and chord stabs push the song along.

Sound effects:
- the engine climbing through its gears with speed, a tyre squeal, a two-tone horn;
- neon crackling and buzzing on, lamps ticking on;
- passing cars panned with a doppler drop;
- a wail/yelp siren panned to the police car; the helicopter's blade slap;
- the store alarm bell and breaking glass;
- gunshots with a crack, a thump and echoes off the buildings (the music ducks under them); ricochets; the getaway engine roar;
- the dog's yips and the cat's indignant meow;
- aviator-hinge clicks when the knob is grabbed;
- plus every tap and idle sound listed above.
