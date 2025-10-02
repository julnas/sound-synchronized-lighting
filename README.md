# Music-Driven Lighting with AI
An AI-based system for real-time music-driven lighting control, developed as part of the university course Advances in AI.
The project connects audio analysis with stage lighting (DMX/Art-Net) to generate synchronized light shows that react to music.
# 🎯 Project Goals
  Capture audio from system loopback in real time. <br>
  Extract relevant features (e.g. energy, beat, spectral distribution). <br>
  Generate lighting cues (brightness, strobe, color, movement). <br>
  Compare rule-based logic with a lightweight AI model. <br>
  Ensure minimal latency for live synchronization.<br>

# 🛠️ System Architecture
Pipeline Overview: <br>
Music (Loopback) → Audio Stream → Feature Extraction 
→ [Rule Engine / AI Model] → Smoothing & Cooldown → DMX/Art-Net Output → Lighting Fixtures <br>
Audio Input: Captured via system loopback (low latency). <br>
Feature Extraction: FFT, Mel spectrogram, onset detection, energy bands.<br>
Decision Logic:<br>
Rule-based baseline (simple mappings from features to light cues).<br>
AI model (GRU / 1D-CNN) trained on auto-labeled audio segments.<br>
Output: Lighting frames mapped to DMX/Art-Net for stage fixtures.<br>
Stability Layer: Exponential smoothing and cooldown timers to avoid rapid flicker and ensure professional transitions.<br>

# 📂 Repository Structure
.
├── src/
│   ├── audio_input.py       # Capture loopback audio
│   ├── ringbuffer.py        # Store recent audio frames
│   ├── features.py          # Compute RMS, bands, onsets, mel
│   ├── decision.py          # Rule-based logic & AI model inference
│   ├── smoothing.py         # EMA & cooldown handling
│   ├── dmx_output.py        # Send DMX/Art-Net frames
│   └── run.py               # Main entry point
│
├── models/                  # Trained AI models
├── data/                    # Example songs & auto-generated labels
├── docs/                    # Reports, fixture profiles, references
└── demo/                    # Demo video and screenshots


