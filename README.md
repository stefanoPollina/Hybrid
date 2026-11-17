# Continuum Rack · Parallel Hybrid Architecture

A browser synthesizer laid out like a modular rack: 8 banks × 8 engines (64 voices), patch cables between banks, a 64-step sequencer for each bank, a live DSP editor, oscilloscopes and a factory patch library. It is all one self-contained `index.html` and uses the Web Audio API, with no build step and no dependencies.

## Run it

Open `index.html` in Chrome, Edge or Firefox, then press **POWER** on the CORE module (top-left) to start audio. The rack opens on **Squelch Dub**, a pre-cabled acid dub patch (acid 303, dub chords, sub, kick, hats and siren at 118 BPM). Press **RUN SEQ** to hear it straight away. Loading any factory recipe or saved patch replaces the demo patch.

To host it, any static host works. For GitHub Pages: **Settings → Pages → Deploy from branch → root**. The empty `.nojekyll` file stops Jekyll from processing the site.

## Repository layout

```
index.html                         the whole synth: HTML, CSS and JS in one file
patches/example-two-bank-send.json example rack patch (Bank 1 → Bank 3 send, LFO → Bank 3 MOD)
README.md
CHANGELOG.md
.nojekyll
```

## The rack

| Row | Modules |
|---|---|
| 1 | CORE (transport, save/load) · MIDI IN · MASTER · DELAY · LFO · SCOPE · OCTOSCOPE · ROUTER · SCENES |
| 2 | SEQ 8×64 · DSP EDITOR |
| 3–6 | Two banks per row: channel strip (level, pan, filter, insert, meter, IN/MOD/OUT jacks) + 8 engines |
| 7 | KEYS · ENGINE ATLAS · FACTORY · MUTATOR |

The eight engine types each have their own panel: Acid 303, Hybrid, FM Matrix, Wavefold, Wavetable, Resonator, Additive and Crossmod.

## Scenes (43 full-rack presets)

The **SCENES** module (top-right) and **Library** menu load a complete rack: engines, bank settings, sequences, cables and FX. Scenes switch live; the sequencer keeps running.

Dub & roots: Squelch Dub · Roots & Culture · Psydub · Dub Techno Deep · Dub House · Steppa · Ragga Jungle
Acid: Acid House · Acid Arab · Acid Breaks · Acid Rave · Tech Trance
House & minimal: Rominimal · Minimal House · Hypnotic Minimal · Tech House · G-House · Funky Tech Groove · Latin Tech · Future Funk · Tribal House
Global: Folktronica · Afrobeats · Afro Tech · Bashment
Techno: Melodic Techno · Detroit Techno · UR Militant · Warehouse · Peak Time · Industrial · Tribal Core · Techcore · EBM · Bleep & Bass
Electro & broken: Electro · IDM Braindance · UK Garage · Breakbeat Hardcore · Dubstep
Fast: Psytrance · Techstep · Liquid DnB

## Engine Atlas (58 engine patches)

8 Continuum originals plus 50 patches converted from genre reference specs (`reference/engine-patches-converted.json`). The converter maps oscillator waveforms and levels, osc-2 detune, filter type, cutoff (Hz → this engine's cutoff curve), resonance, envelope amount, amp ADSR (ms → engine curves), LFO target/rate/depth and drive. Things this engine has no control for — osc-2 octave offsets, pitch envelopes, glide, chorus and reverb — are approximated or left out.

## Controls

- **Knobs:** drag up/down; hold Shift for fine control; double-click to reset; arrow keys work when a knob is focused.
- **Cables:** drag from an OUT jack to an IN jack. To move or remove a cable, pull its plug off the input. Right-click a jack to clear its cables.
  - Bank OUT → later bank IN sends audio forward, at the ROUTER's send level (0–40%). Patches are forward-only, so no feedback loops, with a maximum of 12 sends.
  - LFO OUT → bank MOD chooses which banks the global LFO reaches. With nothing patched, it reaches all banks.
- **Rack:** opens at full size (100%) and remembers your zoom. Ctrl/⌘ + scroll (or pinch) zooms; View → Zoom to fit width shrinks it to the window; View → Full screen (Shift+F) hides the browser chrome. Drag empty rails to pan.
- **Notes:** A W S E D F T G Y H U J K on your computer keyboard, the on-screen keys, or MIDI via MIDI IN → CONNECT.
- **View menu:** room lights, cable opacity and cable tension.

## Patch formats

| File | Format id | Where |
|---|---|---|
| Full rack | `continuum-synth-p01` | CORE ↓ SAVE / ↑ LOAD, or the File menu |
| Single engine | `continuum-black-mamba-engine-p17` | ENGINE ATLAS ↓ EXPORT / ↑ IMPORT |
| Factory recipe | `continuum-synth-p14-patch` | FACTORY ↓ JSON |

Rack patches from earlier versions still load. Cables are stored in `state.cables` as `{from, to, color}`, using jack ids `bo:N`, `bi:N`, `bm:N` and `lfo`. Saved engine patches are kept in the browser's `localStorage` under `continuum-black-mamba-p17-engine-patches`.

## Notes on the DSP

The eight voice models are original, lightweight Web Audio designs inspired by those families of synthesis. They are **not** ports of Open303, Surge XT, Dexed, Plaits, Vital or any other third-party code.
