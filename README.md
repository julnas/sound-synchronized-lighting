# Music-Driven Lighting with AI

An AI-based system for **real-time music-driven lighting control**, developed as part of the university course *Advances in AI*.  
The project connects audio analysis with stage lighting (DMX/Art-Net) to generate synchronized light shows that react to music.

---

## 🎯 Project Goals
- Capture audio from system loopback in real time.  
- Extract relevant features (e.g. energy, beat, spectral distribution).  
- Generate lighting cues (brightness, strobe, color, movement).  
- Compare **rule-based logic** with a **lightweight AI model**.  
- Ensure minimal latency for live synchronization.  

---

## 🛠️ System Architecture

**Pipeline Overview:**

```
Music (Loopback) → Audio Stream → Feature Extraction 
→ [Rule Engine / AI Model] → Smoothing & Cooldown → DMX/Art-Net Output → Lighting Fixtures
```

- **Audio Input**: Captured via system loopback (low latency).  
- **Feature Extraction**: FFT, Mel spectrogram, onset detection, energy bands.  
- **Decision Logic**:  
  - Rule-based baseline (simple mappings from features to light cues).  
  - AI model (GRU / 1D-CNN) trained on auto-labeled audio segments.  
- **Output**: Lighting frames mapped to DMX/Art-Net for stage fixtures.  
- **Stability Layer**: Exponential smoothing and cooldown timers to avoid rapid flicker and ensure professional transitions.  

---

## 📂 Repository Structure

```
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
├── models/                  # Trained AI models (e.g. ONNX)
├── data/                    # Example songs & auto-generated labels
├── docs/                    # Reports, fixture profiles, references
└── demo/                    # Demo video and screenshots
```

---

## 🚀 Usage

1. Clone the repository:
   ```
   git clone https://github.com/username/music-reactive-lighting.git
   cd music-reactive-lighting
   ```
2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```
3. Start the system (loopback input + DMX output):
   ```
   python src/run.py --mode baseline
   ```
   or with the AI model:
   ```
   python src/run.py --mode ai --model models/tiny_lightnet.onnx
   ```

---

## 🎥 Demo
A short demo video showing music-reactive lighting will be added here.  

---

## 📖 Documentation
- docs/fixture_profile.md – Channel layout for the lamp(s).  
- docs/report.pdf – Course report including design, methodology, and results.  

---

## 🧠 AI Component
- **Training Data**: Auto-labeled using rule-based heuristics.  
- **Model**: Lightweight GRU/1D-CNN predicting pattern + parameters.  
- **Evaluation**: Comparison of latency, smoothness, and musical alignment against baseline rules.  

---

## ⚠️ Limitations
- Prototype supports only a single fixture profile.  
- AI model trained on a small dataset (demonstration purpose).  
- Real-time performance depends on audio backend and DMX interface.  

---

## 📚 References
- Open Lighting Architecture (OLA)  
- librosa: Python library for audio analysis  
- Research on music-to-light AI mapping (see docs/references.md)  

---

## 👤 Author
Developed by *[Your Name]* for the course *Advances in AI*.  
