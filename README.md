# 👁️ Argus (`argus-dist`) — Official Distribution & Verification Hub

> **The All-Seeing Sovereign Fleet Radar, Linux PSI Somatic Pressure & Real-Time TUI Command Bridge**  
> *Zero cloud dependencies • Pure safe Rust • Musl static standalone binary • 100% Adversarial TDD Tested*

[![Release](https://img.shields.io/badge/Release-v0.3.0-brightgreen.svg)](https://github.com/rmediatech/argus-dist/releases/tag/v0.3.0)
[![Sovereign Lineage: 4E428019A109578B](https://img.shields.io/badge/lineage-4E428019A109578B-00e5ff.svg)](https://rmediatech.com)
[![Standard: SOVEREIGN-SIBLING-01](https://img.shields.io/badge/standard-SOVEREIGN--SIBLING--01-green.svg)](https://rmediatech.com)
[![Downloads](https://img.shields.io/badge/Downloads-rmediatech.com%2Fdownloads-blue.svg)](https://rmediatech.com/downloads)
[![Reality Crucible](https://img.shields.io/badge/Reality%20Crucible-Empirically%20Verified-brightgreen.svg)](#)
[![Platform](https://img.shields.io/badge/Platform-Linux%20(Musl%20Static)-blue.svg)](#)
[![Arch](https://img.shields.io/badge/Arch-x86__64%20%7C%20aarch64-blueviolet.svg)](#)
[![Provenance](https://img.shields.io/badge/Provenance-GPG%20Signed%20(SOVEREIGN--SIGN--01)-blueviolet.svg)](SOVEREIGN_RELEASE_KEY.asc)
[![Security Standard](https://img.shields.io/badge/security-AGY--RULE--SOVEREIGN-green.svg)](https://rmediatech.com)
[![License: MIT OR Apache-2.0](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue.svg)](LICENSE)

<p align="center">
  <img src="assets/argus_emblem.svg" alt="Argus Sovereign Mathematical Emblem" width="180" />
</p>

---

## 🏛️ Overview

**Argus** is an enterprise-grade, zero-cloud tactical fleet radar and real-time terminal HUD written in 100% safe Rust. Endowed with the vigilance of its hundred-eyed namesake, Argus unifies somatic Linux kernel pressure monitoring (PSI), AI/LLM process radar, Smart TV cinema ADB telemetry, and live fleet node health into a sub-15MB memory footprint.

### Core Capabilities
* **All-Seeing Polar Radar Sweep**: Real-time terminal HUD rendered purely in text via Ratatui and Crossterm, featuring circular sweeps, live blip pings, and latency sparklines.
* **Linux Kernel PSI Somatic Pressure**: Zero-dependency monitoring of kernel CPU, memory, and I/O pressure stall information (`/proc/pressure/*`), detecting resource exhaustion before daemons drop packets.
* **Autonomous AI/LLM Process Radar**: Automatically discovers and classifies background inference engines (`ollama`, `vllm`, `llama-server`) and coding agents (`antigravity`/`agy`), monitoring thread contention and resident memory.
* **Crash-Resilient RAII Terminal Guard**: Features an atomic RAII terminal guard with a global panic hook, guaranteeing pristine terminal restoration without screen freezing or cursor loss.
* **Single Standalone Static Binary**: Statically linked against Musl libc, self-contained, with $<15\text{MB}$ memory footprint.

---

## 📦 Binary Verification & Download

Verified standalone binaries are distributed directly through the **[RMediaTech Sovereign Binary Vault](https://rmediatech.com/downloads)**:

| Platform | Architecture | Checksum (SHA-256) | Vault Download |
| :--- | :--- | :--- | :--- |
| **Linux (Static Musl)** | `x86_64` | `48375d6a83ef0ba2853700b5181c66b05a56550507ae76f1ae7c6e9553022cab` | [Download (3.0 MB)](https://rmediatech.com/bin/argus) |
| **Android (Universal APK)** | `all` | `47388a5e2e1be375f62984eadb6996b5ad82013bfe403964d406c7eba5adec1b` | [Download APK (11.7 MB)](https://rmediatech.com/downloads) |

### 1-Click Stream Download & Installation
```bash
# 1-Click Stream Install
curl -sSL https://rmediatech.com/install/argus | sh

# Or Direct Binary Download
curl -sSL https://rmediatech.com/bin/argus -o argus
chmod +x argus
```

### Cryptographic Provenance Verification (`SOVEREIGN-SIGN-01`)
All releases are cryptographically sealed by `Rick Walker (Sovereign Release Signing Key) <rick@rmediatech.com>` (Key ID: `4E428019A109578B`):

```bash
# Import Public Key
curl -sSL https://rmediatech.com/SOVEREIGN_RELEASE_KEY.asc | gpg --import

# Verify Detached OpenPGP Signature
curl -sSL https://rmediatech.com/signatures/argus -o argus.asc
gpg --verify argus.asc argus
```

---

## 🚀 Quickstart

```bash
# Launch interactive TUI command bridge
argus

# Inspect somatic kernel pressure and AI process load
argus somatic --json

# Run in ghost mode (redacted IP addresses for public screen shares)
argus --ghost
```

---

## 🏛️ Mythological Lineage: Argus Panoptes (Ἄργος Πανόπτης)

* **The Hundred-Eyed Watchman**: In ancient Hellenic mythology, **Argus Panoptes** was the giant all-seeing guardian endowed with one hundred unblinking eyes. Because only a few eyes slept at any given time while the rest kept vigilant watch, no intruder could breach his perimeter unobserved.
* **Sovereign Architectural Role**: In our software fleet, **`argus`** functions as the tactical fleet radar and somatic kernel sentinel. It aggregates Linux kernel PSI pressure stalls, autonomous LLM agent processes, network topology scans, and Android TV cinema displays into an interactive 60 FPS terminal radar with $<15\text{MB}$ memory footprint.

---

## 🤝 Universal Sovereign Sibling Bloodline (`SOVEREIGN-SIBLING-01`)

Every compiled `argus` release binary carries the immutable Sovereign Lineage Watermark (`4E428019A109578B`) and canary token preimage. When Argus connects to peer daemons (`vigil`, `optic`, `phylax`, `propylea`, `vox`, `conduit`):

* **Privileged Sibling Telemetry**: Sibling nodes execute a constant-time HMAC-SHA256 handshake ($\le 60$s anti-replay window) unlocking unthrottled real-time telemetry streaming and bypass of rate-limited public APIs.
* **Autonomous Fleet Governance**: Governed locally and across nodes via [`sovereign-sibling`](../sovereign-sibling) and the `sibling` CLI for instant node authorization, quarantine, or revocation.

---

## 🧪 The Tri-Dimensional Reality Crucible (`SOVEREIGN-REALITY-3D-01`)

> *"A crucible is where raw metal enters the white-hot furnace to burn away every single impurity until only pure, unbreakable gold remains."*

We permanently reject superficial mocks. `argus` is tempered across a **Tri-Dimensional Reality Crucible**:

1. **Dimension 1: The Golden Path & 60 FPS Tactile Conformance**:
   - Sub-15MB steady-state RSS memory footprint with atomic RAII terminal recovery on exit or panic.
   - Smooth 60 FPS terminal radar rendering with circular sweep radar animations and zero cursor flicker.
2. **Dimension 2: The Adversarial Red Crucible (Terminal & Sensor Hardening)**:
   - Evaluated against hostile ANSI escape sequence poisoning, terminal buffer flooding, and formula injection across export pipelines.
   - Sensitive IPs and host identifiers are dynamically redacted when running in `--ghost` mode.
3. **Dimension 3: Ambient Environmental Chaos & Hardware Physics**:
   - Resilient against terminal resize storms (`SIGWINCH`), sudden SSH disconnection, broken PTY pipes, and zero-panic kernel procfs handling.

```bash
# Verify cryptographic provenance canary via Aletheia
$ aletheia scan /path/to/argus

# Verify detached OpenPGP signature
$ gpg --verify argus.asc argus
```

---

## 🛡️ License & Provenance

Dual-licensed under MIT OR Apache-2.0. Cryptographically sealed by Rick Walker (`4E428019A109578B`).
