# Design System Reference — pulled from `llm/index.html`

Source: [llm/index.html](llm/index.html) (homepage) + [llm/llm01/llm01-shared.css](llm/llm01/llm01-shared.css) (base design system loaded by every slide/page).

Use this as the starting point for **any** new project's homepage with the same layout:
top nav → hero → "Course Modules" card grid → about section → footer.

---

## 1. Full HTML structure (header, hero, module grid, footer)

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>{{Course Title}} · Interactive Course</title>
<meta name="description" content="{{meta description}}">
<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 64 64'%3E%3Crect width='64' height='64' rx='14' fill='%236d28d9'/%3E%3Ctext x='50%25' y='54%25' font-family='monospace' font-size='30' font-weight='bold' fill='%23fff' text-anchor='middle' dominant-baseline='middle'%3E%26lt;/%26gt;%3C/text%3E%3C/svg%3E">
<meta property="og:type" content="website">
<meta property="og:url" content="https://{{your-domain}}/">
<meta property="og:title" content="{{Course Title}}">
<meta property="og:description" content="{{longer description}}">
<meta property="og:image" content="https://{{your-domain}}/og-image.svg">
<meta name="twitter:image" content="https://{{your-domain}}/og-image.svg">
<meta name="twitter:card" content="summary">
<meta name="twitter:title" content="{{Course Title}}">
<meta name="twitter:description" content="{{short description}}">
<link rel="canonical" href="https://{{your-domain}}/">
<link rel="stylesheet" href="module01/module01-shared.css">
<style>
/* page-specific overrides — see section 2 below */
</style>
</head>
<body>

<div class="top-nav">
  <a href="../index.html" style="text-decoration:none;display:flex;align-items:center;gap:12px;">
    <span class="nav-badge" style="color:#ffffff;background:rgba(226,232,240,0.06);border-color:#e2e8f0;">{{your-domain}}</span>
    <span class="nav-title">{{Course Name}}</span>
  </a>
</div>

<div class="hero">
  <div class="hero-badge">&#x1F4A1; {{Topic}} · {{Category}} · {{Category}}</div>
  <div class="hero-title">Learn <span>{{Topic}}</span><br>by actually doing it.</div>
  <p class="hero-sub">An interactive, slide-by-slide breakdown of core {{Topic}} concepts. Built for anyone who learns differently.</p>
  <div class="hero-stats">
    <div class="stat"><div class="stat-num">1<span style="color:var(--muted);font-size:14px;">/10</span></div><div class="stat-label">Modules live</div></div>
    <div class="stat"><div class="stat-num">27</div><div class="stat-label">Slides</div></div>
    <div class="stat"><div class="stat-num">1</div><div class="stat-label">Quizzes</div></div>
  </div>
</div>

<div class="section-header">Course Modules</div>

<div class="card-grid">

  <div class="module-card available active">
    <div class="mod-top"><span class="mod-num">MOD01</span><span class="pill pill-ready">Live</span></div>
    <div class="mod-title">{{Module 1 Title}}</div>
    <div class="mod-desc">{{One-line description.}}</div>
    <div class="mod-footer"><span class="mod-slides">27 slides</span></div>
    <a class="mod-link" href="module01/module01-slide-01.html">Start →</a>
  </div>

  <!-- locked / not-yet-built module card -->
  <div class="module-card locked">
    <div class="mod-top"><span class="mod-num">MOD02</span><span class="pill pill-soon">Soon</span></div>
    <div class="mod-title">{{Module 2 Title}}</div>
    <div class="mod-desc">{{One-line description.}}</div>
    <div class="mod-footer"><span class="mod-slides">— slides</span></div>
  </div>

  <!-- …repeat one .module-card per module… -->

</div>

<!-- optional "about" panel — drop if not needed -->
<div class="about-section">
  <div class="about-label">About this course</div>
  <p class="about-text"><strong>{{Course Name}}</strong> is {{description}}.</p>
  <a class="about-link" href="about.html">Learn more →</a>
</div>

<div class="page-footer">
  <div class="footer-bottom">
    <span class="footer-copy">&copy; {{year}} {{your-name}} &middot; Built for learning, free to use.</span>
    <div class="footer-links">
      <a href="terms.html">&#x1F4DC; Terms &amp; Disclaimer</a>
      <a href="../legal-notice.html">&#x2696;&#xFE0F; Legal Notice</a>
    </div>
    <span class="footer-copy">Made with <span class="heart">&#x2665;</span> &amp; a lot of curiosity</span>
  </div>
</div>

</body>
</html>
```

**Notes on the module cards:**
- `.module-card.available.active` — the current/first module: solid border highlight.
- `.module-card.available` — a live, clickable module (has `.mod-link` button).
- `.module-card.locked` — not built yet: `opacity:.4`, no link, pill is `pill-soon` ("Soon") instead of `pill-ready` ("Live").
- Grid is responsive: 5 columns → 3 (≤1024px) → 2 (≤640px) → 1 (≤400px), see CSS below.

---

## 2. Logo, nav bar & footer — detailed breakdown

### 2.1 Logo / top-left brand mark

**To replicate this exact logo, paste this exact markup — nothing else is needed, no image file, no font file beyond the Google Fonts `@import` already in §4's CSS:**

```html
<div class="top-nav">
  <a href="../index.html" style="text-decoration:none;display:flex;align-items:center;gap:12px;">
    <span class="nav-badge" style="color:#ffffff;background:rgba(226,232,240,0.06);border-color:#e2e8f0;">evlbot.xyz</span>
    <span class="nav-title">OWASP LLM Top 10</span>
  </a>
</div>
```

That's the whole logo. Two text strings, two `<span>`s, one wrapping `<a>`. Nothing is an image.

**Exact spec, so it can be rebuilt with zero guessing:**

| Piece | Exact value |
|---|---|
| Link target | `href="../index.html"` — clicking anywhere in the logo (badge or title) navigates to the homepage one folder up. |
| Badge text | `evlbot.xyz` (literal string in the source) |
| Badge font | `'IBM Plex Mono', monospace` |
| Badge font-size | `10px` |
| Badge letter-spacing | `.12em`, `text-transform: uppercase` |
| Badge shape | `border-radius: 4px`, `padding: 3px 9px` |
| Badge text color | `#ffffff` |
| Badge background | `rgba(226,232,240,0.06)` |
| Badge border | `1px solid #e2e8f0` |
| Title text | `OWASP LLM Top 10` (literal string in the source) |
| Title font | inherited from `body` → `'IBM Plex Sans', sans-serif` (no override) |
| Title font-size | `13px` |
| Title color | `#a8b8c8` (i.e. `var(--subtle)`) |
| Gap between badge and title | `12px` (`gap:12px` on the `<a>`) |
| Wrapper bar (`.top-nav`) | `display:flex; align-items:center; justify-content:space-between; padding:14px 20px; border-bottom:1px solid #22222e; position:sticky; top:0; background:#0a0a0f; z-index:100;` |

To reuse for a different project: keep every property above identical, only change the two literal strings (`evlbot.xyz` and `OWASP LLM Top 10`) to your own brand text and site/course name — everything else (font, sizes, colors, spacing, the link-wraps-everything structure) stays exactly as specified to reproduce the same look.

- **The whole logo is a link** (`<a href="../index.html">`) — clicking the badge *or* the title text routes back to the homepage. No separate "logo image" — it's a styled text badge, not an `<img>`/SVG.
- **The badge** (`evlbot.xyz`):
  - Font: `IBM Plex Mono` (monospace), `font-size: 10px`, `letter-spacing: .12em`, `text-transform: uppercase`.
  - Shape: `border-radius: 4px`, `padding: 3px 9px`, `display:inline-flex`.
  - Color, **on the homepage specifically** (inline `style=` override): text `#ffffff` (white), background `rgba(226,232,240,0.06)` (near-transparent light gray), border `1px solid #e2e8f0` (light gray/white). This is a *deliberate override* of the default badge look.
  - **Default badge color** (used on every slide page instead, class `.nav-badge` with no inline override): text `var(--accent-bright)` = `#a78bfa` (light purple), background `var(--accent-glow)` = `rgba(109,40,217,0.10)`, border `1px solid var(--accent)` = `#6d28d9` (purple). So the homepage nav badge is intentionally neutral (white/gray) while every module page's badge is purple-accented.
- **The title text** (`OWASP LLM Top 10`, i.e. the course name next to the badge):
  - Class `.nav-title` — `font-size: 13px`, `color: var(--subtle)` = `#a8b8c8` (light gray-blue).
  - No `font-family` override on `.nav-title` itself, so it inherits the page body font: `'IBM Plex Sans', sans-serif`.
- **Container** (`.top-nav`): `display:flex; align-items:center; justify-content:space-between; padding:14px 20px; border-bottom:1px solid var(--border); position:sticky; top:0; background:var(--bg); z-index:100;` — it's a sticky bar pinned to the top while scrolling, with a 1px bottom border and the page background color (`#0a0a0f`) so it stays opaque over content.

**For a new project:** swap `evlbot.xyz` → your domain/brand text, and `OWASP LLM Top 10` → your project/course name. Keep the same `<a href="../index.html">` wrapper so it still routes home. Keep the white/gray override on the homepage badge and the purple default everywhere else, unless you want a different brand color (see §4).

### 2.2 Footer — detailed breakdown

```html
<div class="page-footer">
  <div class="footer-bottom">
    <span class="footer-copy">&copy; 2026 Susbot &middot; Built for learning, free to use.</span>
    <div class="footer-links">
      <a href="terms.html">&#x1F4DC; Terms &amp; Disclaimer</a>
      <a href="../legal-notice.html">&#x2696;&#xFE0F; Legal Notice</a>
    </div>
    <span class="footer-copy">Made with <span class="heart">&#x2665;</span> &amp; a lot of curiosity</span>
  </div>
</div>
```

Three pieces, laid out left-to-right in a flex row that wraps on small screens:

1. **Copyright line** — `© 2026 Susbot · Built for learning, free to use.`
   - Class `.footer-copy`: `font-size: 11px`, `color: var(--muted)` = `#8899a6` (muted gray), `line-height: 1.6`. Font-family inherited from body (`IBM Plex Sans`).
2. **The two links** — `📜 Terms & Disclaimer` and `⚖️ Legal Notice`, wrapped in `.footer-links` (`display:flex; flex-wrap:wrap; gap:8px`).
   - Each `<a>`: font `IBM Plex Mono`, `font-size: 10px`, `color: var(--subtle)` = `#a8b8c8`, `border: 1px solid var(--border)` = `#22222e`, `border-radius: 6px`, `padding: 6px 12px`, `display:inline-flex` with a small icon + text.
   - Hover state: `border-color: var(--accent)` (purple), `color: var(--accent-bright)` (light purple).
   - `Terms & Disclaimer` links to `terms.html` (same folder); `Legal Notice` links to `../legal-notice.html` (one level up — shared across the whole site, not per-course).
3. **"Made with ♥ & a lot of curiosity"** — same `.footer-copy` styling as the copyright line, except the heart:
   - `.heart` class on the `♥` character only: `color: #f43f5e` (red/pink) — the only colored element in the whole footer.

**Container-level styling** (`.page-footer`, homepage-specific override in the inline `<style>` block):
- `margin: 32px 20px 0; padding: 24px 0 32px; border-top: none; text-align: left;`
- `.footer-bottom`: `display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:10px; padding-top:16px; border-top:1px solid var(--border);` — this is what actually draws the top divider line above the footer content (the outer `.page-footer` explicitly sets `border-top:none` so only `.footer-bottom` draws it).

**For a new project:** swap `Susbot` → your name, `2026` → the current year, and keep both links — `Terms & Disclaimer` should point to a `terms.html` you write for the new project, `Legal Notice` can keep pointing to the shared `../legal-notice.html` if you want one legal page site-wide, or point to a project-specific one if you want it separate.

---

## 3. Homepage-specific inline `<style>` block (from `index.html`)

This is layered **on top of** the shared CSS (section 3) — it only styles homepage-only elements (hero, module grid, footer, about box). Copy verbatim; only the color/copy inside the HTML changes.

```css
html{background:var(--bg);}
body{padding-bottom:24px;}
.heart{color:#f43f5e;}
.hero{padding:40px 20px 32px;}
.hero-badge{display:inline-flex;align-items:center;gap:6px;font-family:'IBM Plex Mono',monospace;font-size:10px;letter-spacing:.12em;text-transform:uppercase;color:var(--accent-bright);background:var(--accent-glow);border:1px solid var(--accent);border-radius:4px;padding:3px 10px;margin-bottom:20px;}
.hero-title{font-size:clamp(24px,6vw,36px);font-weight:600;color:#fff;line-height:1.2;margin-bottom:10px;}
.hero-title span{color:var(--accent-bright);}
.hero-sub{font-size:16px;color:var(--subtle);line-height:1.75;max-width:540px;margin-bottom:28px;}
.hero-stats{display:flex;gap:24px;}
.stat{text-align:center;}
.stat-num{font-family:'IBM Plex Mono',monospace;font-size:22px;font-weight:600;color:var(--accent-bright);}
.stat-label{font-size:11px;color:var(--muted);margin-top:2px;}
.section-header{font-family:'IBM Plex Mono',monospace;font-size:9px;letter-spacing:.14em;text-transform:uppercase;color:var(--muted);padding:24px 20px 12px;border-top:1px solid var(--border);}
.card-grid{display:grid;grid-template-columns:repeat(5,1fr);gap:10px;padding:0 20px 24px;}
@media(max-width:1024px){.card-grid{grid-template-columns:repeat(3,1fr);}}
@media(max-width:640px){.card-grid{grid-template-columns:repeat(2,1fr);}}
@media(max-width:400px){.card-grid{grid-template-columns:1fr;}}
.module-card{background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:14px;transition:border-color .15s;display:flex;flex-direction:column;}
.module-card.available{cursor:pointer;}
.module-card.available:hover{border-color:var(--accent);}
.module-card.available.active{border-color:var(--accent-bright);}
.module-card.locked{opacity:.4;cursor:default;}
.mod-top{display:flex;align-items:center;justify-content:space-between;margin-bottom:10px;}
.mod-num{font-family:'IBM Plex Mono',monospace;font-size:9px;letter-spacing:.1em;color:var(--accent-bright);background:var(--accent-glow);border:1px solid var(--accent);border-radius:4px;padding:2px 7px;}
.mod-title{font-size:16px;font-weight:600;color:#fff;margin-bottom:4px;line-height:1.3;}
.mod-desc{font-size:13px;color:var(--muted);line-height:1.6;margin-bottom:10px;flex:1;}
.mod-footer{display:flex;align-items:center;justify-content:space-between;}
.mod-slides{font-size:10px;color:var(--muted);font-family:'IBM Plex Mono',monospace;}
.pill{font-size:9px;padding:2px 7px;border-radius:99px;font-weight:600;letter-spacing:.04em;}
.pill-ready{background:rgba(16,185,129,.12);color:var(--green);border:1px solid rgba(16,185,129,.25);}
.pill-soon{background:var(--surface2);color:var(--muted);border:1px solid var(--border);}
.mod-link{display:block;width:100%;margin-top:10px;background:var(--accent);color:#fff;border:none;border-radius:6px;padding:9px;font-family:'IBM Plex Sans',sans-serif;font-size:12px;font-weight:500;cursor:pointer;text-align:center;text-decoration:none;transition:opacity .15s;}
.mod-link:hover{opacity:.85;}
.about-section{margin:0 20px 32px;background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:18px;}
.about-label{font-family:'IBM Plex Mono',monospace;font-size:9px;letter-spacing:.14em;text-transform:uppercase;color:var(--muted);margin-bottom:10px;}
.about-text{font-size:13px;color:var(--subtle);line-height:1.75;margin-bottom:12px;}
.about-text strong{color:var(--text);}
.about-link{display:inline-flex;align-items:center;gap:6px;font-family:'IBM Plex Mono',monospace;font-size:10px;color:var(--accent-bright);background:var(--accent-glow);border:1px solid var(--accent);border-radius:4px;padding:4px 10px;text-decoration:none;transition:opacity .15s;}
.about-link:hover{opacity:.8;}
.page-footer{margin:32px 20px 0;padding:24px 0 32px;border-top:none;text-align:left;} .footer-bottom{border-top:none;}
.footer-top{display:flex;flex-wrap:wrap;align-items:center;justify-content:space-between;gap:16px;margin-bottom:20px;}
.footer-brand{display:flex;align-items:center;gap:10px;}
.footer-mark{font-family:'IBM Plex Mono',monospace;font-size:11px;font-weight:600;letter-spacing:.08em;color:var(--accent-bright);background:var(--accent-glow);border:1px solid var(--accent);border-radius:6px;padding:5px 10px;}
.footer-tag{font-size:12px;color:var(--muted);line-height:1.5;}
.footer-links{display:flex;flex-wrap:wrap;gap:8px;}
.footer-links a{font-family:'IBM Plex Mono',monospace;font-size:10px;color:var(--subtle);text-decoration:none;border:1px solid var(--border);border-radius:6px;padding:6px 12px;display:inline-flex;align-items:center;gap:6px;transition:all .15s;}
.footer-links a:hover{border-color:var(--accent);color:var(--accent-bright);}
.footer-bottom{display:flex;flex-wrap:wrap;align-items:center;justify-content:space-between;gap:10px;padding-top:16px;border-top:1px solid var(--border);}
.footer-copy{font-size:11px;color:var(--muted);line-height:1.6;}
.footer-disclaimer{font-size:11.5px;color:var(--muted);line-height:1.8;max-width:760px;margin:14px auto 0;text-align:center;}
.footer-disclaimer strong{color:var(--subtle);font-weight:600;}
.footer-disclaimer a{color:var(--accent-bright);text-decoration:underline;text-underline-offset:2px;border:none;padding:0;border-radius:0;display:inline;}
.footer-disclaimer a:hover{opacity:.8;}
```

---

## 4. Base design system — `module01-shared.css` (copy of `llm01-shared.css`)

Every slide page (and the homepage, via the `<link>` in section 1) loads this. This is layered *underneath* the homepage-specific style block above. It defines the dark theme, color tokens, nav bar, progress bar, tab-nav, all content components (`block`, `callout`, `mono-block`, `outcome-list`, `person-grid`, `compare`, `scenario-card`, `real-incident`, `mit-card`, `tool-grid`, `part-banner`), buttons, and the quiz UI. **Copy this file verbatim** into each module folder — don't rewrite it, per the existing convention in [llm/LESSON-AUTHORING-GUIDE.md](llm/LESSON-AUTHORING-GUIDE.md).

```css
@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;600&family=IBM+Plex+Sans:wght@400;500;600&display=swap');
:root{--bg:#0a0a0f;--surface:#111118;--surface2:#18181f;--border:#22222e;--accent:#6d28d9;--accent-bright:#a78bfa;--accent-glow:rgba(109,40,217,0.10);--green:#10b981;--yellow:#f59e0b;--red:#f43f5e;--blue:#38bdf8;--orange:#fb923c;--text:#e2e8f0;--muted:#8899a6;--subtle:#a8b8c8;}
*{margin:0;padding:0;box-sizing:border-box;}html{scroll-behavior:smooth;}
body{background:var(--bg);color:var(--text);font-family:'IBM Plex Sans',sans-serif;min-height:100vh;padding-bottom:100px;}
.top-nav{display:flex;align-items:center;justify-content:space-between;padding:14px 20px;border-bottom:1px solid var(--border);position:sticky;top:0;background:var(--bg);z-index:100;}
.nav-left{display:flex;align-items:center;gap:12px;}
.nav-badge{font-family:'IBM Plex Mono',monospace;font-size:10px;letter-spacing:.12em;text-transform:uppercase;color:var(--accent-bright);background:var(--accent-glow);border:1px solid var(--accent);border-radius:4px;padding:3px 9px;}
.nav-badge-home{font-family:'IBM Plex Mono',monospace;font-size:10px;letter-spacing:.12em;text-transform:uppercase;color:#ffffff;background:rgba(226,232,240,0.06);border:1px solid #e2e8f0;border-radius:4px;padding:3px 9px;text-decoration:none;}
.nav-title{font-size:13px;color:var(--subtle);}
.nav-right{font-family:'IBM Plex Mono',monospace;font-size:11px;color:var(--muted);}
.progress-wrap{padding:12px 20px 0;background:var(--bg);}
.progress-track{display:flex;gap:3px;}
.progress-track .seg{flex:1;height:3px;border-radius:99px;background:var(--border);transition:background .3s;}
.progress-track .seg.done{background:var(--green);}
.progress-track .seg.active{background:var(--accent-bright);}
.progress-labels{display:flex;justify-content:space-between;font-family:'IBM Plex Mono',monospace;font-size:9px;color:var(--muted);margin-top:6px;padding:0 2px;}
.slide{display:none;padding:28px 20px 0;}.slide.active{display:block;}
.slide-eyebrow{font-family:'IBM Plex Mono',monospace;font-size:9px;letter-spacing:.14em;text-transform:uppercase;color:var(--muted);margin-bottom:10px;}
.slide-title{font-size:clamp(18px,5vw,24px);font-weight:600;color:#fff;line-height:1.25;margin-bottom:6px;}
.slide-subtitle{font-size:14px;color:var(--subtle);line-height:1.6;margin-bottom:24px;}
.block{background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:18px;margin-bottom:14px;}
.block-label{font-family:'IBM Plex Mono',monospace;font-size:9px;letter-spacing:.12em;text-transform:uppercase;margin-bottom:8px;}
.block-label.purple{color:var(--accent-bright);}.block-label.red{color:var(--red);}.block-label.yellow{color:var(--yellow);}.block-label.green{color:var(--green);}.block-label.blue{color:var(--blue);}.block-label.orange{color:var(--orange);}
.block p{font-size:14px;color:var(--subtle);line-height:1.75;margin-bottom:10px;}.block p:last-child{margin-bottom:0;}.block p strong{color:var(--text);}
.callout{border-radius:8px;padding:14px 16px;margin-bottom:14px;}
.callout.purple{background:var(--accent-glow);border:1px solid rgba(109,40,217,.35);}.callout.red{background:rgba(244,63,94,.06);border:1px solid rgba(244,63,94,.25);}.callout.yellow{background:rgba(245,158,11,.06);border:1px solid rgba(245,158,11,.25);}.callout.green{background:rgba(16,185,129,.06);border:1px solid rgba(16,185,129,.25);}.callout.blue{background:rgba(56,189,248,.06);border:1px solid rgba(56,189,248,.25);}.callout.orange{background:rgba(251,146,60,.06);border:1px solid rgba(251,146,60,.25);}
.callout-label{font-family:'IBM Plex Mono',monospace;font-size:9px;letter-spacing:.12em;text-transform:uppercase;margin-bottom:6px;}
.callout.purple .callout-label{color:var(--accent-bright);}.callout.red .callout-label{color:var(--red);}.callout.yellow .callout-label{color:var(--yellow);}.callout.green .callout-label{color:var(--green);}.callout.blue .callout-label{color:var(--blue);}.callout.orange .callout-label{color:var(--orange);}
.callout p{font-size:14px;color:var(--subtle);line-height:1.75;margin-bottom:8px;}.callout p:last-child{margin-bottom:0;}.callout p strong{color:var(--text);}
.mono-block{background:#0d0d14;border:1px solid var(--border);border-radius:8px;padding:14px 16px;margin:12px 0;font-family:'IBM Plex Mono',monospace;font-size:12px;color:var(--accent-bright);line-height:1.7;white-space:pre-wrap;word-break:break-word;}
.mono-block .comment{color:var(--muted);}
.outcome-list{display:flex;flex-direction:column;gap:8px;margin-bottom:14px;}
.outcome-item{display:flex;align-items:flex-start;gap:12px;background:var(--surface);border:1px solid var(--border);border-radius:8px;padding:12px 14px;}
.outcome-icon{font-size:16px;flex-shrink:0;margin-top:1px;}
.outcome-title{font-size:13px;font-weight:600;color:var(--text);margin-bottom:3px;}
.outcome-desc{font-size:12px;color:var(--muted);line-height:1.6;}
.person-grid{display:flex;flex-direction:column;gap:8px;margin-bottom:14px;}
.person-card{background:var(--surface);border:1px solid var(--border);border-radius:8px;padding:12px 14px;display:flex;align-items:flex-start;gap:12px;}
.person-icon{font-size:22px;flex-shrink:0;background:var(--surface2);border-radius:6px;width:40px;height:40px;display:flex;align-items:center;justify-content:center;}
.person-name{font-size:13px;font-weight:600;color:var(--text);margin-bottom:3px;}
.person-role{font-size:11px;color:var(--accent-bright);font-family:'IBM Plex Mono',monospace;margin-bottom:4px;}
.person-desc{font-size:12px;color:var(--muted);line-height:1.6;}
.compare{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:14px;}
@media(max-width:500px){.compare{grid-template-columns:1fr;}}
.compare-col{background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:16px;}
.compare-col.red-col{border-color:rgba(244,63,94,.3);}.compare-col.orange-col{border-color:rgba(251,146,60,.3);}.compare-col.green-col{border-color:rgba(16,185,129,.3);}
.compare-header{font-size:12px;font-weight:600;margin-bottom:10px;padding-bottom:8px;border-bottom:1px solid var(--border);}
.compare-col.red-col .compare-header{color:var(--red);}.compare-col.orange-col .compare-header{color:var(--orange);}.compare-col.green-col .compare-header{color:var(--green);}
.compare-item{font-size:12px;color:var(--muted);line-height:1.6;padding:5px 0;border-bottom:1px solid var(--border);}.compare-item:last-child{border-bottom:none;padding-bottom:0;}.compare-item strong{color:var(--text);}
.scenario-card{background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:16px;margin-bottom:12px;}
.scenario-num{font-family:'IBM Plex Mono',monospace;font-size:9px;color:var(--muted);margin-bottom:6px;}
.scenario-title{font-size:14px;font-weight:600;color:var(--text);margin-bottom:10px;}
.scenario-body{font-size:13px;color:var(--subtle);line-height:1.75;}.scenario-body strong{color:var(--text);}
.scenario-why{margin-top:10px;padding-top:10px;border-top:1px solid var(--border);font-size:12px;color:var(--muted);line-height:1.6;}.scenario-why strong{color:var(--accent-bright);}
.real-incident{background:var(--surface);border:1px solid rgba(244,63,94,.3);border-radius:10px;padding:16px;margin-bottom:12px;}
.real-incident-tag{font-family:'IBM Plex Mono',monospace;font-size:9px;color:var(--red);letter-spacing:.12em;text-transform:uppercase;margin-bottom:6px;}
.real-incident-title{font-size:14px;font-weight:600;color:var(--text);margin-bottom:4px;}
.real-incident-cve{font-family:'IBM Plex Mono',monospace;font-size:10px;color:var(--accent-bright);margin-bottom:10px;}
.real-incident-body{font-size:13px;color:var(--subtle);line-height:1.75;margin-bottom:4px;}.real-incident-body strong{color:var(--text);}
.real-incident-lesson{margin-top:10px;padding-top:10px;border-top:1px solid rgba(244,63,94,.2);font-size:12px;color:var(--muted);line-height:1.6;}.real-incident-lesson strong{color:var(--accent-bright);}
.mit-card{background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:18px;margin-bottom:14px;}
.mit-num{font-family:'IBM Plex Mono',monospace;font-size:10px;color:var(--accent-bright);background:var(--accent-glow);border:1px solid var(--accent);border-radius:4px;padding:2px 8px;display:inline-block;margin-bottom:10px;}
.mit-title{font-size:15px;font-weight:600;color:#fff;margin-bottom:12px;}
.mit-section{margin-bottom:12px;}
.mit-section-label{font-family:'IBM Plex Mono',monospace;font-size:9px;letter-spacing:.12em;text-transform:uppercase;margin-bottom:5px;}
.mit-section-label.green{color:var(--green);}.mit-section-label.red{color:var(--red);}.mit-section-label.yellow{color:var(--yellow);}.mit-section-label.blue{color:var(--blue);}
.mit-section p{font-size:13px;color:var(--subtle);line-height:1.7;margin-bottom:8px;}.mit-section p:last-child{margin-bottom:0;}.mit-section p strong{color:var(--text);}
.tool-grid{display:flex;flex-direction:column;gap:8px;margin-bottom:14px;}
.tool-card{background:var(--surface);border:1px solid var(--border);border-radius:8px;padding:12px 14px;}
.tool-name{font-size:13px;font-weight:600;color:var(--text);margin-bottom:2px;}
.tool-maker{font-family:'IBM Plex Mono',monospace;font-size:10px;color:var(--accent-bright);margin-bottom:4px;}
.tool-desc{font-size:12px;color:var(--muted);line-height:1.6;}
.part-banner{background:var(--surface2);border:1px solid var(--border);border-radius:10px;padding:16px 18px;margin-bottom:20px;display:flex;align-items:center;gap:14px;}
.part-num{font-family:'IBM Plex Mono',monospace;font-size:11px;color:var(--accent-bright);background:var(--accent-glow);border:1px solid var(--accent);border-radius:4px;padding:4px 9px;flex-shrink:0;}
.part-title{font-size:13px;font-weight:600;color:var(--text);}.part-count{font-size:11px;color:var(--muted);margin-top:2px;}
.source-tag{display:inline-flex;align-items:center;gap:5px;font-family:'IBM Plex Mono',monospace;font-size:9px;color:var(--muted);background:var(--surface2);border:1px solid var(--border);border-radius:4px;padding:2px 8px;margin-bottom:12px;}
.notes-label{font-size:12px;color:var(--muted);margin-bottom:6px;font-weight:500;}
textarea{width:100%;background:var(--bg);border:1px solid var(--border);border-radius:8px;color:var(--text);font-family:'IBM Plex Sans',sans-serif;font-size:13px;line-height:1.6;padding:10px 12px;resize:vertical;min-height:80px;}
textarea:focus{outline:none;border-color:var(--accent);}textarea::placeholder{color:var(--muted);}
.btn-row{display:flex;gap:10px;margin-top:24px;}
.btn-primary{flex:1;background:var(--accent);color:#fff;border:none;border-radius:8px;padding:14px;font-family:'IBM Plex Sans',sans-serif;font-size:14px;font-weight:500;cursor:pointer;transition:opacity .18s;}
.btn-primary:hover{opacity:.85;}
.btn-secondary{background:transparent;color:var(--muted);border:1px solid var(--border);border-radius:8px;padding:14px 18px;font-family:'IBM Plex Sans',sans-serif;font-size:13px;cursor:pointer;transition:all .18s;}
.btn-secondary:hover{border-color:var(--accent);color:var(--accent-bright);}
.divider{height:1px;background:var(--border);margin:16px 0;}
.question-card{background:var(--surface);border:1px solid var(--border);border-radius:12px;padding:18px;margin-bottom:16px;}
.question-num{font-family:'IBM Plex Mono',monospace;font-size:10px;color:var(--muted);margin-bottom:8px;}
.question-text{font-size:15px;font-weight:500;color:var(--text);line-height:1.5;margin-bottom:16px;}
.options{display:flex;flex-direction:column;gap:8px;}
.option{background:var(--bg);border:1px solid var(--border);border-radius:8px;padding:12px 14px;font-size:13px;color:var(--muted);cursor:pointer;transition:all .15s;text-align:left;width:100%;font-family:'IBM Plex Sans',sans-serif;}
.option:hover:not(:disabled){border-color:var(--accent);color:var(--accent-bright);}
.option.correct{border-color:var(--green);background:rgba(16,185,129,.08);color:var(--green);}
.option.wrong{border-color:var(--red);background:rgba(244,63,94,.08);color:var(--red);}
.option:disabled{cursor:not-allowed;}
.feedback{margin-top:10px;padding:10px 12px;border-radius:8px;font-size:13px;line-height:1.6;display:none;}
.feedback.show{display:block;}
.feedback.correct{background:rgba(16,185,129,.08);border:1px solid rgba(16,185,129,.2);color:var(--green);}
.feedback.wrong{background:rgba(244,63,94,.08);border:1px solid rgba(244,63,94,.2);color:var(--red);}
.quiz-score{text-align:center;padding:24px 0;}
.score-num{font-size:52px;font-weight:600;color:var(--accent-bright);font-family:'IBM Plex Mono',monospace;}
.score-label{font-size:14px;color:var(--muted);margin-top:4px;}
.score-msg{margin-top:12px;padding:14px;border-radius:8px;font-size:13px;line-height:1.6;text-align:center;}
.complete-wrap{text-align:center;padding:32px 0 24px;}
.complete-icon{font-size:52px;margin-bottom:16px;}
.complete-title{font-size:24px;font-weight:600;color:#fff;margin-bottom:8px;}
.complete-sub{font-size:14px;color:var(--muted);line-height:1.7;margin-bottom:24px;}
.checklist{display:flex;flex-direction:column;gap:8px;margin-bottom:20px;}
.check-item{display:flex;align-items:flex-start;gap:10px;background:var(--surface);border:1px solid rgba(16,185,129,.2);border-radius:8px;padding:12px 14px;}
.check-mark{color:var(--green);font-size:14px;flex-shrink:0;margin-top:1px;}
.check-text{font-size:13px;color:var(--subtle);line-height:1.5;}

/* ── TAB NAV (clickable slide jump) ── */
.tab-nav{display:flex;gap:3px;overflow-x:auto;padding:0 0 2px;-webkit-overflow-scrolling:touch;}
.tab-nav::-webkit-scrollbar{height:3px;}
.tab-nav a.seg{flex:1;height:8px;border-radius:99px;background:var(--border);transition:background .15s;display:block;}
.tab-nav a.seg:hover{background:var(--accent);}
.tab-nav a.seg.done{background:var(--green);}
.tab-nav a.seg.active{background:var(--accent-bright);}

/* ── PAGE FOOTER (sources link) ── */
.page-footer{margin-top:32px;padding-top:18px;border-top:1px solid var(--border);text-align:center;}
.page-footer a{font-family:'IBM Plex Mono',monospace;font-size:11px;color:var(--muted);text-decoration:none;border:1px solid var(--border);border-radius:6px;padding:7px 14px;display:inline-flex;align-items:center;gap:6px;transition:all .15s;}
.page-footer a:hover{border-color:var(--accent);color:var(--accent-bright);}
```

---

## 5. What to change for a new project

- Swap `--accent` / `--accent-bright` / `--accent-glow` in the `:root` block if you want a different brand color than purple (currently `#6d28d9` / `#a78bfa`).
- Hero badge emoji/copy (swap the `💡 {{Topic}} · {{Category}} · {{Category}}` placeholder above for your own, vs. `🔒 Security · AI · LLMs` on the original).
- `.mod-num` prefix: `MOD01`/`MOD02`… (or keep a scheme like `PY01`) instead of `LLM01`.
- Folder/file naming: mirror the existing convention in [llm/LESSON-AUTHORING-GUIDE.md](llm/LESSON-AUTHORING-GUIDE.md) — `moduleNN-lesson/` flat folders, `moduleNN-shared.css` copied verbatim, `moduleNN-slide-01.html` … `-XX.html`, `moduleNN-quiz.js`, `sources.html` per module.
- The full per-slide anatomy (5-part structure, tab-nav, quiz engine, mitigation/compare/scenario card markup) is all documented in that guide — it's designed to be reused 1:1 for any subject, not just security content.
