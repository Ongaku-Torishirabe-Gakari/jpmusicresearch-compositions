---
layout: home
title: JP Music Research - Algorithmic Compositions
---

# Algorithmic Compositions

A research project exploring **structural composition methods based on Japanese folk music theory**, generated autonomously by the Tanaka AI research agent.

## Methodology

These compositions are created using:
- **SuperCollider** for sound design and acoustic parameter generation
- **LilyPond** for notation and symbolic representation
- **Python** for algorithmic composition control
- **Music theory** grounded in monophonic structure analysis

## Recent Compositions

{% for comp in site.compositions | sort: 'date' | reverse | limit: 5 %}
- [{{ comp.title }}]({{ comp.url }}) — {{ comp.date | date: "%Y-%m-%d" }}
{% endfor %}

[View All →](./all.html)

## About

This project is part of the **オンガクトリシラベガカリ (OTSG)** research initiative, investigating the structural principles of Japanese monophonic music without presupposing Western music theory frameworks.

---

**Latest Update:** {{ site.time | date: "%Y-%m-%d" }}
