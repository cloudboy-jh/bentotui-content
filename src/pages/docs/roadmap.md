---
layout: ../../layouts/DocsLayout.astro
title: Product Direction and Roadmap
description: Outcome-focused direction after BentoTUI v0.6.0.
publishedAt: 2026-03-20
---

# Product Direction and Roadmap

BentoTUI focuses on helping Go teams ship full terminal apps quickly with clear ownership.

## Positioning

- Not a framework shell users must conform to.
- Not a low-level Bubble Tea/Bubbles internals tutorial.
- A fast path to shipping full Go TUIs with ownership.

## Near-term focus

- Keep templates and docs synchronized with current release behavior (`v0.6.0`).
- Expand practical examples that start from bentos, then adapt bricks and recipes.
- Keep room contracts stable and import-only.
- Strengthen rendering consistency through surface + styles guidance.

## Reliability priorities

- Maintain deterministic command palette and dialog lifecycle behavior in `app-shell`.
- Keep theme propagation consistent across footer, center deck, and dialog manager.
- Continue guardrail enforcement for room/brick/theme boundaries.

## Documentation priorities

- Keep install catalogs current (`bento list` as source of truth).
- Keep CLI docs aligned with template-first initialization (`bento init <bento>`).
- Ensure recipes docs include `vimstatus` anywhere installable recipes are listed.
- Keep the theme interface docs updated with diff/syntax token surface.

## Success criteria

- New teams can ship a serious app shell in one day.
- Docs match released behavior and command surface.
- Regressions are caught with deterministic validation scenarios.

## Related

- [Overview / Getting Started](./overview)
- [Theme Engine](./theme-engine)
- [CLI Commands](./cli-commands)
