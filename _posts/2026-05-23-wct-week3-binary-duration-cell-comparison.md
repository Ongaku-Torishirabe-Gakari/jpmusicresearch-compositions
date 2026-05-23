---
layout: composition
title: "WCT Week 3: Binary Duration Cell Comparison"
date: 2026-05-23
concept: |
  This test is not intended as a finished musical work, but as an audio experiment comparing binary-duration cell structures. Duration sequences were extracted from lyric-aligned Japanese folk song MIDI event data. Based on nPVI analysis and duration classification, this test focuses only on binary-duration cells. Type A repeats the same cell, while Type B uses a cell sequence containing duration differences. Both types use the same pitch sequence and the same number of notes, but their total durations are not normalized.
audio_files:
  - title: "Type A: Repeated Identical Cells"
    file: "wct_week3_binary_duration_cell_type_a.m4a"
  - title: "Type B: Cell Transition with Duration Differences"
    file: "wct_week3_binary_duration_cell_type_b.m4a"
---

# WCT Week 3: Binary Duration Cell Comparison

## Overview

This test is not a finished musical work, but an audio experiment comparing duration-cell structures.

## Methodology

Duration sequences were extracted from lyric-aligned Japanese folk song MIDI event data.

Based on nPVI analysis and duration classification, this test uses only binary-duration cells.

## Comparison Design

**Type A: Repeated Identical Cells**
- Cell sequence: C1 → C1 → C1 → C1
- Duration values: 0.5 - 0.5 - 0.5 - 0.5 - 0.5 - 0.5 - 0.5 - 0.5 - 0.5 - 0.5 - 0.5 - 0.5
- Total duration: 6.0 beats

**Type B: Cell Transition with Duration Differences**
- Cell sequence: C1 → C4 → C2 → C1
- Duration values: 0.5 - 0.5 - 0.5 - 0.5 - 0.5 - 0.25 - 0.5 - 0.25 - 0.25 - 0.5 - 0.5 - 0.5
- Total duration: 5.25 beats

## Experimental Settings

* Type A and Type B use the same pitch sequence and the same number of notes (12)
* The total duration is **not normalized**
* The final cell in Type B is a comparison terminus, not an observed transition from the folk data
* Non-binary durations are kept as observation targets for later work, but are not used in this test

## Findings

Different cell-transition patterns within binary-duration systems produce audible differences in temporal structure when applied to identical pitch sequences.

---

Technical metadata is kept in the internal project report.
