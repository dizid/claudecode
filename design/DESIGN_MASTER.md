# SalesTaskMaster Design Master Guide

Complete consolidated design system documentation for SalesTaskMaster frontend.

---

## Table of Contents

1. [Core Design Principles](#core-design-principles)
2. [Color Palettes](#color-palettes)
3. [Animation Recipes](#animation-recipes)
4. [RPG/Fantasy Patterns](#rpgfantasy-patterns)

---

# Core Design Principles

Create distinctive, high-quality frontends that surprise and delight users. Avoid generic aesthetics and make bold, creative design choices.

## Typography Excellence

Typography instantly signals quality. Every font choice shapes user perception.

### Never Use These Fonts

- Inter, Roboto, Open Sans, Lato, Arial
- System fonts without intentional styling
- Helvetica in generic implementations

### Distinctive Fonts to Use

- **Code/Technical aesthetic**: JetBrains Mono, Fira Code, Space Grotesk, IBM Plex Mono, Inconsolata
- **Editorial/Literary**: Playfair Display, Crimson Pro, Spectral, Newsreader, Lora
- **Technical/Modern**: IBM Plex family, Source Sans 3, Manrope, DM Sans
- **Distinctive/Unique**: Bricolage Grotesque, Newsreader, Unbounded, Syne, Cabinet Grotesk
- **Geometric/Clean**: Outfit, Plus Jakarta Sans, Lexend, Poppins (sparingly)
- **Display/Bold**: Bebas Neue, Oswald, Archivo Black, Righteous

### Pairing Strategies for Maximum Impact

- High contrast = interesting (Display + Monospace, Serif + Geometric Sans)
- Variable fonts across weights (use extremes: 100/200 vs 800/900, not 400 vs 600)
- Size jumps of 3x+ for hierarchy, not 1.5x
- One distinctive hero font used decisively

### Implementation

Load fonts from Google Fonts or Bunny Fonts. Use `@import` in CSS or `<link>` in HTML head.

---

## Color & Theme Mastery

Generic palettes kill uniqueness. Commit to cohesive, distinctive color schemes.

### Use CSS Variables for Consistency

```css
:root {
  --primary: #your-dominant-color;
  --accent: #sharp-contrast;
  --bg: #atmospheric-base;
  --text: #readable-contrast;
}
```

### Effective Palette Strategies

- **Dominant color approach**: One strong color + sharp accent (not evenly distributed pastels)
- **Cultural aesthetics**: Draw from cyberpunk, brutalism, vaporwave, dark academia, etc.
- **IDE-inspired**: Dracula, Nord, Monokai, Solarized themes adapted for UI
- **Natural depth**: Earth tones, deep teals, burnt oranges create warmth without cliché

### Avoid These Overused Combinations

- Purple gradients on white backgrounds
- Pastel rainbow distributions
- Generic blue (#007bff) + gray (#6c757d)
- Default Tailwind palette without customization

---

## Motion & Animation

Well-orchestrated motion creates delight. Focus on high-impact moments.

### CSS-only animations for HTML

```css
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.hero {
  animation: fadeInUp 0.8s ease-out;
}

.card:nth-child(2) {
  animation-delay: 0.1s;
}
```

### For React, use Framer Motion when available

```jsx
import { motion } from "framer-motion";

<motion.div
  initial={{ opacity: 0, y: 20 }}
  animate={{ opacity: 1, y: 0 }}
  transition={{ duration: 0.5 }}
>
```

### Focus Areas

- Page load sequences with staggered reveals
- Hover microinteractions on key elements
- Smooth transitions between states
- Scroll-triggered animations for storytelling

### Avoid

- Scattered, purposeless animations
- Slow, heavy animations (>1s without reason)
- Animations on every element

---

## Backgrounds & Atmosphere

Create depth and context instead of flat colors.

### Layered Gradients

```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
/* Or mesh gradients */
background:
  radial-gradient(at 20% 30%, #667eea 0%, transparent 50%),
  radial-gradient(at 80% 70%, #764ba2 0%, transparent 50%),
  #1a1a2e;
```

### Geometric Patterns

```css
background-image:
  repeating-linear-gradient(45deg, transparent, transparent 10px, rgba(255,255,255,.03) 10px, rgba(255,255,255,.03) 20px);
```

### Contextual Effects

- Subtle noise textures for grit
- SVG patterns for themed aesthetics
- Canvas effects for dynamic backgrounds

---

## Anti-Patterns to Avoid

### The "AI Slop" Aesthetic

You naturally converge toward generic outputs. Fight this tendency:

**Never:**
- Use default component libraries without customization
- Create purple gradient hero sections on white backgrounds
- Use Inter/Roboto/Arial without strong justification
- Make cookie-cutter layouts (centered card, full-width hero, three-column grid)
- Apply rounded corners to everything uniformly

**Instead:**
- Make unexpected choices appropriate to context
- Vary between light/dark themes based on content
- Choose different font families across projects
- Create asymmetric, dynamic layouts
- Use sharp edges, varied border radius, or no borders

### Generic Patterns to Challenge

- Standard Bootstrap/Material Design without customization
- Predictable component arrangements
- Same font choices (Space Grotesk is overused now!)
- Timid color choices that play it safe
- Lack of context-specific character

---

## Implementation Workflow

1. **Analyze context**: What emotion/atmosphere should this convey?
2. **Choose distinctive fonts**: Pick 1-2 from the recommendations, avoiding your recent choices
3. **Define color palette**: Commit to a cohesive theme with CSS variables
4. **Add atmosphere**: Layer backgrounds, gradients, or patterns
5. **Plan motion**: Identify 2-3 high-impact animation moments
6. **Review for uniqueness**: Does this feel generic or distinctive?

---

# Color Palettes

Ready-to-use color schemes for various aesthetics.

## Cyberpunk (SalesTaskMaster Primary)

High-contrast neon aesthetic with electric accents.

```css
:root {
  --bg: #0a0e27;
  --surface: #151932;
  --primary: #00d9ff;
  --accent: #ff006e;
  --highlight: #ffbe0b;
  --text: #f0f3f5;
  --text-secondary: #a8b5c6;
  --text-tertiary: #6b7684;
  --border: rgba(0, 217, 255, 0.2);
  --border-strong: rgba(0, 217, 255, 0.4);
}
```

**Best for:** Tech dashboards, gaming interfaces, futuristic themes

### Implementation for SalesTaskMaster

All components use CSS variables from `:root` declaration. This ensures:
- Consistency across entire app
- Easy maintenance (single source of truth)
- Semantic naming (--primary, --accent, --highlight)
- Alpha variants for transparency effects

---

## Dark Academia

Sophisticated, scholarly aesthetic with rich browns and deep greens.

```css
:root {
  --bg: #1a1410;
  --surface: #2d2419;
  --primary: #8b7355;
  --accent: #d4af37;
  --text: #e8dcc4;
  --text-secondary: #a89878;
}
```

**Best for:** Educational content, literary projects, archival interfaces

---

## Nord-Inspired

Cool, muted palette with excellent readability.

```css
:root {
  --bg: #2e3440;
  --surface: #3b4252;
  --primary: #88c0d0;
  --accent: #81a1c1;
  --highlight: #ebcb8b;
  --text: #eceff4;
  --text-secondary: #d8dee9;
}
```

**Best for:** Developer tools, technical documentation, clean interfaces

---

## Dracula-Inspired

Purple-forward with vibrant accents.

```css
:root {
  --bg: #282a36;
  --surface: #44475a;
  --primary: #bd93f9;
  --accent: #ff79c6;
  --green: #50fa7b;
  --yellow: #f1fa8c;
  --text: #f8f8f2;
}
```

**Best for:** Creative tools, entertainment apps, developer interfaces

---

## Forest Earth

Warm, organic palette with natural depth.

```css
:root {
  --bg: #1a2015;
  --surface: #2a3325;
  --primary: #4a7c59;
  --accent: #d4a373;
  --highlight: #f4e8c1;
  --text: #e8f0e0;
}
```

**Best for:** Environmental content, wellness apps, nature themes

---

## Retro Terminal

Classic green-on-black with modern refinements.

```css
:root {
  --bg: #0c1015;
  --surface: #1a1f26;
  --primary: #33ff33;
  --accent: #00ffaa;
  --text: #c5f5c5;
  --text-dim: #668866;
}
```

**Best for:** Developer tools, hacker aesthetic, retro computing

---

## Sunset Gradient

Warm, inviting palette with golden hour vibes.

```css
:root {
  --bg: #1a1315;
  --surface: #2d1f24;
  --primary: #ff6b35;
  --accent: #f7931e;
  --highlight: #fdc500;
  --text: #fff5e6;
}
```

**Best for:** Creative portfolios, photography sites, warm interfaces

---

## Monochrome Modern

High-contrast black and white with strategic accent.

```css
:root {
  --bg: #000000;
  --surface: #121212;
  --primary: #ffffff;
  --accent: #00ff41;
  --text: #ffffff;
  --text-secondary: #888888;
}
```

**Best for:** Minimalist designs, art portfolios, bold statements

---

## Ocean Deep

Deep blues with aquatic accents.

```css
:root {
  --bg: #0a1628;
  --surface: #132f4c;
  --primary: #1e88e5;
  --accent: #26c6da;
  --highlight: #ffa726;
  --text: #e3f2fd;
}
```

**Best for:** Maritime content, calm interfaces, professional tools

---

## Vaporwave

Nostalgic 80s/90s aesthetic with pastel neons.

```css
:root {
  --bg: #1a0b2e;
  --surface: #301551;
  --primary: #ff6ec7;
  --accent: #00d4ff;
  --highlight: #fff952;
  --text: #f0e6ff;
}
```

**Best for:** Creative projects, retro aesthetics, artistic interfaces

---

## Gradient Combinations

### Mesh Gradients (CSS)

```css
background:
  radial-gradient(at 0% 0%, var(--primary) 0%, transparent 50%),
  radial-gradient(at 100% 100%, var(--accent) 0%, transparent 50%),
  var(--bg);
```

### Animated Gradients

```css
@keyframes gradient-shift {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}

.animated-bg {
  background: linear-gradient(
    270deg,
    var(--primary),
    var(--accent),
    var(--primary)
  );
  background-size: 200% 200%;
  animation: gradient-shift 15s ease infinite;
}
```

### Color Palette Implementation Tips

1. **Consistency**: Define variables globally and use throughout
2. **Semantic naming**: Consider `--bg-primary`, `--bg-secondary` for multiple background levels
3. **Alpha variants**: Add `--primary-alpha: rgba(...)` for transparent versions
4. **Light mode**: Define alternative values in `@media (prefers-color-scheme: light)`
5. **Testing**: Always verify text contrast ratios (WCAG AA minimum: 4.5:1)

---

# Animation Recipes

Ready-to-use animation code for creating delightful micro-interactions and page transitions.

## Page Load Animations

### Staggered Fade In

```css
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-item {
  animation: fadeInUp 0.8s ease-out both;
}

.animate-item:nth-child(1) { animation-delay: 0s; }
.animate-item:nth-child(2) { animation-delay: 0.1s; }
.animate-item:nth-child(3) { animation-delay: 0.2s; }
.animate-item:nth-child(4) { animation-delay: 0.3s; }
```

### Slide In From Sides

```css
@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideInRight {
  from {
    opacity: 0;
    transform: translateX(50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.slide-left {
  animation: slideInLeft 0.6s ease-out;
}

.slide-right {
  animation: slideInRight 0.6s ease-out;
}
```

### Scale & Fade

```css
@keyframes scaleIn {
  from {
    opacity: 0;
    transform: scale(0.9);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

.scale-in {
  animation: scaleIn 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
}
```

---

## Hover Effects

### Lift & Shadow

```css
.lift-card {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.lift-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 24px rgba(0,0,0,0.15);
}
```

### Glow Effect

```css
.glow-button {
  transition: box-shadow 0.3s ease, transform 0.2s ease;
}

.glow-button:hover {
  box-shadow:
    0 0 20px rgba(var(--accent-rgb), 0.4),
    0 0 40px rgba(var(--accent-rgb), 0.2);
  transform: scale(1.05);
}
```

### Border Draw

```css
.border-draw {
  position: relative;
  background: transparent;
}

.border-draw::before {
  content: '';
  position: absolute;
  inset: 0;
  border: 2px solid var(--accent);
  border-radius: inherit;
  transition: clip-path 0.4s ease;
  clip-path: polygon(
    0 0, 0 0,
    0 100%, 0 100%
  );
}

.border-draw:hover::before {
  clip-path: polygon(
    0 0, 100% 0,
    100% 100%, 0 100%
  );
}
```

### Shimmer Effect

```css
@keyframes shimmer {
  0% {
    background-position: -200% 0;
  }
  100% {
    background-position: 200% 0;
  }
}

.shimmer {
  background: linear-gradient(
    90deg,
    transparent 0%,
    rgba(255,255,255,0.3) 50%,
    transparent 100%
  );
  background-size: 200% 100%;
  animation: shimmer 2s infinite;
}
```

---

## Loading Animations

### Skeleton Loader

```css
@keyframes skeleton-loading {
  0% {
    background-position: -200% 0;
  }
  100% {
    background-position: 200% 0;
  }
}

.skeleton {
  background: linear-gradient(
    90deg,
    #e0e0e0 0%,
    #f0f0f0 50%,
    #e0e0e0 100%
  );
  background-size: 200% 100%;
  animation: skeleton-loading 1.5s infinite;
  border-radius: 4px;
}
```

### Pulse

```css
@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

.pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}
```

### Spinner

```css
@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

.spinner {
  border: 3px solid rgba(0,0,0,0.1);
  border-top-color: var(--accent);
  border-radius: 50%;
  width: 40px;
  height: 40px;
  animation: spin 0.8s linear infinite;
}
```

---

## Button Animations

### Click Ripple (CSS-only approximation)

```css
.ripple-button {
  position: relative;
  overflow: hidden;
}

.ripple-button::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  border-radius: 50%;
  background: rgba(255,255,255,0.5);
  transform: translate(-50%, -50%);
  transition: width 0.6s, height 0.6s;
}

.ripple-button:active::after {
  width: 300px;
  height: 300px;
  transition: width 0s, height 0s;
}
```

### Bounce

```css
@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.bounce-button:hover {
  animation: bounce 0.5s ease;
}
```

---

## Text Animations

### Typing Effect

```css
@keyframes typing {
  from {
    width: 0;
  }
  to {
    width: 100%;
  }
}

@keyframes blink {
  50% {
    border-color: transparent;
  }
}

.typewriter {
  overflow: hidden;
  border-right: 3px solid;
  white-space: nowrap;
  animation:
    typing 3.5s steps(40, end),
    blink 0.75s step-end infinite;
}
```

### Gradient Text Animation

```css
@keyframes gradient-text {
  0%, 100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}

.gradient-text {
  background: linear-gradient(
    90deg,
    #ff00ff,
    #00ffff,
    #ff00ff
  );
  background-size: 200% auto;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradient-text 3s ease infinite;
}
```

### Neon Flicker

```css
@keyframes neon-flicker {
  0%, 100% {
    text-shadow:
      0 0 10px var(--accent),
      0 0 20px var(--accent),
      0 0 30px var(--accent);
  }
  5%, 95% {
    text-shadow: none;
  }
}

.neon-text {
  animation: neon-flicker 3s infinite;
}
```

---

## Scroll Animations (Intersection Observer)

### JavaScript Setup

```javascript
const observerOptions = {
  threshold: 0.1,
  rootMargin: '0px 0px -100px 0px'
};

const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('animate');
    }
  });
}, observerOptions);

document.querySelectorAll('.scroll-animate').forEach(el => {
  observer.observe(el);
});
```

### CSS Classes

```css
.scroll-animate {
  opacity: 0;
  transform: translateY(50px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}

.scroll-animate.animate {
  opacity: 1;
  transform: translateY(0);
}
```

---

## Parallax Effects

### CSS-only Parallax

```css
.parallax-container {
  height: 100vh;
  overflow-x: hidden;
  overflow-y: auto;
  perspective: 1px;
}

.parallax-layer-back {
  transform: translateZ(-1px) scale(2);
}

.parallax-layer-base {
  transform: translateZ(0);
}

.parallax-layer-front {
  transform: translateZ(1px);
}
```

---

## React (Framer Motion) Examples

### Page Transitions

```jsx
import { motion } from "framer-motion";

const pageVariants = {
  initial: {
    opacity: 0,
    y: 20
  },
  animate: {
    opacity: 1,
    y: 0,
    transition: {
      duration: 0.5,
      staggerChildren: 0.1
    }
  },
  exit: {
    opacity: 0,
    y: -20,
    transition: {
      duration: 0.3
    }
  }
};

function Page() {
  return (
    <motion.div
      variants={pageVariants}
      initial="initial"
      animate="animate"
      exit="exit"
    >
      {/* Content */}
    </motion.div>
  );
}
```

### List Stagger

```jsx
const container = {
  hidden: { opacity: 0 },
  show: {
    opacity: 1,
    transition: {
      staggerChildren: 0.1
    }
  }
};

const item = {
  hidden: { opacity: 0, y: 20 },
  show: { opacity: 1, y: 0 }
};

function List() {
  return (
    <motion.ul
      variants={container}
      initial="hidden"
      animate="show"
    >
      {items.map(i => (
        <motion.li key={i} variants={item}>
          {i}
        </motion.li>
      ))}
    </motion.ul>
  );
}
```

### Hover Scale & Rotate

```jsx
<motion.div
  whileHover={{
    scale: 1.05,
    rotate: 2,
    transition: { duration: 0.2 }
  }}
  whileTap={{ scale: 0.95 }}
>
  Card Content
</motion.div>
```

### Drag Gesture

```jsx
<motion.div
  drag
  dragConstraints={{ left: 0, right: 300, top: 0, bottom: 300 }}
  dragElastic={0.2}
  whileDrag={{ scale: 1.1 }}
>
  Draggable Element
</motion.div>
```

---

## Performance Tips

1. **Use `transform` and `opacity`**: These properties are GPU-accelerated
2. **Avoid animating `width`, `height`, `top`, `left`**: Use `transform` instead
3. **Use `will-change` sparingly**: Only for frequently animated elements
   ```css
   .frequently-animated {
     will-change: transform, opacity;
   }
   ```
4. **Reduce motion for accessibility**:
   ```css
   @media (prefers-reduced-motion: reduce) {
     * {
       animation-duration: 0.01ms !important;
       transition-duration: 0.01ms !important;
     }
   }
   ```

---

## Easing Functions

Common easing functions for natural motion:

```css
/* Bounce out */
cubic-bezier(0.34, 1.56, 0.64, 1)

/* Ease out back */
cubic-bezier(0.34, 1.45, 0.64, 1)

/* Smooth */
cubic-bezier(0.4, 0, 0.2, 1)

/* Fast start, slow end */
cubic-bezier(0.4, 0, 1, 1)

/* Slow start, fast end */
cubic-bezier(0, 0, 0.2, 1)
```

---

## Complete Example: Hero Animation Sequence

```html
<div class="hero">
  <h1 class="hero-title">Welcome</h1>
  <p class="hero-subtitle">To something amazing</p>
  <button class="hero-cta">Get Started</button>
</div>
```

```css
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.hero {
  opacity: 0;
  animation: fadeInUp 0.8s ease-out 0.2s forwards;
}

.hero-title {
  opacity: 0;
  animation: fadeInUp 0.8s ease-out 0.4s forwards;
}

.hero-subtitle {
  opacity: 0;
  animation: fadeInUp 0.8s ease-out 0.6s forwards;
}

.hero-cta {
  opacity: 0;
  animation: fadeInUp 0.8s ease-out 0.8s forwards;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.hero-cta:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(0,0,0,0.2);
}
```

---

# RPG/Fantasy Patterns

Complete patterns for creating immersive fantasy and RPG-themed interfaces.

## Core Aesthetic Principles

1. **Ornate over minimal**: Fantasy embraces decoration
2. **Texture is essential**: Aged, weathered materials convey history
3. **Rich color depth**: Jewel tones, metallics, dramatic lighting
4. **Medieval typography**: Serif fonts with embellished headers
5. **Dramatic shadows**: Deep contrast creates atmosphere

---

## Typography for Fantasy

### Primary Fonts

**Display/Headers:**
- Cinzel (elegant, imperial)
- IM Fell English (medieval, authentic)
- UnifrakturMaguntia (blackletter, dramatic)
- MedievalSharp (decorative, ornate)
- Spectral (refined, literary)

**Body Text:**
- Crimson Pro (readable, classic)
- Lora (elegant, readable)
- Spectral (literary feel)
- Bitter (strong, clear)

### Implementation Example

```css
@import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700;900&family=Crimson+Pro:wght@300;400;600&display=swap');

h1, h2, h3 {
  font-family: 'Cinzel', serif;
  font-weight: 700;
  letter-spacing: 0.05em;
  text-shadow: 2px 2px 4px rgba(0,0,0,0.8);
}

body {
  font-family: 'Crimson Pro', serif;
  font-size: 18px;
  line-height: 1.8;
}
```

---

## RPG Color Palettes

### Classic Fantasy

```css
:root {
  --parchment: #f4e8d0;
  --parchment-dark: #d4c4a8;
  --leather: #5c4033;
  --leather-dark: #3d2817;
  --gold: #d4af37;
  --gold-dark: #b8941f;
  --burgundy: #800020;
  --forest: #2d5016;
  --text-light: #3d2817;
  --text-dark: #f4e8d0;
}
```

### Dark Dungeon

```css
:root {
  --bg: #0a0805;
  --stone: #2a2520;
  --stone-light: #3d3830;
  --torch-glow: #ff8c42;
  --ember: #d64933;
  --teal-magic: #1ba098;
  --gold: #ffd700;
  --text: #e8dcc4;
}
```

### Royal Court

```css
:root {
  --deep-purple: #2d1b3d;
  --royal-blue: #1e3a8a;
  --crimson: #9f1239;
  --gold: #fbbf24;
  --silver: #cbd5e1;
  --ivory: #fef3c7;
  --text: #fef3c7;
}
```

---

## RPG Component Patterns

### Parchment Card

```html
<div class="parchment-card">
  <div class="parchment-content">
    <h2>Quest Title</h2>
    <p>Quest description...</p>
  </div>
</div>
```

```css
.parchment-card {
  background: linear-gradient(to bottom, #f4e8d0 0%, #d4c4a8 100%);
  border: 2px solid #8b7355;
  border-radius: 4px;
  box-shadow:
    inset 0 1px 0 rgba(255,255,255,0.3),
    0 5px 15px rgba(0,0,0,0.3);
  padding: 2rem;
  position: relative;

  /* Aged texture */
  background-image:
    url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200"><filter id="noise"><feTurbulence type="fractalNoise" baseFrequency="0.9" numOctaves="4" /></filter><rect width="100%" height="100%" filter="url(%23noise)" opacity="0.05"/></svg>');
}
```

### Ornate Border Frame

```css
.ornate-frame {
  position: relative;
  padding: 3rem;
  background: #1a0f08;
  border: 3px solid #d4af37;
}

.ornate-frame::before {
  content: '';
  position: absolute;
  width: 40px;
  height: 40px;
  border-top: 3px solid #d4af37;
  border-left: 3px solid #d4af37;
  top: -3px;
  left: -3px;
}

.ornate-frame::after {
  content: '';
  position: absolute;
  width: 40px;
  height: 40px;
  border-bottom: 3px solid #d4af37;
  border-right: 3px solid #d4af37;
  bottom: -3px;
  right: -3px;
}
```

### Leather-Bound Book Interface

```css
.book-interface {
  background:
    linear-gradient(to right, #3d2817 0%, #5c4033 50%, #3d2817 100%),
    repeating-linear-gradient(90deg,
      transparent 0px,
      rgba(0,0,0,0.1) 1px,
      transparent 2px,
      transparent 100px
    );
  border: 5px solid #2d1810;
  border-radius: 8px;
  box-shadow:
    inset 0 0 30px rgba(0,0,0,0.5),
    0 10px 30px rgba(0,0,0,0.7),
    0 0 0 1px rgba(212,175,55,0.3);
  padding: 3rem;
}
```

### Metallic Button (Gold/Bronze)

```css
.rpg-button {
  background: linear-gradient(to bottom, #d4af37 0%, #b8941f 100%);
  border: 2px solid #8b6914;
  border-radius: 6px;
  color: #2d1810;
  font-family: 'Cinzel', serif;
  font-weight: 700;
  padding: 0.75rem 2rem;
  text-shadow: 0 1px 0 rgba(255,255,255,0.3);
  box-shadow:
    inset 0 1px 0 rgba(255,255,255,0.4),
    inset 0 -1px 0 rgba(0,0,0,0.2),
    0 4px 8px rgba(0,0,0,0.3);
  transition: all 0.2s;
}

.rpg-button:hover {
  background: linear-gradient(to bottom, #e6c24d 0%, #d4af37 100%);
  box-shadow:
    inset 0 1px 0 rgba(255,255,255,0.4),
    inset 0 -1px 0 rgba(0,0,0,0.2),
    0 6px 12px rgba(0,0,0,0.4),
    0 0 20px rgba(212,175,55,0.4);
  transform: translateY(-2px);
}

.rpg-button:active {
  box-shadow:
    inset 0 2px 4px rgba(0,0,0,0.3),
    0 2px 4px rgba(0,0,0,0.2);
  transform: translateY(0);
}
```

### Glowing Rune/Magic Effect

```css
@keyframes rune-glow {
  0%, 100% {
    text-shadow: 0 0 10px #1ba098, 0 0 20px #1ba098;
    opacity: 0.8;
  }
  50% {
    text-shadow: 0 0 20px #1ba098, 0 0 40px #1ba098, 0 0 60px #1ba098;
    opacity: 1;
  }
}

.magic-text {
  color: #1ba098;
  font-family: 'UnifrakturMaguntia', cursive;
  animation: rune-glow 3s ease-in-out infinite;
}

.magic-border {
  border: 2px solid #1ba098;
  box-shadow:
    0 0 10px #1ba098,
    inset 0 0 10px rgba(27,160,152,0.3);
  animation: rune-glow 3s ease-in-out infinite;
}
```

### Torch-Lit Atmosphere

```css
@keyframes torch-flicker {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.85; }
}

.torch-glow {
  position: relative;
  background: radial-gradient(circle at 50% 0%,
    rgba(255,140,66,0.3) 0%,
    rgba(255,140,66,0.1) 30%,
    transparent 60%
  );
  animation: torch-flicker 4s ease-in-out infinite;
}

.dungeon-scene {
  background: #0a0805;
  position: relative;
}

.dungeon-scene::before {
  content: '';
  position: absolute;
  top: 0;
  left: 20%;
  width: 200px;
  height: 300px;
  background: radial-gradient(ellipse at 50% 0%,
    rgba(255,140,66,0.4) 0%,
    transparent 70%
  );
  animation: torch-flicker 3s ease-in-out infinite;
  pointer-events: none;
}
```

---

## Texture Patterns (Data URLs)

### Aged Paper Texture

```css
.aged-paper {
  background-color: #f4e8d0;
  background-image:
    url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200"><filter id="noise"><feTurbulence type="fractalNoise" baseFrequency="0.9" numOctaves="4" /></filter><rect width="100%" height="100%" filter="url(%23noise)" opacity="0.08"/></svg>');
}
```

### Stone Texture

```css
.stone-texture {
  background-color: #3d3830;
  background-image:
    url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200"><filter id="noise"><feTurbulence type="turbulence" baseFrequency="0.05" numOctaves="4" /></filter><rect width="100%" height="100%" filter="url(%23noise)" opacity="0.3"/></svg>');
}
```

---

## Complete Example: Character Sheet Card

```html
<div class="character-sheet">
  <div class="sheet-header">
    <h1>Eldric the Wise</h1>
    <span class="level-badge">Level 12 Wizard</span>
  </div>

  <div class="stats-grid">
    <div class="stat">
      <span class="stat-label">Strength</span>
      <span class="stat-value">8</span>
    </div>
    <div class="stat">
      <span class="stat-label">Intelligence</span>
      <span class="stat-value">18</span>
    </div>
  </div>

  <div class="abilities-section">
    <h2>Abilities</h2>
    <div class="ability-list">
      <!-- Abilities -->
    </div>
  </div>
</div>
```

```css
.character-sheet {
  background: linear-gradient(to bottom, #f4e8d0 0%, #d4c4a8 100%);
  border: 4px solid #8b7355;
  border-radius: 8px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.5);
  padding: 2rem;
  max-width: 600px;
  font-family: 'Crimson Pro', serif;
}

.sheet-header {
  border-bottom: 3px double #8b7355;
  padding-bottom: 1rem;
  margin-bottom: 2rem;
  text-align: center;
}

.sheet-header h1 {
  font-family: 'Cinzel', serif;
  font-size: 2.5rem;
  color: #2d1810;
  margin: 0;
  text-shadow: 2px 2px 0 rgba(255,255,255,0.5);
}

.level-badge {
  display: inline-block;
  background: linear-gradient(to bottom, #d4af37 0%, #b8941f 100%);
  border: 2px solid #8b6914;
  border-radius: 4px;
  padding: 0.5rem 1rem;
  font-family: 'Cinzel', serif;
  font-weight: 700;
  color: #2d1810;
  margin-top: 0.5rem;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  margin-bottom: 2rem;
}

.stat {
  background: rgba(61, 40, 23, 0.1);
  border: 2px solid #8b7355;
  border-radius: 4px;
  padding: 1rem;
  text-align: center;
}

.stat-label {
  display: block;
  font-size: 0.9rem;
  color: #5c4033;
  margin-bottom: 0.5rem;
}

.stat-value {
  display: block;
  font-family: 'Cinzel', serif;
  font-size: 2rem;
  font-weight: 700;
  color: #2d1810;
}
```

---

## RPG/Fantasy Implementation Checklist

✓ Choose medieval-inspired serif fonts (Cinzel, Crimson Pro)
✓ Use rich, deep color palette with jewel tones
✓ Add texture to backgrounds (aged paper, stone, leather)
✓ Implement ornate borders and decorative elements
✓ Include metallic accents (gold, bronze, silver)
✓ Add dramatic shadows for depth
✓ Consider torch-lit or magical glow effects
✓ Use appropriate animations (subtle, atmospheric)
✓ Test readability on textured backgrounds

---

## RPG/Fantasy Animation Examples

### Page Turn Effect

```css
@keyframes page-turn {
  0% {
    transform: perspective(1000px) rotateY(0deg);
    transform-origin: left;
  }
  100% {
    transform: perspective(1000px) rotateY(-180deg);
    transform-origin: left;
  }
}

.page-turn-animation {
  animation: page-turn 1s ease-in-out;
}
```

### Spell Cast Glow

```css
@keyframes spell-cast {
  0% {
    box-shadow: 0 0 5px #1ba098;
  }
  50% {
    box-shadow: 0 0 30px #1ba098, 0 0 60px #1ba098;
    transform: scale(1.05);
  }
  100% {
    box-shadow: 0 0 5px #1ba098;
  }
}
```

---

## Document Status

**Created**: Consolidation of SKILL.md, color-palettes.md, animation-recipes.md, rpg-patterns.md

**Purpose**: Single comprehensive reference for all design principles, color schemes, animation patterns, and RPG/fantasy design techniques

**Usage**: Reference this master guide for all design decisions. Components use CSS variables from the cyberpunk palette unless otherwise specified.

**Current Implementation**: SalesTaskMaster uses the Cyberpunk color palette with Space Grotesk, Unbounded, and JetBrains Mono typography.
