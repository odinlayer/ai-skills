---
name: update-docs
description: Update existing documentation from local code changes and generate technical documentation (Markdown or HTML) with API references, workflows, and architecture diagrams when needed.
license: GPL-3.0-or-later
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/update-docs
  compatibility: Pi skill format; git-based projects with markdown or html technical docs.
---

# Update Docs

Use this skill after implementation or refactoring when documentation must be synchronized, expanded, or created.

## Modes

- **Sync Mode (default):** update existing docs after code changes.
- **Create Mode:** generate missing technical docs for a module, service, or API.
- **Visual Mode (optional):** produce a single HTML technical doc with embedded SVG diagrams.

## Scope

- Root and module `README.md`
- `docs/` pages, index/navigation files, migration notes
- API reference and request/response examples
- Architecture and workflow documentation
- JSDoc/TSDoc and targeted inline clarifying comments
- Optional standalone HTML documentation files

## Guiding Rules

- Prioritize user-facing impact, not internal churn.
- Keep docs concise and task-oriented.
- Preserve existing style/conventions in the repo.
- Avoid duplicate docs when generated sources already exist.
- Treat uncertain behavior as a gap; verify from code before documenting.
- Prefer minimal, maintainable diagrams over decorative visuals.

## Required Inputs

Collect these up front when available:

- Target documentation scope (service/module/repo)
- Audience (user, integrator, maintainer, internal engineer)
- Output format (`markdown`, `html`, or `both`)
- Change source (`git status -u`, commit range, or release scope)
- Constraints (deadline, style guide, file locations)

If inputs are missing, make conservative assumptions and state them in output notes.

## Workflow

1. Discover documentation context:
   - read root `README.md`, docs index, and project config (`package.json`, `pyproject.toml`, etc.).
   - identify existing docs style and required section structure.
2. Determine documentation-relevant changes:
   - inspect `git status -u` (or latest commit/range if clean).
   - map changed code to impacted setup, behavior, API, and operations.
3. Map required doc updates:
   - APIs, setup/config changes, behavior changes, workflows, and constraints.
4. Update the minimal necessary docs:
   - root/module README and focused docs pages.
5. Generate technical reference sections when needed:
   - endpoint catalog (method, path, params, auth, errors).
   - usage snippets for common operations.
   - architecture/workflow diagrams for non-trivial systems.
6. Validate quality:
   - examples are consistent with current code.
   - links and cross-references resolve.
   - no stale or contradictory statements.
   - commands are runnable or clearly marked as pseudo/example.

## Decision Threshold

- Small changes (1-2 simple files): perform direct targeted edits.
- Larger changes (3+ files or cross-cutting API/flow changes): do a structured pass across docs, then verify coherence.
- If visual or API-heavy docs are requested: produce dedicated technical doc output (Markdown and/or HTML).

## Technical Doc Structure (Create/Visual Mode)

Use this section order when creating new technical docs:

1. Overview (purpose, key capabilities, scope)
2. Getting Started (install/setup/quick start)
3. API Reference (endpoint-by-endpoint)
4. Code Examples (common tasks)
5. Architecture (components and data flow)
6. Workflows (step-by-step operational flows)
7. Operational Notes (limits, failures, troubleshooting)

## API Reference Pattern

Use a consistent endpoint block. Markdown preferred unless HTML is explicitly requested.

````md
### GET /api/users/{id}
Retrieve user details by ID.

- Auth: Bearer token
- Path params: `id` (string)
- Query params: none

#### Request
```bash
curl -X GET https://api.example.com/api/users/123 \
  -H "Authorization: Bearer <token>"
```

#### Response (200)
```json
{
  "id": "123",
  "name": "Jane Doe",
  "email": "jane@example.com"
}
```
````

## Visual Mode Guidance (HTML + SVG)

If the user asks for a visual technical doc:

- Produce a single file named `[system]-docs.html` by default.
- Include embedded CSS, section anchors, and readable code blocks.
- Use inline SVG for architecture/workflow diagrams with explicit `viewBox`.
- Keep labels and node naming aligned with real code/service terms.
- Use semantic HTTP method colors:
  - GET: green
  - POST: blue
  - PUT/PATCH: amber or purple
  - DELETE: red

Minimal endpoint HTML block:

```html
<div class="endpoint">
  <h3><span class="method-get">GET</span> /api/users/{id}</h3>
  <p>Retrieve user details by ID</p>
  <h4>Request</h4>
  <pre><code>curl -X GET https://api.example.com/api/users/123</code></pre>
  <h4>Response</h4>
  <pre><code>{"id":"123","name":"Jane Doe"}</code></pre>
</div>
```

Minimal diagram SVG skeleton:

```html
<svg viewBox="0 0 1200 600" role="img" aria-label="System architecture">
  <rect x="80" y="120" width="240" height="100" rx="10"></rect>
  <text x="200" y="175" text-anchor="middle">API Gateway</text>
  <path d="M 320 170 L 460 170" fill="none" marker-end="url(#arrow)"></path>
</svg>
```

## Quality Bar

- No unverified claims; reflect code reality.
- Separate confirmed behavior from assumptions.
- Keep examples deterministic and copy/paste safe.
- Ensure diagrams and prose match the same architecture and naming.
- Call out remaining doc debt explicitly.

## Output

- List of updated documentation files.
- Brief summary of what changed and why.
- Any assumptions and unresolved gaps.
- Any remaining doc debt explicitly called out.
