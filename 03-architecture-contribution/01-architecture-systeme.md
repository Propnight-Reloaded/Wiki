---
title: "Architecture globale du système"
category: "Architecture & Contribution"
slug: "architecture-systeme"
description: "Spécification technique complète des 4 dépôts actifs (pnr_launcher, SteamRelay, Mods, ShipGate) et des flux de données."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~8 min"
order: 10
---

# Architecture globale du système

Propnight Reloaded repose sur une architecture décentralisée pour le trafic multijoueur (P2P Steamworks), combinée à des microservices centralisés pour la sécurité, l'authentification et la distribution des mises à jour.

## Les 4 Dépôts Actifs

1. **`pnr_launcher`** (Tauri v2 + React 19) : L'orchestrateur client. Gère SteamCMD, injecte UE4SS et Goldberg, lance SteamRelay en arrière-plan et gère les mises à jour signées.
2. **`SteamRelay`** (Rust + Tokio) : Le démon local traduisant les sockets UDP du jeu en flux P2P Steamworks (NAT Traversal).
3. **`Mods`** (Lua / UE4SS v3) : Les scripts injectés dans le runtime Unreal Engine (AuthBypass, RelayConnector, PartyManager).
4. **`ShipGate`** (Node.js + Express + Docker) : Serveur portier (`shipgate.zekyro.dev`) gérant les signatures Minisign, l'auto-updater Tauri v2 et le proxy de releases privées GitHub.

## Diagramme des Flux Réseau

```
[ Jeu Propnight (UE4.26) ] 
       ↕ (UDP Local 127.0.0.1:7777 / 7778)
[ SteamRelay Daemon (Rust) ] <───(File IPC: pnr_relay_req.json)─── [ Mods Lua (UE4SS) ]
       ↕ (Steamworks P2P: SDR / ICE)
[ SteamRelay Hôte Distant ]
```
