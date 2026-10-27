# [Brand name]: brand canon

Rules of the visual brand, written for AI agents and readable by people.
Owner: [name]. Changes only through a branch and a pull request.
Values (colors, sizes, spacing) live in `tokens/brand.tokens.json`. This file says how and when to use them.

---

## 1. Principles

### 1.1 Scope
This canon governs new work from [date]. Existing materials are not corrected retroactively unless a decision says so.

### 1.2 Character
[3 to 5 sentences: what the brand feels like, what "good" means here.]

### 1.3 Stricter is safer, for limits only
When in doubt about a limit (size, count, spacing), take the stricter reading. This does not apply to expression: see 1.4.

### 1.4 Every piece has at least one expressive tool
Every visual uses at least one of: [full-bleed photo / brand shape / accent on a key phrase / …]. One is enough. Two is fine for a campaign. Three is too much.
Broken when: a piece uses none of them.

## 2. Working rules for the agent

- Read this file before any brand work
- Look for an existing asset before drawing anything new (`assets/`)
- Save drafts in `work/`, never in `published/`
- Never edit files in `published/` by hand. Rebuild them with `_build/`
- Don't ask about style or tone. Derive it from the brief. Ask only about platform, size and where it will be used
- [Things the agent must never do without asking]

## 3. Dictionary

The same concept in each tool.

| Concept | Figma | Website | Tokens | Brand book |
|---|---|---|---|---|
| Main text on light | … | … | `color.text.primary` | … |
| … | … | … | … | … |

## 4. Color

### 4.1 Proportions
[Which colors carry the brand and in what rough proportion.]
Broken when: …

### 4.2 Accent per background
[Which accent works on light, which on dark.]
Broken when: …

### 4.3 Bans
- …

## 5. Typography

### 5.1 Scale
Use the type tokens. [Which levels are for what.]

### 5.2 Highlighting a phrase
Options from quietest to loudest:
1. [Accent color only]
2. [Highlighter / underline]
3. [Gradient / other strong effect]
Pick by context: [when to use which]. Don't use the same one on every piece in a set.
Broken when: every piece in a set uses the loudest option.

## 6. Logo

Versions, clear space, minimum size, allowed positions, files in `assets/logo/`.
Broken when: …

## 7. Brand shapes, photos, illustrations, icons

For each: when to use it, when not, where the files are.
Broken when: …

## 8. Layout

Spacing, rhythm, how a page or slide opens and closes, space under headings.
Broken when: …

## 9. Components

Card, button, table, quote, eyebrow. For each: what it looks like and which tokens it uses.
Broken when: …

## 10. Bans

The short list of things that break the brand.

1. …

## 11. Sources of truth

| Kind of thing | Lives in | Edited in |
|---|---|---|
| Rules | `AGENTS.md` | this repo |
| Values | `tokens/brand.tokens.json` | this repo |
| Logo, shapes, photos | `assets/` | this repo |
| [Library edited in Figma] | Figma file [link] | Figma, exported by `_build/…` |

## 12. Don't copy

Old materials still online that are no longer the brand.

- …

## 13. Open decisions

Not decided yet. Don't decide these alone: ask.

- …
