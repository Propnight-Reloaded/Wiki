---
title: "Résolution des problèmes réseau"
category: "Guide du Joueur"
slug: "resolution-problemes"
description: "Diagnostic réseau, pare-feu Windows, vérification des processus résiduels et optimisation de la latence."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~5 min"
order: 5
---

# Résolution des problèmes réseau

Le multijoueur repose sur une liaison P2P directe entre les joueurs via le réseau Steamworks. En cas de difficulté de connexion, voici les étapes de diagnostic.

## 1. Vérifier l'état de Steam

Le protocole P2P repose sur l'API Steamworks. Assurez-vous que votre client Steam est bien en ligne et connecté avec votre compte avant de lancer une partie.

## 2. Autoriser SteamRelay dans le Pare-feu

Lors du premier lancement, Windows Pare-feu peut demander une autorisation d'accès pour `propnight-steam-relay.exe`. Cochez impérativement « Réseaux privés » pour permettre la communication loopback locale (ports UDP `7777` et `7778`).

## 3. Nettoyage des processus résiduels

Si une partie précédente a crashé, un démon de relais ou un processus de jeu peut rester actif en arrière-plan. Le launcher effectue un nettoyage automatique à la fermeture, mais vous pouvez également exécuter dans PowerShell :

```powershell
taskkill /F /IM Propnight-Win64-Shipping.exe /IM propnight-steam-relay.exe
```

### Optimiser la latence

- Privilégiez une connexion filaire Ethernet plutôt que le Wi-Fi.
- Si l'hôte est situé sur un autre continent, une latence de 100 à 150 ms est normale en raison des distances physiques.
