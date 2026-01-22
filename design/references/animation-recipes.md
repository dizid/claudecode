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
/* Continue pattern or use calc for dynamic delays */
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
