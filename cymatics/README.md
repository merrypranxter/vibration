# Cymatics

**Cymatics** is the study of visible sound — the science and art of making acoustic vibrations manifest as visible patterns in matter. The word derives from the Greek *kyma* (κῦμα), meaning "wave," and was coined by Swiss physician and natural scientist **Hans Jenny** in his 1967 monograph *Kymatik* (published in English as *Cymatics*).

Where Chladni patterns (see `../chladni/README.md`) reveal the nodal geometry of vibrating *solid plates* using dry powder, cymatics encompasses a broader family of phenomena: vibrating liquids, fluid surfaces, pastes, and granular materials — each responding to sound in distinct and visually remarkable ways.

---

## What Is Cymatics?

At its core, cymatics is the observation that **acoustic energy organizes matter into structured patterns**. When a medium — whether a thin film of water, a paste of cornstarch, a layer of sand, or a pool of oil — is subjected to a sustained periodic vibration, it does not respond uniformly. It self-organizes into regular geometric forms that reflect the frequency, amplitude, and spatial mode of the driving vibration.

These patterns are not random. They are highly reproducible: the same frequency applied to the same medium on the same plate will produce the same pattern every time. This reproducibility is a key feature that distinguishes cymatics from mere visual noise.

---

## Hans Jenny and the Birth of Modern Cymatics (1967)

**Hans Jenny** (1904–1972) was a Swiss physician, natural scientist, and artist who spent decades systematically documenting the effects of sound vibrations on various materials. Inspired by the earlier work of Ernst Chladni and later by Rudolf Steiner's anthroposophical ideas about the formative forces of sound, Jenny built a device called the **tonoscope** — a metal plate connected to an oscillator that could be driven at precise, controlled frequencies.

Jenny's key contributions:
- Systematic photography and film documentation of cymatic patterns across hundreds of frequencies
- Extension of Chladni's dry-plate experiments to liquids, gels, powders, and colloidal suspensions
- Publication of *Kymatik* (1967, 1972), the foundational text of the field
- Demonstration that **vowel sounds spoken into the tonoscope** produced characteristic patterns — "O" produced a circle, "A" an X-shape — linking language, sound, and form

Jenny's work ignited both scientific interest and artistic fascination, establishing cymatics as a bridge between physics, art, and philosophy.

---

## Different Materials and Their Responses

One of cymatics' richest dimensions is the diversity of materials and their dramatically different responses to vibration:

### Granular Materials (Dry)
- **Sand, salt, sugar**: Migrate to nodal lines, producing sharp-edged geometric patterns (classic Chladni figures)
- **Lycopodium powder**: Extremely fine and light; responds to very low amplitudes and very high frequencies
- **Iron filings**: Align with acoustic radiation pressure, showing field lines
- **Graphite powder**: Produces very fine, high-resolution nodal maps

### Fluids
- **Water**: Creates **Faraday waves** — standing surface waves with half the driving frequency, forming checkerboard and hexagonal patterns
- **Glycerin/oil**: More viscous fluids produce slower-evolving, more stable patterns
- **Ferrofluid**: Under combined acoustic and magnetic fields, produces intricate spike patterns

### Non-Newtonian Fluids
- **Cornstarch suspension (Oobleck)**: Shear-thickening fluid that forms bizarre standing fingers, columns, and blobs — the most dramatic visual effect in cymatics

---

## The Physics of Particle Aggregation at Nodes

### Why Do Particles Move to Nodal Lines?

Acoustic radiation pressure (the Gor'kov potential) pushes particles to regions of minimum acoustic energy density. In a standing wave, these minima occur at the nodal planes/lines. Small particles with density greater than the surrounding medium accumulate at nodal lines; particles less dense than the medium (e.g., air bubbles) accumulate at antinodes.

### Faraday Waves (Fluid Cymatics)

When a liquid surface is driven vertically at frequency `f`, above a threshold amplitude it becomes **parametrically unstable**. The surface spontaneously forms standing waves at frequency `f/2`. These are **Faraday waves**, first described by Michael Faraday in 1831. The wave pattern reflects the symmetry of the container and the driving frequency, producing hexagonal, square, or stripe patterns depending on parameters.

The Faraday instability threshold and pattern wavelength are governed by:
```
λ_Faraday = 2π √(σ / ρ(2πf/2)²)   [capillary regime, shallow fluid]
```
Where `σ` is surface tension and `ρ` is fluid density.

---

## Chladni vs. Cymatics: Key Differences

| Feature | Chladni (Dry) | Cymatics (Wet/Fluid) |
|---|---|---|
| Medium | Dry granular powder | Liquid, paste, or gel |
| Mechanism | Particle bouncing + radiation pressure | Faraday instability + surface tension |
| Pattern type | Nodal line accumulation | Surface wave standing patterns |
| Frequency half-effect | No | Yes (Faraday: patterns at f/2) |
| Visual character | Sharp geometric lines | Wave-like, organic, flowing |
| Amplitude sensitivity | High amplitude needed | Works at very low amplitudes (water) |
| Reproducibility | Very high | High (water slightly less so) |
| Best for | Mapping nodal geometry | Organic, biological-looking forms |

---

## Files in This Section

| File | Description |
|---|---|
| `README.md` | This file — overview and index |
| `particle_aggregation.md` | Physics of acoustic radiation pressure and nodal accumulation |
| `visualization_techniques.md` | Practical guide to cymatic setups, equipment, and photography |
| `cymatics_materials.json` | 11-material dataset with physical properties and pattern characteristics |
| `cymatics_patterns.json` | 32-pattern catalog with descriptions, palettes, and art prompts |
| `material_properties.json` | Detailed physics properties (density, viscosity, surface tension) per material |

---

## The Relationship Between Sound and Form

Cymatics reveals a deep principle: **wave interference patterns encode geometric information**. The same mathematical structures that appear in cymatic patterns — hexagonal close-packing, Bessel function zeros, Lissajous curves — appear throughout nature, from soap bubble arrays to cell division to galaxy spiral arms. Whether this reflects a deep connection between vibration and biological form (as Jenny believed) or simply reflects the universality of the wave equation is still debated.

What is undeniable is that cymatics is a uniquely compelling window into the hidden spatial structure of sound.

---

*See also: `../chladni/README.md` for dry-plate Chladni patterns and `../VIBRATION_PHYSICS_PRIMER.md` for foundational wave mechanics.*
