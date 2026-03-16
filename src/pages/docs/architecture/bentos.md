---
layout: ../../../layouts/DocsLayout.astro
title: BentoTUI Bentos
description: Full-app orchestration layer in the frozen architecture contract.
publishedAt: 2026-03-15
---

# Bentos

`registry/bentos` defines complete app experiences, not one-off widgets.

## Responsibility

- Orchestrate room composition and focus flow.
- Bind user journey scenarios to deterministic snapshots.
- Provide framework-level proving environments.

## Validation Standard

`registry/bentos/app-shell` is the canonical validation bento and must support:

- layout scenarios
- hierarchy scenarios
- footer behavior scenarios
- list row compatibility scenarios
- overlay sequencing scenarios
- stress and ANSI-heavy rendering scenarios

## Contract

- Bentos consume rooms and bricks; they do not duplicate those responsibilities.
- Bentos should expose predictable scenario states for regression checks.
- Bentos must remain composable so teams can copy, own, and adapt quickly.
