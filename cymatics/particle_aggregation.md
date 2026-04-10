# Particle Aggregation at Nodal Lines: The Physics

This document covers the physical mechanisms by which particles, powders, and fluids organize themselves into visible patterns under acoustic excitation — the underlying physics of both Chladni patterns and wet cymatics.

---

## 1. Overview: Why Particles Move to Nodal Lines

When a plate vibrates in a specific eigenmode, a spatially non-uniform acoustic field is created above (and within) the plate surface. Particles resting on the plate experience:

1. **Direct mechanical kicks** from the oscillating plate surface (dominant for coarse particles)
2. **Acoustic radiation pressure** from the standing wave field (dominant for fine particles and in fluid media)
3. **Acoustic streaming** — steady secondary flows induced by viscosity in the acoustic field
4. **Surface tension effects** — critical for fluid cymatics

All four mechanisms act simultaneously, and their relative importance depends on particle size, frequency, amplitude, and medium.

---

## 2. Acoustic Radiation Pressure (Gor'kov Theory)

### The Radiation Force

In a standing acoustic wave, a small particle experiences a net **radiation force** directed toward regions of minimum acoustic energy. This was rigorously derived by L.P. Gor'kov in 1962.

For a small spherical particle in an acoustic standing wave, the radiation force potential is:

```
U = (4π a³/3) × [f₁ × p̄² / (2ρ₀c₀²) − f₂ × ρ₀ v̄² / 2]
```

Where:
- `a` — particle radius
- `p̄²` — time-averaged acoustic pressure amplitude squared
- `v̄²` — time-averaged acoustic velocity amplitude squared
- `ρ₀, c₀` — density and sound speed of medium
- `f₁, f₂` — contrast factors depending on particle vs. medium density and compressibility

The force on the particle is: `F = −∇U`

### Contrast Factors

```
f₁ = 1 − (ρ₀ c₀²) / (ρ_p c_p²)    [compressibility contrast]
f₂ = 2(ρ_p − ρ₀) / (2ρ_p + ρ₀)   [density contrast]
```

Where `ρ_p, c_p` are the particle density and sound speed.

### Critical Result: Direction of Particle Migration

- If `f₂ > 0` (particle denser than medium): particles accumulate at **pressure nodes** (velocity antinodes)
- If `f₂ < 0` (particle less dense than medium): particles accumulate at **pressure antinodes** (velocity nodes)

For **solid particles in air** (e.g., sand on a plate in air):
- Sand is far denser than air: `ρ_sand ≈ 2650 kg/m³`, `ρ_air ≈ 1.2 kg/m³`
- f₂ ≈ +2/3 (strongly positive)
- → Sand migrates to **pressure nodes** = **displacement antinodes**

Wait — this seems backward from observation! Sand visibly collects at nodal lines, not antinodes.

**Resolution**: The relevant force for plate-bound particles is not the bulk acoustic radiation force but the **plate surface acoustic wave (SAW) radiation pressure**, which pushes particles toward the **displacement nodes** of the plate. At the plate surface:
- Displacement nodes = points of zero plate vibration = where sand accumulates ✓
- Displacement antinodes = points of maximum plate vibration = where sand is bounced away ✓

The bulk acoustic radiation theory (Gor'kov) applies to particles **suspended in a fluid medium** (as in acoustic levitation or fluid cymatics), while **direct plate impact** is dominant for dry granular materials on the plate surface.

---

## 3. Direct Plate Impact Mechanism (Dry Granular Particles)

For sand or powder resting on a vibrating plate, the dominant mechanism is straightforward mechanical:

### Bouncing at Antinodes

At an antinode, the plate surface moves up and down with amplitude `A` at frequency `f`. The peak plate acceleration is:

```
a_max = (2πf)² × A
```

When this exceeds gravitational acceleration `g = 9.81 m/s²`, particles are **launched off the plate surface**:

```
Condition for particle launch:   (2πf)² × A > g
Critical amplitude:              A_launch = g / (2πf)²
```

At 440 Hz: `A_launch = 9.81 / (2π × 440)² = 9.81 / 7,669,000 ≈ 1.3 μm`

Sand grains launched at antinodes follow ballistic trajectories and land nearby. Repeated impacts create a net drift of particles toward the adjacent nodal lines. Once at a nodal line (zero displacement), particles experience no launch force and remain stationary.

### Statistical Drift Model

The net particle drift toward nodal lines can be modeled as a biased random walk:
- Particles at antinodes are launched with a random horizontal velocity component
- They land at a random nearby position
- Statistical symmetry means they are equally likely to land closer to or farther from the nearest nodal line — BUT the mean free path before the next bounce is shorter near antinodes
- Net effect: particles execute a slow but persistent drift toward nodal lines

The drift velocity scales approximately as `A² × f³` — faster pattern formation at higher amplitude and frequency (up to the point where particles become completely airborne).

---

## 4. Bernoulli Effect in Acoustic Fields

In oscillating fluid systems (fluid cymatics), the **Bernoulli effect** contributes to pattern formation. In regions of high acoustic velocity, the pressure is lower (Bernoulli's principle). Fluid particles and suspended solids are therefore pushed from high-velocity regions toward low-velocity regions.

This is related to the radiation pressure mechanism but operates through a different physical pathway — the time-averaged static pressure gradient rather than the instantaneous force.

For thin fluid films on vibrating plates, the Bernoulli contribution to particle drift is:

```
ΔP_Bernoulli = −ρ_fluid × v̄²_acoustic / 2
```

Where `v̄²_acoustic` is the root-mean-square acoustic velocity. Particles in the fluid film experience a net pressure force toward velocity nodes (pressure antinodes), which correspond to displacement nodes on the plate.

---

## 5. Acoustic Streaming

**Acoustic streaming** is a steady, time-averaged fluid flow induced by the absorption of acoustic energy in a viscous fluid. Discovered by Lord Rayleigh (1883), it occurs because the dissipative (viscous) forces in an acoustic wave create a small but persistent secondary flow.

### Types of Acoustic Streaming

1. **Eckart streaming** (quartz wind): Bulk fluid streaming along the direction of acoustic propagation; important in focused acoustic beams
2. **Rayleigh streaming**: Recirculating flow cells near boundaries in standing waves; creates counter-rotating vortex pairs
3. **Schlichting streaming**: Very thin vortex cells at the acoustic boundary layer; strongest near plate surfaces

### Relevance to Cymatics

In fluid cymatics (water surface, oil layer), Rayleigh streaming creates recirculating flow cells whose boundaries correspond to the acoustic nodal lines. These flow cells:
- Sweep suspended particles toward their centers (which coincide with nodal regions)
- Are visible as organized swirling motion in the fluid before the final static pattern establishes
- Explain why water cymatics patterns sometimes show spiral arms converging on nodal lines

The streaming velocity scales as: `v_streaming ∝ A² ω² / ν` where `ν` is the kinematic viscosity.

---

## 6. Surface Tension Effects in Fluid Cymatics

### Role of Surface Tension

In water cymatics (thin water film or Faraday waves), **surface tension** plays a crucial role:

1. **Restoring force**: Surface tension provides one of the restoring forces for surface capillary waves (alongside gravity). The dispersion relation for capillary-gravity waves is:
   ```
   ω² = (g k + σ k³ / ρ) × tanh(kh)
   ```
   Where `σ` is surface tension, `k = 2π/λ` is wavenumber, `h` is fluid depth.

2. **Faraday wave wavelength**: The wavelength of Faraday patterns is set by the capillary-gravity dispersion relation at half the driving frequency:
   ```
   λ_Faraday ≈ 2π [σ / (ρ (πf)²)]^{1/3}   [capillary-dominated regime]
   ```

3. **Contamination sensitivity**: Surface tension is extremely sensitive to surface contaminants (oils, detergents). A small amount of soap can completely change the Faraday wave pattern by altering the effective surface tension.

4. **Contact angle effects**: Where the fluid meets the plate edge, the contact angle determines the boundary condition for the surface wave and affects the pattern at the periphery.

### Surface Tension Values

| Fluid | Surface Tension σ (mN/m) at 20°C |
|---|---|
| Water (pure) | 72.8 |
| Water + surfactant | 25–40 |
| Glycerin | 63.0 |
| Ethanol | 22.3 |
| Mercury | 485 |
| Castor oil | 35.0 |

---

## 7. Particle Size Effects on Pattern Formation

Particle size has a profound influence on which mechanism dominates and how sharply patterns form:

### Fine Powder (< 50 μm): Lycopodium, Graphite

- Responds to radiation pressure effects directly from the acoustic field above the plate
- Can detect very low amplitude vibrations (responds to the near field, not just plate contact)
- At very fine sizes (< 5 μm), particles become aerosols and can exhibit **levitation** between pressure nodes
- Forms extremely sharp, fine nodal lines
- Sensitive to air currents — experimental setup must minimize drafts

### Medium Powder (50–250 μm): Fine Sand, Salt, Sugar

- Dominated by direct plate impact (launch and landing)
- Classic Chladni pattern material
- Optimal balance of sensitivity and stability
- Pattern forms quickly (seconds at resonance)
- Less sensitive to air disturbances

### Coarse Sand (250 μm – 2 mm)

- Launch mechanism still operative but requires higher plate amplitude
- Patterns take longer to develop
- Nodal lines are thicker/blurrier due to particle size
- Less sensitive to higher frequencies (launch force decreases as amplitude needed for clarity increases)

### Fluids

- Respond via Faraday instability (subharmonic surface waves)
- Patterns appear at half the driving frequency
- Pattern wavelength is set by surface tension and fluid properties
- Can visualize much lower amplitude vibrations than dry particles

---

## 8. Reynolds Number in Cymatics

The **Reynolds number** characterizes the ratio of inertial to viscous forces in the streaming flow created by acoustic excitation:

```
Re = v_streaming × L / ν
```

Where `L` is the pattern wavelength and `ν` is kinematic viscosity.

For water cymatics at 100 Hz:
- Streaming velocity: ~0.1 mm/s
- Pattern wavelength: ~10 mm
- Kinematic viscosity of water: 1.0 × 10⁻⁶ m²/s
- Re ≈ 0.1 × 10⁻³ × 10 × 10⁻³ / 10⁻⁶ = 1.0

This low Reynolds number (Re ≈ 1) means acoustic streaming in cymatics operates in the **viscous (Stokes) flow regime**, where viscous forces dominate inertia. This explains why cymatic patterns are stable and well-defined rather than turbulent.

At very high amplitudes or in low-viscosity fluids, Re can exceed 100, leading to turbulent secondary flows that destroy pattern clarity.

---

## 9. Wave Superposition and Complex Patterns

### Superposition of Degenerate Modes

As discussed in `../chladni/modal_analysis.md`, square plates have degenerate modes — (m,n) and (n,m) with m≠n occur at the same frequency. When the plate is driven at a degenerate frequency, both modes are simultaneously excited.

If the amplitudes are A₁ and A₂ with relative phase φ:

```
W(x,y) = A₁ sin(mπx/a)sin(nπy/a) + A₂ sin(nπx/a)sin(mπy/a) e^{iφ}
```

For A₁ = A₂ and φ = 0 (symmetric superposition):
```
W(x,y) ∝ sin(mπx/a)sin(nπy/a) + sin(nπx/a)sin(mπy/a)
```
This produces diagonal nodal patterns — the familiar "X" or star-like figures in Chladni's catalog.

For A₁ = A₂ and φ = π/2 (antisymmetric superposition):
```
W(x,y) ∝ sin(mπx/a)sin(nπy/a) − sin(nπx/a)sin(mπy/a)  [×i factor]
```

The resulting nodal pattern is rotated 45° from the symmetric case.

This mode superposition is why many Chladni figures appear rotated by multiples of 45°, depending on where the bow is applied (which selects the relative phase of the two degenerate modes).

---

## 10. Energy Density and Nodal Geometry

The acoustic energy density in a standing wave is:

```
E_acoustic = ⟨p²⟩/(2ρ₀c₀²) + ρ₀⟨v²⟩/2
```

At nodal lines of the plate:
- Plate displacement = 0
- Plate velocity = 0
- Local acoustic energy density ≈ minimum

At antinodal regions:
- Plate displacement = maximum
- Plate velocity = maximum
- Local acoustic energy density = maximum

The Gor'kov potential is proportional to the local acoustic energy density. Particles with positive acoustic contrast (denser than medium) move down the energy gradient — from antinodes to nodes. This is the fundamental reason why **high-density particles always accumulate at nodal lines**.

---

*See also: `../chladni/modal_analysis.md` for the plate physics, `visualization_techniques.md` for practical setup guides, and `cymatics_materials.json` for material-specific aggregation behavior.*
