---
title: Security
---

## Encryption

- Backups can be encrypted client-side before upload. Keys remain with the owner.
- Transport encryption via TLS for all tunnels.

## Token scopes

- Use token-scoped credentials with least privilege (repository-level write or read-only for restores).

## Zero Trust & network

- Cloudflare Tunnel provides authenticated, TLS-protected connectivity without exposing PBS to the public internet.
- Firewall defaults should only allow outbound connections from PBS to the tunnel.

## Data isolation

- Backups are stored per-repository or per-namespace, enabling separation between customers or teams.
