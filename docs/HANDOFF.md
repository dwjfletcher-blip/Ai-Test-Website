# Fletch Media Collective — Project Handoff

## Live Site
- **URL:** https://www.fletcherwebstudio.com/ (old test URL `ai-test-website-rho.vercel.app` is deprecated — should redirect here)
- **GitHub Repo:** https://github.com/dwjfletcher-blip/Ai-Test-Website
- **Hosting:** Vercel (auto-deploys on push to `master`)

---

## Git Remotes
| Name | URL |
|---|---|
| `ai-test-website` | https://github.com/dwjfletcher-blip/Ai-Test-Website.git |
| `portfolio` | https://github.com/dwjfletcher-blip/portfolio.git |
| `origin` | https://github.com/dwjfletcher-blip/nichols-pool-service.git |

**To deploy:** `git push ai-test-website master`

---

## Project Structure

```
Portfolio Website/
├── index.html                  # Main landing page (single-file, all styles inline)
├── portfolio.html              # Full portfolio page
├── barnabys.html               # Barnabys project pages
├── barnabys-menu.html
├── barnabys-events.html
├── barnabys-locations.html
├── barnabys-private-events.html
├── nichols-pool.html           # Nichols Pool Service page
├── prospector.html             # Prospect Finder page
├── ticket-emailer.html         # Ticket Emailer page
├── brand_assets/               # Logo, bg image, style references
│   ├── logo.png                # Main logo (used in hero + nav)
│   └── bg.jpg                  # Background image (fixed, 22% opacity)
├── splash.mp4                  # Remotion-rendered intro video (not currently in use)
├── myvideonew/                 # Remotion project (for future video work)
├── serve.mjs                   # Local dev server → http://localhost:3000
├── screenshot.mjs              # Puppeteer screenshot tool
└── CLAUDE.md                   # AI coding rules for this project
```

---

## Tech Stack

- **Pure HTML/CSS/JS** — no build step, no framework
- **Tailwind CSS** via CDN
- **Google Fonts:** Montserrat (headings) + Roboto + Roboto Mono (body/labels)
- **Hosting:** Vercel (static)
- **Remotion 4.0.438** — installed in `myvideonew/` for video rendering

---

## Brand Tokens

| Token | Value | Use |
|---|---|---|
| `--amber` | `#FF6A00` | Primary brand color |
| `--amber-light` | `#FF9A3C` | Gradients, highlights |
| `--amber-dim` | `rgba(255,106,0,0.12)` | Subtle tints |
| `--navy-dark` | `#060E1C` | Page background |
| `--navy` | `#0A1A2F` | Card backgrounds |
| `--navy-mid` | `#0D2244` | Elevated surfaces |
| `--white` | `#FFFFFF` | Body text |
| `--muted` | `#6B8DB5` | Secondary text |

---

## Hero Animation (on page load)

All animations run natively in CSS/JS on the hero section — no video overlay.

| Element | Animation | Timing |
|---|---|---|
| Scan line | Sweeps top → bottom | 0.05s |
| Light streaks | Diagonal swipes across bg | 0.08–0.35s |
| Logo | Spring scale-in + burst flash | 0.3s |
| Badge | Fade + slide up | 0.25s |
| Headline words | Word-by-word spring pop | 0.55–1.3s |
| Body copy | Fade up | 1.5s |
| CTA buttons | Fade up | 1.7s |
| Stats | Count up from 0 (ease-out cubic) | 1.9s |
| Particles | Float upward, infinite loop | ongoing |

---

## Portfolio Projects & Live URLs

| Project | Tag | Live URL |
|---|---|---|
| PawChart | SaaS Prototype | https://pawchart-lac.vercel.app/ |
| Enchanted Rosie | E-Commerce | https://the-enchanted-rosie.vercel.app/ |
| Job Hunter | AI App | https://job-hunter-theta-tan.vercel.app/ |
| Prospect Finder | SaaS Tool | https://prospect-finder-olive.vercel.app/ |
| Barnabys Restaurant | Restaurant / Events | https://barnabys-test.vercel.app/ |
| Gabrielle Design | Portfolio / Brand | _(no live URL on file — update when available)_ |

All cards on the home page link directly to the live project URLs (open in new tab).

---

## Remotion Setup (`myvideonew/`)

A Remotion project exists for rendering branded video animations.

```bash
cd myvideonew
npm install          # first time only
npm run dev          # opens Remotion Studio at http://localhost:3001
npx remotion render HeroSplash --output ../splash.mp4 --codec h264
```

- Composition: `HeroSplash` — 180 frames, 30fps, 1920×1080
- Source: `myvideonew/src/Composition.tsx`
- Logo asset: `myvideonew/public/logo.png`
- `splash.mp4` is rendered and committed but not currently embedded in the site

---

## Local Dev

```bash
node serve.mjs       # serves http://localhost:3000
node screenshot.mjs http://localhost:3000
# screenshots saved to ./temporary screenshots/screenshot-N.png
```

---

## Known TODOs

- [ ] Add live URL for **Gabrielle Design** project card
- [ ] `splash.mp4` is rendered but not used — decide if/how to embed it
- [ ] `portfolio.html` still has its own separate card layout — keep in sync with `index.html` when adding new projects
