# Initial Chroot & Stack Setup

## 1. Chroot Environment Deployment
- Require Root privileges (`su`) on Android.
- Mount essential pseudo-filesystems (`proc`, `sys`, `dev`, `pts`).
- Enter the chroot shell.

## 2. Base Packages Installation
Ensure the following packages are installed: `supervisor`, `rsyslog`, `curl`, `python3`, `libcap2-bin`.

## 3. Observability Stack Binary Installation Paths
- `/opt/prometheus/`
- `/opt/loki/`
- `/opt/promtail/`
- `/opt/grafana/`
- `/opt/blackbox_exporter/`
- `/opt/alertmanager/`

## 4. Supervisor Master Configuration
The Supervisor master configuration is located at `/etc/supervisor/conf.d/observability.conf`, which manages all binaries simultaneously.
