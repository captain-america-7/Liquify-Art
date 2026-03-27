# Fluid Simulation — Public Web Experiment

**[Live Demo](https://yoursite.com/)** *(Update with actual URL)*

A fullscreen, GPU-powered fluid simulation built for immediate, zero-friction interaction. The page feels less like a website and more like a portal into a living material. Touch it, watch it breathe.

## About the Engine

This simulation evaluates the **Navier-Stokes equations** in real-time entirely on the GPU. It heavily uses WebGL Framebuffer Objects (FBOs) to store velocity, pressure, dye, and vorticity fields, bouncing them back and forth between shaders. 

**Shader Pipeline:**
`curl → vorticity → divergence → pressure → gradient subtract → advection`

The core loop updates these fields every frame (~60fps), generating incredibly detailed fluid motion with no canvas or DOM overhead.

## Quick Start (Local Development)

The project demands **zero build step** and holds no bloated dependencies. Just serve it statically.

```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx serve .
```

Then open `http://localhost:8000` (or the equivalent local URL).

## Architecture

- `index.html`: Entry point, canvas element + floating UI chrome.
- `script.js`: Physics engine + WebGL core. Follows a functional setup and uses heavily optimised GLSL kernels.
- Pure HTML/CSS UI: Control inputs styled to match the custom glassmorphic aesthetic (no external UI libraries required).
- `LDR_LLL1_0.png`: Dithering noise texture to eliminate color banding.

## Features

- Multi-touch fluid splats with responsive color transitions.
- Automatic performance scaling (degrades cleanly on low-end hardware).
- Zero-friction URL State persistence for sharing presets (e.g. `/#viscosity=0.4&bloom=true`).
- Accessible, single-page architecture built purely with ES6 and WebGL.

## Contributing

See ["Good first issues"](https://github.com/paveldogreat/WebGL-Fluid-Simulation/issues) for an entry point. Read `CONTRIBUTING.md` for specific contribution workflows and rules.
