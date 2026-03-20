---
layout: ../../layouts/DocsLayout.astro
title: Overview / Getting Started
description: BentoTUI overview and quick start for v0.6.0.
publishedAt: 2026-03-20
---

# Overview / Getting Started

BentoTUI is the fastest way to build full Go TUIs using copy-and-own bricks and recipes, import-only room layouts, and runnable bento templates.

## Product framing

- **Bricks**: official UI building blocks copied into app code with `bento add <brick>`.
- **Recipes**: copy-and-own composed flow patterns copied with `bento add recipe <name>`.
- **Rooms**: stable import-only page layout contracts from `registry/rooms`.
- **Bentos**: runnable template apps in `registry/bentos/*` for rapid remix.

## Install

```bash
go get github.com/cloudboy-jh/bentotui
go install github.com/cloudboy-jh/bentotui/cmd/bento@latest
```

## First run path

```bash
bento init app-shell
bento
bento list
bento add card
bento add recipe vimstatus
go run ./registry/bentos/home-screen
```

## Current release snapshot

- Current docs/app snapshot target: `v0.6.0`
- `CHANGELOG.md` top release: `0.6.0` dated `2026-03-20`

## v0.6.0 highlights

- `bento init` now requires an explicit named template: `bento init <bento>`.
- The old starter scaffold path (`bento init [name]`) is removed in favor of template-first initialization.
- `bento list` now includes bentos alongside bricks and recipes.
- The interactive `bento` flow uses a template-init picker.
- `dashboard-brick-lab` now handles `theme.ThemeChangedMsg` and propagates updates through composed bricks.

## Related

- [CLI Commands](./cli-commands)
- [Bricks API](./architecture/bricks)
- [Recipes API](./architecture/recipes)
- [Rooms API](./architecture/rooms)
- [Bentos Templates](./architecture/bentos)
