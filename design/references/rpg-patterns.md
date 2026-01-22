# RPG/Fantasy Design Patterns

Complete patterns for creating immersive fantasy and RPG-themed interfaces.

## Core Aesthetic Principles

1. **Ornate over minimal**: Fantasy embraces decoration
2. **Texture is essential**: Aged, weathered materials convey history
3. **Rich color depth**: Jewel tones, metallics, dramatic lighting
4. **Medieval typography**: Serif fonts with embellished headers
5. **Dramatic shadows**: Deep contrast creates atmosphere

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

## Color Palettes

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

## Component Patterns

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

.parchment-card::before {
  content: '';
  position: absolute;
  top: -5px;
  left: -5px;
  right: -5px;
  bottom: -5px;
  background: linear-gradient(45deg, transparent 48%, #8b7355 48%, #8b7355 52%, transparent 52%);
  background-size: 10px 10px;
  pointer-events: none;
  opacity: 0.3;
}
```

### Ornate Border Frame

```css
.ornate-frame {
  position: relative;
  padding: 3rem;
  background: #1a0f08;
  border: 3px solid #d4af37;
  
  /* Corner decorations */
  &::before,
  &::after {
    content: '✦';
    position: absolute;
    font-size: 2rem;
    color: #d4af37;
    text-shadow: 0 0 10px #d4af37;
  }
  
  &::before {
    top: -1rem;
    left: -1rem;
  }
  
  &::after {
    bottom: -1rem;
    right: -1rem;
  }
}

/* Decorative corners with pseudo-elements */
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
  
  /* Embossed effect */
  position: relative;
}

.book-interface::before {
  content: '';
  position: absolute;
  top: 10px;
  left: 10px;
  right: 10px;
  bottom: 10px;
  border: 1px solid rgba(212,175,55,0.3);
  pointer-events: none;
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
    <!-- More stats -->
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

## Animation Examples

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

## Implementation Checklist

✓ Choose medieval-inspired serif fonts (Cinzel, Crimson Pro)
✓ Use rich, deep color palette with jewel tones
✓ Add texture to backgrounds (aged paper, stone, leather)
✓ Implement ornate borders and decorative elements
✓ Include metallic accents (gold, bronze, silver)
✓ Add dramatic shadows for depth
✓ Consider torch-lit or magical glow effects
✓ Use appropriate animations (subtle, atmospheric)
✓ Test readability on textured backgrounds
