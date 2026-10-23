# FunnelCake Case Studies v2 — Handoff Notes for Harshita

7 pages: `index.html` + 6 case studies, plus `assets/` (all screenshots, already in place). Fully self-contained — Poppins from Google Fonts, everything else local. Open `index.html` to preview; all pages cross-link.

**Keep the `assets/` folder next to the HTML files** — the screenshots are local files now, not placeholders.

## Already matched to funnelcake.in
Palette and type are pulled from the real brand: paper `#F7F3EE`, sand `#F1E9DC`, ink `#0D1B2A`, coral `#FF5B5B`, green `#1E8E62`, Poppins throughout. The `:root` block at the top of each page's `<style>` re-skins everything if the brand ever shifts.

## What YOU still need to wire (5 things)
1. **CTA links** — every `Book a call` / `Let's talk` button is `href="#"`. Point them at the booking page or WhatsApp link.
2. **"funnelcake.in" link** in the index topbar → the homepage. "Work with us" links likewise.
3. **Draft quotes — do not publish as-is.** White Lotus, Sri Radhika and Ayurveda Compass have drafted quotes marked with a visible coral chip: `DRAFT — AWAITING CLIENT SIGN-OFF`. Get a one-line WhatsApp OK (or a real replacement quote) from each client, then delete the `<span class="draftchip">…</span>` element. If a client declines, delete that whole `<section>`.
4. **Client approvals** — one-line OK from each named client before publishing (standard practice). The confidential realty page must NEVER gain a name, URL, or unblurred image.
5. **Canonical/OG tags** — add canonical URLs + og:image per page when you know the final paths.

## Screenshots — provenance + refresh plan
- Live sites (Metamorphix, Ayurveda Compass, Tao of Touch, confidential realty) captured 16 Jul 2026 at 1280px desktop / 390px mobile.
- White Lotus "AFTER" + section shots are from the v10 build (not yet live); "BEFORE" is the current live site. **When the new WL site ships (Sept 2026 with the reformer studio), recapture and swap.**
- Sri Radhika + White Lotus v10 shots come from Anoushka's own full-res captures (browser chrome cropped). Swap for live-site captures once deployed.
- White Lotus booking system + Studio Manager shots are from the in-build prototype. Keep the IN BUILD badge until it ships (ClassPass integration pending).
- Realty shots have the logo/name pixelated at source. If you recapture, re-blur before committing — no staging URL in any src.

## Analytics provenance
White Lotus numbers are real, from Anoushka’s dashboards: Google Ads 1 Sept–31 Dec 2024 (794k impressions, 19.9k clicks, 2.50% CTR, AED 0.10 avg CPC) and GBP interactions Feb–Jul 2026 (1,504). Refresh when campaigns resume.

## When real analytics exist for the others (~3 months)
"By the numbers" grids use verifiable scope facts on purpose — the sites are too young for honest traffic claims. When GA4/GSC matures, swap facts for outcomes (enquiries/month, rankings, dosha-test signups, founding-list signups). Keep the same card markup.

## Adding Raahat later (CS/07)
Copy any case study file, update: title/meta, hero, metarail, system strip (`on` / `on k` classes), cards, screenshots in `assets/`, facts, prev/next links on the two neighbouring pages, and add a card on the index. The scroll-reveal script needs no changes.
