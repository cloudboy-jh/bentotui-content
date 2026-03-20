---
layout: ../../layouts/DocsLayout.astro
title: CLI Commands
description: Bento CLI command reference for BentoTUI v0.5.4.
publishedAt: 2026-03-20
---

# CLI Commands

Install the CLI:

```bash
go install github.com/cloudboy-jh/bentotui/cmd/bento@latest
```

## Command surface

- `bento` - launches interactive TUI installer/launcher.
- `bento init [name]` - scaffold a starter app.
- `bento add <brick...>` - copy brick source into `bricks/<name>/`.
- `bento add recipe <name...>` - copy recipe source into `recipes/<name>/`.
- `bento list` - print installable bricks and recipes.
- `bento doctor` - check project health and optional copied bricks.
- `bento version` - print CLI version.

## Installable recipes

- `filter-bar`
- `empty-state-pane`
- `command-palette-flow`
- `vimstatus`

## Notes

- Use `bento list` as source of truth for installable bricks and recipes.
- In docs and app messaging, keep Bento vocabulary consistent: bricks, recipes, rooms, bentos.
