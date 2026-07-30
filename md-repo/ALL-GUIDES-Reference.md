# All Guides Button — Reference

Drop this in the top-right nav of any course site to link back to the main evlbot.xyz hub.

## HTML

```html
<div class="nav-right">
  <a href="https://evlbot.xyz" class="nav-link">&#127968; All Guides</a>
  <a href="https://evlbot.xyz/about.html" class="nav-link" target="_blank" rel="noopener">About</a>
</div>
```

## Required CSS (nav-link style)

```css
.nav-right {
  display: flex;
  align-items: center;
  gap: 8px;
}

.nav-link {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 11px;
  font-weight: 600;
  color: var(--accent-bright);
  background: var(--accent-glow);
  border: 1px solid var(--border);
  border-radius: 4px;
  padding: 4px 10px;
  text-decoration: none;
  letter-spacing: .06em;
  transition: opacity .15s;
}

.nav-link:hover { opacity: .75; }
```

## Full nav bar pattern

```html
<div class="top-nav">
  <a href="index.html" style="text-decoration:none;display:flex;align-items:center;gap:12px;">
    <span class="nav-badge">evlbot.xyz</span>
    <span class="nav-title"><!-- Course name here --></span>
  </a>
  <div class="nav-right">
    <a href="https://evlbot.xyz" class="nav-link">&#127968; All Guides</a>
    <a href="https://evlbot.xyz/about.html" class="nav-link" target="_blank" rel="noopener">About</a>
  </div>
</div>
```

## Notes

- `&#127968;` is the 🏠 emoji
- `--accent-bright`, `--accent-glow`, `--border` come from the site's CSS variable set — swap values to match each course's accent color
- The About link is optional but consistent across all sites
- Hub URL: `https://evlbot.xyz`
