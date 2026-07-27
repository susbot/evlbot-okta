# The Hamburger Menu in the Slide Decks

Every module's reveal.js deck (`module-N/slides/index.html`) has a clickable icon in the top-left — the three-stacked-lines icon.

- **Common name**: hamburger menu / hamburger icon / hamburger button — the universal symbol for "tap to open navigation."
- **What it does here**: acts as a table of contents / jump menu — click it to see every concept slide title in the deck and jump straight there, instead of arrowing through everything.
- **How it's implemented**: the [reveal.js-menu](https://github.com/denehyg/reveal.js-menu) plugin, loaded via CDN (`reveal.js-menu@2.1.0`) alongside the core `reveal.js@4.6.1` library.
- **CSS class**: `.slide-menu-button` — this is what gets targeted if you ever need to restyle it (we did this to tint it the site's blue accent color instead of the plugin's default).
- Auto-generates its list from the deck's `<h2>`/`<h3>` headings (configured via `titleSelector: 'h2, h3'` in the `Reveal.initialize()` menu config).
