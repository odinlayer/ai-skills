# code-modernization

Repository: https://github.com/odinlayer/ai-skills/tree/main/code-modernization

License: MIT

`code-modernization` is a structured modernization workflow for legacy systems.
It covers preflight, assessment, architecture mapping, business-rule extraction,
planning, execution path selection (`transform`, `reimagine`, `uplift`), and
validation via behavior-equivalence tests.

## Files

- `SKILL.md` - Pi-compatible skill instructions.
- `README.md` - Human-facing usage notes and source lineage.

## Adaptation Notes

- Adapted for Pi client usage (model-agnostic, no Anthropic-only hooks).
- Focuses on reusable workflow steps instead of slash-command internals.

## Source Lineage

- Upstream plugin: `code-modernization`
- Source: https://github.com/anthropics/claude-plugins-official/tree/main/plugins/code-modernization
