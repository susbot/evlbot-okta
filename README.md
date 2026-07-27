# Okta Certified Administrator — Study Guide

An interactive, slide-by-slide study guide for the **Okta Certified Administrator Hands-On Configuration Exam**, built as a static site — plain HTML/CSS/JS, no build step, no framework. Open any `index.html` directly in a browser and it works.

Live at [evlbot.xyz](https://evlbot.xyz).

## What's here

The site follows the official Okta exam study guide's structure exactly:

- **Part I** — 35 Discrete Option Multiple-Choice (DOMC) questions, organized into 5 weighted exam sections (Identity and Access Management, User Lifecycle Management, Security, Monitoring and Troubleshooting, API Functions). Each section is broken into modules, and each module into sub-topic slide decks.
- **Part II** — 4 Performance-Based, Hands-On Use Cases. Each configuration task pairs a concept course (reveal.js deck) with a hands-on lab you run yourself in an Okta sandbox.

## Structure

```
okta-admin/
├─ index.html                          # homepage — Part I + Part II overview
├─ 01-identity-access-mgmt/            # section hub
│  ├─ index.html
│  └─ moduleN-.../                     # module hub + sub-topic decks
├─ 02-user-lifecycle-mgmt/
├─ 03-security/
├─ 04-monitoring-troubleshooting/
├─ 05-api-functions/
└─ part2-user-management/              # Part II, first use case
```

Every sub-topic deck is a self-contained [reveal.js](https://revealjs.com/) presentation (loaded via CDN), styled with a shared dark/peach visual system and a story-block content pattern: Exam Bullet → Mechanism → Gotcha → Connection → Exam Angle → Recall. A fixed "← Course Home" pill and a hamburger jump-menu (via [reveal.js-menu](https://github.com/denehyg/reveal.js-menu)) sit on every slide.

## Content policy

All facts are sourced from official Okta documentation (`help.okta.com`, `developer.okta.com`) or the official exam study guide itself — nothing is invented. Where a source was thin or didn't cover something the exam bullet named, that gap is flagged explicitly in the deck rather than filled in with a guess.

## Disclaimer

This is an independent study aid, not an official Okta product, and is not affiliated with, endorsed by, or sponsored by Okta, Inc.

## License

MIT — see [LICENSE](LICENSE).
