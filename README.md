# Anneal — Design & Motion Studio

A single-page, cinematic agency-style website concept: a scroll-driven 3D scene, custom magnetic cursor, and animated typography, built with vanilla JS, Three.js, and GSAP — no build step required.

**[Live demo →](https://claude.ai/artifact/6sesfAt2dmnmVsE3Zzjx1f)**

![tech](https://img.shields.io/badge/stack-HTML%20%2F%20CSS%20%2F%20JS-15130F)
![three.js](https://img.shields.io/badge/three.js-r128-C79A65)
![gsap](https://img.shields.io/badge/GSAP-3.12.5-8CA0AA)

## Features

- **Scroll-driven 3D camera** — a faceted brass icosahedron sits in a Three.js scene; the camera dollies through six hand-placed keyframes tied to scroll position, so every section reveals a new vantage of the same object with no hard cuts.
- **Mouse-reactive object** — the object tilts and rotates toward the cursor, layered on top of its scroll-driven motion.
- **Custom magnetic cursor** — a lagging ring + dot that snaps and grows over interactive elements, which gently pull toward it.
- **Lerped smooth scroll** — wheel input is intercepted and eased toward a target scroll position for a cinematic feel (desktop only; touch devices keep native momentum scrolling).
- **Text animations** — headline and paragraph text are split into masked word spans and revealed via GSAP: an orchestrated sequence on load for the hero, scroll-triggered reveals elsewhere.
- **No build tooling** — everything lives in one `index.html`; dependencies load from CDN via `<script>` tags.

## Tech stack

| Layer | Tool |
|---|---|
| Markup / styling | Plain HTML5 + CSS (custom properties, `clamp()`, Grid/Flexbox — no CSS framework) |
| 3D scene | [Three.js](https://threejs.org/) r128 (UMD build) |
| Animation | [GSAP](https://gsap.com/) 3.12.5 + ScrollTrigger |
| Type | [Unbounded](https://fonts.google.com/specimen/Unbounded) (display) + [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) (body), via Google Fonts |
| Custom cursor / scroll / word-split | Vanilla JS (`requestAnimationFrame` loops, no extra libraries) |

## Getting started

No install, no build step.

```bash
git clone <this-repo>
cd anneal-studio
```

Then either:

- Open `index.html` directly in a browser, or
- Serve it locally (recommended, since some browsers restrict certain features on `file://`):

```bash
npx serve .
# or
python3 -m http.server 8000
```

## Deploying

It's a static file — drop `index.html` into any static host:

- **Vercel / Netlify** — drag-and-drop the folder or connect the repo, no build command needed.
- **GitHub Pages** — enable Pages on this repo pointed at the root (or a `/docs` folder containing `index.html`).

## Project structure

```
.
└── index.html   # everything: markup, styles, and scripts in one file
```

## Customizing

- **Copy & branding** — all studio name, headline, and section copy live directly in the HTML in `<main>`.
- **Color palette** — CSS custom properties at the top of the `<style>` block (`--bg`, `--brass`, `--steel`, `--ember`, etc.).
- **3D object motion** — the `keyframes` array in the `<script>` block controls camera position, look-at target, object rotation, scale, and color at each scroll stage. Add or edit entries to change the scene's choreography.
- **Fonts** — swap the Google Fonts `<link>` and the `--font-display` / `--font-body` variables.

## Browser support

Targets modern evergreen browsers (Chrome, Firefox, Safari, Edge). Requires WebGL. Respects `prefers-reduced-motion` (disables load/scroll animations) and adapts cursor/scroll behavior for touch (`pointer: coarse`) devices.

## License

Feel free to use this as a starting point for your own project. Three.js and GSAP are used under their respective licenses (MIT and GSAP's standard "no charge" license — see [gsap.com/licensing](https://gsap.com/licensing/) if you plan to use GSAP's paid Club plugins beyond what's used here).
