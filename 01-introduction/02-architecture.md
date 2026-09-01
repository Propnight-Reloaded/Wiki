---
title: "Architecture du projet"
category: "Introduction"
slug: "architecture"
description: "Vue d'ensemble des quatre briques du projet : client Propnight vanilla, launcher Tauri, patch Lua UE4SS et tunnel SteamRelay Rust."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~7 min"
order: 2
---

# Architecture du projet

L'écosystème Propnight Reloaded sépare strictement la couche interface utilisateur, la couche réseau locale et le moteur Unreal Engine 4.26 du jeu. Cette séparation permet d'assurer une stabilité maximale sans risque de corrompre l'installation originale.

## La pile technique

Chaque composant remplit une fonction dédiée dans le cycle de vie d'une session multijoueur :

- **pnr_launcher (Tauri v2 + React 19)** : Orchestre le téléchargement des mods, la vérification de version et le lancement du jeu.
- **SteamRelay (Rust + Tokio)** : Démon local traduisant les sockets UDP du jeu en flux P2P Steamworks (NAT Traversal).
- **UE4SS v3 & Mods Lua** : Charge les hooks dans le moteur Unreal Engine 4 pour court-circuiter l'ancien système PlayFab.
- **ShipGate (Node.js & Docker)** : Serveur portier gérant les mises à jour automatiques du launcher et le proxy de téléchargement sécurisé.

### Handshake de session P2P

Lorsqu'un joueur héberge ou rejoint une partie, le script Lua RelayConnector intercepte l'appel Unreal Engine et émet une commande locale vers SteamRelay par File IPC :

```lua
-- File IPC handshake avec le démon local SteamRelay
local function SendRelayCommand(cmd, payload)
  local reqPath = os.getenv("TEMP") .. "/pnr_relay_req.json"
  local file = io.open(reqPath, "w")
  if file then
    file:write(json.encode({ command = cmd, payload = payload, timestamp = os.time() }))
    file:close()
  end
end

-- Exemple : Commande de join vers un hôte Steam
SendRelayCommand("join_host", { targetSteamId = "76561198000000000" })
```

## Composants et rôles réseau

| Composant | Rôle | Technologie | Port / Protocole |
|---|---|---|---|
| pnr_launcher | Orchestrateur client, injection & UI | Tauri v2 · React | Local IPC |
| SteamRelay | Démon de tunnel P2P Steamworks | Rust · Steamworks | UDP 7778 / P2P |
| UE4SS & Mods | Bypass d'authentification & hooks | Lua · C++ | Mémoire runtime |
| ShipGate | Distribution et proxy de mise à jour | Node.js · Minisign | HTTPS 443 |

### Limites connues

- La progression de compte et l'inventaire officiel PlayFab ne peuvent être restaurés côté serveur officiel.
- Les joueurs avec un NAT symétrique très restrictif passent par les relais de secours Steam Datagram Relay (SDR).
- Tous les joueurs d'un lobby doivent disposer de la même version de mod et de map personnalisée.
