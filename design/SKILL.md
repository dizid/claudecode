---
name: design
description: Comprehensive frontend design and aesthetics guidance for creating beautiful, distinctive interfaces. Use when creating HTML, React, or any frontend artifacts where visual design, typography, color schemes, animations, or overall aesthetics matter. Helps avoid generic "AI slop" aesthetic by providing specific guidance on fonts, colors, themes, layouts, and RPG/fantasy styling when appropriate.
---

# Design Skill

Create distinctive, high-quality frontends that surprise and delight users. This skill helps you avoid generic aesthetics and make bold, creative design choices.

## Core Design Principles

### 1. Typography Excellence

Typography instantly signals quality. Every font choice shapes user perception.

**Never use these boring fonts:**
- Inter, Roboto, Open Sans, Lato, Arial
- System fonts without intentional styling
- Helvetica in generic implementations

**Choose distinctive fonts with character:**
- **Code/Technical aesthetic**: JetBrains Mono, Fira Code, Space Grotesk, IBM Plex Mono, Inconsolata
- **Editorial/Literary**: Playfair Display, Crimson Pro, Spectral, Newsreader, Lora
- **Technical/Modern**: IBM Plex family, Source Sans 3, Manrope, DM Sans
- **Distinctive/Unique**: Bricolage Grotesque, Newsreader, Unbounded, Syne, Cabinet Grotesk
- **Geometric/Clean**: Outfit, Plus Jakarta Sans, Lexend, Poppins (sparingly)
- **Display/Bold**: Bebas Neue, Oswald, Archivo Black, Righteous

**Pairing strategies for maximum impact:**
- High contrast = interesting (Display + Monospace, Serif + Geometric Sans)
- Variable fonts across weights (use extremes: 100/200 vs 800/900, not 400 vs 600)
- Size jumps of 3x+ for hierarchy, not 1.5x
- One distinctive hero font used decisively

**Implementation:**
Load fonts from Google Fonts or Bunny Fonts. Use `@import` in CSS or `<link>` in HTML head.

### 2. Color & Theme Mastery

Generic palettes kill uniqueness. Commit to cohesive, distinctive color schemes.

**Use CSS variables for consistency:**
```css
:root {
  --primary: #your-dominant-color;
  --accent: #sharp-contrast;
  --bg: #atmospheric-base;
  --text: #readable-contrast;
}
```

**Effective palette strategies:**
- **Dominant color approach**: One strong color + sharp accent (not evenly distributed pastels)
- **Cultural aesthetics**: Draw from cyberpunk, brutalism, vaporwave, dark academia, etc.
- **IDE-inspired**: Dracula, Nord, Monokai, Solarized themes adapted for UI
- **Natural depth**: Earth tones, deep teals, burnt oranges create warmth without cliché

**Avoid these overused combinations:**
- Purple gradients on white backgrounds
- Pastel rainbow distributions
- Generic blue (#007bff) + gray (#6c757d)
- Default Tailwind palette without customization

**See references/color-palettes.md for specific schemes**

### 3. Motion & Animation

Well-orchestrated motion creates delight. Focus on high-impact moments.

**CSS-only animations for HTML:**
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

**For React, use Framer Motion when available:**
```jsx
import { motion } from "framer-motion";

<motion.div
  initial={{ opacity: 0, y: 20 }}
  animate={{ opacity: 1, y: 0 }}
  transition={{ duration: 0.5 }}
>
```

**Focus areas:**
- Page load sequences with staggered reveals
- Hover microinteractions on key elements
- Smooth transitions between states
- Scroll-triggered animations for storytelling

**Avoid:**
- Scattered, purposeless animations
- Slow, heavy animations (>1s without reason)
- Animations on every element

### 4. Backgrounds & Atmosphere

Create depth and context instead of flat colors.

**Layered gradients:**
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
/* Or mesh gradients */
background: 
  radial-gradient(at 20% 30%, #667eea 0%, transparent 50%),
  radial-gradient(at 80% 70%, #764ba2 0%, transparent 50%),
  #1a1a2e;
```

**Geometric patterns:**
```css
background-image: 
  repeating-linear-gradient(45deg, transparent, transparent 10px, rgba(255,255,255,.03) 10px, rgba(255,255,255,.03) 20px);
```

**Contextual effects:**
- Subtle noise textures for grit
- SVG patterns for themed aesthetics
- Canvas effects for dynamic backgrounds

### 5. RPG/Fantasy Aesthetic (When Applicable)

When creating RPG-themed or fantasy interfaces, commit fully:

**Visual elements:**
- Ornate borders and decorative frames
- Parchment textures and leather-bound styling
- Weathered materials with aged effects
- Medieval-inspired serif typography (Cinzel, IM Fell, UnifrakturMaguntia)

**Color palettes:**
- Rich jewel tones: deep burgundy, emerald, sapphire, gold
- Dramatic contrasts with dark backgrounds
- Metallic accents (gold, bronze, silver via gradients)

**Implementation examples:**
```css
.rpg-card {
  background: linear-gradient(to bottom, #2c1810 0%, #1a0f08 100%);
  border: 3px solid #8b6914;
  box-shadow: 
    inset 0 0 20px rgba(0,0,0,0.5),
    0 5px 15px rgba(0,0,0,0.7);
  font-family: 'Cinzel', serif;
}
```

**See references/rpg-patterns.md for complete examples**

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

## Implementation Workflow

1. **Analyze context**: What emotion/atmosphere should this convey?
2. **Choose distinctive fonts**: Pick 1-2 from the recommendations, avoiding your recent choices
3. **Define color palette**: Commit to a cohesive theme with CSS variables
4. **Add atmosphere**: Layer backgrounds, gradients, or patterns
5. **Plan motion**: Identify 2-3 high-impact animation moments
6. **Review for uniqueness**: Does this feel generic or distinctive?

## Bundled Resources

- `references/color-palettes.md`: Specific color schemes for various aesthetics
- `references/rpg-patterns.md`: Complete RPG/fantasy design patterns
- `references/animation-recipes.md`: Ready-to-use animation code
- `assets/fonts.css`: Pre-configured Google Fonts imports
