# Network Observability Runbook

Welcome to the internal documentation for the Network Observability and Alerting stack. This system provides real-time ICMP monitoring and proactive alerting for our core network infrastructure.

## Architecture Overview

The alerting pipeline is hosted on a localized Ubuntu environment and follows a strict event flow:

**Blackbox Exporter** -> **Prometheus** -> **Alertmanager** -> **Slack**

1. **Blackbox Exporter:** Executes raw ICMP (ping) probes every 5 seconds against critical external and internal targets.
2. **Prometheus:** Scrapes probe metrics from Blackbox and evaluates them against custom alerting rules.
3. **Alertmanager:** Receives firing events from Prometheus, handles grouping and deduplication, and routes notifications.
4. **Slack Webhook:** Pushes color-coded alerts (🔴 Critical / ✅ Resolved) to the designated Slack channel.

## Component Directory

| Service | Binary Path | Configuration File |
|---|---|---|
| **Prometheus** | `/opt/prometheus/prometheus` | `/opt/prometheus/prometheus.yml` |
| **Alert Rules** | N/A | `/opt/prometheus/alerts/icmp.yml` |
| **Blackbox Exporter** | `/opt/blackbox_exporter/blackbox_exporter` | `/opt/blackbox_exporter/blackbox.yml` |
| **Alertmanager** | `/opt/alertmanager/alertmanager` | `/opt/alertmanager/alertmanager.yml` |

## Service Management (Supervisor)

All observability processes are managed via Supervisor (`/etc/supervisor/conf.d/observability.conf`).

- **Check service status:** `supervisorctl status`
- **Restart service:** `supervisorctl restart prometheus`
- **Tail logs:** `tail -f /var/log/supervisor/prometheus-stdout*.log`
