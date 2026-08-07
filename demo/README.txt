XClipGS - Interactive Web Demo (Code Supplement)
================================================

Runs fully offline. No network access and no build step required.

  cd XClipGSWebDemo
  python3 -m http.server 8000
  # open http://localhost:8000 in a WebGL2-capable browser

(Opening index.html directly via file:// also works in most browsers.)

The PlayCanvas engine (v2.7.4, assets/playcanvas-2.7.4.min.js) is bundled, so
the page is self-contained.


What this demonstrates
----------------------
The three half-space clip operators compared in the paper, injected into a real
3D Gaussian-Splatting rasterizer and switchable live at render time:

  Ours - exact per-ray truncation (Equation 5 of the main paper)
  MM   - moment-matched Gaussian surrogate
  HC   - hard per-primitive cull

Controls: operator buttons; Plane position slider; Axis (X/Y/Z); Sweep
(animates the plane). Drag to orbit, scroll to zoom.

What to look for, matching the paper's claims:
  - Sweep with HC selected: whole primitives pop in/out as the plane crosses
    their centers (the center-quantized boundary of Section 3).
  - Sweep with MM selected: the cut face carries a soft residual tail; material
    remains visible past the plane (the O(sigma_n) tail; the Leak metric).
  - Sweep with Ours selected: the boundary stays sharp and no material appears
    on the culled side, from any viewing angle.

A procedural Gaussian scene is generated in-browser so the page works with no
assets. You can drag a .ply / .compressed.ply onto the canvas to view another
Gaussian scene.


Scope and honest caveats
------------------------
- This is an INDEPENDENT WebGL/PlayCanvas reimplementation of the three
  operators for interactive illustration. It is NOT the CUDA rasterizer used
  for any number in the paper. All reported metrics come from the CUDA
  implementation described in Supplement S2.
- The demo therefore corroborates the qualitative operator behavior only. It is
  not evidence for the quantitative results.
- The bundled engine is third-party (PlayCanvas, MIT license), included
  verbatim only so the page runs without network access.

Implementation notes for the curious are in assets/demo.js; the shader clip is
injected by patching the engine's global gsplat chunk registry before the
material builds.
