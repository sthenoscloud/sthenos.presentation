# Design System — SpaceX-Inspired /sthenos.cloud

## 1. Visual Theme & Atmosphere

SpaceX's website is a full-screen cinematic experience treating aerospace engineering like a film — every section is a scene, every photograph is a frame, and the interface disappears entirely behind the imagery. Pure black (`#000000`) canvas with photography of rockets, space, and planets occupying 100% of the viewport. Text overlays sit directly on photographs with no background panels, cards, or containers — just type on image.

**D-DIN** typeface (industrial geometric with DIN heritage). ALL text is uppercase with positive letter-spacing (0.96px–1.17px), creating a military/aerospace labeling system. D-DIN-Bold at 48px with uppercase and 0.96px tracking for hero headlines feels like mission briefing titles.

**Radical minimalism**: no shadows, no borders (except ghost button border at `rgba(240,240,250,0.35)`), no color (only black and spectral `#f0f0fa`), no cards, no grids. The only visual element is photography + text. Ghost button with `rgba(240,240,250,0.1)` background and 32px radius is the sole interactive element — barely visible, floating like a heads-up display.

## 2. Color Palette

| Role | Token | Hex/Value |
|------|-------|-----------|
| Background | `--space-black` | `#000000` |
| Text | `--spectral-white` | `#f0f0fa` |
| Button BG | `--ghost-surface` | `rgba(240, 240, 250, 0.1)` |
| Button Border | `--ghost-border` | `rgba(240, 240, 250, 0.35)` |
| Overlay | `--dark-overlay` | `rgba(0, 0, 0, 0.5)` |

## 3. Typography

### Font
- **D-DIN-Bold** (700) — headlines
- **D-DIN** (400) — body
- Fallback: `Arial, Verdana`

### Hierarchy

| Role | Size | Weight | LS | Notes |
|------|------|--------|----|-------|
| Display Hero | 48px | 700 | 0.96px | uppercase |
| Section Title | 32px | 700 | 0.96px | uppercase |
| Card Title | 18px | 700 | 0.96px | uppercase |
| Body | 16px | 400 | normal | |
| Nav Link Bold | 13px | 700 | 1.17px | uppercase |
| Nav Link | 12px | 400 | normal | uppercase |
| Caption Bold | 13px | 700 | 1.17px | uppercase |
| Micro | 10px | 400 | 1px | uppercase |

## 4. Components

### Ghost Button
```
background: rgba(240, 240, 250, 0.1)
border: 1px solid rgba(240, 240, 250, 0.35)
border-radius: 32px
padding: 18px 32px
text-transform: uppercase
letter-spacing: 1.17px
color: #f0f0fa
```
Hover: background brightens, text to #ffffff

### Navigation
- Transparent overlay on photography
- D-DIN 13px weight 700, uppercase, 1.17px tracking
- Spectral white text

### Section (Full-Viewport)
- 100vh height
- Background-image: cover
- Dark overlay gradient for text legibility
- Left-aligned text block over image

### Cards/Containers
- **None** — text sits directly on photography
- Use subtle section dividers if needed

## 5. Layout

- Base unit: 8px
- Scale: 3px, 5px, 12px, 15px, 18px, 20px, 24px, 30px, 48px
- No traditional grid — each section is full-viewport cinematic frame
- Left-aligned text blocks on photography backgrounds
- Content bleeds to viewport edges

## 6. Depth

| Level | Treatment |
|-------|-----------|
| Photography (0) | Full-viewport imagery |
| Overlay (1) | `rgba(0, 0, 0, 0.5)` gradient |
| Text (2) | Spectral white, no shadow |
| Ghost (3) | `rgba(240, 240, 250, 0.1)` surface |

**Zero shadows** — depth comes from photographic content itself.

## 7. Responsive

| Breakpoint | Width | Changes |
|------------|-------|---------|
| Mobile | <600px | Stacked, reduced padding |
| Tablet | 600–1280px | Adjusted layout |
| Desktop | 1280–1500px | Full layout |
| Ultra-wide | >1500px | Maximum viewport |

## 8. Do's and Don'ts

**Do:**
- Full-viewport photography as primary design element
- Uppercase + positive letter-spacing on ALL text
- D-DIN exclusively
- Black + spectral white (#f0f0fa) only
- Ghost buttons as sole interactive element
- Dark gradient overlays for legibility

**Don't:**
- Cards, panels, containers
- Shadows
- Colors outside palette
- Sentence case
- Negative letter-spacing
- Decorative elements (icons, badges, dividers)

## 9. Implementation Pattern

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Title — sthenos.cloud</title>
<style>
@import url('https://fonts.cdnfonts.com/css/d-din');
*{margin:0;padding:0;box-sizing:border-box}
:root{
  --space-black:#000000;
  --spectral-white:#f0f0fa;
  --ghost-surface:rgba(240,240,250,0.1);
  --ghost-border:rgba(240,240,250,0.35);
  --dark-overlay:rgba(0,0,0,0.5);
}
body{
  font-family:'D-DIN',Arial,Verdana,sans-serif;
  background:var(--space-black);
  color:var(--spectral-white);
  min-height:100vh;
}
.section{
  min-height:100vh;
  background-size:cover;
  background-position:center;
  position:relative;
  display:flex;
  align-items:center;
  padding:80px 5%;
}
.section::before{
  content:'';
  position:absolute;
  inset:0;
  background:var(--dark-overlay);
}
.content{
  position:relative;
  z-index:1;
  max-width:600px;
}
h1{font-size:48px;font-weight:700;text-transform:uppercase;letter-spacing:0.96px;line-height:1}
h2{font-size:32px;font-weight:700;text-transform:uppercase;letter-spacing:0.96px}
p{font-size:16px;line-height:1.6}
.ghost-btn{
  display:inline-block;
  background:var(--ghost-surface);
  border:1px solid var(--ghost-border);
  border-radius:32px;
  padding:18px 32px;
  color:var(--spectral-white);
  text-decoration:none;
  text-transform:uppercase;
  letter-spacing:1.17px;
  font-size:13px;
  font-weight:700;
  margin-top:24px;
}
.ghost-btn:hover{background:rgba(240,240,250,0.2)}
nav{display:flex;gap:24px;padding:24px 5%}
nav a{color:var(--spectral-white);text-decoration:none;text-transform:uppercase;letter-spacing:1.17px;font-size:13px;font-weight:700}
</style>
</head>
<body>
<nav>
  <a href="#">Home</a>
  <a href="#">About</a>
</nav>
<section class="section" style="background-image:url('hero.jpg')">
  <div class="content">
    <h1>Mission Title</h1>
    <p>Supporting text goes here.</p>
    <a href="#" class="ghost-btn">Learn More</a>
  </div>
</section>
</body>
</html>
```