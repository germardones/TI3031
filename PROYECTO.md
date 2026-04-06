# Programación Front End — TI3031
## Documento de Contexto del Proyecto

---

## 📋 Descripción General

**TI3031 — Programación Front End** es una plataforma de aprendizaje web desarrollada por **Germán Mardones**, docente de INACAP. El proyecto proporciona material educativo interactivo para la asignatura de desarrollo web frontend, organizado en módulos progresivos que van desde fundamentos HTML hasta herramientas profesionales de desarrollo.

---

## 🎯 Objetivo

Ofrecer a los estudiantes acceso a clases, laboratorios interactivos y recursos técnicos que complementen el aprendizaje presencial, permitiéndoles explorar conceptos a su propio ritmo con elementos visuales y prácticos.

---

## 🏗️ Arquitectura de Navegación

```
index.html                          ← Hub principal del curso
│
├── clase1.html                     ← Módulo 1: Estructura y Semántica HTML
│   ├── esqueleto-web.html          ← El Esqueleto Web (explorador interactivo)
│   ├── anatomia-html.html          ← Anatomía Semántica (rayos X visual)
│   └── atributos-html.html         ← Parámetros y Atributos
│
├── clase2.html                     ← Módulo 2: Estructura y Diseño CSS
│   ├── aplicando-css.html          ← Fundamentos y Cascada
│   ├── clase2-1.html               ← Especificidad CSS
│   ├── modelo-de-caja.html         ← El Modelo de Caja
│   ├── unidades-de-medida.html     ← Unidades de Medida
│   └── flexbox-playground.html     ← Flexbox Avanzado
│
└── clase3.html                     ← Módulo 3: Flujos de Trabajo e IA
    ├── git-control-versiones.html  ← Clase 3.1: Hub de Git
    │   ├── git-que-es.html         ← ¿Qué es Git?
    │   ├── git-flujo-trabajo.html  ← Flujo de Trabajo
    │   ├── git-comandos.html       ← Comandos Esenciales (terminal)
    │   ├── git-ramas.html          ← Ramas y Branching
    │   └── git-commits.html        ← Conventional Commits
    │
    └── github-copilot-ia.html      ← Clase 3.2: Hub de Copilot / IA
        ├── copilot-que-es.html     ← ¿Qué es GitHub Copilot?
        ├── copilot-autocompletado.html ← Autocompletado en Acción
        ├── copilot-chat.html       ← Chat con Copilot
        ├── copilot-prompts.html    ← Prompt Engineering
        └── copilot-atajos.html     ← Atajos de Teclado

Recursos técnicos (acceso desde index.html):
├── diccionario.html                ← Glosario Semántico HTML (100 etiquetas)
├── diccionario-atributos.html      ← Referencia de Atributos
└── diccionario-css.html            ← Referencia Técnica CSS
```

---

## 🎨 Sistema de Diseño

### Tipografía
- **Títulos (h1, h2, h3):** Outfit (Google Fonts)
- **Cuerpo y UI:** Inter (Google Fonts)
- **Código y terminales:** JetBrains Mono (Google Fonts)

### Paleta de Colores por Módulo

| Elemento | Color | Uso |
|---|---|---|
| Background oscuro | `#0f172a` | Base body dark mode |
| Card background | `#1e293b` | Tarjetas en dark mode |
| Background claro | `#f1f5f9` | Base body light mode |
| Módulo 1 | `#38bdf8` (sky) | HTML / Semántica |
| Módulo 2 | `#38bdf8` (sky) | CSS / Diseño |
| Módulo 3 principal | `#a78bfa` (violet) | Hub Módulo 3 |
| Clase 3.1 (Git) | `#f97316` (orange) | Git / Control de versiones |
| Clase 3.2 (Copilot) | `#818cf8` (indigo) | IA / GitHub Copilot |
| Texto principal | `#f8fafc` | Headings, cuerpo |
| Texto secundario | `#94a3b8` | Descripciones, meta |

### Variables CSS Estándar
```css
:root {
    --bg-color: #0f172a;
    --card-bg: #1e293b;
    --text-main: #f8fafc;
    --text-dim: #94a3b8;
    --accent: /* varía por módulo */;
    --accent-glow: /* rgba del accent con 0.2 de opacidad */;
    --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}
```

---

## 📁 Tipos de Páginas

### 1. Hub Principal (`index.html`)
- Presenta todos los módulos disponibles como tarjetas (`class-card`)
- Sidebar con recursos técnicos (`resource-card`)
- Layout: `grid-template-columns: 1fr 300px`

### 2. Hub de Módulo (`clase1.html`, `clase2.html`, `clase3.html`)
- Diseño de tarjetas (`content-card`) con animación `fadeInUp`
- Back-link al hub principal
- `content-grid`: `repeat(auto-fill, minmax(350px, 1fr))`
- Cada tarjeta: card-tag (Paso XX), h2, p descriptivo, card-action

### 3. Sub-Hub de Tema (`git-control-versiones.html`, `github-copilot-ia.html`)
- Mismo diseño que Hub de Módulo
- Back-link al módulo padre (clase3.html)
- Color accent heredado del tema del módulo

### 4. Páginas de Contenido (laboratorios interactivos)
- Combinan Tailwind CSS + CSS variables custom para efectos vidrio
- Clase `.glass-panel`: glassmorphism con `backdrop-filter: blur(12px)`
- Back-link al sub-hub correspondiente
- Presentan contenido con interactividad JS nativa

---

## 🔧 Tecnologías

| Tecnología | Uso |
|---|---|
| HTML5 semántico | Estructura de todas las páginas |
| CSS3 custom properties | Sistema de diseño y theming |
| Tailwind CSS (CDN) | Utilidades de layout en labs interactivos |
| JavaScript vanilla | Interactividad, theme toggle, animaciones |
| Google Fonts | Tipografía (Inter, Outfit, JetBrains Mono) |
| Google Analytics (gtag) | Tracking en index.html |

> **Nota importante:** El proyecto usa **Tailwind CSS vía CDN** (`<script src="https://cdn.tailwindcss.com">`) únicamente en las páginas de laboratorio interactivo (`esqueleto-web.html`, `aplicando-css.html`, y todas las sub-páginas del Módulo 3). Las páginas hub (`clase1.html`, `clase2.html`, `clase3.html` y sus sub-hubs) usan **solo CSS vanilla** para mantener el diseño unificado.

---

## ✨ Patrones de Interactividad

### Theme Toggle (todas las páginas)
```javascript
// Persistencia en localStorage: 'dark' | 'light'
// data-theme="light" en <html> para modo claro
// Sin data-theme = modo oscuro (default)
```

### Animación de entrada
```css
@keyframes fadeInUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
}
```
Aplicada a `.container` con `animation: fadeInUp 0.8s cubic-bezier(0.4, 0, 0.2, 1) forwards`

### Glass Panel
```css
.glass-panel {
    background: var(--card-bg);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 1.5rem;
}
```

---

## 📐 Convenciones de Nomenclatura

### Archivos HTML
- `clase{N}.html` → Hub del módulo N
- `{tema}-{subtema}.html` → Páginas de contenido específico
  - `git-que-es.html`, `git-flujo-trabajo.html`
  - `copilot-que-es.html`, `copilot-autocompletado.html`

### Flujo de Navegación (back-links)
- Contenido → Sub-Hub → Hub de Módulo → index.html
- Cada página incluye un `back-link` que apunta únicamente a su padre inmediato

---

## 🗂️ Repositorio y Despliegue

- **Control de versiones:** Git + GitHub  
- **URL del repositorio:** `github.com/germardones/TI3031` (pend. confirmar)
- **Despliegue:** Vercel (historial en conversación `7b035669`)

---

## 👤 Autor

**Germán Mardones**  
Docente INACAP  
[linkedin.com/in/mardonesgerman](https://www.linkedin.com/in/mardonesgerman/)  
Email: german.mardones@inacapmail.cl

---

*Última actualización: Abril 2026*
