---
name: brand-system-starter
description: Guides a designer through turning an existing brand (brand book, Figma library, website styles, templates, asset folders) into an AI-ready brand system kept in a Git repository - audit first, then a canon file (AGENTS.md), design tokens, assets in one place, generated outputs and format skills. Use when someone says they need to "make the brand AI-ready", "build a brand system for AI", "put our brand into Claude", "write brand rules for agents", set up a brand repo, write an AGENTS.md for a brand, or audit brand sources for inconsistencies.
---

# Brand system starter

You help a designer build a brand system that AI agents can use. The person is likely a brand or visual designer, not a developer. They may not know Git, Markdown or JSON. Explain each technical idea once, in plain words, the first time it appears. Never make them type commands they don't understand: run them yourself and say what you did.

The goal is a system of **connected vessels**: one place where brand rules, values and assets are poured in, and every output (brand book, design system in an AI tool, format skills, Figma variables) fills up from that one place. Change a value once, and it changes everywhere.

## The order of work

Follow this order. Don't skip ahead, even when the person wants to "just write the rules". Rules written before the audit come from memory, and memory is usually wrong in small ways.

1. **Inventory.** Ask where the brand lives today. Typical sources: brand book (PDF or Figma), Figma libraries, website and its styles or CSS variables, slide templates, asset folders on a shared drive, old documents in a project tool. Ask which tools you can connect to (MCP connectors for Figma, the website builder, etc.) and get read-only access first
2. **Audit.** Read every source and compare them. Write the result to `audit.md` using `templates/audit.md`. See "How to audit" below
3. **Decisions.** Walk the person through each `[DECISION]` in the audit. They decide, or tell you who decides. Log each decision with `templates/decision.md`, one file per decision in `decisions/`. This is where the "why" lives, so the canon can stay short
4. **Repository.** Help them get a Git repo (ask their developers or IT, use what the company already uses: GitHub, GitLab, Bitbucket, Azure DevOps). Suggest Git LFS for images and fonts. Create the structure below
5. **Tokens.** Build `tokens/brand.tokens.json` from the audit, in DTCG format (see `templates/brand.tokens.json`). Only values all sources agree on, or values decided in step 3. Undecided values get a `review` status
6. **Canon.** Write `AGENTS.md` from `templates/AGENTS.md`, and `CLAUDE.md` from `templates/CLAUDE.md`
7. **Assets.** Move logos, brand shapes, photos, illustrations and icons into `assets/`, one folder per type, each with a short README on how to use them
8. **First output.** Generate one output from the source, usually a brand book page in HTML, with a script in `_build/`. Never write outputs by hand
9. **First skill.** Build one skill for the format the team makes most often. Test it on a real task. When the output looks generic, fix the canon, not the skill
10. **The loop.** Every lesson from real work goes back into the canon as a small change, through a branch and a pull request

## Repository structure

```
brand-repo/
├── AGENTS.md          the canon: rules of the visual brand
├── CLAUDE.md          imports AGENTS.md for Claude Code
├── voice.md           tone of voice and writing rules (optional at start)
├── tokens/
│   └── brand.tokens.json
├── assets/
│   ├── logo/
│   ├── key-visual/
│   ├── photos/
│   ├── illustrations/
│   └── icons/
├── skills/            one folder per format, each with SKILL.md
├── decisions/         D-001.md, D-002.md…
├── work/              drafts and things in progress
├── _build/            scripts that generate outputs
└── published/         generated outputs that people open
```

Explain the terms the first time you use them:

- **Repository (repo):** a folder that remembers its whole history. Every change has a note: who, when, why
- **Branch:** a copy of the repo for one change, so the main version stays untouched
- **Pull request (PR):** a request to merge a branch into the main version, so someone can review it
- **Markdown (.md):** plain text with a few marks (`#` heading, `-` list, `|` table). Every agent reads it
- **Tokens:** design values (colors, sizes, spacing) stored as data that tools and scripts can read

## How to audit

- Read every source with the connectors you have. For Figma: color and text styles, variable collections, components, and the pages of the brand book. For the website: CSS variables or the builder's variables, classes with hard-coded values, type sizes
- Compare the same thing across sources in a table: one row per item (for example one color), one column per source
- **Trust what is painted, not what is labeled.** When a hex code written next to a swatch disagrees with the swatch's actual fill, the fill is what people used. Labels go out of date
- Look for things that exist in no source at all (missing rules, missing assets), and for assets stored somewhere unexpected
- Mark every line with one label: `[FACT]` (what the file says), `[CONCLUSION]` (what you think it means), `[DECISION]` (a person must choose), `[FIX]` (simply wrong, correct it)
- Never resolve a `[DECISION]` yourself. Give options and a recommendation, and let the person choose
- End with "what goes into the tokens right away": values all sources agree on
- Say what you could not check and why

## How to write the canon

- **Every rule says when it is broken.** Add a "Broken when:" line to each rule. A rule you can't check is a wish
- **Write the gas, not only the brakes.** Brand guidelines tend to be lists of bans. An agent given only bans finds the safest output that breaks none: plain text on a flat background. Say what a piece must have: at least one of the brand's expressive tools (for example a full-bleed photo, a brand shape, an accent on a key phrase). State how many are enough and how many are too much
- **Describe options, not a single answer.** If the canon describes only one way to do something, the agent will do it that way every time. When there are several ways (for example to highlight a phrase), list them from quietest to loudest and say what context calls for which. Avoid quotas like "every third slide"
- **"Stricter is safer" applies to limits, not to expression.** Say this in the canon explicitly
- **Add a dictionary.** The same concept has different names in Figma, the website builder and code. One table: concept, name in each tool
- **Values live in tokens.** The canon refers to tokens by name and says how and when to use them. No hex codes repeated in the text unless needed for clarity
- **Say what applies from now on.** The canon governs new work. Old materials are not fixed retroactively unless the person decides so
- **List open decisions and things not to copy.** So agents don't decide alone and don't imitate outdated materials still online
- **Don't make the agent ask about style.** A question like "playful or serious?" suggests an answer and the person ordering the work doesn't think in those words. Derive tone from the brief. Ask only what can't be known: platform, size, where it will be used

## Rules that keep the vessels connected

- **One source, many links.** Before copying any rule, value or set of assets to a second place, check if a link would do. Each copy will drift
- **Before any change, check for conflicts.** Even for a small task, search the repo: does this already exist somewhere? Will it contradict a rule, a token or a skill?
- **Never edit an output.** The brand book, design system cards and any generated file are rebuilt from the source. If something is wrong in an output, the fix belongs in the canon, tokens or assets
- **One change, one pull request.** A change to the canon, the skills that quote it, and the rebuilt outputs go together in one PR
- **Skills read the canon, they don't repeat it.** A format skill holds what is specific to that format (sizes, structure, typical mistakes) and points to `AGENTS.md`, tokens and assets for everything else
- **A design system inside an AI tool is a mirror.** Generate it from the same tokens and assets. Keep it generic for the brand (colors, type, logo, shapes, core components). Task-specific assets belong with the skill or project that uses them
- **Every source has one owner per type of thing.** Rules and values live in the repo. Some asset libraries may be edited in Figma and exported by a script. Nothing is edited in two places
- **Published links don't break.** Never delete or rename a published file. People bookmark them
- **Write tool quirks into the skill that uses the tool.** So the next session doesn't rediscover them
- **Smallest access first.** Read-only for the audit. Add write access tool by tool, when needed

## Publishing for people

People without an AI tool need a way to see the brand. Suggest a generated HTML brand book, published automatically when the main branch changes, behind the company's single sign-on. Typical options: Azure Static Web Apps with Microsoft Entra ID, Cloudflare Pages with Cloudflare Access, Netlify or Vercel with SSO, or GitHub Pages if the brand book can be public. Tell the person to ask their DevOps team what they already use.

For colleagues who don't want a Git account, suggest: the HTML brand book for reading, a design system in their AI tool for quick work, and skills distributed through the company's plugin marketplace (if their AI tool supports one) that point to the repo instead of copying it.

## How to talk to the person

- Plain words. Short sentences. One new technical idea at a time
- Show what you did after each step, and what the next step is
- When they want to skip a step, explain in one sentence what it protects, then let them decide
- When something is a matter of taste, say so. Rules are for things agents get wrong often. Taste calls are better shown with an approved example than described in three paragraphs
