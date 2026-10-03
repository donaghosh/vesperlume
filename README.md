# Vesperlume

A static one-page site for a photography studio. No build step, no dependencies, no framework. One HTML file.

---

## Deploy to GitHub Pages

**1. Create the repository**

On GitHub, create a new public repo. Name it anything — `vesperlume` is fine.

**2. Add the files**

```
your-repo/
├── index.html
├── README.md
└── images/
    ├── 01.jpg
    ├── 02.jpg
    ├── 03.jpg
    ├── 04.jpg
    ├── 05.jpg
    ├── 06.jpg
    ├── 07.jpg
    └── portrait.jpg
```

Either drag them into the GitHub web uploader, or:

```bash
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
git push -u origin main
```

**3. Turn on Pages**

Repo → **Settings** → **Pages** → under *Source* choose **Deploy from a branch** → branch `main`, folder `/ (root)` → **Save**.

Live in about a minute at `https://YOUR-USERNAME.github.io/YOUR-REPO/`

---

## Use your own domain

**1.** Add a file called `CNAME` at the repo root containing one line, no `https://`:

```
vesperlume.com
```

**2.** At your domain registrar, create these DNS records:

| Type | Name | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | YOUR-USERNAME.github.io |

**3.** Back in Settings → Pages, enter the domain and tick **Enforce HTTPS** once the certificate is issued (usually under an hour).

---

## Adding your photographs

Drop your files into `images/` using the names above, or change the `src` paths in `index.html` to match your own filenames.

**Keep the aspect-ratio class on the wrapper.** Each image sits inside a `<div class="frame r-...">` — that class reserves the right shape so the page doesn't jump while images load:

| Class | Shape | Used for |
|---|---|---|
| `r-landscape` | 3:2 | Wide shots |
| `r-portrait` | 4:5 | Standard portraits |
| `r-tall` | 2:3 | Vertical frames |
| `r-square` | 1:1 | The three-up row |

**Before uploading, do this:** resize so the longest edge is about 2000px and export as JPEG at quality 80. A 6MB camera file will make the site crawl on mobile. Squoosh.app does this in the browser for free.

Also update each `alt` attribute to describe what's actually in the photograph. It matters for screen readers and for search.

---

## Changing the text

Everything is in `index.html`, in plain HTML. Search for what you want to change and type over it.

The pieces you'll almost certainly want to edit:

- **Line 8** — the `<title>`, which shows in the browser tab and search results
- **Hero headline** — inside `<h1>`
- **Studio section** — the three paragraphs about you
- **Commissions** — package names, descriptions, prices
- **Contact** — email, phone, Instagram handle

---

## Changing the look

All colours and type sit in the `:root` block at the top of the stylesheet:

```css
--paper:#F4F4F2;    /* page background */
--ink:#15171A;      /* main text */
--ink-soft:#5B6067; /* secondary text */
--deep:#1A1D20;     /* dark contact section */
```

Change them in one place and the whole page follows.

Typefaces are Instrument Serif (headings) and Jost (body), loaded from Google Fonts in the `<head>`. To swap them, change the font link and the `--serif` / `--sans` values.

---

## On the name

**Vesperlume** is a coined word — *vesper* (evening) plus *lume* (light). It was invented for this, which makes a conflicting claim less likely than a dictionary word would.

It does **not** mean it is clear to use. Before you print it on anything:

- Search the Indian trademark register at **ipindiaonline.gov.in/tmrpublicsearch**
- If you'll work internationally, check **WIPO Global Brand Database**
- Check the domain and the social handles are actually free
- For anything commercially serious, have a trademark attorney run a proper clearance search

Nothing here is legal advice.

---

## What's deliberately not included

No contact form — a static site can't process one. Use the `mailto:` link, or if you want a real form, Formspree and Netlify Forms both work with static hosting.

No analytics, no cookie banner, no tracking. Add Plausible or Fathom if you want numbers without a consent popup.

No lightbox or gallery JavaScript. The images are the page.

---

## About the images currently on the site

The site ships pointing at **picsum.photos** — a free image CDN. No account, no API key, no attribution required. The photographs are real and the crops are correct, so the layout looks finished straight away.

They are **random subject matter**, not wedding photography. They exist so you can see the design working, not to ship with.

### Swapping in proper free photographs

If you want wedding and portrait images rather than random ones, these three sites are genuinely free for commercial use with no attribution required:

| Site | Direct search |
|---|---|
| **Unsplash** | unsplash.com/s/photos/indian-wedding |
| **Pexels** | pexels.com/search/wedding%20photography |
| **Pixabay** | pixabay.com/images/search/wedding/ |

Useful search terms for this particular layout: *indian wedding*, *mehendi*, *candid wedding*, *window light portrait*, *wedding details*, *bride getting ready*.

Download eight, save them into `images/` as `01.jpg` through `07.jpg` plus `portrait.jpg`, then in `index.html` change each `src` from the picsum URL back to the local path:

```html
<!-- from -->
<img src="https://picsum.photos/seed/vl-ceremony/1500/1000" ...>

<!-- to -->
<img src="images/01.jpg" ...>
```

A copy of the file already wired for local images ships as `index-local.html` — rename it over `index.html` if you'd rather start there.

### What "free" actually means

Those images are still copyrighted. They're licensed permissively, which is different. In practice for a website you're fine, but two things are worth knowing:

**No model releases.** Unsplash and Pexels don't guarantee the people pictured signed anything. Fine for a site, a real exposure for paid advertising.

**You can't resell them as stock.** Using them in a design is allowed. Repackaging them as a downloadable image pack is not.

### The one that actually matters

If this is a working photography business, stock photographs in the portfolio aren't a licensing problem — they're a credibility problem. You'd be showing someone else's work to clients deciding whether to hire you, and reverse image search takes about four seconds.

Use them while you build. Replace every one before the site goes live under your name.
