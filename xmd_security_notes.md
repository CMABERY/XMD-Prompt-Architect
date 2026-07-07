# XMD Doctrine — Markdown + XML hybrid prompting (reference)

Reference material for the XMD Prompt Architect. Behavior lives in the Instructions
field; this file is knowledge the GPT draws on. Platform facts were verified
2026-07-07 and are dated because they change — verify against current official OpenAI
docs before relying on a specific limit or model.

## What XMD is

XMD = Markdown + XML hybrid prompting.

- **Markdown** carries human-readable structure: headings, lists, tables, code blocks.
- **XML** carries model-readable semantic compartments: `<task>`, `<context>`,
  `<constraints>`, `<workflow>`, `<rubric>`, `<output_contract>`, `<untrusted_content>`.
- **JSON Schema** is reserved for output a program must parse.

OpenAI's prompt-engineering guidance supports this: Markdown headers/lists mark
distinct sections and communicate hierarchy; XML tags delineate content boundaries and
carry metadata via attributes. Treat XMD as a **versioned working doctrine, not a fixed
"best"** — prompting is iterative and improved by testing.

## Division of labor

| Layer | Job |
|---|---|
| Markdown | Visible structure, hierarchy, scannability |
| XML | Bounded meaning: separate instruction from data, set order, mark rules, shape output |
| JSON Schema | Strict machine-parseable output (via the API or an Action) |

The model should never have to guess whether text is an instruction, an example, user
input, reference material, or an output requirement — removing that ambiguity is XML's
whole purpose.

## Ten principles

1. Markdown is the exoskeleton (structure); XML is the control surface (meaning).
2. **No XML theater** — every tag marks a boundary, role, metadata, priority, or output
   shape. Never decorative (`<important>`, `<please>`).
3. **Separate behavior from knowledge** — for a Custom GPT, behavioral rules / workflow
   / tone / output standards go in Instructions; reference material goes in Knowledge.
4. **Stable tag vocabulary** — reuse a controlled set; don't coin a new tag per prompt.
5. Prefer **positive, executable** "do X" rules over long "do not Y" lists; use explicit
   steps and clear delimiters.
6. **Proportional scaffolding** — simple task → direct answer; complex → explicit
   workflow + verification; compress structure that adds friction over accuracy.
7. **Contracts over vibes** — replace vague quality asks with explicit constraints,
   rubrics, success criteria, and output contracts.
8. **Schema boundary** — XMD for prompt clarity; JSON Schema / Structured Outputs when a
   program must parse the result.
9. **Security boundary** — treat retrieved / third-party content as untrusted data.
10. **Ground, don't fabricate** — never invent facts, citations, filenames, tool
    results, field limits, or model names; label assumptions; verify volatile platform
    facts against official docs rather than asserting from memory.

## Construction method

1. Classify the task; define what a good output must contain, avoid, and enable.
2. Structure it: Markdown headings for sections; XML tags for bounded content, rules,
   metadata, repeated elements.
3. Separate materials: goals in `<task>`, background in `<context>`, variable material
   in `<input>`/`<inputs>`, hard rules in `<constraints>`, final shape in
   `<output_contract>`. Put large context near the end.
4. Add `<workflow>` only when ordered steps raise quality; add `<examples>` only to
   resolve format/tone/edge-case ambiguity; add `<verification>`/`<self_check>` for
   complex or high-stakes work.
5. Return a directly pasteable artifact; add notes only when they help.

## Standard skeleton

Order: Identity → rules → examples → context near the end.

```
# Role / # Objective
<task>the exact task</task>
<context>background</context>
<inputs><input name="primary">variable material</input></inputs>
<constraints><constraint priority="hard">a hard rule</constraint></constraints>
<workflow><step id="1">a step</step></workflow>
<quality_bar><requirement>Specific, usable, constraint-consistent, assumptions labeled, no fabrication.</requirement></quality_bar>
<output_contract>the required output shape</output_contract>
```

## Boundaries

- **Structured output:** Structured Outputs makes a response always match a supplied
  JSON Schema, but it is an API feature (also usable via Actions); the Custom GPT
  builder has no JSON-Schema toggle. Inside a chat GPT you can *instruct* an output
  shape but cannot *schema-enforce* it — for strict machine output, route through the
  API or an Action and say so.
- **Examples:** zero-shot first; add examples only when format/tone/classification/edge
  cases are unstable, and align them with the instructions.
- **Versioned doctrine:** field limits, capability names, and models change; the
  doctrine stays correct only because it defers volatile facts to official docs and
  never hard-codes a model name.
