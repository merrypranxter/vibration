# Vibration & Resonance — Physics Primer

A comprehensive introduction to the physics underlying this database. Covers mechanical oscillation, wave equations, standing waves, resonance, harmonics, damping, Chladni patterns, cymatics, spectral analysis, and psychoacoustics.

---

## 1. What is Vibration?

**Vibration** is the mechanical oscillation of a physical system about an equilibrium position. When an object is displaced from equilibrium and released, restoring forces act to return it — but inertia carries it past equilibrium, creating oscillation.

**Types of vibration:**
- **Free vibration** — object oscillates at its natural frequency after an initial disturbance (a plucked guitar string)
- **Forced vibration** — an external periodic force drives the oscillation (a speaker cone driven by an amplifier)
- **Damped vibration** — energy is dissipated, amplitude decreases over time (a bell ringing and fading)
- **Self-excited vibration** — the system extracts energy from a steady source to sustain oscillation (a violin bow sustaining a string)

**Examples at every scale:**
| Scale | Example | Frequency |
|---|---|---|
| Subatomic | Molecular bond vibration | 10¹² – 10¹⁴ Hz |
| Atomic | Crystal lattice phonons | 10⁹ – 10¹³ Hz |
| Macro | Tuning fork A4 | 440 Hz |
| Human | Vocal cords | 80 – 1100 Hz |
| Geological | Earth's free oscillations | 0.3 – 10 mHz |
| Cosmic | Pulsars | 0.001 – 716 Hz |

---

## 2. Simple Harmonic Motion (SHM)

The simplest form of vibration is **Simple Harmonic Motion (SHM)**, where the restoring force is proportional to displacement:

```
F = −kx
```

Where:
- `F` = restoring force (Newtons)
- `k` = spring constant / stiffness (N/m)
- `x` = displacement from equilibrium (m)

The negative sign indicates the force always opposes displacement.

### Equation of Motion

From Newton's second law (`F = ma = m·d²x/dt²`):

```
m·(d²x/dt²) = −kx
```

Or equivalently:

```
d²x/dt² + ω₀²x = 0
```

Where **ω₀ = √(k/m)** is the angular natural frequency (radians/second).

### Solution

The general solution is sinusoidal:

```
x(t) = A·cos(ω₀t + φ)
```

Where:
- `A` = amplitude (maximum displacement, metres)
- `ω₀` = natural angular frequency = 2πf₀ (rad/s)
- `φ` = phase angle (radians)
- `t` = time (seconds)

---

## 3. Key Parameters

### Frequency (f)
The number of complete oscillation cycles per second. Unit: **Hertz (Hz)**.

```
f = ω₀ / (2π) = 1/T
```

### Period (T)
The time for one complete oscillation cycle. Unit: **seconds (s)** or **milliseconds (ms)**.

```
T = 1/f = 2π/ω₀
```

**Example:** A440 Hz → T = 1/440 = **2.273 ms**

### Angular Frequency (ω)
Frequency expressed in radians per second. Preferred in physics/engineering equations.

```
ω = 2πf    [rad/s]
```

**Example:** A440 → ω = 2π × 440 = **2764.6 rad/s**

### Amplitude (A)
The maximum displacement from equilibrium. Related to energy:

```
E = ½kA² = ½mω₀²A²    [Joules]
```

In acoustics, amplitude corresponds to **sound pressure level (SPL)**, measured in Pascals or decibels (dB SPL).

### Wavelength (λ)
The spatial period of a wave — the distance over which the wave pattern repeats. For a sound wave in air at 20°C (v = 343 m/s):

```
λ = v/f    [metres]
```

**Examples:**
- 20 Hz (lowest hearing limit): λ = 343/20 = **17.15 m**
- 440 Hz (concert A): λ = 343/440 = **0.780 m**
- 20,000 Hz (upper limit): λ = 343/20000 = **0.017 m = 1.7 cm**

---

## 4. The Wave Equation

A mechanical wave in a continuous medium satisfies the **classical wave equation**:

```
∂²y/∂t² = v² · ∂²y/∂x²
```

Where:
- `y(x,t)` = displacement at position x, time t
- `v` = wave propagation speed (m/s)
- The left side = temporal acceleration
- The right side = spatial curvature

### Wave Speed

For different media:

| Medium | Wave Speed Formula | Example |
|---|---|---|
| String | v = √(T/μ) where T=tension, μ=mass/length | Guitar string: ~200–600 m/s |
| Air (sound) | v = √(γP/ρ) ≈ 343 m/s at 20°C | Concert hall acoustics |
| Steel (longitudinal) | v = √(E/ρ) ≈ 5100 m/s | Piano string (bulk) |
| Water | v ≈ 1480 m/s | Underwater acoustics |

**Temperature dependence of sound in air:**
```
v(T) = 331.3 × √(1 + T/273.15)   [m/s, T in °C]
```

### General Solution

The wave equation has solutions of the form:

```
y(x,t) = f(x − vt) + g(x + vt)
```

These represent right-travelling and left-travelling waves respectively. The superposition of these two opposing waves creates **standing waves**.

---

## 5. Standing Waves and Resonance

When a wave reflects back on itself in a bounded medium (a string fixed at both ends, a tube, a room), the forward and reflected waves interfere to create **standing waves** — patterns that appear stationary with fixed nodes and antinodes.

### Nodes and Antinodes

- **Node** — point of zero displacement (destructive interference)
- **Antinode** — point of maximum displacement (constructive interference)

### Resonant Frequencies of a String (Fixed at Both Ends)

For a string of length L, standing wave condition requires an integer number of half-wavelengths:

```
L = n·λₙ/2     →     λₙ = 2L/n
```

Therefore the resonant frequencies are:

```
fₙ = n·v/(2L) = n·f₁    where n = 1, 2, 3, 4, ...
```

- **n=1**: Fundamental frequency (1st harmonic)
- **n=2**: 2nd harmonic (1st overtone) = 2f₁
- **n=3**: 3rd harmonic (2nd overtone) = 3f₁

### Resonance Condition

**Resonance** occurs when a driving frequency matches one of the system's natural frequencies. At resonance:
- Energy transfer from driver to system is maximised
- Amplitude grows dramatically (limited by damping)
- Phase difference between force and displacement is 90°

The resonance response as a function of driving frequency ω:

```
A(ω) = F₀/m / √[(ω₀² − ω²)² + (γω)²]
```

Where γ is the damping coefficient. Maximum amplitude at ω ≈ ω₀.

---

## 6. The Harmonic Series

When a musical instrument vibrates, it simultaneously produces a **fundamental frequency** plus **harmonics** (integer multiples):

```
f₁ (fundamental), f₂ = 2f₁, f₃ = 3f₁, f₄ = 4f₁, ...
```

### Musical Significance of Harmonics

| Harmonic | Ratio to Fundamental | Musical Interval | Example (A=110 Hz) |
|---|---|---|---|
| 1st (fundamental) | 1:1 | Unison | 110 Hz |
| 2nd | 2:1 | Octave | 220 Hz |
| 3rd | 3:1 | Octave + perfect 5th | 330 Hz |
| 4th | 4:1 | Two octaves | 440 Hz |
| 5th | 5:1 | Two octaves + major 3rd | 550 Hz |
| 6th | 6:1 | Two octaves + perfect 5th | 660 Hz |
| 7th | 7:1 | Two octaves + minor 7th (flat) | 770 Hz |
| 8th | 8:1 | Three octaves | 880 Hz |

### Timbre (Tone Colour)

The **relative amplitude of harmonics** determines timbre — why a flute and a violin sound different on the same note:
- **Flute**: strong fundamental, weak upper harmonics → pure, clear
- **Violin**: rich harmonic content including high partials → complex, warm
- **Clarinet**: strong odd harmonics (1st, 3rd, 5th...) due to cylindrical closed bore → hollow, reedy
- **Sawtooth wave** (synthesiser): all harmonics present in equal proportion → harsh, buzzy

### Inharmonicity

In real-world instruments (especially piano), high harmonics deviate from exact integer multiples due to **stiffness** of the vibrating medium. This **inharmonicity** increases with frequency and is a key factor in piano tuning (octave stretch).

---

## 7. Q-Factor and Damping

### Damping

In real systems, vibration energy is dissipated through friction, air resistance, and material hysteresis. Damped oscillation:

```
x(t) = A₀·e^(−γt/2) · cos(ω_d·t + φ)
```

Where:
- `γ` = damping coefficient (s⁻¹)
- `ω_d = √(ω₀² − γ²/4)` = damped natural frequency
- `A₀·e^(−γt/2)` = exponentially decaying envelope

### Damping Ratio (ζ)

```
ζ = γ / (2ω₀) = c / (2√(km))
```

- **ζ < 1**: Underdamped — oscillates with decreasing amplitude (most musical instruments)
- **ζ = 1**: Critically damped — returns to equilibrium fastest without oscillating
- **ζ > 1**: Overdamped — returns to equilibrium slowly without oscillating

### Q-Factor (Quality Factor)

The Q-factor measures how "sharp" or "pure" a resonance is:

```
Q = ω₀ / Δω = f₀ / Δf = 1/(2ζ) = energy stored / energy dissipated per cycle × 2π
```

Where Δf is the bandwidth at the -3dB points of the resonance peak.

| Q Value | Description | Example |
|---|---|---|
| Q = 0.5 | Critically damped | Shock absorber |
| Q = 1–5 | Highly damped | Car body panels |
| Q = 10–100 | Moderate Q | Musical instruments |
| Q = 100–10,000 | High Q | Bells, tuning forks |
| Q = 10,000–10⁶ | Very high Q | Quartz crystals |
| Q > 10⁶ | Ultra-high Q | Atomic clocks, optical cavities |

**Practical meaning:** A 440 Hz tuning fork with Q = 5,000 has a resonance bandwidth of 440/5000 = 0.088 Hz — it's extremely selective. A guitar body with Q = 30 has a broad resonance peak spanning ~15 Hz.

---

## 8. Chladni Patterns

**Ernst Chladni** (1756–1827), German physicist called "the father of acoustics," discovered that scattering sand on a vibrating plate and drawing a violin bow along its edge created beautiful geometric patterns. These patterns reveal the **nodal lines** — regions of zero vibration.

### How Chladni Patterns Form

1. Sand is sprinkled uniformly on a rigid plate (metal, glass, wood)
2. The plate is driven at a specific resonant frequency (bow, speaker, or vibration exciter)
3. Sand migrates away from vibrating antinodes toward stationary nodes
4. Sand accumulates along nodal lines, revealing the mode shape

### Mode Shapes and Mathematics

For a square plate of side L, the mode frequencies are approximately:

```
f(m,n) = (π/2) · (D/ρh)^(1/2) · [(m/a)² + (n/b)²]
```

Where:
- m, n = mode numbers (integers)
- D = plate flexural rigidity
- ρ = material density
- h = plate thickness
- a, b = plate dimensions

The nodal patterns for rectangular plates are described by:

```
y(x,y) = sin(mπx/a) · sin(nπy/b)
```

### Pattern Complexity

As frequency increases, Chladni patterns become more complex:
- **Simple modes** (low frequency): 2–4 nodal lines, simple symmetry
- **Medium modes**: Star patterns, cross patterns, concentric structures
- **High modes**: Intricate lattices, fractal-like complexity

### Symmetry

Patterns possess the same symmetry as the plate:
- Circular plate → rotational symmetry
- Square plate → 4-fold symmetry
- Irregular plate → complex asymmetric patterns

### Dimensional Scaling

Higher frequency → shorter wavelength → finer nodal patterns. The characteristic scale of a Chladni pattern in a plate of size L driven at frequency f is approximately:

```
pattern_scale ≈ v_plate / (2f)
```

---

## 9. Cymatics

**Cymatics** (from Greek *kyma* = wave) is the broader study of visible sound and vibration effects. Coined by **Hans Jenny** (1904–1972), Swiss physician and artist, who published two landmark volumes (1967, 1974).

### Cymatic Media

Different media reveal different aspects of vibration:

| Medium | Effect Revealed | Best Frequency Range |
|---|---|---|
| Dry sand on plate | Nodal lines (Chladni) | 100–5,000 Hz |
| Fine salt | Finer detail nodal patterns | 200–10,000 Hz |
| Iron filings | Nodal lines with magnetic coupling | 50–2,000 Hz |
| Water surface | Interfering wave rings (Faraday waves above threshold) | 1–500 Hz |
| Cornstarch slurry | Non-Newtonian standing structures | 10–100 Hz |
| Lycopodium powder | Antinodal concentration | 20–5,000 Hz |
| Tone on CRT oscilloscope | Lissajous figures (2D frequency ratios) | Any |

### Faraday Waves

At sufficient driving amplitude, a fluid surface breaks into **Faraday instability waves** — regular, subharmonic standing wave patterns at half the driving frequency:

```
f_pattern = f_drive / 2
```

The wavelength follows the **capillary-gravity wave dispersion relation**.

### Cymatic Observations

- Higher frequencies produce finer, more complex patterns
- Harmonic relationships (octaves, fifths) produce visually "harmonious" patterns
- Dissonant frequency relationships produce asymmetric or chaotic patterns
- The same frequency in different media produces different but geometrically related patterns

### Connection to Nature

Cymatic patterns appear throughout nature:
- Sand ripples on beaches and dunes (wind forcing)
- Barchan dunes (aeolian standing waves)
- Zebra stripes and leopard spots (Turing reaction-diffusion, mathematically equivalent)
- Radiolarian skeletons (growth under vibrational templates)
- Snowflake structure (hexagonal symmetry from molecular vibration)
- Sunflower seed spirals (Fibonacci standing wave intersections)

---

## 10. Spectrogram and FFT Analysis

### Fourier Analysis

Any periodic signal can be decomposed into a sum of sinusoids (**Fourier series**):

```
x(t) = a₀ + Σ[n=1 to ∞] (aₙcos(nω₀t) + bₙsin(nω₀t))
```

This is fundamental to all audio analysis — every complex sound is a superposition of pure frequencies.

### Fast Fourier Transform (FFT)

The **FFT** is an efficient algorithm to compute the **Discrete Fourier Transform (DFT)** of a digital signal, converting from the time domain to the frequency domain:

```
X[k] = Σ[n=0 to N-1] x[n] · e^(−j2πkn/N)
```

- Input: N time-domain samples at sampling rate fs
- Output: N/2 frequency bins from 0 to fs/2 (Nyquist frequency)
- Frequency resolution: Δf = fs/N
- Time-frequency uncertainty: Δt·Δf ≥ 1/(4π) (Heisenberg-Gabor limit)

### Short-Time Fourier Transform (STFT) & Spectrogram

A **spectrogram** is computed by applying the FFT to successive overlapping short windows of a signal:

```
STFT{x}(t,ω) = ∫ x(τ) · w(τ−t) · e^(−jωτ) dτ
```

Where w(t) is a window function (Hann, Hamming, Blackman, etc.).

**Spectrogram axes:**
- **X-axis**: Time
- **Y-axis**: Frequency
- **Colour/brightness**: Amplitude (usually in dB)

**Reading a spectrogram:**
- Horizontal lines = sustained tones
- Vertical lines = transients (click, impulse)
- Diagonal lines = frequency sweeps (chirps)
- Complex texture = noise or chaotic signals

### Mel Scale

The **Mel scale** is a perceptual frequency scale based on human pitch perception:

```
m = 2595 · log₁₀(1 + f/700)
```

Used in speech recognition and music information retrieval. Humans are more sensitive to frequency differences in the lower range.

---

## 11. Human Hearing Range

### Audible Range
The human ear responds to:
- **Lower limit**: ~20 Hz (perceived as rumble or pulse, not a clear pitch)
- **Upper limit**: ~20,000 Hz (decreases with age)

### Frequency Resolution

The ear's frequency resolution follows the **Weber-Fechner law** — discrimination is roughly proportional to frequency (constant relative resolution):
- At 1,000 Hz: can distinguish ~3 Hz difference
- At 10,000 Hz: can distinguish ~30 Hz difference
- Equals approximately 3 cents of pitch resolution for trained listeners

### Equal Loudness Contours (Fletcher-Munson Curves)

The **Fletcher-Munson curves** (1933), updated as the **ISO 226** equal loudness contours, show that perceived loudness varies dramatically with frequency:

- **Maximum sensitivity**: 2,000–5,000 Hz (peak near 3,500 Hz)
- **Dip in sensitivity**: below 500 Hz and above 8,000 Hz
- **Implication**: A 40 Hz tone must be ~30 dB louder than a 3,000 Hz tone to sound equally loud at 60 phon

```
Loudness Level (phon) ≠ Sound Pressure Level (dB SPL) — except at 1 kHz
```

### The Ear as a Spectrum Analyser

The cochlea performs a real-time frequency analysis:
- ~3,500 outer hair cells act as active resonators (prestin motor protein)
- Basilar membrane is tonotopically mapped: base → high frequencies, apex → low
- Frequency resolution: ~3,500 channels, each ~0.2 mm wide on basilar membrane
- Dynamic range: 0–140 dB SPL (10⁷ in amplitude, 10¹⁴ in intensity)

---

## 12. Psychoacoustics Summary

| Perceptual Effect | Physical Cause | Example |
|---|---|---|
| **Pitch** | Frequency | A4 = 440 Hz sounds "higher" than A3 = 220 Hz |
| **Loudness** | Sound Pressure Level (SPL) | 0 dB SPL (threshold) to 130 dB SPL (pain) |
| **Timbre** | Harmonic spectrum + envelope | Flute vs violin on same note |
| **Masking** | Strong tone masks nearby weaker tone | Bass obscures low-mid frequencies |
| **Beats** | Two close frequencies → amplitude modulation | 440 + 444 Hz → 4 Hz beats |
| **Critical bands** | Cochlear frequency grouping ~1/3 octave | Dissonance detection |
| **Missing fundamental** | Brain infers fundamental from harmonics | Bass reproduction in small speakers |
| **Binaural beat** | Different freq each ear → perceived beat | 200 Hz L + 210 Hz R → 10 Hz beat |
| **Cocktail party effect** | Auditory scene analysis | Focusing on one voice in crowd |
| **Haas effect** | First-arrival dominates localization | Within 35ms, earlier sound localizes |

---

## Further Reading

- **Chladni, E.F.F.** (1787). *Entdeckungen über die Theorie des Klanges*. Leipzig.
- **Jenny, H.** (1967, 1974). *Cymatics*, Vols. 1 & 2. Basilius Press.
- **Fletcher, H., & Munson, W.A.** (1933). Loudness, its definition, measurement and calculation. *JASA*, 5(2).
- **Morse, P.M.** (1948). *Vibration and Sound*. McGraw-Hill.
- **French, A.P.** (1971). *Vibrations and Waves*. MIT Introductory Physics Series.
- **Rossing, T.D.** (2007). *The Science of Sound*, 3rd Ed. Addison-Wesley.
- **Leissa, A.W.** (1969). Vibration of Plates. NASA SP-160.
- **Zwicker, E., & Fastl, H.** (2007). *Psychoacoustics: Facts and Models*, 3rd Ed. Springer.
