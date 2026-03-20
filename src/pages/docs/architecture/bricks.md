---
layout: ../../../layouts/DocsLayout.astro
title: BentoTUI Bricks
description: Installable copy-and-own UI building blocks for BentoTUI v0.5.4.
publishedAt: 2026-03-20
---

# Bricks

Bricks are official UI building blocks copied into app code with `bento add <brick>`.

## Responsibility

- Render reusable terminal UI components.
- Accept `WithTheme(t)` and runtime `SetTheme(t)` updates.
- Remain copy-and-own so teams can adapt behavior safely.

## Installable bricks (`bento add`)

1. `surface` - full-terminal paint surface with UV cell buffer
2. `card` - content container (raised default or flat with `Flat()`)
3. `bar` - header/footer row with keybind cards
4. `dialog` - modal manager + confirm/custom/theme picker/command palette
5. `filepicker` - file and directory picker wrapper
6. `list` - scrollable list wrapper
7. `table` - data table wrapper
8. `text` - static text label
9. `input` - single-line text field
10. `badge` - inline status label
11. `kbd` - command/label shortcut pair
12. `wordmark` - themed heading block
13. `select` - single-choice picker
14. `checkbox` - boolean toggle
15. `progress` - horizontal progress bar
16. `package-manager` - sequential install flow with spinner + progress
17. `tabs` - tab row with keyboard input
18. `toast` - stacked notifications
19. `separator` - horizontal/vertical divider

## v0.5.4 behavior notes

- Command palette action ordering is deterministic.
- Dialog lifecycle handling now uses explicit `dialog.OpenMsg` and `dialog.CloseMsg` flow events.
- `app-shell` theme propagation updates footer, center deck, and dialog manager consistently.

## Contract

- Bricks paint UI; they do not decide app-level orchestration or room geometry.
- Bricks do not import other bricks (guardrail-enforced).
- Brick APIs keep backward-compatible defaults where possible.
