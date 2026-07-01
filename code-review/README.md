# code-review

Repository: https://github.com/odinlayer/ai-skills/tree/main/code-review

License: MIT

`code-review` provides a structured review flow for PRs and diffs using
parallel review lanes and confidence scoring to reduce false positives.

## Files

- `SKILL.md` - Pi-compatible review workflow instructions.
- `README.md` - Human-facing documentation and source lineage.

## Adaptation Notes

- Adapted for Pi client usage, not tied to Anthropic slash commands.
- Retains the confidence-scoring pattern and high-signal output style.

## Source Lineage

- Upstream plugin: `code-review`
- Source: https://github.com/anthropics/claude-plugins-official/tree/main/plugins/code-review
