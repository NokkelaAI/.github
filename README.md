# `.github` — organisation profile of Nokkela.ai

This repository is the special `.github` repository of the GitHub organisation
[`NokkelaAI`](https://github.com/NokkelaAI). GitHub renders
[`profile/README.md`](profile/README.md) on the organisation's landing page — that file is the
introduction to the AI side of Nokkela, in English.

This is the **narrow** profile: it covers `nokkela.ai` and `nokkela.io` and the infrastructure
those two stand on. The full company introduction lives in two sibling organisations —
[`nokkela-it-concept-com`](https://github.com/nokkela-it-concept-com) in English and
[`nokkela-it-concept-gmbh`](https://github.com/nokkela-it-concept-gmbh) in German. All three are
kept in sync on the facts they share: legal identity, contact details, and the claim that the
company is NIS2- and ISO-27001-oriented rather than certified.

## Layout

```
.github/
├─ README.md                     # this file — only visible inside the repository
├─ SECURITY.md                   # org-wide default: security policy and contact
└─ profile/
   ├─ README.md                  # ← rendered at github.com/NokkelaAI
   └─ assets/
      ├─ banner.png              # hero: the AI edition of the brand card
      ├─ logo-mark.svg           # the "N" brand mark
      └─ services/
         ├─ nokkela-ai.png       ├─ nokkela-host.png
         └─ nokkela-io.png       └─ nokkela-cloud.png
```

Files placed here also act as organisation-wide defaults: any repository in the organisation
without its own `SECURITY.md` falls back to the one in this repository.

## Where the images come from

- `assets/banner.png` is the AI edition of the brand card: the same geometry as the Open Graph
  image of the hub website — rust rules 8 px, tile 168 px at 80/205, the same footer line — but
  with `Nokkela.ai` as the wordmark, set the way the site header sets it (name in the text tone,
  suffix in rust), and the tagline of the landing page. The wordmark is scaled up because a
  short one at the hub's size would leave the card half empty.
- `assets/services/*.png` are the **English** 1200×628 assets from the Nokkela ad image set.
  Their artwork is not a rebuild: each one embeds the real hero SVG of the matching landing
  page, rendered against that domain's live stylesheet. Headlines and sublines are taken from
  the page they link to, which is deliberate — a promise in the image that the target page does
  not keep costs quality score in advertising and credibility here.

The banner is built from the template next to the repositories (`_vorlagen/`, not part of this
repository):

```powershell
wsl python3 /mnt/c/Users/claude-app/Desktop/Claude/nokkela-github-profile/_vorlagen/build-banner.py
powershell -File _vorlagen\render-banner.ps1
```

Three files come out: this one, the German company banner, and an English one that exists purely
as calibration — it carries the same text as the real `og.png`, so its text bands have to land
on the original's. `render-banner.ps1` prints the bands of every render next to the original's;
if they drift, the font size, tracking or position is wrong. Then copy
`banner-ai-1200x630.png` over `profile/assets/banner.png`.

## Image URLs are absolute — and pinned

Images in `profile/README.md` are referenced as absolute
`https://raw.githubusercontent.com/NokkelaAI/.github/main/profile/assets/…` URLs rather than
relative paths. Relative paths are resolved against the repository, not against the organisation
page that renders the file, so absolute URLs are the reliable form here.

The trade-off: the organisation name and the branch name `main` are baked into every image URL.
**If the organisation is renamed or the default branch changes, every image link in
`profile/README.md` breaks** and has to be rewritten in one pass.

## Editing

Plain Markdown with a little HTML — GitHub allows `<table>`, `<img>`, `<a>`, `<sub>`,
`<details>` and alignment attributes, but strips `<style>`, so there is no CSS to lean on.

Three things to keep true when editing:

- **The technical claims come from the landing pages.** The comparison table, the model list and
  the answers under "Questions we get asked first" are the published wording of `nokkela.ai`.
  Changing them here without changing them there leaves two versions of the same promise.
- **Mind the two operating modes.** On-premise can run air-gapped; the hosted variant cannot.
  That distinction runs through the whole page and is the one readers check.
- **No claim beyond the website.** The company is NIS2- and ISO-27001-**oriented**, not
  certified; it publishes no customer numbers, revenue figures, references, awards or ratings.
  The legal identifiers (HRB 7780, EUID, D-U-N-S, VAT ID) must match the imprint exactly.

## Licence and marks

The texts, brand marks and images in this repository belong to Nokkela-IT-Concept GmbH and are
published here for the presentation of the company. They are not covered by an open-source
licence and are not free for reuse. This does not affect client software, which the company
hands over under the MIT licence.
