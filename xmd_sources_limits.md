# Custom GPT Configuration Notes (reference)

How to build a Custom GPT with XMD. Verified 2026-07-07 — dated because it changes.

## Instructions vs. Knowledge (the golden rule)

- **Instructions field = BEHAVIOR:** identity, routing/triggers, workflow, rules, tone,
  security, output behavior, self-check. A compact runtime kernel.
- **Knowledge files = REFERENCE:** doctrine, glossary, examples, security rationale,
  eval suite, platform limits.
- Behavior never goes in Knowledge; reference never goes in Instructions.
- OpenAI's own guidance: knowledge files "give it source material," *unlike*
  instructions, which "define how your GPT should behave."

## Verified platform envelope (2026-07-07; verify before relying)

| Field / limit | Value |
|---|---|
| Instructions field | **8,000 characters** (hard). Keep a compact kernel with headroom. |
| Knowledge | **20 files, 512 MB per file.** Use slots deliberately; unused = reserved, not unavailable. |
| Conversation starters | builder displays **4**; exact hard cap not officially stated. |
| Name / Description limits | not officially documented. |
| Capabilities | Web Search, Canvas, Image Generation, Code Interpreter & Data Analysis, Actions (call APIs via OpenAPI/JSON). Optional tools, not doctrine. |
| MCP | Custom GPTs integrate via **Actions**, not native MCP. MCP-based "Apps" are a separate ChatGPT track. |
| Model | builder has a model picker + a "recommended model" setting; the default frontier model churns. **Never hard-code a model name.** |
| Structured Outputs | an **API/Actions** feature, NOT a builder toggle. A chat GPT can instruct an output shape but cannot schema-enforce it. |

Note: **"1,500 characters" is the SEPARATE personal ChatGPT Custom Instructions
feature, NOT the Custom GPT Instructions field** (which is 8,000).

## Paste discipline (this caused a real error)

Paste **only** the Instructions kernel into the Instructions box — nothing before or
after it. Pasting a whole doctrine/article (name, description, tables, notes) into
Instructions blows past 8,000 and the builder rejects it. Name, Description, and
Conversation Starters each go in their **own** fields; everything else is a **Knowledge
upload**.

## Build order

1. Name → 2. Description → 3. Instructions (kernel only) → 4. Conversation Starters →
5. Knowledge (upload the reference files) → 6. Capabilities (as needed) →
7. Preview-test with the eval suite → 8. Publish.
