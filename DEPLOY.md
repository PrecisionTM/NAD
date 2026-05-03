# NAD+ Landing Page — Vercel Deployment Guide

## Folder Structure

```
vercel-nad/
├── index.html              ← Single-file landing page (inline CSS + JS)
├── vercel.json             ← { "cleanUrls": true } only
├── DEPLOY.md               ← This file
├── download                ← Blank placeholder (required)
└── images/
    ├── hero-bg.jpg         ← Hero background (woman on LA hilltop, sage-green outfit)
    ├── science-visual.jpg  ← Science section visual (cinematic cellular composite)
    ├── doctors/
    │   ├── dr-palumbo.jpg
    │   ├── angela-kifer-thomas.jpg
    │   ├── dr-patel.jpg
    │   ├── dr-colon-molero.jpg
    │   └── samuel-palmer.jpg
    └── logos/
        ├── lecom.svg
        ├── utmb-health.svg
        ├── cu-colorado.svg
        ├── ponce.svg
        ├── vanderbilt.svg
        ├── tel-aviv.svg
        ├── texas-tech.svg
        ├── cleveland-state.svg
        ├── maryville.svg
        └── kentucky.svg
```

---

## Deployment Steps

1. **Initialize Git & push to GitHub**
   ```bash
   cd vercel-nad
   git init
   git add .
   git commit -m "initial commit — NAD+ landing page"
   git branch -M main
   git remote add origin https://github.com/YOUR-ORG/nad-landing.git
   git push -u origin main
   ```

2. **Import into Vercel**
   - Go to [https://vercel.com/new](https://vercel.com/new)
   - Click **Import Git Repository**
   - Select the `nad-landing` repo
   - **Framework Preset**: Other
   - **Root Directory**: *(leave blank)*
   - **Build Command**: *(leave blank)*
   - **Output Directory**: *(leave blank)*
   - **Install Command**: *(leave blank)*
   - Click **Deploy**

3. Vercel will serve `index.html` from the folder root. No build step needed.

---

## ⚠️ Do NOT

- Add a `build` script to `package.json`
- Add a `/(.*) rewrite` in `vercel.json`
- Set a subfolder as the Root Directory in Vercel
- Use absolute image paths (e.g., `/images/...`) — always use relative (`images/...`)
- Use `vh`, `dvh`, or `svh` units for any section heights

---

## CTA URLs

| Button | URL |
|---|---|
| Primary CTA (Check Eligibility) | `https://precisiontelemed.com/nad/` |
| Sermorelin cross-sell | `https://precisiontelemed.com/sermorelin/` |

---

## Conventions Compliance Checklist

- [x] No `vh`, `dvh`, or `svh` units anywhere in the file
- [x] Hero `min-height` uses `clamp(560px, 60vw, 860px)` (content-driven, not viewport-height)
- [x] Hero image uses `object-fit: cover` with relative path `images/hero-bg.jpg`
- [x] All absolute layers (`hero__bg`, `hero__overlay`) are inside `#hero` which has explicit `min-height`
- [x] Brand tokens: `--color-bg: #fdfbf7`, `--color-bg-alt: #f5f2ec`, `--color-primary: #788C75`
- [x] `--section-gap: clamp(1.5rem, 3.5vw, 3rem)` (content-driven)
- [x] `#page-wrap` has `overflow-x: hidden`
- [x] All image paths are relative (`images/...`) — no absolute `/images/...` paths
- [x] `vercel.json` contains only `{ "cleanUrls": true }` — no rewrites or extra fields
- [x] Blank `download` placeholder file present
- [x] No `../` cross-folder image references
- [x] Tested standalone and iframe-safe (no circular viewport sizing)

---

*Last updated: April 2026*
