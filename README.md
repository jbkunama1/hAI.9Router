<div align="center">

# 🤖 hAI.9Router

### AI Management Dashboard & Router — Portainer Stack

[![Version](https://img.shields.io/badge/version-1.0.0-blue?style=for-the-badge&logo=docker)](https://github.com/jbkunama1/hAI.9Router)
[![Status](https://img.shields.io/badge/status-active-brightgreen?style=for-the-badge&logo=checkmarx)](https://github.com/jbkunama1/hAI.9Router)
[![License](https://img.shields.io/badge/license-MIT-yellow?style=for-the-badge&logo=opensourceinitiative)](LICENSE)
[![Portainer](https://img.shields.io/badge/Portainer-Ready-13BEF9?style=for-the-badge&logo=portainer)](https://portainer.io)
[![9Router](https://img.shields.io/badge/9Router-Official-764ba2?style=for-the-badge&logo=docker)](https://hub.docker.com/r/decolua/9router)

---

```
 ██╗  ██╗ █████╗ ██╗    ██████╗ ██████╗  ██████╗ ██╗   ██╗████████╗███████╗██████╗
 ██║  ██║██╔══██╗██║    ██╔══██╗██╔══██╗██╔═══██╗██║   ██║╚══██╔══╝██╔════╝██╔══██╗
 ███████║███████║██║    ██████╔╝██████╔╝██║   ██║██║   ██║   ██║   █████╗  ██████╔╝
 ██╔══██║██╔══██║██║    ██╔══██╗██╔══██╗██║   ██║██║   ██║   ██║   ██╔══╝  ██╔══██╗
 ██║  ██║██║  ██║██║    ██║  ██║██║  ██║╚██████╔╝╚██████╔╝   ██║   ███████╗██║  ██║
 ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝    ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝  ╚═════╝    ╚═╝   ╚══════╝╚═╝  ╚═╝
```

**Zentrales AI-Management mit 60+ Providern — Web-UI & API**

[Docker Hub](https://hub.docker.com/r/decolua/9router) • [Official Repo](https://github.com/decolua/9router) • [Documentation](https://9router.com)

</div>

---

## 📋 Inhaltsverzeichnis

- [✨ Was ist 9Router?](#-was-ist-9router)
- [🎯 Features](#-features)
- [🚀 Schnellstart](#-schnellstart)
- [🐳 Portainer Stack Import](#-portainer-stack-import)
- [🌐 Web-Dashboard](#-web-dashboard)
- [⚙️ Konfiguration](#%EF%B8%8F-konfiguration)
- [📁 Dateistruktur](#-dateistruktur)
- [🔧 Troubleshooting](#-troubleshooting)
- [📜 Lizenz](#-lizenz)

---

## ✨ Was ist 9Router?

**9Router** ist ein **All-in-One AI Management Dashboard**, das:

🎯 Zugriff auf **60+ AI-Provider** bietet (OpenAI, Claude, Gemini, etc.)  
📊 **Smart Fallback** zwischen kostenlosen und bezahlten Modellen  
🔑 **API-Key-Management** mit zentraler Verwaltung  
📊 **Usage Tracking** und Kostenübersicht  
🌐 **Web-UI** für einfache Konfiguration  
🔌 **OpenAI-kompatible API** für bestehende Tools  

> **Wichtig:** 9Router ist **KEIN** einfacher Reverse Proxy, sondern eine vollwertige Plattform zur Verwaltung aller deiner AI-Dienste!

---

## 🎯 Features

| Feature | Beschreibung |
|--------|-------------|
| 🐳 **Docker-ready** | Offizielles Image: `decolua/9router:latest` |
| 🌐 **Web Dashboard** | Vollständige UI auf Port `20128` |
| 🔑 **Multi-Provider** | 60+ AI-Provider in einem Dashboard |
| 📊 **Smart Routing** | Auto-Fallback zu kostenlosen Alternativen |
| 🔒 **Authentifizierung** | JWT-basiert mit Passwortschutz |
| 💾 **Persistenz** | Alle Einstellungen in `./data` gespeichert |
| 🚀 **Portainer-ready** | Direkter Stack-Import aus GitHub |
| ❤️ **Health Checks** | Automatische Überwachung alle 30s |

---

## 🚀 Schnellstart

### Voraussetzungen

```bash
✅ Docker >= 24.0
✅ Docker Compose >= 2.20  
✅ Portainer >= 2.19 (optional)
✅ Port 20128 frei
```

### Option A: Docker Compose (CLI)

```bash
# 1. Repository klonen
git clone https://github.com/jbkunama1/hAI.9Router.git
cd hAI.9Router

# 2. Stack starten
docker compose up -d

# 3. Dashboard öffnen
open http://localhost:20128

# 4. Login mit Standardpasswort
# Passwort: 123456
```

### Option B: Docker Run (Schnelltest)

```bash
mkdir -p ./data

docker run -d \
  --name 9router \
  -p 20128:20128 \
  -v "$(pwd)/data:/app/data" \
  -e DATA_DIR=/app/data \
  -e INITIAL_PASSWORD=123456 \
  decolua/9router:latest
```

---

## 🐳 Portainer Stack Import

<div align="center">

### Schritt-für-Schritt Anleitung

</div>

```
Schritt 1 ──► Portainer öffnen (http://portainer:9000)
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
Schritt 4 ──► Environment variables (optional):
              INITIAL_PASSWORD = dein_sicheres_passwort
              JWT_SECRET       = lange_zufällige_zeichenkette
              ROUTER_PORT      = 20128
    │
    ▼
Schritt 5 ──► Deploy the stack ✅
```

---

## 🌐 Web-Dashboard

Das integrierte Web-UI ist erreichbar unter:

```
http://<deine-LAN-IP>:20128
```

**Dashboard-Features:**

- 📋 **Provider-Verwaltung**: Füge API-Keys für 60+ Services hinzu
- 📈 **Usage Analytics**: Echtzeit-Statistiken deiner API-Nutzung
- ⚙️ **Routing-Regeln**: Konfiguriere Fallback-Ketten
- 📊 **Cost Tracking**: Überwache deine AI-Kosten
- 🔑 **API-Key-Generator**: Erstelle Zugangsschlüssel für deine Apps
- 👥 **Multi-User**: Unterstützt mehrere Accounts

**Standard-Login:**
- **Passwort:** `123456` (aus `INITIAL_PASSWORD`)

> 🚨 **Sicherheit:** Ändere das Passwort sofort nach dem ersten Login!

---

## ⚙️ Konfiguration

### Umgebungsvariablen

| Variable | Standard | Beschreibung |
|----------|---------|-------------|
| `DATA_DIR` | `/app/data` | Datenbankverzeichnis |
| `PORT` | `20128` | Interner Port |
| `ROUTER_PORT` | `20128` | Externer Port-Mapping |
| `INITIAL_PASSWORD` | `123456` | Erstes Login-Passwort |
| `JWT_SECRET` | auto | JWT-Signaturschlüssel |
| `TZ` | `Europe/Berlin` | Zeitzone |

### Volume-Mapping

```yaml
volumes:
  - ./data:/app/data  # SQLite-DB + Konfigurationen
```

**Wichtig:** Das `./data`-Verzeichnis wird automatisch erstellt und enthält:
- `9router.db` - SQLite-Datenbank
- Provider-Konfigurationen
- API-Keys (verschlüsselt)
- Usage-Logs

---

## 📁 Dateistruktur

```
hAI.9Router/
├── 📄 README.md                  # Diese Datei
├── 📄 LICENSE                    # MIT Lizenz
├── 🐳 docker-compose.yml         # Portainer Stack (61 Zeilen)
├── 🌐 index.html                 # Info-Seite (optional)
├── ⚙️  .env.example              # Umgebungsvariablen-Vorlage
└── 📋 portainer-template.json   # Portainer App Template

Generiert beim Start:
data/
└── 9router.db                    # SQLite-Datenbank
```

---

## 🔧 Troubleshooting

### Port 20128 bereits belegt

```bash
# Prüfen
sudo lsof -i :20128

# Alternativen Port in docker-compose.yml
ports:
  - "20129:20128"  # Externer Port 20129
```

### Container startet nicht

```bash
# Logs prüfen
docker compose logs -f 9router

# Volume-Berechtigungen prüfen
chmod 755 ./data
```

### Login funktioniert nicht

```bash
# Passwort zurücksetzen
docker compose down
rm -rf ./data/9router.db
docker compose up -d

# Neues Passwort: INITIAL_PASSWORD aus docker-compose.yml
```

### Health Check schlägt fehl

```bash
# Direkt testen
curl http://localhost:20128

# Container-Status
docker compose ps
```

---

## 🔗 Nützliche Links

- **Official 9Router:** https://github.com/decolua/9router
- **Docker Hub:** https://hub.docker.com/r/decolua/9router
- **Website:** https://9router.com
- **Dieses Template:** https://github.com/jbkunama1/hAI.9Router

---

## 📜 Lizenz

MIT License — Copyright (c) 2026 [jbkunama1](https://github.com/jbkunama1)

> **Hinweis:** Dieses Repository ist ein Portainer-Stack-Template für [decolua/9router](https://github.com/decolua/9router).  
> 9Router selbst hat eine eigene Lizenz — siehe [Original-Repo](https://github.com/decolua/9router).

---

<div align="center">

**Gebaut mit ❤️ für das Heimnetzwerk**

[![GitHub](https://img.shields.io/badge/GitHub-jbkunama1-181717?style=flat-square&logo=github)](https://github.com/jbkunama1)
[![Repo](https://img.shields.io/badge/Repo-hAI.9Router-blue?style=flat-square&logo=github)](https://github.com/jbkunama1/hAI.9Router)
[![9Router](https://img.shields.io/badge/Powered%20by-9Router-764ba2?style=flat-square)](https://github.com/decolua/9router)

*🤖 9Router • 60+ AI Provider • Portainer-ready*

</div>
