---
title: "Démon SteamRelay (Rust)"
category: "Architecture & Contribution"
slug: "steam-relay-daemon"
description: "Fonctionnement interne du démon Rust, écoute HTTP locale sur le port 8080, arguments CLI et File IPC."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~7 min"
order: 11
---

# Démon SteamRelay (Rust)

`SteamRelay` est le cœur de l'émulation réseau. Développé en Rust avec Tokio et les bindings C Steamworks, il résout les problèmes de NAT traversal sans nécessiter de serveur VPS dédié coûteux en bande passante.

## Arguments de Lancement CLI

```bash
# Lancement classique en mode démon supervisé par le launcher
propnight-steam-relay.exe --daemon --watch-process Propnight --port 8080
```

| Argument | Description | Défaut |
|---|---|---|
| `--daemon` | Lance le serveur HTTP local de contrôle | `false` |
| `--port` | Port de l'API HTTP locale | `8080` |
| `--local_game_port` | Port UDP du serveur de jeu hôte | `7777` |
| `--local_bind_port` | Port UDP d'écoute du client | `7778` |
| `--watch-process` | Ferme le démon dès que le processus cible quitte | `Option<String>` |

## API HTTP Locale & File IPC

Le démon écoute les requêtes sur `http://127.0.0.1:8080` :
- `GET /health` : État de santé du démon.
- `GET /api/status` : Retourne l'état actuel (`Idle`, `Hosting`, `Joining`), le pseudo Steam et le SteamID local.
- `GET /api/logs` : Buffer circulaire des derniers logs réseau.
- **File IPC** : Écoute en continu le dossier `%TEMP%/pnr_relay_req.json` émis par les scripts Lua asynchrones du jeu.
