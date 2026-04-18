# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Interactive web application for a university-level Data Mining course (Computer Science track). Each module contains visual, hands-on demos showing how data mining algorithms work on real problems (recommender systems, fraud detection, social network analysis, image classification).

Deployed as a static site via **GitHub Pages** (Jekyll). No backend. All computation runs client-side in the browser.

## Tech Stack

- **Jekyll** — static site generator (GitHub Pages compatible)
- **D3.js** — 2D charts, scatter plots, dendrograms, decision trees
- **Math.js** — numeric computation (PCA, distance metrics, matrix ops)
- **Vanilla JS / Canvas 2D** — lightweight interactive demos

## Module Structure

Each module lives in its own directory with self-contained HTML pages:

```
/modulo-01/   — Introducción y Tipos de Datos
/modulo-02/   — Exploración y Visualización
/modulo-03/   — Preprocesamiento y Limpieza
/modulo-04/   — Clasificación: KNN y Métodos por Instancias
/modulo-05/   — Clasificación: Árboles de Decisión y Ensambles
/modulo-06/   — Clustering (K-Means, DBSCAN, Jerárquico)
/modulo-07/   — Reglas de Asociación (Apriori, FP-Growth)
/modulo-08/   — Reducción de Dimensionalidad (PCA, t-SNE)
/modulo-09/   — Minería de Texto (TF-IDF, Word2Vec)
/modulo-10/   — Evaluación de Modelos (ROC, Cross-validation)
_layouts/
_includes/
assets/
  css/main.css
  js/
```

Each demo page is independently usable (no shared state between modules). Shared utilities go in `assets/js/`.

## Development

```bash
bundle install          # first time only
bundle exec jekyll serve --livereload
# Site runs at http://localhost:4000
```

To add a new demo page, create an HTML file with Jekyll front matter:

```yaml
---
layout: default
title: "Título del Demo"
prev_url: /modulo-04/demo-anterior.html
prev_title: Demo Anterior
next_url: /modulo-04/demo-siguiente.html
next_title: Demo Siguiente
---
```

Then include the navigation component at the top of the content:

```liquid
{% include demo-nav.html %}
```

## Design Principles

- All computation is local — no server calls from any demo page.
- Demos must be parametric: sliders, drag handles, and inputs that let students manipulate values and see results instantly.
- Desktop-first; mobile-friendly is a nice-to-have.
- Spanish is the primary language for all UI text.
- Design system lives in `assets/css/main.css` — use CSS custom properties (`--accent`, `--surface`, etc.) instead of hardcoded colors.
