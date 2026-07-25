# SOP-001: Chroot Initialization & Networking

## 1. Environment Setup
*   **Hardware:** Realme GT2 (Snapdragon 8 Gen 1).
*   **OS:** PixelOS, rooted via Magisk.
*   **Chroot:** Ubuntu 24.04 native environment sharing the Android kernel.

## 2. Process Management
Because `systemd` is incompatible with the shared Android kernel, `supervisor` is used to manage all background daemons.
*   **Install:** `apt-get install supervisor`
*   **Config Location:** `/etc/supervisor/conf.d/`

## 3. Tailscale Failover (Multi-WAN)
The device utilizes a custom Magisk script (`tailscale_failover.sh`) to actively manage routing tables and prevent Android "ghost tables" from interfering with Tailscale's mesh networking when switching between Cellular and Wi-Fi interfaces.
