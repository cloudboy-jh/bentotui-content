---
layout: ../../layouts/DocsLayout.astro
title: BentoTUI Roadmap After Architecture Freeze
description: Direction after locking the architecture contract.
publishedAt: 2026-03-15
---

# Roadmap

Architecture is now frozen around bentos, rooms, and bricks.

## Definition

This roadmap is execution-focused. The model itself is not being redesigned.

- We improve quality, validation, and documentation depth.
- We do not introduce new architecture categories.
- We prioritize deterministic behavior over novelty.

## Priority Areas

- Expand app-shell validation scenarios and coverage depth.
- Continue hardening ANSI and stress rendering contracts.
- Grow architecture docs with concrete composition examples.
- Improve developer confidence via deterministic snapshot tuples.

## Delivery Phases

### Phase 1: Validation hardening

- Increase scenario breadth in `app-shell` across layout, hierarchy, footer, list, overlay, and stress.
- Require reproducible snapshots for each scenario profile.

### Phase 2: Layer contract depth

- Publish stronger guidance for bentos orchestration boundaries.
- Expand room split examples including `WithGutter` and `WithDivider`.
- Document brick compatibility behavior for typed rows and ANSI-heavy rendering.

### Phase 3: Team adoption

- Improve onboarding flow so teams start from bento scenarios instead of ad-hoc screens.
- Keep docs and examples synchronized with the frozen model.

## Validation Tuple

Every regression should be reproducible through:

`scenario + viewport + theme + focus + snapshot`

## Success Criteria

- App-shell scenarios catch layout regressions before release.
- Theme changes do not require per-screen overrides.
- New teams can onboard using docs without architecture re-interpretation.

## Direction

The roadmap now emphasizes quality and repeatability over introducing new architecture categories.

## Related

- [Untouchable Theme Engine](./theme-engine)
- [Next Steps](./next-steps)
