# MODULE 10 — PHOTOGRAPHY & IMAGE GOVERNANCE
### C.L. Bailey & Co. — Image Standard, Current-State Assessment & Production Guideline
**Companion to BRAND_BIBLE.md §2.6 (Imagery Direction), §2.7 (Naming), §8.3 (AI Image Parameters)**
*Assessed against clbailey.com/en and the ImageKit library (`ik.imagekit.io/billiardfactory/CLB_Site_Rebuild/`) — June 2026*

---

# PART A — CURRENT-STATE ASSESSMENT

## A.1 What the library is today

The live image library is a blend of three incompatible photographic generations:

1. **Legacy catalog photography.** Bright, flat, daylight-flooded rooms; burgundy felt; striped rugs; staged family models (e.g., the Viking collection hero with four kids around a burgundy-felt table). Reads as 2010s furniture catalog. Violates §2.6 color grade (cool, over-lit, no protected shadows).
2. **AI-generated lifestyle imagery (Nano Banana).** The dominant new layer: green-library Skylar rooms, brick-loft Viking scenes, desert-modern dinner parties, golden-hour sunset shots. Often beautiful in isolation — but inconsistent with each other and with the legacy layer.
3. **Stock-flavored one-offs.** The bright-blue-felt overhead loft shot in the Interior Designers section; the LED-lit black-felt penthouse shot in the Skylar gallery. Neither belongs to any collection world.

## A.2 Findings, by severity

### CRITICAL

**F-1. The AI prompts are publicly visible in the URLs.**
Production filenames contain raw generation-prompt text and the generator name, e.g.:
- `Make_the_pucks_real_shuffleboa_Nano_Banana_2_98233_z1_eR2pIw.jpg`
- `Wide_cinematic_editorial_shot__Nano_Banana_2_93885_IxnPxUL5F.png`
- `the_two_spectator_chairs_on_th_Nano_Banana_2_48625_9qA_A-ONt.jpg`
- `SHOT_4_The_Dining_Conversion_B_Nano_Banana_2_97057 (1)_geLmMBOqx.jpg`

Anyone who right-clicks an image — a dealer, a competitor, a journalist — can see the brand's lifestyle photography is AI-generated, *with the prompt attached*. For a brand whose entire promise is "built by hand," this is a reputational exposure, not a housekeeping issue. It also violates §2.7 (naming framework) outright.

**F-2. The site violates the bible's own AI policy (§8.3).**
§8.3 states AI imagery is for *concepting and mood only* and "MUST NOT be passed off as photographs of actual product in dealer-facing or paid assets." The homepage hero rotation, collection pages, and product galleries are dealer-facing surfaces running AI imagery as primary product representation. Either the policy changes (see Part B §10.6 for the governed version) or the imagery does. The current state — policy says one thing, flagship surface does another — is the worst of both.

**F-3. Felt color chaos.**
Across the assessed pages the playing surface appears in burgundy, bright blue, purple, black, graphite, tan/cream, and green. The mark itself letters the brand in Heritage Green (`#006840`) — the brand owns one green. The single most recognizable square footage in any photograph — the felt — is currently the least controlled brand surface.

### HIGH

**F-4. Geography and architecture don't match the brand story.**
The Viking — "Tomball, Texas… matched by hand since 1999" — is photographed against a Manhattan skyline in a brick loft. The Tunbridge sits in a NYC-skyline loft. Other scenes are Sonoran desert modern (saguaros through the window). The brand is Texan heritage; the imagery is anywhere-and-nowhere. No image assessed places the product in a recognizably Southern/Texan residential world.

**F-5. One collection, many worlds.**
The same collection jumps art direction shot-to-shot: Viking is beach-house bright in one frame, industrial-loft moody in the next, desert-contemporary in a third. §2.6's intent (a coherent "lived-in home") is impossible when each image invents a new house. Collections read as *matched families* in copy and *orphans* in pictures.

**F-6. AI artifacts visible at production size.**
Spot checks show classic tells: incoherent abstract wall art, prop debris under tables, slightly waxy faces in group scenes, architecture that doesn't resolve. Each one quietly erodes the "honest joinery" promise. There is no evidence of a human QC gate (§8.3's "brand truth check") between generation and publish.

### MEDIUM

**F-7. The workshop is missing.**
"Built by hand. Guaranteed for life." is illustrated by an anonymous hands-on-wood shot. There is no visible library of the actual Tomball shop floor: saws, finish room, slate leveling, the people. The single most defensible photographic asset this brand could own — real provenance — is absent. (§2.7.2 reserves `03_Photography/` for it; the social grid in §4 requires craft/material macros.)

**F-8. Image delivery hygiene.**
Multiple slots render as blank beige for seconds (lazy-load with no LQIP placeholder); transforms request `w-3840` at `q-70` even for card-size slots; at least one URL ships with no format extension and a stray `?updatedAt` cache-buster; one filename contains ` (1)` — a desktop duplicate artifact now in production. Mixed naming (`PTB_HERO_r6IPkaQze.png` vs `skylar combo_ySLqSRsgG.jpg` — spaces in URLs) confirms there is no enforced ingest gate on the ImageKit library.

**F-9. Convertible-top proof is under-shot.**
§2.6 requires every collection to show the dining top *deployed*. Coverage is inconsistent — the strongest version is an AI dinner-party scene rather than a real conversion sequence (the one thing a photograph can prove and a render can only claim).

## A.3 What's working

To be kept and built on: the **green-walled Skylar library scenes** are the closest thing to a correct brand world — warm, lamp-lit, green-felted, furniture-not-equipment. The **moody craft/hands imagery** direction is right even if the current execution is generic. The site's typography-led design carries heritage; the photography just needs to live in the same house.

---

# PART B — THE PHOTOGRAPHY STANDARD

*This is the governing standard for every image on every C.L. Bailey surface: web, social, paid, dealer portal, print. If an image cannot be traced to a shot type in §10.2 and pass the gate in §10.8, it does not ship.*

## 10.1 The One-Sentence Standard

**Every C.L. Bailey photograph is a warm, lamp-lit room in one believable Texas home, where solid hardwood furniture is being lived with — and the felt is Heritage Green.**

## 10.2 The Shot Taxonomy

Six shot types. Every asset in the library is exactly one of these.

| # | Type | Code | Purpose | Notes |
|---|------|------|---------|-------|
| 1 | **Residential Hero** | `Hero` | Collection/product anchor. The room at its best hour. | One room per collection (§10.4). 16:9 web / 4:5 feed. |
| 2 | **Family-in-Use** | `Lifestyle` | People using the furniture: game night, dinner on the top, quiet morning. | Hands and posture natural; nobody posing at camera. |
| 3 | **Craft Macro** | `Macro` | Grain, joinery, slate edge, finish coat, brass nameplate. | Shallow DOF. Wood grain MUST be legible (§2.6). |
| 4 | **Conversion Demo** | `Demo` | The dining top deployed — sequence or pair (felt → dinner). | Required once per collection. Photograph, never render. |
| 5 | **Workshop / Provenance** | `Shop` | The Tomball floor: saws, finish room, leveling, the makers. | Real only. AI is banned for this type without exception. |
| 6 | **Product Study** | `Study` | Clean three-quarter and detail views on a quiet, warm ground. | Never white-seamless (§2.6 "never"). Warm White or wood-toned environment. |

Social grid rhythm (§4.1) maps to types 1/3/2. Paid asset groups (§6) require types 1, 3, and 4.

## 10.3 Light, Color, Felt

- **Light:** Warm ambient — golden-hour window light, lamps, hearth. Practical sources visible in frame where natural. Never cold strobe, never midday flat-bright, never LED-strip "games room" lighting.
- **Grade:** Warm white balance, 4800–5200K feel. Protected shadows — moody is correct, crushed is not. No pure `#000` blacks (honor Deep Charcoal `#1C1C1E`). Felt green and wood tones true-to-finish; no saturation pushes.
- **Felt:** **Heritage Green (`#006840`) — the green of the mark's lettering — is the default playing surface in all brand photography.** A second approved felt may appear only when the image's explicit subject is the felt program (Module: Felt/Velocity Pro) — never as set dressing. Burgundy, blue, purple, black, and tan felts are retired from brand imagery. This single rule does more for shelf-recognition than any logo placement.
- **Palette discipline:** Rooms are dressed inside the brand system — warm whites, sand, charcoal iron, the wood finishes, and bronze accents. The green felt is the room's single saturated note; a prop color outside the system must be incidental, never dominant.

## 10.4 One Collection, One House

Each collection lives in **one architectural world**, documented as a one-page "room bible" (location, light, wall color, flooring, props) before any shoot or generation:

- **Skylar** — *the modern green library.* Clean-lined contemporary home; deep-green millwork; brass and linen; morning-to-lamplight range. (The existing green-walled Skylar scenes are the seed — keep them.)
- **Viking** — *the Texas hill-country lodge.* Stone, timber, forged iron; big hearth; dusk and firelight. Replaces both the beach-house catalog world and the Manhattan loft world.
- **Tunbridge** — *the transitional family home.* Warm whites, weathered brown, generational mix; Sunday-afternoon light.
- **Dutchess** — *world to be defined.* No room bible exists yet; one MUST be written and approved before the next Dutchess shoot or generation ships.

Rules: no skylines that aren't Texan, no desert-modern unless a collection world is explicitly defined there, no white-box lofts. A new world requires the same written approval as a new brand color (§2.2).

## 10.5 People

Multi-generational, natural, mid-action — reaching for a cue, laying a place setting, leaning on a rail. Faces may be soft or turned; the furniture is the protagonist. Casting reflects real American homes. Nobody wears brand-clashing saturated colors. No stock-photo grins at camera.

## 10.6 AI-Generated Imagery — The Governed Policy

This section **amends §8.3** to match operational reality: C.L. Bailey uses generative imagery (Nano Banana / Gemini, or successors) in production. Denying it is untenable; governing it is mandatory.

**Tiering:**

| Tier | Surfaces | AI permitted? |
|------|----------|---------------|
| 1 | Product Studies, Craft Macros, Conversion Demos, Workshop/Provenance, co-op & paid ads making product claims | **No.** Real photography only. These are *proof* surfaces. |
| 2 | Residential Heroes, Family-in-Use lifestyle on web & social | **Yes, conditionally** — the depicted furniture must be dimensionally and materially true to the real product (built from real product photography as input, not imagined), and the image must pass the §10.8 gate. |
| 3 | Internal concepting, mood boards, room-bible exploration | Yes, freely. |

**Non-negotiables for Tier 2:**
1. **Truth of product.** Proportions, finish, hardware, pocket and leg count exactly match the shipping product. Anatomically wrong product = non-shippable (§8.3).
2. **Truth of world.** The image obeys §10.3 and §10.4 like any photograph.
3. **Human QC sign-off.** Named reviewer, recorded in the asset's metadata, before upload.
4. **Clean filenames.** Prompt text and generator names NEVER appear in any public URL, filename, alt text, or EXIF. Renamed per §10.7 *before* upload to ImageKit.
5. **No fake provenance.** AI never depicts the workshop, the makers, or "our factory." The craft story is the one place a synthetic image would be a lie rather than an illustration.

## 10.7 File Naming & ImageKit Hygiene

Extends §2.7 to the photography library. Pattern:

```
CLB-[Collection|Module]-[ShotType]-[Subject]-[Source]-vNN.[ext]
```

- **Collection:** `Skylar`, `Viking`, `Tunbridge`, `Dutchess`, `Brand` (non-collection)
- **ShotType:** `Hero`, `Lifestyle`, `Macro`, `Demo`, `Shop`, `Study`
- **Source:** `Ph` (photograph) or `Gen` (generated) — internal honesty marker, innocuous in public
- Examples: `CLB-Skylar-Hero-Library-Gen-v02.jpg` · `CLB-Viking-Demo-DiningTop-Ph-v01.jpg`

**ImageKit rules:**
- No spaces, no parentheses, no ` (1)` duplicates, no prompt text, no missing extensions.
- Folder mirror: `/CLB_Library/[Collection]/[ShotType]/`.
- Transform discipline: request the rendered size (`w-800` for cards, `w-1920`–`w-2560` for heroes — not `w-3840` everywhere); `f-auto`; `q-75` heroes / `q-80` macros (grain must survive).
- Every image slot ships a low-quality placeholder (ImageKit `q-10,bl-6` LQIP) — no more blank beige boxes.
- Monthly audit (same cadence as §2.7): non-conforming files are renamed or purged.

## 10.8 The Publish Gate

No image ships to any public or dealer surface until every box is checked:

- [ ] Maps to exactly one §10.2 shot type
- [ ] Felt is Heritage Green (or image is an approved felt-program asset)
- [ ] Light and grade meet §10.3 (warm, protected shadows, true tones)
- [ ] Setting belongs to the collection's documented world (§10.4)
- [ ] Wood grain legible; product proportions true; pockets/legs/rails anatomically correct
- [ ] If generated: Tier permitted, product-true, named human sign-off, `Gen` source tag
- [ ] Filename conforms to §10.7; no prompt text anywhere in URL, alt, or metadata
- [ ] Alt text per §7 (descriptive, collection-led; decorative gets `alt=""`)
- [ ] Correct transform size for the slot; LQIP present

## 10.9 Remediation Priorities

1. **This week — kill F-1.** Rename every `Nano_Banana` / prompt-text file in ImageKit and update site references. This is exposure, not polish.
2. **Next 30 days.** Retire off-felt and off-world imagery from primary surfaces (homepage rotation, collection heroes); standardize on the green-felt assets that already exist; write the three room bibles (§10.4); fix transforms + LQIP.
3. **Next quarter.** Commission the one shoot that AI cannot do: **two days in the Tomball workshop** (type 5) plus one real Conversion Demo sequence per collection (type 4). These become the proof layer under the generated lifestyle layer — and the only image set no competitor can copy.

---

*Document version 1.0 — June 2026. Governed by the same change-control as BRAND_BIBLE.md. Photography questions resolve to this module; if this module is silent, §2.6 governs.*
