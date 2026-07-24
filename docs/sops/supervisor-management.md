# Standard Operating Procedure: Managing Background Services

This operational guide details how to manage background daemons using Supervisor.

## 1. Checking Status
To view the status of all managed services:
```bash
supervisorctl status
```

## 2. Restarting Individual Services
To restart a specific service, use:
```bash
supervisorctl restart <service_name>
```

## 3. Reading Live Logs
To follow the live standard output logs for a service:
```bash
tail -f /var/log/supervisor/<service_name>*.log
```

## 4. Updating Service Definitions
If you edit the master configuration at `/etc/supervisor/conf.d/observability.conf`, you must reload Supervisor:
```bash
supervisorctl reread && supervisorctl update
```
