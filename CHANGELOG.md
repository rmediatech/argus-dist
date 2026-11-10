# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.3.0] - 2026-11-07

### Architectural Ground-Floor Rebuild (`SOVEREIGN-CHANGELOG-E2E-01`)

- **`[Hardware/Kernel]` & `[State/SST]` Zero-Dependency Somatic Hardware Pressure, Thermal & AI/LLM Process Radar (`src/collectors/somatic.rs`, `argus somatic`)**:
  - **Root Cause Dissection**: Prior `argus` releases monitored network TCP latency and Smart TV ADB playhead telemetry, but lacked visibility into local Linux kernel resource stalls (PSI) and autonomous AI/LLM inference/agent workloads (`ollama`, `llama-server`, `vllm`, `antigravity`/`agy`, `claude`, `codex`) competing with sovereign defense daemons for CPU, RAM, and I/O bandwidth.
  - **Architectural & Mathematical Resolution**:
    1. Engineered `argus::collectors::somatic` in pure Rust directly atop `/proc/pressure/{cpu,memory,io}`, `/proc/meminfo`, `/proc/loadavg`, `/sys/class/thermal/thermal_zone*/temp`, and `/proc/[pid]/{comm,cmdline,status}` with zero external `sysinfo` or `libc` dependencies.
    2. Implemented `parse_psi_content` extracting `some` and `full` 10s/60s/300s stall averages and cumulative stall microseconds, with `SystemPressure::is_throttling()` flagging contention at `cpu >= 15%`, `mem_some >= 10%`, or `mem_full >= 2%`.
    3. Implemented `classify_process_workload` categorizing processes into `WorkloadClass::AiInference`, `WorkloadClass::AiAgent`, `WorkloadClass::SovereignDaemon`, and `WorkloadClass::Standard`, ranked by resident memory (`VmRSS`) and thread count.
    4. Hardened `/proc/[pid]/cmdline` ingestion via `sanitize_proc_text` (`MAX_PROC_SCAN_PIDS = 4096`, `MAX_CMDLINE_LEN = 240`), stripping raw ANSI CSI/OSC escape sequences and neutralizing spreadsheet formula injection payloads (`'=`).
    5. Integrated live somatic telemetry into `NodeInspectorWidget` in the interactive TUI and exposed `argus somatic [--json]` for CLI and automated fleet telemetry pipelines.
  - **Empirical Verification**: Verified via `tests/adversarial_somatic_and_ai_radar_tests.rs` against corrupted procfs PSI/meminfo/thermal outliers, ANSI terminal poisoning payloads, and live Linux kernel inspection.

## [0.2.0] - 2026-11-01

### Added
- **Sovereign Cinema & Smart TV Playhead Collector (`src/collectors/cinema.rs`)**: High-precision non-DRM hardware `media_session` and `power` state interrogator over ADB for Fire TV and Google TV nodes.
- **Kernel-Anchored Playhead Calculation**: Synchronizes live playhead milliseconds against kernel wake uptime without latency drift or sleep distortion.
- **Synchronized SRT Subtitle Cue Matcher**: Live matching and windowed extraction of scene dialogue cues from local `.srt` files (`[playhead_ms - 15s, playhead_ms + 35s]`).
- **Autonomous Sleeping HDMI Self-Heal**: Automatically detects sleeping screens during active playback and injects non-invasive `KEYEVENT_WAKEUP` (code `224`) to eliminate black screens.
- **Adversarial Security Hardening**: Added spreadsheet formula injection neutralization (`'=`), ANSI escape code stripping, and boundary stress tests in `tests/adversarial_collector_tests.rs`.
- **`argus cinema` Command**: CLI entry point supporting live telemetry reporting and synchronized subtitle observation (`argus cinema --host 192.168.1.158:5555 --srt movie.srt`).

## [0.1.0] - 2026-10-03

### Added
- **TUI Factory Singleton & RAII Terminal Guard**: Crash-resilient terminal initialization with global `std::panic::set_hook` ensuring zero terminal corruption upon unexpected crashes.
- **Polar Radar Sweep Widget**: Mathematical ASCII/Unicode circular radar sweep with angular trails and active blip pings.
- **Interactive Fleet Node Table**: Real-time fleet health matrix with color-coded status, latency badges, and instant muting toggles (<kbd>Space</kbd>).
- **Live Threat Ticker**: High-velocity circular ring-buffer stream capturing sinkhole events from `aegis`, `phylax`, and `propylea`.
- **Node Telemetry Inspector**: Detailed node metadata drawer with sparkline latency history.
- **Ghost Mode**: Real-time IP address redaction (<kbd>g</kbd>) for secure public screencasts and operator demonstrations.
- **Demo Adversarial Stream**: Cyclic threat event generator (<kbd>d</kbd>) for realistic offline HUD exercising.
- **Native Discovery Engine**: CLI command (`argus discover`) to auto-detect running local sovereign daemons.
- **Adversarial Self-Attack Test Battery (`POC TDD+++++`)**: 9 comprehensive test suites validating terminal panic recovery, ring-buffer allocation limits, viewport boundary resilience, formula injection defense, and blackhole probe timeouts.
- **Cryptographic Provenance (`SOVEREIGN-SIGN-01`)**: Full release signing manifest (`SHA256SUMS.asc`) using the sovereign release key.
