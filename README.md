# Edge AI Network Observability Stack

This repository contains the Standard Operating Procedures (SOPs), architecture diagrams, and wiki documentation for the locally hosted Network Operations Center (NOC).

## 📌 Core Architecture
The entire stack runs on an edge device (Realme GT2 / Snapdragon 8 Gen 1) utilizing a native Ubuntu 24.04 chroot.

*   **OS/Environment:** PixelOS (Rooted via Magisk), Ubuntu 24.04 Chroot.
*   **Networking:** Tailscale Mesh (`192.168.0.0/16`), Magisk-based Multi-WAN Failover script.
*   **Process Management:** Supervisor (replacing systemd).

## 📚 Documentation Directory
*   [SOP-001: Chroot Initialization & Tailscale Networking](docs/SOP-001-chroot-tailscale.md)
*   [SOP-002: Promtail & rsyslog Pipeline Configuration](docs/SOP-002-syslog-pipeline.md)
*   [SOP-003: Gemini AI Middleware & UI Deployment](docs/SOP-003-ai-middleware.md)
*   [SOP-004: Proactive Alerting & Cron Scheduling](docs/SOP-004-proactive-alerting.md)
