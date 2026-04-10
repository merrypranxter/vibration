# Chladni Patterns

Chladni patterns are the visible geometric figures formed by nodal lines on a vibrating plate. When a plate is driven at one of its resonant frequencies and covered with fine particles (sand, salt, lycopodium powder), the particles migrate away from regions of maximum vibration (antinodes) and accumulate along the stationary lines of zero displacement called **nodal lines**. The resulting figures are among the most striking visual demonstrations of wave physics.

---

## What Are Chladni Patterns?

A vibrating plate does not move uniformly. At any given resonant frequency, certain lines across the plate surface remain perfectly still — the **nodal lines** — while the regions between them (antinodes) oscillate up and down with maximum amplitude. When sand or powder is scattered on the plate, particles are literally bounced away from the high-amplitude antinodal zones and come to rest where there is no motion: along the nodal lines.

The pattern that emerges is a direct visual map of the plate's vibrational mode at that frequency. Change the frequency, and the pattern changes. Each resonant frequency produces a unique, reproducible geometric fingerprint.

---

## Historical Discovery: Ernst Chladni (1787)

German physicist Ernst Florenz Friedrich Chladni (1756–1827) discovered these patterns in 1787 while bowing the edge of a metal plate with a violin bow. He had scattered sand across the plate beforehand, and as he bowed, the sand reorganized into intricate, symmetric figures.

Chladni systematically catalogued these patterns and presented them in his 1787 work *Entdeckungen über die Theorie des Klanges* (Discoveries on the Theory of Sound). His demonstrations captivated European scientific society, including Napoleon Bonaparte, who famously offered a prize for a mathematical explanation of the patterns.

The prize was eventually claimed by Sophie Germain in 1816 after three attempts, establishing the foundations of plate vibration theory.

---

## The Physics: Modal Analysis and Eigenfrequencies

### Wave Equation for Plates

The motion of a thin elastic plate is governed by the **biharmonic wave equation** (Kirchhoff plate theory):

```
D∇⁴w + ρh(∂²w/∂t²) = 0
```

Where:
- `D = Eh³ / [12(1 − ν²)]` — flexural rigidity (N·m)
- `E` — Young's modulus of the plate material (Pa)
- `h` — plate thickness (m)
- `ρ` — material density (kg/m³)
- `ν` — Poisson's ratio (dimensionless)
- `w(x,y,t)` — transverse displacement at position (x,y) and time t
- `∇⁴` — biharmonic operator (∇⁴ = ∂⁴/∂x⁴ + 2∂⁴/∂x²∂y² + ∂⁴/∂y⁴)

### Eigenmodes and Eigenfrequencies

Solutions to the plate wave equation take the form of **eigenmodes** — specific spatial patterns that oscillate at well-defined **eigenfrequencies**. Each eigenmode is characterized by a pair of **modal indices** (m, n):

- **m** = number of nodal lines parallel to the y-axis (across the plate width)
- **n** = number of nodal lines parallel to the x-axis (across the plate length)

For a simply-supported **square plate** of side length `a`, the eigenfrequencies are:

```
f_mn = (π/2) × √(D/ρh) × (m² + n²) / a²
```

This formula shows that:
1. Higher modal indices → higher frequency
2. Larger plates → lower frequencies (scales as 1/a²)
3. Stiffer or thinner plates → different frequency spacing

### Free-Edge Plates (Real Chladni Setup)

Chladni's original experiment used plates held at a single center point (free edges). Free-edge boundary conditions produce somewhat different eigenfrequency values than simply-supported edges, but the qualitative behavior — sand accumulating at nodal lines — is identical. The patterns tend to be even more symmetric and visually striking.

---

## How Sand Reveals Nodal Lines

The migration of particles to nodal lines involves several physical mechanisms:

1. **Acoustic radiation pressure**: The oscillating plate creates a non-uniform acoustic field. Particles experience a net drift force (radiation pressure) directed toward regions of minimum acoustic energy — the nodal lines.

2. **Direct plate contact**: Particles on antinodal regions are repeatedly struck by the rapidly oscillating plate surface, bouncing them away from high-amplitude zones.

3. **Surface acoustic streaming**: Viscous drag in the thin air layer above the plate creates slow convective currents that sweep particles toward nodal lines.

Light, fine-grained particles (lycopodium, fine sand) respond most visibly. The pattern sharpens at higher amplitudes but requires finding the precise resonant frequency.

---

## Different Plate Shapes

### Square Plates
The most commonly used geometry. Produces rectangular nodal line patterns characterized by integer-pair modal indices. Symmetry depends on the indices:
- (m, m): **C4v** symmetry (fourfold rotation axis)
- (m, n) with m ≠ n: **C2v** symmetry (two mirror planes)

### Circular Plates
Produce patterns involving **Bessel functions** (Jₙ). Modes are described by (d, c) — nodal diameters and nodal circles:
- (d, 0): d straight lines through center (diameters)
- (0, c): c concentric rings
- (d, c): combination of diameters and circles

### Hexagonal Plates
Produce patterns with **C6v**, **C3v**, or **C2v** symmetry. The six-fold geometry of hexagonal plates allows modes that do not appear on square or circular plates, including stunning six-petalled snowflake patterns.

---

## Frequency → Pattern Complexity

As frequency increases, the modal indices (m, n) increase, producing patterns with more nodal lines and smaller domains:

| Frequency Range | Pattern Character |
|---|---|
| Very low (20–100 Hz) | 1–2 simple nodal lines; large sand-free zones |
| Low (100–300 Hz) | 2–4 nodal lines; clear geometric shapes |
| Mid (300–1000 Hz) | 4–8 nodal lines; elaborate lattice patterns |
| High (1–4 kHz) | 8–20 fine lines; dense, intricate webs |
| Very high (4–20 kHz) | 20+ lines; near-fractal complexity |

The number of antinodal regions equals (m+1)(n+1) for a rectangular plate with m,n nodal lines, growing rapidly with frequency.

---

## Applications

- **Musical instrument making**: Violin and guitar makers use Chladni patterns to assess plate stiffness and tap-tone quality before assembly.
- **Structural engineering**: Modal analysis of aircraft panels, turbine blades, and bridge decks uses the same principles.
- **Quality control**: Resonant frequency testing can detect cracks, delaminations, or material inconsistencies in plates and sheets.
- **Acoustic levitation**: Engineering applications exploit nodal geometry to trap and manipulate small particles without contact.

---

## Files in This Section

| File | Description |
|---|---|
| `README.md` | This file — overview and index |
| `historical_context.md` | Ernst Chladni biography, historical demonstrations, subsequent discoveries |
| `modal_analysis.md` | Technical deep-dive into plate vibration physics and eigenmodes |
| `chladni_patterns.json` | 42-entry dataset of documented Chladni patterns (20 Hz – 8 kHz) |
| `plate_types.json` | Physical properties of square, circular, and hexagonal plate configurations |
| `pattern_gallery/patterns_by_frequency.csv` | 52-row tabular catalog of patterns across full audible spectrum |
| `pattern_gallery/modal_shapes.json` | Modal index grid describing shape for every (m,n) combination from (1,1) to (6,6) |

---

## Quick Reference: Key Formulas

```
Flexural rigidity:       D = Eh³ / [12(1 − ν²)]
Square plate frequency:  f_mn = (π/2) √(D/ρh) (m²+n²)/a²
Node count (square):     N_nodes = m + n − 2   (free-edge approximation)
Antinode count:          N_anti = (m−1)(n−1) + 4   (approx)
Q-factor:                Q = f_res / Δf_3dB
Decay time:              τ = Q / (π·f_res)
```

---

*See also: `../cymatics/README.md` for wet/fluid cymatic patterns and `../VIBRATION_PHYSICS_PRIMER.md` for foundational wave mechanics.*
