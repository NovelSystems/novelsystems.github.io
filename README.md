# novelsystems.me

Website for Novel Systems Engineering, LLC — an IP licensing and R&D firm specializing in polarimetric LiDAR sensor technology (DDR) for maritime search and rescue.

## Tech Stack

- [Hugo](https://gohugo.io/) static site generator, custom theme (`themes/novelsystems/`)
- Plain CSS — no frameworks (dark theme, EB Garamond typography)
- Hosted on GitHub Pages, deployed via GitHub Actions on push to `main`

---

## Running Locally

**Prerequisites:** Hugo installed ([installation guide](https://gohugo.io/installation/))

```bash
# Clone the repo
git clone https://github.com/novelsystems/novelsystems.github.io.git
cd novelsystems.github.io

# Start the dev server
hugo server
```

Site will be available at `http://localhost:1313`. Live-reloads on file save.

---

## Deploying

### GitHub Pages (automatic)

Push to `main`. The GitHub Actions workflow in `.github/workflows/deploy.yml` will:
1. Install Hugo
2. Run `hugo --minify`
3. Push the `public/` directory to the `gh-pages` branch
4. GitHub Pages serves from `gh-pages`

The custom domain (`novelsystems.me`) is configured via `static/CNAME`.

### Netlify

1. Connect the repository in the Netlify dashboard
2. Set build command: `hugo --minify`
3. Set publish directory: `public`
4. Set environment variable: `HUGO_VERSION=0.120.0` (or latest)
5. Add a custom domain in Netlify DNS settings

---

## Swapping In Real Assets

### Logo

Place your logo file at:

```
static/img/logo.png
```

The nav template (`themes/novelsystems/layouts/partials/nav.html`) already references `/img/logo.png`. If the image fails to load, it falls back gracefully to the text logo. The `onerror` attribute hides a broken image — text fallback is always visible alongside.

Recommended logo specs: PNG with transparent background, height ~36–48px at 1x (72–96px @2x), gold or white mark on transparent background.

### Diagrams

Two diagram placeholders appear on the homepage and technology page. Replace the `.diagram-placeholder` divs with real `<img>` tags when assets are ready:

| Placeholder caption | Suggested filename |
|---|---|
| System architecture diagram — FMCW dual-channel coherent receiver | `static/img/ddr-signal-architecture.svg` |
| 1D vs 2D phased array architecture — Yield and cost comparison | `static/img/phased-array-1d-vs-2d.svg` |

In each layout file (e.g. `themes/novelsystems/layouts/partials/tech-layers.html`), replace:

```html
<div class="diagram-placeholder">
  <div class="diagram-placeholder__icon">■</div>
  <p class="diagram-placeholder__caption">...</p>
</div>
```

with:

```html
<img src="/img/ddr-signal-architecture.svg" alt="DDR signal architecture diagram">
```

---

## Site Structure

```
hugo.toml                          # Site config, menu, params
content/
  _index.md                        # Homepage (no body content — layout drives it)
  technology/_index.md             # Technology page
  applications/_index.md           # Applications page
  ip-portfolio/_index.md           # IP Portfolio page
  about/_index.md                  # About page
data/
  domains.yaml                     # Application domain cards (homepage + applications)
  capabilities.yaml                # Capability tiles (homepage)
themes/novelsystems/
  layouts/
    _default/baseof.html           # Base HTML shell, nav/footer includes, JS
    index.html                     # Homepage (assembles partials)
    partials/
      nav.html                     # Sticky navigation with hamburger
      footer.html                  # Site footer
      hero.html                    # Full-viewport hero section
      origin.html                  # Origin / mission section
      domains.html                 # Application domain grid (reads data/domains.yaml)
      tech-layers.html             # Two alternating tech rows
      capabilities.html            # 4-up capability tile grid
      closing-cta.html             # Closing CTA section
    technology/list.html           # Technology inner page
    applications/list.html         # Applications inner page
    ip-portfolio/list.html         # IP Portfolio inner page
    about/list.html                # About inner page
  static/
    css/main.css                   # Single CSS file, plain CSS, dark theme
static/
  img/                             # Drop logo.png here
  favicon.ico
  CNAME                            # novelsystems.me
.github/
  workflows/deploy.yml             # GitHub Pages deploy workflow
```

---

## Color Reference

| Variable | Value | Usage |
|---|---|---|
| `--bg` | `#0a0a0a` | Page background |
| `--surface` | `#111111` | Card and section surface |
| `--text` | `#f0e6cc` | Primary text (warm cream) |
| `--text-mid` | `#b8a98a` | Body copy, secondary text |
| `--accent` | `#c9a044` | Gold accent, links, labels |
| `--hover` | `#d4b05a` | Hover state |
| `--border` | `#2a2318` | Dividers, card borders |

All typography uses **EB Garamond** (loaded from Google Fonts). No sans-serif is used anywhere on the site.
