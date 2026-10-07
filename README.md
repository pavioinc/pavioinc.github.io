# pavio-website

The Pavio marketing/product website. Plain HTML/CSS/JS, no build step, styled from
the tokens in `design_handoff_pavio/Pavio Design System.dc.html` (Pavio Green +
Warm Gold palette, Noto Sans, the same button/card/badge shapes as the product itself).

## Local preview

```bash
cd docs
python3 -m http.server 8000
# open http://localhost:8000
```

Or just open `docs/index.html` directly in a browser — it has no server dependency.

## Deploying to GitHub Pages

This repo is already structured for the "deploy from a branch, `/docs` folder" Pages
option — no GitHub Actions workflow needed.

1. Push this repo to GitHub (e.g. `pavio/pavio-website` or under your own account).
2. On GitHub: **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Branch: `main`, folder: **`/docs`**. Save.
5. GitHub publishes the site at `https://<org-or-user>.github.io/pavio-website/`
   (or your custom domain, once a `CNAME` file is added to `docs/`).

`docs/.nojekyll` is included so GitHub Pages serves the files as-is without running them
through Jekyll first.

## Structure

```
docs/
  index.html            single-page site: hero, features, how it works, security, pricing, contact
  assets/css/style.css  design tokens + layout
  assets/js/main.js     mobile nav toggle only
  assets/img/           logo mark (inline SVG source)
  .nojekyll
```

## Content notes

Copy is grounded in what's actually built (see `pavio/README.md` and
`requirements/PHASE1-MVP-ISSUES.md` in the main project) — the payment loop, bed
management, WhatsApp notifications, tenant app scope, Aadhaar OTP flow, RBAC, and the
exact pricing tiers from `pavio/auth-service/src/plans.ts`. No fabricated customer
logos or testimonials, since the product hasn't had a live pilot yet (Phase 1 backlog
issue 15 is still open) — the CTA is framed as early access rather than general
availability. Update the pricing grid here by hand if `plans.ts` changes; it's not
generated from it.
