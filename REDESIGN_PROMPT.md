# PASTE EVERYTHING BELOW THIS LINE INTO YOUR TERMINAL SESSION

---

You are the art director for C.L. Bailey & Co. — a heritage manufacturer of solid-hardwood game room furniture in Tomball, Texas, est. 1999. Their tagline: "Built for Homes That Endure." Their products are engineered to be re-leveled, restored, and inherited.

Your task: completely redesign `portal/index.html` and `portal/style.css`. The current build looks like default AI output. The CONTENT is final and frozen — every word, heading, spec, and module stays exactly as written. Only the markup structure, layout, and visual design change.

## THE PROBLEM — current AI signatures to eliminate

The current build uses the default Claude layout vocabulary. Every one of these must be gone in the rebuild:

1. The centered hero with eyebrow text → lede paragraph → tagline stack
2. The 3-up `index-card` grid where every card is number + title + description in identical boxes
3. Pill-shaped chips (`chip ok` / `chip no`) for do/don't content
4. One uniform `border-radius: 10px` applied to everything
5. Identical soft box-shadows on every elevated element
6. The sticky topbar with `backdrop-filter: blur()`
7. Symmetric, centered section layouts where every module follows the same template
8. `clamp()`-driven fluid type that reads as "modern SaaS landing page"
9. Callout boxes that all look like alert components
10. Equal vertical rhythm between all sections — nothing breathes differently

## THE DIRECTION — heritage corporate identity manual, printed circa a company that's been around since 1999 and acts like it's been around since 1899

Design this as if it were a printed brand standards manual from a legacy furniture maker — the kind of document that lives in a leather binder in the showroom office — translated faithfully to the web. Think Massimo Vignelli's NYC Transit Authority manual, the 1976 NASA Graphics Standards Manual, or a Herman Miller identity book: numbered sections, hairline rules, ruthless grid discipline, and typography doing all the work.

### Layout system
- Build on a strict 12-column grid with visible discipline. Asymmetry is the rule: text columns offset, generous outer margins, content that hangs off a strong left axis rather than centering.
- Each module opens like a chapter spread: an oversized section number (set in the serif, very large, possibly cropped by the viewport edge or screened back in low-opacity emerald) with the module title set against it. NOT a centered heading over a subtitle.
- Replace the index-card grid with a manual-style table of contents: a ruled list — hairline rules between rows, module number in a narrow left column, title and description sharing a baseline, page-reference-style numerals on the right. Rows are full-width, not boxes.
- Do/Don't content becomes a two-column specification comparison divided by a single vertical hairline rule — column headers set in small caps with letterspacing. No pills, no chips, no colored badges.
- Callouts become margin notes or indented passages with a single thick left rule in brass — like an editor's annotation — not boxed alert components.
- Spec tables should look like they came from a parts catalog: hairline borders only (no zebra striping, no rounded corners), generous cell padding, column headers in letterspaced small caps.
- Vary the rhythm deliberately: some sections dense and tabular, some sparse with one statement holding a whole viewport. A printed manual is not uniform.

### Typography
- Serif (`Canela`, fallback `Tiempos Headline`, Georgia) leads everything: headings, the oversized chapter numerals, pull-stats, the tagline. Let it get genuinely large at display sizes — and use lining figures proudly.
- Inter is demoted to captions, table data, labels, and small caps annotations only. Body text may also be serif if it improves the manual feel — test it.
- Use real typographic devices: small caps with +0.08em tracking for labels, hanging indents, baseline-aligned columns, hairline rules above/below headings instead of margin gaps doing the separating.
- Fixed, confident type sizes per breakpoint. No `clamp()`.

### Color & surface
- Keep the existing token palette exactly: emerald `#14352A`, iron `#2B2B28`, espresso/chestnut/mahogany woods, slate `#B8BCC0`, brass `#B08D57`, bone `#F4F1EA`, surface `#FBFAF7`.
- Bone is the paper. Most of the page is bone with ink-on-paper typography. Emerald appears as full-bleed chapter divider bands (with bone type reversed out) and as the screened-back oversized numerals — not as button fills and chip backgrounds.
- Brass is precious: hairline rules, the thick callout rule, small caps labels, fine details. Never large fills.
- Shadows: none, or nearly none. A printed page has no drop shadows. Elevation comes from rules and spacing.
- Border radius: 0 everywhere. Square corners. This is a manual, not an app.

### Navigation & chrome
- Replace the sticky blurred topbar with a slim, flat masthead: solid emerald or solid bone with a single bottom hairline rule, logo left, module numbers as plain text links. No blur, no transparency.
- Consider a fixed left rail (desktop only) with module numerals 01–09 as a vertical index — like thumb tabs on a reference binder. Collapse gracefully on mobile.
- Footer styled as a colophon: small caps, single rule above, document version and date — like the last page of a printed manual.

## WHAT MUST SURVIVE THE REBUILD
- Every word of copy, verbatim. All nine modules, the vault, every spec value, every prompt block.
- All anchor IDs (`#m1`–`#m9`, `#vault`, `#main`) so existing links keep working.
- The copy-to-clipboard buttons on prompt blocks (restyle them as understated bordered text buttons — "COPY" in letterspaced small caps).
- Accessibility: skip link, focus-visible styles, semantic landmarks, WCAG AAA contrast (the bible itself mandates AAA — verify every text/background pair).
- No external frameworks, no JS libraries. Raw HTML/CSS as before.

## PROCESS
1. Read `spec/BRAND_BIBLE.md` and `GUARDRAILS.md` fully before touching anything — the manual must visually embody its own rules.
2. Read all of `portal/index.html` and inventory every piece of content so nothing is dropped.
3. Rebuild `style.css` from scratch around the system above. Rebuild `index.html` markup to serve the new layout.
4. Self-review against the 10-item AI-signature list at the top. If any item survives, fix it before finishing.
5. Final check: open the file mentally at 1440px, 1024px, and 375px. The mobile layout should feel like the same manual, single-column, not a collapsed dashboard.

The test for done: someone flipping through this should think "a brand team spent weeks on this with a print designer," never "Claude made this in one pass." When in doubt, ask: would this element exist in a 1976 graphics standards manual? If no, it doesn't belong.
