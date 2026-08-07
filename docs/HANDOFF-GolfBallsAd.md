# Golf Balls Everywhere — Instagram Ad Handoff

**Client:** Golf Balls Everywhere
**Format:** Instagram Reel / Story (1080 × 1920, vertical)
**Duration:** 30 seconds (900 frames @ 30fps)
**Built with:** Remotion 4.0.438, React, TypeScript
**Ad Framework:** Alex Hormozi — $100M Leads (Hook → Offer → Proof → CTA)

---

## Project Location

```
myvideonew/
├── src/
│   ├── GolfBallsAd.tsx       ← The ad composition (all scenes)
│   └── Root.tsx              ← Registers both compositions
├── public/
│   └── gbe-logo.png          ← Golf Balls Everywhere logo (local copy)
└── package.json
```

---

## How to Preview

1. Open a terminal in `myvideonew/`
2. Run the dev server:
   ```bash
   npm run dev
   ```
3. Open **http://localhost:3001** (or 3002 if 3001 is taken)
4. Select **`GolfBallsAd`** from the left sidebar

Use the scrubber at the bottom to step through the timeline.

---

## How to Export (Render to MP4)

```bash
npx remotion render GolfBallsAd out/golf-balls-ad.mp4
```

For Instagram-optimized output (H.264, high quality):
```bash
npx remotion render GolfBallsAd out/golf-balls-ad.mp4 --codec h264 --crf 18
```

The output file will be at `myvideonew/out/golf-balls-ad.mp4`.

---

## Ad Framework — Hormozi $100M Leads

Each scene maps to a specific stage of Hormozi's conversion framework:

| Scene | Role | Principle |
|-------|------|-----------|
| **1 — Hook** | Stop the scroll | Lead with the customer's PAIN, not your brand |
| **2 — Offer** | Make the deal irresistible | Specific numbers + handle the objection ("but they're used") |
| **3 — Proof** | Remove all reasons to say no | Social proof + risk reversal (money-back guarantee) |
| **4 — CTA** | Tell them exactly what to do | Callback to hook + urgency + repeat the guarantee |

---

## Scene Breakdown

| Scene | Global Frames | Local Duration | Content |
|-------|--------------|----------------|---------|
| **1 — Hook** | 0 – 240 | 8.0s | "STILL PAYING $50+ A DOZEN?" slams in, agitation copy, logo reveals as the solution, "There's a smarter way.", stock badge |
| *Fade transition* | 225 – 240 | 0.5s | 15-frame cross-dissolve |
| **2 — Offer** | 225 – 465 | 8.0s | "The Smarter Choice" label, TITLEIST / CALLAWAY / TAYLORMADE animate in (staggered), price "FROM $28.99 / DOZEN", savings context, objection handler badge |
| *Fade transition* | 450 – 465 | 0.5s | 15-frame cross-dissolve |
| **3 — Proof** | 450 – 690 | 8.0s | "50,000+ Golfers Can't Be Wrong", 70% / 50K+ / FREE stats pop in, 100% Money-Back Guarantee card |
| *Fade transition* | 675 – 690 | 0.5s | 15-frame cross-dissolve |
| **4 — CTA** | 675 – 900 | 7.5s | Brand ticker, logo, "STOP / OVERPAYING." spring pop-out, SHOP NOW button, URL, urgency line, guarantee badge |

**Frame math:** (240 + 240 + 240 + 225) − (15 + 15 + 15) = 945 − 45 = **900 frames**

---

## Scene 1 — Hook: Animation Timeline

| Frame | Event |
|-------|-------|
| 4 | "STILL PAYING" slides in from top |
| 14 | "$50+ A DOZEN?" bounces up from bottom (lime gradient) |
| 38 | Agitation copy fades in: *"Most golfers overpay by 3× every single round"* |
| 70 | Logo springs in on white card (slow, weighty entrance) |
| 100 | "There's a smarter way." slides up |
| 118 | "50,000+ Balls in Stock" badge fades in |

---

## Scene 2 — Offer: Animation Timeline

| Frame | Event |
|-------|-------|
| 0 | "The Smarter Choice" label fades in |
| 5 | TITLEIST slides up |
| 28 | CALLAWAY slides up (lime gradient) |
| 42 | Divider line draws across |
| 52 | TAYLORMADE slides up |
| 58 | "FROM $28.99 / DOZEN" scales in |
| 80 | "$30+ savings per dozen vs. the pro shop" slides up |
| 100 | "Rigorously cleaned & graded to near-mint" badge fades in |

---

## Scene 3 — Proof: Animation Timeline

| Frame | Event |
|-------|-------|
| 0 | "50,000+ Golfers Can't Be Wrong" fades in |
| 10 | Lime divider line draws |
| 22 | "70% Off Retail Prices" springs in |
| 44 | "50K+ Balls Always in Stock" springs in |
| 66 | "FREE Shipping Over $79" springs in |
| 100 | "100% Money-Back" guarantee card scales in |

---

## Scene 4 — CTA: Animation Timeline

| Frame | Event |
|-------|-------|
| 5 | Brand ticker fades in at top |
| 10 | Logo springs in |
| 28 | "STOP / OVERPAYING." bounces in with spring overshoot + lime glow bloom |
| 44 | "SHOP NOW" lime button scales in |
| 62 | golfballs-everywhere.com fades in |
| 76 | "Stock changes daily — order today" urgency line slides up |
| 95 | "100% Money-Back Guarantee" badge fades in |

---

## Customization Guide

All editable values are at the top of `src/GolfBallsAd.tsx`.

### Brand Colors
```ts
const LIME        = "#8DC63F";   // Primary lime green
const LIME_BRIGHT = "#B4E542";   // Gradient highlight
const BG          = "#040900";   // Background (near-black, green-tinted)
```

### Logo
Logo is stored locally at `public/gbe-logo.png`.
To update it, replace that file with a new PNG (same filename).
> Note: The logo has a white background — it sits on a white frosted card intentionally. If a transparent-background version is available, the card `background` can be removed or set to `transparent`.

### Copy — Quick Find

| Text | Search for |
|------|-----------|
| Hook line 1 | `"STILL PAYING"` |
| Hook line 2 | `"$50+ A DOZEN?"` |
| Agitation | `"Most golfers overpay"` |
| Payoff | `"There's a smarter way."` |
| Stock badge | `"50,000+ Balls in Stock"` |
| Scene 2 label | `"The Smarter Choice"` |
| Price | `"FROM $28.99 / DOZEN"` |
| Savings context | `"$30+ savings per dozen"` |
| Objection handler | `"Rigorously cleaned"` |
| Proof header | `"50,000+ Golfers Can't Be Wrong"` |
| Guarantee | `"100% Money-Back"` |
| CTA hook callback | `"STOP"` / `"OVERPAYING."` |
| URL | `"golfballs-everywhere.com"` |
| Urgency | `"Stock changes daily"` |

### Ticker Brands
The scrolling brand ticker in Scene 4 is defined near the top of the file:
```tsx
const BRANDS = ["Titleist", "·", "Callaway", "·", "TaylorMade", "·",
                "Srixon", "·", "Bridgestone", "·", "Nike", "·", "Vice", "·"];
const TICKER_ITEM_W = 230; // px per item — increase if a brand name clips
```

### Brand Name Delays (Scene 2)
To adjust how fast each brand name appears:
```tsx
<Word word="TITLEIST"   frame={frame} delay={5}  fontSize={96} />
<Word word="CALLAWAY"   frame={frame} delay={28} fontSize={96} isGradient />
<Word word="TAYLORMADE" frame={frame} delay={52} fontSize={80} />
```
`delay` is in frames. Increase gaps between values to slow them down further.

### Timing
Scene durations are set at the bottom of `GolfBallsAd.tsx` inside `<TransitionSeries>` and mirrored in `Root.tsx`:
```tsx
// GolfBallsAd.tsx
<TransitionSeries.Sequence durationInFrames={240}> // Scene 1
<TransitionSeries.Sequence durationInFrames={240}> // Scene 2
<TransitionSeries.Sequence durationInFrames={240}> // Scene 3
<TransitionSeries.Sequence durationInFrames={225}> // Scene 4

// Root.tsx
durationInFrames={900}  // Must match the total (945 - 45 transition overlap)
```

### Adding Music
Place an MP3 in `public/` and add to the main composition:
```tsx
import { Audio } from "remotion";
// Inside GolfBallsAd return:
<Audio src={staticFile("music.mp3")} volume={0.6} />
```

---

## Background System

Every scene uses three layered background components:

| Component | Purpose |
|-----------|---------|
| `<GlowBg>` | Pulsing radial green glow — intensity varies per scene |
| `<AnimatedBg>` | 4 expanding ring pulses + 2 diagonal sweeping light rays |
| `<Grain>` | SVG noise overlay (opacity 0.045) for film texture |

`AnimatedBg` ring period is 90 frames. To speed up the rings, lower `RING_PERIOD`. To make the sweep rays faster, increase the multiplier on `frame * 2.2` and `frame * 1.3`.

---

## Installed Packages

| Package | Version | Purpose |
|---------|---------|---------|
| `remotion` | 4.0.438 | Core video rendering |
| `@remotion/cli` | 4.0.438 | Studio + render CLI |
| `@remotion/transitions` | 4.0.438 | Fade transitions between scenes |
| `@remotion/google-fonts` | 4.0.438 | Montserrat + Roboto fonts |
| `@remotion/tailwind-v4` | 4.0.438 | Tailwind (available, not used in ad) |

---

## Fonts Used

| Font | Weights | Usage |
|------|---------|-------|
| **Montserrat** | 300, 400, 700, 800, 900 | Headlines, hook text, stat numbers, CTA, brand names |
| **Roboto** | 300, 400, 500 | Labels, body copy, agitation text, URLs |

---

## Design Tokens

| Token | Value | Notes |
|-------|-------|-------|
| Primary green | `#8DC63F` | Matches logo lime green |
| Bright green | `#B4E542` | Gradient highlight end — used on hook line 2, CALLAWAY, price |
| Background | `#040900` | Near-black with green tint |
| Heading tracking | `-0.03em` to `-0.05em` | Tight, sporty feel |
| Body line-height | `1.7` | Used on agitation/body copy |
| Spring (hook text) | `damping: 10–12, stiffness: 140–160` | Snappy, high-energy entrance |
| Spring (logo) | `damping: 11, stiffness: 65, mass: 1.3` | Slower, weighty entrance |
| Spring (stats) | `damping: 10, stiffness: 90` | Bouncy pop-in |
| Spring (STOP OVERPAYING) | `damping: 7, stiffness: 180, mass: 0.6` | Aggressive overshoot with glow bloom |
| Spring (CTA button) | `damping: 10, stiffness: 120` | Punchy scale-in |

---

## Notes

- **Golf ball particles** — CSS radial-gradient circles, no image assets needed. 24 particles in Scene 1 and 4, seeded with a deterministic `rand()` function so they look random but render identically every frame.
- **Ticker** — Each brand item is `230px` wide (previously `160px` — was causing overflow/bleed on long names like BRIDGESTONE and TAYLORMADE). If you add a longer brand name, increase `TICKER_ITEM_W`.
- **"STOP OVERPAYING" spring** — Uses very low damping (7) for a visible overshoot bounce. The glow blooms in after the spring settles (`interpolate(recallSpr, [0.6, 1], [0, 1])`).
- All animations use `transform` and `opacity` only — no `transition-all`, as required for correct Remotion rendering.
- CSS animations and Tailwind animation classes are not used (they do not render correctly in Remotion).
