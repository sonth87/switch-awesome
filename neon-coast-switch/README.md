# Neon Coast Switch
## Material Studies No. 066 — WebGL2 + Web Audio

A single self-contained page: a big horizontal toggle switch holding a 176×50 pixel-art coast road. Drag a lens of amber aviator glass from golden hour to night; the street switches on behind it, and a convertible with a dog and a cat follows the glass. Open `neon-coast-switch.html` in a WebGL2 browser. No libraries, no assets.

## Controls

- **Drag** the lens (or drag anywhere on the track). Arrow keys, Home / End; Enter or Space sends it to the far end with a double honk. `role="slider"`.
- **Tap** the scene (hover shows corner brackets on what can be tapped). Touches on the lens always mean the car.
- **H** honks and hops the car.
- **Sound on/off** button; audio starts on the first touch.
- `#t=0.8` in the URL starts the knob at a position (0–1).

| Tap | What happens |
| --- | --- |
| Lens / H | the convertible hops on its hydraulics and honks |
| Road | the car drives to that spot |
| Palm | fronds shake, a coconut falls (and bonks the dog if the car is under it) |
| Hotel window | three knocks, the room lights, a silhouette, "hey!", a "!" |
| Store | door chime, sliding door, the clerk waves; three taps after dark start the hold-up |
| Diner | order bell, a roller-skating carhop brings the dog a milkshake |
| Neon sign | shorts out with sparks and a stuttering buzz |
| Sea | a dolphin leaps |
| Lifeguard tower | whistle trill, flag flaps |
| Traffic car | honks back at its own pitch and flashes |
| Police car | bullhorn yelp, radio chatter |
| Helicopter | radio squelch, the searchlight swings onto you |
| Sky | night: shooting star and chime; day: a gull flies in |

Stop for a few seconds and the dog drums on the door in time with the music; wait longer and he leans on the horn.

## Story

- **Pursuit:** after dark, drive fast and a black-and-white police car takes your tail. Slow down and it swings out, overtakes and leaves; the dog barks.
- **Hold-up:** late at night once the far lane is clear (or after three store taps in the dark): the store window shatters, masked thieves run to a yellow muscle car, the police slide in, about five seconds of stylised, bloodless gunfire, then a getaway and a chase. The dog and cat duck down. The helicopter's searchlight follows.
- Readouts: Clock 18:30 → 23:30, Speed in mph, Status (Cruising / Speeding / Pursuit / Lost them / Alarm / Shots fired / Getaway).

## How it is built

- **Rendering:** CPU buffers for albedo, emission and two light layers (street lights masked by the knob, dynamic lights always on). Sprites are stamped with an automatic outline, a light top row and a dark bottom row; painting a pixel clears the glow behind it. Light pools and cones are quantised through a 4×4 Bayer matrix. Neon uses a 3×5 pixel font and line shapes.
- **Shader:** one WebGL2 fragment shader draws the moulded bezel and the capsule lens: magnification 0.78 sampling (sampled slightly low so the whole car shows), RGB-split rim refraction, Fresnel edge, light focused at its foot, highlights and an amber gradient tint, darker at the top. The lens reads a fully lit copy of the scene.
- **Audio:** everything synthesised live. 100 BPM, four bars of A minor (Am · F · C · G) on one lookahead clock, layered by knob position (coast bed → pad and arpeggio → drums and bass → lead → FM bells, toms, crash). Compressor, reverb and a dotted-eighth echo; music sits about 5 dB under the effects and ducks under gunshots. During a chase or hold-up the bass doubles to sixteenths and chord stabs enter.

## Browser support

Needs WebGL2 and Web Audio. Developed against Chrome.
