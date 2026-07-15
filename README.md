<div align="center">

# 📖 The Corpus of AI Clichés

### 758 words, phrases, names, and formatting tics that give away AI-written text. With the receipts.

[![Version](https://img.shields.io/badge/version-1.7-blue)](#changelog)
[![Entries](https://img.shields.io/badge/entries-758-brightgreen)](#whats-inside)
[![License: MIT](https://img.shields.io/badge/license-MIT-lightgrey)](LICENSE)
[![Format](https://img.shields.io/badge/format-JSON-orange)](ai-cliches-corpus.json)

**[🔎 Try the live detector at app.aistoryhub.co →](https://app.aistoryhub.co)**

</div>

---

## Why this exists

Every model has a tell. Usually a few hundred of them. Kobak and colleagues found `delve` showing up in PubMed abstracts at 25 times its pre-2023 rate. GPTZero clocked similar spikes for `tapestry` and `landscape` across 3.3 million documents. Character generators keep landing on Elara, so often that a name blog crowned it Name of the Year in 2025, for reasons that have nothing to do with parents naming actual babies.

None of that is a hunch, and it isn't limited to one or two overused words. This corpus tracks the full pattern: the stock verbs (`delve`, `underscore`, `leverage`), the sentence scaffolds ("In today's fast-paced world..."), the assistant boilerplate ("Would you like me to...?"), even the formatting habits, like bolding a term right after defining it, or leaving `oaicite` citation debris pasted into a document that was supposed to look handwritten. Every entry carries a score and, where one exists, a citation. Where the research doesn't exist yet, we say so.

This is the same data behind the detector at **[AIStoryHub](https://app.aistoryhub.co)**. You can browse it interactively at **[app.aistoryhub.co/corpus](https://app.aistoryhub.co/corpus)**. This repo is the source file underneath it: open, versioned, and free to fork.

## What's inside

`ai-cliches-corpus.json` holds **758 entries** across six categories, each scored 0 to 100 for detection strength and banded into a confidence tier.

| Category | Entries | What it covers |
|---|---:|---|
| **Words & phrases** | 509 | Signature verbs (`delve`, `underscore`, `leverage`), stock nouns (`tapestry`, `landscape`, `realm`), transitions, hedges, email and social slop, fiction clichés |
| **Names & personas** | 86 | The names models reach for by default in characters and example people (`Elara`, `Marcus Chen`), plus fantasy, sci-fi, and invented place names |
| **Sentence patterns** | 53 | Structural formulas: "In today's fast-paced world...", "Here's the thing...", "Whether you're a founder, a marketer, or...", "No X. No Y. No Z." |
| **Channel-specific & assistant tells** | 50 | Chatbot boilerplate ("Would you like me to...?", "Regenerate response"), citation markup leaks, cutoff-date hedges, LinkedIn slop, email sign-offs |
| **Rhetorical & structural moves** | 36 | Contrast-and-reveal scaffolds, false balance ("it's not just X, it's Y"), fiction structural tells, anti-synthesis paragraph closers |
| **Formatting tells** | 24 | Bolded-term bullets, emoji-as-structure, em-dash overuse, uniform paragraph length, unfilled template placeholders, leftover citation artifacts (`oaicite`, `contentReference`, `utm_source=chatgpt.com`) |

### Confidence tiers

Every entry is banded by how much weight it can carry on its own.

| Tier | Meaning | Count |
|---|---|---:|
| 🔴 **red** | Strong tell. Rare in genuine human writing at this frequency | 359 |
| 🟠 **orange** | Moderate tell. Elevated, but needs corroboration | 300 |
| 🟡 **yellow** | Context-dependent. Only meaningful under overuse | 99 |

A single yellow-tier hit proves nothing. A document with a dozen reds does.

### The receipts: highest-scoring tells

| Score | Term | Category | Evidence |
|---:|---|---|---|
| 99 | `delve` | Words & phrases | Kobak et al. 2024, *arXiv:2406.07016*: 25.2x frequency ratio across 14M PubMed abstracts |
| 97 | `tapestry` | Words & phrases | GPTZero AI Vocabulary corpus |
| 96 | `it's important to note` | Words & phrases | Hedge-phrase overrepresentation |
| 95 | Leftover AI citation artifacts (`oaicite`, `contentReference`, `turn0search`) | Formatting tells | Copy-paste residue from ChatGPT citation markup |
| 95 | `utm_source=chatgpt.com` in cited URLs | Formatting tells | Direct paste-through artifact |
| 95 | `Regenerate response` | Channel-specific tells | Leftover UI chrome pasted into copy |
| 94 | `landscape` | Words & phrases | GPTZero AI Vocabulary corpus |
| 92 | `voice barely above a whisper` | Fiction clichés | EQ-Bench slop-score trigram list (Paech, 2025) |
| 90 | `Elara` | Names & personas | seehuhn.de 2026 100-prompt Claude test; Namerology 2025 "Name of the Year" |
| 89 | `underscore` (verb) | Words & phrases | Kobak et al. 2024, 9.1x frequency ratio |

That's the top ten. The other 748 are in the JSON.

## Schema

Each entry in the `entries` array looks like this:

```json
{
  "term": "delve",
  "category": "Words & phrases",
  "category_key": "words_and_phrases",
  "subcategory": "Signature verbs",
  "confidence": "red",
  "strength_score": 99,
  "example": null,
  "study_ratio": 25.2,
  "study_metric": "r",
  "study_measured_form": "delves",
  "study_source": "Kobak et al. 2024, arXiv:2406.07016 (14M PubMed abstracts)",
  "note": null
}
```

| Field | Type | Description |
|---|---|---|
| `term` | string | The word, phrase, name, or pattern name |
| `category` / `category_key` | string | One of the 6 top-level categories (human-readable / slug form) |
| `subcategory` | string | Finer-grained grouping, e.g. "Fiction emotional-beat clichés" |
| `confidence` | `red` \| `orange` \| `yellow` | Strong / moderate / context-dependent tell |
| `strength_score` | 0-100 | Composite detection strength, see [Methodology](#methodology) |
| `example` | string \| null | Illustrative sentence(s), populated mainly for structural and formatting entries |
| `study_ratio` | number \| null | Measured frequency ratio (`r`) or excess-frequency gap (`delta`) from a cited study |
| `study_metric` | `r` \| `delta` \| null | Which statistic `study_ratio` represents |
| `study_measured_form` | string \| null | The exact word form the cited study measured (e.g. `delves` vs `delve`) |
| `study_source` | string \| null | Citation for the study or detector run backing this score |
| `note` | string \| null | Extra context, e.g. observed dominance in controlled prompt tests |

Top-level metadata (`name`, `version`, `generated`, `scoring`, `study_headline_figures`, `entry_count`, `changelog`) documents the corpus itself. Field-by-field definitions live in the `scoring` object inside the file.

## Methodology

`strength_score` is a composite rating from 0 to 100. Where a published number exists, the score comes straight from it:

- **Detector scores**, from the "Your AI Slop Bores Me" Hall of Shame
- **GPTZero AI Vocabulary** frequency ratios, drawn from a 3.3 million document corpus
- **Peer-reviewed frequency studies**: Kobak et al. 2024 and 2025, Juzek & Ward 2024 and 2026, Liang et al. 2024, Ward et al. 2025
- **EQ-Bench and antislop** rankings for fiction-specific tells (Zhang et al. 2025 model fingerprints, Paech 2025 trigram lists)

Where no direct measurement exists yet, entries are banded by confidence tier instead: strong lands around 75, moderate around 50, context-dependent around 30. That's an admitted gap, not a hidden one. Some corners of this list are better evidenced than others, and the confidence tier tells you which corner you're in.

A few numbers worth knowing on their own, straight from `study_headline_figures`:

- `delve` runs at 25.2 times the expected rate in post-2023 text (Kobak et al., 14M PubMed abstracts)
- `showcasing` runs at 9.2x, `underscores` at 9.1x
- At least 10% of 2024 PubMed abstracts show measurable LLM involvement

One caveat worth flagging on its own. Character names like `Elara` and `Marcus Chen` are the weakest individual signal in this whole set, because they're also just names real people have. Score them as one small vote among many, never as a verdict by themselves.

## Using the corpus

**jq: pull every red-tier word or phrase tell**

```bash
jq -r '.entries[] | select(.confidence=="red" and .category=="Words & phrases") | .term' ai-cliches-corpus.json
```

**Python: load the corpus and score a document**

```python
import json

with open("ai-cliches-corpus.json") as f:
    corpus = json.load(f)

terms = {e["term"].lower(): e["strength_score"] for e in corpus["entries"] if e["category"] == "Words & phrases"}

def score_text(text: str) -> int:
    text_low = text.lower()
    return sum(score for term, score in terms.items() if term in text_low)

print(score_text("Let's delve into this multifaceted tapestry of ideas."))
```

**Build a regex sweep**

```python
import re
pattern = re.compile("|".join(re.escape(e["term"]) for e in corpus["entries"] if e["confidence"] == "red"), re.I)
hits = pattern.findall(your_text)
```

A keyword match like the one above will get you started, but it can't weigh context, catch a pattern that spans a full sentence, or tell a deliberate quote from a real tell. **[app.aistoryhub.co](https://app.aistoryhub.co)** runs this corpus against full manuscripts with that weighting built in. [Try it free](https://app.aistoryhub.co).

## Claude Skill

`Skills/` packages this corpus as a Claude Skill: `avoid-ai-writing`. Drop the folder into a project's `.claude/skills/` (or wherever your agent loads skills from) and Claude will detect and remove AI writing tells from fiction, blog posts, marketing copy, emails, social posts, docs, and code comments, in either `detect` (flag only) or `rewrite`/`edit` (flag and fix) mode.

The skill is self-contained. `SKILL.md` is the entry point, and the terms themselves are embedded in the reference files rather than just linked, so it keeps working if you copy the folder into another project on its own:

| File | Covers |
|---|---|
| `references/words-and-phrases.md` | Vocabulary tiers with replacements, plus grouped phrase lists (marketing hype, stock transitions, hedges, email and social boilerplate) |
| `references/sentence-and-structure.md` | Sentence-level construction patterns, hook and closer formulas, formatting tells, whole-piece rhythm |
| `references/fiction-tells.md` | Fiction-only clichés: body language, atmosphere, emotional beats, dialogue-tag crutches, cliché names |
| `references/channel-and-chatbot-tells.md` | Assistant and chatbot fingerprints treated as near-proof regardless of context |
| `references/severity-and-workflow.md` | Confidence-tier model, scoring approximation, and register calibration |

## Changelog

- **1.7** (2026-07-15). Added 7 entries and 10 structural-pattern regexes, ported from [conorbronsdon/avoid-ai-writing](https://github.com/conorbronsdon/avoid-ai-writing) (MIT license): chatbot citation markup leaks, AI-tool UTM params, cutoff-date and self-disclosure disclaimers, unfilled template placeholders, formulaic essay openers, hedge-stacked predictions, social CTA closers, parenthetical hedging. Also fixed three pre-existing description-only entries (`utm_source`, em-dash overuse, Title Case headers) that had no working matcher.
- **1.6** (2026-07-15). Added 9 entries: fiction dialogue-tag crutches (`said gently`, `said quietly`, `genuinely`, `I feel like`, sympathy-check and therapy-speak dialogue lines) and anti-synthesis paragraph closers (`an unspoken understanding passed between them`, `said more than words ever could`, `words left unsaid between them`), sourced from a curated anti-AI-tell prose watchlist.
- **1.5** (2026-07-13). Added 184 entries from Wikipedia's "Signs of AI writing," GPTZero AI Vocabulary (3.3M docs), Kobak et al. 2025 (*Science Advances*), Juzek & Ward 2024/2026, Liang et al. 2024, Ward et al. 2025, Zhang et al. 2025 model fingerprints, and EQ-Bench/antislop fiction slop lists. Added a new fiction wing covering body language, emotional beats, atmosphere, structural tells, and place names. Pruned 16 generic terms that turned out to be too false-positive-prone to keep.
- **1.4** (2026-06-09). Initial public release, 574 entries.

## Contributing

Found a tell we missed, or a citation we got wrong? Open an issue or a PR against `ai-cliches-corpus.json`. Bring a source if you can, a study, a detector run, or at minimum a clear pattern with examples. Pure gut feeling is fine too, but keep it in the yellow tier where it belongs.

## License

MIT. See [LICENSE](LICENSE). Use it, fork it, build a detector on it, ship a product with it. Attribution is appreciated, not required.

---

<div align="center">

Built by the team at **[AIStoryHub](https://app.aistoryhub.co)**, tools for writers who want their words to sound like *theirs*.

**[Browse the corpus live →](https://app.aistoryhub.co/corpus)** · **[Run the detector →](https://app.aistoryhub.co)**

</div>
