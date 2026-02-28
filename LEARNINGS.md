# Learnings

## 2026-02-28 — Axis Swaps Are Fragile

Swapping Y/Z by changing the projection function (`cy - p[2] * s` instead of `cy - p[1] * s`) or just swapping axis labels in `getAxes()` breaks circle alignment. The rotation functions (rotX, rotY), plane quad definitions, face centers, and cube vertices all assume a specific coordinate system. A proper axis swap needs a coordinated change across all geometry.

## 2026-02-28 — Geometry Must Match Across Drawing Functions

When rewriting `drawSpheresCube`, the sphere centers and radius calculation must be identical to `drawSpheres` (origin + 6 face centers, radius = minDist * 0.5). Any deviation causes visible misalignment.
