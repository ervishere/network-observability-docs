# Network Observability Runbook

Welcome to the **Network Observability Runbook** repository!

This repository houses the complete MkDocs-based documentation for our custom, low-power network observability stack. The system is uniquely built on top of a rooted Android device running an Ubuntu chroot environment, turning it into a dedicated telemetry and alerting appliance.

## 📖 Live Documentation
**[View the Live Documentation here (via GitHub Pages)](#)** 
*(Note: Replace `#` with the actual GitHub Pages URL once deployed!)*

## 🚀 Features & Architecture
- **Host**: Android Kernel (Snapdragon 888) -> Ubuntu Chroot
- **Metrics & Probing**: Prometheus + Blackbox Exporter (ICMP monitoring)
- **Log Management**: rsyslog + Promtail + Loki
- **Alerting**: Alertmanager -> Slack Notifications
- **Visualization**: Grafana

## 🛠️ Repository Structure
- `mkdocs.yml`: The master configuration file for the MkDocs site (using the Material theme).
- `docs/`: Contains all Markdown documentation files.
  - `index.md`: Architecture overview.
  - `setup/`: Initial deployment guides.
  - `sops/`: Standard Operating Procedures (e.g., adding/removing target IPs, managing background services).
  - `troubleshooting.md`: Common issues and their fixes.
  - `reference.md`: CLI and API cheat sheet.
- `.github/workflows/deploy-docs.yml`: GitHub Actions pipeline for automated deployment.

## ⚙️ Building Locally
To preview this documentation on your local machine:

1. Install MkDocs and the Material theme:
   ```bash
   pip install mkdocs-material
   ```
2. Run the local development server:
   ```bash
   mkdocs serve
   ```
3. Open `http://127.0.0.1:8000` in your browser.
