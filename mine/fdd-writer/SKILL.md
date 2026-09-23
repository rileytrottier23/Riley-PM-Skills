---
name: "fdd-writer"
description: "Write, draft, structure, revise, or fold content into a Functional Design Document (FDD) or Product Requirements Document (PRD), or any section of one. Trigger on \"write the FDD\", \"write the PRD\", \"draft an FDD section\", \"fold this into the FDD\", \"write the Develop section\", \"write the use cases\", \"create a Topic 101\". Governs house style: warm in the 101 sections, tight and declarative everywhere else. For a standalone business rule with no FDD/PRD in play, use deterministic-logic-spec instead."
---

# FDD Writer

**Domain context:** Workday Revenue Center & Contract Modifications. Adapt house-style rules for other domains.

This skill defines how to write Functional Design Documents (FDDs) for Revenue Center / Contract product work. It exists to keep every FDD in one consistent voice: accessible to a team new to the domain, but professional and reference-like where it counts.

**Applies to PRDs too.** When a PRD is referenced instead of an FDD, apply this same skill — the two registers, tense, formatting rules, and templates are identical. A PRD leans more on the problem, users, and requirements (the Discover/Define material) and less on detailed engine mechanics, but the house style does not change.

The core rule that governs everything: **teaching voice is quarantined to the 101 sections; every other section is tight, declarative, and reference-like.** The most common failure mode is letting the explanatory, conversational voice from the 101 sections bleed into the specification sections. Guard against that above all else.

## The two registers

An FDD contains two kinds of writing, and they must not mix within a section.

### Register A — Warm and explanatory (101 sections only)

Use this **only** in sections explicitly named as primers: `Topic 101` (a plain-language overview of the feature) and `Accounting 101` (or any similar `<Domain> 101` primer that teaches background concepts). These sections exist to bring a non-expert reader up to speed.

In Register A:
- Explain *why* something matters before or alongside *what* it is.
- Use analogies, concrete real-life examples, and defined terminology inline.
- Warmth is fine: "the tricky part is...", "think of it like...", a conversational aside.
- Define every domain term the first time it appears, in plain words.
- Aim for a reader who has never seen the domain before and should finish the section understanding it.

Register A earns its warmth because its job is comprehension, not specification. Do not apologize for it or clip it — a good 101 section is genuinely friendly.

### Register B — Tight, declarative, reference-like (everything else)

Use this for all specification content: Discover, Define, Develop, Deliver, use cases, acceptance criteria, key considerations, open questions, appendices, and any new sections that specify rather than teach.

In Register B:
- **Lead with the point.** State the claim, requirement, or behavior first. Cut throat-clearing ("The tricky part is what happens after..."). A developer scanning for "what do I build" should not have to read past a warm-up sentence.
- **Declarative, not conversational.** State behavior as fact or requirement. Remove softeners ("fairly", "pretty much", "kind of") unless they carry real meaning.
- **Distinguish known from unknown precisely.** Do not blanket everything in hedges. State expected behavior declaratively and mark genuine uncertainty explicitly and specifically: "Pending confirmation with a domain expert" or "Open — see Section 7", not a vague "probably" scattered everywhere. (Exception: if the user explicitly asks for a hedge marker like "(probably)" on a specific set of items, honor it — a single deliberate marker works precisely because the surrounding text isn't hedged.)
- **Tighten mechanically.** Prefer periods over em-dashes. Short sentences. Avoid nested parentheticals. The em-dash should not be doing structural work that a sentence boundary should do.
- **Control redundancy with cross-references.** State a concept authoritatively once, then cross-reference it ("see Section X"). Do not re-explain the same principle in five places; in a formal document that reads as padding.
- **Standardize section shape.** Reuse a consistent internal template within a section type (see below). Consistency makes the document read as authored, not assembled.
- **No meta-phrases.** Never preface a section with "let me draft this for you," "here's the section," or "I'll write up..." Start with the content itself.
- **No unsolicited summary or advice.** Don't recap a section after writing it unless asked. The judgment-call note (see Working process) is the only sanctioned add-on, and it's a note, not a second essay.
- **Specific and accurate over generic.** Every requirement, behavior, or claim should be concrete enough to build against — no vague placeholders standing in for a real answer when the source material has one.

## Tense

Write unbuilt functionality in the **future tense**: "we need to build X", "the engine will resolve Y", "we need to solve Z". Use present/past tense only for decisions genuinely already made ("Drivers live on the Treatment" as a settled design decision, "the admin selected the default"). Within a mixed section, future-tense the behavior that still needs building and present-tense the decisions that are locked.

## Formatting rules

These are the standard formatting preferences for this skill. Follow them unless told otherwise.

- **Bold and underline are reserved for titles and subtitles only** — never for inline emphasis on important points. If a point matters, sentence structure should carry the weight, not typography. The one tolerated exception is a short term-label that functions as a mini-title at the start of a list item (e.g., a glossary term, or a lead-in like "Effective date is sacred:"). When in doubt, don't bold.
- **Minimal formatting.** Prose over bullets for explanatory content. Use bullets, numbered lists, and tables only when the content is genuinely multifaceted (decision tables, acceptance criteria, status trackers, field mappings) or when asked.
- **Descriptive source citations, not comment-number references.** Cite "FINREV customer research, Apr 2025" or "[Case 4]", not "per comment 12".
- **No ownership columns** in decision-tracking or open-question lists. The PM owns all decisions; an owner column is noise.
- **Product naming.** Refer to "this product" or "the contract product" rather than "RC" — RC (Revenue Center) is too broad a container for the specific contract-modifications product. Use "Revenue Center" only for the platform/area, not the product being specced.

## Flowcharts and images

Visuals are welcome when they genuinely aid understanding — a flow the reader has to hold in their head (a user flow, an engine execution sequence, a decision tree, a Path 1 vs. Path 2 split, a stage/status lifecycle) is often clearer as a diagram than as prose. Use them when they earn their place, not for decoration.

Keep them relatively simple. A good FDD diagram shows the shape of a flow or a decision at a glance. It should not try to capture every branch, edge case, or field — those live in the prose and tables. Prefer a handful of boxes and arrows over a dense engineering schematic. If a diagram needs a legend to be understood, it is probably too complex for an FDD.

Practical guidance:
- Reach for a flowchart for sequences and decisions; a simple table for structured comparisons; a status tracker for lifecycle stages.
- Mermaid is a good default for flowcharts and decision trees because it stays legible and is easy to edit. ASCII/box sketches are fine for a quick review-screen or layout mockup.
- Always pair a diagram with a one-line caption stating what it shows, and make sure the prose still stands on its own — the diagram supports the text, it does not replace it.
- Match the register of the surrounding section: a Topic 101 diagram can be friendly and high-level; a Develop-section diagram should be spare and precise.

## Standard document structure

Default to this skeleton for an FDD. Add, merge, or renumber sections as the content requires — the structure serves the content, not the reverse. When a template is provided, follow the template's structure and apply these style rules to the prose inside it. For a PRD, the same skeleton applies but weight it toward Discover/Define (problem, users, requirements, epics) and lighten the detailed Develop-section mechanics.

1. **Topic 101** — Register A. Plain-language overview: what the feature is, why it exists, a real-life example, what's in and out of scope at the highest level.
2. **`<Domain>` 101** (e.g., Accounting 101) — Register A. Teaches the background concepts a developer needs (e.g., ASC 606 basics) without assuming domain expertise. Include a short glossary of terms and a one-paragraph summary for the busy reader.
3. **Discover** — Register B. Background/context, users and stakeholders, current state and pain points, research inputs, and (often) the use cases.
4. **Define** — Register B. Problem statement, goals and success criteria, in-scope, out-of-scope, and key decisions already resolved (so they aren't reopened).
5. **Develop** — Register B. The functional solution design: solution overview, each subsystem, user flows, integrations, and system touchpoints.
6. **Deliver** — Register B. Build sequence, acceptance criteria, lifecycle/audit, dependencies and risks, metrics.
7. **Key Considerations** — Register B. Business processes, security, conversions, integrations, localization, setup, reporting, accessibility.
8. **Unresolved Questions / Decisions Needed** — Register B. Grouped by topic. Mark resolved items as resolved so the list stays honest; keep genuinely open ones as questions.
9. **Appendix** — Register B. Source documents and related components.

## Section-specific templates

### Use cases

Use a consistent three-part template per case, in Register B (the business-situation portion may carry a touch more warmth since it describes a human scenario, but stay declarative):

- **Business situation:** Who is involved, what the customer wants, and why it comes up. Ground it in a concrete example with dates where the source material provides one.
- **Why it matters:** One or two sentences on business value or risk. Cut if obvious.
- **What needs to happen:** The system behavior — what updates, what schedules change, what is scoped to the effective date. (If asked for a hedge marker like "What (probably) needs to happen", apply it consistently across all cases.)

Carry source case numbers in brackets (e.g., "[Cases 3 & 5]"). Mark customer-research-only scenarios as such so their behavior is understood to be less precisely documented than numbered cases.

### Acceptance criteria

Group by epic or feature to match the build sequence. Write each criterion in Given/When/Then form:

`Given <precondition>, when <action>, then <expected result>.`

Cover the full surface, not just the happy path. A complete set includes admin configuration (including any config the reader might overlook, like accounting-treatment setup), the primary user flow, engine/runtime behavior, each downstream automation, review/confirmation mechanics, audit/reporting, and validation/blocking rules. Do **not** write acceptance criteria for genuinely unresolved behavior — that belongs in Open Questions. Writing an open question as a criterion falsely implies a decision was made.

### Decision tables, status trackers, field mappings

Use tables. Keep them tight — columns only for information the reader acts on. No ownership columns.

## Working process

- **When folding content into a full document,** reproduce the whole document with the new content integrated, and reconcile numbering end to end. Flag any collisions (duplicate section numbers, an emptied section slot) rather than silently leaving them.
- **When revising,** make the targeted change asked for. The work is iterative and precise — specific omissions or phrasing issues get identified and should be fixed, not answered with a full rewrite of surrounding material that wasn't mentioned.
- **Ground claims in the project sources.** Search available project knowledge (including Google Drive) for the PRD, use-case docs, customer research, and epic breakdowns before inventing behavior. Prefer compound queries (e.g., "driver resolution engine review screen") over single-concept ones. Cite descriptively.
- **Surface judgment calls at the end.** After a substantial section, briefly note where you made a defensible choice (e.g., which treatment a use case was mapped to) or where source material was thin, so it can be corrected. Keep this to a short note, not a second essay.
- **Output medium.** Write in the chat as Markdown-style prose by default. Only produce a .docx or PDF when explicitly asked.

## Quick self-check before returning a draft

- Is any teaching/analogy/warm-up voice present outside a 101 section? Remove it.
- Does every specification section lead with its point, or does it warm up first? Fix warm-ups.
- Is bold/underline used for inline emphasis anywhere? Remove it — titles/subtitles only.
- Are unbuilt features in future tense?
- Is any concept re-explained where a cross-reference would do?
- Are open questions kept out of the acceptance criteria?
- If I used a diagram, is it simple enough to read at a glance, captioned, and backed by prose that stands on its own?
- Did I say "RC" where I meant "this product"?

