# Apex site

Single-file marketing site for the Apex AI agency. Everything lives in `index.html` (HTML + CSS + JS, Three.js loaded from CDN). No build step.

## Preview locally
- Preview config `apex` on port 4325 (in `~/.claude/launch.json`), or:
- `python3 -m http.server 4325 --directory ~/apex-site` then open http://localhost:4325

## The 2 things to set before launch
1. **Contact form target.** In `index.html`, find the `<script type="module">` near the bottom:
   - `const APEX_EMAIL = 'hello@apex.studio'` → set your real email (used by the mailto fallback).
   - `const WEB3FORMS_KEY = ''` → paste a free access key from https://web3forms.com to make the form submit in-page (otherwise it falls back to opening the visitor's email app, which still works).
2. **Social share image.** Search `TODO: add og:image` in the `<head>` and add a 1200x630 screenshot URL once deployed (for nice link previews).

## How to edit common things
- **Copy:** all text is plain HTML in the body. Search for the headline and edit in place.
- **Packages:** the `<!-- PACKAGES -->` section. Each tier is a `.pkg` block (Launch / Growth / Autopilot). To add hard prices, drop a price line under each `.pname` (there is a TODO comment marking the spot). The section note holds the "$2k to $3k a month" range.
- **Work / portfolio:** the `<!-- WORK -->` section. Each project is one `<a>` with a tag, name, description, and live link. All four links are verified live. If you add one, test the link first (dead links were a past mistake).
- **Nav:** the `.navlinks` block. Active highlight (scrollspy) is automatic based on `href="#section"`.

## SEO
- Three pillars drive all the messaging: **AI consulting, automation, website design and building.**
- The deep SEO page is `ai-consulting-phoenix.html`, linked quietly from the footer and listed in `sitemap.xml`. It targets local searches for AI consulting, AI receptionists, missed-call text-back, chatbots, CRM automation, web design, and local SEO across Phoenix and the West Valley, with an FAQ (FAQPage schema) for rich results.
- `sitemap.xml` + `robots.txt` point Google at both pages. After deploy, submit the sitemap in Google Search Console (Sitemaps → enter `sitemap.xml`) to get indexed faster.
- To rank for more terms later, clone `ai-consulting-phoenix.html` into per-service or per-city pages (e.g. `ai-receptionist-phoenix.html`, `web-design-glendale.html`) and add each to `sitemap.xml`. That is programmatic local SEO.
- A truly hidden/unlinked or keyword-stuffed page does NOT rank and can get penalized; that is why the SEO page is real, readable, and crawlable.

## Deploy (same as your other sites)
- Push to a GitHub repo and enable GitHub Pages, or drag the folder into Netlify. HTTPS is automatic on both.
- Then point a domain at it and add the `og:image`.

## Corrections from past builds that are already baked in
- No em dashes in copy; ALL-CAPS only for intentional emphasis.
- No invented stats; portfolio uses only real, live, verified links.
- No popups; one inline contact form with a guaranteed fallback (no silently-broken form, the Michigan Shippers lesson).
- High-contrast text + scrim over the 3D for legibility; `prefers-reduced-motion` respected.
- SEO: meta description, Open Graph, Twitter, `ProfessionalService` JSON-LD schema (Phoenix NAP), favicon.
- Active-nav highlight, mobile-responsive grids, single-file for fast iteration.

## The brain
The hero is a live Three.js mesh (iridescent, shader-displaced, two-hemisphere fissure). Click anywhere and it lights up a color, with a ripple from the click point; the hue comes from where on screen you clicked. Tuning lives in the `<script type="module">` block (search `addPing` for click behavior, `bloom` for glow).
