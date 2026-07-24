# CLI & API Reference Manual

A cheat sheet for all system interfaces.

## 1. CLI Commands
- **`promtool`**: Validation commands for rules and main config.
- **`logger`**: Generating synthetic test logs (`logger -p daemon.err "test message"`).
- **`supervisorctl`**: Process control commands.

## 2. LogQL Reference
- **Basic query:** `{job="syslog"}`
- **Filter query:** `{job="syslog"} |= "error" != "keepalive"`
- **Aggregation query:** `sum(count_over_time({job="syslog"} |= "block" [1h]))`

## 3. API Endpoints
- **Prometheus Metrics:** `GET http://127.0.0.1:9090/metrics`
- **Loki Query Range:** `GET http://127.0.0.1:3100/loki/api/v1/query_range`
- **Alertmanager API:** `POST http://127.0.0.1:9093/api/v2/alerts`
- **Blackbox Probe:** `GET http://127.0.0.1:9115/probe?module=icmp&target=8.8.8.8`
