---
name: youtube-transcript
description: Download YouTube transcripts/captions from a video URL, prefer manual subtitles first, fallback to auto subtitles, and optionally convert VTT output into clean deduplicated plain text.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/youtube-transcript
  compatibility: Pi skill format; requires shell access and yt-dlp.
---

# YouTube Transcript

Use this skill when the user wants transcript/captions/subtitles from a YouTube video.

## Inputs

- YouTube URL
- Preferred output type (`.vtt` or cleaned `.txt`)
- Optional language preference

## Workflow

1. Verify tooling:
   - check `yt-dlp` availability first.
2. Check subtitle availability:
   - run `yt-dlp --list-subs <URL>`.
3. Download in this order:
   - manual subtitles (`--write-sub --skip-download`)
   - auto subtitles (`--write-auto-sub --skip-download`)
4. Confirm output file path and language code.
5. Optional normalization:
   - convert `.vtt` to plain text.
   - remove duplicate progressive-caption lines while preserving speaking order.

## Fallback

If no subtitles exist:

- ask user before doing audio download/transcription.
- if approved, use Whisper workflow as last resort.
- state expected size/time tradeoff before starting.

## Guardrails

- Do not download full video unless needed.
- Do not run Whisper fallback without explicit user confirmation.
- Preserve original `.vtt` unless user asks to replace/cleanup.
