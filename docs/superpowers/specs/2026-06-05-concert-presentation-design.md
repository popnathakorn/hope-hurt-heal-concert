# Design Spec: Hope Hurt Heal Concert Presentation

**Date:** 2026-06-05
**Project:** Kangwan Singers — Hope Hurt Heal Annual Concert
**Output:** `public/index.html`

---

## Overview

A self-contained HTML slide deck presenting the post-concert audience feedback analysis for the Kangwan Singers' "Hope Hurt Heal" concert. The deck is projected on a shared screen at Post-Concert Meeting No. 5 (5 June 2026). One presenter drives navigation; the audience watches.

Source data: `audience-feedback-analysis.md` (68 survey responses, structured analysis across 3 agenda sections).

---

## Format & Delivery

- **Format:** Click-through slide deck — one topic per slide, linear flow
- **Delivery:** Projected on screen; single presenter controls navigation
- **File:** Single self-contained `public/index.html` — no CDN, no server, no external dependencies
- **Browser:** Opens directly from the filesystem (`file://`)

---

## Slide Structure — 31 slides

| # | Slide | Source |
|---|---|---|
| 1 | Title slide — "Hope · Hurt · Heal", concert date, Kangwan Singers logo | — |
| 2 | Agenda overview — §1.1 / §1.2 / §1.3 with clickable jump links | — |
| 3 | **§ 1.1 Section card** — Audience Feedback & Evaluation | — |
| 4 | Overall Ratings (out of 5), 68 responses | Q5–Q10 overall table |
| 5 | Ratings by Attendance History | Q5–Q10 × attendance cross-tab |
| 6 | Ratings by Choir Background | Q5–Q10 × choir cross-tab |
| 7 | Favourite Songs — overall ranking | Q11 overall |
| 8 | Favourite Songs by Attendance History | Q11 × attendance |
| 9 | Favourite Songs by Choir Background | Q11 × choir |
| 10 | Most Impressive Performance — overall | Q12 overall |
| 11 | Most Impressive Performance by Attendance History | Q12 × attendance |
| 12 | Most Impressive Performance by Choir Background | Q12 × choir |
| 13 | Concert Expectations (Q13) — overall | Q13 overall |
| 14 | Concert Expectations by Attendance History | Q13 × attendance |
| 15 | Concert Expectations by Choir Background | Q13 × choir |
| 16 | Genre Preferences (Q14) — overall | Q14 overall |
| 17 | Genre Preferences by Attendance History | Q14 × attendance |
| 18 | Genre Preferences by Choir Background | Q14 × choir |
| 19 | **§ 1.2 Section card** — Reflections on Performance | — |
| 20 | What the Audience Loved Most — themes + representative quotes | Q15 themes |
| 21 | What Loved Most by Attendance History | Q15 × attendance |
| 22 | What Loved Most by Choir Background | Q15 × choir |
| 23 | Messages to Members — tone summary + selected quotes | Q18 |
| 24 | Messages to Members by Attendance History | Q18 × attendance |
| 25 | Messages to Members by Choir Background | Q18 × choir |
| 26 | **§ 1.3 Section card** — Lessons Learned & Post-Concert Review | — |
| 27 | Areas for Improvement — themes + representative quotes | Q16 themes |
| 28 | Areas for Improvement by Attendance History | Q16 × attendance |
| 29 | Areas for Improvement by Choir Background | Q16 × choir |
| 30 | Future Wishes — themes | Q17 themes |
| 31 | Future Wishes by Attendance History | Q17 × attendance |
| 32 | Future Wishes by Choir Background | Q17 × choir |
| 33 | Audience Profile — attendance history + choir background breakdown | Profile tables |

---

## Navigation & Interaction

- **Keyboard:** left/right arrow keys; spacebar advances forward
- **On-screen buttons:** `◀ PREV` and `NEXT ▶` always visible at bottom of every slide — large enough to click comfortably from across a table
- **Slide counter:** `n / 33` displayed bottom-center
- **Section jump:** agenda items on slide 2 are clickable links that jump directly to the corresponding section title card (slides 3, 19, 24)
- **No transitions or animations:** instant slide swap — nothing to stall or flicker on a projector
- **Cross-tab slides:** fully static; each breakdown is its own slide

---

## Visual Design

### Colour Palette (from Kangwan Singers logo)

| Token | Value | Usage |
|---|---|---|
| `--bg-dark` | `#1a0008` | Slide background (corners) |
| `--bg-mid` | `#4a0018` | Slide background (centre of radial gradient) |
| `--gold` | `#c8921e` | Section labels, callout borders, cross-tab header accent |
| `--gold-light` | `#e8c060` | Slide titles, highlighted data values |
| `--text` | `#f5e8c8` | Body text, table rows |
| `--panel` | `#2d0010` | Table/card backgrounds |
| `--row-alt` | `#221008` | Alternating table row tint |
| `--muted` | `#a07040` | Secondary text, source labels |

Background: radial gradient from `--bg-mid` at centre to `--bg-dark` at edges, matching the logo backdrop.

### Typography

- **Slide titles:** `Georgia, serif` — matches the concert's classical feel
- **Section labels:** uppercase, letter-spaced, `--gold`, small size
- **Table data:** system sans-serif (`-apple-system, Segoe UI, sans-serif`) — readable at projection size
- **Minimum font size in tables:** 13px (legible at projector distance)

### Slide Layout

- **Title slide:** logo centred top-half; concert name below in large gold serif; date and "Audience Feedback Analysis" subtitle
- **Section title cards:** full-bleed gradient, large gold section number (`§ 1.1`), section title below — acts as a visual chapter break
- **Data slides:** section label (small caps, gold) top-left; slide title (serif, gold-light) below; table or content fills the centre; key insight callout at the bottom (left-bordered in `--gold`, italic cream text)
- **Agenda slide:** three clickable cards, one per section, gold-bordered on dark panel

### Logo

`logojpg.jpg` used on the title slide only, top-centre, at ~160px width.

---

## File Structure

```
public/
  index.html       # Single self-contained slide deck (all HTML + CSS + JS inline)

logojpg.jpg        # Logo — referenced as ../logojpg.jpg from public/index.html
```

The logo sits one directory above `public/`, so the reference path is `../logojpg.jpg`. This works when serving from the project root or opening `public/index.html` directly from the filesystem.

---

## Out of Scope

- No speaker notes mode
- No print/PDF export
- No animations or slide transitions
- No dark/light mode toggle
- No mobile layout (projector use only)
