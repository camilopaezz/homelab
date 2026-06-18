# Homelab

## Current Services

### Media Management & Automation
- **jellyfin** - Media server
- **sonarr** - TV show collection manager
- **radarr** - Movie collection manager
- **bazarr** - Subtitle manager
- **prowlarr** - Torrent indexer manager
- **flaresolverr** - Proxy server to bypass cloudflare protection

### Torrent Client
- **qbittorrent** - Torrent client with web interface

### Media Requests
- **seerr** - Media request and discovery manager

### Proxies
- **hackstore-proxy** - Reverse proxy for hackstore.fo (built from submodule)

### Password Management
- **vaultwarden** - Unofficial Bitwarden server implementation

### Automation & Monitoring
- **watchtower** - Automatic Docker container updates

## Essential Commands

### Setup

```bash
git submodule update --init --recursive   # clone hackstore-prowlarr submodule
cp .env.example .env                       # then edit .env with your values
```

### Docker Compose

```bash
docker compose up -d              # start all services
docker compose down               # stop all services
docker compose logs -f <service>  # tail logs for a service
docker compose ps                 # list running services
docker compose restart <service>  # restart a single service
```

### hackstore-proxy (custom build)

```bash
docker compose build hackstore-proxy          # rebuild the proxy image
docker compose up -d --build hackstore-proxy  # rebuild and restart
docker compose up -d --build                  # rebuild everything and start
```

### hackstore-proxy (dev)

```bash
cd hackstore-prowlarr
uv run pytest                  # run tests
uv run ruff check .            # lint
uv run ruff format .           # format
python decrypt_url.py "<url>"  # decrypt an acortalink.net URL
```
