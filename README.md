# Threefold Lighthouse Co. — Deployment Notes

Production single-file site for Gail's virtual assistant business. Built to your standard stack: GitHub Pages + Porkbun + Formspree + base64-embedded assets.

## File overview

| File | Purpose |
|---|---|
| `index.html` | The whole site — single file, all assets inline |
| `robots.txt` | Search engine crawler directives |
| `sitemap.xml` | XML sitemap for Google Search Console |
| `CNAME` | GitHub Pages custom domain mapping |

## Pre-launch checklist

### 1. Domain
- [ ] Register `threefoldlighthouse.com` on Porkbun
- [ ] Point Porkbun DNS to GitHub Pages:
  - A records: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
  - CNAME for `www` → `<gail-username>.github.io`

### 2. Formspree ✓ DONE
- [x] Form wired to `https://formspree.io/f/mkoyorer`
- [ ] Verify ownership email Formspree sent to Gail's Gmail
- [ ] Send a test submission after deploy to confirm it arrives

### 3. GitHub Pages
- [ ] Create new repo (e.g., `threefoldlighthouse-site`)
- [ ] Upload all files including `CNAME`
- [ ] Settings → Pages → Source: deploy from `main` branch root
- [ ] Wait ~5 min for SSL cert provisioning, then verify HTTPS works

### 4. Google Search Console
- [ ] Add property for `https://threefoldlighthouse.com`
- [ ] Verify via DNS TXT record on Porkbun
- [ ] Submit `sitemap.xml`

### 5. Google Analytics 4 (optional)
- [ ] Create GA4 property
- [ ] Add the `gtag` snippet just before `</head>` in `index.html`

## What's already set up

- **SEO**: Title, meta description, keywords, robots, canonical URL, theme-color
- **Open Graph + Twitter Cards**: Set for social sharing previews
- **Schema.org JSON-LD**: ProfessionalService markup with all DFW area cities, hours, services, contact info, geo coordinates
- **Favicon**: Inline base64 SVG (no separate file, can't break)
- **Accessibility**: Skip link, ARIA labels, semantic landmarks, role/aria-live on form status
- **Form**: Formspree-ready with honeypot anti-spam, async submission, success/error messaging
- **Mobile**: Fully responsive with breakpoints at 880px / 800px / 700px / 600px
- **Click-to-call** and **mailto** links work on mobile
- **Auto year** in footer (no annual update needed)

## Quick test before deploy

Open `index.html` in a browser — everything should render correctly. The form submission will silently fail until Formspree ID is set, but every other interaction will work.

## After Gail launches

Things to keep an eye on for the first month:
- Google Search Console for crawl errors
- Formspree dashboard for form submissions
- DNS propagation (sometimes takes 24–48 hours fully)
- Verify mailto and tel links open correctly on iPhone and Android

---

Built by Three Lights Studio · May 2026
