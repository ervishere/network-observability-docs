# SOP-004: Proactive AI Alerting Daemon

## 1. Overview
An autonomous Python script (`proactive_alert.py`) that periodically scans the network logs for critical anomalies and hardware failures.

## 2. Execution Flow
*   **Schedule:** Runs every 15 minutes via the local `cron` daemon.
*   **Query:** Fetches all logs marked with `severity=error` from Loki for the past 15 minutes.
*   **Analysis:** The logs are fed to the `gemini-3.6-flash` model with instructions to identify critical anomalies or repeating hardware noise.
*   **Alerting:** If the AI determines an anomaly exists, it prefixes the output with `STATUS: ALERT` and pushes a notification directly to a configured Slack Webhook URL.
