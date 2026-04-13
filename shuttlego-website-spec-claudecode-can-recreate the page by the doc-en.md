# ShuttleGo Website Rebuild Specification
**Version:** v1.0  
**Date:** April 2026  
**File Type:** Single-page static website  
**Source File:** `index.html` (inline CSS + JS, no external framework)

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [File Structure & Dependencies](#2-file-structure--dependencies)
3. [Design System](#3-design-system)
4. [Page Layout](#4-page-layout)
5. [Navigation Bar](#5-navigation-bar)
6. [Section Specifications](#6-section-specifications)
7. [Interaction Behaviour](#7-interaction-behaviour)
8. [Internationalisation (i18n)](#8-internationalisation-i18n)
9. [Responsive Breakpoints](#9-responsive-breakpoints)
10. [Image Asset Inventory](#10-image-asset-inventory)
11. [Known Caveats](#11-known-caveats)

---

## 1. Project Overview

| Field | Value |
|-------|-------|
| **Brand** | ShuttleGo |
| **Slogan** | Fun Play, Every Day! |
| **Market** | Australia (badminton & pickleball community) |
| **Purpose** | Introduce app features, drive downloads & sign-ups, showcase the shop |
| **Tech stack** | Single HTML file — inline CSS + Vanilla JS, no build tools |
| **Languages** | English / Chinese — auto-detected from browser, manually switchable |

---

## 2. File Structure & Dependencies

### Local Files

```
/
├── index.html                   # Main file — all CSS and JS inline
├── logo.png                     # Nav logo (displayed at 150×40 px)
├── shuttlecock-vertical-48.png  # Shuttlecock icon (displayed at 50×50 px)
├── pickleball-small-200.png     # Pickleball icon (multi-size reuse)
```

### External Font (Google Fonts CDN)

```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;0,900;1,400;1,700&family=Montserrat:wght@300;400;500;600;700&display=swap" rel="stylesheet">
```

| Font | Role |
|------|------|
| **Playfair Display** | Headlines, brand name, stat numbers, section titles (serif) |
| **Montserrat** | Body text, nav links, buttons, labels (sans-serif) |

### No Other External Dependencies
- No jQuery / React / Vue
- No CSS framework (no Bootstrap / Tailwind)
- No map SDK — maps are pure CSS + HTML simulations
- All logic uses Vanilla JS

---

## 3. Design System

### 3.1 Brand Colours

| Variable | Value | Usage |
|----------|-------|-------|
| `--blue` | `#2391dc` | Primary — buttons, links, highlights |
| `--orange` | `#fe870a` | Secondary — prices, tags, secondary buttons |
| `--green` | `#b7da28` | Accent — dividers, section labels, badges |
| `--blue-dark` | `#1a6fa8` | Button hover state |
| `--orange-dark` | `#d96e00` | Orange hover state |

### 3.2 Light Mode Semantic Colours (`:root`)

| Variable | Value | Usage |
|----------|-------|-------|
| `--text-dark` | `#1a1a2e` | Primary text |
| `--text-mid` | `#3a3a5c` | Secondary text, nav links |
| `--text-light` | `#6b6b8a` | Descriptions, placeholders |
| `--bg-light` | `#fff9f3` | Main panel background |
| `--bg-card` | `#ffffff` | Card backgrounds |
| `--bg-section` | `#fdf4ea` | Alternating section backgrounds |
| `--border` | `rgba(183,218,40,0.3)` | Borders |
| `--shadow` | `0 8px 40px rgba(35,145,220,0.10)` | Card shadows |
| `--page-bg-start` | `#fef8f0` | Body gradient start (sides) |
| `--page-bg-end` | `#f0f5ea` | Body gradient end (sides) |

### 3.3 Dark Mode Semantic Colours (`[data-theme="dark"]`)

| Variable | Value |
|----------|-------|
| `--text-dark` | `#f0f0ff` |
| `--text-mid` | `#c0c0e0` |
| `--text-light` | `#a0a0c0` |
| `--bg-light` | `#1e1e3a` |
| `--bg-card` | `#252545` |
| `--bg-section` | `#181830` |
| `--border` | `rgba(183,218,40,0.25)` |
| `--shadow` | `0 8px 40px rgba(0,0,0,0.3)` |
| `--page-bg-start` | `#0f111a` |
| `--page-bg-end` | `#1a1a2e` |

### 3.4 Global Tokens

```css
--radius: 18px;
--transition: 0.35s cubic-bezier(0.4, 0, 0.2, 1);
```

### 3.5 Typography Rules

| Context | Font | Weight | Size |
|---------|------|--------|------|
| Hero H1 | Playfair Display | 900 | `clamp(2.8rem, 7vw, 5.5rem)` |
| Section title | Playfair Display | 700 | `clamp(2rem, 4vw, 3.2rem)` |
| Card title | Playfair Display | 700 | `1.4rem` |
| Slogan | Playfair Display | 400 italic | `clamp(1.1rem, 2.5vw, 1.6rem)` |
| Stat numbers | Playfair Display | 900 | `3rem` |
| Body / buttons / nav | Montserrat | 400–700 | `0.78rem – 1rem` |
| Nav links | Montserrat | 600 | `0.82rem`, uppercase, letter-spacing `0.08em` |

### 3.6 Reusable Component Styles

**Primary Button (`.btn-primary`)**
- Background: `var(--blue)` → hover: `var(--blue-dark)`
- Shape: pill (`border-radius: 50px`), padding `15px 38px`
- Hover: lift `translateY(-2px)` + shadow + shimmer sweep (`::before` pseudo-element)

**Secondary Button (`.btn-secondary`)**
- Transparent background, orange border and text
- Hover: orange fill, white text

**Card Rules**
- `border-radius: var(--radius)` (18px)
- `border: 1.5px solid var(--border)`
- `box-shadow: var(--shadow)`
- Hover: `translateY(-4px to -6px)` + enhanced shadow

**Section Label (`.section-label`)**
- Green bar (40px wide, 2.5px tall) + uppercase green text
- Used as a small prefix label above each section title

**Divider (`.divider`)**
- `height: 2px`
- `background: linear-gradient(90deg, transparent, var(--green), transparent)`

---

## 4. Page Layout

### 4.1 CSS Grid — Three-Column Centred Structure

```css
body {
  background: linear-gradient(135deg, var(--page-bg-start), var(--page-bg-end));
}
.page-wrapper {
  display: grid;
  grid-template-columns: 1fr min(1400px, 100%) 1fr;
  min-height: 100vh;
}
.main-panel {
  grid-column: 2 / 3;
  background: var(--bg-light);
  box-shadow: 0 0 40px rgba(0,0,0,0.08);
}
```

- Content max-width: **1400px**, horizontally centred
- Sides show the gradient body background as visible gutters
- `<nav>`, `<div id="floaters">`, and `<div id="cursor">` sit **outside** `.page-wrapper` (they are `fixed` positioned and must not participate in the grid)

### 4.2 DOM Structure

```
<body>
  <div id="cursor">              ← Custom cursor dot
  <div id="floaters">            ← Floating emoji particles
  <div class="page-wrapper">
    <div class="main-panel">
      <section id="home">        ← Hero
      <div class="divider">
      <section id="about">       ← Platform stats
      <div class="divider">
      <section id="features">    ← Core features (4 cards)
      <div class="divider">
      <section id="rewards">     ← Sign-up rewards
      <div class="divider">
      <section id="shop">        ← Gear shop
      <div class="divider">
      <section id="download">    ← App download
      <div class="divider">
      <section id="contact">     ← Contact
      <footer>
    </div>
  </div>
  <nav>                          ← Navigation (outside page-wrapper)
  <div class="mobile-menu">      ← Mobile menu (outside page-wrapper)
  <script>                       ← All JS inlined at bottom
```

---

## 5. Navigation Bar

### 5.1 Layout

| Property | Value |
|----------|-------|
| Position | `fixed; top:0; left:0; right:0` |
| z-index | `1000` |
| Height | `70px` |
| Background (light) | `rgba(255,249,243,0.88)` + `backdrop-filter: blur(18px)` |
| Background (dark) | `rgba(18,18,42,0.88)` |

### 5.2 Left — Logo

```html
<a href="#home" class="logo clickable">
  <img src="logo.png" class="logo-img" alt="ShuttleGo Logo">
</a>
```
- `.logo-img`: `width: 150px; height: 40px; object-fit: contain`
- **Do not** wrap `<img>` in a second `<div class="logo">` — causes double flex nesting

### 5.3 Centre — Nav Links

Six anchor links: About / Features / Rewards / Shop / Download / Contact  
Hover effect: text turns orange + orange underline expands from left (`scaleX` transition)

### 5.4 Right — Settings Button

```html
<button class="settings-btn" id="settingsBtn">   ← Gear icon (inline SVG)
<div class="settings-menu" id="settingsMenu">    ← Dropdown panel
  Language toggle  (English / Chinese)
  Theme toggle     (Light / Dark)
```

**Settings menu positioning — critical:**
```css
.settings-menu {
  position: fixed;   /* NOT absolute */
  top: 70px;
  right: 5vw;
  z-index: 9990;     /* Must exceed nav z-index of 1000 */
}
```

**Click logic (JS):**
```js
// Use an explicit `open` flag to prevent the document click listener
// from immediately closing the menu on the same event tick.
let open = false;
btn.addEventListener('click', e => {
  e.stopPropagation();
  open ? closeMenu() : openMenu();
});
document.addEventListener('click', () => { if (open) closeMenu(); });
menu.addEventListener('click', e => e.stopPropagation());
```

### 5.5 Mobile Hamburger Menu

- At `≤ 900px`: nav links hidden, hamburger icon shown (`display: flex`)
- Tap to toggle `.mobile-menu` (`position: fixed; top: 70px`)
- Contains all 6 nav links as full-width rows

---

## 6. Section Specifications

### 6.1 Hero (`#home`)

**Background:**  
`linear-gradient(135deg, rgba(35,145,220,0.03) 0%, rgba(254,135,10,0.03) 50%, rgba(183,218,40,0.03) 100%)`

**Rotating Racket Animation (`.hero-racket-anim`):**
- Three rackets arranged at 120° intervals like a Mercedes-Benz logo, rotating slowly around the centre
- Blue: badminton racket (ellipse shape)
- Orange: pickleball paddle (rounded rectangle)
- Green: tennis racket (ellipse + horizontal string lines)
- `animation: racket-spin 18s linear infinite`
- `opacity: 0.15`, `pointer-events: none`

**Content (top to bottom):**

1. **Hero Tag** — orange pill badge: `🏸 Badminton & Pickleball Platform`
2. **H1 — Three lines:**
   - Line 1: default colour — *Play More.*
   - Line 2: blue — *Connect Better.*
   - Line 3: orange — *Live Healthier.*
3. **Slogan:** `Shuttle Go — Fun Play, Every Day!` (Playfair Display, italic)
4. **Sub-copy:** brief description paragraph
5. **Two buttons:** Download App (primary) + Explore Features (secondary)

---

### 6.2 Platform Stats (`#about`)

**Background:** `var(--bg-section)`  
**Content:** section label + large title + description + 4-column stat cards

**Stat Cards (`.stats-grid`, 4 columns):**

| Number | English Label | Chinese Label |
|--------|--------------|---------------|
| 200+ | Venues | 场馆 |
| 1,500+ | Sessions / Month | 活动 / 月 |
| 25+ | Cities | 城市 |
| 8,000+ | Active Players | 活跃球员 |

Numbers use `background-clip: text` gradient (blue → orange).

---

### 6.3 Core Features (`#features`)

**Layout:** 2-column grid, 4 feature cards  
**Card structure:** `.feature-header` (icon + title + description) + `.feature-body` (content)

---

#### Card 1 — Session Finder

- **Icon:** `pickleball-small-200.png` (28×28 px), orange background
- **Body:** map carousel (2 slides)

**Slide 1** (`id="slide_s1"`) — Sydney, Badminton

| Field | Bubble A | Bubble B |
|-------|----------|----------|
| Distance | 📍 2.36 km | 📍 1.72 km |
| Venue | ABC Club @ Sydney Olympic Park | Jeremy's Group @ Marrickville Indoor |
| Session | Social Session, Tonight | Group Social, Tonight |
| Courts | 4 courts | 1 court |
| Players needed | 24 | 6 |
| Level | Intermediate+ | All levels welcome 🌟 |
| Badge | Badminton (blue) | Beginner OK (green) |

**Slide 2** (`id="slide_s2"`) — Melbourne, Pickleball

| Field | Bubble A | Bubble B |
|-------|----------|----------|
| Distance | 📍 2.1 km | 📍 4.5 km |
| Venue | Pickleball @ Alphington Sports Centre | Competitive Round Robin @ MSAC |
| Session | Open Play, Sat 9am | Tournament Style, Sun 2pm |
| Courts | 3 courts | 6 courts |
| Players needed | 12 | — |
| Level | All levels welcome 🌟 | Intermediate–Advanced |
| Badge | Pickleball (orange) | Rated (blue) |

**Carousel controls:** left/right arrows + dot indicators + text label (`id="slide_s_label"`)  
**Label texts:** `['Sydney · Badminton Activities', 'Melbourne · Pickleball Activities']`

---

#### Card 2 — Venue Search

- **Icon:** 🗺️, orange background
- **Body:** map carousel (2 slides)

**Slide 1** (`id="slide_v1"`) — Adelaide, Badminton Venues

| Field | Bubble A | Bubble B |
|-------|----------|----------|
| Distance | 📍 5.2 km | 📍 3.4 km |
| Name | Badminton SA Centre | Marion Indoor Stadium |
| Address | Wayville SA 5034 | Mitchell Park SA 5043 |
| Status | ● Open Now · 8 courts | ● Closed · Opens 6pm |

**Slide 2** (`id="slide_v2"`) — Brisbane, Pickleball Venues

| Field | Bubble A | Bubble B |
|-------|----------|----------|
| Distance | 📍 0.9 km | 📍 2.7 km |
| Name | Brisbane Pickleball Club | RNA Showgrounds Courts |
| Address | Coorparoo QLD 4151 | Bowen Hills QLD 4006 |
| Status | ● Open Now · 4 courts | ● Open Now · 6 courts |

**Carousel label ID:** `id="slide_v_label"`  
**Label texts:** `['Adelaide · Badminton Venues', 'Brisbane · Pickleball Venues']`

---

#### Card 3 — Club & Group Centre

- **Icon:** 🏆, green background
- **Body:** 4 feature rows (✓ list style)

| Item | Description |
|------|-------------|
| Create Club or Group | Public clubs or private invite-only groups |
| Manage Members | Approve, invite, remove, and assign roles |
| Session Controls | Set player count, courts, skill level, session price |
| Analytics Dashboard | Track attendance, revenue, and player engagement |

---

#### Card 4 — Gear Shop

- **Icon:** 🛍️, purple background
- **Body:** 2×2 grid, 4 category tiles

| Tile | Icon | Description | Discount |
|------|------|-------------|----------|
| Shuttlecocks | 🏸 | SG-10 ~ SG-50 | Up to 35% off |
| Restringing | 🎾 | Labour / Yonex / General | Up to 50% off |
| Pickleball Gear | pickleball image | Paddles & balls | 30% off w/ Token |
| Token Rewards | 🪙 | Earn & spend tokens | Join free |

---

#### Map Module — Common HTML Structure

```
.map-demo > .map-canvas > .map-bg
  ├── .map-road × 4        (horizontal and vertical road strips)
  ├── .map-label           (city name badge)
  ├── .map-user            (blue circle user icon, pulsing animation)
  ├── .map-bubble × 2      (floating info cards with tail arrow)
  └── .map-dot × 2         (venue location dots)
```

**Map bubble tail:** CSS triangle via `::after` pseudo-element  
**Bubble entry animation:** `bubble-in` keyframe (`scale(0.8) + translateY(10px)` → normal)  
**User pulse animation:** `pulse-user` keyframe (box-shadow expands/contracts, 2s loop)

---

### 6.4 Sign-up Rewards (`#rewards`)

**Background:** `linear-gradient(135deg, var(--bg-section) 0%, rgba(183,218,40,0.05) 100%)`  
**Layout:** `.rewards-container` — 2-column grid (`1fr 1fr`, gap `40px`, `align-items: start`)

**Left Panel (`.rewards-panel`) — 4-step flow:**

| Step | Title (EN) | Description |
|------|-----------|-------------|
| 1 | Download & Register | Sign up with the official invite code for an ad-free experience |
| 2 | Enter Official Code | Enter `GI12345` to receive 100 free Tokens 🎉 |
| 3 | Share Your Code | Your personal code `DI12345` — both you and your friend earn 100 bonus Tokens |
| 4 | Spend Tokens | Redeem for gear discounts (up to 35%) and restringing (up to 50%) |

**Invite code style (`.code-box`):** dashed border, monospace font, blue/orange colour

**Right Panel (`.rewards-panel`) — Token card:**
- Top: 🪙 gradient circle icon (orange → blue), 90×90 px, with glow shadow
- Title + description text
- 2×2 data grid:

| Value | Label |
|-------|-------|
| 100 (blue) | On Registration |
| +100 (orange) | Per Referral |
| 35% (green) | Max Gear Discount |
| 50% (purple) | Max Restring Discount |

---

### 6.5 Gear Shop (`#shop`)

**Tab bar:** Badminton / Pickleball (pill-shaped tab bar)  
**Default active tab:** Badminton

#### Badminton Tab (`#tab_badminton_content`)

**Shuttlecocks — 4-column grid:**

| Product | Retail Price | Token Price |
|---------|-------------|-------------|
| SG-10 | $42.00 | $27.00 |
| SG-20 | $44.90 | $29.90 |
| SG-30 | $47.00 | $32.00 |
| SG-50 | $49.90 | $35.00 |

Image: `shuttlecock-vertical-48.png` (displayed 50×50 px)

**Restringing Services — 4-column grid:**

| Service | Retail Price | Token Price |
|---------|-------------|-------------|
| Labour Only (BYO String) | $25.00 | $10.00 |
| General String | $30.00 | $20.00 |
| Yonex String (BG65, BG80 etc.) | $35.00 | $25.00 |
| Grommet Replacement | $10.00 | $5.00 |

#### Pickleball Tab (`#tab_pickleball_content`)

**Token price rule: Token price = Retail price × 70% (30% off across the board)**

**Paddles — 4-column grid:**

| Product | Retail | Token |
|---------|--------|-------|
| Control Pro Paddle | $89.00 | $62.30 |
| Power Drive Paddle | $129.00 | $90.30 |
| Elite Carbon Paddle | $189.00 | $132.30 |
| Junior Starter Paddle | $49.00 | $34.30 |

**Pickleballs — 4-column grid:**

| Product | Retail | Token |
|---------|--------|-------|
| Indoor Ball (3-pack) | $18.00 | $12.60 |
| Outdoor Ball (3-pack) | $22.00 | $15.40 |
| Tournament Ball (6-pack) | $35.00 | $24.50 |
| Starter Kit Bundle | $65.00 | $45.50 |

---

### 6.6 App Download (`#download`)

**Layout:** centred, max-width `800px`  
**Content:** section label + title + description + 2 QR cards side by side

Each QR card contains:
- 150×150 px QR placeholder (SVG-drawn mock pattern)
- Platform name (App Store / Google Play)
- Platform subtitle
- Download button (primary button with platform SVG icon inline)

---

### 6.7 Contact (`#contact`)

**Layout:** 6-column grid (`repeat(6, 1fr)`)

| Icon | Platform | Handle |
|------|----------|--------|
| 📧 | Email | hello@shuttlego.com.au |
| 💬 | WeChat | vx: shuttlego |
| 👤 | Facebook | @ShuttleGoAu |
| 🎵 | TikTok | @shuttlegoau |
| 📕 | Red Note | shuttlegoau |
| SVG | Instagram | @shuttlegoau |

Instagram uses an inline SVG (`viewBox="0 0 24 24"`, stroke style, `width/height: 35px`)

---

### 6.8 Footer (`<footer>`)

| Property | Value |
|----------|-------|
| Background (light) | `var(--text-dark)` (`#1a1a2e`) |
| Background (dark) | `#161628` |
| Text colour | `rgba(255,255,255,0.6)` |
| Layout | Centred, `padding: 40px 5vw` |

Content: brand name (Playfair Display, white) → slogan → copyright line (© 2026 ShuttleGo) → three footer links (Privacy Policy / Terms of Service / About)

---

## 7. Interaction Behaviour

### 7.1 Custom Cursor (`#cursor`)

| Property | Value |
|----------|-------|
| Size (default) | 22×22 px |
| Size (hovering) | 44×44 px |
| Background | `rgba(35,145,220,0.35)` |
| Border | `2px solid rgba(35,145,220,0.5)` |
| Position | `fixed`, `pointer-events: none`, `z-index: 99999` |
| Follow method | `requestAnimationFrame` lerp, factor `0.18` |
| Blend mode (light) | `mix-blend-mode: multiply` |
| Blend mode (dark) | `mix-blend-mode: screen` |

Hovering state triggered on all `.clickable`, `a`, and `button` elements via `mouseenter` / `mouseleave`.

### 7.2 Floating Particles (`#floaters`)

- On `mousemove` (if cursor moved > 8px): spawn a random 🏸 or 🔍 emoji near the cursor
- Size: `10–18px` random, `opacity: 0.22`
- After 700ms: fade out + scale down to 0.3
- 8 reusable DOM elements pre-created in JS, recycled by index

### 7.3 Map Carousel

```js
const slideIdx = { s: 0, v: 0 }; // Track current index for each group

function goSlide(key, idx) {
  // Toggle .active on all [id^="slide_${key}"] elements
  // Toggle .active on carousel dots within the same .feature-body
  // Update text of #slide_${key}_label
  slideIdx[key] = idx;
}

function slideMap(key, dir) {
  const slides = document.querySelectorAll(`[id^="slide_${key}"]`);
  const next = (slideIdx[key] + dir + slides.length) % slides.length;
  goSlide(key, next);
}
```

**Label element IDs — must match exactly:**
- Session Finder: `id="slide_s_label"`
- Venue Search: `id="slide_v_label"`

**Label text arrays:**
```js
const slideLabels = {
  s: ['Sydney · Badminton Activities', 'Melbourne · Pickleball Activities'],
  v: ['Adelaide · Badminton Venues',   'Brisbane · Pickleball Venues']
};
```

### 7.4 Shop Tab Switch

```js
function switchTab(tab) {
  document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  document.getElementById(`tab_${tab}_content`).classList.add('active');
  document.getElementById(`tab_${tab}`).classList.add('active');
}
```

Default active: `badminton`

### 7.5 Scroll Animation (`.fade-up`)

CSS sets `opacity: 0; transform: translateY(40px)`.  
`IntersectionObserver` (threshold `0.12`) adds `.visible` class to trigger `opacity:1; transform:none`.

> ⚠️ **Warning:** In iframe / embedded environments the observer may never fire, leaving content invisible. If deploying in such a context, change the CSS to `opacity: 1; transform: none` and remove the observer entirely.

### 7.6 Theme Toggle

```js
function setTheme(t) {
  document.body.setAttribute('data-theme', t); // 'light' or 'dark'
  localStorage.setItem('sg_theme', t);
  // Update active state on #modeLight and #modeDark buttons
}
// On init: read localStorage, default to 'light'
```

### 7.7 Language Toggle

```js
function applyLang(lang) {
  document.querySelectorAll('[data-i18n]').forEach(el => {
    const key = el.getAttribute('data-i18n');
    if (i18n[lang][key] !== undefined) el.textContent = i18n[lang][key];
  });
  // Update active state on #langEN and #langZH buttons
}
// On init: detect navigator.language — starts with 'zh' → Chinese, else English
```

---

## 8. Internationalisation (i18n)

All translatable text nodes carry a `data-i18n="key"` attribute.  
JS maintains `i18n.en` and `i18n.zh` objects. On switch, `el.textContent` is replaced with the matching value.

### Complete Key Reference

| Key | English | Chinese |
|-----|---------|---------|
| `nav_about` | About | 关于 |
| `nav_features` | Features | 功能 |
| `nav_rewards` | Rewards | 注册奖励 |
| `nav_shop` | Shop | 商城 |
| `nav_download` | Download | 下载 |
| `nav_contact` | Contact | 联系 |
| `settings_lang` | Language | 语言 |
| `settings_mode` | Display Mode | 显示模式 |
| `mode_light` | Light | 亮色 |
| `mode_dark` | Dark | 暗色 |
| `hero_tag` | 🏸 Badminton & Pickleball Platform | 🏸 羽毛球 & 匹克球平台 |
| `hero_title1` | Play More. | 多玩球。 |
| `hero_title2` | Connect Better. | 多交友。 |
| `hero_title3` | Live Healthier. | 更健康。 |
| `hero_sub` | Find sessions, discover courts… | 找活动、发现场馆… |
| `hero_btn1` | Download App | 下载App |
| `hero_btn2` | Explore Features | 探索功能 |
| `about_label` | Platform Overview | 平台概览 |
| `about_title` | ShuttleGo by the Numbers | ShuttleGo 数据一览 |
| `about_sub` | We're building the largest… | 我们正在打造… |
| `stat_venues` | Venues | 场馆 |
| `stat_sessions` | Sessions / Month | 活动 / 月 |
| `stat_cities` | Cities | 城市 |
| `stat_users` | Active Players | 活跃球员 |
| `feat_label` | Core Features | 核心功能 |
| `feat_title` | Everything You Need to Play | 一切你需要的，尽在其中 |
| `f1_title` | Session Finder | 活动查找 |
| `f1_desc` | Find nearby sessions… | 实时查找附近… |
| `f2_title` | Venue Search | 场馆搜索 |
| `f2_desc` | Discover courts near you… | 发现附近的场地… |
| `f3_title` | Club & Group Centre | 俱乐部 & 群组中心 |
| `f3_desc` | Organizers can create… | 组织者可创建… |
| `f3_a` | Create Club or Group | 创建俱乐部或群组 |
| `f3_a_d` | Public clubs or private invite-only groups | 公开俱乐部或私密邀请群组 |
| `f3_b` | Manage Members | 管理成员 |
| `f3_b_d` | Approve, invite, remove… | 审批、邀请、移除… |
| `f3_c` | Session Controls | 活动设置 |
| `f3_c_d` | Set player count, courts… | 设置人数、场地数量… |
| `f3_d` | Analytics Dashboard | 数据分析面板 |
| `f3_d_d` | Track attendance, revenue… | 追踪出席率、收益… |
| `f4_title` | Gear Shop | 装备商城 |
| `f4_desc` | Premium equipment… | 精选优质装备… |
| `f4_shuttle` | Shuttlecocks | 羽毛球 |
| `f4_restring` | Restringing | 穿线服务 |
| `f4_pickle` | Pickleball Gear | 匹克球装备 |
| `f4_token` | Token Rewards | Token奖励 |
| `rewards_label` | Sign-up Bonus | 注册福利 |
| `rewards_title` | Register & Earn Tokens | 注册即得Token |
| `rewards_sub` | Join ShuttleGo today… | 立即加入ShuttleGo… |
| `r1_title` | Download & Register | 下载并注册 |
| `r1_desc` | Sign up with official invite code… | 使用官方邀请码注册… |
| `r2_title` | Enter Official Code | 输入官方邀请码 |
| `r2_desc` | Enter code | 输入邀请码 |
| `r2_desc2` | to receive 100 free Tokens 🎉 | ，即可获得100个免费Token 🎉 |
| `r3_title` | Share Your Code | 分享你的邀请码 |
| `r3_desc` | Your personal code | 你的专属邀请码 |
| `r3_desc2` | — both you and your friend get 100 bonus Tokens! | — 你和你的朋友各得100个Token奖励！ |
| `r4_title` | Spend Tokens | 使用Token |
| `r4_desc` | Redeem tokens for gear discounts… | 用Token兑换装备折扣… |
| `rewards_card_title` | ShuttleGo Tokens | ShuttleGo Token |
| `rewards_card_sub` | Earn tokens through referrals… | 通过邀请好友… |
| `token_register` | On Registration | 注册奖励 |
| `token_refer` | Per Referral | 每次成功邀请 |
| `token_gear` | Max Gear Discount | 装备最高折扣 |
| `token_restring` | Max Restring Discount | 穿线最高折扣 |
| `shop_label` | Equipment Store | 装备商城 |
| `shop_title` | Gear Shop | 装备商城 |
| `shop_sub` | Premium equipment at the best prices… | 优质装备，最优价格… |
| `tab_bad` | Badminton | 羽毛球 |
| `tab_pick` | Pickleball | 匹克球 |
| `shop_shuttles` | Shuttlecocks | 羽毛球 |
| `shop_restring` | Restringing Services | 穿线服务 |
| `shop_paddles` | Paddles | 球拍 |
| `shop_balls` | Pickleballs | 匹克球 |
| `retail` | Retail: $42.00 | 零售价：$42.00 |
| `retail2` | Retail: $44.90 | 零售价：$44.90 |
| `retail3` | Retail: $47.00 | 零售价：$47.00 |
| `retail4` | Retail: $49.90 | 零售价：$49.90 |
| `token_price` | with Token | Token最优惠价 |
| `rs1` | Labour Only (BYO String) | 纯人工（自带线） |
| `rs2` | General String | 通用线穿线 |
| `rs3` | Yonex String (BG65, BG80 etc.) | Yonex线穿线（BG65、BG80等） |
| `rs4` | Grommet Replacement | 换护线管 |
| `pk1` | Control Pro Paddle | 控制型球拍 |
| `pk2` | Power Drive Paddle | 力量型球拍 |
| `pk3` | Elite Carbon Paddle | 精英碳素球拍 |
| `pk4` | Junior Starter Paddle | 青少年入门球拍 |
| `pb1` | Indoor Ball (3-pack) | 室内球（3个装） |
| `pb2` | Outdoor Ball (3-pack) | 室外球（3个装） |
| `pb3` | Tournament Ball (6-pack) | 比赛用球（6个装） |
| `pb4` | Starter Kit Bundle | 新手套装 |
| `dl_label` | Mobile App | 移动应用 |
| `dl_title` | Download ShuttleGo | 下载 ShuttleGo |
| `dl_sub` | Available on iOS and Android… | 支持iOS和Android… |
| `dl_ios` | iOS · iPhone & iPad | iOS · iPhone & iPad |
| `dl_android` | Android · All Devices | Android · 全系安卓设备 |
| `dl_ios_btn` | Download for iOS | iOS 下载 |
| `dl_android_btn` | Download for Android | Android 下载 |
| `contact_label` | Get in Touch | 联系我们 |
| `contact_title` | Contact Us | 联系方式 |
| `contact_sub` | Reach us through any of the following… | 通过以下任何渠道… |
| `footer_privacy` | Privacy Policy | 隐私政策 |
| `footer_terms` | Terms of Service | 服务条款 |
| `footer_about` | About | 关于我们 |

---

## 9. Responsive Breakpoints

| Breakpoint | Changes |
|------------|---------|
| `≤ 900px` | Nav links hidden → hamburger menu shown; `stats-grid` 2 cols; `features-grid` 1 col; `rewards-container` 1 col; `products-grid` 2 cols; `services-grid` 2 cols; `contact-grid` 2 cols; `qr-row` stacks vertically |
| `≤ 600px` | `stats-grid` 2 cols; `products-grid` 2 cols; `contact-grid` 2 cols; hero buttons stack vertically |
| `≤ 400px` | `contact-grid` 1 col |

---

## 10. Image Asset Inventory

| Filename | Usage | Display Size | Notes |
|----------|-------|-------------|-------|
| `logo.png` | Nav bar brand logo | 150×40 px | `object-fit: contain` |
| `shuttlecock-vertical-48.png` | Shop product image for shuttlecocks | 50×50 px | Used in 4 product cards |
| `pickleball-small-200.png` | Multi-size reuse across the page | See below | Same file, different sizes |

**`pickleball-small-200.png` size contexts:**

| Context | Size | CSS Class |
|---------|------|-----------|
| Feature icon | 28×28 px | `.feature-icon .pickleball-img` |
| Map bubble inline | 12×12 px | `.pickleball-small-img` |
| Shop product image | 50×50 px | `.product-emoji .pickleball-img` |
| Tab button | 18×18 px | `.tab-btn .pickleball-img` |

---

## 11. Known Caveats

**1. `fade-up` invisible in iframe / embedded contexts**  
`IntersectionObserver` may not fire when the page runs inside an iframe or sandboxed environment, leaving all `.fade-up` elements at `opacity: 0` permanently. When deployed to a standalone domain this works correctly. To support embedded contexts, change the CSS to `opacity: 1; transform: none` and remove the observer JS.

**2. Settings menu must use `position: fixed`**  
The `<nav>` element lives outside `.page-wrapper`. If `.settings-menu` uses `position: absolute`, it positions relative to the nearest positioned ancestor (the viewport edge), which causes the menu to drift. Use `position: fixed; top: 70px; right: 5vw; z-index: 9990`.

**3. Carousel label IDs must match the JS lookup**  
`goSlide(key, idx)` looks up `#slide_${key}_label`. The HTML must use exactly:
- Session Finder: `id="slide_s_label"`
- Venue Search: `id="slide_v_label"`

Any other ID value will silently fail to update the label text.

**4. Do not double-nest the logo**  
The `<a class="logo">` element already applies the flex layout. Placing a second `<div class="logo">` inside it creates duplicate flex containers and breaks alignment.

**5. Cloudflare email obfuscation**  
If the site is proxied through Cloudflare, email addresses in the HTML are automatically replaced with `<a class="__cf_email__">` tags and a decoding script is injected. This is expected behaviour, not a code error.

**6. `<nav>` placement outside `.page-wrapper` is intentional**  
`position: fixed` elements do not participate in grid layout. Placing `<nav>` inside the grid would cause it to occupy a grid cell and disrupt the layout. The comment in the HTML (`<!-- NAVIGATION (放在外面因为fixed定位会影响grid) -->`) documents this decision.

**7. Token discount rules differ by category**  
- Shuttlecocks and restringing: fixed Token prices (not a percentage — each product has a specific discounted value)
- Pickleball products: Token price = Retail × 70% (flat 30% off)

---

*Maintained by the ShuttleGo development team — Last updated: April 2026*
