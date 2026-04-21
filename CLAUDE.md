# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**TI3031 — Programación Front End** is a static interactive learning platform for a university frontend course taught at INACAP by Germán Mardones. It consists of pure HTML/CSS/JS pages with no build system — open any `.html` file directly in a browser. The site is deployed automatically to Vercel on push to `main`.

There are no build, lint, or test commands. Development is: edit files → open in browser → verify visually.

## Module Structure

```
index.html                     ← Main hub (all modules)
clase1/                        ← HTML semantics & structure
clase2/css/                    ← CSS labs (box model, flexbox, units, etc.)
clase3/
  git/                         ← Git & version control
  copilot/                     ← GitHub Copilot usage
  fundamentos-ia/              ← AI fundamentals (LLMs, tokens, agents, MCP)
  componentes-comunes/         ← Reusable UI component demos
clase4/
  variables/                   ← JS variables, types, scope
  estructuras/                 ← Control flow (if, for, while)
  funciones/                   ← Functions & arrow functions
  objetos-arreglos/            ← Arrays & objects
  dom/                         ← DOM manipulation
  ia-js/                       ← AI integration with JS
```

## Page Architecture

There are three distinct page types with different CSS approaches:

**Hub pages** (`index.html` at each level): vanilla CSS only, no Tailwind. Grid of cards with `fadeInUp` animation. Back-link points to `../index.html`.

**Sub-hub pages** (`clase3/git/index.html`, etc.): same as hub pages, with module-specific accent color.

**Content/lab pages** (all other `.html` files): Tailwind CSS via CDN + custom CSS for glass effects and theming. More complex interactive layouts.

## Design System

### CSS Variables (all pages)
```css
:root {
    --bg-color: #0f172a;
    --card-bg: rgba(30, 41, 59, 0.7);   /* glassmorphism */
    --text-main: #f8fafc;
    --text-dim: #94a3b8;
    --accent: /* varies by module */;
    --accent-glow: /* accent at 0.2 opacity */;
    --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}
[data-theme="light"] {
    --bg-color: #f8fafc;
    --card-bg: rgba(255, 255, 255, 0.85);
    --text-main: #0f172a;
    --text-dim: #475569;
    --accent: /* darker shade of module accent */;
}
```

### Accent Colors by Module
| Module | Color |
|---|---|
| Clase 1 & 2 | `#38bdf8` sky blue |
| Clase 3 hub | `#a78bfa` violet |
| Git (3.1) | `#f97316` orange |
| Copilot (3.2) | `#818cf8` indigo |
| Fundamentos IA (3.3) | `#2dd4bf` teal |
| Clase 4 | `#38bdf8` sky blue |

### Fonts (Google Fonts, loaded on every page)
- **Headings (h1–h3):** Outfit
- **Body & UI:** Inter
- **Code blocks & terminals:** JetBrains Mono

### Glass Panel Pattern (lab pages)
```css
.glass-panel {
    background: var(--card-bg);
    backdrop-filter: blur(12px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 1.5rem;
}
```

## Conventions

### Theme Toggle (every page, identical pattern)
```javascript
const themeBtn = document.getElementById('themeToggle');
const html = document.documentElement;
if (localStorage.getItem('theme') === 'light') {
    html.setAttribute('data-theme', 'light');
    themeBtn.innerHTML = '🌙 Modo Oscuro';
}
themeBtn.addEventListener('click', () => {
    const isLight = html.getAttribute('data-theme') === 'light';
    localStorage.setItem('theme', isLight ? 'dark' : 'light');
    if (isLight) { html.removeAttribute('data-theme'); themeBtn.innerHTML = '☀️ Modo Claro'; }
    else { html.setAttribute('data-theme', 'light'); themeBtn.innerHTML = '🌙 Modo Oscuro'; }
});
```

### File Naming
- Descriptive kebab-case, no module prefix (the folder provides context)
- `clase3/git/que-es.html` ✓ — not `clase3/git/git-que-es.html` ✗

### Navigation Back-links
- Lab page → `index.html` (sub-hub)
- Sub-hub → `../index.html` (module hub)
- Module hub → `../index.html` (main hub)

### Tailwind vs Vanilla CSS Rule
- Hub/index pages: vanilla CSS only
- Content/lab pages: Tailwind CDN + custom CSS for effects not expressible in Tailwind (glassmorphism, CSS variables, animations, tooltips)

### Tooltips (lab pages)
Technical terms use a `.tecnicismo` pattern: `border-bottom: 2px dashed var(--accent)` with `data-tooltip="..."` and an `::after` pseudo-element that shows on hover.
