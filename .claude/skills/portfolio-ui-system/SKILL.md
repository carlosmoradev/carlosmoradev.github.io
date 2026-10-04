---
name: portfolio-ui-system
description: "Trigger: portfolio design, ui system, css styles, layout, visual styling, aesthetic improvements. Design system constraints, typography scales, spacing rules, and component standards for carlosmora.dev."
license: Apache-2.0
metadata:
  author: carlosmora
  version: "1.0"
---

## Activation Contract

Use this skill when modifying `assets/css/style.css`, `assets/css/syntax.css`, `_layouts/`, `_includes/`, or implementing new UI components for `carlosmora.dev`.

Enforce these constraints to maintain a clean, authoritative Principal Platform Architect personal brand, strict WCAG 2.1 AA accessibility, and consistent typographic rhythm.

## Hard Rules

- **Reading Measure**: Article and page prose (`.post-content`, `.project-content`, `.page-content`) must never exceed `740px` (`max-width: 740px; margin-inline: auto;`). Target 60–80 characters per line.
- **Mobile Spacing**: All headers, banners, and layout containers must maintain at least `20px` horizontal padding on viewports `< 768px`. Never allow text to touch screen glass.
- **System Typography**: Body text must use the system stack: `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;`. Monospace code must use `ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;`. Do not add unimported web fonts.
- **Single `<h1>` Landmark**: Every page must contain exactly one `<h1>`. Standardize on `<div class="section-title"><h1>...</h1></div>`. Never declare secondary `<h1>` elements in markdown content.
- **Tokens First**: All colors, background gradients, borders, and shadows must consume `:root` CSS variables in `assets/css/style.css`. Do not inject arbitrary inline styles or unmapped hex codes.
- **Accessibility & Touch**: Normal text contrast must meet WCAG AA (>= 4.5:1). Interactive controls (buttons, links, nav toggles) must provide minimum 44x44px touch targets.
- **Public Sanitization**: UI designs and mockups must never expose client identifiers, AWS account IDs, or unsanitized enterprise infrastructure metrics per `.mindblowing/public-showcase/sanitization-rules.md`.

## Decision Gates

| Target | Requirement | Action |
| --- | --- | --- |
| Reading Layout | Line length unbounded | Wrap in `.post-content` / `.page-content` with 740px constraint |
| New Component | Needs new color or surface | Add token to `:root` in `style.css` and check WCAG AA contrast |
| Page Template | Multiple or missing H1 | Use single `<div class="section-title"><h1>...</h1></div>` |
| Mobile Viewport | Content touches edge (< 20px) | Add horizontal padding `20px` to header or container |
| Code Highlight | Comment contrast < 4.5:1 | Use `#4b5563` or darker in `syntax.css` |

## Execution Steps

1. Read `:root` variables in `assets/css/style.css` before authoring CSS changes.
2. Ensure changes reuse existing tokens (`--primary-color`, `--secondary-color`, `--bg-light`, `--border-color`).
3. Check headings and landmarks across `_layouts/` and markdown files.
4. Verify build succeeds with `bundle exec jekyll build`.
5. Run sanitization grep checks before recommending git staging.

## Output Contract

Return:
- Files modified and CSS selectors affected.
- Contrast verification and responsive breakpoint behavior (mobile 375px, desktop 1200px).
- Confirmation that reading width (740px) and single H1 rules remain intact.

## References

- `assets/css/style.css` — Canonical design system and `:root` variables.
- `assets/css/syntax.css` — Rouge code syntax highlighting styles.
- `.mindblowing/public-showcase/sanitization-rules.md` — Mandatory sanitization guidelines.
- `.claude/skills/web-audit/SKILL.md` — Diagnostic and audit protocol.
