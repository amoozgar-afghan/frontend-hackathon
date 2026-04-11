# Frontend Hackathon — Project Documentation

> A multi-page static website for a frontend hackathon event. Built with semantic HTML5 and vanilla CSS using a shared base stylesheet + per-page CSS architecture.
---

## 📁 Project Structure

```
frontend-hackathon/
│
├── index.html                  ← Homepage (root level)
│
├── pages/
│   ├── awards.html
│   ├── schedule.html
│   ├── contact.html
│   └── signup.html
│
├── styles/
│   ├── style.css               ← Shared base styles (loaded on ALL pages)
│   ├── awards.css              ← Awards page only
│   ├── schedule.css            ← Schedule page only
│   ├── contact.css             ← Contact page only
│   └── signup.css              ← Sign Up page only
│
├── images/
│   ├── logo-2.png
│   ├── hackathon-1.jpg
│   ├── attendAI.png
│   ├── buildScope.png
│   └── coding-icon.png
│
└── fonts/
    ├── Roboto-Regular.ttf
    ├── Roboto-Bold.ttf
    ├── Roboto-ExtraBold.ttf
    ├── Roboto-Light.ttf
    └── Roboto-LightItalic.ttf
```

---

## 🎨 CSS Architecture

### The Two-Layer Approach

Every page loads two CSS files: the shared base (`style.css`) and its own page-specific file.

```html
<!-- Example: contact.html -->
<link rel="stylesheet" href="./../styles/style.css" />
<link rel="stylesheet" href="./../styles/contact.css" />
```

The only exception is `index.html`, which only needs `style.css` because all of its sections (hero, features, testimonials, CTA) are already defined there.

```html
<!-- index.html — no page CSS needed -->
<link rel="stylesheet" href="styles/style.css" />
```

### Why This Structure?

| Approach | Pros | Cons |
|---|---|---|
| One giant CSS file | Simple to start | Gets messy fast; any dev editing it can break other pages |
| Separate file per page | Isolated, easy to find, easy to hand off | Slightly more `<link>` tags |
| CSS-in-JS / frameworks | Very powerful | Overkill for a static multi-page site |

This project uses **separate files per page** because it keeps each developer's work scoped. Editing `awards.css` cannot break the schedule page.

---

## 📄 What Lives Where

### `style.css` — Shared Base (All Pages)

Contains everything that appears on every single page.

| Section | Key Classes |
|---|---|
| Reset & base | `* { box-sizing }`, `body`, `h1`, `h2` |
| Navbar | `.navbar`, `.nav-links`, `.nav-item`, `.hamburger`, `#menu-toggle` |
| Hero (homepage) | `.hero`, `.hero-wrapper`, `.hero-content`, `.hero-visual` |
| Features (homepage) | `.features`, `.features-wrapper`, `.feature`, `.feature-icon` |
| Testimonials (homepage) | `.testimonials`, `.testimonial` |
| Call to Action (homepage) | `.action`, `.action-card`, `.action-title` |
| Footer | `footer`, `.copyright`, `.footer-logo`, `.page-links`, `.footer-links`, `.legal-links`, `.social-links` |
| Utility buttons | `.btn`, `.btn-lg`, `.btn-full`, `.btn-primary`, `.btn-secondary` |
| Fonts | `@font-face` for all 5 Roboto weights |

### `contact.css` — Contact Page Only

| Section | Key Classes |
|---|---|
| Hero | `.contact-hero`, `.contact-intro`, `.intro-card` |
| Contact card | `.contact-card`, `.phone-info`, `.email-info`, `.social-icons` |
| Form | `.contact-form`, `.input-group`, form inputs/textarea/select |

### `schedule.css` — Schedule Page Only

| Section | Key Classes |
|---|---|
| Hero | `.hero-flex`, `.hero-desc` |
| Layout shells | `.section-dark`, `.section-light`, `.container` |
| Arena | `.arena-flex`, `.arena-content`, `.location-box`, `.btn-outline`, `.btn-group` |
| Timeline | `.schedule-row`, `.schedule-title`, `.day-label`, `.events-list`, `.event-item`, `.event-time`, `.event-title` |
| Blockquote | `blockquote`, `.blockquote-author`, `.blockquote-icon` |
| FAQ | `.faq-title`, `.faq-flex`, `.faq-column`, `.faq-item` |

### `awards.css` — Awards Page Only

| Section | Key Classes |
|---|---|
| Hero | `.Awards-hero` |
| Prizes | `.upcoming-prizes-section`, `.upcoming-prizes-header`, `.prizes-container`, `.prize-card`, `.prize-icon` |
| Prize variants | `.grand-champion`, `.best-ui`, `.performance`, `.clean-arch`, `.small-quote` |
| Quote | `.quote-section` |
| Hall of Fame | `.hall-of-fame`, `.project`, `.project-image`, `.Project-text`, `.project-year`, `.project-tags` |
| CTA | `.call-to-action` |

### `signup.css` — Sign Up Page Only

| Section | Key Classes |
|---|---|
| Intro | `.Join` |
| Flow banner | `.flow-banner-container`, `.flow-banner-overlay`, `.flow-banner-img` |
| Form | `.form-container`, `.Form-Area`, `.Information-fill`, `.input-group` |
| Quote block | `.quote-block`, `.quote-text`, `.quote-img` |

---

## 🎨 Design Tokens

These values are used consistently across all CSS files. If you ever rebrand, these are the only values you need to change.

| Token | Value | Used For |
|---|---|---|
| Dark background | `#1F2937` | Navbar, footer, dark sections, cards |
| Light background | `#F9FAF8` | Page body, light sections |
| Accent blue | `#3882F6` | Buttons, highlights, icons, links |
| Accent blue hover | `#2a62c4` | Button hover states |
| Mid-dark card | `#2d3a4a` | Award prize cards |
| Input background | `#34445a` | Form inputs, icon backgrounds |
| Body text | `#1F2937` | Default text on light backgrounds |
| Light text | `#F9FAF8` | Text on dark backgrounds |
| Muted text | `#c7cbd4` / `#b1b7c2` | Descriptions, secondary text |
| Border/divider | `#E5E7EB` / `#b2b8c5` | Dividers, testimonial bg |
| Border radius — small | `5px` | Inputs, small buttons |
| Border radius — medium | `10px–12px` | Cards, contact cards |
| Border radius — large | `20px` | Feature cards, CTA card |
| Max content width | `1200px` | All `.container` / section wrappers |
| Font family | `'Roboto', 'Inter', 'Segoe UI', sans-serif` | All body text |

---

## 📐 Responsive Breakpoints

| Breakpoint | Rule | What changes |
|---|---|---|
| `≤ 600px` | `@media (max-width: 600px)` | Blockquote font shrinks; section padding reduces |
| `≤ 768px` | `@media (max-width: 768px)` | Hamburger menu appears; nav links stack vertically |
| `≥ 768px` | `@media (min-width: 768px)` | Hero goes side-by-side; contact card info rows become horizontal |
| `≤ 992px` | `@media (max-width: 992px)` | Schedule flex rows stack; arena, FAQ go single-column |
| `≥ 512px` | `@media (min-width: 512px)` | Contact card / form get min-width and padding |

---

## 🧭 Navigation & Routing

The nav is a pure CSS hamburger menu — no JavaScript. It works via a hidden `<input type="checkbox">` and the CSS sibling selector `~`.

```html
<!-- Pattern used on all pages -->
<input type="checkbox" id="menu-toggle">
<label for="menu-toggle" class="hamburger">
  <i class="fas fa-bars"></i>
</label>
<ul class="nav-links">...</ul>
```

```css
/* The toggle magic in style.css */
#menu-toggle:checked ~ .nav-links {
  display: flex;
}
```

### Path Convention

`index.html` lives at the root. All other pages live in `/pages/`. This means paths differ slightly:

| From `index.html` | From any page in `/pages/` |
|---|---|
| `styles/style.css` | `./../styles/style.css` |
| `./pages/awards.html` | `./awards.html` |
| `./images/logo-2.png` | `./../images/logo-2.png` |

---

## 🔤 Typography Scale

| Element | Size | Weight | Notes |
|---|---|---|---|
| `h1` | `48px` (awards hero: `72px`) | 900 | Uppercase, tight line-height |
| `h2` | `36px` | 700 | Section titles |
| Hero description | `18px` | 300/normal | Muted colour |
| Body / paragraph | `16px` | normal | `line-height: 1.6` |
| Small labels / tags | `0.8–0.9rem` | 700–800 | Uppercase, letter-spaced |
| Blockquote | `2.5rem` | 300 italic | Shrinks to `1.8rem` on mobile |
| Testimonial | `36px` | 300 italic | — |

---

## 🧩 Reusable Component Patterns

### Button Variants

All buttons share `.btn` as a base class. Layer modifiers on top:

```html
<button class="btn">Default</button>
<button class="btn btn-lg">Large</button>
<button class="btn btn-lg btn-secondary">Large Outline</button>
<button class="btn btn-lg btn-full">Full Width</button>
```

### Icon Badges (used in Features & Contact)

```html
<span class="feature-icon"><i class="fas fa-users"></i></span>
<!-- or -->
<span class="contact-card-icon"><i class="fa-solid fa-phone"></i></span>
```

Both use a `#34445a` rounded background with a `#3882F6` icon.

### Prize Cards (Awards)

Each prize card follows the same structure. The wrapper class (`.grand-champion`, `.best-ui`, etc.) can be used to apply per-card accent colours if needed:

```html
<div class="grand-champion prize-card">
  <span class="prize-icon"><i class="fa-solid fa-award"></i></span>
  <h3>Title</h3>
  <p>Description</p>
  <strong>$10,000</strong>
</div>
```

---

## 🔗 External Dependencies

| Dependency | Version | Purpose | CDN |
|---|---|---|---|
| Font Awesome | 7.0.1 | All icons (nav, contact, features, social) | cdnjs.cloudflare.com |

No JavaScript libraries. No CSS frameworks. No build tools required — open any `.html` file directly in a browser.

---

## 🚀 Getting Started

1. Clone or download the project
2. Make sure the folder structure matches the tree above (especially `styles/`, `images/`, `fonts/`)
3. Open `index.html` in any modern browser — no server needed
4. To work on a specific page, open the relevant HTML + its CSS file side by side

### Adding a New Page

1. Create `pages/newpage.html` — copy the nav and footer from any existing page
2. Create `styles/newpage.css` — add only styles specific to that page
3. Add `<link rel="stylesheet" href="./../styles/newpage.css" />` in the `<head>` after `style.css`
4. Add a nav link on all existing pages

---

## ✅ Developer Checklist

Before committing changes to any page:

- [ ] Does the page link both `style.css` and its own CSS file?
- [ ] Are new classes added to the **page CSS**, not to `style.css`?
- [ ] Does the navbar include all 5 links (Home, Award, Schedule, Contact, Sign Up)?
- [ ] Are image paths using `./../images/` (for `/pages/`) or `./images/` (for root)?
- [ ] Does the page look correct at 375px, 768px, and 1440px widths?
- [ ] Does the footer include copyright, page links, social links, and legal links?