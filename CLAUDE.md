# Shani Cohen — personal academic website

Static site (plain HTML/CSS, no build step, no framework) served by GitHub Pages.

- **Live at:** https://www.shanicohen.org
- **Repo:** https://github.com/shanicn-art/shanicohen.org (branch `main`)
- **Files:** `index.html` (all content), `style.css`, `images/headshot.webp`

## How to publish a change

Edit the file, then:

```bash
git add -A && git commit -m "…" && git push
```

GitHub Pages rebuilds automatically; the change is live in **~1 minute**. Verify with a
cache-busting request rather than a plain curl:

```bash
curl -s "https://www.shanicohen.org/?cachebust=$RANDOM" | grep "some new text"
```

To preview locally before pushing:

```bash
python3 -m http.server 4321
```

## Content conventions

All content lives in `index.html`. Sections: intro, Research (Working Papers /
Published), Non-academic (Public writing / Podcast episodes).

**Public writing** — newest first. One `<p>` per piece; language links in square
brackets; publication and date in parentheses at the end:

```html
<p>Title of the piece [<a target="_blank" href="URL">Hebrew</a>] (Month Year, Publication)</p>
```

Some pieces have both languages: `[<a …>English</a>] [<a …>Hebrew</a>]`.
External links use `target="_blank"`.

**Papers** — each sits in a `<div class="paper">` with the title link, then a
`<ul class="click-reveal">` block holding the collapsible abstract. The +/− toggle is
pure CSS (a hidden checkbox), no JavaScript — keep that structure when adding a paper.

**LaTeX does not render here.** Shani often pastes abstracts straight from a paper.
Convert to HTML: `\textit{x}` / `\emph{x}` → `<em>x</em>`, `$…$` math → Unicode
characters or HTML. Ask if a conversion is ambiguous.

## Don't touch

- `CNAME` — holds `www.shanicohen.org`. Removing it un-registers the custom domain and
  takes the site down. (This happened once; it also broke HTTPS cert issuance.)
- DNS lives at Squarespace (domain registrar only — the website plan is cancelled).
  Apex `@` → GitHub's four A records; `www` → CNAME to `shanicn-art.github.io`.
- GitHub Pages settings, including Enforce HTTPS (on) and the Let's Encrypt cert.

## Design

Fonts: EB Garamond (body + headings, ~19.5px), Work Sans (nav, small-caps section
labels, "Abstract" toggles). Warm off-white background `#faf9f7`, terracotta accent
`#9d3b32`. No bold or italic in headings — emphasis comes from size and serif contrast.
