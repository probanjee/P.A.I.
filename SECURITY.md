# 🛡️ PAI Security Policy & Threat Model

[![Security Patch](https://img.shields.io/badge/Security%20Patch-Sys%20Knot%204.0.3--v-emerald?style=for-the-badge)](#active-security-version-and-patch-architecture)
[![System Build](https://img.shields.io/badge/System%20Build-D.20.1v-purple?style=for-the-badge)](#supported-versions)
[![Core Project](https://img.shields.io/badge/Core%20Project-Pi%20%E2%88%82-blue?style=for-the-badge)](#supported-versions)
[![License](https://img.shields.io/badge/License-CC%20BY--NC%204.0-orange?style=for-the-badge)](https://creativecommons.org/licenses/by-nc/4.0/)

> **Prosenjit** — Practical Assistant Inside (PAI)
> **Engineered by Prosun Banerjee** ([@probanjee](https://github.com/probanjee))*

---

## 🔒 Executive Security Overview & Philosophy

**PAI (Practical Assistant Inside)** is designed from the ground up on the principle of **uncompromising digital sovereignty, absolute local confidentiality, and defense-in-depth desktop safety**. Unlike cloud-tethered voice assistants and SaaS chatbots that harvest telemetry and store private audio on corporate servers, PAI executes all system automation, memory lookups, and visual processing **entirely within your local user-space**.

Our core security architecture focuses on:

1. **Zero External Telemetry:** Direct communication is strictly confined to official Google Gemini API endpoints (full-duplex WebSockets for Live voice interaction and authenticated REST for fallback/multimodal analysis). No analytics beacons, third-party analytics SDKs, or background servers are included.
2. **Deterministic UI Token Gates:** Language models are probabilistic and vulnerable to prompt injection or hallucination. PAI strictly prohibits the AI model from confirming or executing irreversible operations on its own authority.
3. **Continuous Transaction Reversibility:** Any state mutation that can be undone is tracked in an in-memory transactional undo journal, providing instant recovery from misunderstanding or malicious tool calls.
4. **Hardened Filesystem Boundaries:** File manipulation is restricted to safe user-space roots, with protected core operating system directories and safe trash recycling preventing data loss.

---

## 📦 Supported Versions

Security updates, firewall integration patches, and vulnerability remediations are tracked under the **Sys Knot** security specification and cumulative **System Build** releases.

| Version Track | Build Identifier | Security Patch Tier | Status | Security Support Level |
| :--- | :--- | :--- | :---: | :--- |
| **Current Operational** | `D.20.1v` | `Sys Knot 4.0.3-v` | :white_check_mark: **Active** | Full active security support & vulnerability patching |
| **Core Architecture** | `Pi ∂` (Base) | `Sys Knot 4.0.x` | :white_check_mark: **Supported** | Critical security patches only |
| **Upcoming Roadmap** | `PAI ∂ 2.0` (Dev Mode) | `Sys Knot ∇` (Nabla) | :construction: **Planned** | Next-gen cryptographic isolation & sandboxed terminal |
| **Legacy Builds** | `< D.20.0` | `Sys Knot < 4.0` | :x: **End of Life** | Unsupported; upgrade to `D.20.1v` immediately |

### Active Security Version & Patch Architecture

- **Active Patch Tier:** `Sys Knot 4.0.3-v`
  - **Sys Knot:** System Knot represents PAI's internal security architecture and hardened firewall integration layer (**Sys** defines internal core topology, **Knot** specifies the hardened patch level).
  - **4 (Major):** System-level security architecture generation.
  - **0 (Major Revisions):** Architectural overhaul tier within generation 4.
  - **3 (Minor Updates):** Cumulative security revisions, patch level, and hardening fixes.
  - **v:** Standard release verification tag.

---

## 🛡️ Defense-in-Depth Security Architecture

```
                       ┌───────────────────────────────────────────────┐
                       │          UNTRUSTED INPUT CHANNELS             │
                       │ Voice / Transcripts / Web Content / Documents │
                       └───────────────────────┬───────────────────────┘
                                               │
                                               ▼
                       ┌───────────────────────────────────────────────┐
                       │            GEMINI LIVE / REST ENGINE          │
                       │           Generates Proposed Tool Call        │
                       └───────────────────────┬───────────────────────┘
                                               │
                                               ▼
                       ┌───────────────────────────────────────────────┐
                       │           PAI SECURITY DISPATCHER             │
                       └───────┬───────────────────────────────┬───────┘
                               │                               │
            Is Action Irreversible?                 Is Action Reversible?
         (shutdown, restart, wifi_toggle)         (volume, write_file, move_file)
                               │                               │
                               ▼                               ▼
               ┌───────────────────────────────┐ ┌───────────────────────────┐
               │    UI CONFIRMATION GATE       │ │  TRANSACTIONAL UNDO STACK │
               │     [core/confirm.py]         │ │      [core/undo.py]       │
               │  Interactive Human Click on   │ │ Pushes inverse operation  │
               │  HUD Banner Required          │ │ onto 10-step LIFO journal │
               │  (90-second hardware timeout) │ └─────────────┬─────────────┘
               └───────────────┬───────────────┘               │
                               │                               │
                      Approved by User                         ▼
                               │                 ┌───────────────────────────┐
                               └────────────────►│   SANDBOXED FILESYSTEM    │
                                                 │   [_SAFE_ROOTS & Trash]   │
                                                 └───────────────────────────┘
```

### 1. UI Confirmation Token Gate (`core/confirm.py`)

Conventional tool-calling architectures often pass a boolean flag like `confirmed=True` inside the tool parameters. **This is fundamentally vulnerable to prompt injection**, as an attacker or an over-eager LLM can simply forge `confirmed=True` during tool generation.

PAI eliminates this vulnerability:

- **Human-Issued Tokens Only:** Irreversible actions (`shutdown`, `restart`, `toggle_wifi`) are intercepted and parked by `core.confirm.request()`.
- **Zero Model Bypass:** The action is never executed until the human physically clicks **CONFIRM** on the PyQt6 HUD interface banner.
- **Asynchronous & Non-Blocking:** The assistant continues conversational interaction without UI freezes, auto-expiring pending requests after a strict **90-second timeout**.

### 2. Transactional Undo Engine (`core/undo.py`)

Rather than causing cognitive fatigue by interrupting the user with prompts for mundane actions, PAI operates on an **active reverse-action model**:

- Every state mutation (volume adjustment, display brightness change, file creation, content modification, or file move) captures a reverse callable and pushes it to `core.undo.push_undo()`.
- A 10-operation rolling LIFO journal preserves quick recovery via voice (`"Undo that"`) or HUD interaction.
- If an undo callable raises an exception, it fails safely without destabilizing the running application thread.

### 3. Filesystem Scoping & Safe-Directory Isolation (`actions/file_controller.py`)

PAI controls local file workflows under strict defensive guardrails:

- **`_SAFE_ROOTS` Boundary Enforcement:** Operations are confined to user-space directories (`Path.home()`). Attempts to traverse into arbitrary root folders, system kernels, or operating system system32/bin directories are rejected with `Access denied`.
- **Protected Core Directories:** Critical user directories (Desktop, Downloads, Documents, Pictures, Music, Videos, and Home root) are protected from bulk deletion or accidental wiping.
- **Recycle Bin / Trash Routing:** Deletions use `send2trash` or the native OS Recycle Bin (`win32com` BitBucket on Windows). Files are never permanently unlinked on the first action, allowing immediate manual or automated restoration.
- **Memory Buffer Caps:** Content reads and writes enforce a `1,000,000` character threshold (`_UNDO_CONTENT_LIMIT`) to protect the host against denial-of-service (DoS) via memory exhaustion from oversized files.

### 4. Credential & Memory Protection (`memory/config_manager.py`)

- **Git-Ignored Secrets:** Local API keys (`config/api_keys.json`), persistent memory facts (`memory/long_term.json`), and TLS certificates (`config/certs/`) are explicitly excluded from version control via `.gitignore`.
- **Local Key Storage:** API keys are read locally from the host disk and injected directly into runtime headers; they are never uploaded, logged to external aggregators, or mirrored to external endpoints.

### 5. Local Network & Companion Dashboard Security

- **Self-Signed TLS:** The companion mobile HUD communicates exclusively across your local area network (LAN) using on-device self-signed certificates in `config/certs/`.
- **No WAN Ingress:** PAI does not expose public listening ports, reverse proxies, or cloud relays.

### 6. Plugin Extensibility Containment (`core/plugin_loader.py`)

- **Validated Identifiers:** Plugin names are strictly sanitized against alphanumeric regex boundaries (`^[a-zA-Z_][a-zA-Z0-9_]{0,63}$`).
- **Fault Containment:** Plugins run in isolated worker contexts with explicit exception traps (`traceback.print_exc()`), preventing rogue or crashing third-party scripts from terminating the main audio/UI loop.

---

## 🎯 Threat Model & Specific Attack Scenarios

| Attack Vector | Threat Scenario | Mitigation in PAI |
| :--- | :--- | :--- |
| **Indirect Prompt Injection** | Malicious text in a scraped webpage, email, or PDF instructs PAI to execute destructive commands (e.g., `"Shut down computer"`). | **Mitigated:** Irreversible actions require interactive human click via `core/confirm.py`. Malicious file changes can be reverted via `core/undo.py`. |
| **Path Traversal / Data Exfiltration** | Prompt directs assistant to read sensitive root system files (e.g., `/etc/shadow` or `C:\Windows\System32`). | **Mitigated:** `_is_safe_path()` checks enforce strict `_SAFE_ROOTS` user-space boundaries. |
| **Accidental Data Loss** | The assistant mishears a command and deletes a critical user directory or file. | **Mitigated:** Protected directory lists prevent root deletion; all deletions route through native OS Trash with automatic undo hooks. |
| **Credential Hijacking** | A rogue tool call attempts to print or transmit API keys stored in `config/api_keys.json`. | **Mitigated:** Core configuration managers isolate API key strings from general conversational prompt injections; files are git-ignored. |
| **DoS via Memory Bomb** | Reading a massive file causes high memory consumption, freezing the system. | **Mitigated:** `_UNDO_CONTENT_LIMIT` (1 MB cap) and `max_chars=4000` truncate large inputs, preserving RAM stability. |

---

## 🚨 Reporting a Vulnerability

We deeply appreciate the efforts of security researchers, developers, and users who help keep PAI and its community safe through responsible disclosure.

### How to Report

If you discover a security vulnerability or exploit in PAI, **please DO NOT open a public GitHub issue**. Instead, submit a private disclosure through one of the following channels:

- ✉️ **Primary Security Email:** [prosunbanerjee8@gmail.com](mailto:prosunbanerjee8@gmail.com)
- 🐙 **GitHub Security Advisories:** Submit a private advisory via [GitHub Security Advisories](https://github.com/probanjee/PAI/security/advisories/new) (if enabled on the repository)

### What to Include in Your Report

To help us triage and resolve the issue quickly, please provide:

1. **Title & Summary:** A concise overview of the vulnerability and its potential impact.
2. **Affected Version:** The System Build (e.g., `D.20.1v`) and Security Patch tier (e.g., `Sys Knot 4.0.3-v`).
3. **Target Environment:** Operating system (Windows 10/11, macOS, Linux) and Python version.
4. **Step-by-Step Proof of Concept (PoC):** Detailed reproduction steps, sample prompts, or exploit payloads.
5. **Impact Assessment:** Explain how an attacker could exploit this vulnerability (e.g., unauthorized file access, prompt injection bypass, arbitrary execution).
6. **Suggested Fix:** (Optional) Code patch, regex improvement, or configuration adjustment.

---

## ⏱️ Response Timetable & SLA

We are committed to rapid response and coordinated vulnerability remediation:

```
  [0 - 48 Hours]           [3 - 5 Days]             [7 - 14 Days]           [Post-Patch]
 Initial Triage    ──►   Root-Cause &   ──►   Security Patch   ──►   Coordinated Public
& Acknowledgment         Risk Analysis         Release & Test            Disclosure
```

- **Acknowledgment:** Within **24 to 48 hours**, you will receive an initial response acknowledging receipt of your report.
- **Assessment & Triage:** Within **3 to 5 business days**, we will validate the vulnerability, evaluate its severity score, and determine the remediation approach.
- **Patch Release:** Depending on severity, we aim to deploy a fix within **7 to 14 days** under a new `Sys Knot` security patch level.
- **Coordinated Disclosure:** We will coordinate with you on public release notes and credit your contribution in the advisory (unless you request anonymity).

---

## 💡 Operator & User Security Best Practices

To ensure maximum security when running PAI on your local machine:

1. **Protect Your Gemini API Key:** Never commit `config/api_keys.json` or `.env` files to public version control. Rotate your API keys periodically via [Google AI Studio](https://aistudio.google.com/app/apikey).
2. **Use an Isolated Virtual Environment:** Always run PAI inside a dedicated Python virtual environment (`python -m venv .venv`), preventing dependency conflicts with system packages.
3. **Audit Third-Party Plugins:** Review any custom `.py` scripts placed in `plugins/` before running the assistant. Only install extensions from sources you trust.
4. **Keep OS and Drivers Updated:** Audio drivers (DirectSound/MME) and system packages receive routine OS patches that ensure hardware stability and latency optimization.
5. **Never Bypass Confirmation Gates:** Do not modify `core/confirm.py` or `_IRREVERSIBLE` action dictionaries to remove the human-in-the-loop HUD approval requirement.

---

## 🔮 Future Security Roadmap (`Sys Knot ∇`)

As outlined in the **PAI ∂ 2.0 ("Dev Mode")** roadmap, future updates will introduce the **`Sys Knot ∇` (Nabla)** security tier:

- **Cryptographic File Vaulting:** Hardware-backed and AES-GCM encrypted sandboxes for sensitive user repositories.
- **Isolated Developer Mode Sandbox:** Ephemeral containerization for automated shell script execution and terminal tool calls during developer tasks.
- **Strict Out-of-Bounds Path Traversal Blocking:** Machine-level enforcement prohibiting write or execution access outside the explicit Git workspace root.

---

*For general questions, non-sensitive feature discussions, or architectural inquiries, please visit our [Discussions / Issues](https://github.com/probanjee/PAI) or contact [Prosun Banerjee](https://probanjee.vercel.app/).*
