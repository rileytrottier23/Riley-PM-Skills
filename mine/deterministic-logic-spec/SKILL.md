---
name: "deterministic-logic-spec"
description: "Turn a business rule into an engineering-ready spec with a decision table and Given/When/Then acceptance criteria. Trigger on \"spec this rule\", \"define acceptance criteria\", \"decision table for X\", \"edge cases for this rule\". For acceptance criteria going into an FDD or PRD section, use fdd-writer instead — this is for a standalone rule with no document in play."
---

# Deterministic Logic Spec Writer

**Domain context:** Workday Revenue Center & Contract Domain. Adapt for other business logic.

Turn a rule into unambiguous logic — every branch explicit, no silent fallback.

## Scope boundary

This skill produces a **standalone rule spec**. If there is an FDD or PRD in play and the acceptance criteria are going into a section of it, use `fdd-writer` instead — that skill governs house style for document prose. Use context to decide: is there a document this feeds, or just a rule?

## Steps

1. **Extract the frame.** Inputs, outputs, happy-path logic, and the downstream consumer of the result.
2. **Probe edge cases.** Boundaries, nulls, conflicts, overrides, re-runs, and explicitly out-of-scope conditions. Ask about any the source material leaves silent rather than inventing a behavior.
3. **Produce the spec:**
   - **Inputs table** — name, type, source, required/optional, default
   - **Outputs table** — name, type, consumer
   - **Decision table** — one row per branch. Always include an explicit "no match" row. A rule with an implicit fallback is not specified.
   - **Acceptance criteria** in Given/When/Then form, covering at minimum: happy path, boundary condition, missing input, and conflict/override
   - **Non-goals** — what this rule must NOT decide
   - **Audit** — what gets logged when the rule fires
4. **Offer to go further.** Stress-test the spec against a concrete scenario, or draft QA test cases from the acceptance criteria.

## Non-negotiables

The decision table and the Given/When/Then criteria are mandatory. Prose alone is not a spec — if a developer has to infer a branch from a paragraph, the rule is underspecified.

Do not write acceptance criteria for behavior that is genuinely unresolved. List it as an open question instead; writing it as a criterion falsely implies a decision was made.

