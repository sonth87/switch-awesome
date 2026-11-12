# East Blue Duel Switch — Design Brief

Make "East Blue Duel Switch", No. 062 in a series of web material studies: an iconic Zoro vs. Mihawk sword-clash toggle in its own original style, as a single self-contained page (no libraries; raw WebGL2 + Web Audio + a 2D pixel buffer). Editorial layout: a small "Material Studies / No. 062 · WebGL + Web Audio" kicker, an italic serif title "East Blue Duel Switch.", a one-line caption; the switch centred and large; below it readouts (Phase, Tension, Audio), a hint line and a "Sound on/off" button. The whole page's colours (background, text, lines) follow the switch from bright East Blue ocean-sky daylight at the ends to a high-contrast storm-amber and crimson clash palette at the centre. Works at phone width.

## THE SWITCH

A pill-shaped switch in a moulded bezel: weathered teak wood and brass trim by the edges, shifting to dark tempered steel at the peak of the clash. A soft drop shadow falls on the page and fades to nothing before the canvas edge, with a slight inner shadow along the top of the track.

Inside, a 176×50 pixel-art marine deck scene, redrawn every frame on the CPU and shown with nearest sampling, never smoothed. Whole device pixels per scene pixel where there is room.

The knob is a vertical capsule of clear jelly glass, drawn in one full-canvas WebGL2 fragment shader:

- Dynamic Climax Scaling: its baseline size is slightly taller than the track at both ends (0.0 and 1.0), and smoothly swells/magnifies as it approaches the centre (0.5)—reaching ~1.35× scale right at the sword-clash apex before shrinking back to normal as it passes toward the far end;
- it magnifies (~1.30× optical refraction) and bends the pixels under it, intensifying the lens distortion at the centre;
- it splits R/G/B at its rim, with a darker refraction band, a bright edge and a Fresnel tint (white-gold at the clash, ocean-cyan at the ends);
- two highlights: a long soft streak at the upper left and a small dot at the lower right;
- light focused toward its foot, and a soft shadow on the wooden deck.

The knob lags the finger on a spring, stretches horizontally with speed (squashing vertically to keep its volume), and wobbles on a damped spring fed by its acceleration (plus high-frequency micro-vibration when locked at the centre clash).

Inside the knob the scene is rendered with heightened contrast and impact frames: the glass acts like a combat lens highlighting the steel edges and spark trails.

Controls: drag the knob or drag anywhere on the track; tap to toggle to the other end (it travels there on its spring, briefly flaring as it crosses the centre); arrow keys, Home/End, Space/Enter; role="slider" with aria values.

## THE SCENE (Baratie deck, crisp anime-inspired pixel palette)

Built from filled shapes stamped with an automatic 1-px outline and a light top / dark bottom, so every character and prop reads as a crisp pixel sprite:

- sunlit East Blue ocean waves rolling in the background, clear sky with drifting cumuli, and the ornate fish-shaped prow/railings and mast rigging of the floating restaurant ship Baratie;
- warm honey-oak deck planks with subtle wood grain and perspective lines;
- a crowd of onlookers lined up along the back railing in varied pixel silhouettes and colours (Sanji in a dark suit with blonde hair, Luffy in his straw hat, Usopp, Johnny & Yosaku, and Baratie chefs in tall white hats) reacting dynamically to the duel;
- Roronoa Zoro (green hair, white shirt, dark haramaki belly-warmer, black bandana—tied on as tension rises—wielding his three katana: Wado Ichimonji in his mouth and two blades in hand);
- Dracule Mihawk (feathered black hat, crimson/black coat, golden cross pendant, piercing yellow eyes, holding his tiny silver-and-gold Kogatana pocket dagger).

## LIGHT AND ATMOSPHERE

The knob controls the dramatic tension across the deck, blending with a 4×4 Bayer dither and sharp anime speed-lines around the knob's position:

- at both ends (0.0 and 1.0): bright, calm East Blue daylight, gentle sea breeze, crisp shadows;
- approaching and at the centre (0.35–0.65): sky darkens into dramatic slate-blue and fiery sunset-amber clouds, wind gusts whip across the deck, and radial anime impact lines + black-and-white flash frames pulse from the centre.

Every spark emitted at the centre casts tiny flickering dithered orange-white glints onto the surrounding onlookers and deck planks.

## THE DUEL STORY, BY POSITION (0.0 → 0.5 → 1.0)

- Start (0.00–0.20 — Standoff): Zoro stands on the left in his three-sword stance; Mihawk stands calmly on the right, casually holding the tiny Kogatana dagger with one hand. Onlookers watch tensely; Sanji's cigarette smoke drifts up.
- The Charge (0.20–0.44 — Closing In): Both fighters dash toward the middle, leaning low with trailing wind streaks and afterimage ghosts; onlookers lean forward in shock.
- The Clash (0.45–0.55 — Blade Lock at Centre): Zoro's three katanas collide dead-centre against Mihawk's tiny Kogatana dagger. Both sprites lock in a trembling, high-tension parry pose while continuous showers of bright yellow, orange, and white pixel sparks spray outward, bouncing off the deck with gravity. Speed-lines radiate behind them and onlookers shield their eyes.
- The Pass-Through (0.56–0.80 — Cross-Slash): Both fighters burst past each other in opposite directions with sharp white crescent slash trails cutting across the screen; Zoro's two outer blades shatter into spinning pixel fragments in mid-air while Wado Ichimonji remains intact.
- Aftermath (0.80–1.00 — Back-to-Back): Both stand motionless on opposite sides with their backs turned to each other (Zoro now on the right, Mihawk on the left), wind blowing their clothes and cape, broken blade pieces resting on the planks, while the crowd stands frozen in stunned silence (! / sweat-drop pixel emotes over Luffy and the chefs).

## SOUND — all synthesised live with Web Audio, original swashbuckler-duel score

126 BPM, a dramatic four-bar loop in D minor / Dorian (Dm · B♭ · Gm · A7), on one lookahead-scheduled clock.

Layers crossfade dynamically by proximity to the centre (0.5) and progress from 0.0 to 1.0:

0. Calm ends (0.0 & 1.0): ocean waves (slowly modulated filtered pink noise), creaking wooden ship timbers, and calling seagulls.
1. Approach (0.2 / 0.8): tense pizzicato strings and a lone acoustic guitar / shamisen motif.
2. Duel surge (0.35 / 0.65): driving taiko/timpani war drums, staccato brass swells, and fast bowed bass.
3. Centre Apex (0.45–0.55): full dramatic orchestral-rock climax with pounding drums, roaring synth-brass chords, and rhythmic metallic clash accents synced to the spark bursts.

Switch & combat sounds:

- a crisp steel unsheathing shing + glass tink when grabbed, a heavy wooden deck thud when released;
- a rushing wind whoosh scaled to drag velocity;
- Continuous Spark Clash at Centre (0.45–0.55): rapid, randomized high-frequency metallic pings, ringing steel resonance (FM bell partials at 2.4 kHz–4.8 kHz), and crackling spark noise bursts while held near the middle;
- a sharp anime slash-snap + shattering glass/steel chime as the knob crosses past 0.58 (when Zoro's two swords break);
- a deep, somber wind gust and single resonant shamisen note when settling into the back-to-back stance at 1.0.

Audio starts on the first touch; a Sound on/off button.

Readouts: Phase (Standoff / Dash / Blade Lock / Cross-Slash / Back-to-Back), Tension (0%–100%–0%), Audio (Sea Breeze / Shamisen / War Drums / Steel Clash / Silence).
