# Changelog

## Rack edition — 2026-11-17

The interface is rebuilt as a modular rack, in the style of VCV Rack. The audio engine and patch formats are unchanged.

### Added
- Rack layout: rails, screws, module panels with a different skin for each engine type, knobs, sliders, LEDs, LCDs and hex jacks.
- Patch cables with drag-to-connect, drag-to-unplug and right-click to clear, plus cable opacity and tension settings.
- LFO OUT → bank MOD patching. Unpatched, the LFO still reaches all banks, as before.
- Quick knobs on each engine for cutoff, resonance, filter envelope, attack and release, kept in sync with the DSP editor.
- DSP editor as one large module, with sliders for the ADSR and the eight harmonics.
- Level meters on every bank strip and the master, plus activity LEDs on every engine.
- Opens at full size (100%) and remembers your zoom level; zoom with Ctrl/⌘ + scroll or the View menu; pan by dragging.
- Full screen mode (View menu or Shift+F).
- Opens on "Squelch Dub", a demo patch at 118 BPM: a resonant acid 303 line with a wavefold grit layer, a dub-techno Cm7 chord stab, a sine sub, a kick, inharmonic FM hats and a dub siren. It has 7 cables (acid → drive return, chords → tremolo echo return, kick → hat bus, hats → high-passed siren bus, LFO → three MOD inputs) and dotted-eighth master echo.
- ROUTER send range widened from 0–18% to 0–40% so dub sends cut through.
- Room lights dimmer. It replaces the Day/Night theme.
- Web MIDI input module.
- 4-octave keyboard with glissando when you drag across the keys.

- SCENES module: 43 full-rack presets across dub, acid, house, minimal, global, techno, electro, breaks and DnB, switchable live.
- Engine Atlas expanded to 58 patches: 50 converted from genre reference specs (303 squelch, Reese/neuro, hoover, DX100 solid bass, Juno strings, log drum, Hijaz lead, dub siren, wobble and more).
- Sequencer step gates can now be up to 3200% (two bars) for pads, sirens and long sub notes.

### Changed
- The synthesis matrix is now the ROUTER module plus cables. Its send level is global.
- PLAY BANK now plays every enabled engine in the bank, not just the first.
- The tremolo insert now actually modulates, at 5.5 Hz; before, it did nothing.
- Saving uses the page's download permission when running as a published artifact. Opened as a plain file, it uses a normal browser download.

### Unchanged
- Voice DSP, bank bus chain, master drive, compressor and delay, sequencer scheduler, arpeggiator, engine targets and masks.
- The 32 factory recipes, the mutator and variations, and the P17 engine patch atlas.
- Patch formats `continuum-synth-p01`, `continuum-synth-p14-patch` and `continuum-black-mamba-engine-p17`.
