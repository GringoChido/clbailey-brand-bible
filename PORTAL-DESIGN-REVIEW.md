# C.L. Bailey & Co. — Design Review & Brand Suggestions

*Reviewed: the live portal (clbailey-brand-bible.netlify.app), `portal/index.html` + `style.css`, against `GUARDRAILS.md`, `spec/BRAND_BIBLE.md`, and `spec/PHOTOGRAPHY.md`. June 2026.*

This is suggestions only — nothing here removes content or asks you to cut a module. Each item names the guideline it traces back to, per the project's own rule (CLAUDE.md: "when you make a notable brand call, name the rule behind it"). Items are grouped into three buckets you asked for: visual polish, brand-compliance, and broader C.L. Bailey branding.

---

## The short version

The portal is genuinely good. The editorial, typography-led system — full-bleed charcoal hero, oversized screened-back chapter numerals, ruled hairline tables, square corners, no shadows — lands the "heritage standards manual" intent cleanly, and the accessibility fundamentals (skip link, `:focus-visible`, `prefers-reduced-motion`, ARIA-labeled figures, keyboard-operable swatches) are already in place. The interactive palette and vault both work.

The highest-leverage fixes are small and specific:

1. **The headline typeface isn't actually loading** — the portal renders Le Jour Serif's fallback (Georgia/Times), so the canonical reference isn't showing the canonical face.
2. **The portal breaks its own contrast law** — the bronze "MODULE 0X" eyebrows (and the link-hover color) are Aged Bronze on Warm White, the exact 2.8:1 pairing Module 7 flags as failing.
3. **Headline CSS asks for weight 500 + negative tracking + italic tagline**, all of which contradict the "Le Jour Serif 400 only, never bolded, never italicized, normal tracking" rule (§2.5.1).

None of these are big jobs. Details below.

---

## 1 · Visual design polish (the portal)

**1.1 — Load the real headline font. (Biggest visual gap.)**
The `<head>` loads Roboto, Roboto Condensed, and Raleway from Google Fonts, but **not Le Jour Serif**. The `--serif` token is `"leJourSerif", "Le Jour Serif", Georgia, …`, so with no `@font-face` and no link, every headline falls through to Georgia/Times. The screenshots confirm it — the hero, module titles, and card titles are all rendering in a generic serif. For the surface that's supposed to *be* the design reference, this is the one fix that most changes how on-brand it looks. Self-host the licensed Le Jour Serif webfont (the spec says the files live in the vault, `02_Color_Type/`) with a proper `@font-face`, and keep Georgia as the documented fallback. Ref: §2.5.1, §2.5.6.

**1.2 — Tighten the hero balance.**
The hero's right half is empty next to the oversized "01" numeral, which leaves the headline and lede hugging the left edge on wide screens. It reads a little lopsided. Either pull the `hero-meta` row up into that whitespace, or let the lede run slightly wider — a small thing, but it's the first impression.

**1.3 — Body/caption floor.**
Card bodies, table cells, and TOC descriptions render at 13px (`--fs-caption`). The bible sets a 14px minimum body size (§2.5.2). It still passes contrast (Mid Gray on Warm White is 5.4:1), but nudging card/table reading text to 14px would match your own floor and read easier.

**1.4 — `--ink-ghost` (#9C958D) is doing too much.**
It's used for the TOC "§" page markers, the type-row sub-labels, and the clear-space ticks — all on Warm White, where it lands around ~2.6:1 and fails AA. For anything that's actually a label (not pure decoration), step it up to Mid Gray or Graphite. Ref: §7.2.

**1.5 — Favicon.**
The portal sets no `<link rel="icon">` at all, so browsers show a blank default in the tab. Until the Crest exists (see 3.1), even a single-color simplified mark on a Warm White tile would look more finished than nothing. Ref: §2.1.3 / §2.1.4 (acknowledged open item).

---

## 2 · Brand-compliance findings (portal vs. its own guardrails)

Severity uses the project's convention: a **MUST** violation is fix-before-ship; everything else is a deviation worth tidying.

| # | Finding | Guideline | Severity |
|---|---------|-----------|----------|
| 2.1 | **Bronze "MODULE 0X" eyebrows are Aged Bronze text on Warm White (~2.8:1).** Visible on every module header. This is the exact pairing Module 7's own table marks "Fails — accent only, never text on light grounds." | §2 visual, §5/§7.2 accessibility, GUARDRAILS §2 | **MUST** |
| 2.2 | **Link hover sets text to bronze** (`a:hover { color: var(--bronze) }`). Body links sit on the light ground, so hover drops them to the failing 2.8:1. Use Deep Charcoal or an underline on hover instead. | §7.2 | **MUST** |
| 2.3 | **Headlines set to `font-weight: 500`** (`h1, h2, .chapter-num`). Le Jour Serif is a single-weight 400 family that is "never bolded, faux-bolded, or italicized." Once the real font loads (1.1), 500 forces a synthesized faux-bold. Set headlines to 400. | §2.5.1 | **MUST** |
| 2.4 | **Hero tagline is italic** (`.hero .tagline { font-style: italic }`). Same rule — Le Jour Serif is never italicized. Render it upright; the brass underline already gives it emphasis. | §2.5.1 | **MUST** |
| 2.5 | **Headline letter-spacing is `-0.02em`.** The type spec calls for normal tracking at display sizes (only `.heading-sub` carries +0.5px). Remove the negative tracking. | §2.5.1 | deviation |
| 2.6 | **`h3`/`h4` and `.block-title` use Raleway 700.** Labels are specified at Raleway 500/600. Drop to 600. | §2.5.3 | deviation |
| 2.7 | **Masthead logo (40px) and footer logo (48px) sit far below the Primary mark's 180px floor.** This is the same class of issue the spec already concedes for the favicon: the badge is being used where the (not-yet-built) Secondary Lockup belongs. Not a fault of the build so much as evidence for 3.1. | §2.3, §2.1.4 | deviation (blocked on asset) |
| 2.8 | **Vault mock-data type tags mismatch filenames** — `CLB-LOGO-PrimaryMark-Full-v01.png` and the Velocity `.png` are tagged `JPG` in the table. Cosmetic, but this is the *naming-and-hygiene* showcase, so it should be exact. | §2.7 | minor |

What's already compliant and worth protecting: Heritage Green appears only in the mark and the palette swatch (labeled "Mark & Felt"), never as UI; the 60/30/10 grounding reads correctly; motion/transition timings sit inside the §2.8 envelope and `prefers-reduced-motion` is honored; the legal micro-line, CTA language ("Find a Dealer"), Oxford commas, and exclamation discipline all hold; alt text on the figures follows the pattern.

---

## 3 · Broader C.L. Bailey branding (beyond the portal)

You asked for help with the brand, not just the page. The portal is healthy; the brand's real exposure lives on clbailey.com and in the asset library. Most of this is already diagnosed inside `spec/PHOTOGRAPHY.md` — I'm surfacing it because it's higher-leverage than anything on the portal, and it's easy to leave buried in a spec file.

**3.1 — Commission the Crest and the Secondary Lockup. (The #1 structural gap.)**
The spec is candid that only the Primary badge exists in production (§2.1.4). That single gap is what forces the failing favicon, the under-size nav/footer marks (2.7), the missing social avatar, and the rail nameplate to all stay unsolved. The Crest unblocks four touchpoints at once; the Lockup unblocks every header, email signature, and co-op footer. The spec already names this the top open asset action — it's worth treating as a funded project, not a someday.

**3.2 — Make the felt Heritage Green everywhere. (Highest-ROI recognition move.)**
`PHOTOGRAPHY.md` F-3 documents felt appearing in burgundy, blue, purple, black, tan, and green across live surfaces. The felt is the single largest branded surface in any product photo, and the brand already owns exactly one green. Standardizing the playing surface on `#006840` does more for shelf recognition than any logo placement — and you already have green-felt Skylar assets to build from. Ref: §10.3 (the felt law).

**3.3 — Rename the AI-generated image files. (Reputational, this-week item.)**
F-1: production image URLs still contain raw generation prompts and "Nano_Banana" in the filename (e.g. `SHOT_4_The_Dining_Conversion…Nano_Banana…`). Anyone who right-clicks an image on a "built by hand" brand can read that the lifestyle photography was generated, with the prompt attached. Rename to the §10.7 framework before anything else; it's exposure, not housekeeping.

**3.4 — Shoot the Tomball workshop.**
F-7: there's no real library of the actual shop floor — saws, the finish room, slate leveling, the people. It's the one image set no competitor can copy and the one place AI imagery would be an actual lie rather than an illustration (§10.6 bans generated provenance). Two days of real photography becomes the proof layer under everything else.

**3.5 — Close the Spanish + machine-readability gaps on the live site.**
The spec flags these as live violations: untranslated nav labels on `/es` (§3B.6), no `hreflang` pairs anywhere on clbailey.com (§11.5), and missing Organization/Product JSON-LD (§11.2). With AI assistants increasingly the discovery layer, the structured-data and bilingual-parity fixes are cheap and compounding — the brand states exact, verifiable claims, which is exactly what gets cited.

---

## Quick-win punch list (portal, in order)

1. Add the Le Jour Serif `@font-face` so the reference shows the real headline face. *(1.1)*
2. Change module eyebrows + link-hover off bronze-on-light to Graphite. *(2.1, 2.2)*
3. Set headlines to weight 400, upright, normal tracking. *(2.3, 2.4, 2.5)*
4. Bump `--ink-ghost` labels and 13px reading text up to AA-safe / 14px. *(1.4, 1.3)*
5. Add a favicon; fix the two vault type tags. *(1.5, 2.8)*

Items 1–3 are an hour of CSS and resolve every MUST-level flag. Everything in section 3 is brand-program work that sits above the portal.

*Nothing here was changed in the files — these are recommendations for your review.*
