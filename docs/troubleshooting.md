# Troubleshooting & Diagnostic Guide

Diagnostic workflows for common infrastructure failures in the observability stack.

## 1. Prometheus "Spawn Error" or Startup Crash
- **Cause:** Invalid YAML indentation or duplicate root keys (`alerting:`, `rule_files:`) caused by append commands (`cat >>`).
- **Fix:** Inspecting `/var/log/supervisor/prometheus-stderr*.log` and running `promtool check config`.

## 2. Blackbox Exporter Permission Denied (ICMP)
- **Cause:** Lack of `cap_net_raw` socket capabilities inside the chroot environment.
- **Fix:** Executing `setcap cap_net_raw+ep /opt/blackbox_exporter/blackbox_exporter`.

## 3. Alertmanager Webhook Failures
- **Cause:** Misconfigured Slack Webhook URL, wrong channel name, or network unreachability.
- **Fix:** Testing Slack connection using direct `curl` payloads to `http://127.0.0.1:9093/api/v2/alerts`.

## 4. Loki Log Ingestion Gaps
- **Cause:** Time drift between Android host and Ubuntu chroot, or Promtail offset errors.
- **Fix:** Ensure NTP synchronization and check Promtail logs for position file errors.
