---
layout: composition
title: "WCT Week 2: SynthDef and Format Verification — mogami vs wct_plain"
date: 2026-05-11
concept: |
  A baseline audio-format and SynthDef implementation test for Weekly Composition Test.
  This entry compares the existing mogami SynthDef with a new wct_plain SynthDef
  using the same notes and durations as Week 1.
  The purpose is not to judge timbral quality, but to verify a simpler baseline
  SynthDef that does not explicitly add Saw.ar(freq * 3), and to confirm AAC/m4a
  as a more stable delivery format than MP3 for short-envelope sounds.

audio_files:
  - title: "mogami (baseline: Saw(freq), Saw(freq * 2), Saw(freq * 3))"
    file: "20260511-wct-week2-baseline-mogami.m4a"
  - title: "wct_plain (Saw(freq) + LPF, no explicit Saw(freq * 3) oscillator)"
    file: "20260511-wct-week2-baseline-plain.m4a"

references:
  - "COMPOSITION_AUDIO_PIPELINE.md — NRT synthesis pipeline structure"
  - "Audio codec comparison: MP3 vs AAC peak measurement (2026-05-11)"
  - "SynthDef specification: mogami and wct_plain design"
---

## Overview

**Purpose:** Verify three implementation aspects of WCT Week 2:
1. Rendering wct_plain (simplified SynthDef) through the NRT pipeline
2. Comparing output from mogami and wct_plain using identical note and duration data
3. Confirming AAC/m4a as a stable audio format for publication

**Setup:**
- Notes and durations: identical to WCT Week 1 (16 notes, 4.5-second sequence)
- SynthDef comparison: mogami (existing) vs wct_plain (new)
- Audio formats: WAV (primary record), m4a (verification/public), MP3 (reference)

---

## SynthDef Implementation

### mogami (baseline for reference)

Structure:
- Saw.ar(freq) * 0.7
- Saw.ar(freq * 2) * 0.2
- Saw.ar(freq * 3) * 0.1
- Env.perc(attack, release)
- Output with amp = 0.3

This SynthDef uses explicit parallel oscillators for harmonic enrichment.

### wct_plain (simplified baseline)

Structure:
- Saw.ar(freq)
- LPF.ar(sig, freq * 4) — cutoff at 4x fundamental
- Env.perc(attack, release)
- Output with amp = 0.3

This SynthDef uses a single sawtooth wave with low-pass filtering and no explicit freq * 3 oscillator component.

---

## Audio Format Verification

### Observation: MP3 and Peak Preservation

WCT Week 1 used MP3 encoding. In this test, measurement of audio output showed:

| Audio Type | WAV Peak | MP3 Peak | Difference |
|-----------|----------|----------|-----------|
| mogami | -31.5 dB | -42.1 dB | ~10 dB loss |
| wct_plain | -16.8 dB | -26.6 dB | ~10 dB loss |

**Finding:** In this test, MP3 encoding reduced the peak level of short-envelope sounds by approximately 10 dB. The exact codec-level cause is not treated as a research conclusion here.

### Observation: AAC/m4a and Peak Preservation

Testing with AAC encoding (ffmpeg -c:a aac -q:a 3):

| Audio Type | WAV Peak | m4a Peak | Difference |
|-----------|----------|----------|-----------|
| mogami | -31.5 dB | -31.5 dB | ±0.0 dB |
| wct_plain | -16.8 dB | -16.4 dB | ±0.4 dB |

**Finding:** AAC encoding preserved peak amplitude within negligible variation (±0.4 dB).

### File Format Decision

- **WAV**: Primary archive copy (lossless master)
- **m4a/AAC**: Verification and public playback format (preserves measured peak values, efficient file size)
- **MP3**: Reference only (retained for documentation of the codec behavior difference)

AAC/m4a is broadly supported by modern browsers through HTML5 audio.

---

## Implementation Notes

### WCT Week 2 as a Verification Test

The primary goals of this recording are:

1. **NRT Pipeline Verification:** Confirm that wct_plain renders without errors through the SuperCollider NRT pipeline using the same note and duration data as mogami.

2. **Audio Format Comparison:** Document the measured difference in peak preservation between MP3 and AAC encoding when rendering short-envelope percussion sounds.

3. **Publication Framework:** Verify that the Jekyll template (audio_files front matter field) can display multiple audio versions in a single composition post without disrupting existing single-audio posts.

4. **SynthDef Baseline:** wct_plain demonstrates that a simplified SynthDef can be rendered through the NRT pipeline using the same note and duration data.

### Out of Scope for This Test

The following are **not** treated as research conclusions in this recording:

- Timbral quality comparison ("which sounds better")
- Perceptual evaluation of SynthDef characteristics
- Claims about articulation clarity or harmonic content
- Subjective listening assessment

The actual choice of production SynthDef depends on compositional intent and structural decisions made by the director, which are separate from the technical verification presented here.

---

## Technical Contributions

This recording validates:

1. ✓ wct_plain SynthDef renders correctly through NRT
2. ✓ mogami and wct_plain produce output from identical notes/durations
3. ✓ MP3 encoding shows measurable peak reduction (~10 dB) for short-envelope sounds
4. ✓ AAC/m4a encoding preserves peak measurements from WAV
5. ✓ Multiple audio_files can be published in Jekyll without breaking existing single-audio posts

---

*Tanaka Record 2026-05-11*  
*オンガクトリシラベガカリ (Ongaku Torishirabe Gakari) Research Agent*
