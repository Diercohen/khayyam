# رباعیات خیام · Rubāʿiyāt of Omar Khayyām — Anki Deck

An open, ready‑to‑study **Anki deck** for memorizing **178 quatrains (رباعی) of Omar Khayyām** in the original Persian, based on the classic **Foroughi (فروغی)** edition.

Each quatrain is turned into a small set of spaced‑repetition cards that walk you from the first line to the whole poem, backed by a **Persian audio recitation** and a **Persian‑miniature illustration** for every rubāʿi.

> خیزید و خیز کنید ای رفیقان — این deck برای از بر کردن رباعیات خیام ساخته شده است.

---

## Table of Contents

- [What's in this repository](#whats-in-this-repository)
- [The Anki deck at a glance](#the-anki-deck-at-a-glance)
- [Inside the `.apkg`: notes, fields and cards](#inside-the-apkg-notes-fields-and-cards)
- [How the four cards teach you a quatrain](#how-the-four-cards-teach-you-a-quatrain)
- [Why this design helps you memorize](#why-this-design-helps-you-memorize)
- [Installing and studying](#installing-and-studying)
- [Rebuilding the deck from source](#rebuilding-the-deck-from-source)

---

## What's in this repository

| Path | Description |
| --- | --- |
| `Khayyam.apkg` | The complete, importable Anki package (deck + note type + all media). |
| `khayyam_foroughi_178.csv` | The source text: 178 quatrains, one per row, semicolon‑separated. |
| `images/` | 178 Persian‑miniature style illustrations (`khayyam-001.jpeg` … `khayyam-178.jpeg`). |
| `sound/` | 178 audio recitations (`khayyam-001.mp3` … `khayyam-178.mp3`), one per quatrain. |

The `.apkg` is self‑contained — you do **not** need the `images/` and `sound/` folders to study. Those folders (and the CSV) are the **source assets** used to build the package, kept in the repo so the deck can be regenerated or improved.

### The source data (`khayyam_foroughi_178.csv`)

The CSV carries an Anki import header and one row per quatrain:

```text
#separator:Semicolon
#html:false
#columns:FirstHemistich;SecondHemistich;ThirdHemistich;ForthHemistich;MetaData;Sound
برخیز بُتا، بیا ز بهر دل ما;حل کن به جمال خویشتن مشکل ما;یک کوزه شراب تا به هم نوش کنیم;زآن پیش که کوزه‌ها کنند از گِل ما;1;
```

A **rubāʿi** is a quatrain made of four **hemistichs** (مصرع), traditionally rhyming **A‑A‑b‑A**. The CSV mirrors this structure exactly:

- `FirstHemistich` … `ForthHemistich` — the four lines of the poem.
- `MetaData` — the quatrain's number (1–178), used as its reference label.
- `Sound` — audio slot (populated during build as `[sound:khayyam-XXX.mp3]`).

---

## The Anki deck at a glance

| Property | Value |
| --- | --- |
| Deck name | `Khayyam` |
| Note type | `Robayiat Khayyam - رباعیات خیام` |
| Notes (quatrains) | **178** |
| Cards | **712** (4 cards per note) |
| Fields per note | **7** |
| Bundled media | **357** files — 178 images + 178 recitations + 1 Persian font (`_vazir.ttf`) |
| Text direction | Right‑to‑left (RTL), Vazir font, responsive layout |

---

## Inside the `.apkg`: notes, fields and cards

An `.apkg` is a ZIP archive containing an SQLite collection plus the media. Every quatrain is stored as **one note** using the custom `Robayiat Khayyam` note type, which has these **7 fields**:

| # | Field | Example content | Purpose |
| --- | --- | --- | --- |
| 0 | `Image` | `<img src="khayyam-001.jpeg">` | The illustration shown on every card. |
| 1 | `MetaData` | `1` | Quatrain number / reference. |
| 2 | `FirstHemistich` | برخیز بُتا، بیا ز بهر دل ما | Line 1. |
| 3 | `SecondHemistich` | حل کن به جمال خویشتن مشکل ما | Line 2. |
| 4 | `ThirdHemistich` | یک کوزه شراب تا به هم نوش کنیم | Line 3. |
| 5 | `ForthHemistich` | زآن پیش که کوزه‌ها کنند از گِل ما | Line 4. |
| 6 | `Sound` | `[sound:khayyam-001.mp3]` | Full recitation of the quatrain. |

From each note, Anki generates **4 cards** (`Card 1`–`Card 4`). Cards 1–3 build the poem line by line; Card 4 reviews the whole quatrain with audio.

Each card is color‑coded so lines are easy to distinguish once revealed:

- Line 2 → **darkorange**
- Line 3 → **yellowgreen**
- Line 4 → **firebrick**

A `metadata` footer always shows *«رباعی شماره N»* so you know which quatrain you are on.

---

## How the four cards teach you a quatrain

The heart of this deck is a **progressive, line‑by‑line recall** method. Instead of trying to memorize four lines at once, you learn to produce **the next line given the previous ones** — the exact skill you use when reciting a poem from memory.

### Card 1 — recall line 2 from line 1

- **Front:** the illustration + line 1, with the prompt *«مصرع دوم این رباعی چیست؟»* (“What is the second hemistich?”).
- **Hint:** a clickable hint reveals the **first letter of each word** of the answer line — a memory nudge, not the full answer.
- **Back:** line 2 appears in orange.

### Card 2 — recall line 3 from lines 1–2

- **Front:** illustration + line 1 + line 2 (orange), prompt *«مصرع سوم این رباعی چیست؟»*.
- **Back:** line 3 in yellowgreen.

### Card 3 — recall line 4 (the punchline) from lines 1–3

- **Front:** illustration + lines 1–3, prompt *«مصرع آخر این رباعی چیست؟»*.
- **Back:** line 4 in red. In a rubāʿi the fourth line usually carries the twist or philosophical point, so it gets its own card.

### Card 4 — full recitation review with audio

- **Front:** illustration + a faded placeholder of line 1 (*«یادآوری کل رباعی 🔊»*) — your cue to recite the entire quatrain aloud.
- **Back:** all four lines together, color‑coded, followed by the **MP3 recitation** so you can check your pronunciation, rhythm (وزن), and rhyme.

### The first‑letter hint (how it works)

Cards 1–3 include a tiny script that takes the answer line, keeps only the **first character of every word**, and shows it on demand:

```js
const nextHint = nextHemistich
  .split(' ')
  .map((word) => word[0])
  .join(' ');
```

So a forgotten line surfaces as a skeleton of initials — enough to jog your memory without giving the answer away. This is a classic **retrieval‑practice** aid.

---

## Why this design helps you memorize

Memorizing classical poetry is hard because the lines are dense and the vocabulary archaic. This deck leans on several evidence‑based learning ideas:

- **Chunking + chaining.** Each card asks for exactly one new line given the context you already know. You build the quatrain as a chain (1→2→3→4), which is how the brain naturally stores sequences like songs and poems.
- **Active recall over re‑reading.** You are always *producing* the next line, not just recognizing it. Retrieval practice is far stronger for long‑term retention than passive review.
- **Graduated hints.** The first‑letter hint gives “desirable difficulty” — enough struggle to strengthen the memory, without the frustration of a total blank.
- **Multi‑modal encoding.** Every quatrain pairs **text + a unique illustration + audio**. The image acts as a visual anchor for the poem, and the recitation teaches correct **meter (وزن)** and pronunciation — three separate retrieval cues for one memory.
- **Spaced repetition.** Anki schedules each of the four cards independently, so the lines you find hard resurface more often than the ones you already know.
- **Recite‑the‑whole review (Card 4).** After the pieces are learned, Card 4 forces you to perform the complete poem from memory and self‑check against the audio — the real‑world goal of memorization.

The net effect: you don't just *recognize* Khayyām's quatrains — you can **recite all four lines from the first one**, with the right rhythm and rhyme.

---

## Installing and studying

1. Install [Anki](https://apps.ankiweb.net/) (desktop) or AnkiDroid / AnkiMobile.
2. Download `Khayyam.apkg` from this repository.
3. In Anki: **File → Import** (or just double‑click the file) and select `Khayyam.apkg`.
4. The deck `Khayyam` appears with all 712 cards and media ready to go.

Study tips:

- Read/recite **out loud** — the audio is there so you can match pronunciation and meter.
- Tap the hint on Cards 1–3 only after you've genuinely tried to recall the line.
- Treat Card 4 as a performance: recite the full quatrain before flipping, then compare with the recording.

---

## Rebuilding the deck from source

The deck can be regenerated from the assets in this repo:

- `khayyam_foroughi_178.csv` — the 178 quatrains (semicolon‑separated, columns as documented above).
- `images/khayyam-XXX.jpeg` — one illustration per quatrain.
- `sound/khayyam-XXX.mp3` — one recitation per quatrain.

To rebuild, create a note type with the 7 fields listed above and the 4 card templates (progressive recall + audio review), import the CSV, and attach the media by number (`khayyam-001` → quatrain 1, etc.). The bundled `_vazir.ttf` provides the Persian font used for the RTL layout.


This is a public, freely shareable study resource. If you improve the text, images, or audio, contributions are welcome via pull request.

> این مجموعه برای علاقه‌مندان به شعر فارسی و به‌ویژه رباعیات خیام آزادانه در دسترس است. خوش باشید. 🍷
