# East Blue Duel Switch
## Material Studies No. 062 — WebGL2 + Web Audio

A single self-contained page: a big pill switch holding a 176×50 pixel-art restaurant-ship deck on a calm blue sea. Drag a capsule of jelly glass across it and you play out a sword duel: a three-sword swordsman and a master with a pocket dagger close in, lock blades at the centre and cut past each other. The knob widens into a combat lens at the clash and narrows back at the ends. Open `east-blue-duel-switch.html` in a WebGL2 browser. No libraries, no assets.

Fan study of the One Piece Baratie duel (characters © Eiichiro Oda / Shueisha). The pixel sprites and the score are drawn and synthesised from scratch.

## Controls

- **Drag** the knob, or drag anywhere on the track. **Tap** to send it to the other end; it flares as it crosses the centre.
- Arrow keys, Page Up / Down, Home / End; Space or Enter flips it. `role="slider"` with aria values.
- **Sound on/off** button; audio starts on the first touch.
- `#t=0.5` in the URL starts the knob at a position (0–1).

## Story, by position

Tension runs 0% → 100% → 0%, peaking at the centre.

| Position | Phase | Audio | What happens |
| --- | --- | --- | --- |
| 0.00–0.20 | Standoff | Sea Breeze | Zoro in the three-sword stance on the left; Mihawk calm on the right with the Kogatana. The crowd at the rail watches; Sanji's smoke drifts. Bandana goes on past 0.15. |
| 0.20–0.45 | Dash | Shamisen → War Drums | Both close in, leaning low, with afterimage ghosts and wind streaks. The crowd leans in. |
| 0.45–0.55 | Blade Lock | Steel Clash | Three katana against one dagger, trembling. Spark showers bounce off the deck and flicker glints on the crowd and planks; speed-lines and flash frames; the crowd shields its eyes. The knob micro-vibrates. |
| 0.55–0.80 | Cross-Slash | War Drums → Shamisen | They burst past each other under two white crescent slashes. At 0.58 the two hand blades shatter into spinning fragments; Wado stays whole. |
| 0.80–1.00 | Back-to-Back | Sea Breeze → Silence | Both hold their cross-slash follow-through, backs turned, coat and bandana in the wind, fragments on the planks. "!" over Luffy and the chefs, sweat drops on the rest. A wind gust and one shamisen note at the end. |

## How it is built

- **Pixel buffer:** CPU albedo with a per-pixel kind (sky, emissive, sea, deck, steel). Sprites are stamped with an automatic outline, a light top row and a dark bottom row. The duellists are drawn in a mirrored sprite space so one pose set serves both facings. Two skies are drawn every frame: calm blue with white cumuli, and storm slate with amber-lit cloud bellies.
- **Light:** a storm zone grows around the knob with tension and dissolves into the calm deck through a 4×4 Bayer dither (slate grade, amber rims on the skyline). Spark glints, radial speed-lines from the knob and half-bar black-and-white flash frames sit on top. The lens samples a separate buffer with stronger contrast and saturation, white-hot steel, and an impact frame on every beat. Flash frames are switched off under `prefers-reduced-motion`.
- **Shader:** one WebGL2 fragment shader. The bezel is teak with a brass trim ring, tempering into brushed dark steel with tension. The knob is a fully rounded box: at the centre it widens to 2.5× and drops to 80% height, ends staying semicircular, magnifies 1.30–1.44×, splits RGB at the rim, has a Fresnel tint from ocean-cyan to white-gold, two highlights, light at its foot, a shadow on the deck and a flare when it crosses the centre fast. It follows a spring, stretches with speed and wobbles.
- **Audio:** all synthesised live. 126 BPM, four bars of D minor (Dm · B♭ · Gm · A7) on one lookahead clock, layered by tension: sea swell, timber creaks and gulls → Karplus–Strong pizzicato and a shamisen motif → taiko, staccato brass and bowed bass → a rock kit, synth-brass and FM-bell clash accents. Combat sounds: steel shing on grab, deck thud on release, a wind whoosh on drag, random FM pings and crackle with every spark burst, the slash-snap and shatter at 0.58, and the closing gust and shamisen note.

## Browser support

Needs WebGL2 and Web Audio. Developed against Chrome.
