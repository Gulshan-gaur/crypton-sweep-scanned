# Crypton Sweep Reports

This folder contains the scan results for five open-source projects.

| Folder | Project | JSON | HTML |
|---|---|---|---|
| `envoy` | Envoy | `envoy.json` | `envoy.html` |
| `hproxy` | HAProxy | `hproxy.json` | `hproxy.html` |
| `mosquitto` | Eclipse Mosquitto | `mosquitto-crypto.json` | `mosquitto-crypto.html` |
| `ngnix` | Nginx | `nginx.json` | `nginx.html` |
| `tailscale` | Tailscale | `tailscale.json` | `tailscale.html` |

For each project, read the JSON as the authoritative structured evidence and
the HTML as the human-readable dashboard. The folder names `hproxy` and
`ngnix` are preserved from the existing collection.

All reports were generated with Crypton Sweep `0.1.1`. They are static source
reports and should be paired with build/configuration review before making
runtime or security claims.
