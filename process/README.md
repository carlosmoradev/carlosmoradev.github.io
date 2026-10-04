# Process & Editorial Workspace

This directory isolates internal strategy, editorial workflows, drafts, and design decisions from the public portal source.

## Structure

- `CONTENT_STRATEGY.md`: Editorial pillars, post narrative templates, and thought leadership positioning.
- `drafts/`: Work-in-progress posts and raw outlines before being sanitized and published to `_posts/`.
- `design/`: UI/UX tokens, audit findings, and aesthetic upgrade plans.

## Guardrails

- This directory is explicitly excluded from Jekyll builds in `_config.yml`.
- Content in `drafts/` must undergo sanitization review against `.mindblowing/public-showcase/sanitization-rules.md` before moving to `_posts/`.
