<div align="center">

# 🤖 hAI.9Router

### AI Routing Proxy — Portainer Stack Template

[![Version](https://img.shields.io/badge/version-1.0.0-blue?style=for-the-badge&logo=docker)](https://github.com/jbkunama1/hAI.9Router)
[![Status](https://img.shields.io/badge/status-active-brightgreen?style=for-the-badge&logo=checkmarx)](https://github.com/jbkunama1/hAI.9Router)
[![License](https://img.shields.io/badge/license-MIT-yellow?style=for-the-badge&logo=opensourceinitiative)](LICENSE)
[![Portainer](https://img.shields.io/badge/Portainer-Stack-13BEF9?style=for-the-badge&logo=portainer)](https://portainer.io)
[![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?style=for-the-badge&logo=docker)](docker-compose.yml)
[![LAN](https://img.shields.io/badge/LAN-Dashboard-FF6B35?style=for-the-badge&logo=googlechrome)](#lan-dashboard)

---

```
 ██╗  ██╗ █████╗ ██╗    ██████╗ ██████╗  ██████╗ ██╗   ██╗████████╗███████╗██████╗
 ██║  ██║██╔══██╗██║    ██╔══██╗██╔══██╗██╔═══██╗██║   ██║╚══██╔══╝██╔════╝██╔══██╗
 ███████║███████║██║    ██████╔╝██████╔╝██║   ██║██║   ██║   ██║   █████╗  ██████╔╝
 ██╔══██║██╔══██║██║    ██╔══██╗██╔══██╗██║   ██║██║   ██║   ██║   ██╔══╝  ██╔══██╗
 ██║  ██║██║  ██║██║    ██║  ██║██║  ██║╚██████╔╝╚██████╔╝   ██║   ███████╗██║  ██║
 ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝    ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝  ╚═════╝    ╚═╝   ╚══════╝╚═╝  ╚═╝
```

**Intelligenter AI-Routing-Proxy mit Live-LAN-Dashboard — bereit fuer Portainer**

</div>

---

## 📋 Inhaltsverzeichnis

- [✨ Features](#-features)
- [🏗️ Architektur](#-architektur)
- [🚀 Schnellstart](#-schnellstart)
- [🐳 Portainer Stack Import](#-portainer-stack-import)
- [🌐 LAN Dashboard](#-lan-dashboard)
- [⚙️ Konfiguration](#-konfiguration)
- [📁 Dateistruktur](#-dateistruktur)
- [🔧 Troubleshooting](#-troubleshooting)
- [📜 Lizenz](#-lizenz)

---

## ✨ Features

| Feature | Beschreibung |
|--------|-------------|
| 🤖 **AI Routing** | Intelligentes Routing zu verschiedenen AI-Backends (OpenAI, Ollama, LocalAI) |
| 🌐 **LAN Dashboard** | Visuelles Status-Dashboard fuer alle LAN-Dienste auf Port `20128` |
| 🐳 **Portainer Ready** | Direkter Stack-Import per YAML — kein CLI benoetigt |
| 🔒 **Netzwerk-Isolation** | Dediziertes Docker-Bridge-Netzwerk `9router_net` |
| 💾 **Persistente Volumes** | Config + Logs bleiben bei Container-Restart erhalten |
| 📊 **Health Checks** | Automatische Gesundheitsueberpruefung alle 30 Sekunden |
| 🔄 **Auto-Restart** | `unless-stopped` Policy fuer maximale Verfuegbarkeit |
| 🛡️ **Read-Only FS** | Sicherheitshaertung durch Read-Only-Dateisystem |

---

## 🏗️ Architektur

```
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

## 🚀 Schnellstart

### Voraussetzungen

```bash
# Mindestanforderungen
✅ Docker >= 24.0
✅ Docker Compose >= 2.20  
✅ Portainer >= 2.19 (optional, aber empfohlen)
✅ 256 MB RAM
✅ Port 20128 frei
```

### Option A: Docker Compose (CLI)

```bash
# 1. Repository klonen
git clone https://github.com/jbkunama1/hAI.9Router.git
cd hAI.9Router

# 2. Umgebungsvariablen konfigurieren
cp .env.example .env
nano .env  # API-Keys eintragen

# 3. Stack starten
docker compose up -d

# 4. Dashboard aufrufen
open http://localhost:20128
```

### Option B: Portainer Stack Import

> Siehe Abschnitt [Portainer Stack Import](#-portainer-stack-import) fuer detaillierte Anleitung

---

## 🐳 Portainer Stack Import

<div align="center">

### Schritt-fuer-Schritt Anleitung

</div>

```
Schritt 1 ──► Portainer oeffnen (http://portainer:9000)
    │
    ▼
Schritt 2 ──► Stacks ► + Add Stack
    │
    ▼
Schritt 3 ──► Build method: Repository
              Repository URL: https://github.com/jbkunama1/hAI.9Router
              Compose path:   docker-compose.yml
    │
    ▼
Schritt 4 ──► Environment Variables hinzufuegen:
              OPENAI_API_KEY = sk-...
              ROUTER_PORT    = 20128
    │
    ▼
Schritt 5 ──► Deploy the stack ✅
```

> 💡 **Tipp:** Alternativ `docker-compose.yml` direkt als "Web editor"-Inhalt einfuegen.

---

## 🌐 LAN Dashboard

Das integrierte Status-Dashboard ist erreichbar unter:

```
http://<deine-LAN-IP>:20128
```

**Dashboard-Features:**
- 🟢 Live-Status aller konfigurierten AI-Backends
- 📈 Request-Statistiken in Echtzeit  
- 🔄 Auto-Refresh alle 10 Sekunden
- 📱 Mobile-freundliches Design
- 🌙 Dark Mode by default

---

## ⚙️ Konfiguration

### Umgebungsvariablen

| Variable | Standard | Beschreibung |
|----------|---------|-------------|
| `ROUTER_PORT` | `20128` | Externer Port des Dashboards |
| `OPENAI_API_KEY` | — | OpenAI API-Schluessel |
| `OLLAMA_HOST` | `http://ollama:11434` | Ollama Backend-URL |
| `LOCAL_AI_HOST` | `http://localai:8080` | LocalAI Backend-URL |
| `LOG_LEVEL` | `info` | Logging-Level (`debug`/`info`/`warn`/`error`) |
| `HEALTH_CHECK_INTERVAL` | `30` | Health-Check-Intervall in Sekunden |

### Netzwerke

```yaml
# Intern: Container-Kommunikation
9router_net:    bridge, intern

# Optional: Verbindung zu bestehendem Traefik/NGINX
proxy_net:      external (falls vorhanden)
```

### Volumes

```
9router_config:/app/config    # Routing-Konfiguration
9router_logs:/app/logs        # Anwendungslogs
```

---

## 📁 Dateistruktur

```
hAI.9Router/
├── 📄 README.md                  # Diese Datei
├── 📄 LICENSE                    # MIT Lizenz
├── 🐳 docker-compose.yml         # Portainer Stack Definition
├── 🌐 index.html                 # LAN Status Dashboard
├── ⚙️  .env.example              # Umgebungsvariablen-Vorlage
└── 📋 portainer-template.json   # Portainer App Template
```

---

## 🔧 Troubleshooting

### Port 20128 bereits belegt

```bash
# Belegung pruefen
sudo lsof -i :20128
# Alternativen Port in .env setzen
ROUTER_PORT=20129
```

### Container startet nicht

```bash
# Logs pruefen
docker compose logs -f 9router
# Container-Status
docker compose ps
```

### Health Check schlaegt fehl

```bash
# Direkt testen
curl http://localhost:20128/health
# Erwartete Antwort: {"status":"ok"}
```

---

## 📜 Lizenz

MIT License — Copyright (c) 2026 [jbkunama1](https://github.com/jbkunama1)

Siehe [LICENSE](LICENSE) fuer den vollstaendigen Text.

---

<div align="center">

**Gebaut mit ❤️ fuer das Heimnetzwerk**

[![GitHub](https://img.shields.io/badge/GitHub-jbkunama1-181717?style=flat-square&logo=github)](https://github.com/jbkunama1)
[![Repo](https://img.shields.io/badge/Repo-hAI.9Router-blue?style=flat-square&logo=github)](https://github.com/jbkunama1/hAI.9Router)

*🤖 9Router • AI trifft Heimnetz • Portainer-ready*

</div>
