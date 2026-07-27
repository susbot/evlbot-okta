# Style Reference — Okta Study-Guide Slide Deck

Extracted verbatim from:
`C:\Users\intune1001\Documents\okta\okta-admin\01-identity-access-mgmt\module1-ad-integration\submodule1-delegated-auth.html`

(Identified by its title slide: crumb `"Okta Certified Administrator · Part I"`, `<h1>Identity and Access Management</h1>`.)

This file documents the **literal CSS/framework values** for exact visual replication. For the *narrative/labeling pattern* (how content is structured into story-blocks), see the companion file `reveal-story-style-guide.md` in this same folder — the two are complementary, not duplicates.

## 1. Framework

**This deck is built on reveal.js — not a custom framework.**

- Core: **reveal.js v4.6.1**
- Base theme: **black** (reveal.js's built-in dark theme)
- Nav plugin: **reveal.js-menu v2.1.0** (by denehyg) — provides the hamburger icon / table-of-contents slide-out panel

All four loaded via jsDelivr CDN, exact URLs as they appear in the source file's `<head>` and before `</body>`:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@4.6.1/dist/reveal.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@4.6.1/dist/theme/black.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js-menu@2.1.0/menu.css">

<script src="https://cdn.jsdelivr.net/npm/reveal.js@4.6.1/dist/reveal.js"></script>
<script src="https://cdn.jsdelivr.net/npm/reveal.js-menu@2.1.0/menu.js"></script>
```

Initialization (also verbatim from the source file):

```js
Reveal.initialize({
  hash: true,
  slideNumber: true,
  transition: 'slide',
  width: 1200,
  height: 700,
  plugins: [ RevealMenu ],
  menu: {
    titleSelector: 'h1, h2',
    useTextContentForMissingTitles: true,
    markers: true,
    openButton: true,
    openSlideNumber: false,
    keyboard: true,
    themes: false,
    transitions: false,
    themesPath: '',
    openOnInit: false
  }
});
```

## 2. Font-family

**Not declared locally.** This deck's own `<style>` block contains no `@font-face`, no `@import`, and no `font-family` override (the one exception is `.quotebox`, which explicitly sets a monospace font — see below). The base typeface is inherited entirely from the linked reveal.js `black.css` theme, which defines:

```css
--r-main-font: Source Sans Pro, Helvetica, sans-serif;
```

...applied via `.reveal { font-family: var(--r-main-font); }` inside that theme file. So the actual rendered font stack is **Source Sans Pro, falling back to Helvetica, then generic sans-serif** — this comes along automatically as long as `black.css` is linked; nothing extra is needed to replicate it.

The one local override: `.quotebox` uses `font-family: 'Courier New', monospace;` to visually distinguish verbatim-quoted facts from prose.

## 3. Full Custom `<style>` Block (verbatim)

This is the entire local CSS from the source file — everything layered on top of reveal.js's own `reveal.css` + `black.css` + `menu.css`.

```css
:root {
  --amber:#f5a623; --red:#ff5c5c; --green:#3ddc84; --purple:#bb86fc; --blue:#5fb3ff; --peach:#ffb787;
}
.reveal .slides section { text-align: left; }
.reveal { font-size: 30px; }
.reveal h1, .reveal h2, .reveal h3 { text-align: left; }

.label {
  display: block;
  font-size: 0.5em;
  letter-spacing: 3px;
  font-weight: 700;
  text-transform: uppercase;
  margin: 0 0 14px 0;
}

.slide-menu-button { color: var(--peach) !important; }
.slide-menu-button .fa-bars::before { color: var(--peach); }
#slide-menu { background: #0a0a0a !important; }
.slide-menu-item a { font-size: 0.8em !important; }

.reveal .controls { color: var(--peach); }
.label.scenario { color: var(--amber); }
.label.mechanism { color: var(--blue); }
.label.gotcha { color: var(--red); }
.label.connection { color: var(--green); }
.label.angle { color: var(--purple); }
.label.recall { color: var(--green); }

.block { border-top: 1px solid #333; padding-top: 24px; margin-top: 24px; }
.block:first-of-type { border-top: none; margin-top: 0; padding-top: 0; }

.prose { font-size: 0.68em; line-height: 1.5; color: #e8e8e8; }
.prose b { color: #fff; }

.quotebox {
  background: #161616;
  border: 1px solid #333;
  border-left: 4px solid var(--blue);
  border-radius: 6px;
  padding: 18px 24px;
  font-family: 'Courier New', monospace;
  font-size: 0.55em;
  color: var(--blue);
  margin: 18px 0;
}

.badge {
  display: inline-block;
  background: #1e2a3a;
  color: var(--blue);
  font-size: 0.4em;
  padding: 4px 14px;
  border-radius: 14px;
  letter-spacing: 1px;
  vertical-align: middle;
  margin-left: 16px;
}

.titleslide h1 { font-size: 1.6em; margin-bottom: 10px; }
.titleslide .sub { font-size: 0.6em; color: #999; }
.titleslide .crumb { font-size: 0.45em; color: #666; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 20px; }

.recallbox {
  background: #10201a;
  border: 1px solid #235;
  border-left: 4px solid var(--green);
  border-radius: 6px;
  padding: 22px 28px;
  font-size: 0.65em;
  line-height: 1.5;
}
.source { font-size: 0.32em; color: #666; margin-top: 20px; }

.navlink { font-size: 0.4em; color: var(--peach); text-decoration: none; letter-spacing: 1px; }
.navlink:hover { text-decoration: underline; }
.navlink.next { display: block; margin-top: 16px; }
```

## 4. Reuse Notes

To replicate this look in another project exactly:

1. Include the same 4 CDN `<link>`/`<script>` tags from section 1 — this brings in reveal.js core, the `black` base theme (which supplies the `Source Sans Pro` font stack for free), and the reveal.js-menu plugin.
2. Paste the CSS block from section 3 into a `<style>` tag after those theme links, so it can override/extend them.
3. Base reveal font-size is `30px` (`.reveal { font-size: 30px; }`) — all other sizes in this deck are `em`-relative to that, so changing this one value rescales the whole deck proportionally.
4. Colors are all CSS custom properties on `:root` (`--amber`, `--red`, `--green`, `--purple`, `--blue`, `--peach`) — swap these 6 values to retheme without touching any other rule.
