# SOP-002: Syslog Collection Pipeline (Loki)

## 1. Pipeline Architecture
External Device (UDP/514) -> `rsyslog` (Relay) -> `promtail` (RFC5424/TCP/1514) -> `loki` (Storage).

## 2. Configuration Details
*   **Loki:** Configured for 7-day retention to prevent excessive UFS flash storage degradation.
*   **rsyslog:** Acts as a lightweight relay listening on standard port UDP/514, forwarding cleanly formatted logs to Promtail via TCP.
*   **Promtail:** Scrapes local logs and receives forwarded syslog data, pushing it to Loki on `http://127.0.0.1:3100`.
