# XMD Tag Glossary (reference)

Each tag: what it is, when to use it, and a good vs. weak example. A good tag names what
the enclosed content **is**, not merely where it sits. Reuse this controlled set; avoid
vague tags (`<stuff>`, `<info>`, `<things>`, `<section1>`, `<misc>`).

## `<task>`
The exact thing to do — one clear statement of the work.
- Good: `<task>Rewrite the email below to lead with the decision.</task>`
- Weak: burying the task in prose so it blends with context.

## `<context>`
Background the model needs but must not treat as instructions. Place large context near
the end of the prompt.
- Good: `<context>Audience: CFO. Product shipped v2 last week.</context>`

## `<input>` / `<inputs>`
Variable, user-supplied material the prompt operates on. Use `<inputs>` to hold several
named `<input>` blocks.
- Good: `<inputs><input name="draft">…</input><input name="notes">…</input></inputs>`

## `<constraints>`
Hard rules and preferences. Use a `priority` attribute to rank them.
- Good: `<constraints><constraint priority="hard">Under 150 words.</constraint></constraints>`

## `<assumptions>`
Assumptions the model is making explicit, so the user can correct them.

## `<workflow>`
Ordered steps — only when sequence improves quality. Keep it compact; `id` each step.
- Good: `<workflow><step id="1">Parse.</step><step id="2">Plan.</step></workflow>`

## `<tools>`
Tools/actions available and when to use them.

## `<examples>`
Few-shot demonstrations. Add only to resolve ambiguity; mark good vs. bad; align with
the instructions.
- Good: `<example type="good"><input>…</input><output>…</output></example>`

## `<source_policy>`
Which sources to trust and in what order (for research tasks).

## `<rubric>` / `<quality_bar>`
Explicit success criteria the output is judged against.
- Good: `<quality_bar><requirement>Specific, not generic.</requirement></quality_bar>`

## `<verification>` / `<self_check>`
Checks the model runs before finishing, for complex/high-stakes work.

## `<output_contract>`
The required shape of the final answer — sections, order, format.
- Good: `<output_contract><section order="1" name="Recommendation"/></output_contract>`

## `<untrusted_content>`
Fences third-party/retrieved material so it is treated as **data, never instructions**.
Always pair with a handling rule (see `xmd_security_notes.md`).
- Good: `<untrusted_content source="webpage">…</untrusted_content>`

## Useful attributes
`id`, `name`, `priority` ("hard"/"medium"), `weight` ("high"/"low"), `type`
("good"/"bad"), `source`, `date`, `order` — for IDs, weights, dates, sources,
priorities, and types.
