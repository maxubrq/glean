# Glean

**A reading app for the part that stays with you.**

> *glean* (v.) — to gather what is worth keeping from a large field, slowly, after the harvest.
> *gleanings* (n.) — the passages a reader collects while reading. The ancestor of the commonplace book.

---

Most document readers are judged on how well they turn pages. That is table stakes. Apple Books and Kindle already won there, and they won at a scale no one is going to out-render.

Glean is built on a different bet: a book is not the pages, it is **what you take out of it**. The reading is the easy part. Keeping it — being changed by it — is the part every reader has quietly abandoned. That is the part Glean is for.

So Glean does the rendering well enough to disappear, and spends its real effort on the layer above it: the highlight that survives, the note that comes back to you, the library that says something about who you are.

## What it does

**Reads what you actually have.** EPUB and PDF first, with MOBI/FB2/CBZ to follow. Fixed-layout (PDF) and reflowable (EPUB) are two genuinely different problems; Glean unifies them behind a single format-agnostic position model so everything above — navigation, bookmarks, highlights, sync — never has to care which one it's looking at.

**Reads without friction.** Instant open even on large files, no white flash on page turn, typography you can sit with for two hours, sensible defaults plus full control over font / margin / theme without breaking the publisher's intent. None of this is a feature you'll be thanked for. All of it is a feature you'd complain about if it were missing. That's the bar.

**Keeps what's worth keeping.** Highlights and notes are first-class, durable objects — anchored so precisely that they stay attached to the exact sentence even after you change the font size and the whole book reflows underneath them. This is the hardest engineering problem in the app, and it is load-bearing: everything that makes Glean more than a reader is built on top of robust anchoring.

**Brings it back.** Your highlights don't go to a graveyard. They resurface — a review surface, spaced over time — so that reading turns into retention instead of nice-feeling amnesia. A modern commonplace book that does the remembering for you.

**Reflects who's reading.** Your library and your gleanings are yours to shape and, when you want, to share — not as an app review, but as an expression of what you read and how you think.

## Architecture

Glean is a **Tauri** desktop app: a Rust core, a Svelte front end, one native WebView.

```
┌─────────────────────────────────────────────┐
│  WebView  (Svelte)                            │
│  · EPUB rendering — it's a browser, let it    │
│    be one (foliate-js + a user-override CSS   │
│    layer over the publisher's styles)         │
│  · Reader chrome, library, settings           │
├─────────────────────────────────────────────┤
│  Position layer  (format-agnostic Locator)    │
│  · PDF → page coordinates                     │
│  · EPUB → CFI (a path into the DOM)           │
│  · Everything above speaks Locator, nothing   │
│    above knows the format                     │
├─────────────────────────────────────────────┤
│  Rust core                                    │
│  · OPF / spine parsing                        │
│  · PDF rasterization (pdfium-render / mupdf)  │
│  · Full-text search indexing                  │
│  · Storage: reading state + annotations       │
│    + review schedule                          │
└─────────────────────────────────────────────┘
```

Two principles hold the design together:

1. **A single position model.** Borrowed from the Readium ecosystem: a `Locator` is one format-agnostic pointer into content. Get this right at the start and everything above it stays clean. Get it wrong and you write format-specific code in a hundred places.

2. **Heavy work goes to Rust.** Rasterizing PDF pages, indexing a book for search, persisting state — none of it touches the UI thread. Big files virtualize: render the current page and its neighbors, cache what's been rasterized, never decode the whole thing.

We stand on `foliate-js` rather than reinventing a rendering engine. The effort we save there is spent where it actually differentiates: anchoring, retention, and the reading-identity layer.

## Status

Early. This is a work in progress and the API/storage formats are not yet stable.

**Roadmap (rough):**

- [ ] EPUB reading — open, paginate, persist position
- [ ] PDF reading — rasterize, virtualize, search
- [ ] CFI-robust annotations — the substrate everything else needs
- [ ] Library + reading state
- [ ] Review / retention surface
- [ ] Shareable gleanings
- [ ] (later, watching) in-book AI — ask the book, recall across your library

## Building

> Prerequisites: Rust (stable), Node, and the Tauri toolchain.

```bash
# install deps
npm install

# run in dev
npm run tauri dev

# build a release bundle
npm run tauri build
```

## A note on scope

Glean only supports DRM-free books. Adobe DRM is a wall, and walking up to it is not how this app gets better. Bring your own EPUBs and PDFs.

---

*Built by Max · [maxubrq.space](https://maxubrq.space)*
