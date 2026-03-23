# Contributing to Fluid

First of all, thank you! The code relies heavily on raw WebGL/GLSL—don't let the ~1650 lines intimidate you. There are a handful of major files with straightforward responsibilities:

## General Principles

1. **No Frameworks.** 
   The initial v1 product ships natively and instantly. Avoid importing React, Vue, Three.js or thick abstractions. 
   
2. **Performance.** 
   The simulation evaluates complex Navier-Stokes equations per-frame across thousands of GPU pixels. Ensure physics logic (curl, vorticity, divergence, advection) only acts when strictly necessary. Avoid excessive state reads (`gl.readPixels`) if unneeded for rendering.

3. **Graceful Degrade over Errors.**
   There should never be a crash screen. If `EXT_color_buffer_float` or `OES_texture_half_float` are unsupported, simply ignore or degrade resolution without console spew.

## Feature Philosophy

- The UI MUST NEVER shout over the sim. The controls run entirely in floating, unobtrusive glassmorphism chrome.
- Add features via the `#hash` URL sync. Every change to physical dynamics should be shareable via a single URL.
- No monolithic `Webpack`/`Vite` setups are permitted for v1. Work directly via ES6 `script` tags.

## Reporting Issues

If you find visual glithes on specific devices:
- Specify exactly the Platform and Browser.
- Capture console logs if a WebGL fallback error triggers.
- Take a screenshot of the `#` URL hash that causes the erratic behaviour.

## Submitting Pull Requests

Please keep PRs tight. Focus on a specific fix or feature. 

1. Create a descriptive branch (e.g. `feature/obstacle-drawing`).
2. Add the URL hash to the commit title when affecting simulation constants.
3. Test the build dynamically by disabling GL extensions in your browser DevTools physically. Ensure no regression of fallback physics.
