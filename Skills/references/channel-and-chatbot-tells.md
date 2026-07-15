# Channel and chatbot fingerprints

Unlike vocabulary and structure, everything in this file is near-definitive rather than probabilistic. These are artifacts of the chat/generation pipeline itself leaking into published text. A single occurrence is essentially proof that AI output was pasted without a cleanup pass, regardless of how the surrounding prose reads. Always in scope, in every mode, for every register.

## Assistant / chatbot boilerplate

- **red**: `Regenerate response`, chatbot citation markup leak (`citeturn0search3`, `contentReference[oaicite:3]{index=3}`, `oai_citation`, `grok_card`, `[attached_file:1]`), `Would you like me to…?`, AI self-disclosure and cutoff-date hedges (`"as of my last update"`, `"I don't have access to real-time data"`, `"based on available information"`), `"As an AI language model"`, `"As of my last knowledge update"`, `"certainly! here's"`, `"I cannot fulfill this request"`, `"I do not have access to real-time"`, `"I don't have personal opinions"`, `"I don't have the ability to"`, `"I'd be happy to assist you with that"`, `"I'm just an AI"`, `"I'm sorry, but I cannot"`, `"please note that I am an AI"`
- **orange**: `"always consult a professional"`, `"I cannot provide"`, `"It's important to remember that"`, `"Here is a..."` deliverable opener (`"Here is a comprehensive overview of the company's history:"`)
- **yellow**: `"Of course!"`

## Model-signature phrasing

- **orange**: `"Based on the provided text"`
- **yellow**: `"Below is..."` deliverable opener (`"Below is a detailed breakdown of each option."`)

## Fix

Every entry here is mechanical, not a judgment call: strip the artifact entirely. Don't try to "humanize" a citation token or a cutoff-date hedge into softer prose; delete it and, if the underlying claim mattered, replace it with a real, checkable source or just the fact itself. If a chatbot-chrome line survived into a draft ("Would you like me to turn this into a table?"), it means the draft was never actually reviewed before being handed over. Treat that as a signal to re-read the whole piece, not just patch the one line.

## Related mechanical detectors in this repo

`lib/corpus/structural-patterns.ts` has working regexes for the two highest-value entries in this file: `ai-citation-markup` (citeturn/oai_citation/grok_card patterns) and `ai-utm-source` (utm_source=chatgpt.com and similar), plus `cutoff-disclaimer` and `ai-placeholder`. If you're working in this repo and want a mechanical pass instead of an eyeball scan, run text through those patterns or through `/slop-checker` rather than re-deriving the regex by hand.
