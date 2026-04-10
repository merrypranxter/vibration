# 🎵 Vibration & Resonance Database

A comprehensive, open reference database of frequencies, resonances, Chladni patterns, cymatics, brainwaves, solfeggio tones, chakra frequencies, material resonances, and acoustic physics — structured for use in AI art generation, audio-reactive visuals, scientific research, sound healing, and shader/generative art development.

---

## 📁 Repository Structure

```
vibration/
├── README.md                          ← This file
├── VIBRATION_PHYSICS_PRIMER.md        ← Physics background: SHM, waves, resonance, cymatics
│
└── core/
    ├── vibration_database.json         ← Master database: 35+ key frequencies with full metadata
    └── frequency_reference/
        ├── musical_notes.json          ← All 108 standard notes C0–B8 (MIDI 12–119)
        ├── special_frequencies.json    ← Solfeggio, Schumann, chakra, cosmic, earth frequencies
        ├── material_resonances.json    ← Resonant frequencies of physical objects & structures
        ├── binaural_beats.json         ← Brainwave states: Delta → Lambda with carrier guides
        └── hearing_range.md            ← Human hearing map with psychoacoustics context
```

---

## ⚡ Quick Start

### Find a frequency entry
```bash
# Look up 528 Hz (Solfeggio miracle tone)
cat core/vibration_database.json | python3 -c "
import json,sys
db=json.load(sys.stdin)
hits=[e for e in db['entries'] if e['frequency_hz']==528]
print(json.dumps(hits, indent=2))
"
```

### List all Solfeggio frequencies
```bash
cat core/frequency_reference/special_frequencies.json | python3 -c "
import json,sys
data=json.load(sys.stdin)
for e in data:
    if e['category']=='Solfeggio':
        print(f\"{e['frequency_hz']} Hz — {e['name']}\")
"
```

### Get all notes in octave 4
```bash
python3 -c "
import json
notes=json.load(open('core/frequency_reference/musical_notes.json'))
for n in notes:
    if n['octave']==4:
        print(f\"{n['note']:5s} {n['frequency_hz']:8.2f} Hz  MIDI {n['midi_number']}  {n['color_hex']}\")
"
```

### Find frequencies by hearing range position
```bash
python3 -c "
import json
db=json.load(open('core/vibration_database.json'))
for e in db['entries']:
    if 'Bass' in e['hearing_range_position']:
        print(f\"{e['frequency_hz']:8.2f} Hz — {e['perception'][:60]}\")
"
```

---

## 🎯 Use Cases

### 🎨 AI Art & Image Generation
Every frequency entry includes:
- `ai_art_tags` — curated descriptive tags for prompt engineering
- `color_hex` — the chromesthetic color mapping for the frequency
- `visual_personality` — poetic visual description for generative art prompts
- `chladni_pattern_reference` — links to Chladni pattern imagery
- `cymatics_reference` — links to cymatics photography data

**Example prompt construction:**
```
"A vibrating metal plate at 440Hz covered in sand, forming Chladni patterns,
 golden crystalline geometry, sharp penetrating light rays — #FFD700"
```

### 🔊 Audio-Reactive Visuals & Shaders
- `frequency_hz` + `harmonics_hz` → shader frequency banks
- `wavelength_m` → spatial wave period for GLSL wave equations
- `period_ms` → animation timing / BPM alignment
- `hearing_range_position` → maps to visual intensity/spatial zone
- `brainwave_effect` → shader "mood" state parameter

**GLSL usage example:**
```glsl
// Use period_ms as animation speed
float freq = 440.0;
float period = 1000.0 / freq; // 2.27 ms
float wave = sin(uTime / period * TWO_PI + uv.x * freq * 0.01);
```

### 🌀 Cymatics & Chladni Pattern Simulation
- All 108 musical notes include harmonics for multi-mode excitation
- `wavelength_m` provides spatial scale for pattern simulation
- Chladni patterns: sprinkle sand on a resonating plate at `frequency_hz`
- The pattern complexity increases with frequency
- See `VIBRATION_PHYSICS_PRIMER.md` for the math

### 🧠 Brainwave / Binaural Beat Applications
- `core/frequency_reference/binaural_beats.json` provides full Delta→Lambda coverage
- Each state includes `carrier_frequency_hz`, `associated_neurotransmitters`, and `use_cases`
- To create a binaural beat: play left ear at carrier, right ear at carrier+beat_frequency
- Example: Alpha at 10 Hz → Left: 200 Hz, Right: 210 Hz

### 🔬 Sound Healing & Frequency Therapy
- Solfeggio frequencies (174–963 Hz) with `solfeggio_intent` and `digital_root`
- Chakra frequencies (256–480 Hz) with `chakra_element`, `body_location`, `chakra_color`
- 432 Hz alternative tuning vs. 528 Hz DNA repair tone
- Earth/cosmic frequencies: Om (136.1 Hz), Schumann (7.83 Hz)

### 🏗️ Structural & Materials Engineering
- `core/frequency_reference/material_resonances.json` covers objects from wine glasses to bridges
- Q-factor and damping ratio for each material
- Mode shapes and failure frequencies (e.g., Tacoma Narrows at 0.2 Hz)

---

## 📊 Data Format Examples

### Frequency Entry (`core/vibration_database.json`)
```json
{
  "id": "FREQ-440-A4",
  "note": "A4",
  "frequency_hz": 440,
  "octave": 4,
  "wavelength_m": 0.7795,
  "period_ms": 2.2727,
  "harmonics_hz": [440, 880, 1320, 1760, 2200],
  "harmonic_ratios": ["1:1", "2:1", "3:1", "4:1", "5:1"],
  "perception": "Concert pitch standard since 1939 ISO 16. Bright, clear, penetrating.",
  "chakra_association": "Throat Chakra",
  "brainwave_effect": "Beta",
  "color_hex": "#FFD700",
  "hearing_range_position": "Upper Midrange",
  "visual_personality": "Sharp golden crystalline geometry, concert hall resonance",
  "chladni_pattern_reference": "CHLAD-440-A4",
  "cymatics_reference": "CYMAT-440-A4-SAND",
  "ai_art_tags": ["A4", "440hz", "concert-pitch", "golden", "crystalline", "reference"]
}
```

### Musical Note Entry (`core/frequency_reference/musical_notes.json`)
```json
{
  "id": "NOTE-C4",
  "note": "C4",
  "midi_number": 60,
  "frequency_hz": 261.63,
  "octave": 4,
  "note_name": "C",
  "wavelength_m": 1.311,
  "period_ms": 3.8222,
  "harmonics_hz": [261.63, 523.26, 784.89, 1046.52, 1308.15],
  "semitone_from_A4": -9,
  "color_hex": "#FF0000",
  "perception": "Middle C — universal reference, piano key 40"
}
```

### Chladni Pattern Entry (planned: `patterns/chladni/`)
```json
{
  "id": "CHLAD-A4",
  "frequency_hz": 440,
  "plate_material": "steel",
  "plate_size_mm": 300,
  "pattern_complexity": "moderate",
  "node_count": 8,
  "symmetry_order": 4,
  "image_file": "chladni_440hz_steel_300mm.png",
  "description": "Four-fold symmetric node lines forming an X pattern with curved segments"
}
```

---

## 🔗 Cross-Reference Index

| Concept | Primary File | Cross-References |
|---|---|---|
| Musical notes (C0–B8) | `musical_notes.json` | `vibration_database.json`, `hearing_range.md` |
| Solfeggio frequencies | `special_frequencies.json` | `vibration_database.json` (FREQ-174 through FREQ-963) |
| Chakra frequencies | `special_frequencies.json` | `vibration_database.json` (FREQ-256 through FREQ-480) |
| Schumann resonance | `special_frequencies.json` | `vibration_database.json` (FREQ-7.83) |
| Brainwave states | `binaural_beats.json` | `vibration_database.json` (`brainwave_effect` field) |
| Material resonances | `material_resonances.json` | `VIBRATION_PHYSICS_PRIMER.md` (Q-factor section) |
| Hearing map | `hearing_range.md` | `vibration_database.json` (`hearing_range_position` field) |
| Physics background | `VIBRATION_PHYSICS_PRIMER.md` | All frequency files |

---

## 🔬 Physics Background

All frequencies use:
- **Equal temperament tuning**: `f = 440 × 2^((n−69)/12)` where n = MIDI number
- **Speed of sound**: 343 m/s at 20°C (sea level)
- **Wavelength**: `λ = 343 / f` (metres)
- **Period**: `T = 1000 / f` (milliseconds)
- **Harmonics**: integer multiples of fundamental `f, 2f, 3f, 4f, 5f`

See [`VIBRATION_PHYSICS_PRIMER.md`](VIBRATION_PHYSICS_PRIMER.md) for complete physics derivations.

---

## 📜 Credits & Notes

- Musical note frequencies calculated using ISO 16 equal temperament (A4 = 440 Hz)
- Solfeggio frequencies per Horowitz & Puleo, *Healing Codes for the Biological Apocalypse* (1999)
- Schumann resonance values from Schumann (1952) and NOAA atmospheric physics data
- Chakra frequencies per various traditions; no single canonical source
- Binaural beat research references: Monroe Institute, Oster (1973), Başar (2012)
- Material resonance data from acoustics engineering handbooks and published research
- 432 Hz vs 440 Hz: historical analysis from Haynes, *A History of Performing Pitch* (2002)
- Chladni pattern physics: Chladni, *Entdeckungen über die Theorie des Klanges* (1787)
- Cymatics: Jenny, *Cymatics* Vol. 1 & 2 (1967, 1974)

> **Scientific note**: Some frequencies in this database (e.g., Solfeggio, chakra) originate from spiritual/traditional sources rather than peer-reviewed physics. They are included for completeness and creative use. The physics parameters (wavelength, period, harmonics) are rigorously calculated regardless of source.
vibration math
