# Architecture Overview & Data Flows

## 1. Host & Containerization Layer
- **Chroot Isolation**: Runs natively on top of the Android Linux kernel at `/data/local/tmp/ubuntu`.
- **Supervisor**: A process controller managing all service lifecycles (`/etc/supervisor/conf.d/observability.conf`).

## 2. Log Ingestion Flow
`rsyslog` receiving network syslogs -> Promtail parsing and shipping -> Loki indexing (`http://127.0.0.1:3100`).

## 3. Metrics & Probing Flow
Blackbox Exporter performing ICMP probes every 5s -> Prometheus scraping `/probe` endpoints (`http://127.0.0.1:9090`).

## 4. Alerting Pipeline
Prometheus evaluating rules (`/opt/prometheus/alerts/icmp.yml`) -> Alertmanager (`http://127.0.0.1:9093`) -> Incoming Slack Webhook (`#general`).

## 5. Visualization Layer
Grafana (`http://127.0.0.1:3000`) querying Loki and Prometheus data sources.
