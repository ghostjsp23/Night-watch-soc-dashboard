# NIGHTWATCH — Simulated SOC Dashboard

A simulated Security Operations Centre (SOC) dashboard built to demonstrate 
security monitoring concepts, correlation-based threat detection, and 
incident response workflows.

🔗 **Live demo:** https://ghostjsp23.github.io/Night-watch-soc-dashboard/

⚠️ **This is a simulated environment.** All data (IP addresses, incidents, 
sensors) is randomly generated on page load — no real network traffic, 
live threat feeds, or actual IP blocking is involved.

## What it does

- **Live overview** — summary stats for login attempts, failed authentications, 
  critical alerts, and auto-detected threats, plus a "network pulse" 
  visualization of recent event density
- **Automated detection** — two correlation rules scan the simulated log 
  pool and automatically flag incidents:
  - **Brute Force**: 10+ failed logins from one IP within 60 seconds → HIGH
  - **Directory/Port Scanning**: 50+ requests from one IP within 5 minutes → MEDIUM
  
  Auto-detected incidents are visibly tagged `AUTO` and distinguished from 
  manually logged events
- **Incident detail view** — click any incident to see the attacker IP, 
  target, first/last seen timestamps, attempt count, raw evidence logs, 
  MITRE ATT&CK technique ID, and a recommended response
- **Analyst response workflow** — Investigate / Block IP / Dismiss / Escalate 
  actions that update incident status and log to a session activity feed
- **Attack distribution & timeline charts** — visual breakdown of attack 
  types and event volume over 24 hours
- **Sensor fleet monitoring** — simulated network sensors (gateway, auth 
  cluster, honeypot, WAF, etc.) with uptime and heartbeat status

## Why I built this

I wanted to go beyond theory and build something that reflects how a SOC 
analyst actually works: correlating raw log events into incidents, 
triaging by severity, mapping attacks to MITRE ATT&CK, and following 
through with a response — not just displaying static numbers.

## Tech stack

- HTML / CSS / JavaScript — no frameworks, single self-contained file
- Native `<canvas>` for all charts (timeline, distribution donut, pulse strip)
- Hosted via GitHub Pages

## How detection works (in short)

On load, the app generates ~450 simulated log events across a 48-hour 
window, including a few deliberately clustered bursts. Separate detection 
logic then scans that data for patterns — repeated failed logins from one 
IP in a short window, or high-volume endpoint scanning — and converts 
matches into incidents automatically, the same basic principle real SIEM 
correlation rules use.

## Roadmap / possible next steps

- Live/continuous simulated attack generation
- Additional detection rules (e.g. credential stuffing, malware beaconing)
- Persisting analyst actions beyond the current session

## Disclaimer

Built for educational and portfolio purposes only. Not intended for use 
as an actual security monitoring tool.
