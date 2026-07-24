# Standard Operating Procedure: Add or Remove Target IPs

This document details how to modify the list of network hosts monitored by Blackbox Exporter and Prometheus.

## Step 1: Modify Prometheus Configuration
Open `/opt/prometheus/prometheus.yml` in an editor:
```bash
sudo nano /opt/prometheus/prometheus.yml
```

Locate the `blackbox_icmp` job under `scrape_configs`:
```yaml
- job_name: 'blackbox_icmp'
    metrics_path: /probe
    params:
      module: [icmp]
    static_configs:
      - targets:
          - 8.8.8.8          # Public DNS / WAN Check
          - 192.168.100.1    # Default Gateway
          - 192.168.102.110  # Local Host
          # Add new IP addresses below
```

## Step 2: Restart Prometheus
After modifying and saving the file, restart Prometheus via Supervisor:
```bash
supervisorctl restart prometheus
```
