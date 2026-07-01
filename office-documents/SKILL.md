---
name: office-documents
description: Unified workflow for creating, reading, editing, converting, and validating Office-style documents across DOCX, PDF, PPTX, and XLSX files. Use when the task involves one or more of these file types as input or output.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/office-documents
  compatibility: Pi skill format; works in local shell environments with document tooling installed.
---

# Office Documents

Use this skill whenever the primary task involves document work in any of these formats:

- `.docx`
- `.pdf`
- `.pptx`
- `.xlsx` (and related spreadsheet inputs like `.csv`/`.tsv` when output is spreadsheet-focused)

## Routing by File Type

- `DOCX`:
  - professional document authoring, editing, structure cleanup, tracked-change aware extraction
- `PDF`:
  - text/table extraction, split/merge/rotate/watermark, form filling, OCR workflows
- `PPTX`:
  - slide deck creation/editing, content replacement, visual QA and export workflows
- `XLSX`:
  - spreadsheet modeling/editing, formulas, formatting, data cleanup and transformation

## Core Workflow

1. Confirm scope:
   - source file(s), desired output file(s), and required fidelity (layout vs data-only).
2. Choose document-native tooling:
   - DOCX: docx-focused tooling and XML-safe editing methods.
   - PDF: pypdf/pdfplumber/reportlab + OCR path when needed.
   - PPTX: pptx tooling with design + visual validation pass.
   - XLSX: openpyxl/pandas with formula-safe workflows.
3. Apply edits with format integrity:
   - preserve template/style conventions when editing existing files.
4. Validate before delivery:
   - file opens successfully.
   - no corrupted structure or broken references.
   - no unresolved placeholders.
   - spreadsheet outputs contain zero formula errors.
5. Deliver with clear artifact list:
   - output paths, major transformations, and any known limitations.

## Quality Gates

- DOCX:
  - heading hierarchy and formatting remain consistent.
  - avoid accidental style drift from template.
- PDF:
  - extracted content is checked for completeness.
  - OCR use is explicitly noted when source is scanned/image-based.
- PPTX:
  - no text overflow/overlap.
  - slide visuals are reviewed via rendered images when layout changed.
- XLSX:
  - formulas are used instead of hardcoded computed values.
  - no `#REF!`, `#DIV/0!`, `#VALUE!`, `#N/A`, `#NAME?` in final output.

## Guardrails

- Do not silently convert deliverable type unless requested.
- Do not drop content for convenience during conversion.
- Flag ambiguous requirements (especially layout-preservation vs data-extraction) before deep edits.
