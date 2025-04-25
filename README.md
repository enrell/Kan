# Kan (閂) — The Lock That Learns You - Initial Idea

> *"No passwords. No cloud. Just your breath. Your steps. Your time — encoded in entropy. You are the cipher."*

---
<br>

## 🧬 What is Kan (閂)?

*Night. Neon bleeds through blinds. Your phone hums faintly on the desk — not from a message, but from the tremor of your step. No face ID. No code. Just motion, sound, and silence becoming signal.*

**Kan**, inspired by the Japanese kanji 閂 (meaning "bolt" or "latch"), is a sci-fi-driven, cyberpunk-styled Android app that redefines how you secure and authenticate your data.

The kanji 閂 depicts a gate (門) locked by a bar (一), symbolizing security. Commonly read as *kannuki* (かんぬき), a traditional Japanese bolt, or *san* in other contexts, it evokes a timeless act of safeguarding. The name **Kan** likely draws from this imagery, stylized to echo a futuristic lock.

KAN harnesses **ambient data** — your gait, the sounds of your surroundings, the light at your location, the time of day — to create temporary **biometric signatures**. These act as dynamic, context-aware cryptographic keys, locking your data as securely as a bolt across a gate.

> It’s like a digital lock forged from your everyday movements. No cloud. No fancy UI. Just raw, local, secure tech.

---
<br>

## 🔒 TL;DR — Why KAN?

- 🧠 *Passive biometric authentication from sensors*
- 🔐 *No passwords — the key is your context*
- 🚫 *Zero server dependency — 100% offline*
- 💾 *Encrypted local storage with adaptive trust*
- 🧪 *Feels like experimental tech smuggled out of a neon-drenched lab in Tokyo — encryption latched to light, to footfall, to the ghosts of your data trail*

---
<br>

## 🧠 How It Works

Every X second (that I don't know yet), **Kan** does this:

### 1. 📡 Sensor Data Collection
- Accelerometer
- Gyroscope
- Microphone
- Ambient light
- Time of day
- *(Maybe: GPS, magnetometer, etc.)*

### 2. 🧪 Feature Extraction
- Fast Fourier Transform (FFT)
- Statistical filters (mean, variance, peaks)
- Signal smoothing / band-pass filters

### 3. 🧬 Embedding Generation
- Autoencoder or LSH / SimHash
- Outputs a short embedding (e.g., 128-bit vector)

### 4. 🔑 Key Derivation
- Embedding is fed into a KDF (e.g., HKDF or Argon2)
- Generates a cryptographic key to encrypt/decrypt vaults

### 5. 🤖 Adaptive Learning
- Fallback authentication updates trusted embeddings
- Database evolves as you evolve

---
<br>

## 🧩 Architecture Overview

```
╔══════════════════════════════════════════════╗
║             ANDROID SENSOR HUB               ║
╚══════════════════════════════════════════════╝
                    ↓
╔══════════════════════════════════════════════╗
║       Feature Extractor Engine (NDK/C++)     ║
╚══════════════════════════════════════════════╝
                    ↓
╔══════════════════════════════════════════════╗
║      Embedding Encoder (TFLite / SimHash)    ║
╚══════════════════════════════════════════════╝
                    ↓
╔══════════════════════════════════════════════╗
║           Key Derivation (Argon2 / HKDF)     ║
╚══════════════════════════════════════════════╝
                    ↓
╔══════════════════════════════════════════════╗
║        Encrypted Vault / Context Gatekeeper  ║
╚══════════════════════════════════════════════╝
                    ↓
╔══════════════════════════════════════════════╗
║         Local Database (Encrypted SQLite)    ║
╚══════════════════════════════════════════════╝
```

- **Kotlin** for application logic
- **C++ NDK** for performance-heavy feature processing
- **TensorFlow Lite / NumPy** for context encoding
- **Zero internet permissions** — designed to be air-gapped

---
<br>

## 🧠 Adaptive Trust Model

> *"Your body and context change. So does the lock."*

- If context is unrecognized:
  - Prompt fallback auth (PIN, passkey, backup codes)  
  - On success: embedding added to trusted list
- Matching determined via cosine or Hamming distance  
- Sensitivity dynamically adapts to your entropy pattern

<br>

## 👤 Auth Without Trying

**Use cases:**

- Unlock encrypted data only when your natural behavior/context matches expected signature
- Combine with PIN or biometrics for contextual MFA

<br>

## 🛡️ Anti-Theft Mode

- App monitors for sudden, unnatural motion (jerk, snatch)
- If triggered:
  - Locks app screen temporarily
  - Suppresses new embedding updates (to preserve data quality)
  - Enters emergency mode:
    - Requests PIN/Biometric *(default fallback)*
    - Requests user to re-read original calibration phrase
    - Matches voice embedding to initial signature
    - If match fails:
      - Wait for cooldown and context normalization
      - Or use one of 12 optional recovery codes (if configured)

> ⚠️ *Note: This does not lock the entire device — only behaves like a temporary screen off to simulate safe locking.*

---
<br>

## 🌌 Inspiration & Design Aesthetic

- Ghost in the Shell
- Ergo Proxy
- Serial Experiments Lain

<br>

## 📡 Contribute / Fork / Hack

This project is yours to fork, break, encrypt, and evolve.

<br>

## 🧾 License

MIT License. Built for the data ghosts.

<br>


- *"We are not stuff that abides, but patterns that perpetuate themselves" - Norbert Wiener*
