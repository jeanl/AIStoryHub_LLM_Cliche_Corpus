# Words and phrases

Confidence tiers, matching the corpus (`public/ai-cliches-corpus.json`) and the live scorer (`lib/social/clichecheck.ts`):

- **red**: strong tell. Flag on sight, individually.
- **orange**: moderate tell. Fine alone; flag when two or more from the same list appear in one paragraph.
- **yellow**: context-dependent. Only flag on the 2nd+ occurrence in a piece. A single incidental use is normal writing.

Match inflected forms too (`-ly`, `-ing`, plural, verb conjugations) unless the variant carries a distinct, honest meaning judged by context.

## Signature verbs

The classic AI verb list. Reach for the plain verb instead.

| Term | Replace with |
|---|---|
| delve | explore, dig into, look at |
| leverage | use |
| underscore | highlight, show |
| streamline | simplify, speed up |
| foster | encourage, build |
| resonate | connect with, matter to |
| elevate | improve, raise |
| accentuate | emphasize, bring out |
| anchor | ground, base |
| augment | add to, expand |
| boast | have |
| bolster | support, strengthen |
| catalyze | trigger, spark |
| champion | back, push for |
| consolidate | combine, merge |
| cultivate | build, grow |
| curate | select, choose |
| dive into | look at, examine |
| elucidate | explain, clarify |
| embark | start, begin |
| encompass | include, cover |
| enhance | improve |
| enrich | improve, add depth to |
| evoke | bring to mind, suggest |
| exemplify | show, illustrate |
| facilitate | help, enable, run |
| galvanize | spur, motivate |
| garner | get, earn |
| harmonize | align, bring together |
| harness | use, tap |
| ignite | spark, start |
| illuminate | clarify, show |
| immerse | surround, absorb in |
| infuse | add, mix in |
| manifest | appear, show up as |
| mitigate | reduce, lessen |
| navigate | handle, work through |
| pave the way | make possible, open the door for |
| propagate | spread |
| reframe | rethink, recast |
| reimagine | rethink, redesign |
| reinforce | strengthen, back up |
| revolutionize | change, transform (say what specifically changed) |
| showcase | show, display |
| spearhead | lead, drive |
| synthesize | combine, distill |
| transcend | go beyond |
| transform | change (say how) |
| underpin | support, form the basis of |
| unlock | enable, open up |
| unveil | reveal, announce |
| utilize | use |

Orange tier (flag when 2+ land in the same paragraph): `comprehend`, `surpass`, `necessitate`, `emphasize`, `advocate`, `aggregate`, `align`, `amplify`, `benchmark`, `bridge`, `calibrate`, `differentiate`, `distill`, `elaborate`, `empower`, `enable`, `evaluate`, `evolve`, `formulate`, `mediate`, `orchestrate`, `reconcile`, `delineate`, `encapsulate`, `grapple`, `pinpoint`, `unravel`, `revitalize`.

Yellow tier (flag at density only): `blend`, `discern`, `emulate`, `interpret`, `ponder`, `scaffold`, `scrutinize`, `juxtapose`, `personalize`.

## Signature nouns

| Term | Replace with |
|---|---|
| tapestry | (describe the actual complexity, or cut the metaphor) |
| realm | area, field |
| intricacies | details, complexities (name the specific ones) |
| beacon | (rewrite; name what it actually signals) |
| confluence | combination, meeting point |
| continuum | range, spectrum |
| cornerstone | foundation, basis |
| crucible | testing ground (or name the actual pressure) |
| ecosystem | system, market, community |
| fabric | structure, makeup (name the actual thing) |
| facet | part, aspect |
| frontier | edge, new area |
| impetus | reason, driver |
| interplay | relationship, interaction |
| kaleidoscope | mix, variety (name the actual elements) |
| labyrinth | maze (or name the actual complexity) |
| modality | method, mode, way |
| mosaic | mix, blend (name the actual pieces) |
| nexus | hub, center, link |
| paradigm | model, approach |
| symphony | (describe the actual coordination) |
| synergy | combined effect (describe it) |
| testament | proof, evidence |
| touchpoint | contact point, interaction |
| treasure trove | (name specifically what's valuable) |
| landscape *(metaphor sense, "the publishing landscape")* | field, space, industry (literal terrain/software-landscape senses are fine) |

Orange tier (flag when 2+ land in the same paragraph): `advancements`, `reliance`, `catalyst`, `construct`, `discourse`, `domain`, `ethos`, `framework`, `horizon`, `iteration`, `matrix`, `mechanism`, `narrative`, `schema`, `spectrum`, `trajectory`, `interconnectedness`.

Yellow tier (flag at density only): `findings`, `potential`, `inquiry`.

## Signature adjectives and adverbs

| Term | Replace with |
|---|---|
| multifaceted | (name the actual facets, or cut) |
| pivotal | important, key |
| robust | strong, reliable |
| boundless | unlimited, endless (or cite scope) |
| bustling | busy, active (or cite what makes it busy) |
| captivating | (say why it holds attention) |
| commendable | good, worth noting (say why) |
| comprehensive | thorough, complete |
| cutting-edge | newest, latest |
| daunting | hard, difficult |
| ever-changing | changing (describe how) |
| ever-evolving | changing, growing |
| expansive | large, wide-ranging |
| fast-paced | quick, busy |
| futuristic | advanced (describe what specifically) |
| game-changing | (say what specifically changed) |
| groundbreaking | new, first-of-its-kind (name the precedent broken) |
| holistic | complete, full |
| immersive | engaging (describe how) |
| innovative | new (describe what's new) |
| integral | essential, necessary |
| intricate | complex, detailed |
| intrinsic | inherent, built-in |
| iterative | repeated, step-by-step |
| limitless | unlimited (or cite the actual bound) |
| meticulous | careful, detailed |
| monumental | huge, major (cite scale) |
| next-level | better (say how) |
| profound | deep, significant (say why) |
| quintessential | typical, classic |
| renowned | well-known (name who knows them) |
| resilient | tough, durable (or cite what it withstood) |
| revolutionary | new (name the precedent it breaks) |
| scalable | able to grow (describe how and to what) |
| seamless | smooth, easy |
| state-of-the-art | newest, most advanced |
| timeless | lasting (or cite how long) |
| transformative | (describe what changed and how) |
| unparalleled | unmatched (cite the comparison) |
| unprecedented | first of its kind (name the precedent it breaks) |
| vibrant | lively, active (or cite specifics) |
| visionary | forward-thinking (name the vision) |
| world-class | top-tier (cite a benchmark) |
| burgeoning | growing, emerging (cite a number) |
| nuanced | specific, subtle (name the actual nuance) |

Orange tier (flag when 2+ land in the same paragraph): `adaptive`, `compelling`, `crucial`, `dynamic`, `enduring`, `essential`, `keen`, `rapidly`, `vital`, `poised`, `uncharted`, `genuinely`.

Yellow tier (flag at density only): `proactive`, `markedly`, `synergistically`, `pioneering`, `firsthand`, `introspective`, `swiftly`.

## Phrase groups

These are multi-word phrases, grouped by register. Fix by cutting the phrase or replacing it with the plain, specific claim it's standing in for. "A testament to X's success" becomes "X sold 40,000 copies," not a shorter version of the same vagueness.

### Marketing & hype phrases

- **red**: `embark on a journey`, `holistic approach`, `unwavering commitment`, `a testament to`, `actionable insights`, `best practices`, `best-in-class`, `bridging the gap between`, `built for tomorrow`, `crafted with precision`, `designed to enhance`, `drive innovation`, `driven by innovation`, `empowering the next generation`, `end-to-end`, `engineered for excellence`, `fueled by passion`, `game changer`, `harness the power of`, `inflection point`, `next-generation`, `paradigm shift`, `pushing the boundaries of`, `redefining what's possible`, `revolutionizing the way we`, `scalable solution`, `seamlessly integrated`, `shaping the future`, `take a deep dive into`, `the intersection of`, `unleash your potential`, `unlock the power of`, `unlock the secrets`, `where innovation meets`
- **orange**: `supercharge`, `stay ahead of the curve`, `future-proof`, `drive meaningful impact`, `demystify`
- **yellow**: `forward-thinking`, `leading the charge`

### Stock phrases & transitions

- **red**: `it's important to note`, `it's worth noting`, `valuable insights`, `as we've seen`, `at its core`, `from a broader perspective`, `here's the thing`, `in essence`, `in light of`, `in the realm of`, `in this context`, `it is important to understand`, `it should be noted`, `needless to say`, `on the other hand`, `that being said`, `when it comes to`, `with that in mind`
- **orange**: `additionally`, `alternatively`, `consequently`, `essentially`, `firstly`, `furthermore`, `importantly`, `indeed`, `moreover`, `nonetheless`, `notably`, `similarly`, `diverse array`, `in summary`, `but here's where it gets interesting`, `what does this mean for you?`
- **yellow**: `focal point`, `that's only half the story`

### Business idioms & filler

- **red**: `a gateway to`, `at the forefront of`, `bring to the table`, `in a nutshell`, `low-hanging fruit`, `move the needle`, `take it to the next level`, `think outside the box`, `thought leader`, `when all is said and done`
- **orange**: `boil the ocean`, `circle back`, `double down on`, `hit the ground running`, `on the same page`, `signal vs noise`, `the bottom line is`, `touch base`
- **yellow**: `playbook`, `win-win`, `best of both worlds`, `does the heavy lifting`

### Tourism-brochure vocabulary

Overused for places, but also creeps into product/company descriptions ("nestled in the SaaS space").

- **red**: `a feast for the senses`, `breathtaking`, `charming`, `deeply rooted`, `enduring legacy`, `hidden gem`, `lasting legacy`, `leaves a lasting impression`, `must-see`, `must-visit`, `nestled`, `picturesque`, `profound heritage`, `rich cultural heritage`, `rich history`, `rich tapestry`, `steadfast dedication`, `stunning natural beauty`, `vibrant culture`
- **orange**: `in the heart of`

### Academic-register tells

- **red**: `a growing body of research`, `has garnered significant attention`, `paving the way for`, `sheds light on`, `open new avenues`
- **orange**: `a nuanced understanding`, `generalizability`, `a wide range of`, `further research is needed`, `in recent years`, `it is worth mentioning`, `remains to be seen`, `the present study`, `to the best of our knowledge`, `noteworthy`, `laudable`, `amidst`
- **yellow**: `aims to`, `cogent`, `admirable`, `prevalent`, `akin`

### Significance-inflation formulas

The move: turn a routine event into a historic one without evidence. If the sentence still works after deleting the inflation clause, delete it.

- **red**: `left an indelible mark`, `cements its status`, `continues to captivate`, `contributes to the broader`, `highlights the importance of`, `holds the distinction of`, `is a testament to`, `leaves a lasting impact`, `marks a significant shift`, `marks a turning point`, `plays a crucial role`, `plays a pivotal role`, `plays a significant role`, `plays a vital role`, `reflects a broader`, `represents a paradigm shift`, `serves as a reminder`, `serves as a testament`, `sets the stage for`, `solidifies its position as`, `stands as a testament to`, `underscores its importance`, `underscores the need for`, `a stark reminder`
- **orange**: `watershed moment`

### Vague-landscape / "in today's" openers

- **red**: `as businesses navigate the evolving`, `as the world becomes increasingly`, `in an age of`, `in an ever-changing landscape`, `in an ever-evolving world`, `in the era of`, `in the modern era`, `in today's competitive environment`, `in today's digital age`, `in today's fast-paced world`, `in today's rapidly evolving landscape`, `more than ever before`, `now more than ever`, `with the rise of`
- **orange**: `as technology continues to evolve`

### Hedges & qualifiers

- **red**: `it depends on various factors`, `there are several considerations`, `this is a complex topic with no single answer`
- **orange**: hedge-stacked predictions ("could potentially," "might eventually"; either word alone is fine, the stack is the tell), `arguably`, `broadly speaking`, `generally speaking`, `in many cases`, `it could be argued`, `it's worth mentioning`, `results may vary`, `to some extent`, `while this may vary`, `I feel like`
- **yellow**: `tends to`, `whilst`

### Connective / transition phrases

- **red**: `a key takeaway is`, `food for thought`, `last but not least`, `let's unpack`, `speaks volumes`, `this highlights the fact that`, `this underscores the importance of`, `to put it simply`
- **orange**: `first and foremost`, `in addition`, `more importantly`, `moving forward`, `on a larger scale`, `simply put`, `the reality is`, `when you zoom out`
- **yellow**: `at the same time`, `in other words`

### Conversational openers & closers

- **red**: `Absolutely!`, `As we move forward`, `At the end of the day`, `Certainly!`, `Feel free to reach out`, `Great question!`, `Happy [verb]-ing!`, `I hope this helps! Let me know if you have any questions`, `I'd be happy to help`, `Imagine a world where`, `In conclusion`, `Let me break this down for you`, `Only time will tell`, `Picture this:`, `That's a really interesting point.`, `The key takeaway here is`, `The possibilities are endless`, `To sum up`, `Ultimately the choice is yours`, `You raise a valid concern.`
- **orange**: `Without further ado`, `There you have it`, `Let's face it`

### Encyclopedia & bio slop

- **red**: `active social media presence`
- **orange**: `notable figures`, `coverage in local and national media outlets`
- **yellow**: `independent coverage`

### Email slop

- **red**: `don't hesitate to reach out`, `I hope this email finds you well`, `I hope this message finds you well`, `I hope you're doing well`, `I trust this email finds you well`, `I wanted to reach out`, `I'm reaching out because`
- **orange**: `as per our conversation`, `at your earliest convenience`, `just following up`, `looking forward to hearing from you`, `per my last email`, `thank you for reaching out`, `rest assured`
- **yellow**: `should you have any questions`

### Social / LinkedIn slop

- **red**: `Agree?`, `And honestly? That's okay.`, `Here's why that matters:`, `I'll say it louder for the people in the back`, `Let that sink in`, `Let's dive in 🧵`, `Read that again`, `Thoughts?`
- **orange**: social endorsement / CTA closers ("thank me later," "bookmark this," "don't sleep on this"; generic, could sit under any link, so say what the thing is and who it's for instead), `Hot take:`, `Let's normalize`, `Plot twist:`, `The result?`, `This is everything`, `Unpopular opinion:`
- **yellow**: `Thrilled to announce`, `Real talk`
