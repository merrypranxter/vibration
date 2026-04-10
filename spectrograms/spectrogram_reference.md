# Spectrogram Technical Reference

A comprehensive mathematical and technical reference for spectrogram generation, analysis, and interpretation.

---

## 1. Fourier Transform

### Continuous Fourier Transform
```
F(ω) = ∫₋∞^∞ f(t) · e^(-iωt) dt

Inverse:
f(t) = (1/2π) ∫₋∞^∞ F(ω) · e^(iωt) dω
```

- `f(t)` — signal in time domain
- `F(ω)` — signal in frequency domain (complex)
- `ω = 2πf` — angular frequency (radians/sec)
- `e^(-iωt) = cos(ωt) - i·sin(ωt)` — Euler's formula basis

### Properties
| Property | Formula | Meaning |
|---|---|---|
| Linearity | F{af + bg} = aF + bG | Superposition |
| Time shift | F{f(t-t₀)} = e^(-iωt₀)·F(ω) | Phase shift |
| Frequency shift | F{e^(iω₀t)·f(t)} = F(ω-ω₀) | Modulation |
| Convolution | F{f * g} = F(ω)·G(ω) | Convolution = multiplication |
| Parseval's theorem | ∫|f(t)|²dt = (1/2π)∫|F(ω)|²dω | Energy conservation |

---

## 2. Discrete Fourier Transform (DFT)

For a discrete signal x[n] of length N:

```
X[k] = Σₙ₌₀^(N-1) x[n] · e^(-i·2πkn/N)    k = 0, 1, ..., N-1

Inverse DFT:
x[n] = (1/N) Σₖ₌₀^(N-1) X[k] · e^(i·2πkn/N)
```

- **k** — frequency bin index (0 to N-1)
- **Frequency resolution** = f_s / N (Hz per bin)
- **Nyquist limit** = f_s / 2 (maximum unaliased frequency)
- **Bin k corresponds to frequency** = k · f_s / N Hz

### DFT Output Interpretation
For a real-valued input signal:
- Bins 0 to N/2 — positive frequencies (0 Hz to Nyquist)
- Bins N/2 to N-1 — mirror image (negative frequencies, redundant)
- Bin 0 — DC component (mean value)
- Bin N/2 — Nyquist frequency

---

## 3. Fast Fourier Transform (FFT)

The Cooley-Tukey FFT algorithm (1965) computes the DFT in **O(N log N)** rather than O(N²) by exploiting symmetry:

### Radix-2 Decimation-in-Time (DIT)
```
X[k] = Σ_{n even} x[n]·W_N^(kn) + W_N^k · Σ_{n odd} x[n]·W_N^(kn)

Where W_N = e^(-i·2π/N) is the twiddle factor
```

The signal is recursively split into even/odd samples until 2-point DFTs remain. Requires N to be a power of 2 (or zero-padded to the next power of 2).

### Computational Cost
| Size N | DFT ops | FFT ops | Speedup |
|---|---|---|---|
| 64 | 4,096 | 384 | 10.7× |
| 1,024 | 1,048,576 | 10,240 | 102× |
| 4,096 | 16,777,216 | 49,152 | 341× |
| 65,536 | 4.3 billion | 1,048,576 | 4,096× |

---

## 4. Short-Time Fourier Transform (STFT)

```
STFT{x}(m, ω) = Σ_n x[n] · w[n - m] · e^(-iωn)
```

- `x[n]` — input signal
- `w[n]` — window function
- `m` — frame index (time position)
- Spectrogram = |STFT{x}(m, ω)|²

### Parameters
| Parameter | Typical Range | Effect |
|---|---|---|
| **FFT size (N)** | 256–8192 | ↑N = ↑freq resolution, ↓time resolution |
| **Hop size (H)** | N/4 to N/2 | Smaller = smoother, more overlap |
| **Overlap %** | 50–75% | Higher = better time localization display |
| **Sample rate (fs)** | 8–192 kHz | Sets frequency range (0 to fs/2) |

### Output Dimensions
```
Time frames = floor((signal_length - N) / H) + 1
Frequency bins = N/2 + 1
Spectrogram shape = (N/2 + 1) × time_frames
```

---

## 5. Window Functions

Window functions taper the signal at frame edges to reduce spectral leakage.

### Hann Window (most common)
```
w[n] = 0.5 · (1 - cos(2πn / (N-1)))
```
- Excellent sidelobe suppression (-31.5 dB)
- Good frequency resolution
- Best general-purpose choice

### Hamming Window
```
w[n] = 0.54 - 0.46 · cos(2πn / (N-1))
```
- Slightly less sidelobe suppression than Hann (-42.5 dB)
- Marginally better main lobe resolution
- Common in speech processing

### Blackman Window
```
w[n] = 0.42 - 0.5·cos(2πn/(N-1)) + 0.08·cos(4πn/(N-1))
```
- Very low sidelobes (-58.1 dB)
- Wider main lobe (lower frequency resolution)
- Good for separating closely spaced tones of different amplitudes

### Kaiser Window
```
w[n] = I₀(β·√(1 - (2n/N-1)²)) / I₀(β)
```
- `I₀` = modified Bessel function of order zero
- `β` controls sidelobe level (β=0 → rectangular, β=8.6 → ~Blackman)
- Tunable tradeoff between main lobe width and sidelobe level

### Flat-Top Window
```
w[n] = a₀ - a₁·cos(2πn/N) + a₂·cos(4πn/N) - a₃·cos(6πn/N) + a₄·cos(8πn/N)
a = [0.21557895, 0.41663158, 0.277263158, 0.083578947, 0.006947368]
```
- Minimal amplitude measurement error
- Poor frequency resolution
- Used for amplitude calibration

### Window Comparison
| Window | Main Lobe Width | Peak Sidelobe (dB) | Amplitude Accuracy |
|---|---|---|---|
| Rectangular | 2 bins | -13 | Poor |
| Hann | 4 bins | -31.5 | Good |
| Hamming | 4 bins | -42.5 | Good |
| Blackman | 6 bins | -58.1 | Very Good |
| Kaiser (β=8) | 6 bins | -69 | Excellent |
| Flat-top | 8 bins | -93 | Best |

---

## 6. Spectral Leakage

When a signal does not complete an integer number of cycles within the analysis window, energy "leaks" from the true frequency into adjacent bins.

**Cause:** Discontinuity at window edges due to non-periodic truncation
**Effect:** A single pure tone appears as a smeared peak with sidelobes
**Solutions:**
1. Apply a window function (always recommended)
2. Zero-padding (increases frequency resolution display, not true resolution)
3. Ensure analysis window is a multiple of the signal period

---

## 7. Zero-Padding

Adding zeros to the end of a signal before the FFT increases frequency **display** resolution (interpolates between bins) but does NOT add new frequency information.

```
True freq resolution = fs / N_actual_samples
Display freq resolution = fs / N_zero_padded

(N_zero_padded ≥ N_actual_samples)
```

Common practice: zero-pad to the next power of 2 for FFT efficiency, or 2×–4× for visual smoothness.

---

## 8. Resolution Tradeoffs

The time-frequency uncertainty principle:
```
Δt · Δf ≥ 1 / (4π)  [Gabor limit]

For STFT specifically:
Δt = N/fs  (window duration in seconds)
Δf = fs/N  (bin width in Hz)
Δt · Δf = 1 (constant — cannot improve both simultaneously)
```

### Practical Guidance
| Scenario | Window Size | Note |
|---|---|---|
| Whale songs (infrasound) | 16384–65536 | Very long windows needed |
| Bass guitar / cello | 4096–8192 | Long for frequency precision |
| Piano / vocal | 2048–4096 | Balanced |
| Speech phonemes | 512–1024 | Shorter for time clarity |
| Percussion / clicks | 128–256 | Short for precise timing |
| Electronic transients | 64–256 | Very short |

---

## 9. Mel Spectrogram

Human hearing is logarithmic: we perceive pitch differences on a logarithmic scale. The **Mel scale** approximates this perceptual warping.

### Mel Conversion Formulas
```
mel = 2595 · log₁₀(1 + f/700)
f = 700 · (10^(mel/2595) - 1)
```

### Construction
1. Compute standard STFT spectrogram
2. Create a bank of triangular filters spaced on the Mel scale
3. Apply filters by matrix multiplication
4. (Optional) Take log of filter energies → log-Mel spectrogram

### Uses
- Speech recognition (ASR systems)
- Music genre classification
- Environmental sound classification
- MFCCs are derived from log-Mel spectrogram via DCT

---

## 10. Constant-Q Transform (CQT)

Unlike the STFT which uses constant frequency resolution, the **CQT** uses constant *relative* frequency resolution (constant Q = f/Δf per octave). This matches the logarithmic nature of musical pitch.

```
Q = f_center / Δf = N_k / (2^(1/B) - 1)
```

Where B = bins per octave (typically 12 or 24).

**Properties:**
- Each octave has equal number of bins (B bins per octave)
- Higher frequencies have wider absolute bandwidth but same relative bandwidth
- Perfect for music analysis, chord detection, guitar tablature
- Computationally more expensive than STFT

---

## 11. Phase vs. Magnitude Spectrogram

### Magnitude Spectrogram
```
S_mag[k, m] = |STFT[k, m]|
```
Most commonly visualized. Shows "how much" energy at each time-frequency point.

### Power Spectrogram
```
S_power[k, m] = |STFT[k, m]|²
```
Emphasizes dominant frequencies; used in source separation.

### Phase Spectrogram
```
S_phase[k, m] = ∠STFT[k, m] = arctan(Im/Re)
```
Encodes timing information. Critical for audio reconstruction (Griffin-Lim algorithm).

### Log-Magnitude Spectrogram
```
S_log[k, m] = log(|STFT[k, m]| + ε)
```
Compresses dynamic range; matches human perception of loudness.

### dB Spectrogram
```
S_dB[k, m] = 20 · log₁₀(|STFT[k, m]| / S_ref)
```
Standard in audio engineering; human hearing is ~120 dB dynamic range.

---

## 12. Color Mapping Conventions

| Color Map | Low Magnitude | High Magnitude | Use Case |
|---|---|---|---|
| **Viridis** | Dark purple | Bright yellow | General scientific; perceptually uniform |
| **Magma** | Black | Cream/white | High contrast; elegant |
| **Inferno** | Black | Yellow-white | Scientific; similar to Magma |
| **Plasma** | Dark blue | Yellow | Bright, vivid |
| **Hot** | Black | White (through red/yellow) | Classic spectrogram |
| **Jet** | Blue → Cyan → Green → Yellow → Red | Legacy; perceptually non-uniform |
| **Grayscale** | Black | White | Print-friendly; simple |
| **Viridis (reversed)** | Yellow | Dark purple | Inverted; bright backgrounds |

**Best practice:** Avoid Jet for scientific publication. Prefer perceptually uniform maps (Viridis, Magma, Inferno, Plasma).

---

## 13. Normalization and Dynamic Range

Before color mapping, normalize the spectrogram:

```python
# Min-max normalization
S_norm = (S - S_min) / (S_max - S_min)

# Percentile clipping (more robust)
S_norm = clip(S, percentile(S, 5), percentile(S, 99))
S_norm = (S_norm - S_norm.min()) / (S_norm.max() - S_norm.min())

# Log normalization (recommended for audio)
S_log = log(1 + C * S)  # C controls compression
```

### Dynamic Range Considerations
- Raw linear spectrogram: huge dynamic range (10⁶:1 typical)
- After log: manageable range for display
- Top-ref dB normalization: 0 dB = loudest bin, negative values elsewhere
