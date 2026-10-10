# 🤖 Prosenjit — Practical Assistant Inside (PAI)

### The Ultimate Cross-Platform Autonomous Personal AI Assistant — Engineered by Prosun Banerjee

[![Current Build](https://img.shields.io/badge/System%20Build-D.20.1v-purple?style=for-the-badge)](#version-overview)
[![Core Project](https://img.shields.io/badge/Core%20Project-Pi%20%E2%88%82-blue?style=for-the-badge)](#version-overview)
[![Security Patch](https://img.shields.io/badge/Security%20Patch-Sys%20Knot%204.0.3--v-emerald?style=for-the-badge)](#security-version-breakdown-sys-knot-403-v)
[![Python](https://img.shields.io/badge/Python-3.11%20%7C%203.12%20%7C%203.13-3776AB?style=for-the-badge&logo=python&logoColor=white)](#requirements--os-compatibility)
[![Platforms](https://img.shields.io/badge/Platforms-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey?style=for-the-badge)](#requirements--os-compatibility)
[![Engine](https://img.shields.io/badge/Live%20Engine-Gemini%20Live%20API-4285F4?style=for-the-badge&logo=google&logoColor=white)](#overview)
[![License](https://img.shields.io/badge/License-CC%20BY--NC%204.0-orange?style=for-the-badge)](https://creativecommons.org/licenses/by-nc/4.0/)

A real-time, autonomous voice AI that can hear, see, speak, and control your computer on any operating system. Powered by Google's Gemini Live API for native bidirectional audio streaming, PAI delivers ultra-low latency, zero subscription costs, and total digital privacy.

---

# PAI System Information

## Version Overview

- **Current System Build (Main Version):** `D.20.1v` (the active operational build running PAI)
- **Core Project Update:** `Pi ∂` (the overarching project architecture and version name)
- **Active Security Version:** `Sys Knot 4.0.3-v` (the active security patch and firewall integration level)

## Main System Version Breakdown (D.20.1v)

`D.20.1v` is the primary system build currently running:

- **D:** Represents the Determinative versioning track, indicating major architectural upgrades.
- **20:** The 20th major upgrade revision.
- **1:** The 1st minor upgrade iteration within this cycle.
- **v:** Indicates standard version identifier.

## Security Version Breakdown (Sys Knot 4.0.3-v)

`Sys Knot 4.0.3-v` designates the active security patch architecture and firewall integration (analogous to routine monthly OS security updates in platforms like Samsung / Android):

- **Sys Knot:** System Knot represents the security patch designation and firewall integration layer, where **Sys** defines internal system architecture and **Knot** specifies the hardened security patch level.
- **4 (Major):** Indicates the level of system updates, specifically security patch enhancements.
- **0 (Major Updates):** Number of major architectural revisions in this version.
- **3 (Minor Updates):** Number of smaller updates, bug fixes, or revisions within this build.
- **v:** Indicates standard version identifier.

## Security Philosophy

PAI is architected with a primary focus on maximizing data confidentiality and system security, designed to exceed the specific security benchmarks of other personal AI counterparts like Rudra. Upgrades are batched cumulatively for deployment, with a future objective to upgrade to the 'Sys Knot ∇' specification for optimized protection against unauthorized access to confidential files.

---

## 💡 The Core Idea & Why PAI Stands Apart

Most conventional voice assistants are either **passive text chatbots with text-to-speech wrappers** or **cloud-tethered corporate appliances** designed to collect telemetry and sell ecosystem services.

**PAI (Practical Assistant Inside)** was created from a fundamentally different philosophy:

1. **Digital Sovereignty & Zero Subscriptions:** No monthly SaaS fees, no hidden cloud servers, no account logins, and zero corporate tracking. All credentials, configurations, and long-term memory remain strictly on your local disk.
2. **Deep Desktop Operating Agency:** PAI does not just talk about computing — it **drives the machine**. It launches applications, organizes workspaces, manages windows, controls hardware volume/brightness, captures screen and webcam contexts, automates web browsers, and reads local documents.
3. **GPU-Free Software Holographic Rendering:** A lightweight, software-rendered 3D holographic avatar built on MediaPipe geometry and PyQt6 `QPainter`. It runs at high frame rates with natural facial acting, blinking, and ~50 visemes per second without needing an expensive dedicated GPU.
4. **Resilient Nine-Tier Model Fallback Ladder:** Instead of failing or freezing when an AI model hits rate limits or server timeouts, PAI automatically falls back through an empirical 9-model ladder with intelligent cooldowns.
5. **Non-Destructive Safety with UI Token Gates:** Actions that alter files or system configurations register automatic reverse operations in an undo stack. Irreversible commands (like system shutdown or network toggle) require a hardware-level confirmation token issued exclusively by the UI.

---

## 🧠 Knowledge & Research Origins: Discovering MediaPipe

The realization of PAI's software-rendered holographic avatar originates directly from deep exploration into **Google AI Edge and MediaPipe's computer vision research**, specifically surrounding real-time face mesh topologies, landmark graphs, and geometric facial reconstruction.

### 1. The Research Breakthrough
During architectural research into lightweight computer vision pipelines on [Google AI Edge / MediaPipe](https://github.com/google-ai-edge/mediapipe), the primary engineering challenge was: *How can an AI assistant possess an expressive, biologically authentic face without requiring heavy 3D game engines (Unity/Unreal), 500 MB avatar assets, or dedicated GPU hardware?*

Traditional 3D avatars require compute-heavy rendering engines, skeletal skinning shaders, and GPU rasterization. MediaPipe's canonical 3D face model solved this problem at the mathematical level:
- **468 Measured Anatomical Vertices:** Rather than an artificial graphic artist mesh, MediaPipe's canonical model provides 468 measured human facial vertices and 898 Delaunay triangles mapped in normalized 3D coordinate space.
- **Microscopic Asset Footprint:** The entire face model file (`core/face_model.obj`) is merely **25 KB**, loading into RAM in a fraction of a millisecond with zero runtime model download overhead.

### 2. How MediaPipe Geometry Drives PAI's Avatar
By extracting and indexing specific landmark rings from MediaPipe's topology, PAI translates vocal audio and internal state into live facial kinematics:
- **Viseme Lip Articulation:** Real-time speech formants and Unicode phonemes deform the MediaPipe inner and outer lip contour vertices (rings 0, 13, 14, 17, 37, 61, 84...) at ~50 mouth shapes per second.
- **Natural Gaze & Eyelids:** MediaPipe eye contour indices dynamically track blinking cycles, gaze saccades between fixations, and thoughtful squints during thinking phases.
- **Pure Software Rendering Pipeline:** PAI projects these 3D coordinates onto a 2D viewport using pure affine vector math and draws the lit polygonal wireframe directly with `PyQt6.QPainter`. The result is a smooth, reactive holographic avatar consuming only ~1.2% CPU.

---

## 🖥️ Live Dashboard & State Visualization

The PAI Heads-Up Display (HUD) provides complete real-time situational awareness. The central holographic face reflects the internal state of the assistant through gaze direction, eyelid openness, and eye pupil color coding.

| **Listening Mode** | **Thinking Mode** | **Speaking Mode** |
| :---: | :---: | :---: |
| ![PAI Listening Mode](image/PAI%20Listening%20mode.png) | ![PAI Thinking Mode](image/PAI%20Thinking%20mode.png) | ![PAI Speaking Mode](image/PAI%20Speaking%20mode.png) |
| **Active Gaze · Emerald Glow**<br>Audio waveform tracks microphone input. Ready for voice or keyboard input. | **Thoughtful Gaze · Gold Glow**<br>Model processes input via Gemini ladder. Zero UI stutter or thread freezing. | **Phonetic Lip-Sync · Amber Glow**<br>Formant-synced mouth movement (~50 fps). Audio waveform tracks PAI's voice. |

### Dashboard Interface Elements

- **SYS MONITOR (Top-Left):** Real-time hardware telemetry tracking CPU utilization, RAM consumption, network throughput, GPU status, uptime, active processes, and OS platform.
- **ACTIVITY LOG (Top-Right):** Clean, real-time audit log of system events, tool invocations, audio statuses, and memory reads.
- **FILE UPLOAD (Middle-Right):** Instant multi-modal drop zone supporting images, video, audio, PDFs, source code, and structured data files.
- **COMMAND INPUT & CONTROLS (Bottom-Right):** Hybrid command input field, instantaneous `INTERRUPT [ESC]` button, and live microphone status indicator.
- **SECURITY & CORE STATUS (Bottom-Left):** Real-time indicators verifying `AI CORE ACTIVE`, `SEC CLEARED`, and the active `SYS KNOT 4.0.3-v` patch tier.

---

## 🔮 **FUTURE ROADMAP: PAI ∂ 2.0 ("Dev Mode")**

The upcoming generation release, **PAI ∂ 2.0**, introduces major system expansions, architectural refactorings, security patch upgrades, and the flagship **Developer Mode ("Dev Mode")**.

![PAI Dev Mode Visualization](image/future%20update.png)

### Key Highlights of PAI ∂ 2.0

- **Dedicated Wake Word:** Activate instantly with the vocal phrase:
  > **`"Prosenjit enable developer mode"`**
- **Cybernetic Crimson HUD Transformation:** Upon activation, the entire HUD transitions from calm cyan to aggressive high-alert **Crimson Red**, complete with glowing red wireframe vertex lighting, high-contrast telemetry panels, and the prominent **`[ Dev mode activated ]`** HUD status beacon.
- **Deep Codebase & Workspace Intelligence:**
  - Full AST indexing of local Git repositories and active coding workspaces.
  - Multi-file automated code editing, refactoring, and linting routines.
  - Integrated terminal execution with real-time build and error tracing.
  - Direct shell script synthesis with explicit sandboxed confirmation boundaries.
- **Next-Gen Security Specification (`Sys Knot ∇`):**
  - Upgrading from `Sys Knot 4.0.3-v` to the target **`Sys Knot ∇` (Nabla/Del)** architecture.
  - Hardened cryptographic protection for local confidential repositories, preventing unauthorized automated read/write operations outside project roots.
- **Offline Code LLM Fallback:** Hybrid local-model routing for offline code comprehension and local diff generation when internet access is unavailable.

---

## 🏛️ System Architecture & Workflow

PAI is architected into modular, decoupled layers to maintain a strict separation of concerns, thread safety, and sub-second responsiveness.

```
                      ┌───────────────────────────────────────────┐
                      │            USER INTERACTION               │
                      │  Voice (Mic/Wake Word)  │ Keyboard / Files│
                      └─────────────────────┬─────────────────────┘
                                            │
                                            ▼
                      ┌───────────────────────────────────────────┐
                      │              CORE ENGINE                  │
                      │ ┌───────────────┐       ┌───────────────┐ │
                      │ │ Audio Devices │       │ Hotkey Engine │ │
                      │ │ (DirectSound) │       │ (Ctrl+Space)  │ │
                      │ └───────┬───────┘       └───────┬───────┘ │
                      │         │                       │         │
                      │         ▼                       ▼         │
                      │ ┌───────────────────────────────────────┐ │
                      │ │        Acoustic Echo Guard            │ │
                      │ └───────────────────┬───────────────────┘ │
                      └─────────────────────┼─────────────────────┘
                                            │
                    ┌───────────────────────┴───────────────────────┐
                    │                                               │
                    ▼                                               ▼
      ┌───────────────────────────┐                   ┌───────────────────────────┐
      │     GEMINI LIVE API       │                   │    GEMINI REST LADDER     │
      │  Bidirectional Audio Stream│                  │  9-Tier One-Shot Fallback │
      │  Low-Latency Live Dialogue│                   │  Active Outage Cooldowns  │
      └─────────────┬─────────────┘                   └─────────────┬─────────────┘
                    │                                               │
                    ▼                                               ▼
      ┌───────────────────────────┐                   ┌───────────────────────────┐
      │   VISEME & AVATAR RIG     │                   │     TOOL DISPATCHER       │
      │ Formant Extraction (~50Hz)│                   │ ┌───────────────────────┐ │
      │ 468-Vertex Software Mesh  │                   │ │ OS & Window Control   │ │
      │ Real-time QPainter HUD    │                   │ │ Browser Automation    │ │
      └───────────────────────────┘                   │ │ File Controller & Undo│ │
                                                      │ │ Hardware Telemetry    │ │
                                                      │ └───────────────────────┘ │
                                                      └─────────────┬─────────────┘
                                                                    │
                                            ┌───────────────────────┴─────────────┐
                                            │                                     │
                                            ▼                                     ▼
                              ┌───────────────────────────┐         ┌───────────────────────────┐
                              │     LOCAL MEMORY STORE    │         │  UI CONFIRMATION GATE     │
                              │ Budgeted Prompt Index     │         │ Hardware UI Token Issued  │
                              │ Sub-ms Local JSON Recall  │         │ For Irreversible Actions  │
                              └───────────────────────────┘         └───────────────────────────┘
```

### End-to-End Processing Workflow

1. **Audio Capture & Echo Isolation:** Audio inputs stream through measured native host APIs (DirectSound on Windows). The acoustic echo guard drops system audio feedback before it can re-trigger the microphone.
2. **Bimodal Processing:**
   - **Live Conversation:** Directly streams full-duplex audio through Gemini Live API over WebSockets.
   - **One-Shot & Visual Queries:** Routed through the 9-model Gemini fallback ladder with explicit timeouts.
3. **Viseme Lip-Sync & Face Mesh Rig:** Transcripts and audio formants are converted into 50 mouth shapes/second, driving the software 3D face mesh in real time.
4. **Execution & Reversibility:** Tool calls invoke isolated action handlers. Destructive actions trigger a UI confirmation token, while file mutations register inverse actions on the undo stack.

---

## 📊 Empirical Benchmarks & Test Results

The architecture of PAI has been rigorously profiled and benchmarked across real-world workloads:

### 1. Gemini Model Ladder Benchmark

Every one-shot call is governed by measured latencies, ensuring the assistant never stalls when an alias goes down:

| Model Tier | Measured Latency | Failover Behavior | Active Cooldown |
| --- | --- | --- | --- |
| `gemini-3.5-flash-lite` | **0.56s** | Primary fast path | None (Healthy) |
| `gemini-3.1-flash-lite` | **0.60s** | Secondary low-latency tier | None (Healthy) |
| `gemini-flash-lite-latest` | **0.60s** | Dynamic rolling tier | None (Healthy) |
| `gemini-2.5-flash` | **0.67s** | Balanced compute tier | None (Healthy) |
| `gemini-2.5-flash-lite` | **0.74s** | High-efficiency tier | None (Healthy) |
| `gemini-3.5-flash` | **1.13s** | Complex synthesis tier | None (Healthy) |
| `gemini-3-flash-preview` | 504 Gateway Timeout | Automatic ladder step | **30 min cooldown** |
| `gemini-3.6-flash` | 504 Gateway Timeout | Automatic ladder step | **30 min cooldown** |
| `gemini-flash-latest` | 503 Service Unavailable | Automatic ladder step | **30 min cooldown** |

> **Efficiency Gain:** Implementing adaptive cooldowns eliminates **11.2 seconds of dead wait time** per call during third-party API outages.

### 2. Audio Subsystem & Latency Profile

| Host Audio Driver | Buffer Latency | Observed Behavior | Deployment Decision |
| --- | --- | --- | --- |
| **DirectSound (Input)** | ~18 ms | Zero dropped frames, robust callback mode | **Selected for Microphone** |
| **MME (Output)** | ~22 ms | Consumed smoothly in real-time | **Selected for Speakers** |
| **DirectSound (Output)** | 0.00 ms | PortAudio silent sink (audio swallowed) | Rejected during startup probe |
| **WASAPI (Shared)** | N/A | Fails on non-48kHz hardware resampling | Avoided for shared compatibility |

### 3. Subsystem Performance Telemetry

- **Avatar Render Cost:** ~1.2% CPU overhead on modern 6-core processors (zero GPU required).
- **Wake Word Detection:** ~1.8% background CPU load using quantized local ONNX models (`openwakeword`).
- **Memory Query Latency:** `< 0.8 ms` to search 500+ facts locally in `memory/long_term.json`.
- **Plugin Auto-Discovery:** Reduced from **211 ms → 39 ms** via non-executing `importlib.util.find_spec` checks.

---

## ⚡ Quick Start & Installation

### 1. Prerequisites

- **Operating System:** Windows 10/11, macOS, or Linux
- **Python:** 3.11, 3.12, or 3.13
- **Hardware:** Microphone and speakers/headphones
- **Gemini API Key:** Free key from [Google AI Studio](https://aistudio.google.com/app/apikey)

### 2. Step-by-Step Setup

```bash
# 1. Clone the repository
git clone https://github.com/probanjee/PAI.git
cd PAI

# 2. Set up virtual environment
python -m venv .venv

# Windows:
.venv\Scripts\activate

# macOS / Linux:
source .venv/bin/activate

# 3. Run the automated installer (installs current OS packages + Playwright)
python setup.py

# 4. Launch PAI
python main.py
```

### 3. First-Run Configuration

- On initial launch, a setup prompt will ask for your **Gemini API Key** (saved locally in `config/api_keys.json`).
- Open **⚙ SETUP → WAKE WORD** to download the offline local wake word model in one click.
- Use **Ctrl+Space** to trigger Push-to-Talk at any time.

---

## 📋 Requirements & OS Compatibility

| Component | Specification | Supported Systems | Notes |
| --- | --- | --- | --- |
| **OS** | Windows 10/11, macOS, Linux | Cross-Platform | Native APIs used per OS |
| **Python** | 3.11 – 3.13 | All | Tested & verified |
| **Display** | Any 1080p+ display | All | Fullscreen (`F11`) or floating HUD |
| **Audio I/O** | 16kHz+ Mic, 24kHz+ Output | All | Dynamically calibrated at startup |
| **GPU** | Not required | All | Software rendered via `QPainter` |
| **Browser Engine** | Chromium (Playwright) | All | Auto-installed by `setup.py` |

---

## 🗂️ Project Structure

```
PAI/
├── main.py                   # Core execution loop: Gemini Live API session, audio I/O & tool dispatch
├── ui.py                     # PyQt6 HUD: avatar renderer, waveform, activity log, settings drawers
├── setup.py                  # OS-aware dependency installer and environment verification
├── requirements.txt          # Python packages with platform-specific environment markers
├── .gitignore                # Protects local API keys, memory databases, and TLS certificates
├── plugins/                  # User plugins directory (auto-discovered on startup)
│   └── _template.py          # Reference template for creating custom skills
├── actions/                  # Core bundled action modules (computer and system controllers)
│   ├── web_search.py         # Multi-mode grounded web search (Gemini + DuckDuckGo)
│   ├── screen_processor.py   # Screen capture & webcam vision analysis
│   ├── background_monitor.py # Scheduled topic and news monitor
│   ├── proactive.py          # Context-aware proactive notifications & morning brief
│   ├── reminder.py           # OS-native notification reminders
│   ├── system_monitor.py     # Hardware telemetry (CPU, RAM, GPU, temperature)
│   ├── computer_settings.py  # Audio volume, display brightness, network, power
│   ├── computer_control.py   # Keyboard shortcuts, mouse input, window control
│   ├── open_app.py           # Cross-platform application launcher
│   ├── browser_control.py    # Playwright-driven browser automation
│   ├── file_controller.py    # Local file operations with undo support
│   ├── file_processor.py     # Document summarization and content extraction
│   ├── send_message.py       # WhatsApp, Telegram, and communication integrations
│   ├── weather_report.py     # Real-time weather reporting
│   ├── video_player.py       # Dual-stream HUD media player
│   └── desktop.py            # Desktop organization and workspace management
├── memory/                   # State, configuration, and persistent memory
│   ├── memory_manager.py     # Long-term knowledge base manager (`long_term.json`)
│   ├── config_manager.py     # Local settings and credential loader (`api_keys.json`)
│   └── long_term.json        # Persistent user memory store (git-ignored)
├── core/                     # Internal subsystems & foundational engines
│   ├── gemini.py             # 9-model Gemini ladder, failover logic, and cooldown timers
│   ├── prompt.txt            # System prompt templates and identity definitions
│   ├── avatar.py             # Software avatar rendering engine (QPainter)
│   ├── avatar_mesh.py        # 3D face geometry, mesh rigging, and interpolation
│   ├── face_model.obj        # MediaPipe 468-vertex 3D facial model
│   ├── viseme.py             # Viseme synthesis & formant-to-mouth mapping
│   ├── echo.py               # Self-echo detection and acoustic guard
│   ├── hotkey.py             # Push-to-talk global/windowed hotkey engine
│   ├── undo.py               # Unified reverse-action transaction journal
│   ├── confirm.py            # Security confirmation token gate for destructive actions
│   ├── audio_devices.py      # Host audio API probe and sink measurement engine
│   ├── plugin_loader.py      # Plugin discovery, dependency check, and sandbox loader
│   ├── action_loader.py      # Core actions loader
│   └── wake_word.py          # Offline "Hey PAI" wake word detection thread
└── config/                   # Local configuration and secure assets
    ├── api_keys.json         # API keys and user preferences (git-ignored)
    └── certs/                # Local self-signed TLS certificates for mobile dashboard (git-ignored)
```

---

## 🔒 Security, Privacy & Data Confidentiality

As detailed in the **Security Philosophy**, PAI enforces absolute data confidentiality:

- **Zero Remote Telemetry:** PAI communicates strictly with official Google Gemini API endpoints during an active live session. No third-party servers, tracking beacons, or telemetry aggregators exist.
- **Local Credentials & Memory:** Personal memories (`memory/long_term.json`) and API keys (`config/api_keys.json`) are stored solely on your hard drive and ignored by Git.
- **Encrypted Local Pairing:** The companion mobile dashboard uses on-device self-signed TLS certificates (`config/certs/`), securing traffic across your local Wi-Fi.
- **Human-in-the-Loop Safeguards:** Destructive OS commands (system shutdown, reboot, network disconnection) cannot be triggered autonomously by the language model; they mandate an interactive human click on the HUD confirmation banner.

---

## 🙏 Third-Party Credits & Lineage

| Asset / Inspiration | Origin | Details |
| --- | --- | --- |
| **Face Geometry** | [MediaPipe](https://github.com/google-ai-edge/mediapipe) | 468-vertex human face model (Apache License 2.0) |

---

## ⚠️ License

This project is licensed for **personal and non-commercial use only** under the **[Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/)**.

---

## 👤 Connect with the Creator

Engineered by **Prosun Banerjee** (**probanjee**).

| Platform | Link |
| --- | --- |
| 🌐 **Website** | [probanjee.vercel.app](https://probanjee.vercel.app/) |
| 🐙 **GitHub** | [@probanjee](https://github.com/probanjee) |
| 💡 **LeetCode** | [Prosun01](https://leetcode.com/u/Prosun01) |
| 💼 **LinkedIn** | [Prosun Banerjee](https://linkedin.com/in/prosun-banerjee-545942293) |
| ✉️ **Email** | [prosunbanerjee8@gmail.com](mailto:prosunbanerjee8@gmail.com) |
