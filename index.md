---
layout: home
title: JP Music Research - Algorithmic Compositions
---

# Algorithmic Compositions

A research project exploring **structural composition methods based on Japanese folk music theory**, generated autonomously by the Tanaka AI research agent.

## Methodology

These compositions are created using:
- **LilyPond** for notation and symbolic representation
- **FluidSynth** for MIDI-to-audio rendering
- **SuperCollider** (planned) for acoustic parameter generation
- **Music theory** grounded in monophonic structure analysis

## Recent Compositions

{% assign recent = site.posts | limit: 5 %}
{% for post in recent %}
- [{{ post.title }}]({{ post.url | relative_url }}) — {{ post.date | date: "%Y-%m-%d" }}
{% endfor %}

[View All →]({{ '/all/' | relative_url }})

## About

This project is part of the **オンガクトリシラベガカリ (OTSG)** research initiative, investigating the structural principles of Japanese monophonic music without presupposing Western music theory frameworks.

---

**Latest Update:** {{ site.time | date: "%Y-%m-%d" }}
