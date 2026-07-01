# youtube-transcript

Repository: https://github.com/odinlayer/ai-skills/tree/main/youtube-transcript

License: MIT

`youtube-transcript` downloads YouTube captions/transcripts with a practical
fallback flow: manual subtitles first, auto subtitles second, optional plain
text cleanup with deduplication, and Whisper transcription only as last resort
with explicit user confirmation.

## Files

- `SKILL.md` - Pi-compatible transcript workflow instructions.
- `README.md` - Human-facing notes and source lineage.

## Features

- Manual-caption first workflow with fallback to auto captions.
- Optional transcript cleanup and deduplication guidance.
- Explicit user-confirmed fallback path for Whisper-style transcription.

## Source Lineage

- Upstream repository: https://github.com/michalparkola/tapestry-skills
- Upstream skill path: `youtube-transcript/`
