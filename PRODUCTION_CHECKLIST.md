# Production Readiness Checklist

Use this checklist before deploying to production.

---

## Final pass (Mar 2025)

- **404 page**: "Back home" link now uses `relative_url` for baseurl compatibility
- **Portfolio footer**: LinkedIn link uses `{{ site.linkedin_username }}` for config consistency
- **Build**: ✓ passes with `bundle exec jekyll build`
- **Sass deprecation warnings**: From Minima theme (darken/lighten in gem). Non-blocking; consider upgrading Minima when a fix is released

---

## ✅ Completed

### SEO
- [x] jekyll-seo-tag plugin (meta tags, Open Graph, Twitter Cards)
- [x] jekyll-sitemap plugin (auto-generates sitemap.xml)
- [x] robots.txt (allows crawlers, references sitemap)
- [x] Page-specific meta descriptions (index, about, portfolio, project pages)
- [x] Canonical URLs (handled by jekyll-seo-tag)
- [x] Author config for structured data

### Technical
- [x] Custom domain (CNAME: www.georgenyakundi.com)
- [x] GitHub Actions workflow for build & deploy
- [x] Mobile responsive design
- [x] Light/dark mode support
- [x] Semantic HTML (headings, sections, nav)

---

## ⚠️ Needs Attention

### 1. Install New Dependencies
```bash
bundle install
```
Required for `jekyll-sitemap`. Run before deploying.

### 2. GitHub Pages Settings
- **Repository → Settings → Pages**: Source = "GitHub Actions"
- **Custom domain**: Set to `www.georgenyakundi.com` (or apex `georgenyakundi.com`)
- **Enforce HTTPS**: Enable

### 3. Default OG Image
- Current default: `/assets/christ-in-song-screenshot.png`
- **Recommendation**: Create a dedicated OG image (1200×630px) for cleaner social previews when sharing the homepage
- Place at `assets/og-image.png` and update `_config.yml`:
  ```yaml
  image: /assets/og-image.png
  ```

### 4. Image Optimization
- `christ-in-song-screenshot.png` (~938 KB) could be compressed
- Consider: WebP format, or resize for web (max 1200px wide)
- Tools: [Squoosh](https://squoosh.app), `cwebp`

### 5. Analytics (Optional)
- Add Google Analytics 4: set `google_analytics: G-XXXXXXX` in `_config.yml`
- Minima includes the GA snippet when configured

### 6. 404 Page
- Custom 404 exists; ensure GitHub Pages uses it
- Test: https://georgenyakundi.com/nonexistent-page

### 7. Favicon
- Add `favicon.ico` or `apple-touch-icon.png` to `assets/`
- Add to head: `<link rel="icon" href="/assets/favicon.ico">`

### 8. Performance
- Fonts: Source Sans 3 loads from Google Fonts (add `&display=swap` if not present)
- Consider self-hosting fonts for privacy and faster load

### 9. Accessibility
- Run [Lighthouse](https://developers.google.com/web/tools/lighthouse) audit
- Verify: sufficient color contrast, focus states on links, alt text on images

### 10. Links Verification
- [ ] All internal links work
- [ ] External links (LinkedIn, GitHub, App Store) valid
- [ ] No broken mailto: links (email hidden as requested)

---

## Pre-Deploy Quick Test

```bash
bundle install
bundle exec jekyll build
bundle exec jekyll serve
```

Then verify:
1. Homepage loads, hero and featured work display
2. About → timeline renders
3. Portfolio → card links to Christ In Song detail
4. Footer: social links, description, no email
5. Mobile view: nav, footer, cards stack correctly
6. Dark mode: toggle OS preference, styles adapt

---

## Post-Deploy Verification

- [ ] https://georgenyakundi.com loads
- [ ] https://georgenyakundi.com/sitemap.xml exists
- [ ] https://georgenyakundi.com/robots.txt exists
- [ ] [Google Search Console](https://search.google.com/search-console): Add property, submit sitemap
- [ ] [Facebook Debugger](https://developers.facebook.com/tools/debug/): Check OG preview
- [ ] [Twitter Card Validator](https://cards-dev.twitter.com/validator): Check card preview
