# Glean — Feature Map (SFIM T1 → T5)

Features classified by **mechanism of value**, not by size. The point of ordering this way is to know *where to spend*. The reading engine is table stakes; the reasons to use Glean live up at T4 and T5.

Legend: `[MVP]` ship-first · `[v1]` near-term · `[later]` deferred · `★` core differentiator

---

## T1 — Threshold · *complain if missing, no credit for having*

**Mechanism:** negative asymmetry. Absence is felt; presence is invisible.
**Investment strategy:** spend exactly enough to never be complained about. Over-investing here is wasted — you cannot out-T1 Apple Books. Stand on `foliate-js`; don't reinvent.

### Reading core
- `[MVP]` Open EPUB reliably — spine, OPF, embedded fonts, images, tables, footnotes
- `[MVP]` Open PDF reliably — fixed-layout, embedded fonts, vector + raster
- `[v1]` MOBI / AZW3 (Kindle exports), FB2
- `[later]` CBZ / CBR (comics), plain TXT, DjVu
- `[MVP]` Graceful failure — corrupt or malformed file reports clearly, never crashes
- `[MVP]` DRM detection — tell the user plainly, don't crash or pretend (DRM-free only by design)

### Navigation & state
- `[MVP]` Remember exact reading position per book; restore on reopen
- `[MVP]` Table of contents; jump to chapter / page
- `[MVP]` Back / forward through jumps (follow a footnote, return cleanly)
- `[MVP]` In-book search
- `[MVP]` Position / progress indicator (page, %, location)

### The "feel" that's secretly T1
- `[MVP]` **No white flash on page turn** — this one quietly marks amateur vs not
- `[MVP]` Fast cold open, even on a 500-page PDF (virtualize: render current + neighbors only)
- `[MVP]` Reflow for EPUB / pinch-zoom + fit modes for PDF
- `[MVP]` Dark mode that isn't blinding at night
- `[v1]` Sensible memory ceiling — never decode a whole large book into RAM

### Don't-lose-my-stuff
- `[MVP]` Durable local storage — annotations and state survive crashes, never corrupt
- `[MVP]` Fully offline / local-first
- `[v1]` Import: drag-drop, "open with", watched folder
- `[v1]` Cover thumbnails

### Accessibility (also T1 — its absence is a hard complaint)
- `[v1]` Screen-reader support, dynamic type, reduced-motion respect
- `[v1]` Keyboard shortcuts for everything core

---

## T2 — Proportional · *more is better, and users can name it*

**Mechanism:** linear utility. Users benchmark it ("faster than X", "searches my whole library").
**Investment strategy:** find the industry "good enough" threshold and clear it. Don't try to lead every dimension — leading PDF render speed by 8% wins nothing.

- `[MVP]` Render / rasterize latency (perceived speed of turning to a heavy page)
- `[v1]` Search scope: single book → **whole-library full-text search** ★
- `[v1]` Library scale — thousands of books without lag
- `[v1]` Typography control depth: font, size, line-height, margins, justification, hyphenation, letter/word spacing
- `[v1]` Theme depth: light / sepia / dark / true-black + custom
- `[v1]` Annotation richness: colors, tags, note length, types (quote / idea / question / disagree)
- `[v1]` Export fidelity & formats: Markdown, JSON, CSV, plain text
- `[v1]` Dictionary / translation coverage (offline dictionaries, language count)
- `[later]` Sync speed & reliability; number of devices
- `[later]` Battery efficiency, cold-start time (always worth a notch better)

---

## T3 — Delight · *unexpected positive, decays to T1*

**Mechanism:** positive expectation violation.
**Investment strategy:** intentional but not gaudy. Remember the migration law — most reader "delight" already decayed into T1 (page-curl was wow in 2010, now its absence is a complaint). Keep a *rotating portfolio*; don't bet differentiation here.

- `[v1]` Tap-to-define / translate inline, instant and beautiful ★
- `[v1]` "**8 minutes left in this chapter**" — estimates that learn your actual pace
- `[v1]` A genuinely lovely first-open typographic moment (margins, drop-cap, type that reads like print)
- `[v1]` Smart resume — "you left off mid-sentence" with the sentence shown
- `[v1]` Import a Kindle `clippings.txt` and watch years of old highlights pour in ★ *(huge first-run delight)*
- `[later]` Justification + hyphenation that genuinely looks typeset (Hyphenopoly)
- `[later]` Auto day/night by time or ambient light
- `[later]` Drag a highlight → an instantly beautiful share card *(bridges into T4)*
- `[later]` "On this day you read…" — a gentle resurfacing *(bridges into T5)*
- `[later]` Focus / immersive reading mode, optional ambient

---

## T4 — Symbolic · *says who the reader is* ★★

**Mechanism:** self-concept + social signaling. Users share **about themselves**, not to review the app. Communities form. This is where Apple Books and Kindle are almost empty — the open territory.
**Investment strategy:** design backward from *"who does this reader want to be?"* — never "what do they want to do?" Must be **authentic**; the moment it's fake (a badge everyone gets), readers see through it.

- `[later]` ★ **Glean Year in Reading** — deeper than a book count. Your *themes*, your intellectual arc, the sentences that defined your year. Made to be posted as identity, not as a Spotify-Wrapped clone.
- `[later]` ★ **The Commonplace Book** as a shareable artifact — your gleanings collected into something beautiful enough to actually publish. The product's namesake, made visible.
- `[later]` ★ **Shareable highlight cards** — quote + *your note* + attribution. The note is the point: you're showing how you think, not recommending an app.
- `[later]` **Public shelf as a statement** — a curated, designed library page; a *tuyên ngôn* of what you read. ("This is the reader I am.")
- `[later]` **Taste fingerprint** — an honest, derived portrait of *what and how* you read (depth, breadth, where you linger). Reflected back, never imposed.
- `[later]` **Your annotation style becomes yours** — color system, symbols, marginalia voice that feels like a signature.
- `[later]` **Currently-reading status** worth putting in a bio.
- `[later]` **Shared marginalia** — opt-in, see others' gleanings on the same book; communities around a text, not around the app. *(Hypothesis / Genius, but tasteful.)*

> ⚠️ **The T4 boundary:** authentic reflects real behavior; manipulative manufactures it. Test: if every user knew everyone got the same thing, would they still share it? If no → it isn't real T4.

---

## T5 — Transformative · *changes how you read & remember, for good* ★★★

**Mechanism:** behavioral schema change. The user is a different reader afterward — outside the app. Irreversible (you can't un-learn it). This is the deepest bet, and the one that makes Glean a *tool for thinking* rather than a viewer.
**Investment strategy:** can't be designed directly. Ask: *"what job in the reader's life is being done badly — or not at all?"* Answer: **highlight-and-forget.** People mark the best sentences and never see them again. Solve that completely.

- `[later]` ★ **Spaced-repetition resurfacing** — your highlights come back on a schedule. The commonplace book that does the remembering *for* you. Reading stops being amnesia.
- `[later]` ★ **Daily review surface** — a handful of past gleanings each day; reading *compounds* instead of evaporating.
- `[later]` ★ **The Connections engine** — while reading book B, Glean surfaces a highlight from book A because they rhyme. Builds a personal web of ideas across everything you've read. *This changes how you synthesize* — the most genuinely transformative feature here.
- `[later]` **Highlight → active recall** — frictionless flashcards from your own marginalia, for the books you're actually studying.
- `[later]` **Progressive summarization** — layered highlighting that distills a book down over repeated passes (bold-of-the-bold).
- `[later]` ★ **Reading → writing loop** — gleanings flow into your own drafts. For a writer, reading becomes *raw material for creation*; the loop shifts from consume → create. *(Direct line to maxubrq.space.)*
- `[later]` **Behavior-changing analytics** — not vanity counts, but the kind that alter how you read: "you abandon books at ch. 3", "you retain far more when you write a note." Then you read differently.
- `[later]` ★ **Portable knowledge graph** — your gleanings export whole and outlive Glean. T5 is bound to *behavior, not product*: the transformation travels with you even if you leave. *(The BlackBerry-email rule — carry it to the next tool.)*

---

## T6 — Paradigmatic · *recognize, don't design for*

Not a build target — a watch list. Per SFIM, T6 is recognized and then doubled-down on fast, not designed up front.

- **AI-native reading** — *talk to the book*, query across your whole library, RAG over what you're reading and have read. The candidate to redefine "what a reader is for." Build the substrate (clean text + your annotations as context) so that **if** it becomes T6, you can move in days. Intersects directly with Sift.

---

## Suggested build order (you don't do this all at once)

1. **Prove the engine, earn the right to exist** — T1 reading core for EPUB + PDF, position memory, no-flash turns, durable storage.
2. **Build the substrate that everything depends on** — CFI-robust annotations. This is T1-looking work doing T4/T5-load-bearing duty. Do not cut corners here.
3. **First reason to switch** — Kindle-clippings import (T3 delight) + whole-library search (T2) → you instantly own a reader's *back catalog* of highlights.
4. **The retention layer** — daily review + spaced resurfacing (T5). This is the moat. The moment highlights stop dying, Glean is no longer "another reader."
5. **The identity layer** — shareable gleanings, the commonplace book, Year in Reading (T4). This is the growth loop — people share *themselves*, and the app spreads.
6. **The Connections engine + reading→writing loop** (T5★) — the long-game depth that nothing else does well.
7. **Watch T6** — keep the AI substrate clean; pounce if the category shifts.

The discipline in one line: **steps 1 are admission; steps 4–6 are the product.**
