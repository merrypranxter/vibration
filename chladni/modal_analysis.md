# Modal Analysis of Vibrating Plates

This document provides a technical treatment of the physics underlying Chladni patterns, covering eigenmodes, the plate wave equation, circular plate solutions, symmetry groups, and computational methods.

---

## 1. Fundamentals: Eigenmodes and Eigenvectors

### What Is a Mode?

A vibrating structure does not oscillate arbitrarily. When driven at a resonant frequency, it adopts a specific spatial deformation pattern that repeats in time — an **eigenmode** (or normal mode). The spatial pattern is the **eigenvector** (mode shape), and the frequency at which it occurs is the **eigenfrequency** (natural frequency).

For a linear elastic system, the motion at any time can be expressed as a superposition of all eigenmodes:

```
w(x, y, t) = Σ_mn A_mn · φ_mn(x,y) · cos(2π f_mn t + θ_mn)
```

Where:
- `φ_mn(x,y)` — the mode shape (eigenvector) for mode (m,n)
- `f_mn` — the eigenfrequency for mode (m,n)
- `A_mn` — modal amplitude (set by initial conditions or driving amplitude)
- `θ_mn` — phase angle

The nodal lines visible in a Chladni experiment are the zero-contours of `φ_mn(x,y)` — the places where the eigenfunction equals zero.

### Physical Interpretation

- **Eigenvector (mode shape)**: The spatial fingerprint of a resonance. For a square plate mode (2,3), the eigenvector has 2 nodal lines in one direction and 3 in the other.
- **Eigenfrequency**: The natural oscillation rate of that mode. Drives the system at this frequency → large amplitude (limited only by damping).
- **Orthogonality**: Mode shapes are orthogonal — each mode carries its own independent "channel" of vibration.

---

## 2. The Plate Wave Equation

### Kirchhoff-Love Plate Theory

The transverse vibration of a thin elastic plate is described by the **Kirchhoff-Love plate equation** (or biharmonic wave equation):

```
D ∇⁴w(x,y,t) + ρh ∂²w(x,y,t)/∂t² = q(x,y,t)
```

Where:
- `w(x,y,t)` — transverse (out-of-plane) displacement (m)
- `D` — flexural rigidity (N·m) = `Eh³ / [12(1 − ν²)]`
- `ρ` — plate material density (kg/m³)
- `h` — plate thickness (m)
- `q(x,y,t)` — distributed transverse load (Pa) — zero for free vibration
- `∇⁴ = ∂⁴/∂x⁴ + 2∂⁴/∂x²∂y² + ∂⁴/∂y⁴` — biharmonic operator

### Flexural Rigidity D

The flexural rigidity `D` determines how resistant a plate is to bending:

```
D = E h³ / [12(1 − ν²)]
```

| Parameter | Symbol | Typical Steel | Typical Aluminum | Typical Glass | Typical Acrylic |
|---|---|---|---|---|---|
| Young's modulus | E (GPa) | 200 | 69 | 72 | 3.2 |
| Poisson's ratio | ν | 0.30 | 0.33 | 0.23 | 0.37 |
| Density | ρ (kg/m³) | 7850 | 2700 | 2500 | 1190 |

Higher D → higher eigenfrequencies. Thin acrylic plates have much lower D than steel plates of the same dimensions, and correspondingly lower resonant frequencies.

### Free Vibration Solution

Assuming harmonic time dependence `w(x,y,t) = W(x,y) e^{iωt}`:

```
∇⁴W − k⁴W = 0     where k⁴ = ρhω²/D = ρh(2πf)²/D
```

The **wave number** k governs the spatial wavelength of the plate modes: λ = 2π/k.

---

## 3. Modal Indices for Square Plates

### Simply-Supported Boundary Conditions

For a square plate of side length `a` with simply-supported edges (transverse displacement and bending moment both zero at each edge), the eigenmodes are:

```
W_mn(x,y) = sin(mπx/a) · sin(nπy/a)     m,n = 1, 2, 3, ...
```

These are products of sine functions, producing:
- `m−1` nodal lines parallel to the y-axis
- `n−1` nodal lines parallel to the x-axis

The corresponding eigenfrequencies are:

```
f_mn = (π/2) · √(D/ρh) · (m² + n²) / a²
```

**Example**: For a 20 cm × 20 cm steel plate, 1 mm thick:
```
D = 200×10⁹ × (0.001)³ / [12 × (1 − 0.09)] = 18.3 N·m
ρh = 7850 × 0.001 = 7.85 kg/m²
√(D/ρh) = √(2.33) = 1.527 m²/s

f_mn = (π/2) × 1.527 × (m² + n²) / (0.20)²
     = 60.0 × (m² + n²)  Hz
```

Mode frequencies:
```
(1,1): f = 60 × 2 = 120 Hz
(1,2): f = 60 × 5 = 300 Hz
(2,2): f = 60 × 8 = 480 Hz
(1,3): f = 60 × 10 = 600 Hz
(2,3): f = 60 × 13 = 780 Hz
(3,3): f = 60 × 18 = 1080 Hz
(1,4): f = 60 × 17 = 1020 Hz
(2,4): f = 60 × 20 = 1200 Hz
(4,4): f = 60 × 32 = 1920 Hz
```

### Free-Edge Boundary Conditions

Real Chladni plates are typically held at a single point (the center, for square plates) with free edges. Free-edge boundary conditions are more complex — they require both the bending moment AND the transverse shear force to vanish at the edges, leading to transcendental characteristic equations that must be solved numerically.

The frequency ordering is similar to the simply-supported case, but the absolute values differ (free-edge plates generally have lower eigenfrequencies for the same (m,n) index).

### Frequency Degeneracy

A key feature of square plates: modes (m,n) and (n,m) with m≠n have the **same eigenfrequency** (degenerate modes). For example, mode (1,2) and mode (2,1) both occur at `f = 60 × 5 = 300 Hz` for our example.

This degeneracy has profound consequences: driving the plate at a degenerate frequency excites a superposition of the two modes. The resulting pattern depends on the relative phase and amplitude of the two modes, producing a continuous family of patterns between the two pure-mode extremes. This is why Chladni sometimes observed unexpected patterns at certain frequencies — he was exciting degenerate mode combinations.

---

## 4. Circular Plate Modes and Bessel Functions

### The Circular Plate Eigenproblem

For a circular plate of radius `R`, the natural coordinate system is polar `(r, θ)`. The eigenvalue equation for the circular plate is:

```
∇⁴W − k⁴W = 0     in polar coordinates
```

The general solution that is finite at the center is:

```
W_dn(r,θ) = [J_d(k_dn r) + α_dn I_d(k_dn r)] × {cos(dθ) or sin(dθ)}
```

Where:
- `J_d` — Bessel function of the first kind, order d
- `I_d` — modified Bessel function of the first kind, order d
- `d` — number of **nodal diameters** (0, 1, 2, 3, ...)
- `n` — number of **nodal circles** (0, 1, 2, 3, ...)
- `k_dn` — the n-th root of the characteristic equation for d nodal diameters
- `α_dn` — coefficient determined by boundary conditions

### Boundary Conditions

**Free edge** (most common for Chladni demonstrations):
```
Bending moment:    M_r(R) = 0     →     W'' + ν(W'/R) = 0
Shear force:       V_r(R) = 0     →     W''' + ... = 0
```

These transcendental equations must be solved numerically to find k_dn R values.

### Table of Eigenfrequency Parameters (k_dn R) for Free Circular Plates

| d (diameters) | n=0 | n=1 | n=2 |
|---|---|---|---|
| 0 | 3.011 | 6.200 | 9.369 |
| 1 | 1.893 | 4.842 | 7.959 |
| 2 | 2.988 | 5.937 | 9.075 |
| 3 | 4.539 | 7.473 | 10.62 |

The eigenfrequency for circular plate mode (d,n) is:

```
f_dn = (k_dn R)² / (2π R²) · √(D/ρh)
     = (k_dn)² / (2π) · √(D/ρh)
```

### Circular Plate Mode Shape Descriptions

| (d, n) | Description | Visual Pattern |
|---|---|---|
| (0, 1) | Breathing mode: single nodal circle | Concentric ring |
| (1, 0) | Diametral mode: single line through center | Single diameter |
| (2, 0) | Two diameters at 90°: X or + pattern | Cross / X |
| (3, 0) | Three diameters at 60°: snowflake (3 arms) | 3-armed star |
| (4, 0) | Four diameters at 45°: 4-armed star | 4-armed star |
| (0, 2) | Two concentric circles, no diameter | Double ring |
| (1, 1) | One diameter + one circle | Yin-yang variant |
| (2, 1) | Two diameters + one circle | Cross with ring |

---

## 5. Symmetry Groups of Plate Modes

The symmetry of a mode shape can be described using **point group notation** from crystallography:

| Symmetry Group | Symmetry Operations | Plate/Mode Example |
|---|---|---|
| C1 | Identity only | No symmetry |
| C2 | 2-fold rotation | Rectangular plate asymmetric mode |
| C2v | 2-fold rotation + 2 mirror planes | Square plate (m≠n) |
| C4v | 4-fold rotation + 4 mirror planes | Square plate (m=n) |
| C∞v | Full rotational symmetry | Circular plate (d=0) pure ring modes |
| Cnv | n-fold rotation + n mirrors | Circular (d=n), hexagonal modes |
| D4h | Square point group (full) | Square plate with all symmetries |
| D6h | Hexagonal point group (full) | Hexagonal plate lowest modes |

### Symmetry of Square Plate Modes

- Mode (m,m): C4v — four-fold symmetric, looks like a checkerboard
- Mode (m,n) with m≠n: C2v — only two-fold symmetric, rectangular pattern
- Superposition of (m,n) and (n,m): Can produce C4v if equal amplitudes and phases

### Symmetry of Circular Plate Modes

- Mode (0,n): C∞v — full rotational symmetry (ring patterns)
- Mode (d,n) with d≥1: Cdv — d-fold symmetry
- A (3,0) mode (three nodal diameters) has C3v symmetry (6 equivalent orientations)

---

## 6. Nodal Line Patterns

### Square Plate

For mode (m,n) on a square plate (simply-supported), the nodal lines are the zero-contours of `sin(mπx/a) · sin(nπy/a)`:

```
sin(mπx/a) = 0   →   x = k·a/m,   k = 1, 2, ..., m−1
sin(nπy/a) = 0   →   y = k·a/n,   k = 1, 2, ..., n−1
```

So there are exactly:
- `m − 1` nodal lines parallel to the y-axis
- `n − 1` nodal lines parallel to the x-axis
- Total nodal lines: `(m − 1) + (n − 1) = m + n − 2`
- Total antinodal regions: `m × n`

| Mode | Nodal lines | Antinodal regions |
|---|---|---|
| (1,1) | 0 + 0 = 0 | 1 |
| (2,1) | 1 + 0 = 1 | 2 |
| (2,2) | 1 + 1 = 2 | 4 |
| (3,2) | 2 + 1 = 3 | 6 |
| (3,3) | 2 + 2 = 4 | 9 |
| (4,4) | 3 + 3 = 6 | 16 |
| (5,5) | 4 + 4 = 8 | 25 |

Note: For free-edge plates, the nodal pattern is similar but the lines are slightly curved near the edges due to boundary condition effects.

---

## 7. Finite Element Method for Complex Shapes

For plates of non-rectangular, non-circular shape (hexagonal, triangular, irregular panels), the eigenfrequencies and mode shapes cannot be derived analytically. The **Finite Element Method (FEM)** is used instead.

### FEM Discretization

The plate domain is divided into a mesh of small elements (triangular or quadrilateral). Within each element, the displacement is approximated by polynomial basis functions. The global problem becomes a matrix eigenvalue problem:

```
([K] − ω² [M]) {U} = {0}
```

Where:
- `[K]` — global stiffness matrix (assembled from element stiffness matrices)
- `[M]` — global mass matrix (consistent or lumped mass)
- `{U}` — vector of nodal displacements
- `ω` — natural circular frequency

Solving this system yields all eigenvalues ωₙ² (natural frequencies squared) and eigenvectors {U}_n (mode shapes at the mesh nodes). The mode shapes are visualized by plotting the displacement contours — the zero-contour lines are the computational Chladni patterns.

### Mesh Requirements

Accurate FEM modal analysis requires sufficient mesh density. A rule of thumb: at least **6–8 elements per half-wavelength** at the highest frequency of interest. For a 20cm plate with modes up to 5 kHz, this requires elements of approximately 3–5 mm size, yielding ~1500–4000 elements.

---

## 8. Q-Factor of Plate Resonances

### Definition

The **Q-factor** (quality factor) of a plate resonance measures the sharpness of the resonance peak and is directly related to the rate of energy dissipation (damping):

```
Q = f_res / Δf₋₃dB = 2π × (Peak energy) / (Energy dissipated per cycle)
```

Where `Δf₋₃dB` is the 3 dB bandwidth of the resonance peak.

### Physical Interpretation

- **High Q (Q > 100)**: Sharp, narrow resonance. Plate rings for a long time after excitation. Typical of metal plates in air.
- **Low Q (Q < 20)**: Broad, flat resonance. Plate damps quickly. Typical of composite panels, heavily damped structures.

### Decay Time

The free decay of a resonance is:

```
w(t) = A · e^{−πf_res t/Q} · cos(2πf_res t)
```

The time for amplitude to decay to 1/e of initial value:

```
τ = Q / (π · f_res)
```

For a 440 Hz (A4) resonance with Q = 120:
```
τ = 120 / (π × 440) = 0.087 seconds
```

### Typical Q Values by Material and Configuration

| Configuration | Typical Q Range |
|---|---|
| Steel plate in air (thin) | 80–300 |
| Aluminum plate in air | 100–500 |
| Glass plate in air | 150–800 |
| Acrylic plate in air | 20–80 |
| Steel plate with sand load | 40–120 |
| Plate submerged in water | 5–30 |
| Composite (carbon fiber) | 200–1000 |

The sand itself adds mass and damping to the plate, lowering both the resonant frequency and the Q-factor — which is why the pattern sharpens (sand moves more cleanly) at intermediate amplitudes, not maximum amplitude.

---

## 9. Summary: Key Formulas

```
Flexural rigidity:
  D = E h³ / [12(1 − ν²)]

Square plate eigenfrequency (simply-supported):
  f_mn = (π/2) √(D/ρh) (m² + n²) / a²

Circular plate eigenfrequency (free edge):
  f_dn = (k_dn)² / (2π) × √(D/ρh)    where k_dn from Bessel characteristic equation

Wave number:
  k⁴ = ρh ω² / D

Nodal line count (rectangular, simply-supported):
  N_nodal_lines = (m − 1) + (n − 1)

Antinodal region count (rectangular):
  N_antinodes = m × n

Q-factor:
  Q = f_res / Δf₋₃dB

Decay time:
  τ = Q / (π f_res)

Frequency scaling with plate size:
  f ∝ 1/a²   (inversely proportional to area)

Frequency scaling with plate thickness:
  f ∝ h      (proportional to thickness)
```

---

*See also: `../chladni_patterns.json` for measured/computed eigenfrequency data, `historical_context.md` for the mathematical history of plate theory, and `../cymatics/particle_aggregation.md` for the physics of how particles respond to the plate mode shapes.*
