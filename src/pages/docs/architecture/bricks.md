---
layout: ../../../layouts/DocsLayout.astro
title: BentoTUI Bricks
description: Reusable UI component layer in the frozen architecture contract.
publishedAt: 2026-03-15
---

# Bricks

`registry/bricks` is the UI component layer.

## Responsibility

- Render reusable visual and interaction components.
- Apply theme-driven semantics through stable style contracts.
- Preserve compatibility while enabling typed model upgrades.

## Current Contract Additions

- Anchored footer card style modes: `plain`, `chip`, `mixed`.
- Structured list rows expanded with typed fields and compatibility behavior.
- Panel render contract hardened for ANSI-heavy content.

## Contract

- Bricks paint; they do not decide app-level orchestration or room geometry.
- Brick rendering must remain stable across theme changes.
- Brick APIs should preserve backward-compatible defaults.
