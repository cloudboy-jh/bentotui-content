---
layout: ../../../layouts/DocsLayout.astro
title: BentoTUI Recipes
description: Installable copy-and-own composed flow patterns for BentoTUI v0.6.0.
publishedAt: 2026-03-20
---

# Recipes

Recipes are copy-and-own composed flow patterns copied with `bento add recipe <name>`.

## Responsibility

- Compose multiple bricks into reusable workflow slices.
- Speed up common app interactions without locking teams into a framework shell.
- Stay straightforward to copy, inspect, and adapt.

## Installable recipes (`bento add recipe`)

1. `filter-bar` - input + status + keybind strip composition
2. `empty-state-pane` - reusable empty-result card content
3. `command-palette-flow` - open palette and route actions
4. `vimstatus` - vim-style statusline with mode/context/clock

## Contract

- Recipes are copy-and-own and can be freely modified by app teams.
- Recipes should compose bricks and rooms rather than introducing parallel architecture.
- Recipes avoid raw `bubbles/*` imports (spinner exception, guardrail-enforced).
