---
name: avoid-ai-writing
description: Detect and remove AI writing tells ("AI-isms," "slop") from any written content, fiction chapters, blog posts, marketing copy, emails, social posts, docs, code comments. Use whenever asked to "remove AI-isms," "check for AI slop," "make this sound less like AI," "de-AI this," "audit for AI tells," "does this read like ChatGPT wrote it," or any time you are about to hand back finished prose an agent drafted. This skill is the general-purpose reference for every other register, and for fiction it's the only one of the two that applies.
---

# Avoid AI Writing

You are auditing or drafting content so it doesn't read as AI-generated. This applies to fiction prose, blog posts, marketing copy, social posts, emails, docs, PR/issue comments, and anything else a human will read as if a person wrote it.

## What this is and isn't

This is a writing-quality tool, not a verdict. Every pattern below is *more common* in AI output, not *exclusive* to it. Humans on deadline, writing in a second language, or working in a compressed genre (technical docs, academic abstracts) produce some of these same shapes. Treat matches as signal to weigh, not proof to prosecute. Don't use this to accuse a specific human of using AI; use it to make text (yours, an agent's, or a draft someone handed you) read like a person wrote it.

The flip side matters too: over-applying every rule at once produces sterilized prose, which is its own tell. A piece with zero em dashes, zero repeated words, and perfectly uniform "human-like" imperfection sprinkled in is still following a formula. The goal is specific and alive, not merely rule-compliant.

## Modes

**`detect`**: Flag tells with severity, don't rewrite. Use when auditing someone else's text, published content, or when the writer wants to fix things themselves.

**`rewrite`** (default for drafting): Flag and fix. Use when you're producing the text yourself or the writer wants a clean version back.

**`edit`**: Fix a named file in place with targeted edits, not a wholesale rewrite. Leave already-human passages untouched. Re-read the file after editing to confirm the flagged spans are actually resolved.

Infer the mode from context. An agent finishing a draft should self-check in `rewrite` mode by default. A request to "check this" or "audit this" is `detect`. A named file plus "fix it" is `edit`.

## Quick-start: never let these through, in any mode

These are near-definitive fingerprints of unedited AI output. A single hit is enough to flag regardless of everything else in the piece. Full list and detail in `references/channel-and-chatbot-tells.md`.

- Chatbot self-disclosure: "As an AI language model," "I don't have access to real-time data," "as of my last update"
- Citation/markup leaks from a chat UI: `citeturn0search0`, `contentReference[oaicite:...]`, `oai_citation`, `grok_card`, `attributableIndex`
- `utm_source=chatgpt.com` / `utm_source=claude.ai` / similar tracking params surviving into a cited URL
- Unfilled placeholders: `[Your Name]`, `[INSERT SOURCE URL]`, `2025-XX-XX`, `<!-- add citation -->`
- Assistant chrome: "Would you like me to...?", "I hope this helps!", "Here is a comprehensive overview of..."

## How to run an audit

1. Read the whole piece once before flagging anything. Some tells (uniform paragraph length, the AI "sentence DNA" arc, symmetric development) only show up at the piece level, not the sentence level.
2. Scan against the category files in `references/`, matching this piece's register to the right one(s):
   - `references/words-and-phrases.md`: vocabulary and stock phrases (applies almost everywhere)
   - `references/sentence-and-structure.md`: sentence-level patterns, openers/closers, formatting tells, whole-piece rhythm
   - `references/fiction-tells.md`: narrative-specific clichés (body language, atmosphere, cliché names). Apply this one only to fiction/narrative prose.
   - `references/channel-and-chatbot-tells.md`: near-definitive assistant/chatbot fingerprints, always in scope
3. Weight findings using `references/severity-and-workflow.md` (confidence tiers, when a single hit matters vs. when it only matters in clusters, and how to calibrate strictness to the register: fiction narration, blog, marketing, social, email, docs, casual chat).
4. In `rewrite`/`edit` mode, fix what's flagged, then re-read the result once more for anything the first pass introduced. A rewrite that swaps five red-tier words for five different red-tier words hasn't fixed anything.
5. Quoted examples of bad writing (including everything in this skill's own reference files) are exempt from flagging. Only flag patterns in the author's actual prose.

## Working inside this repo

The reference files below are self-contained (the terms are embedded, not just linked) so this skill works if copied into another project. But if you're working inside aistoryhub, the canonical, currently-maintained source of truth is `public/ai-cliches-corpus.json` (758 entries, versioned) plus `lib/corpus/structural-patterns.ts` (regex structural detectors) and `lib/social/clichecheck.ts` (`scoreAiSlop()`, the exact scoring function). If the corpus has grown since this skill was last generated, or you want a mechanical score instead of a judgment call, prefer those live sources: grep the JSON directly, or point the user at `/slop-checker`.

## Files

- `references/words-and-phrases.md`: vocabulary tiers with replacements (signature verbs/nouns/adjectives), plus grouped phrase lists (marketing hype, stock transitions, business idioms, tourism vocabulary, academic tells, hedges, email/social boilerplate)
- `references/sentence-and-structure.md`: sentence-level construction patterns, hook/opener formulas, rhetorical moves, formatting tells, and whole-piece rhythm diagnostics
- `references/fiction-tells.md`: fiction-only clichés: body language, atmosphere/sensory description, emotional beats, dialogue-tag crutches, structural tells, and cliché character/place names with alternatives
- `references/channel-and-chatbot-tells.md`: assistant/chatbot fingerprints treated as near-proof regardless of context
- `references/severity-and-workflow.md`: confidence-tier model, scoring approximation, register calibration, and output format per mode
