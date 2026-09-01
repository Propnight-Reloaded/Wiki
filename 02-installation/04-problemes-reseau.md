---
title: "Résolution des problèmes réseau & NAT"
category: "Guide d'installation"
slug: "problemes-reseau"
description: "Que faire en cas d'échec de connexion, de déconnexion inopinée ou de latence élevée lors du matchmaking P2P."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~5 min"
order: 8
---

# Résolution des problèmes réseau & NAT

Le multijoueur repose sur une négociation P2P directe entre les joueurs. En cas de difficulté à rejoindre un salon, suivez les vérifications ci-dessous.

## Vérifier l'état de Steam

Le protocole P2P repose sur l'API Steamworks. Assurez-vous que votre client Steam est bien en ligne et connecté avant de lancer une partie.

## Autoriser SteamRelay dans le Pare-feu

Lors du premier lancement, Windows Pare-feu peut demander une autorisation d'accès pour `propnight-steam-relay.exe`. Cochez impérativement « Réseaux privés » pour permettre la communication loopback locale.

### Optimiser la latence

- Privilégiez une connexion filaire Ethernet plutôt que le Wi-Fi.
- Si votre hôte est situé sur un autre continent, une latence de 100 à 150 ms est normale en raison des distances physiques.
- Fermez les applications gourmandes en bande passante ou en upload pendant vos sessions.
