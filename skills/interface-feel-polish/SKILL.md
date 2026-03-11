---
name: interface-feel-polish
description: Improve the small UI details that make interfaces feel more polished, readable, and responsive. Use when Claude is asked to refine a frontend, review a component or design system, improve hover/focus/loading states, tune motion, clean up typography or spacing, or make an existing interface feel better without redesigning it from scratch.
---

# Interface Feel Polish

## Overview

Use this skill after the core UX already works and the remaining gap is feel, clarity, or polish. Focus on small, high-leverage fixes that compound: typography, geometry, motion, state changes, surfaces, and media treatment.

Read [references/interface-details.md](references/interface-details.md) for the concrete heuristics. Do not load the whole file unless the task is broad; read only the sections that match the current UI problem.

## Workflow

1. Determine the task type:
   Audit request: inspect the interface and return the highest-impact polish fixes first.
   Implementation request: apply the smallest code changes that materially improve feel.

2. Inspect the UI in this order:
   Text behavior and numeric stability.
   Geometry and alignment.
   Motion and state transitions.
   Surfaces, borders, shadows, and media treatment.

3. Apply the least invasive fix first:
   Prefer CSS or token-level changes before restructuring components.
   Preserve the existing design system unless the task explicitly asks for a broader visual shift.
   Avoid adding decorative motion or styling that is not tied to usability or perceived quality.

4. Verify the result:
   Check the normal, hover, focus, active, loading, empty, and disabled states that were touched.
   If the task involves motion, make sure repeated interactions still feel responsive and interruptible.
   If the task involves layout or typography, verify both desktop and mobile breakpoints.

## Heuristics

- Treat polish as a systems problem, not a bag of tricks. Small improvements should reinforce the product's existing visual language.
- Favor optical correctness over purely mathematical correctness when the two conflict.
- Prefer perceived-performance improvements that make interactions feel immediate over flashy animation.
- When several issues are present, fix the ones users will feel repeatedly: text wrapping, icon alignment, interruptibility, hover feedback, and surface depth.

## Output

For audits, report findings in priority order and include the concrete UI element, why it feels off, and the smallest fix that would improve it.

For implementations, mention which heuristics from `references/interface-details.md` were applied and what still needs visual verification.

## Resource Map

- [references/interface-details.md](references/interface-details.md): concrete checklist, defaults, and examples derived from the source article.
