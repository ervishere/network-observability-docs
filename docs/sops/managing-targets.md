# Standard Operating Procedure: Managing Probed Targets

This document outlines how to add or remove monitored network hosts.

## Step 1: Edit Target Definitions
Edit the target definitions in `/opt/prometheus/prometheus.yml`. Add or remove IPs under the `blackbox_icmp` job `static_configs`.

## Step 2: Validate YAML Syntax
Validate the YAML syntax using the Promtool validator:
```bash
/opt/prometheus/promtool check config /opt/prometheus/prometheus.yml
```

## Step 3: Grant Raw Network Permissions
If ICMP probes fail with permission errors, ensure raw network capabilities are granted to Blackbox Exporter:
```bash
setcap cap_net_raw+ep /opt/blackbox_exporter/blackbox_exporter
```

## Step 4: Reload Prometheus
Apply the changes by restarting Prometheus via Supervisor:
```bash
supervisorctl restart prometheus
```
