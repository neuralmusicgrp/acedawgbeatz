# Acedawgbeatz — Neural Music Group Website

**Producer:** Anthony "Acedawg" Boyd  
**Brand:** Acedawgbeatz / Neural Music Group  
**Stack:** Pure HTML + CSS + Vanilla JS — no frameworks, no build tools, drop-in ready

---

## Site Map

| File | Page | Purpose |
|---|---|---|
| `index.html` | Catalog | Main storefront — all beat packs, email capture, quick links |
| `landing.html` | Promo Gate | Email capture / free beats funnel — conversion-optimised, minimal nav |
| `vault.html` | Beat Vault | Exclusive drops, early access, subscriber-only content |
| `packs.html` | Beat Packs | Full product menu — artist packs and producer loops |
| `openverse.html` | Open Verse | Hook-ready beats for TikTok, reels, artist collabs |
| `sync.html` | Sync & Cinematic | Film, TV, brand, and creator sync cue library |
| `bio.html` | Artist Bio | Anthony Boyd's story, timeline, awards, and legacy |
| `contact.html` | Contact | Custom production, sync briefs, collab, and business requests |
| `thanks.html` | Vault Unlocked | Post-email-capture confirmation — standalone, no nav |

---

## Design System

**Fonts** (Google Fonts — loaded in every `<head>`)
- `Orbitron` — headings, brand mark, all-caps labels (weight 400–900)
- `Rajdhani` — body copy, paragraphs, cards (weight 400–700)
- `Share Tech Mono` — nav links, eyebrows, section IDs, monospace labels

**Color Tokens** (CSS custom properties)
```css
--bg:           #03040A   /* near-black base */
--cyan:         #00E5C8   /* primary accent */
--cyan-dim:     rgba(0,229,200,0.10)
--magenta:      #FF0077   /* tension accent */
--gold:         #F0C040   /* premium / vault */
--text:         #D8E8F0
--text-soft:    #87A6BB
--text-dim:     #3A5060
--border:       rgba(0,229,200,0.14)
--border-strong:rgba(0,229,200,0.30)
```

**Shared UI Patterns**
- Animated 60px grid background (drifts diagonally via `@keyframes grid`)
- Scanline overlay — fixed, `z-index: 1`, pointer-events none
- Scroll progress bar — cyan → magenta → gold gradient across top of viewport
- All buttons — `clip-path` cut corners, shimmer sweep on hover
- Corner bracket decorations on cards — expand on hover
- Section ID labels — `SYS::XX // SECTION NAME` in Share Tech Mono
- Eyebrow labels — cut-corner badge with `//` prefix

---

## Navigation

Every page (except `landing.html` and `thanks.html`) uses the same nav:

```
Catalog | Vault 🔓 | Packs | Open Verse | Sync | Bio | Contact
```

- Active page link gets `class="active"` (cyan underline)
- Contact always renders as `.nav-cta` (boxed CTA button style)
- Hamburger menu activates below **980px** — desktop nav hides at same breakpoint
- `landing.html` uses a slim conversion nav (no Bio or Contact)
- `thanks.html` has no nav — standalone post-conversion page

---

## JavaScript

All JS is inline at the bottom of each file — no external dependencies.

| Feature | How it works |
|---|---|
| Sticky nav | `scroll` listener toggles `.scrolled` class on `#stickyNav` at `scrollY > 20` |
| Scroll progress bar | `scrollY / scrollHeight` → `width %` on `#scroll-progress` |
| Scroll reveal | `IntersectionObserver` adds `.visible` to `.reveal` elements at `threshold: 0.08` |
| Hamburger | Toggles `.open` on `#mobileMenu` and `#hamburger`, closes on link click |
| Scroll-to-top | `#scroll-top` button appears at `scrollY > 400` |
| Reduced motion | `@media (prefers-reduced-motion: reduce)` disables all animations |

---

## Going Live

**Connect the contact form**  
`contact.html` form currently runs `fakeSubmit()` for demo. Connect to a real backend before launch:
- [Formspree](https://formspree.io) — paste your endpoint into the `action` attribute
- [MailerLite](https://mailerlite.com) — replace form with their embed code
- [Kit (ConvertKit)](https://kit.com) — use their hosted form URL

**Connect the email capture forms**  
`landing.html`, `vault.html`, and `index.html` all have email capture fields. Wire to MailerLite or Kit.

**Update BeatStars links**  
All `href="#"` placeholders on pack cards need real BeatStars product URLs.

**Update the thanks page redirect**  
`thanks.html` — the Shop BeatStars button (`href="#"`) needs your BeatStars storefront URL.

---

## File Naming Rules (Catalog System)

All music assets follow the NMG catalog ID format:

```
NMG-CAT-[####]-[TYPE][##]

Examples:
NMG-CAT-0001-A01    → main instrumental
NMG-CAT-0001-OV01   → open verse version
NMG-CAT-0001-SYNC01 → sync alt / no-drums
NMG-CAT-0001-LP01   → loop asset
NMG-CAT-0001-CL01   → 15-second clip
```

No unnamed files. No "Final Final." No "Mix2."

---

## Release Gates

Before any beat goes live:
- [ ] Catalog ID assigned
- [ ] Metadata complete (BPM, key, genre, mood)
- [ ] Split sheet confirmed
- [ ] All exports present (tagged, untagged, open verse, no-drums, stems, clip)
- [ ] BeatStars listing copy written
- [ ] Cover art exported

**No split sheet = no release.  
No catalog ID = no release.**

---

## Three Business Lanes

| Lane | Purpose | Primary Channel |
|---|---|---|
| **Lane 1 — Streaming Catalog** | Long-term IP ownership | DistroKid / distribution |
| **Lane 2 — BeatStars Engine** | Daily cashflow | BeatStars storefront |
| **Lane 3 — Sync Vault** | Licensing inventory | `sync.html` + direct pitching |

---

*Built for Acedawgbeatz — Neural Music Group — © 2026*
