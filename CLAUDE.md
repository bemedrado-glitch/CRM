# Filveo — Project Instructions for Claude

> Read this file before making any changes. It defines scope, structure, brand,
> and guard-rails that keep Filveo consistent across sessions.

---

## What Filveo is

**Filveo** is a CRM built for independent professionals working in **interior
design and architecture**. Its wedge against every generic CRM (HoneyBook,
Mydoma, Houzz Pro, Salesforce) is the **post-sale lifecycle**: the Post-30 and
Post-60 follow-ups, the mileage deduction, the vendor credits, and the
referral engine that turns a delivered project into the next one.

The product is positioned against spreadsheets, not against other CRMs. The
real competitor is the $28,400/year that walks out the door when a designer
forgets to follow up after delivery.

---

## Brand at a glance

- **Name:** Filveo (pronounced "fill-VEE-oh")
- **Etymology:** *filo* (thread) + *veo* (I see) — "I see every thread of your client relationships"
- **Palette:** Midnight Silk — champagne gold (`#d4c4a8`) on midnight (`#0d1018`)
- **Typography:** Playfair Display (display) · DM Sans (body) · Cormorant Garamond (numbers)
- **Voice:** trusted colleague, not a sales tool — confident, warm, direct, industry-native

Read `BRAND.md` before touching UI, copy, or marketing surfaces. Do not
introduce new colors, fonts, or voice without updating `BRAND.md` first.

---

## Repository layout

```
/
├── CLAUDE.md                    # This file
├── README.md                    # Public-facing project overview
├── BRAND.md                     # Brand guidelines
├── LICENSE
├── .env.example                 # Environment variable template
├── package.json                 # Metadata (no build step)
│
├── src/
│   ├── hub.html                 # Command Center — navigates all 4 surfaces
│   ├── index.html               # Landing page (SEO/GEO/LLMO optimized)
│   ├── demo.html                # 16-scene Sofia Reyes walkthrough
│   └── app.html                 # Full CRM application
│
├── docs/
│   └── gtm-bible-v4.html        # GTM Bible — 10-tab strategy deck
│
└── supabase/
    └── schema.sql               # Supabase database schema
```

### Current component status

| Component | File | Status |
|---|---|---|
| Brand guidelines | `BRAND.md` | ✅ Filveo-branded |
| Project README | `README.md` | ✅ Filveo-branded |
| Env template | `.env.example` | ✅ Filveo-branded |
| Supabase schema | `supabase/schema.sql` | ✅ Filveo-branded |
| Command Center (hub) | `src/hub.html` | ⏳ Pending commit (user provided) |
| Landing page | `src/index.html` | ⏳ Pending commit (user provided) |
| Demo | `src/demo.html` | ⚠ Canvass-branded — needs rebrand |
| CRM app | `src/app.html` | ⏳ Pending commit (user provided) |
| GTM Bible | `docs/gtm-bible-v4.html` | ⏳ Pending commit (user provided) |
| PWA assets (sw.js, manifest.json, icons) | — | ❌ Missing |
| Logo / favicon / og-image | — | ❌ Missing |

---

## Development workflow

Zero-build project. No bundler, no transpiler, no npm install required.

```bash
python3 -m http.server 8080
open http://localhost:8080/src/hub.html     # Command Center
open http://localhost:8080/src/index.html   # Landing page
open http://localhost:8080/src/demo.html    # Demo
open http://localhost:8080/src/app.html     # CRM app
```

`package.json` exists only for metadata. Do not introduce a build step
without discussing first.

### Default branch for agent work

All agent work on **`claude/setup-project-diwsY`**. Do not push to `main`
without explicit permission. Create a draft PR for every meaningful change.

---

## Coding & writing conventions

1. **Vanilla HTML/CSS/JS only** for the app. No React/Vue/Svelte. The demo
   and GTM bible use pre-bundled React artifacts — that's a single-file
   shipping pattern for those two surfaces only, not a template for the app.
2. **Single-file HTML surfaces.** Landing, demo, app, hub, and GTM bible are
   each intentionally single-file HTML for offline/portable demos.
3. **Every revenue / price / calculation number must be traceable.**
4. **Voice check on every user-facing string.** See `BRAND.md` voice examples.
5. **Dates in copy use today's date or a clearly fictional future date.**

---

## Known pitfalls

- **Canvass leftovers.** The project was previously named *Canvass*. If you
  find `canvasscrm.com`, `"Canvass"` brand strings, or the old palette
  (`#e4c97e` on `#06080b`) — update to Filveo (`#d4c4a8` / `#0d1018`,
  Playfair Display). `demo.html` still has 51 "Canvass" references awaiting
  a rebrand pass.
- **Domain is not purchased.** Use `filveo.com` as a placeholder but don't
  commit to anything that depends on the final domain (transactional email,
  SSO domain, etc.).
- **GitHub web uploads shuffle filenames.** An April 14 upload swapped every
  file's name. If you see that again, check file contents vs. extensions.

---

## What Claude should do by default

- Read `BRAND.md` and this file before edits.
- Use dedicated tools (Read, Edit, Glob, Grep, Bash — not `cat`/`find`/`sed`).
- Commit with clear, scoped messages. Keep phases separate.
- Never skip pre-commit hooks.
- Create a draft PR after pushing.

## What Claude should ask before doing

- Any change that alters brand (name, palette, voice).
- Any new dependency, build step, or framework.
- Any hosting / domain / email decision.
- Any delete of content over ~10k (the user may want a backup first).

---

*Last updated: 2026-04-14 — Phase 1 restructure*
