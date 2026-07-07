# Homelab Architecture

## Overview

```text
                    Internet
                        │
                        │
                  WireGuard VPN
                        │
                        ▼
              Ubuntu Docker Host
               192.168.1.243
                        │
      ┌─────────────────┼─────────────────┐
      │                 │                 │
      ▼                 ▼                 ▼
  Jellyfin        qBittorrent       Prowlarr
                        │
                        ▼
                  /mnt/media (NFS)
                        │
                        ▼
                 TrueNAS SCALE
                 192.168.1.230
                        │
        media/
        ├── downloads/
        ├── movies/
        ├── tv/
        ├── music/
        └── photos/
```

## Components

### Ubuntu Docker Host

- Docker Engine
- Docker Compose
- Jellyfin
- qBittorrent
- Prowlarr

### Storage

- TrueNAS SCALE
- NFS share
- Mounted on `/mnt/media`

## Network

| Host | IP |
|------|----|
| Ubuntu Docker Host | 192.168.1.243 |
| TrueNAS SCALE | 192.168.1.230 |
