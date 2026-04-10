# Spectrograms

A spectrogram is a visual representation of how the frequency content of a signal changes over time. It bridges the gap between the time domain and the frequency domain, making invisible patterns in sound and vibration visible to the eye.

---

## What Is a Spectrogram?

A spectrogram is a 2D image derived from a signal. It encodes three dimensions of information:

| Axis / Channel | Represents |
|---|---|
| **X-axis** | Time (left = start, right = end) |
| **Y-axis** | Frequency (bottom = low, top = high) |
| **Color / Brightness** | Magnitude (amplitude) at that time-frequency point |

The brighter or warmer the color at a given point, the more energy (louder, stronger) the signal has at that frequency at that moment in time.

---

## Fourier Transform Fundamentals

Every periodic signal can be decomposed into a sum of sine waves — each with a specific frequency, amplitude, and phase. This is the insight behind Fourier analysis.

**Fourier Transform (continuous):**
```
F(ω) = ∫₋∞^∞ f(t) · e^(-iωt) dt
```

This converts a time-domain signal `f(t)` into its frequency-domain representation `F(ω)`. The result is complex-valued; the **magnitude** `|F(ω)|` tells you how much of each frequency is present, and the **phase** `∠F(ω)` tells you the timing offset.

**Inverse Fourier Transform:**
```
f(t) = (1/2π) ∫₋∞^∞ F(ω) · e^(iωt) dω
```

For digital signals, we use the **Discrete Fourier Transform (DFT)**, computed efficiently via the **Fast Fourier Transform (FFT)** algorithm (Cooley-Tukey, 1965), which reduces complexity from O(N²) to O(N log N).

---

## Short-Time Fourier Transform (STFT)

A plain FFT computes frequency content over the *entire* signal — it loses all time information. To create a spectrogram, we use the **Short-Time Fourier Transform (STFT)**:

1. **Divide** the signal into short, overlapping frames (windows)
2. **Apply a window function** to each frame (to reduce spectral leakage)
3. **Compute the FFT** of each windowed frame
4. **Stack** the magnitude spectra as columns to form the 2D spectrogram image

**STFT formula:**
```
STFT{x}(τ, ω) = ∫₋∞^∞ x(t) · w(t - τ) · e^(-iωt) dt
```

Where `w(t)` is the window function and `τ` is the time offset (frame position).

**Key parameters:**
- **Window size** (FFT size): determines frequency resolution vs. time resolution
- **Hop size**: how far to advance between windows (controls overlap)
- **Window function**: Hann, Hamming, Blackman, etc.

---

## Reading a Spectrogram

```
Frequency (Hz)
   ▲
16k│·  ·   ·  ·
8k │   ██  ██
4k │  ████████
2k │ ██████████
1k │  ████████
500│   ██  ██
250│  ·   ·  ·
 80│·           ·
 20├──────────────→ Time (s)
   0  1  2  3  4
```

**How to interpret:**
- **Horizontal bands** = sustained tones at constant frequencies (e.g., a held note)
- **Vertical lines / streaks** = transients, clicks, impulses (energy across all frequencies)
- **Diagonal lines** = frequency sweeps / chirps (frequency changing over time)
- **Formant bands** = resonant peaks in voice, instruments
- **Harmonic stacks** = evenly-spaced horizontal lines (fundamental + overtones)

**Color scale conventions:**
- **Dark / black** = low magnitude (near silence)
- **Bright / warm** = high magnitude (loud)
- Common palettes: Viridis (dark purple → yellow), Hot (black → red → yellow → white), Grayscale

---

## Applications

| Domain | Application |
|---|---|
| **Music analysis** | Chord detection, instrument separation, pitch tracking |
| **Speech recognition** | Phoneme classification, speaker identification, emotion detection |
| **Sonar / Radar** | Target detection, range-Doppler imaging, clutter analysis |
| **Medical imaging** | EEG/ECG frequency analysis, ultrasound signal processing |
| **Bioacoustics** | Animal call identification (birds, whales, bats) |
| **Seismology** | Earthquake frequency analysis, underground resonance |
| **Industrial NDT** | Structural health monitoring, vibration fault detection |
| **Cymatics / Art** | Visual music, frequency-to-image mapping, generative art |
| **Radio / Telecom** | Signal identification, interference analysis, waterfall displays |

---

## Heisenberg Uncertainty Principle in Signal Processing

There is a fundamental tradeoff in spectrogram analysis analogous to quantum mechanics:

```
Δt · Δf ≥ 1 / (4π)
```

You **cannot simultaneously have perfect time resolution and perfect frequency resolution**. A longer window gives better frequency resolution but worse time resolution. A shorter window gives better time localization but blurs frequency detail.

**Common tradeoff choices:**
| Use Case | Window Size | Result |
|---|---|---|
| Music (pitched instruments) | Large (2048–4096 samples) | Sharp frequency lines, smeared time |
| Percussion / transients | Small (256–512 samples) | Precise timing, blurred pitch |
| Speech | Medium (512–1024 samples) | Balanced |

---

## File Index — This Section

| File | Contents |
|---|---|
| `README.md` | This overview |
| `spectrogram_reference.md` | Technical deep dive: math, window functions, transforms |
| `audio_analysis.md` | Audio analysis theory: harmonics, pitch, spectral features |
| `color_mapping_schemes.json` | 10 color map definitions with hex stops |
| `waveform_types.json` | 12 waveform types with spectral profiles |
| `harmonic_series.json` | Harmonic series data for 10 instrument types |

---

## Related Sections

- `../data/note_frequencies.json` — All 88 piano key frequencies
- `../data/frequency_database.csv` — Full frequency reference database
- `../data/harmonic_series.json` — Note-by-note harmonic data (C1–B5)
- `../chladni/` — Plate vibration patterns
- `../cymatics/` — Fluid and surface vibration visualizations
