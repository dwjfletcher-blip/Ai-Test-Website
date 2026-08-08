# Portfolio Audit — Fletcher Web Studio

**Date:** 2026-08-07
**Scope:** All 24 projects in Vercel account `dwjfletcher-4159s-projects`
**Method:** `vercel projects ls` (2 pages) → HTTP status check on every production URL → Playwright screenshots at 1440px and 390px → per-image load verification with scroll-triggered lazy-load → internal link crawl on every multi-page site.

---

## 0. Verification of your assumptions

| Your claim | Verdict |
|---|---|
| index.html desktop grid = PawChart (large), Enchanted Rosie, Job Hunter, Prospect Finder, Barnabys + "See Full Portfolio" tile | **Confirmed** — `index.html:1897–1955` |
| index.html mobile grid omits Barnaby's | **Confirmed** — `index.html:1849–1894` has only 4 cards. Barnaby's is desktop-only. |
| portfolio.html = Barnaby's, Enchanted Rosie, PawChart, Job Hunter, Prospect Finder | **Confirmed** — `portfolio.html:667–760` |
| "Three of five are web apps" | **Confirmed.** PawChart, Job Hunter, Prospect Finder = 3 of 5. |
| "I have many more projects than are featured" | **Confirmed.** 24 projects; 5 featured. At least 5 unfeatured projects outrank featured ones. |

**One correction to my own first pass:** an early automated check flagged broken images on Tom N Jerry's, Esthie Bestie, and Golf Balls Everywhere. On re-test with scroll-triggered lazy-loading, **zero images are genuinely broken anywhere in the account.** The first result was a capture-timing artifact. The placeholder findings below are real and were confirmed by reading the actual image URLs.

---

## 1. Your hypothesis, tested

> *"A restaurant owner learns nothing about whether I can build their restaurant site from an AI resume tool. I suspect my selection is optimized for the wrong audience."*

**You are right, but you have diagnosed the smaller of your two problems.**

Problem 1 (the one you spotted): 3 of 5 homepage tiles are developer tools. Buyer relevance 1–2/10. Correct.

Problem 2 (the one you missed, and it is worse): **of the two local-business tiles you did feature, one is visibly unfinished and the other is visibly broken.**

- **The Enchanted Rosie** — 12 of its 14 images are `placehold.co` boxes. Its product grid renders literal gold **"?" missing-image icons** where the charm chains should be. A buyer clicks your e-commerce example and finds a shop with no products.
- **Barnaby's** — the `<h1>` computes to **16px** (browser default, no CSS rule matches it). Your flagship restaurant headline renders smaller than the paragraph beneath it. At 390px the nav bar collides with the logo and runs off-screen — and Barnaby's isn't in the mobile grid anyway, so a phone visitor never sees the restaurant at all.

So the lineup fails twice over: wrong category, *and* worst-in-category. The single most on-target asset you own — a restaurant in the same town as your buyer persona — is both broken and hidden from the device your buyers actually use.

**Where I push back on you:** PawChart is the best-crafted thing in the account (9/10 visual, 4316px, real interaction design). Cutting it from the homepage is right. Cutting it from the business entirely is not — see §7.

---

## 2. Full inventory — all 24 projects

Scoring: **Buyer Relevance ×2**, Visual Craft, Completeness, Mobile Quality, Story. Max 60.

### Tier A — local business sites (the only ones that answer the buyer's question)

| Project | URL | Buyer ×2 | Visual | Complete | Mobile | Story | **Total** | Verdict |
|---|---|---|---|---|---|---|---|---|
| **Putt-Putt Fun Center** | puttputt-fun-center | 10 (20) | 9 | 9 | 9 | 10 | **57** | **PROMOTE — ship today** |
| **Esthie Bestie CAS** | esthie-bestie-cas | 10 (20) | 9 | 9 | 8 | 9 | **55** | **PROMOTE — ship today** |
| **Barnaby's Restaurant & Pub** | barnabys-test | 10 (20) | 8 | 9 | 3 | 9 | **49** | **FIX, then feature large** |
| **Nichols Pool Service** | nichols-deploy | 10 (20) | 8 | 9 | 3 | 9 | **49** | **FIX mobile nav, then promote** |
| **Michael Harris Real Estate** | michael-harris-re | 8 (16) | 8 | 9 | 9 | 5 | **47** | Portfolio page only; relabel + strip stats |
| **Tom N Jerry's Sports Bar** | tomnjerrys-website | 10 (20) | 8 | 3 | 7 | 9 | **47** | **HOLD — needs 6 real photos + menu page** |
| The Enchanted Rosie | the-enchanted-rosie / enchantedrose | 6 (12) | 9 | 3 | 8 | 7 | **39** | **DROP from homepage** until product photos land |
| Gray Photography | gray-photography | 6 (12) | 6 | 3 | 7 | 4 | **32** | **KILL** |
| Golf Balls Everywhere | golfballs-everywhere | 5 (10) | 7 | 1 | 6 | 5 | **29** | **KILL** |

### Tier B — apps & tools (low buyer relevance regardless of quality)

| Project | URL | Buyer ×2 | Visual | Complete | Mobile | Story | **Total** | Verdict |
|---|---|---|---|---|---|---|---|---|
| PawChart | pawchart-lac | 2 (4) | 9 | 8 | 8 | 8 | **37** | Demote to portfolio page, bottom section |
| Prospect Finder | prospect-finder-olive | 1 (2) | 6 | 6 | 5 | 6 | **25** | Remove from public site |
| Job Hunter | job-hunter-theta-tan | 1 (2) | 5 | 5 | 5 | 5 | **22** | Remove from public site |
| DraftIQ (fantasy football) | fantasy-football-draft-assistant | 1 (2) | 6 | 5 | 2 | 5 | **20** | Not portfolio material |
| Reel (video editor) | video-editor-kappa-six | 1 (2) | 6 | 4 | 2 | 4 | **18** | Not portfolio material |
| Ticket Email Generator | ticket-emailer-deploy | 1 (2) | 4 | 4 | 4 | 4 | **18** | Internal tool |
| CompTIA A+ Study Guide | comptia-deploy | 1 (2) | 5 | 7 | 6 | 4 | **24** | Personal study tool |

### Tier C — gaming / streaming / stale (out of scope entirely)

| Project | URL | Note |
|---|---|---|
| BO2 Weapon Builds | bo2-weapon-builds | Gaming content site. Well built (4697px), zero buyer relevance. |
| Apex Builds | apex-builds-five | Gaming meta guide. Zero buyer relevance. |
| BTF Leekyy Stinger | btf-leekyy-stinger | OBS stinger transition tool. `/out/btf-stinger.webm` fails to load. |
| BTF Leekyy Overlay | btf-leekyy-overlay | 1920×1080 stream overlay. Not a website. |
| **nichols-pool-service** | nichols-pool-service | ⚠️ **Serves the OLD Fletch Media Collective site. See §3.** |
| **portfolio** | portfolio-tau-flax-87 | ⚠️ **Serves the OLD Fletch Media portfolio. See §3.** |
| enchantedrose | enchantedrose | Duplicate of `the-enchanted-rosie` (byte-identical, 35080). Delete one. |
| ai-test-website | www.fletcherwebstudio.com | Your live site. |

---

## 3. 🔴 HONESTY LIABILITY — two live deployments still carry the fabricated content you removed

This is the most urgent finding in the audit and it is unrelated to which projects you feature.

**`https://nichols-pool-service.vercel.app`** does not serve Nichols Pool Service. It serves the pre-audit **Fletch Media Collective** site, publicly, right now, containing:

- `50+ SITES LAUNCHED`
- `3M+ VIEWS GENERATED`
- `98% CLIENT RETENTION`
- A **"TRUSTED BY LOCAL BUSINESSES"** logo marquee naming Barnaby's, Gray Photography, Nichols Pool Service, Enchanted Rosie, Gabrielle Design, PawChart, and Prospect Finder as clients.

`https://portfolio-tau-flax-87.vercel.app` serves the matching old portfolio page.

These are exactly the invented statistics and fake client logos your audit stripped from fletcherwebstudio.com. They are indexable, linkable, and the project name makes `nichols-pool-service.vercel.app` a URL someone could plausibly guess or be sent.

**Action: delete both Vercel projects today.** `vercel remove nichols-pool-service` and `vercel remove portfolio`. This is not a portfolio decision, it's a cleanup.

### Other honesty flags

| Project | Issue | Action |
|---|---|---|
| Michael Harris RE | `$42M+ in closed transactions`, `150+ families helped`, `98% client satisfaction`, `5★ average rating`, plus a stock-photo headshot. This is a **fictional agent persona** — those numbers describe nobody. | Label unambiguously as a concept build **and delete the four stat tiles.** Invented numbers on a concept build are still invented numbers. |
| Putt-Putt | `4.6★ · 652 GOOGLE REVIEWS` | Verify against the real Google listing before featuring, or remove the tile. |
| Nichols | `Happening List Winner — Bucks County's Best · 2025`, `65+ years`, `CPO Certified` | Verify against nicholspoolservice.com before featuring. |
| Barnaby's | `500+ five-star reviews`, `27 years` | Sourced from the real business. Fine **only** while the concept-build label stays. Keep that framing. |
| Barnaby's / Nichols / Golf Balls | Images are **hotlinked** from popmenucloud.com, nicholspoolservice.com, and golfballseverywhere.com respectively. | Third-party bandwidth, and they break without warning. Self-host before featuring. |

### Client vs. concept — I cannot verify this and have not assumed it

Everything below needs **your** confirmation before any label is written. What the evidence shows:

- **Esthie Bestie CAS** — serves locally-hosted real photos (`/nacasphotos/*.jpeg`, `/Before.png`) and a custom `CasLogo.png`. Strongly suggests a real engagement.
- **The Enchanted Rosie** — links to `poshmark.com/closet/gabriellewhelan` and a real Instagram. Strongly suggests a real engagement.
- **Putt-Putt** — custom mascot asset, real pricing, real owner name ("Rob"), real social links.
- **Nichols, Barnaby's, Tom N Jerry's, Michael Harris, Golf Balls** — no evidence either way from the build.

---

## 4. QA kill list — with evidence

| Project | Defect | Confirmed by |
|---|---|---|
| **Golf Balls Everywhere** | **All 19 internal links 404.** `/shop`, `/about`, `/contact`, `/grading-scale`, and all 14 `/brand/*` pages. Every nav item is dead. | HTTP 404 on all |
| **Gray Photography** | **All 6 images are `picsum.photos` random stock.** A photography portfolio containing none of the photographer's photographs. Nav also overlays the gallery with no background bar; masonry grid has large empty black gaps. Copy self-describes as *"Amateur photography."* | Image src audit |
| **Tom N Jerry's** | **All 6 images are `placehold.co`** gray boxes reading "Big Screen", "Bar Area", "Live Music", "Game Day", "Patio", "Wings". The `MENU` nav link 404s. Headline clips off the right edge at 390px. | Image src audit + HTTP 404 |
| **The Enchanted Rosie** | **12 of 14 images are `placehold.co`.** Product grid renders gold "?" icons. | Image src audit |
| **Barnaby's** | `<h1>` computes to `16px` — no CSS rule matches (element has no class). Persists after 9s wait, so it is not an animation artifact. Mobile nav collides with logo and overflows viewport. | `getComputedStyle` + screenshots |
| **Nichols** | No mobile breakpoint on the nav. Desktop nav renders at phone width, "Contact" cut off, logo drops out. | 390px screenshot |
| **DraftIQ** | Horizontal scroll at 390px (content 421px wide). | scrollWidth check |
| **BTF Stinger** | `/out/btf-stinger.webm` request fails; the advertised download is dead. | requestfailed |

Everything else returns 200 and renders. No console errors anywhere in the account.

---

## 5. RECOMMENDATION — the homepage lineup

### Ship **four**, not five.

You invited this and it's the right call. There is no honest fifth tile today. A fifth weak card costs you more than an empty slot, and you already have the "See the Full Portfolio" tile to fill the grid.

| # | Project | Slot | Reasoning |
|---|---|---|---|
| **1** | **Barnaby's Restaurant & Pub** | **LARGE FEATURE** | A Havertown pizza shop owner opening this sees a Havertown restaurant. Same town, same category, same customer. Nothing else you own converts that buyer as directly. 5 pages, real photography, full customer journey. **Gated on two fixes — see below.** |
| **2** | **Putt-Putt Fun Center** | standard | The most complete, most distinctive, most *finished* thing in your account. Custom mascot, real pricing ($7.50/18 holes, 25¢ token, $229 party package), 5 working pages, flawless at 390px. Family entertainment reads as hospitality to a restaurant buyer. Ships today, no fixes. |
| **3** | **Esthie Bestie CAS** | standard | Salon — a named target vertical. Real client photography, real prices, a genuine pricing mechanism (the "Bestie Bundle" prepay). Elegant dark/gold craft that doesn't look like a template. Ships today. |
| **4** | **Nichols Pool Service** | standard | Trades — your other named vertical, and the only one currently represented by nothing. 70-year-old family business, real owner, before/after gallery, 7467px of real content. **Gated on one fix.** |
| — | *"See the Full Portfolio" tile* | fills slot 5 | Keep it. |

### The large feature slot

**Barnaby's — but do not ship it large until both fixes land.**

The tie between Barnaby's and Putt-Putt is the closest call in this audit, and the panel split on it:

- **The Mobile Reviewer voted Putt-Putt** and voted hard. Barnaby's is broken on the exact device the buyer is holding. Shipping a broken nav in the largest tile is the worst possible failure.
- **The Buyer (double weight) voted Barnaby's** — "that's the place on West Chester Pike, I know it." Category and town match beat everything else for her.
- **The QA Engineer voted Putt-Putt** on the 16px `<h1>` alone.
- **The Visual Designer split**, calling Putt-Putt more distinctive but Barnaby's more credible as commercial work.

**How the Strategist broke it:** the Buyer's double weight decides the *destination*, the QA Engineer decides the *timing*. Both Barnaby's defects are small CSS fixes — one missing rule and one missing breakpoint, well under an hour. It is not worth permanently downgrading your single best-targeted asset to avoid an hour of work.

**So: fix Barnaby's, then feature it large. Until the fixes ship, Putt-Putt takes the large slot.** Do not ship Barnaby's large in its current state.

### Dropped from the current lineup

| Drop | Why |
|---|---|
| **PawChart** (currently the large feature) | Buyer relevance 2/10 in your largest, most prominent slot. It is beautiful, and it is answering a question no local business owner asked. Move to portfolio page. |
| **Job Hunter** | Buyer relevance 1/10. An AI resume tool tells a pizza shop owner nothing. Also the thinnest build of the three apps (900px, single upload screen). Remove entirely. |
| **Prospect Finder** | Buyer relevance 1/10 — and it is *the tool you use to cold-call them*. Showing prospects the machine that generated their phone call is an unforced own-goal. **Remove from the public site entirely.** |
| **The Enchanted Rosie** | Not a category problem — a finish problem. Gold "?" boxes where products should be. Restore when Gabrielle's product photos are in. |

---

## 6. Hidden in your account and deserving promotion

Ranked by what they unlock:

1. **Putt-Putt Fun Center** — the single best unfeatured asset. Should have been on the homepage already.
2. **Esthie Bestie CAS** — your only salon build, a named target vertical, real client assets.
3. **Nichols Pool Service** — your only trades build. Trades are a large share of your cold-call list and you currently show them nothing.
4. **Tom N Jerry's Sports Bar** — *highest upside in the account.* Excellent bones (5986px, sharp yellow-on-green identity, strong hero) held back by 6 placeholder tiles and one 404. Swap in real photos and fix `/menu/` and this becomes a top-3 tile. Delaware County sports bar — near-perfect buyer match.
5. **Michael Harris Real Estate** — genuinely well built, 6 working pages, clean mobile. Held back only by the invented stats. Strip those, label it a concept build, park it on the portfolio page.

---

## 7. Should portfolio.html carry a longer list?

**Yes — but structured, not just longer.** The homepage answers "can he build my kind of site?" The portfolio page answers "is there enough of it to trust?" Two different jobs.

### Recommended portfolio.html structure

**Section 1 — Local Business Websites** *(the section that sells)*

1. Barnaby's Restaurant & Pub — *concept build* (after fixes)
2. Putt-Putt Fun Center
3. Esthie Bestie CAS
4. Nichols Pool Service (after mobile fix)
5. Michael Harris Real Estate — *concept build*, stats removed
6. Tom N Jerry's Sports Bar — *hold until real photos land*
7. The Enchanted Rosie — *hold until product photos land*

**Section 2 — Tools & Prototypes** *(below the fold, visually smaller, clearly secondary)*

8. PawChart

One app, not three. It exists to answer the occasional "could you also build us a booking system?" — not to demonstrate range to developers. Job Hunter and Prospect Finder do not belong on a site whose only job is convincing a shop owner you can build her website.

---

## 8. Diff — exact changes

> **Not implemented.** Reporting only, per your instruction.

### `index.html`

**Mobile grid — `index.html:1849–1894`**

```
- REMOVE  PawChart            (pawchart-screenshot.webp)      line 1851–1859
- REMOVE  Enchanted Rosie     (enchanted-rosie-screenshot.webp) line 1862–1870
- REMOVE  Job Hunter          (job-hunter-screenshot.webp)    line 1873–1881
- REMOVE  Prospect Finder     (prospector-screenshot.webp)    line 1884–1892
+ ADD     Barnaby's           (barnabys-screenshot.webp)      ← currently desktop-only
+ ADD     Putt-Putt Fun Center (puttputt-screenshot.webp)     ← NEW ASSET NEEDED
+ ADD     Esthie Bestie CAS   (esthie-screenshot.webp)        ← NEW ASSET NEEDED
+ ADD     Nichols Pool Service (nichols-screenshot.webp)      ← NEW ASSET NEEDED
```

**Desktop grid — `index.html:1897–1955`**

```
- REMOVE  PawChart from LARGE slot        line 1899–1908
- REMOVE  Job Hunter                      line 1922–1931
- REMOVE  Prospect Finder                 line 1934–1942
- REMOVE  Enchanted Rosie                 line 1911–1920
~ MOVE    Barnaby's  small slot → LARGE slot  (line 1944 → 1899)
+ ADD     Putt-Putt Fun Center
+ ADD     Esthie Bestie CAS
+ ADD     Nichols Pool Service
= KEEP    "See the Full Portfolio" tile   line 1952
```

**Result:** desktop and mobile grids finally carry the *same four projects*. Right now they don't, and the one that differs is your best one.

### `portfolio.html`

```
= KEEP     Barnaby's Restaurant & Pub   line 665–680   (keep "concept build" label verbatim)
~ RELABEL  The Enchanted Rosie          line 685–700   → move to hold section, or drop until photos
~ DEMOTE   PawChart                     line 705–720   → move to new "Tools & Prototypes" section
- REMOVE   Job Hunter                   line 725–740
- REMOVE   Prospect Finder              line 745–760
+ ADD      Putt-Putt Fun Center         → https://puttputt-fun-center.vercel.app
+ ADD      Esthie Bestie CAS            → https://esthie-bestie-cas.vercel.app
+ ADD      Nichols Pool Service         → https://nichols-deploy.vercel.app   ⚠ NOT nichols-pool-service
+ ADD      Michael Harris Real Estate   → https://michael-harris-re.vercel.app  (concept build, stats stripped)
+ ADD      section heading "Tools & Prototypes" above PawChart
```

⚠️ **The correct Nichols URL is `nichols-deploy.vercel.app`.** `nichols-pool-service.vercel.app` serves the old Fletch Media site (§3). Linking the intuitive-sounding one would point buyers straight at the fabricated statistics.

### Screenshot assets to capture

Match the existing `<name>-screenshot.webp` convention in the project root:

| File | Source URL | Notes |
|---|---|---|
| `puttputt-screenshot.webp` | puttputt-fun-center.vercel.app | Hero at 1440px — the "LET'S GO PLAY." headline with the mascot |
| `esthie-screenshot.webp` | esthie-bestie-cas.vercel.app | Hero at 1440px — includes the lash photo and pricing cards |
| `nichols-screenshot.webp` | nichols-deploy.vercel.app | Hero at 1440px — pool photo, "Happening List Winner" badge |
| `tomnjerrys-screenshot.webp` | tomnjerrys-website.vercel.app | **Hold** until placeholder photos are replaced |
| `barnabys-screenshot.webp` | — | **Re-capture after the `<h1>` fix.** The existing asset shows the 16px headline bug. |

Existing and still valid: `enchanted-rosie-screenshot.webp`, `pawchart-screenshot.webp`.
Retire when cards are removed: `job-hunter-screenshot.webp`, `prospector-screenshot.webp`.

There is also an unused **`gabrielles-screenshot.webp`** already sitting in the project root with no card referencing it — worth resolving alongside the Enchanted Rosie decision.

---

## 9. Do these first, in this order

1. **`vercel remove nichols-pool-service` and `vercel remove portfolio`** — kills the live fabricated stats and fake client logo bar. Nothing else on this list matters as much.
2. **Fix Barnaby's `<h1>`** — no CSS rule matches the element (it has no class). One rule.
3. **Add a mobile nav breakpoint to Barnaby's and Nichols** — both render desktop nav at 390px with no hamburger.
4. **Verify or remove** the Putt-Putt Google review count and the Nichols 2025 award.
5. **Delete the four Michael Harris stat tiles.**
6. Capture the three new screenshot assets, re-capture Barnaby's.
7. Ship the four-tile homepage.
8. **Then** chase Tom N Jerry's photos — it's your best remaining upside.

---

## Panel disagreements, on record

| Question | Split | Resolution |
|---|---|---|
| Large feature: Barnaby's or Putt-Putt? | Buyer (×2) + Visual → Barnaby's. QA + Mobile → Putt-Putt. | **Barnaby's, gated on fixes; Putt-Putt in the interim.** Buyer weight sets the destination, QA sets the timing. |
| Keep PawChart anywhere? | Visual Designer argued it's the best-crafted asset in the account and cutting it wastes real quality. Buyer: "I don't have a dog." | **Portfolio page only, below the fold, under "Tools & Prototypes."** Craft is real but it is answering an unasked question. |
| Four tiles or five? | Mobile Reviewer wanted five for grid symmetry. QA refused to pass any fifth candidate. | **Four.** The "See the Full Portfolio" tile already fills the slot, and no fifth project passes QA honestly today. |
| Ship Tom N Jerry's now with placeholders? | Buyer loved the hero and voted yes. QA vetoed. | **QA veto upheld.** Six gray boxes reading "Wings" is the exact impression that loses the call. |
| Enchanted Rosie — drop or fix? | Visual Designer defended the craft (genuinely strong). QA pointed at the "?" icons. | **Drop from homepage, hold on portfolio page.** The build is good; it just isn't finished. |
