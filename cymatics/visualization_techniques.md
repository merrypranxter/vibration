# Visualization Techniques for Cymatics

A practical guide to setting up, operating, and documenting cymatic experiments — from simple Chladni plate demonstrations to advanced water cymatics and digital simulation.

---

## 1. Traditional Chladni Plate Setup

### Equipment
- **Metal plate**: Steel (preferred) or aluminum, typically 20–40 cm square or circular, 0.5–2 mm thick
- **Support**: Hold the plate at its center (for square plates) or at any nodal point (for circular plates) with a rubber cork or foam pad on a stand. Avoid rigid clamping.
- **Excitation source**: Violin or cello bow (traditional), or piezoelectric transducer bonded to plate underside
- **Particles**: Fine dry sand (125–250 μm), table salt, lycopodium powder, or fine sugar

### Procedure (Bow Excitation)
1. Support the plate horizontally at its center
2. Scatter a thin, even layer of dry sand across the plate surface
3. Press one finger firmly at a specific point on the plate edge (this forces a nodal point at that location, constraining which modes can be excited)
4. Draw the bow across the plate edge at a 90° angle, perpendicular to the plate surface, approximately midway between the support point and the edge
5. Apply steady, moderately fast bow speed with firm pressure
6. A clear tone will emerge when the plate resonates; the sand will immediately begin moving
7. Maintain bowing until the pattern stabilizes (2–10 seconds)
8. Photograph before moving

### Tips for Better Patterns
- **Bow speed and pressure**: Too slow → no sound; too fast → multiple frequencies excited simultaneously → blurry pattern
- **Finger position**: Moving the damping finger to different edge locations selects different resonant modes. Try 1/3, 1/4, 1/2 of the edge length from a corner.
- **Sand amount**: Use the minimum needed for visibility. Excess sand makes patterns sluggish and masks fine details.
- **Plate cleanliness**: Remove oils and dust from the plate surface before adding sand — contamination disrupts particle flow.
- **Humidity**: High humidity causes sand to clump. Use dried sand or work in a dry environment.

---

## 2. CNC/Electronic Frequency Generator Setup

The modern approach: drive the plate with a precision electronic oscillator and speaker or transducer, allowing exact, repeatable frequencies.

### Equipment
- **Signal generator**: Function generator (hardware) or audio software (Audacity, GarageBand, tone generator apps) producing a pure sine wave
- **Amplifier**: Small audio amplifier (10–50 watts), 4–8 ohm speaker output
- **Transducer/speaker**: Attach a small loudspeaker (or piezo disc) to the center underside of the plate with strong epoxy or double-sided tape. Alternatively, use a speaker facing upward with the plate resting on it.
- **Connecting wire**: From signal generator → amplifier → transducer

### Frequency Sweep Method
1. Set up the transducer and plate
2. Scatter particles on the plate
3. Start at a low frequency (e.g., 50 Hz) at moderate amplitude
4. Slowly increase frequency in small steps (1–5 Hz)
5. At each resonant frequency, the amplitude increases dramatically and the pattern snaps into focus
6. Hold the frequency steady and photograph
7. Note: resonant frequencies depend on plate size, thickness, material, and how it's supported

### Finding Resonant Frequencies
- Listen for a noticeable increase in loudness and clarity of the plate tone
- Watch the particles — they suddenly become "alive" and sort themselves rapidly
- Use a spectrum analyzer app (phone) to confirm the dominant frequency
- For systematic work, record the frequencies where clear patterns appear — this is your plate's eigenfrequency map

### Frequency Resolution Required
- Low frequencies (< 200 Hz): ±0.5 Hz resolution sufficient
- Mid frequencies (200–1000 Hz): ±0.2 Hz
- High frequencies (> 1 kHz): ±0.1 Hz
- Very high (> 5 kHz): ±0.05 Hz (very sharp resonances)

### Waveform
Use **pure sine waves** only. Square waves contain odd harmonics (3f, 5f, 7f...) that simultaneously excite multiple modes, blurring patterns. Triangle waves similarly contain harmonics. Pure sine → single-mode excitation → sharp, clean pattern.

---

## 3. Water Surface Cymatics (Faraday Waves)

### Basic Setup
- **Container**: Shallow tray or petri dish, 15–30 cm diameter
- **Water depth**: 3–8 mm (shallow)
- **Platform**: Place the container on a speaker cone (pointing up) or attach to a vibration exciter
- **Illumination**: Light from below (backlit) or raking side illumination to reveal surface topography

### Faraday Wave Behavior
Water cymatics operates via the **Faraday instability** — at a critical amplitude threshold, the flat water surface becomes unstable and spontaneously forms standing surface waves at **half the driving frequency**:

```
Observed pattern frequency = f_drive / 2
```

So driving at 80 Hz → water surface patterns oscillate at 40 Hz. This frequency halving is a key signature of Faraday waves.

### Pattern Types in Water
| Driving Frequency | Typical Pattern | Water Depth | Notes |
|---|---|---|---|
| 10–30 Hz | Large amplitude sloshing | 5–15 mm | Non-Faraday regime |
| 30–60 Hz | Hexagonal cells | 5–10 mm | Classic honey-comb |
| 60–100 Hz | Square lattice | 3–8 mm | Transition zone |
| 100–200 Hz | Stripes or squares | 2–6 mm | Direction sensitive |
| 200–500 Hz | Fine hexagonal or triangular | 1–4 mm | Best photogenic zone |
| > 500 Hz | Very fine, unstable | < 2 mm | Hard to sustain |

### Amplitude Threshold
There is a critical amplitude below which Faraday waves do not form. Just above threshold, the pattern is regular and stationary. Well above threshold, chaos and irregular patterns appear. The best visual patterns appear just 10–30% above the threshold amplitude.

### Water Quality
- Use **distilled water** for the most reproducible results
- Tap water contains surfactants and dissolved gases that alter surface tension, changing pattern wavelength
- A tiny drop of isopropyl alcohol (reduces surface tension) changes the pattern dramatically — a useful variable
- Temperature matters: cooler water has higher surface tension and slightly different pattern scales

---

## 4. Lycopodium Powder

**Lycopodium** (spores of club moss, *Lycopodium clavatum*) is the most sensitive granular material for Chladni experiments. The spores are:
- ~25–35 μm diameter (very fine)
- Hydrophobic — do not clump with humidity
- Near-spherical — flow freely even in thin layers
- Very low density (~0.1 g/cm³ bulk) — respond at very low plate amplitudes
- Electrically slightly charged — slight electrostatic sensitivity

Lycopodium responds to plate vibrations at amplitudes 10–50× lower than sand, making it ideal for:
- High frequencies (> 2 kHz) where plate amplitudes are inherently small
- Fragile plates (glass, acrylic) that cannot be driven at high amplitude
- Very large plates where achieving high amplitude uniformly is difficult

Caution: Lycopodium cloud is a **combustion hazard** — do not use near open flames.

---

## 5. Oil Droplets on Vibrating Surface

### Setup
- Place a thin layer (~0.5 mm) of silicone oil on a smooth plate
- Vibrate at low frequencies (10–80 Hz) with moderate amplitude
- Observe: oil organizes into regular patterns of droplets, waves, and streams

### Phenomena Observed
- **Droplet lattices**: Oil forms regular arrays of droplets separated by thin films
- **Walking droplets**: Individual droplets can "walk" across the surface, propelled by Faraday waves they themselves generate (this is the basis of hydrodynamic quantum analog experiments)
- **Self-organizing ribbons**: At certain frequencies, oil forms ribbon-like streams along nodal lines
- **Toroidal vortices**: In some conditions, circular toroidal vortices form around antinodal points

This technique requires more patience to set up but produces some of the most visually dramatic cymatics effects.

---

## 6. Digital Cymatics (Computer Simulation)

For visualizing patterns at any frequency and any plate geometry without physical equipment.

### Simulation Methods

**Finite Difference Method (FDM)**:
Discretize the biharmonic plate equation on a regular grid. Update plate displacement at each time step using:
```python
w[i,j,t+dt] = 2*w[i,j,t] - w[i,j,t-dt] - (dt²/rho_h) * D * biharmonic(w,i,j,t)
```
Add a damping term `−2ζω₀ ẇ` to model plate losses.

**FEM** (see `../chladni/modal_analysis.md`): Solve the matrix eigenvalue problem for eigenmodes and directly visualize zero-contours of mode shapes.

**Spectral methods**: Expand displacement in Fourier series or Chebyshev polynomials; efficient for simple geometries.

### Software Tools
- **Python + numpy/scipy**: FDM or eigenvalue analysis
- **MATLAB PDE Toolbox**: Plate vibration eigenmodes
- **FEniCS/OpenFOAM**: Full FEM plate modal analysis
- **Processing/p5.js**: Real-time visualization of plate simulations (interactive)
- **TouchDesigner**: Real-time audio-reactive cymatic art generation
- **VCV Rack**: Modular synthesis with visual cymatic output plugins

---

## 7. Photography Tips for Cymatics

### Lighting
- **Raking light** (side illumination at 10–20° to the plate): Creates dramatic shadows that reveal three-dimensional texture of sand patterns. Best for sand/powder on plates.
- **Backlit** (light from below through translucent plate): Works with acrylic plates. Sand appears dark against bright background.
- **Diffuse overhead**: Flat, even illumination. Good for capturing fine detail but loses 3D texture.
- **Colored gels**: Adding a colored filter to the light source gives the pattern a characteristic hue.

### Camera Settings
- **Mode**: Manual or Aperture priority
- **Aperture**: f/8–f/16 for maximum depth of field (pattern can be slightly curved)
- **Shutter**: As fast as possible while maintaining exposure (plate vibrates, but the pattern is static)
- **ISO**: Keep below 400 to minimize noise
- **Focus**: Manual focus on the center of the plate; use live view and zoom in digitally to confirm sharpness
- **White balance**: Set manually to match your light source

### Common Mistakes
- **Camera shake**: Use a tripod and remote shutter release. Vibration from the plate can travel to the camera.
- **Shadows from sand piles**: Sand accumulates in ridges at nodal lines that can cast shadows obscuring fine details. Use two light sources from opposite sides.
- **Overexposure**: Sand reflects light very efficiently. Underexpose by 0.5–1 stop from metering suggestion.
- **Pattern not sharp**: Frequency not exactly at resonance. Fine-tune the frequency by 0.1–0.5 Hz while watching the pattern.

---

## 8. Frequency Calibration Methods

### Tuning Fork Reference
A set of calibrated tuning forks provides reference frequencies to verify signal generator accuracy. Compare the tuning fork frequency (verified with a tuner) against the generator's digital readout.

### Piano / Guitar Tuner App
Smartphone tuner apps measure frequency to ±0.1 Hz accuracy. Place the phone's microphone near the vibrating plate to measure its actual resonant frequency.

### Stroboscope Method
Illuminate the vibrating plate with a strobe light and adjust the strobe frequency until the plate appears stationary. The strobe frequency equals the plate vibration frequency.

### Laser Doppler Vibrometer (LDV)
Professional-grade method: a laser beam reflects off the vibrating plate surface; Doppler shift in the reflected beam directly yields the instantaneous plate velocity. Frequency spectrum analysis gives exact resonant frequencies. LDVs are used in professional modal analysis labs.

---

## 9. Materials Comparison Chart

| Material | Frequency Range | Amplitude Needed | Pattern Clarity | Visual Effect | Best For |
|---|---|---|---|---|---|
| Fine dry sand (125 μm) | 50–1500 Hz | 0.5–2 mm | High | Golden lines | General purpose |
| Table salt | 50–1000 Hz | 0.3–1.5 mm | Very high | White lines | Photography |
| Lycopodium powder | 50–8000 Hz | 0.05–0.5 mm | Very high | Yellow-green haze | High freq / fragile plates |
| Fine sugar | 50–800 Hz | 0.5–2 mm | Medium-high | White granular | Budget option |
| Graphite powder | 100–5000 Hz | 0.1–0.5 mm | High | Dark gray sheen | Dark plate contrast |
| Water (Faraday) | 20–500 Hz | 0.1–1 mm | Medium | Rippled surface | Organic, flowing patterns |
| Cornstarch in water | 20–200 Hz | 0.5–5 mm | Medium | 3D spikes, blobs | Maximum dramatic effect |
| Silicone oil | 10–100 Hz | 0.5–3 mm | Medium | Droplet lattices | Walking droplets |
| Glycerin | 20–200 Hz | 0.3–2 mm | Low-medium | Slow-forming rings | Patience, slow patterns |
| Iron filings | 50–500 Hz | 0.5–2 mm | Low | Fuzzy dark lines | Metallic aesthetic |
| Colored sand | 50–1000 Hz | 0.5–2 mm | High | Colorful lines | Art / display |
| Flour | 50–1000 Hz | 0.3–1.5 mm | High | White dust patterns | Food-safe applications |

---

*See also: `cymatics_materials.json` for physical properties of each material, `particle_aggregation.md` for the underlying physics, and `../chladni/modal_analysis.md` for the plate physics.*
