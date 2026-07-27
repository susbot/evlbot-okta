# Course Home Reference — the "← Course Home" back-link

Source: every module's reveal.js deck in this project (`module-1/part-1/slides/index.html`
through `module-12/slides/index.html`).

Use this as the reference for the small fixed-position "back to homepage" button that sits
in the top-left corner of every slide deck, next to the reveal.js hamburger menu icon.

---

## 1. What it is

A single `<a>` tag, fixed to the top-left of the viewport, that stays visible on every slide
(it isn't part of any one `<section>`) and links back to the course's homepage
(`index.html`). It reads **"← Course Home"**.

It is deliberately NOT a full top-nav bar like the homepage uses (see
`DESIGN-SYSTEM-REFERENCE.md`) — slide decks are a different page type (a reveal.js
presentation, not a card-grid page), so they get this one small, unobtrusive link instead
of the full site header/footer.

---

## 2. Exact markup — paste this exactly, change only the `href`

```html
<a class="course-home" href="../../index.html">← Course Home</a>
```

Place it as the **first element inside `<body>`, before the `.reveal` div** — not inside
any slide `<section>`. That's what makes it persist across every slide instead of
disappearing when you navigate.

```html
<body>
<a class="course-home" href="../../index.html">← Course Home</a>
<div class="reveal">
  <div class="slides">
    ...
  </div>
</div>
</body>
```

---

## 3. Exact CSS — copy verbatim into the deck's `<style>` block

```css
.course-home {
  position: fixed; top: 12px; left: 56px; z-index: 40;
  font-family: monospace; font-size: 11px; letter-spacing: .08em; text-transform: uppercase;
  color: #58a6ff; background: rgba(31,111,235,0.10); border: 1px solid #1f6feb;
  border-radius: 4px; padding: 4px 9px; text-decoration: none;
}
.course-home:hover { opacity: .8; }
```

**Exact spec, so it can be rebuilt with zero guessing:**

| Piece | Exact value |
|---|---|
| Position | `fixed`, `top: 12px`, `left: 56px` — stays put on scroll, doesn't move between slides |
| Stacking | `z-index: 40` — above slide content, below reveal.js's own UI chrome |
| Text | `← Course Home` (literal string, includes the left-arrow character) |
| Font | `monospace` (the browser default monospace stack — no custom font import needed) |
| Font size | `11px` |
| Letter spacing | `.08em`, `text-transform: uppercase` |
| Text color | `#58a6ff` (this course's blue accent — swap for your own brand accent color) |
| Background | `rgba(31,111,235,0.10)` — same blue at 10% opacity |
| Border | `1px solid #1f6feb` — same blue, solid |
| Shape | `border-radius: 4px`, `padding: 4px 9px` |
| Text decoration | `none` (no underline) |
| Hover state | `opacity: .8` — the whole pill fades slightly, nothing else changes |

---

## 4. Why `left: 56px`, not `left: 20px`

This project's slide decks also load the **reveal.js-menu** plugin (the hamburger/jump-menu
icon — see `reveal-menu-notes.md`), which renders its own button fixed in the same top-left
corner at roughly `left: 20px`. `left: 56px` was chosen specifically so the "Course Home"
pill sits *next to* the hamburger icon instead of overlapping it.

**If your project doesn't use reveal.js-menu (or any other top-left-corner UI element),
you can safely use `left: 20px` instead** — 56px is only necessary to make room for that
specific plugin's button. If you do use reveal.js-menu or any other fixed top-left element,
keep the gap (measure your own element's width and offset accordingly).

---

## 5. The `href` changes based on folder depth — this is the only thing that varies

The link always points to the project's root `index.html`, so the relative path depends on
how many folders deep the slide file lives:

| Deck location (relative to project root) | Correct `href` |
|---|---|
| `module-N/slides/index.html` (2 folders deep) | `href="../../index.html"` |
| `module-N/part-M/slides/index.html` (3 folders deep) | `href="../../../index.html"` |

Rule of thumb: count the folders between the deck file and the project root, and use that
many `../` segments before `index.html`. Get this wrong and the link either 404s or opens
the wrong file.

---

## 6. Checklist to replicate this in a new project

1. Copy the CSS block from §3 verbatim into every slide deck's `<style>` block.
2. Copy the HTML from §2, placed as the first child of `<body>`.
3. Set the `href` per §5's rule for that specific file's folder depth.
4. Swap `#58a6ff` / `rgba(31,111,235,0.10)` / `#1f6feb` for your own project's accent color
   if it's not blue — all three values should stay the same hue at different
   opacities/shades (this project's blue is `--accent-bright`/`--accent`/`--accent-glow`
   from the homepage's design system, reused here for visual consistency between the
   homepage and every slide deck).
5. If your project doesn't have a hamburger/jump-menu plugin in the same corner, change
   `left: 56px` to `left: 20px` per §4.
6. Confirm the link text stays exactly `← Course Home` (or translate/rename consistently,
   but keep the arrow) — it's the same string across every deck in this project, which is
   what makes it recognizable as "the way back" no matter which module you're in.
