# Severity, scoring, and workflow

## Confidence tiers

Every term across this skill is tagged the same way the corpus and the live scorer tag it:

- **red**: strong tell (individual studies put these at 5-25x the frequency of human text, or they're near-unique to AI output). Flag every occurrence.
- **orange**: moderate tell. Legitimate on its own; two or more from the same category in one paragraph is the actual signal.
- **yellow**: context-dependent. Only counts on its 2nd+ occurrence in a piece. A single incidental use is just normal writing catching a word the corpus happens to track.

## Scoring

If you want a number instead of a judgment call and you're working in this repo, use the exact function: `scoreAiSlop()` in `lib/social/clichecheck.ts`, or the public `/slop-checker` tool; both run the same 758-entry corpus. Its formula, for reference:

1. Count every matched term (yellow only counts once it's hit twice).
2. Score equals the strongest single match's `strength_score` (0-100), plus `min((extra_matches) * 4, 20)` as a stacking bonus, capped at 100.

That formula exists so one weak yellow hit can't sink an otherwise clean draft, but several moderate tells stacking up still gets flagged even without a single red hit.

**Portable approximation** (no corpus file to hand, e.g. this skill copied into another project): treat any single red hit as worth flagging outright; treat 2+ orange hits from the same category in one paragraph as worth flagging; treat yellow hits as noise until they repeat. When 3+ distinct categories all trigger in the same piece (vocabulary, sentence patterns, and formatting), that's a stronger signal than any one category maxed out, even if no single hit is red.

**When to advise a full rewrite instead of patching**: 5+ flagged terms across multiple categories, plus uniform sentence/paragraph length. At that point the structure itself is generated, not just the word choice; patch-fixing individual phrases won't fix a piece whose actual problem is its shape. Advise stating the core point in one sentence and rebuilding from there, rather than editing sentence by sentence.

## Self-reference escape hatch

When writing *about* AI tells (a blog post on this exact topic, a tutorial, or this skill's own reference files), quoted examples are exempt. Only flag patterns that show up in the author's actual prose, not in cited illustrations of bad writing.

## Register calibration

Not every rule applies at full strength everywhere. Loosen or tighten based on what you're editing:

| Register | Loosen | Tighten |
|---|---|---|
| **Fiction / narrative prose** | none of the general-content rules loosen; apply `fiction-tells.md` on top, not instead | body-language and atmosphere clichés (`fiction-tells.md`), cliché name clusters |
| **Blog / long-form article** | (default register) | everything at full strength; this is the register the corpus was built against |
| **Marketing / landing copy** | some promotional language is the genre; a little sell is expected | tourism-brochure vocabulary and significance-inflation stay strict; hype about a real feature still needs a real claim behind it |
| **Social / LinkedIn post** | short fragments, one or two emoji, a single rhetorical-question hook | social endorsement closers (`"thank me later"`) and engagement-bait framing stay strict; that's precisely where the AI shape is most recognizable |
| **Email** | (no relaxation) | email-slop openers/closers (`"I hope this email finds you well"`, `"don't hesitate to reach out"`) are almost always improvable to something specific to this recipient |
| **Docs / README** | hedging language that's genuinely accurate ("may," "in most cases"), uniform structure (docs are supposed to be scannable) | copula avoidance still reads badly even in docs; prefer "X is Y" over "X serves as Y" |
| **Casual (chat, Slack, DMs, issue/PR comments)** | most rules; a quick reply isn't a publication | chatbot boilerplate and citation-markup leaks (`channel-and-chatbot-tells.md`) never get a pass; watch the wall-of-text tell too, since a real person breaks a reply at thought boundaries and an LLM defaults to one dense unbroken block |

## Voice, if the writer wants one

Voice is independent of how strict to be. You can write blunt for a blog or warm for docs. If the writer names a voice or gives a writing sample, match its actual sentence-length pattern, contraction rate, and recurring word choices rather than imposing a generic "human" register on top. Don't upgrade their vocabulary; if they write "stuff" and "things," keep that.

## Output format

**`detect` mode**: Two sections. (1) Issues found: bulleted, each with the offending text quoted and its tier. (2) Assessment: for each flag, say whether it's a clear problem or a judgment call. Some flagged patterns are fine in context (one well-placed "however" isn't a problem; three "notably"s in 500 words is).

**`rewrite` mode**: Four sections. (1) Issues found, same as above. (2) Rewritten version: preserve structure, intent, and every specific technical/narrative detail; change only what the flags require. (3) What changed: the meaningful edits, not a word-by-word diff. (4) Second-pass check: re-read the rewrite itself for anything the first pass introduced, such as a recycled transition or a new red-tier word swapped in for the one you cut. If it's clean, say so.

**`edit` mode**: After editing the file in place: (1) Edits made: bulleted, file location plus before/after, only the spans touched. (2) Verification: confirm you re-read the file and the flagged spans are actually resolved; note anything deliberately left alone because it was already clean or clearly intentional.

In every mode: don't over-correct into sterilized prose. If the original is already strong, say so and make only the necessary cuts.
