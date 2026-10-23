# FunnelCake Case Studies — Handoff Notes

7 files: `index.html` (the case studies landing page) + 6 individual case study pages. All self-contained — fonts from Google Fonts, zero other dependencies. Open any file in a browser to preview as-is.

## Restyling to match funnelcake.in
Palette is currently APPROXIMATED (light #F8F9FC body, deep navy #0E1B33 ink/dark blocks, warm #E8563F accent) from the live site structure — the exact hexes live in funnelcake-v2.html. Swap the 7 `:root` variables against that file and it matches 1:1.
Every page has the same `:root` variable block at the top of its `<style>`. Swap these 7 variables and the whole system re-skins:

```css
--paper  (page background)      --ink    (text / dark blocks)
--berry  (primary accent)       --syrup  (secondary accent)
--smoke  (muted text)           --line   (borders)   --chip (tag bg)
```

Fonts: Bricolage Grotesque (display) / Instrument Sans (body) / Space Grotesk (mono labels). Replace in the Google Fonts `<link>` + the three `--disp/--body/--mono` variables if v2 uses different faces.

## Screenshot slots
Every dashed box is a labeled slot. Replace the `<div class="shot ...">` with an `<img>` (keep the same class OR just match the aspect ratio: `r169` = 16:9, `r43` = 4:3, `tall` = 9:16 mobile).

### Shot list (capture at 1440px desktop / 390px mobile, PNG or WebP)
- **White Lotus** (from whitelotus-v10.html, open locally): hero, services, FAQ, mobile — PLUS: Google Business Profile listing view, Instagram grid, a Google Ads screenshot if shareable (blur spend figures)
- **Sri Radhika** (from the standalone HTML, open locally): hero, collections, gold-rate ticker close-up, mobile
- **Metamorphix** (metamorphix.in): hero, three-paths section, impact numbers, mobile CTA
- **Ayurveda Compass** (ayurvedacompass.de): hero with EN/DE toggle visible, pillars, retreats, mobile dosha capture
- **Tao of Touch** (taooftouch.earth): ⚠️ ONLY after cleanup — see blockers
- **Confidential realty** (staging): hero, live listings grid, valuation funnel, mobile listing card — ⚠️ CROP/BLUR the logo, agent name and face in EVERY shot. No staging URL anywhere.

## ⚠️ Publish blockers
1. **Tao of Touch — HOLD.** The live site still contains theme demo content: lorem ipsum sections, fake coaches (Joe Thomas/Genny/Tonina), footer address "No: 58 A, East Madison Street" + info@example.com, and demo blog posts. If we link a case study to it in this state, it hurts us. Either get Mav to approve the cleanup punch-list (already flagged to him) or launch with 5 case studies and add ToT later. The card is marked "ON HOLD" on the index — remove the `hold` class when clear.
2. **Client approvals.** Get a one-line WhatsApp OK from each named client before publishing (standard practice, protects us). Ayurveda Compass quote is from her own public testimonials page — still confirm with Ulrike.
3. **Quote slots.** Pages without quotes have a dashed "CLIENT QUOTE SLOT". Fill or delete the section — never invent a quote.
4. **CTA links.** All "Let's talk" / "Book a call" buttons point to `#contact` / `#` — wire to the real contact page or WhatsApp link.
5. **Raahat** intentionally excluded (build in progress). It becomes CS/07 when the booking-flow decision lands.

## When real analytics exist
The "By the numbers" grids currently use verifiable scope facts (deliberately — the sites are too new for traffic claims). When GA4/GSC data matures (~3 months), swap facts for outcomes: enquiries/month, ranking positions, dosha-test signups, etc.
