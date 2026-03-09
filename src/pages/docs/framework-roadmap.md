---
layout: ../../layouts/DocsLayout.astro
title: BentoTUI 1.0 Scope Finalized
description: Final component catalog locked; roadmap now bento-first.
publishedAt: 2026-03-09
tags:
  - bentotui
  - bubbletea
  - golang
  - tui
  - cli
---

# BentoTUI 1.0 Scope Finalized

## Positioning

BentoTUI is a copy-and-own terminal UI registry for Bubble Tea v2.

- No framework shell
- No lifecycle lock-in
- Add source with `bento add <component>`
- Compose full screens with reusable bento patterns

Core principle for 1.0: **do not reinvent established primitives**. Bento ships composition-focused components and leans on Bubbles directly for low-level primitives (for example `spinner`).

---

## 1.0 Status Snapshot

- Registry architecture is in place
- CLI commands shipped: `bento init`, `bento add`, `bento list`, `bento doctor`
- Theme/layout core packages are stable imports: `theme`, `styles`, `layout`
- Component catalog is finalized for 1.0 scope
- Next execution focus is bento example breadth

---

## Final Component List (1.0)

### Core layout/container

- `surface`
- `panel`
- `bar`
- `dialog`

---

### Display helpers

- `badge`
- `kbd`
- `wordmark`

---

### Form/feedback

- `select`
- `checkbox`
- `progress`

---

### Advanced composition helpers

- `tabs`
- `toast`
- `separator`

---

### Compatibility components (already shipped)

- `input`
- `list`
- `table`
- `text`

---

## Primitive Policy

For 1.0, Bento does **not** add extra wrapper components for primitives that are already strong in Bubbles.

- Use `charm.land/bubbles/v2/spinner` directly
- Prefer direct Bubbles primitives unless Bento-specific composition value is clear

---

## Final Bento List (1.0)

### Foundation wave

- `home-screen`
- `app-shell`
- `dashboard`
- `settings`

---

### Workflow wave

- `form`
- `detail-view`
- `log-viewer`
- `command-view`
- `table-browser`
- `file-browser`

---

### Advanced wave

- `release-monitor`
- `incident-console`
- `chat-console`
- `kanban-board`
- `onboarding-wizard`
- `admin-control-center`

---

## Recommended Site Copy (Short)

"BentoTUI 1.0 finalizes a composition-first component catalog and shifts fully into shipping runnable bento screen patterns. You copy source, own source, and build production TUIs without framework lock-in."

---

## Recommended Site Copy (Long)

"BentoTUI is a copy-and-own registry for Bubble Tea v2. Instead of forcing a framework shell, Bento gives you production-ready components and full-screen bento patterns that land directly in your codebase. The 1.0 scope is now locked: a composition-focused component catalog (`surface`, `panel`, `bar`, `dialog`, `badge`, `kbd`, `wordmark`, `select`, `checkbox`, `progress`, `tabs`, `toast`, `separator`) plus compatibility components already in use (`input`, `list`, `table`, `text`). Primitive wrappers are intentionally limited; for example, loading states use `bubbles/spinner` directly. The roadmap now prioritizes broad bento coverage so teams can start from proven screen templates and adapt quickly."

---

## Related

- [Architecture](./architecture) — Component registry architecture and policy details
