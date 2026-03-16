---
layout: ../../../layouts/DocsLayout.astro
title: BentoTUI Rooms
description: Geometry and layout composition layer in the frozen architecture contract.
publishedAt: 2026-03-15
---

# Rooms

`registry/rooms` owns geometry and spatial composition.

## Responsibility

- Allocate width, height, and split behavior.
- Coordinate panel adjacency and readable density.
- Keep layout policy consistent across bentos.

## Current Contract Additions

- `WithGutter` for explicit split spacing.
- `WithDivider` for explicit split separators.

## Contract

- Rooms allocate space; they do not paint final visual semantics.
- Room APIs should remain deterministic across viewport changes.
- Room composition should be scenario-friendly for app-shell validation.
