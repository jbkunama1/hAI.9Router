<div align="center">

<img src="logo_9router.png" alt="hAI.9Router Logo" width="300">

# 🤖 hAI.9Router

### AI Routing Proxy — Portainer Stack Template

[![Buy me a coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-ffdd00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://www.buymeacoffee.com/highfish)

[![Version](https://img.shields.io/badge/version-1.0.0-blue?style=for-the-badge&logo=docker)](https://github.com/jbkunama1/hAI.9Router)
[![Status](https://img.shields.io/badge/status-active-brightgreen?style=for-the-badge&logo=checkmarx)](https://github.com/jbkunama1/hAI.9Router)
[![License](https://img.shields.io/badge/license-MIT-yellow?style=for-the-badge&logo=opensourceinitiative)](LICENSE)
[![Portainer](https://img.shields.io/badge/Portainer-Stack-13BEF9?style=for-the-badge&logo=portainer)](https://portainer.io)
[![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?style=for-the-badge&logo=docker)](docker-compose.yml)
[![LAN](https://img.shields.io/badge/LAN-Dashboard-FF6B35?style=for-the-badge&logo=googlechrome)](#-lan-dashboard)

---
██╗ ██╗ █████╗ ██╗ ██████╗ ██████╗ ██████╗ ██╗ ██╗████████╗███████╗██████╗
██║ ██║██╔══██╗██║ ██╔══██╗██╔══██╗██╔═══██╗██║ ██║╚══██╔══╝██╔════╝██╔══██╗
███████║███████║██║ ██████╔╝██████╔╝██║ ██║██║ ██║ ██║ █████╗ ██████╔╝
██╔══██║██╔══██║██║ ██╔══██╗██╔══██╗██║ ██║██║ ██║ ██║ ██╔══╝ ██╔══██╗
██║ ██║██║ ██║██║ ██║ ██║██║ ██║╚██████╔╝╚██████╔╝ ██║ ███████╗██║ ██║
╚═╝ ╚═╝╚═╝ ╚═╝╚═╝ ╚═╝ ╚═╝╚═╝ ╚═╝ ╚═════╝ ╚═════╝ ╚═╝ ╚══════╝╚═╝ ╚═╝

text

**Intelligent AI Routing Proxy with Live LAN Dashboard — Portainer Ready**

[🇩🇪 German Version](README.md)

</div>

---

## 📋 Table of Contents

- [✨ Features](#-features)
- [🏗️ Architecture](#-architecture)
- [🚀 Quick Start](#-quick-start)
- [🐳 Portainer Stack Import](#-portainer-stack-import)
- [🌐 LAN Dashboard](#-lan-dashboard)
- [⚙️ Configuration](#-configuration)
- [📁 File Structure](#-file-structure)
- [🔧 Troubleshooting](#-troubleshooting)
- [📜 License](#-license)

---

## ✨ Features

| Feature | Description |
|--------|-------------|
| 🤖 **AI Routing** | Intelligent routing to multiple AI backends (OpenAI, Ollama, LocalAI) |
| 🌐 **LAN Dashboard** | Visual status dashboard for all LAN services on port `20128` |
| 🐳 **Portainer Ready** | Direct stack import via YAML — no CLI required |
| 🔒 **Network Isolation** | Dedicated Docker bridge network `9router_net` |
| 💾 **Persistent Volumes** | Config and logs survive container restarts |
| 📊 **Health Checks** | Automatic health monitoring every 30 seconds |
| 🔄 **Auto-Restart** | `unless-stopped` policy for maximum availability |
| 🛡️ **Read-Only FS** | Security hardening with read-only filesystem |

---

## 🏗️ Architecture

```text
╔══════════════════════════════════════════════════════════╗
║                    LAN / Home Network                    ║
║                                                          ║
║  Browser ──────────────────────────────────────────────► ║
║              ↓ Port 20128                                ║
║  ┌───────────────────────────────────────────────────┐   ║
║  │               🤖 hAI.9Router Container            │   ║
║  │                                                   │   ║
║  │  ┌─────────────┐    ┌────────────────────────┐   │   ║
║  │  │ 🌐 Dashboard │    │   AI Routing Engine    │   │   ║
║  │  │  index.html │    │  /v1/chat/completions  │   │   ║
║  │  └─────────────┘    └──────────┬─────────────┘   │   ║
║  │                                │                  │   ║
║  │              ┌─────────────────┼──────────────┐   │   ║
║  │              ▼                 ▼              ▼   │   ║
║  │        🟢 OpenAI        🟡 Ollama      🔵 LocalAI  │   ║
║  └───────────────────────────────────────────────────┘   ║
║              9router_net (bridge)                        ║
╚══════════════════════════════════════════════════════════╝
```

---

## 🚀 Quick Start

### Prerequisites

```bash
# Minimum requirements
✅ Docker >= 24.0
✅ Docker Compose >= 2.20
✅ Portainer >= 2.19 (optional but recommended)
✅ 256 MB RAM
✅ Port 20128 available
```

### Option A: Docker Compose (CLI)

```bash
# 1. Clone repository
git clone https://github.com/jbkunama1/hAI.9Router.git
cd hAI.9Router

# 2. Configure environment variables
cp .env.example .env
nano .env  # Enter API keys

# 3. Start stack
docker compose up -d

# 4. Open dashboard
open http://localhost:20128
```

### Option B: Portainer Stack Import

> See [Portainer Stack Import](#-portainer-stack-import) section for detailed instructions

---

## 🐳 Portainer Stack Import

<div align="center">

### Step-by-Step Guide

</div>

```text
Step 1 ──► Open Portainer (http://portainer:9000)
    │
    ▼
Step 2 ──► Stacks ► + Add Stack
    │
    ▼
Step 3 ──► Build method: Repository
           Repository URL: https://github.com/jbkunama1/hAI.9Router
           Compose path:   docker-compose.yml
    │
    ▼
Step 4 ──► Add environment variables:
           OPENAI_API_KEY = sk-...
           ROUTER_PORT    = 20128
    │
    ▼
Step 5 ──► Deploy the stack ✅
```

> 💡 **Tip:** Alternatively paste `docker-compose.yml` directly into the “Web editor”.

---

## 🌐 LAN Dashboard

The integrated status dashboard is available at:

```text
http://<your-LAN-IP>:20128
```

**Dashboard Features:**

- 🟢 Live status of all configured AI backends  
- 📈 Real-time request statistics  
- 🔄 Auto-refresh every 10 seconds  
- 📱 Mobile-friendly design  
- 🌙 Dark mode by default  

---

## ⚙️ Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `ROUTER_PORT` | `20128` | External dashboard port |
| `OPENAI_API_KEY` | — | OpenAI API key |
| `OLLAMA_HOST` | `http://ollama:11434` | Ollama backend URL |
| `LOCAL_AI_HOST` | `http://localai:8080` | LocalAI backend URL |
| `LOG_LEVEL` | `info` | Logging level (`debug`/`info`/`warn`/`error`) |
| `HEALTH_CHECK_INTERVAL` | `30` | Health check interval in seconds |

### Networks

```yaml
# Internal: container communication
9router_net:    bridge, internal

# Optional: connection to existing Traefik/NGINX
proxy_net:      external (if available)
```

### Volumes

```text
9router_config:/app/config    # Routing configuration
9router_logs:/app/logs        # Application logs
```

---

## 📁 File Structure

```text
hAI.9Router/
├── 📄 README.md                  # German documentation
├── 📄 README_EN.md               # English documentation
├── 📄 LICENSE                    # MIT License
├── 🐳 docker-compose.yml         # Portainer stack definition
├── 🌐 index.html                 # LAN status dashboard (app)
├── ⚙️  .env.example              # Environment variables template
├── 📋 portainer-template.json   # Portainer app template
└── 🖼️  logo_9router.png          # Project logo
```

---

## 🔧 Troubleshooting

### Port 20128 already in use

```bash
# Check port usage
sudo lsof -i :20128
# Set alternative port in .env
ROUTER_PORT=20129
```

### Container will not start

```bash
# Check logs
docker compose logs -f 9router
# Check container status
docker compose ps
```

### Health check fails

```bash
# Test directly
curl http://localhost:20128/health
# Expected response: {"status":"ok"}
```

---

## 📜 License

MIT License — see [LICENSE](LICENSE) for full text.

---

<div align="center">

**Built with ❤️ for home networks**

[![GitHub](https://img.shields.io/badge/GitHub-jbkunama1-181717?style=flat-square&logo=github)](https://github.com/jbkunama1)
[![Repo](https://img.shields.io/badge/Repo-hAI.9Router-blue?style=flat-square&logo=github)](https://github.com/jbkunama1/hAI.9Router)

*🤖 9Router • AI meets home network • Portainer-ready*

</div>

