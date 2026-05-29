# Personal Portfolio Website — UI/UX Design Spec (v1)

A beginner-friendly blueprint for a modern student portfolio, buildable with **only HTML5 + CSS3** (Flexbox, Grid, media queries). No frameworks required.

---

## 1. Design Language

### Color Palette — "Modern Light + Indigo Accent"
| Token | Hex | Use |
|---|---|---|
| `--bg` | `#F7F8FA` | Page background |
| `--surface` | `#FFFFFF` | Cards, header |
| `--text` | `#0F172A` | Headings, primary text |
| `--muted` | `#64748B` | Secondary text |
| `--primary` | `#4F46E5` | Buttons, links, accents |
| `--primary-hover` | `#4338CA` | Hover state |
| `--border` | `#E5E7EB` | Dividers, card borders |
| `--shadow` | `rgba(15, 23, 42, 0.06)` | Soft shadows |

**Optional Dark Mode swap:** `--bg #0B1020`, `--surface #131A2B`, `--text #F8FAFC`, `--muted #94A3B8`, primary unchanged.

### Typography
- **Headings:** `Poppins`, fallback `system-ui, sans-serif` — weights 600/700
- **Body:** `Inter`, fallback `system-ui, sans-serif` — weight 400/500
- **Scale (rem):** H1 `2.75` · H2 `2` · H3 `1.5` · Body `1` · Small `0.875`
- **Line-height:** 1.2 headings, 1.65 body
- Load via single `<link>` from Google Fonts.

### Spacing System (8px grid)
`4, 8, 12, 16, 24, 32, 48, 64, 96` — use these only. Section vertical padding: `96px` desktop / `64px` tablet / `48px` mobile.

### Radius & Shadows
- `--radius-sm: 8px` (buttons, inputs)
- `--radius-md: 16px` (cards)
- `--radius-lg: 24px` (hero image frame)
- Card shadow: `0 4px 16px var(--shadow)`
- Hover shadow: `0 10px 24px rgba(79,70,229,0.15)`

### Motion
- All interactive elements: `transition: all 200ms ease;`
- Hover: lift `translateY(-2px)` + shadow upgrade
- Buttons: subtle scale `1.02`
- Avoid heavy JS animation — pure CSS only.

---

## 2. Page Structure (Desktop, max-width 1200px, centered, 24px gutter)

```
┌──────────────────────────────────────────────────────┐
│ HEADER (sticky, 72px, white, bottom border)          │
│  [Logo: Alex.dev]                  Home About Skills │
│                                    Contact           │
├──────────────────────────────────────────────────────┤
│ HERO  (two-column flex, 96px padding)                │
│  ┌──────────────────────┐  ┌────────────────────┐    │
│  │ Hi, I'm Alex 👋       │  │                    │    │
│  │ Frontend Developer    │  │   PROFILE IMAGE    │    │
│  │ Learning Modern Web   │  │   (rounded blob)   │    │
│  │                       │  │                    │    │
│  │ short paragraph...    │  └────────────────────┘    │
│  │ [Contact Me] [Projects]                       │    │
│  └──────────────────────┘                        │    │
├──────────────────────────────────────────────────────┤
│ ABOUT  (two-column)                                  │
│  [Avatar 240px]   About Me                           │
│                   bio paragraph + soft card           │
├──────────────────────────────────────────────────────┤
│ SKILLS  (3-column grid of skill cards)               │
│  [HTML5]   [CSS3]   [JS basics]                      │
│  icon       icon     icon                            │
│  progress   progress progress                         │
├──────────────────────────────────────────────────────┤
│ CONTACT  (centered form, 560px max)                  │
│  Name __________                                     │
│  Email _________                                     │
│  Message _______                                     │
│              [Send Message]                          │
├──────────────────────────────────────────────────────┤
│ FOOTER  (centered, muted bg)                         │
│  social icons     © 2026 Alex                        │
└──────────────────────────────────────────────────────┘
```

---

## 3. Section-by-Section

### Header / Nav
- `position: sticky; top: 0;` with `backdrop-filter: blur(10px);` and 80% white background
- Flex row: `justify-content: space-between; align-items: center;`
- Logo: bold 1.25rem text — `Alex<span style="color:var(--primary)">.dev</span>`
- Nav links: 32px gap, color `--muted`, hover `--text` with 2px underline grow
- **Hamburger** (≤768px): three 24×2px bars stacked, animate to X on `:checked` using a hidden checkbox trick — pure CSS

### Hero
- Flex container, gap 64px, `align-items: center`
- Left column (55%): eyebrow chip "Available for internships" → H1 → paragraph → button row
- Buttons:
  - Primary: solid `--primary`, white text, `padding: 14px 28px`, radius 8px
  - Secondary: transparent, 1.5px primary border, primary text
- Right column (45%): circular/blob image 360×360, soft drop shadow, optional gradient ring `background: linear-gradient(135deg, #4F46E5, #06B6D4)` padding 4px around image

### About
- White card, padding 48px, radius 16px, soft shadow
- Two columns: avatar (240px round) + text
- Short bio (2–3 lines) + 3 quick-fact pills ("📍 Based in Karachi", "🎓 BSc Year 2", "💻 Self-taught")

### Skills
- CSS Grid: `grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 24px;`
- Skill card (white, radius 16px, padding 24px):
  - Icon 48px (use Devicon CDN or inline SVG)
  - Skill name (H3)
  - Progress bar: outer `height:8px; background:#E5E7EB; radius:999px`, inner filled `--primary` with width % (HTML5 70%, CSS3 65%, JS 40%)
- Hover: `transform: translateY(-4px)` + colored shadow

### Contact
- Centered form, max-width 560px
- Inputs: full-width, padding 14px 16px, 1px `--border`, radius 8px, white bg
- `:focus` → border `--primary`, `box-shadow: 0 0 0 4px rgba(79,70,229,0.15)`
- Textarea: min-height 140px, resize vertical
- Labels above inputs, 8px gap, font-weight 500
- Submit: full-width primary button on mobile, auto-width right-aligned on desktop

### Footer
- Background `--text` (dark slate), text white/muted
- Centered: row of 4 social icons (32px, circular hover bg), copyright line below
- Padding 48px vertical

---

## 4. Responsive Breakpoints

| Breakpoint | Behavior |
|---|---|
| `≥1024px` | Full desktop layout as drawn |
| `768–1023px` | Container 90%; hero text 2.25rem; skills 2 cols |
| `≤767px` | **Mobile**: nav collapses to hamburger; hero stacks (image first, text below, center-aligned); about stacks; skills 1 col; form full width; section padding 48px |

Use **mobile-first** media queries:
```css
/* base = mobile */
.hero { flex-direction: column; }

@media (min-width: 768px) {
  .hero { flex-direction: row; }
}
```

---

## 5. Mobile Wireframe

```
┌─────────────────┐
│ Alex.dev    ☰  │  ← sticky
├─────────────────┤
│   [ IMAGE ]     │
│                 │
│  Hi, I'm Alex   │
│  Frontend Dev   │
│  paragraph...   │
│ [Contact Me]    │
│ [View Projects] │
├─────────────────┤
│ About Me        │
│ [avatar]        │
│ bio text...     │
├─────────────────┤
│ Skills          │
│ [HTML5 card]    │
│ [CSS3 card]     │
│ [JS card]       │
├─────────────────┤
│ Contact         │
│ Name _____      │
│ Email ____      │
│ Message __      │
│ [Send]          │
├─────────────────┤
│   © 2026 Alex   │
└─────────────────┘
```

---

## 6. Hover & Interaction Notes
- **Buttons:** lift + shadow + slight scale
- **Nav links:** animated underline left→right (`::after` width transition)
- **Skill cards:** lift + colored glow
- **Inputs:** focus ring + border color shift
- **Social icons:** background fill in on hover
- **Hamburger:** rotate bars into X (CSS only, checkbox hack)

---

## 7. Accessibility Checklist
- Contrast ≥ 4.5:1 (palette above passes)
- `<button>` and `<a>` have visible `:focus-visible` outlines
- All images: `alt=""` text
- Form: `<label for="...">` paired with each input
- Semantic tags: `<header> <nav> <main> <section> <form> <footer>`

---

## 8. Suggested File Structure
```
portfolio/
├── index.html
├── styles.css
└── assets/
    ├── profile.jpg
    ├── avatar.jpg
    └── icons/  (html5.svg, css3.svg, js.svg, github.svg, linkedin.svg)
```

---

## 9. Beginner-Friendly Build Order
1. Set up `<head>` with fonts + meta viewport
2. Build mobile layout first (single column, no media queries)
3. Add header + hamburger (CSS checkbox trick)
4. Style hero with flex
5. Add about, skills (grid), contact
6. Footer
7. Add `@media (min-width: 768px)` to enable desktop two-column layouts
8. Polish: hover states, transitions, focus rings

---

**End of spec.** Use this as your design reference and build it section-by-section with vanilla HTML/CSS.
