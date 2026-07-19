# Legal & support pages — hosting guide

These four static pages (`index.html`, `privacy.html`, `terms.html`, `support.html`)
are the public web copies of the app's Privacy Policy, Terms, and Support content.
The App Store listing **requires a public Privacy Policy URL** (and a Support URL),
so these need to live at a real https link before submission.

They are generated — **don't hand-edit the HTML.** The words live in one place:
`src/content/legalContent.json` (the same file the in-app screens read). To change
anything:

```bash
# 1. edit the prose
src/content/legalContent.json
# 2. regenerate these pages
node scripts/build-legal-html.mjs
```

## ⚠️ Before you publish (review checklist)

This is an honest, accurate **draft** grounded in how the app actually works — not
legal advice. Before the store listing goes live:

- [ ] **Support mailbox** — `support@mytruestyle.app` is a placeholder. Set up that
      inbox (or change `supportEmail` in the JSON to a real one) so the "Email us"
      links work.
- [ ] **Publisher** — decide the name/entity you publish under. If you register a
      business/ABN, add it (and a contact address, which some stores want).
- [ ] **A quick read-through** for the places you actually ship to.
- [ ] Re-run the generator after any edit.

## Where to host (pick one — all give free https)

You do **not** need to buy a domain just to satisfy Apple — a free host works. A
domain is recommended (it looks legit and gives you email + a landing page later),
but it's optional for launch.

**Option A — Cloudflare Pages (recommended).** Free, fast, custom domain later.
1. Create a Cloudflare account → Pages → "Upload assets".
2. Drag in the `docs/legal` folder.
3. You get `https://<project>.pages.dev` → your Privacy URL is
   `https://<project>.pages.dev/privacy.html`.

**Option B — GitHub Pages.** Free, already have the repo.
1. Repo → Settings → Pages → Deploy from a branch → pick the branch + `/docs` folder
   (or move these to a `docs/` root / `gh-pages` branch).
2. URL is `https://<user>.github.io/<repo>/legal/privacy.html`.

**Option C — Netlify.** Drag-and-drop `docs/legal` at app.netlify.com/drop.

## If you want the domain (optional, ~A$25–35/yr)

- **Registrar:** Cloudflare Registrar (at-cost, no markup) is the pick; Porkbun /
  Namecheap are fine too.
- **Name:** `mytruestyle.app` or `mytruestyle.com.au` (verify availability — the
  plain `.com` is taken). Note `.app` **requires https**, which every host above
  gives automatically.
- Then point the domain at your Pages/Netlify project and your URLs become
  `https://mytruestyle.app/privacy.html`.

## What to paste into App Store Connect

- **Privacy Policy URL:** `…/privacy.html`
- **Support URL:** `…/support.html`
- Terms are linked in-app (Me → About & privacy) and from every page footer; a
  Terms/EULA URL is optional unless you use a custom EULA.
