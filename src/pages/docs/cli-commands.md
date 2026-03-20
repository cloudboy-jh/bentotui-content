---
layout: ../../layouts/DocsLayout.astro
title: CLI Commands
description: Bento CLI command reference for BentoTUI v0.6.0.
publishedAt: 2026-03-20
---

# CLI Commands

Install the CLI:

```bash
go install github.com/cloudboy-jh/bentotui/cmd/bento@latest
```

## Command surface

- `bento` - launches the interactive template-init picker.
- `bento init <bento>` - initialize a named bento template.
- `bento add <brick...>` - copy brick source into `bricks/<name>/`.
- `bento add recipe <name...>` - copy recipe source into `recipes/<name>/`.
- `bento list` - print installable bentos, bricks, and recipes.
- `bento doctor` - check project health and optional copied bricks.
- `bento version` - print CLI version.

## Installable recipes

- `filter-bar`
- `empty-state-pane`
- `command-palette-flow`
- `vimstatus`

## Notes

- Use `bento list` as source of truth for installable bentos, bricks, and recipes.
- In docs and app messaging, keep Bento vocabulary consistent: bricks, recipes, rooms, bentos.
