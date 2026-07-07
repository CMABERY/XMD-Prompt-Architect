# Sources, Dated Platform Limits & Open Unknowns (reference)

## Provenance

Methodology adapted from a ChatGPT "XMD" exploration (7/7/2026); every platform/vendor
fact was independently re-verified against official OpenAI sources on **2026-07-07** and
corrected where wrong.

## Official OpenAI sources (checked 2026-07-07)

- Creating/editing GPTs, limits, capabilities — help.openai.com/en/articles/8554397-creating-and-editing-gpts
- Writing instructions for Custom GPTs; Preview testing — help.openai.com/en/articles/9358033-key-guidelines-for-writing-instructions-for-custom-gpts
- Knowledge in GPTs — help.openai.com/en/articles/8843948-knowledge-in-gpts
- Prompt engineering (Markdown/XML, instruction hierarchy, context placement) — developers.openai.com/api/docs/guides/prompt-engineering
- Structured Outputs — developers.openai.com/api/docs/guides/structured-outputs
- Model Spec (untrusted-data fencing) — model-spec.openai.com/2025-12-18.html
- Agent safety / prompt injection — developers.openai.com/api/docs/guides/agent-builder-safety ; openai.com/index/prompt-injections/
- ChatGPT Custom Instructions (the separate 1,500-char feature) — help.openai.com/en/articles/8096356-chatgpt-custom-instructions

**Fetch caveat:** developers.openai.com and model-spec.openai.com were fetched directly;
help.openai.com pages returned HTTP 403 to direct fetch and were corroborated via
OpenAI-domain search snippets. The 20-file / 512 MB knowledge limits were separately
confirmed by the operator.

## Dated limits (re-verify before relying)

- Instructions field: **8,000 characters**.
- Knowledge: **20 files, 512 MB / file**.
- Conversation starters shown: **4**.
- **Correction of record:** "~1,500-char instruction limit" is WRONG for Custom GPTs —
  that's the separate personal *Custom Instructions* feature. Custom GPT Instructions =
  **8,000**.

## Open unknowns / unverified

- Name and Description character limits — not officially documented.
- Exact conversation-starter hard cap — not officially stated (builder shows 4).
- Per-file knowledge token cap (~2M tokens) — plausible, not verified this session.
- Custom-GPT-specific default model — inferred from the ChatGPT-wide default; the model
  surface churns.

## Refresh cadence

Re-verify field limits, capability names, and available models against current OpenAI
docs before any reliance — these change. **Never hard-code a model name.**
