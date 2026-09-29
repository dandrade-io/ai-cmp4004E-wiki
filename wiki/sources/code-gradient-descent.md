---
title: "Code — Gradient Descent (gd_functions.py, gd_steroids.py)"
type: source
tags: [optimization, gradient-descent, code]
sources: [raw/code/gd_functions.py, raw/code/gd_steroids.py]
updated: 2026-09-29
---
# Code — Gradient Descent

Two Python scripts (comments in Spanish) that minimize the convex quadratic
**f(x, y) = (x−2)² + (y+2)²**, whose unique minimum is at (2, −2) with f = 0. Gradient: ∇f = [2(x−2), 2(y+2)]. Concept: [[gradient-descent]].

## gd_functions.py
- Start w = (0, 0), learning rate **η = 0.1**, **1000 iterations**, update `w = w - eta * g`.
- Prints every iteration and the final point/value.

## gd_steroids.py
- Same objective/gradient, but **η = 0.02**, **200 iterations**; stores the trajectory and animates it over a 3D surface (matplotlib `FuncAnimation`), saved as MP4 via ffmpeg.

## Convergence analysis (quadratic)
For each coordinate, e.g. x: x_{t+1} − 2 = (x_t − 2) − η·2(x_t − 2) = (1 − 2η)(x_t − 2). So error shrinks by factor **(1 − 2η)** per step; converges iff |1 − 2η| < 1, i.e. 0 < η < 1 (unverified derivation, straightforward algebra).
- η = 0.1: factor 0.8; after 1000 steps error ≈ 0.8¹⁰⁰⁰ ≈ 0 (machine precision reached after ~200 steps; the rest is wasted).
- η = 0.02: factor 0.98; after 200 steps error ≈ 0.98²⁰⁰ ≈ 0.018 of the initial distance (≈ 0.05 units from the optimum for an initial distance of ~2.8) — close but not converged.
- η = 0.5 would land exactly on the minimum in one step; η > 1 diverges.

> ⚠️ Errata: in `gd_steroids.py` the plotted surface is `Z = (X-2)**2 + (Y+1)**2` and the trajectory height is `(ys+1)**2`, but the objective and gradient use `(y+2)²`. The visual bowl's minimum is at y = −1 while the optimizer converges to y = −2, so the animated point ends on a slope, not the bottom. Fix: use `(Y+2)**2` in both places.

Also (unverified/minor): `gd_steroids.py` sets `ax.set_ylim(-5, 3)` fine for both; the `Axes3D` import is only needed for old matplotlib.

## Takeaways
Learning rate controls speed vs stability; a well-conditioned convex bowl has no local minima, so these scripts do not show [[optimization-landscape]] difficulties — contrast with [[benchmark-functions]] used in [[code-simulated-annealing]].
