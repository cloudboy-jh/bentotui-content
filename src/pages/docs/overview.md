---
layout: ../../layouts/DocsLayout.astro
title: Overview / Getting Started
description: BentoTUI overview and quick start for v0.5.4.
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
bento
bento init myapp
bento list
bento add card
bento add recipe vimstatus
go run ./registry/bentos/home-screen
```

## Current release snapshot

- Current docs/app snapshot target: `v0.5.4`
- `CHANGELOG.md` top release: `0.5.4` dated `2026-03-19`

## v0.5.4 highlights

- Command palette action ordering is deterministic.
- Dialog lifecycle handling (`dialog.OpenMsg` / `dialog.CloseMsg`) is explicit in bento update flows.
- `app-shell` theme propagation updates footer, center deck, and dialog manager consistently.

## Related

- [CLI Commands](./cli-commands)
- [Bricks API](./architecture/bricks)
- [Recipes API](./architecture/recipes)
- [Rooms API](./architecture/rooms)
- [Bentos Templates](./architecture/bentos)
