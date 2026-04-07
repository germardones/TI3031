# Programación Front End — TI3031
## Documento de Contexto del Proyecto

---

## Descripción General

**TI3031 — Programación Front End** es una plataforma de aprendizaje web desarrollada por **Germán Mardones**, docente de INACAP. El proyecto proporciona material educativo interactivo para la asignatura de desarrollo web frontend, organizado en módulos progresivos que van desde fundamentos HTML hasta herramientas de IA y control de versiones.

---

## Objetivo

Ofrecer a los estudiantes acceso a clases, laboratorios interactivos y recursos técnicos que complementen el aprendizaje presencial, permitiéndoles explorar conceptos a su propio ritmo con elementos visuales y prácticos.

---

## Estructura de Carpetas (estado actual)

```
TI3031/
├── index.html                              ← Hub principal del curso
├── PROYECTO.md                             ← Este documento
├── README.md
│
├── clase1/                                 ← Módulo 1: Estructura y Semántica HTML
│   ├── index.html                          ← Hub del módulo
│   ├── esqueleto-web.html                  ← El Esqueleto Web (explorador interactivo)
│   ├── anatomia-html.html                  ← Anatomía Semántica (rayos X visual)
│   ├── atributos-html.html                 ← Parámetros y Atributos
│   └── diccionario.html                    ← Glosario Semántico (100 etiquetas)
│
├── clase2/                                 ← Módulo 2: Estructura y Diseño CSS
│   ├── index.html                          ← Hub del módulo
│   ├── clase2-1.html                       ← Especificidad CSS
│   └── css/                               ← Sub-carpeta: laboratorios CSS
│       ├── aplicando-css.html              ← Fundamentos y Cascada
│       ├── modelo-de-caja.html             ← El Modelo de Caja
│       ├── unidades-de-medida.html         ← Unidades de Medida
│       ├── flexbox-playground.html         ← Flexbox Avanzado
│       ├── diccionario-css.html            ← Referencia Técnica CSS
│       └── diccionario-atributos.html      ← Referencia de Atributos
│
└── clase3/                                 ← Módulo 3: Flujos de Trabajo e IA
    ├── index.html                          ← Hub Módulo 3
    │
    ├── git/                               ← Clase 3.1: Control de Versiones Git
    │   ├── index.html                      ← Hub Git
    │   ├── que-es.html                     ← ¿Qué es Git? (problemas y soluciones)
    │   ├── flujo-trabajo.html              ← Flujo de Trabajo (zonas interactivas)
    │   ├── comandos.html                   ← Comandos Esenciales (terminal simulada)
    │   ├── ramas.html                      ← Ramas y Branching (historial visual)
    │   └── commits.html                    ← Conventional Commits (constructor)
    │
    ├── copilot/                           ← Clase 3.2: GitHub Copilot / IA
    │   ├── index.html                      ← Hub Copilot
    │   ├── que-es.html                     ← ¿Qué es GitHub Copilot?
    │   ├── autocompletado.html             ← Autocompletado en Acción (demo)
    │   ├── chat.html                       ← Chat con Copilot (simulador)
    │   ├── prompts.html                    ← Prompt Engineering (comparador)
    │   └── atajos.html                     ← Atajos de Teclado (tracker de progreso)
    │
    └── fundamentos-ia/                    ← Clase 3.3: Fundamentos de IA
        ├── index.html                      ← Hub Fundamentos IA
        ├── como-funciona.html              ← Cómo funciona la IA (pasos + capas)
        ├── llm.html                        ← ¿Qué es un LLM? (tokenizador live)
        ├── tokens.html                     ← Tokens y Modelos (tabla comparativa)
        ├── parametros.html                 ← Parámetros del modelo (sliders)
        ├── contexto.html                   ← Contexto y Prompts (constructor)
        ├── alucinaciones.html              ← Alucinaciones (ejemplos interactivos)
        ├── agentes.html                    ← Agentes de IA (ciclo ReAct)
        ├── mcp.html                        ← MCP: Model Context Protocol
        └── orquestadores.html              ← Orquestadores (Claude Code, Cursor...)
```

---

## Sistema de Diseño

### Tipografía
- **Títulos (h1, h2, h3):** Outfit (Google Fonts)
- **Cuerpo y UI:** Inter (Google Fonts)
- **Código y terminales:** JetBrains Mono (Google Fonts)

### Paleta de Colores por Módulo

| Elemento | Color | Uso |
|---|---|---|
| Background oscuro | `#0f172a` | Base body dark mode |
| Card background | `rgba(30,41,59,0.7)` | Glassmorphism dark |
| Background claro | `#f8fafc` | Base body light mode |
| Módulo 1 | `#38bdf8` (sky) | HTML / Semántica |
| Módulo 2 | `#38bdf8` (sky) | CSS / Diseño |
| Módulo 3 principal | `#a78bfa` (violet) | Hub Módulo 3 |
| Clase 3.1 (Git) | `#f97316` (orange) | Git / Control de versiones |
| Clase 3.2 (Copilot) | `#818cf8` (indigo) | IA / GitHub Copilot |
| Clase 3.3 (Fund. IA) | `#2dd4bf` (teal) | Fundamentos de IA |
| Texto principal | `#f8fafc` | Headings, cuerpo |
| Texto secundario | `#94a3b8` | Descripciones, meta |

### Variables CSS Estándar

```css
:root {
    --bg-color: #0f172a;
    --card-bg: rgba(30,41,59,0.7);  /* glassmorphism en labs */
    --text-main: #f8fafc;
    --text-dim: #94a3b8;
    --accent: /* varía por módulo */;
    --accent-glow: /* rgba del accent con 0.2 de opacidad */;
    --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}
[data-theme="light"] {
    --bg-color: #f8fafc;
    --card-bg: rgba(255,255,255,0.85);
    --text-main: #0f172a;
    --accent: /* versión oscura del accent */;
}
```

---

## Tipos de Páginas

### 1. Hub Principal (`index.html`)
- Presenta todos los módulos como tarjetas (`class-card`)
- Sidebar con recursos técnicos (`resource-card`)
- Layout: `grid-template-columns: 1fr 300px`
- Usa CSS vanilla puro (sin Tailwind)

### 2. Hub de Módulo (`clase{N}/index.html`)
- Grid de tarjetas (`content-card`) con animación `fadeInUp`
- Back-link a `../index.html`
- `content-grid`: `repeat(auto-fill, minmax(320px, 1fr))`
- Cada tarjeta: `card-tag`, `h2`, `p` descriptivo, `card-action`
- CSS vanilla (sin Tailwind)

### 3. Sub-Hub de Tema (`clase3/git/index.html`, etc.)
- Mismo diseño que Hub de Módulo
- Back-link al módulo padre (`../index.html`)
- Color accent del tema correspondiente

### 4. Páginas de Contenido / Laboratorios
- Tailwind CSS vía CDN + CSS custom para efectos
- `.glass-panel` con glassmorphism (`backdrop-filter: blur(12px)`)
- Back-link al sub-hub (`index.html` relativo)
- Interactividad con JavaScript vanilla

---

## Tecnologías

| Tecnología | Uso |
|---|---|
| HTML5 semántico | Estructura de todas las páginas |
| CSS3 custom properties | Sistema de diseño y theming |
| Tailwind CSS (CDN) | Utilidades en páginas de laboratorio |
| JavaScript vanilla | Interactividad, theme toggle, simuladores |
| Google Fonts | Inter, Outfit, JetBrains Mono |
| Google Analytics (gtag) | Tracking en `index.html` |

> **Nota:** Tailwind CSS via CDN se usa **solo en páginas de contenido/lab**. Los hubs (`clase{N}/index.html`, sub-hubs) usan **CSS vanilla únicamente** para mantener coherencia visual con los hubs de módulo 1 y 2.

---

## Patrones de Interactividad

### Theme Toggle (todas las páginas)
```javascript
// Persistencia: localStorage.setItem('theme', 'dark' | 'light')
// data-theme="light" en <html> activa modo claro
// Sin data-theme = modo oscuro (default)
```

### Animación de entrada (hubs)
```css
@keyframes fadeInUp {
    from { opacity: 0; transform: translateY(30px); }
    to   { opacity: 1; transform: translateY(0); }
}
/* Aplicada a .container con 0.8s cubic-bezier(0.4,0,0.2,1) */
```

### Animación de entrada (labs Tailwind)
```css
@keyframes fadeIn {
    from { opacity: 0; transform: translateY(12px); }
    to   { opacity: 1; transform: translateY(0); }
}
/* .animate-in con animation-delay escalonado por sección */
```

### Glass Panel
```css
.glass-panel {
    background: var(--card-bg);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 1.5rem;
}
[data-theme="light"] .glass-panel {
    border-color: rgba(0,0,0,0.06);
    box-shadow: 0 10px 30px -5px rgba(0,0,0,0.05);
}
```

---

## Convenciones de Nomenclatura

### Estructura de URLs (post-migración)
```
/                           → index.html (hub principal)
/clase1/                    → clase1/index.html
/clase1/{tema}.html         → página de contenido de clase 1
/clase2/                    → clase2/index.html
/clase2/css/{tema}.html     → laboratorio CSS
/clase3/                    → clase3/index.html
/clase3/git/                → clase3/git/index.html (hub Git)
/clase3/git/{tema}.html     → página de contenido Git
/clase3/copilot/            → clase3/copilot/index.html
/clase3/copilot/{tema}.html → página de contenido Copilot
/clase3/fundamentos-ia/     → clase3/fundamentos-ia/index.html
/clase3/fundamentos-ia/{tema}.html → página contenido IA
```

### Back-links (navegación hacia arriba)
- Lab → `index.html` (sub-hub del tema)
- Sub-hub → `../index.html` (hub del módulo)
- Hub módulo → `../index.html` (hub principal)

### Nombres de archivo de contenido
- Descriptivos y sin prefijo de módulo (ya está dado por la carpeta)
- Ej: `clase3/git/que-es.html` (no `git-que-es.html`)

---

## Inventario de Interactividades por Módulo

### Módulo 1 — HTML
- Explorador visual de etiquetas semánticas
- Visualizador de rayos X de estructura HTML
- Inspector de atributos con tabs

### Módulo 2 — CSS
- Sandbox de aplicación de estilos en vivo
- Modelo de caja interactivo con medidas
- Comparador de unidades de medida
- Flexbox playground con controles en tiempo real

### Módulo 3.1 — Git
- Simulador de terminal con comandos reales
- Zonas interactivas del flujo de trabajo (Working Dir / Stage / Repo)
- Historial visual de ramas
- Constructor de commits convencionales con validador

### Módulo 3.2 — Copilot
- Demo de autocompletado con texto fantasma animado
- Simulador de chat con respuestas predefinidas
- Comparador de prompts buenos vs malos con barra de calidad
- Tracker de atajos de teclado con barra de progreso

### Módulo 3.3 — Fundamentos IA
- Pasos interactivos: redes neuronales, transformer, predicción
- Tokenizador en vivo (input → chips de tokens)
- Tabla comparativa de modelos con calculadora de contexto
- Simulador de parámetros (sliders temperature, top-p, max tokens)
- Constructor de prompts (Rol / Contexto / Tarea / Formato) con preview y copia
- Ejemplos de alucinaciones por tipo (citas, URLs, fechas, código)
- Ciclo ReAct clickeable (Pensar → Actuar → Observar → Responder)
- Diagrama de arquitectura MCP con flujo visual
- Comparativa interactiva de orquestadores (Claude Code, Cursor, Aider, etc.)

---

## Flujo de Navegación Completo

```
index.html
├── clase1/index.html
│   ├── esqueleto-web.html
│   ├── anatomia-html.html
│   ├── atributos-html.html
│   └── diccionario.html
│
├── clase2/index.html
│   ├── clase2-1.html
│   └── css/
│       ├── aplicando-css.html
│       ├── modelo-de-caja.html
│       ├── unidades-de-medida.html
│       ├── flexbox-playground.html
│       ├── diccionario-css.html
│       └── diccionario-atributos.html
│
└── clase3/index.html
    ├── git/index.html
    │   ├── que-es.html
    │   ├── flujo-trabajo.html
    │   ├── comandos.html
    │   ├── ramas.html
    │   └── commits.html
    │
    ├── copilot/index.html
    │   ├── que-es.html
    │   ├── autocompletado.html
    │   ├── chat.html
    │   ├── prompts.html
    │   └── atajos.html
    │
    └── fundamentos-ia/index.html
        ├── como-funciona.html
        ├── llm.html
        ├── tokens.html
        ├── parametros.html
        ├── contexto.html
        ├── alucinaciones.html
        ├── agentes.html
        ├── mcp.html
        └── orquestadores.html
```

---

## Repositorio y Despliegue

- **Control de versiones:** Git + GitHub
- **Repositorio:** `github.com/germardones/TI3031`
- **Despliegue:** Vercel

---

## Autor

**Germán Mardones**
Docente INACAP
[linkedin.com/in/mardonesgerman](https://www.linkedin.com/in/mardonesgerman/)
Email: german.mardones@inacapmail.cl

---

*Última actualización: Abril 2026*
