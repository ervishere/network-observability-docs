# Network Observability Runbook

Welcome to the internal documentation for the Network Observability and Alerting stack.

## Project Purpose
Transforming a rooted Android device (Snapdragon 888) into a low-power, dedicated network observability appliance via an Ubuntu chroot environment.

## High-Level Topology
Android Kernel -> Ubuntu Chroot -> Supervisor Daemon -> Telemetry Stack (Prometheus, Loki, Grafana, Promtail, Blackbox Exporter, Alertmanager) -> Mesh Network (Tailscale) -> Slack Notifications.

## System Resource Footprint
- **Memory Management**: Low memory profile by running native Linux binaries directly.
- **CPU Efficiency**: Leveraging the Snapdragon 888 ARM64 architecture natively.
- **Optimization**: Disabling unnecessary background LLM daemons to preserve resources.
