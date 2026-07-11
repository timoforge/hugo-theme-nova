<p align="center">
  <img src="images/tn.png" alt="Nova Theme" width="600">
</p>

<h1 align="center">Nova Theme</h1>

<p align="center">
  <em>A bilingual (CN/EN) Hugo blog theme — three-column Grid layout, clean and modern</em>
</p>

<p align="center">
  <a href="https://gohugo.io/">
    <img src="https://img.shields.io/badge/Hugo-%3E%3D0.146.0-ff4088?style=flat-square&logo=hugo&logoColor=white" alt="Hugo Version">
  </a>

  <a href="LICENSE">
    <img src="https://img.shields.io/badge/License-MIT-blue?style=flat-square" alt="License">
  </a>
  <a href="https://github.com/timoforge/hugo-theme-nova/releases">
    <img src="https://img.shields.io/badge/Release-v1.0.0-brightgreen?style=flat-square" alt="Release">
  </a>
</p>

<p align="center">
  <a href="#features">Features</a> ·
  <a href="#screenshots">Screenshots</a> ·
  <a href="#quick-start">Quick Start</a> ·
  <a href="#configuration">Configuration</a> ·
  <a href="#theme-architecture">Architecture</a> ·
  <a href="#customization">Customization</a>
</p>

> 📖 **中文版**请参阅 [README-zh.md](README-zh.md)

---

Nova is a feature-rich [Hugo](https://gohugo.io/) blog theme with a **three-column Grid layout** — left sidebar, main content, and right widgets panel. It inherits PaperMod's proven CSS variable system and dark/light mode switching, while completely rebuilding the layout and adding extensive customization.

Built for bilingual (Chinese/English) tech blogs.

---

## Features

- **Three-column Grid** — Left sidebar (250px) + Main content + Right sidebar (240px)
- **Homepage split** — Profile left / search + recent posts right
- **Responsive** — 3 breakpoints down to single column on mobile
- **Fuse.js search** — Real-time fuzzy search with keyboard navigation
- **Timeline archives** — Year-grouped with visual markers
- **Tag index** — A-Z grouping with Chinese pinyin sorting
- **Bilingual (CN/EN)** — Default Chinese, one-click switch, page-level language memory
- **Right sidebar widgets** — Dynamic greeting, site intro, daily quote, runtime counter
- **Dark/Light mode** — Auto switching
- **SEO** — JSON-LD structured data, RSS feeds

---

## Screenshots

| Page     | Layout                                            |
| -------- | ------------------------------------------------- |
| Home     | Left-right split: profile + search & recent posts |
| Article  | 3-col: sidebar + content + TOC                    |
| Archives | 3-col: timeline with year grouping                |
| Tags     | 3-col: A-Z index with pinyin sorting              |
| Search   | 3-col: search box + popular tags                  |
| Mobile   | Single column stacked                             |

---

## Quick Start

### Preview (clone & run)

```bash
git clone https://github.com/timoforge/hugo-theme-nova.git
cd hugo-theme-nova
hugo server -D
```

Open `http://localhost:1313/` — HelloWorld, search, archives, all ready.

### Install into your site

```bash
cd your-site
git submodule add https://github.com/timoforge/hugo-theme-nova themes/nova
```

In `hugo.toml`:

```toml
theme = 'nova'
defaultContentLanguage = 'zh'
```

Or copy the full example:

```bash
cp themes/nova/exampleSite/hugo.toml .
cp -r themes/nova/exampleSite/content/* content/
hugo server -D
```

> Set `[params] preferChineseHome = false` for English landing.
> Theme defaults in `config/_default/` — override as needed.

---

## Configuration

### Base Config

```toml
theme = 'nova'
defaultContentLanguage = 'zh'
hasCJKLanguage = true

[params]
  ShowReadingTime = true
  ShowToc = true
  ShowCodeCopyButtons = true
  defaultTheme = 'auto'
```

> Full configuration reference in [`config/_default/`](config/_default/).
> Set `[params] preferChineseHome = false` for English landing page.

---

## Theme Architecture

```
├── assets/
│   ├── css/
│   │   ├── core/              # PaperMod core CSS (vars, reset, media)
│   │   ├── common/            # PaperMod common styles
│   │   ├── includes/          # Chroma syntax highlighting
│   │   └── extended/          # ⭐ Custom CSS (5 files)
│   │       ├── sidebar.css    #   3-col Grid + sidebar + TOC
│   │       ├── custom.css     #   Homepage layout, nav, footer
│   │       ├── search.css     #   Search page styles
│   │       ├── tagcloud.css   #   Tag cloud styles
│   │       └── social-icons.css
│   └── js/
│       ├── fastsearch.js      # ⭐ Custom Fuse.js search implementation
│       ├── fuse.basic.min.js  # Fuse.js library
│       └── license.js
├── config/_default/           # Theme defaults (merged into sites)
├── exampleSite/               # ⭐ Demo site (content + config + static)
│   ├── hugo.toml
│   ├── content/
│   └── static/
├── i18n/                      # 46 language translations
├── layouts/
│   ├── partials/              # Template partials (Hugo 0.146+)
│   │   ├── sidebar_profile.html # ⭐ Sidebar
│   │   ├── right_sidebar.html # ⭐ Right widgets
│   │   ├── toc.html           # ⭐ TOC (always expanded + scroll highlight)
│   │   ├── head.html          # ⭐ <head> (CSS/JS pipeline, SEO)
│   │   ├── header.html        # ⭐ Nav bar
│   │   ├── footer.html        # ⭐ Footer (filing info)
│   │   ├── social_icons.html  # ⭐ Social icons
│   │   └── ...                # PaperMod original partials
│   ├── single.html            # ⭐ Article detail (3-col)
│   ├── list.html              # ⭐ Homepage + listing (split)
│   ├── archives.html          # ⭐ Timeline archives
│   ├── search.html            # ⭐ Search page
│   ├── taxonomy.html          # ⭐ Tag index (A-Z + pinyin)
│   ├── _default/term.html     # Tag detail page
│   └── posts/list.html        # Post list
├── images/
│   ├── screenshot.png         # Theme screenshot
│   └── tn.png                 # Thumbnail
├── archetypes/
├── hugo.toml                  # Local repo preview config
├── theme.toml                 # Theme metadata
├── README.md                  # Theme docs (EN)
├── README-zh.md               # Theme docs (ZH)
├── LICENSE                    # MIT License
└── go.mod                     # Go module
```

> ⭐ = Files modified or added compared to PaperMod

### Page Layout Reference

| Page                    | Layout           | Description                            |
| ----------------------- | ---------------- | -------------------------------------- |
| Home (`/`)              | Left-right split | Profile (left) + Search & recent posts |
| Article detail          | 3-column         | Sidebar + Content + TOC                |
| Post list (`/posts/`)   | 3-column         | Sidebar + Posts + Right sidebar        |
| Archives (`/archives/`) | 3-column         | Sidebar + Timeline + Right sidebar     |
| Search (`/search/`)     | 3-column         | Sidebar + Search + Right sidebar       |
| Tags (`/tags/`)         | 3-column         | Sidebar + Tag index + Right sidebar    |
| Tag detail              | 3-column         | Sidebar + Posts + Info panel           |

---

## Customization

### CSS Variables

PaperMod's CSS variable system ensures consistent theming:

```css
/* Core variables (PaperMod drives light/dark switching) */
color: var(--primary); /* Main / links */
color: var(--secondary); /* Secondary */
background: var(--bg); /* Page background */
background: var(--entry); /* Card background */
border-color: var(--border); /* Borders */
background: var(--tertiary); /* Hover background */
```

### Layout Variables

```css
:root {
  --sidebar-w: 250px; /* Left sidebar width */
  --toc-w: 240px; /* Right sidebar width */
  --top-offset: 6rem; /* Sticky position start */
  --gap-col: 2rem; /* Column gap */
  --avatar-size: 130px; /* Avatar size (desktop) */
  --avatar-size-mobile: 100px; /* Avatar size (mobile) */
}
```

### Content Writing

```yaml
---
title: "Article Title"
date: 2026-05-25T00:00:00+08:00
slug: "article-slug"
categories: ["Category"]
tags: ["tag1", "tag2"]
draft: false
---
```

**Bilingual articles**: Main file `xxx.md` (Chinese) + `xxx.en.md` (English), with matching `date` values.

---

## Changelog

- **v1.0.0** (2026-07-11) — Initial release: three-column Grid layout

---

## Contributing

Contributions are welcome!

1. Fork this repo
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Commit: `git commit -am 'Add my feature'`
4. Push: `git push origin feature/my-feature`
5. Open a Pull Request

---

## License

MIT License — see [LICENSE](LICENSE).

---

<p align="center">
  <sub>Tech · Product · Engineering · Growth · Long-termism</sub>
</p>
