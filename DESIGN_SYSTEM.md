# Myers & Co — Design System
> Extracted from myersandcompany.co (Wix) on 2026-05-23  
> Intended for use by Claude Code to rebuild the site from scratch

---

## 1. Brand Identity

**Name:** Myers & Co Growth Consultancy  
**Tagline:** Growth Marketing Consultancy for Financial Services  
**Voice:** Bold, lowercase, conversational, irreverent ("co-conspirator", "cold brew", "rewrite the rules")  
**Tone:** Confident, peer-level, fintech-savvy. All body copy and headings use **lowercase** — this is a deliberate stylistic choice, not an error.

---

## 2. Color Palette

Colors confirmed against the actual logo source files (provided 2026-05-23).

| Token | Hex | RGB | Usage |
|---|---|---|---|
| `--color-sky-blue` | `#BDE0F5` | rgb(189, 224, 245) | Primary page background (all interior pages; right panel of homepage) |
| `--color-white` | `#FFFFFF` | rgb(255, 255, 255) | Homepage left panel background; form input fields |
| `--color-coral` | `#E8635A` | rgb(232, 99, 90) | **Confirmed from logo.** Logo rule, square period glyph, section titles, body text on blue, card backgrounds, page borders |
| `--color-logo-blue` | `#55AADF` | rgb(85, 170, 223) | **Confirmed from logo.** MYERS & CO. text; "Growth Consultancy" subtitle |
| `--color-charcoal` | `#363432` | rgb(54, 52, 50) | Large page headings ("what we do", "our philosophy", "work with us", "our c.v.") |
| `--color-coral-muted` | `#ED8880` | rgb(237, 136, 128) | Secondary text, lighter coral for body copy |
| `--color-nav-gray` | `#6B6B6B` | rgb(107, 107, 107) | Inactive navigation link text |
| `--color-nav-active` | `#E8635A` | rgb(232, 99, 90) | Active / current page nav link (same as coral) |

> ⚠️ **Source of truth for coral + logo blue:** Always eyedrop from the provided logo PNG files, not the Wix site. Wix rendering can shift these slightly.

### Color Usage Rules
- **Sky blue** is the canvas — almost every page uses it wall-to-wall
- **Coral** is the brand's energy — it lives in all text on blue, card fills, and accent lines
- **Charcoal** is reserved for the large hero page-title headings only
- **Logo blue** is used exclusively for the brand mark and its subtitle
- **White** appears only on the homepage left split panel and form inputs

---

## 3. Typography

### Font Family
**Primary:** `Poppins` (Google Font)  
**Weights used:** 300 (Light), 400 (Regular), 600 (SemiBold), 700 (Bold), 800 (ExtraBold)  
**Style:** All headings and most body copy render in **lowercase**

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700;800&display=swap');

font-family: 'Poppins', sans-serif;
```

### Type Scale

| Role | Size | Weight | Color | Transform | Notes |
|---|---|---|---|---|---|
| `logo-display` | 96–120px | 800 ExtraBold | `--color-logo-blue` | uppercase | "MYERS" / "& CO." stacked, wide tracking |
| `logo-subtitle` | 22px | 400 Regular | `--color-logo-blue` | none | "Growth Consultancy" — wider letter-spacing |
| `page-heading` | 72–96px | 800 ExtraBold | `--color-charcoal` | lowercase | "what we do", "our philosophy", "our c.v." |
| `section-title` | 22–26px | 700 Bold | `--color-coral` | lowercase | Service/philosophy pillar names |
| `sub-heading` | 16–18px | 700 Bold | `--color-coral` | lowercase | Sub-section labels within cards |
| `body` | 16–18px | 300 Light | `--color-coral-muted` | none | Paragraph text on blue backgrounds |
| `body-dark` | 16–18px | 300 Light | `--color-charcoal` | none | Paragraph text on light/white backgrounds (contact page intro) |
| `nav` | 16px | 400 Regular | `--color-nav-gray` | lowercase | Inactive nav links |
| `nav-active` | 16px | 700 Bold | `--color-nav-active` | lowercase | Active page nav link |
| `contact-label` | 13px | 400 Regular | `--color-charcoal` | lowercase | Form field labels (first, last, email, message) |

### Letter Spacing
- Logo display (`MYERS & CO.`): `letter-spacing: 0.04em`
- Logo subtitle: `letter-spacing: 0.15em`
- Page headings: `letter-spacing: -0.01em` (tight, impactful)
- Navigation: `letter-spacing: 0.02em`
- Body: `letter-spacing: normal`

### Line Height
- Headings: `1.0–1.1`
- Body: `1.7–1.9`

---

## 4. Spacing & Layout

### Spacing Scale (8px base)
```
4px   — xs  (tight inline gaps)
8px   — sm
16px  — md
24px  — lg
40px  — xl
64px  — 2xl
96px  — 3xl  (section vertical padding)
128px — 4xl  (hero panel padding)
```

### Max Content Width
```
max-width: 1280px;
margin: 0 auto;
```

### Grid
- **Services / Philosophy cards:** 3-column grid with equal gutters (`gap: 48px`)
- **Contact info row:** 3-column flex row (phone, email, social)
- **Homepage:** 2-column split (see homepage layout below)

---

## 5. Page Layouts

### 5.1 Homepage (`/`)
**Unique split-screen layout — not shared by other pages.**

```
┌──────────────────┬────────────────────────────┐
│                  │  [NAV: right-aligned]       │
│   WHITE PANEL    │                             │
│   (47% width)    │   BLUE PANEL (53% width)    │
│                  │                             │
│  [LOGO MARK]     │   [HERO BODY COPY]          │
│  MYERS           │                             │
│  & CO.           │   [LINKEDIN ICON]           │
│  ————————        │                             │
│  Growth          │                             │
│  Consultancy     │                             │
│                  │                             │
└──────────────────┴────────────────────────────┘
```

- Left panel: `background: #FFFFFF`, centered vertically
- Right panel: `background: #BDE0F5`, padded top/left
- Logo is visually centered in the left panel both horizontally and vertically
- Nav is positioned top-right within the blue panel
- The coral underline rule under the logo is approximately `2px solid #D4665E`, full logo-text width

### 5.2 Interior Pages (Services, Philosophy, Work, Contact)
**Full-width sky blue background. Content is left-aligned inside a max-width container.**

```
┌──────────────────────────────────────────────┐
│  [NAV: right-aligned, padded top]            │
│                                              │
│  [PAGE HEADING — very large, charcoal]       │
│                                              │
│  [PAGE CONTENT]                              │
│                                              │
└──────────────────────────────────────────────┘
background: #BDE0F5
```

- Nav: `position: sticky; top: 0;` or simply padded at top right
- Page heading: `font-size: clamp(56px, 8vw, 96px)` — large, bold, charcoal, lowercase
- Content area: `max-width: 1280px; padding: 0 80px;`

### 5.3 Services Page (`/services`)
Three-column card layout below the page heading.

```
[what we do]   ← page heading, full width

[CIRCLE IMG]   [CIRCLE IMG]   [CIRCLE IMG]
[title]        [title]        [title]
[sub-head]     [sub-head]     [sub-head]
[body]         [body]         [body]
[sub-head]     ...            ...
[body]
```

- Circle images: `width: 140px; height: 140px; border-radius: 50%; object-fit: cover;`
- Card: no border/shadow, background transparent (inherits sky blue)
- Text alignment: centered within each column

### 5.4 Philosophy Page (`/philosophy`)
Identical layout to Services — 3-column with circular images.

```
[our philosophy]  ← page heading

[CIRCLE IMG]   [CIRCLE IMG]   [CIRCLE IMG]
[plant the     [cultivate     [blossom
 roots]         passion]       boldly]
[sub-head]     [sub-head]     [sub-head]
[body copy]    [body copy]    [body copy]
```

### 5.5 Work / C.V. Page (`/c-v`)
Coral frame / border around the page with sky blue inner content.

```
┌─ CORAL BORDER (left + right frame ~40px) ──┐
│ ┌──────────────────────────────────────┐   │
│ │  [our c.v.]  ← heading               │   │
│ │  [intro paragraph]                   │   │
│ │                                      │   │
│ │  work                                │   │
│ │  [CIRCLE LOGOS — client logos]       │   │
│ │                                      │   │
│ │  skills                              │   │
│ │  [list of skills, coral links]       │   │
│ └──────────────────────────────────────┘   │
└────────────────────────────────────────────┘
```

- Body background: `#BDE0F5`
- Side frame/border color: `#D4665E` (coral — approximately 40px solid border or background strip)
- Client logos: circular crop, `width: 140px; height: 140px;`

### 5.6 Contact Page (`/contact`)
Split layout: blue hero header at top, coral contact card below.

```
┌──────────────────────────────────────────────┐
│  [NAV]                                        │
│                                              │
│  work with us           ← large charcoal h1  │
│  ready to outpace the competition? ...       │
│                                              │
├──────────────────────────────────────────────┤
│  ┌────────────────────────────────────────┐  │
│  │  CORAL CARD (#D4665E bg)               │  │
│  │                                        │  │
│  │  let's chat   ← large charcoal h2      │  │
│  │                                        │  │
│  │  phone | email | social (3 cols)       │  │
│  │                                        │  │
│  │  [CONTACT FORM]                        │  │
│  │  first  last  email*                   │  │
│  │  [message textarea]                    │  │
│  │  [submit button]                       │  │
│  └────────────────────────────────────────┘  │
└──────────────────────────────────────────────┘
```

- Top section: `background: #BDE0F5`
- Coral card: `background: #D4665E; padding: 64px; border-radius: 4px;`
- Form inputs: `background: #FFFFFF; border: 1px solid #363432; padding: 12px 16px;`
- Card text: charcoal headings, charcoal labels, charcoal body

---

## 6. Navigation Component

```
[home]   [services]   [work]   [philosophy]   [contact]
```

- **Position:** Top right on every page
- **Font:** Poppins 400, 16px, lowercase
- **Color (inactive):** `#6B6B6B`
- **Color (active/current):** `#D4665E` (coral), weight 700
- **Spacing:** `gap: 48px` between items
- **No underline** on links
- **No background** (transparent nav bar, floats over page)
- **Hover state:** transition to coral `#D4665E`

---

## 7. Components

### Logo Mark

```
MYERS
& CO.■     ← the period is a coral-colored SQUARE, not a round glyph
──────────────────  ← coral rule, full width of text block
Growth Consultancy
```

**Confirmed from logo source files (2026-05-23):**

- "MYERS" and "& CO." stacked on two lines
- Font: Poppins 800 ExtraBold, ~96–120px display size, `color: #55AADF`
- **The period in "CO." is a small coral-colored square** (`color: #E8635A`) — this is a deliberate typographic brand detail, not a standard period. Implement as a `<span>` with coral color, or use a CSS `::after` square block.
- Horizontal rule: `border: none; border-top: 3px solid #E8635A; width: 100%` of text block width
- "Growth Consultancy": Poppins 400 Regular, ~22px, `color: #55AADF`, `letter-spacing: 0.15em`

**Two logo variants provided:**
- `images/logo-white.png` — blue text on white square background → **use on homepage left white panel**
- `images/logo-transparent.png` — blue text on transparent background → use on dark overlays, OG image, etc.

**⚠️ Action required:** Save the two logo PNG files provided by the client into `images/logo-white.png` and `images/logo-transparent.png`. The HTML already references these paths with a CSS fallback while they're missing.

**Do not recreate the logo in CSS alone** — always reference the PNG source files for exact proportions and spacing.

### Circular Image / Logo Card
```css
.circle-asset {
  width: 140px;
  height: 140px;
  border-radius: 50%;
  object-fit: cover;
  overflow: hidden;
}
```

### Contact Form
```
[first name input]  [last name input]  [email input]
[message textarea — full width]
[submit button]
```
- Input: white background, 1px solid border, no border-radius (square)
- Submit button: coral background, white text, Poppins 600, uppercase or lowercase depending on style choice
- Label text: 13px, charcoal, lightweight

### Three-Column Feature Grid
```css
.feature-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 48px;
  text-align: center;
}
```

---

## 8. Content Inventory (all pages)

### Home (`/`)
- **Hero copy:** "for over a decade, i've been shoulder-to-shoulder with the disruptors…"
- **CTA line:** "let's grab a whiteboard, some cold brew, and rewrite the rules of the game."
- **Closing line:** "welcome to myers & company growth consultancy"
- **Social:** LinkedIn → http://linkedin.com/in/mmyers0429

### Services (`/services`)
**Section heading:** "what we do"

| Pillar | Icon type | Sub-services |
|---|---|---|
| foundational acquisition | circular photo (building blocks) | customer acquisition strategy; marketing automation & analytics |
| data-driven growth | coral brain icon (circular) | customer experience optimization; go-to-market strategy & execution |
| brand expansion & scale | megaphone icon (circular) | growth hacking & experimentation; scalable growth infrastructure |

### Philosophy (`/philosophy`)
**Section heading:** "our philosophy"

| Pillar | Image | Description |
|---|---|---|
| plant the roots | seedling photo | Acquisition through smart traffic channels (SEM, SEO, affiliate) |
| cultivate passion | vineyard/field photo | Data-driven up-funnel strategy using early adopter insights |
| blossom boldly | flowers photo | Brand expansion via OTT/TV, audio, direct mail |

### Work / C.V. (`/c-v`)
**Intro:** "with 20+ years of marketing experience, the last 10 of which at financial service firms..."

**Client logos shown:** HireQuest (H logo), another fintech logo, "YOUR LOGO HERE" placeholder

**Skills listed:**
- customer acquisition & retention
- affiliate & lead generation marketing
- data analysis & interpretation
- copywriting & storytelling

### Contact (`/contact`)
- **Heading:** "work with us"
- **Sub-copy:** "ready to outpace the competition? let's unlock your growth potential - together."
- **Card heading:** "let's chat"
- **Phone:** 201 614 7418
- **Email:** matt@myersandcompany.co
- **Social:** LinkedIn

---

## 9. Meta / SEO
- **Site title pattern:** `Myers&Co | [Page Name]`
- **Meta description:** "Myers&Company helps financial services companies of all shapes and sizes scale and refine their growth marketing & customer acquisition efforts"
- **OG image:** Hosted at Wix static CDN (should be replaced with custom asset in redesign)

---

## 10. Design Principles for Redesign

1. **Lowercase everything** — it's a brand voice decision. All headings, nav, CTAs, and body copy render in lowercase.
2. **Sky blue is the brand canvas.** The interior page experience should feel immersive in this color.
3. **Coral is the energy.** Use it liberally for text on blue backgrounds, accents, and call-to-action elements.
4. **Big, bold headings.** The display type should be very large and confident — this is not a shy brand.
5. **Generous whitespace.** The current design breathes well; maintain large section padding (80–96px+).
6. **Poppins only.** Stick to a single font family across all weights. No serif or secondary fonts.
7. **Circles for imagery.** All photos and logos should be cropped to circular frames.
8. **Mobile:** The Wix version doesn't do mobile well. The redesign should use responsive column stacking (3-col → 1-col, split → stacked).
9. **No gradients, no shadows.** The aesthetic is flat and clean. Depth comes from color contrast, not effects.
10. **Contact form on coral card.** The coral card framing the contact form is a signature element — preserve it.
