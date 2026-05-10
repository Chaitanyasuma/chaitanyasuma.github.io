# chaitanyasuma.github.io — Site Guide

## File structure

```
chaitanyasuma.github.io/
├── index.html          ← home page (card grid)
├── research.html       ← research areas, publications, projects
├── leadership.html     ← leadership & innovation (chronological)
├── blog.html           ← your blog (create this yourself, or link externally)
├── style.css           ← all shared styles — edit colors/fonts here
└── assets/
    └── images/         ← put all your photos here
        ├── hero.jpg
        ├── photo-1.jpg
        └── ...
```

> **No build step needed.** These are plain HTML files. Edit, push to GitHub, done.

---

## How to deploy

1. Make sure your repo is named exactly `chaitanyasuma.github.io`
2. Delete (or rename) any existing `index.md` — GitHub Pages serves `index.html` over it
3. Delete or keep `_config.yml` — it won't interfere with plain HTML
4. Push all files to the `main` branch:
   ```bash
   git add .
   git commit -m "redesign"
   git push origin main
   ```
5. Your site is live at `https://chaitanyasuma.github.io` within ~60 seconds

---

## How to add a photo to a card

Find the `<div class="card-img-slot">` placeholder inside the card. Replace the **entire** div with an `<img>` tag:

**Before:**
```html
<div class="card-img-slot">
  <div class="ph-icon">🖼</div>
  TODO: one of your landscape photos · 400 × 220px
</div>
```

**After:**
```html
<img src="assets/images/your-photo.jpg"
     alt="describe the photo"
     style="width:100%; border-radius:10px; height:200px; object-fit:cover;" />
```

For the **hero photo** (top of the intro card), replace `<div class="hero-photo-slot">...</div>` with:
```html
<img src="assets/images/hero.jpg"
     alt="hero"
     style="width:calc(100% + 4rem); margin:-2rem -2rem 0;
            border-radius:16px 16px 0 0; height:240px; object-fit:cover;" />
```

---

## How to add a new card (index.html)

1. Open `index.html` and find the `<div class="grid">` section
2. Copy any existing card block
3. Paste it where you want it in the grid (cards flow left-to-right, top-to-bottom)
4. Update the `class` for color and size (see tables below)

**Color classes:**
| Class        | Color          |
|-------------|----------------|
| `c-sage`    | green          |
| `c-mint`    | teal           |
| `c-yellow`  | yellow         |
| `c-peach`   | peach/coral    |
| `c-sky`     | sky blue       |
| `c-lavender`| purple         |
| `c-rose`    | pink           |
| `c-cream`   | warm gold      |
| `c-white`   | white + border |

**Size classes (combine with `card`):**
| Class   | Effect                     |
|---------|----------------------------|
| *(none)*| 1 column wide (default)    |
| `wide`  | 2 columns wide             |
| `full`  | 3 columns wide (full row)  |
| `tall`  | 2 rows tall                |

Example — a wide sky card:
```html
<div class="card wide c-sky">
  <div class="card-label">new section</div>
  <div class="card-title">Your <em>Title</em></div>
  <p class="card-body">Your description here.</p>
</div>
```

---

## How to make a card link somewhere

**Link to an internal page (research.html, leadership.html):**
Change the wrapping `<div class="card ...">` to `<a class="card ..." href="research.html">`. An arrow (→) appears automatically in the top-right corner.

```html
<!-- Before (non-clickable): -->
<div class="card c-sky">...</div>

<!-- After (links to research page): -->
<a class="card c-sky" href="research.html">...</a>
```

**Link to an external URL (Google Scholar, GitHub, etc.):**
Same as above, but add `target="_blank" rel="noopener"`:
```html
<a class="card c-cream" href="https://scholar.google.com/citations?user=YOUR_ID"
   target="_blank" rel="noopener">
  ...
</a>
```

**Link to a section on the same page (e.g. #connect):**
```html
<a class="card c-white" href="#connect">...</a>
```

---

## How to change card order

Cards are rendered in the order they appear in the HTML inside `<div class="grid">`. To reorder:
1. Select the entire card block (from `<!-- CARD: ... -->` comment to closing `</div>` or `</a>`)
2. Cut and paste it to the new position

Cards automatically reflow in the grid. The only caveat: a `wide` card at position 3 in a 3-column grid will start a new row — if you want it flush left, make sure it's the first card in its row (i.e., positions 1, 4, 7, 10…).

---

## How to add a new entry to research.html or leadership.html

Both pages use a simple `item-row` pattern. Copy this block and fill in your details:

```html
<div class="item-row">
  <div class="item-year">2024</div>
  <div>
    <div class="item-label">type · venue</div>
    <div class="item-title">Title of the thing</div>
    <p class="item-body">A short description of what this is and why it matters.</p>
    <div class="item-tags">
      <span class="item-tag">tag one</span>
      <span class="item-tag">tag two</span>
    </div>
    <!-- optional link: -->
    <a href="https://..." target="_blank" class="item-link">→ read more</a>
  </div>
</div>
```

Paste it **inside** the relevant `<div class="page-section">` block. Items appear in the order they're written — put newest first.

---

## How to add a new page (e.g. blog.html)

1. Create a new file, e.g. `blog.html`
2. Start with this shell (copy from any existing page header):

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Blog — Chaitanyasuma Jain</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,400;1,9..144,300;1,9..144,400&family=DM+Sans:wght@300;400;500&family=Syne+Mono&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <!-- paste the shared <header>, <nav>, <div class="socials">, <div class="divider"> blocks here -->

  <div class="page-inner">
    <a href="index.html" class="page-back">← back to home</a>
    <!-- your content here using item-row blocks -->
  </div>

  <footer>© 2026 Chaitanyasuma Jain</footer>
</body>
</html>
```

3. Add it to the `<nav>` in **all pages** so the link appears everywhere:
```html
<a href="blog.html">blog</a>
```

---

## How to change colors or fonts

Open `style.css` and find the `:root` block at the top:

```css
:root {
  --bg:       #FDFCFA;   /* page background */
  --ink:      #1A1814;   /* main text color */
  --mid:      #5C574F;   /* secondary text */
  --border:   #DDD9D4;   /* dividers and borders */

  /* card colors — change any of these */
  --sage:     #A8D4A0;
  --mint:     #87C9BC;
  --yellow:   #F0D060;
  --peach:    #F0A882;
  --sky:      #88BBDA;
  --lavender: #B8A4D8;
  --rose:     #E898A4;
  --cream:    #F0D898;
}
```

To change a font, find the Google Fonts `<link>` in the `<head>` of any page, swap the family name, then update `font-family` references in `style.css`.

---

## Quick reference — what links where

| Nav item   | Destination              | Type          |
|------------|--------------------------|---------------|
| work       | `index.html#work`        | same-page anchor |
| research   | `research.html`          | internal page |
| projects   | `research.html`          | internal page |
| blog       | `blog.html`              | internal page |
| pursuits   | `index.html#pursuits`    | same-page anchor |
| leadership | `leadership.html`        | internal page |
| connect    | `index.html#connect`     | same-page anchor |

| Card               | Destination              |
|--------------------|--------------------------|
| Data Privacy       | `research.html`          |
| Data Visualisation | `research.html`          |
| Data Mining        | `research.html`          |
| Publications       | Google Scholar (external)|
| Leadership cards   | `leadership.html`        |
| Social links       | external URLs            |
