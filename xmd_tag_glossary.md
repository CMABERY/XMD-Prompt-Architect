XMD PROMPT ARCHITECT — Custom GPT build bundle
Generated 2026-07-07. Every piece is its own clean upload.

HOW TO ASSEMBLE THE GPT (OpenAI GPT builder -> Configure):

1. NAME            -> from Name-Description-Starters.txt
2. DESCRIPTION     -> from Name-Description-Starters.txt
3. INSTRUCTIONS    -> open 00-INSTRUCTIONS-field.txt, SELECT ALL, paste into the
                      Instructions box. The whole file IS the field content
                      (5,440 characters, under the 8,000 limit). Paste NOTHING
                      else into this box.
4. CONVERSATION STARTERS -> the 4 lines in Name-Description-Starters.txt, one per row.
5. KNOWLEDGE (Upload files) -> upload the 7 xmd_*.md files. Reference material only.
6. CAPABILITIES    -> enable only what you need (Web Search, Canvas, Image
                      Generation, Code Interpreter, Actions). Optional.
7. PREVIEW         -> run the tests in xmd_eval_suite.md BEFORE publishing.

FILES:
  00-INSTRUCTIONS-field.txt      -> the Instructions field (paste this, and ONLY this)
  Name-Description-Starters.txt  -> Name / Description / Starters fields
  xmd_doctrine.md                -> Knowledge: the full XMD doctrine
  xmd_tag_glossary.md            -> Knowledge: tag-by-tag reference
  xmd_examples_patterns.md       -> Knowledge: worked XMD prompts per task type
  xmd_customgpt_config_notes.md  -> Knowledge: Instructions/Knowledge split + limits
  xmd_security_notes.md          -> Knowledge: untrusted-content / injection rules
  xmd_eval_suite.md              -> Knowledge + the Preview tests
  xmd_sources_limits.md          -> Knowledge: sources, dated limits, open unknowns

GOLDEN RULE: Instructions = behavior. Knowledge = reference. Do NOT paste reference
material into the Instructions box — pasting a whole doctrine there is what caused the
earlier "over the 8,000 limit" error. Name / Description / Starters each go in their
own fields.

Platform facts here were verified 2026-07-07 and are dated because they change.
Re-verify field limits, capabilities, and models against current OpenAI docs.
