# Crypton Sweep Scanned Research Dataset

Crypton Sweep Scanned is a curated research dataset of cryptographic exposure
and post-quantum migration evidence collected from widely used open-source
network and security projects. It provides a reproducible basis for comparing
classical cryptography usage, PQC readiness, and proxy migration candidates
across representative infrastructure software.

## Upstream projects and reports

| Project | Upstream repository | Report directory |
|---|---|---|
| Envoy | [envoyproxy/envoy](https://github.com/envoyproxy/envoy) | `reports/envoy/` |
| HAProxy | [haproxy/haproxy](https://github.com/haproxy/haproxy) | `reports/hproxy/` |
| Mosquitto | [eclipse-mosquitto/mosquitto](https://github.com/eclipse-mosquitto/mosquitto) | `reports/mosquitto/` |
| Nginx | [nginx/nginx](https://github.com/nginx/nginx) | `reports/ngnix/` |
| Tailscale | [tailscale/tailscale](https://github.com/tailscale/tailscale) | `reports/tailscale/` |

The four source checkouts are temporary inputs used to produce the archived
reports. Mosquitto is represented by its report and upstream GitHub reference
because its source checkout is not retained here.

## Final archive layout

After the temporary source checkouts are removed, the top level of this
repository will contain only:

```text
README.md
reports/
```

The `reports/` directory retains one subdirectory per scanned project. Each
subdirectory contains JSON evidence, an HTML dashboard, and a README explaining
how to read that project’s result.

## Reading the reports

Each report directory contains:

- `*.json`: machine-readable evidence, assets, findings, and summary counts.
- `*.html`: self-contained offline dashboard for human review.
- `README.md`: project-specific provenance and reading guidance.

Read the JSON summary first, inspect the HTML evidence view second, and use the
report README for project-specific context. Static findings are migration
evidence; they do not prove that a code path is built, enabled, or negotiated
at runtime.

## Report snapshot

All reports were generated with Crypton Sweep `0.1.1`.

| Project | Assets | Classical-only | PQC-ready | Proxy candidates | High-risk |
|---|---:|---:|---:|---:|---:|
| Envoy | 959 | 504 | 4 | 504 | 0 |
| HAProxy | 158 | 68 | 1 | 68 | 0 |
| Mosquitto | 76 | 6 | 0 | 6 | 0 |
| Nginx | 25 | 3 | 0 | 3 | 0 |
| Tailscale | 108 | 106 | 0 | 106 | 0 |

`hproxy` and `ngnix` are retained as report-directory names for compatibility
with the existing artifacts; they mean HAProxy and Nginx respectively.

## Crypton Sweep tool reference

The scans were produced with the open-source Crypton Sweep tool maintained at
[Gulshan-gaur/crypton-sweep](https://github.com/Gulshan-gaur/crypton-sweep).
Read the authoritative [Crypton Sweep README](https://github.com/Gulshan-gaur/crypton-sweep/blob/main/README.md)
for installation, scan, report, and evidence-boundary details.

The reports in this archive were generated with Crypton Sweep `0.1.1` using
authorized local source checkouts.

Typical reproduction commands are:

```bash
crypton-sweep scan /path/to/authorized/checkout \
  --out reports/project/project.json
crypton-sweep report reports/project/project.json \
  --out reports/project/project.html
```

## Research limitations

- Source matches do not prove runtime behavior or vulnerability.
- Build flags, deployment configuration, and negotiated TLS require separate
  review.
- Runtime network discovery is separate from these source reports.
- Only authorized source checkouts should be scanned and shared.
- Cite the upstream project, pinned revision, report JSON, tool version, and
  generation timestamp in paper tables.
