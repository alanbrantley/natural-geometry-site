# Learnings

## 2026-02-28 — Axis Swaps Are Fragile

Swapping Y/Z by changing the projection function (`cy - p[2] * s` instead of `cy - p[1] * s`) or just swapping axis labels in `getAxes()` breaks circle alignment. The rotation functions (rotX, rotY), plane quad definitions, face centers, and cube vertices all assume a specific coordinate system. A proper axis swap needs a coordinated change across all geometry.

## 2026-02-28 — Geometry Must Match Across Drawing Functions

When rewriting `drawSpheresCube`, the sphere centers and radius calculation must be identical to `drawSpheres` (origin + 6 face centers, radius = minDist * 0.5). Any deviation causes visible misalignment.

## 2026-02-28 — Ethereal Design: Less Is More

User aesthetic strongly favors pencil-drawn monochrome. Colored plane fills were rejected — keep geometry pure grey. Dwell flash needed 10-100x reduction from initial implementation. Ambient color (orbs, glassmorphism hover glow) works best as peripheral/background only, never on the geometry itself.

## 2026-02-28 — Static Site Vercel Deployment

Single `index.html` sites need zero Vercel config. Framework preset: "Other". No build command. Auto-deploys on every push to main. Custom domain requires A record (76.76.21.21) for root and CNAME (cname.vercel-dns.com) for www.

## 2026-03-02 — Typewriter Timing with Dwell Triggers

Align typewriter to angular position, not rotation count. Type-in at TW_APPROACH (22°) before trigger, backspace at TW_BACKSPACE_BEFORE (35°) before the NEXT trigger. Use wall-clock time (performance.now()) for character stepping so typing speed is consistent regardless of rotation velocity changes from decel/accel. Keep suffix visible between dwells — backspace late, not early.

## 2026-03-02 — User Prefers Minimal Copy Changes

When user says "just add X to Y", do exactly that — don't restructure HTML or add new elements. One-line text changes should be one-line edits.
