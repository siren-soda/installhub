# Installer Tools Suite — Brand Guide

> **Decisions, 17 Nov 2026 (Dean):** TechMate lives at techmate.installhub.org under the InstallHub suite. SafeInstall gets the shared "Part of InstallHub" footer (same as TechMate's) and a TechMate card in its Resources tab. TechMate keeps footer + About disclaimers with no terms gate. Moving both sites onto `suite.css` is parked until a redesign. Section 9 below is kept for history.

Covers SafeInstall (safeinstall.org) and TechMate (installer manuals + tech help). Source of truth: the live SafeInstall site as of 14 Nov 2026. TechMate items marked [verify] come from planning notes, not the live site — check them against the repo siren-soda/techmate.

## 1. Logo family

One family: a navy shield with a single orange glyph. The glyph tells you which tool it is.

| Tool | Glyph | Status |
|---|---|---|
| SafeInstall | Tick (check mark) | Live |
| TechMate | Magnifying glass | Agreed [verify the SVG] |

### Shield geometry (120×120 viewBox)

```svg
<!-- Base shield -->
<path d="M60 8 L102 23 V57 C102 84 84 103 60 112 C36 103 18 84 18 57 V23 Z" fill="#1f3a5f"/>
<!-- Right-half highlight (used in header logo only) -->
<path d="M60 8 L102 23 V57 C102 84 84 103 60 112 Z" fill="#2b4d7a"/>
<!-- SafeInstall glyph -->
<polyline points="40,60 54,74 82,44" fill="none" stroke="#F59E42" stroke-width="12" stroke-linecap="round" stroke-linejoin="round"/>
```

### Variants in use

- **Header mark:** two-tone shield (with highlight), 34px, on a 44px white rounded tile (radius 11px), sitting on the navy header.
- **Favicon:** flat shield (no highlight), glyph stroke width 14 so it holds up at small sizes. Inline SVG data URI.
- **App icon:** /icons/apple-touch-icon.png plus manifest.webmanifest (PWA install prompt).

**Rules:** the glyph is always orange `#F59E42` with round caps and joins. Keep the glyph inside the shield. Use stroke 12 at header size and 14 for the favicon.

## 2. Wordmark

Two-tone, bold, tight tracking: SafeInstall with the second word in orange.

```html
<h1 style="margin:0;font-size:24px;letter-spacing:-.5px">Safe<span style="color:#F59E42">Install</span></h1>
```

TechMate follows the same pattern: TechMate, with "Mate" in orange. [verify]

Under the wordmark there's a small uppercase tagline: 12px (10.5px on phones), 0.08em tracking, 75% opacity. SafeInstall tagline: "Free pre-start & SWMS / for security installers".

## 3. Colour

| Token | Hex | Use |
|---|---|---|
| `--brand` | `#1f3a5f` | Navy. Header, primary buttons, headings, focus ring, theme-color |
| `--brand-2` | `#2b4d7a` | Shield highlight |
| `--brand-soft` | `#e8eef6` | Info notes |
| `--accent` | `#F59E42` | Orange. Logo glyph, wordmark, progress bars, install banner edge |
| `--bg` | `#f3f4f1` | Page background (warm off-white) |
| `--card` | `#ffffff` | Section cards |
| `--ink` | `#1b2220` | Body text |
| `--muted` | `#5b6561` | Secondary text, labels |
| `--line` | `#dce0db` | Borders and dividers |
| `--warn` | `#9a3412` | Hazard alerts, "Yes = hazard present" answers |
| `--warn-soft` | `#fdeee4` | Alert background |
| `--yes` | `#15803d` | Safe/OK state, ticks, success |
| `--no` | `#b91c1c` | Errors |

Note: the accent orange `#F59E42` is hard-coded in several places on SafeInstall and isn't a variable yet. The shared stylesheet fixes that.

## 4. Type

- **Font:** system stack only, with no web fonts (fast, free, no external requests): `system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`
- **Body:** 16px / 1.45
- **Section heading (h2):** 14px, uppercase, 0.06em tracking, navy, with an optional numbered navy pill (22px)
- **Labels:** 13px muted. **Small print:** 12.5px muted
- **Buttons:** weight 600, 15px (13px small)

## 5. Layout and UI conventions

- **Mobile-first, single column:** max width 640px, centred, 12px side padding.
- **Header:** full-width navy band holding the logo tile, wordmark plus tagline, a pill button on the right (outlined white, e.g. "How it works"), then tab nav underneath (white text at 70% opacity; active tab at 100% with a 3px white underline).
- **Cards:** white, 1px `--line` border, radius 12px, 14px padding, 12px gap.
- **Inputs:** 11/12px padding, radius 9px, `#fbfcfb` fill, 2px navy focus outline.
- **Buttons:** radius 10px. Primary is navy fill. Secondary is `#e7eae6` with ink text.
- **Sticky bottom action bar:** white at 97%, top border, respects the safe-area inset.
- **Bottom sheets for modals:** top radius 16px, max height 88vh.
- **Alerts:** soft fill, 4px left border in the status colour, radius 8px.
- **Install banner:** white card with a 4px orange left border.
- **Yes/No segmented controls:** in hazard questions, Yes goes orange-red (`--warn`) and No goes green (`--yes`).
- **Resource lists:** stacked links, navy bold title, muted one-line description underneath.

## 6. Footer pattern

SafeInstall currently has no `<footer>` element. Its small print sits in `.foot` lines inside each view. Proposed shared footer for both sites:

> [shield mark] SafeInstall · TechMate — free tools for security installers
> Guide only — you're responsible for your own safety and compliance. Terms · Privacy

## 7. Cross-linking

**Current state:** SafeInstall doesn't link to TechMate anywhere.

**Proposed:**

- Add a "More free tools" row to the shared footer on both sites.
- Add a TechMate card to SafeInstall's Resources tab ("Manuals & tech help → TechMate").
- Add a SafeInstall card on TechMate ("Need a pre-start? → SafeInstall").

## 8. Disclaimer wording

**Short form, for footers and small print:**

> Free guidance tool only. You are responsible for the safety and legal compliance of your own work.

**SafeInstall full terms** (live, shown on first use and accepted by checkbox). The headings are: Not a substitute for your own due diligence · You are responsible · No guarantee · Laws differ by state (Victorian guidance first) · Third-party links · Privacy (nothing collected; data stays on the device; Resend keeps short-term sending records; host visit logs) · No liability ("as is", to the extent permitted by law).

**TechMate needs its own additions** [verify what's live]:

- Manuals belong to their manufacturers. Always check the current official version.
- AI chatbot answers may be wrong. Answers that come from web search rather than the site's manual library are labelled as such.
- 240V and mains work: licensed electrician only.

**Voice:** plain Aussie trade English, second person, short sentences ("Keep it.", "Make one in 2 minutes"). Victorian sources first, with a nudge to check your own state's regulator.

## 9. Where the two sites differ (pick one)

| Item | SafeInstall (live) | TechMate | Decide |
|---|---|---|---|
| Domain | safeinstall.org | Free Netlify address | Own domain, or a subpath of safeinstall.org? |
| Glyph | Tick | Magnifying glass | — (intended to differ) |
| Accent as a variable | Hard-coded | [verify] | Use `--accent` everywhere |
| Footer | None (inline small print) | [verify] | Shared footer (section 6) |
| Cross-links | None | [verify] | Section 7 |
| Disclaimer | Full terms gate on first use | [verify] | Same gate, or footer-only for a reference site? |
| Email domain | Resend via safeinstall.org | Not applicable yet | — |
