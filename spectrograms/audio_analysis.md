# Audio Analysis — Fourier Theory and Spectral Features

A comprehensive guide to audio analysis using Fourier methods, harmonic analysis, and spectral feature extraction.

---

## 1. Time Domain vs Frequency Domain

A signal can be viewed from two complementary perspectives:

### Time Domain
- Signal amplitude as a function of time: `x(t)`
- Reveals: dynamics, attack/release, rhythm, temporal patterns
- What you see on an oscilloscope
- Natural for: rhythmic analysis, envelope detection, waveshaping

### Frequency Domain
- Signal energy as a function of frequency: `X(f)`
- Reveals: pitch, timbre, harmonics, noise characteristics
- What you see on a spectrum analyzer
- Natural for: pitch detection, instrument identification, equalization

**The Fourier Transform is the bridge:**
```
Time Domain ←→ Frequency Domain
    x(t)    ←→    X(f)
```

Both representations contain identical information; neither is more "real."

---

## 2. Convolution Theorem

The **convolution theorem** is one of the most powerful results in signal processing:

```
Time domain convolution ↔ Frequency domain multiplication:
(f * g)(t) = ∫ f(τ) g(t-τ) dτ  ←→  F(ω) · G(ω)

Time domain multiplication ↔ Frequency domain convolution:
f(t) · g(t)  ←→  (F * G)(ω) / (2π)
```

**Applications:**
- Filtering = multiplication in frequency domain (much faster via FFT)
- Reverb = convolution with impulse response
- Windowing in STFT = convolution with window spectrum
- FIR filter design = designing frequency response, then inverse FFT

---

## 3. Autocorrelation and Power Spectral Density

### Autocorrelation
The autocorrelation measures how similar a signal is to a time-shifted version of itself:

```
R_x(τ) = ∫ x(t) · x*(t + τ) dt
```

- Periodic signals produce periodic autocorrelation → peaks at period multiples
- Used in **pitch detection** (fundamental period = first strong peak after τ=0)
- Noise has autocorrelation ≈ δ(τ) (Dirac delta)

### Power Spectral Density (PSD)
The PSD is the Fourier transform of the autocorrelation (Wiener-Khinchin theorem):

```
S_x(ω) = F{R_x(τ)} = |X(ω)|² / T
```

- Measures power per unit frequency (W/Hz)
- Independent of phase — purely energetic description
- Log PSD is proportional to perceived loudness

---

## 4. Harmonic Analysis: Fundamental and Overtones

Real-world pitched sounds consist of a fundamental frequency plus **harmonics** (integer multiples):

```
f_1 = fundamental frequency
f_n = n · f_1   (for ideal harmonic series)

Signal: x(t) = Σ_n A_n · cos(2π · n · f_1 · t + φ_n)
```

- **Harmonic**: exact integer multiple of fundamental
- **Partial**: any component in a complex tone (may be non-integer = "inharmonic")
- **Overtone**: any partial above the fundamental (overtone 1 = harmonic 2)

### Inharmonicity
Real instruments deviate from ideal harmonics. Piano strings, for example, have stiff strings causing partials to be slightly sharp:

```
f_n ≈ n · f_1 · √(1 + B·n²)
```

Where B is the inharmonicity coefficient (B ≈ 0.0001–0.001 for piano).

### Harmonic Content by Waveform
| Waveform | Harmonics Present | Formula |
|---|---|---|
| Sine | None (fundamental only) | f₁ |
| Square | Odd harmonics | f₁, 3f₁, 5f₁, ... (∝ 1/n) |
| Triangle | Odd harmonics | f₁, 3f₁, 5f₁, ... (∝ 1/n²) |
| Sawtooth | All harmonics | f₁, 2f₁, 3f₁, ... (∝ 1/n) |
| Pulse (duty≠50%) | All harmonics | Amplitude depends on duty cycle |

---

## 5. Pitch Detection Algorithms

### 5.1 Autocorrelation Method
1. Compute autocorrelation R_x(τ) of the windowed signal
2. Find the lag τ₀ of the first strong peak (after zero-crossing)
3. Fundamental period T₀ = τ₀, frequency f₀ = 1/T₀

**Pros:** Simple, robust to noise
**Cons:** Can octave-double; slow for polyphonic signals

### 5.2 YIN Algorithm
An improved autocorrelation method using the **Difference Function**:

```
d(τ) = Σ_j (x[j] - x[j+τ])²

Cumulative Mean Normalized Difference:
d'(τ) = d(τ) / [(1/τ) Σ_{j=1}^τ d(j)]   (τ > 0)
d'(0) = 1
```

Find the first τ where `d'(τ) < threshold` (typically 0.1–0.2).

**Pros:** Reduced octave errors, better onset tracking
**Cons:** Still primarily monophonic; requires tuning of threshold

### 5.3 Harmonic Product Spectrum (HPS)
Emphasizes the fundamental by multiplying downsampled versions of the spectrum:

```
HPS(f) = Π_{r=1}^R |X(r·f)|

Fundamental = argmax_f HPS(f)
```

**Pros:** Works when fundamental is weak/absent
**Cons:** Can fail at high harmonics; affected by noise

### 5.4 CREPE (CNN-based)
Modern deep learning approach achieving near-human pitch tracking accuracy. Takes raw waveform input, outputs pitch confidence distribution.

---

## 6. Onset Detection

Onset = the moment a new musical event begins (note attack).

### Energy-based Onset Detection
```
E[m] = Σ_k |STFT[k, m]|²
ODF[m] = E[m] - E[m-1]   (positive half-wave rectified)
```

### Spectral Flux
```
SF[m] = Σ_k max(|X[k,m]| - |X[k,m-1]|, 0)
```
More frequency-selective than energy; detects onsets in specific bands.

### Complex Domain Method
Uses both magnitude and phase information for improved accuracy in polyphonic music.

### Peak Picking
After computing the **Onset Detection Function (ODF)**:
1. Find local maxima above a threshold
2. Apply minimum inter-onset interval (e.g., 50 ms)
3. Adaptive thresholding using local median

---

## 7. Beat Tracking

Beat tracking locates the pulse/meter of music.

### Tempo Estimation
1. Compute onset strength signal ODF[m]
2. Compute autocorrelation or Fourier transform of ODF
3. Find peak corresponding to beat period T_beat
4. BPM = 60 × f_s / (T_beat × hop_size)

### Dynamic Programming Beat Tracking
Given a tempo estimate, use dynamic programming to find the globally optimal beat sequence:

```
score[t] = ODF[t] + max_{t'} [ score[t'] - α · (t - t' - T)² ]
```

Where α controls the penalty for deviating from the expected tempo.

---

## 8. Spectral Features

Key spectral features used in music information retrieval (MIR):

### 8.1 Spectral Centroid
Center of mass of the spectrum — correlates with perceived brightness:
```
SC = Σ_k (k · |X[k]|) / Σ_k |X[k]|
```

### 8.2 Spectral Spread
Width of the spectrum around the centroid — related to timbre richness:
```
SS = √[ Σ_k ((k - SC)² · |X[k]|) / Σ_k |X[k]| ]
```

### 8.3 Spectral Flux
Rate of change of the spectrum — detects onsets and transients:
```
SF = Σ_k (|X[k, m]| - |X[k, m-1]|)²
```

### 8.4 Spectral Rolloff
Frequency below which a specified percentage (e.g., 85%) of spectral energy is contained:
```
Σ_{k=0}^{k_r} |X[k]|² = 0.85 · Σ_k |X[k]|²
```

### 8.5 Zero Crossing Rate (ZCR)
Number of times the signal crosses zero per unit time:
```
ZCR = Σ_n |sign(x[n]) - sign(x[n-1])| / (2N)
```
High ZCR → noisy or high-frequency content. Low ZCR → tonal, voiced content.

### 8.6 Spectral Flatness (Tonality)
Ratio of geometric mean to arithmetic mean of spectrum — measures noise vs. tonality:
```
SF = (Πₖ |X[k]|^(1/N)) / ((1/N) Σₖ |X[k]|)
```
SF ≈ 0 → pure tone. SF ≈ 1 → white noise.

---

## 9. MFCC — Mel-Frequency Cepstral Coefficients

MFCCs are the standard feature set for speech recognition and music classification.

### Computation Pipeline
```
1. Pre-emphasis filter: y[n] = x[n] - 0.97·x[n-1]   (boosts high frequencies)
2. Frame & window: apply Hann window to 25ms frames, 10ms hop
3. FFT: compute magnitude spectrum
4. Mel filter bank: apply 26–40 triangular filters on Mel scale
5. Log: take log of filter energies
6. DCT: apply Discrete Cosine Transform
7. Keep first 12–20 coefficients → MFCCs
```

### What MFCCs Capture
- **C0** — overall energy (sometimes excluded)
- **C1–C3** — broad spectral shape (vowel identity, instrument type)
- **C4–C12** — finer spectral detail (phoneme differentiation)
- **Delta MFCCs** (ΔC) — first-order temporal derivatives (velocity)
- **Delta-Delta MFCCs** (ΔΔC) — second-order derivatives (acceleration)

---

## 10. Real-Time FFT Considerations

For real-time spectrogram generation, key constraints:

### Latency
```
Latency = window_size / sample_rate + processing_overhead

Example: 1024-sample window at 44100 Hz = 23.2 ms window
With 50% overlap: new frame every 11.6 ms
```

### Ring Buffer Pattern
```
1. Write incoming samples into ring buffer
2. When hop_size new samples accumulated: trigger FFT
3. Extract window_size samples from ring buffer
4. Apply window function
5. Compute FFT
6. Update display (asynchronous)
```

### Optimization Techniques
- Use radix-2 FFT (power-of-2 window sizes only)
- Pre-compute window coefficients
- Use SIMD/vectorized FFT libraries (FFTW, Apple Accelerate, Intel MKL)
- Process multiple channels in parallel
- Separate analysis and display threads
- Use fixed-point arithmetic on embedded systems

### GPU-Accelerated Spectrograms
Modern real-time systems use GPU for FFT computation:
- cuFFT (NVIDIA CUDA) — batch FFT processing
- WebGL/WebGPU — browser-based real-time spectrograms
- Metal Performance Shaders (Apple) — iOS/macOS apps
