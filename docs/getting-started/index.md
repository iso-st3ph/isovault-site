---
title: Getting Started
---

## Requirements

- A running Proxmox Backup Server (PBS).
- A token with appropriate scope for the repository you will push backups to.

## Create a token in PBS

1. In PBS web UI go to Users -> Tokens.
2. Create a limited-scope token (repository write) and copy the token string.

## Client install

Linux (Debian/Ubuntu)

```bash
# Add APT repo (example)
curl -sSL https://example.com/repos/isovault-apt.key | sudo apt-key add -
echo "deb [arch=amd64] https://packages.example.com/ stable main" | sudo tee /etc/apt/sources.list.d/isovault.list
sudo apt update && sudo apt install -y proxmox-backup-client
```

Docker

```bash
docker run --rm -v $(pwd):/data proxmox/pbs-client backup docs.pxar=/data
```

## Environment variables

- PBS_REPOSITORY — repository name (e.g. myrepo)
- PBS_USERNAME — token name
- PBS_PASSWORD — token secret

## Example backup

```bash
PBS_REPOSITORY=docs PBS_USERNAME=backup-token PBS_PASSWORD=abcd1234 proxmox-backup-client backup docs.pxar=./myfolder
```

## Restore

```bash
proxmox-backup-client restore --repository docs --target ./restore-folder --snapshot latest
```

## Verify

- Check the PBS UI for recent snapshots and successful jobs.
- Use `proxmox-backup-client status` or examine job logs.
