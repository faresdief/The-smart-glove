# SignGlove Translator (The-smart-glove)

A pure-software sign language translation glove simulator: an interactive 3D glove (Three.js), a 16x2 LCD output module and Web Speech API voice output. 100% client-side.

**Live demo:** https://faresdief.github.io/The-smart-glove/

Five virtual flex sensors (one per finger) encode bent/extended states into a 5-bit gesture code (32 possible states), matched against a 15-entry word dictionary with Hamming-distance suggestions. The same encoding maps directly onto physical hardware (flex sensors -> microcontroller ADC -> thresholds -> 5-bit code), so the simulator works as a software twin for testing vocabularies before any hardware exists.

## Running locally

Any static file server works:

```bash
python3 -m http.server 8000
# open http://localhost:8000/
```

## Dependencies

Three.js r160 (`vendor/three.module.js` and `vendor/addons/controls/OrbitControls.js`) is vendored locally, so the 3D demo no longer depends on a CDN to boot. Tailwind CSS is loaded from its CDN for styling only; if it is unreachable the app still works, just unstyled.

## Resilience

A boot watchdog shows a visible error banner if the 3D module fails to start, instead of leaving the glove panel blank and the dictionary at 0 signs.

## Status

This is a software simulator and teaching/demo project. The dictionary is a custom 15-word vocabulary, not a validated sign language corpus.
