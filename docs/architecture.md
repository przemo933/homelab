# Homelab Architecture

## Overview

```text
                    Internet
                        │
                        │
                  WireGuard VPN
                        │
                        ▼
                    Internet
                        │
                        │
                  WireGuard VPN
                        │
                        ▼
              Ubuntu Docker Host
               192.168.1.243
                        │
        ┌───────────────┼──────────────────────────────┐
        │               │                              │
        ▼               ▼                              ▼
    Jellyfin      qBittorrent                     Prowlarr
        ▲               ▲                              │
        │               │                              │
        │               │                         Sync Indexers
        │               │                              ▼
        │            Downloads                     Radarr
        │               ▲                              │
        │               │                              │
        │               └──────────────┐               │
        │                              │               │
        │                           Bazarr ◄──────────┘
        │                              │
        └─────────────── Reads Movies ─┘
                        │
                        ▼
                  /mnt/media (NFS)
                        │
        ┌───────────────┴───────────────┐
        │                               │
        ▼                               ▼
 downloads/                        movies/
                        │
                        ▼
                 TrueNAS SCALE
                 192.168.1.230


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
- Radarr
- Bazarr

### Storage

- TrueNAS SCALE
- NFS share
- Mounted on `/mnt/media`

## Network

| Host | IP |
|------|----|
| Ubuntu Docker Host | 192.168.1.243 |
| TrueNAS SCALE | 192.168.1.230 |
