# Color Palettes Reference

Ready-to-use color schemes for various aesthetics. Copy CSS variables directly into your projects.

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

## Cyberpunk

High-contrast neon aesthetic with electric accents.

```css
:root {
  --bg: #0a0e27;
  --surface: #151932;
  --primary: #00d9ff;
  --accent: #ff006e;
  --highlight: #ffbe0b;
  --text: #f0f3f5;
}
```

**Best for:** Tech dashboards, gaming interfaces, futuristic themes

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

## Implementation Tips

1. **Consistency**: Define variables globally and use throughout
2. **Semantic naming**: Consider `--bg-primary`, `--bg-secondary` for multiple background levels
3. **Alpha variants**: Add `--primary-alpha: rgba(...)` for transparent versions
4. **Light mode**: Define alternative values in `@media (prefers-color-scheme: light)`
5. **Testing**: Always verify text contrast ratios (WCAG AA minimum: 4.5:1)

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
