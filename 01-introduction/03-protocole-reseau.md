---
title: "Protocole réseau P2P & Steamworks"
category: "Introduction"
slug: "protocole-reseau"
description: "Détails sur l'émulation réseau, la traduction des paquets UDP locaux en flux P2P Steamworks et le franchissement des NAT."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~6 min"
order: 3
---

# Protocole réseau P2P & Steamworks

Sans serveurs de jeu dédiés centralisés, faire communiquer deux joueurs situés derrière des box Internet (routeurs NAT) nécessite soit d'ouvrir manuellement des ports, soit d'utiliser des techniques de STUN/TURN/ICE. SteamRelay tire parti de l'infrastructure mondiale de Steamworks pour négocier automatiquement la connexion directe P2P.

## Le défi du NAT Traversal

Le NAT Traversal est le processus permettant à deux machines clientes d'établir une liaison directe sans adresse IP publique dédiée :

- **NAT Facile (Full Cone / Restricted)** : Les paquets UDP sont transmis directement en peer-to-peer (latence minimale ~20-40 ms).
- **NAT Symétrique** : Les paquets sont relayés automatiquement via les serveurs de relais de Valve (Steam Datagram Relay - SDR) avec un léger surcroît de latence (10-25 ms).

## Fonctionnement de SteamRelay

SteamRelay agit comme un proxy bidirectionnel ultra-léger développé en Rust. Il capture les paquets UDP émis par le jeu Unreal Engine local et les envoie au SteamID de l'hôte via les sockets P2P Steamworks.

> **Information**
> Aucun port n'a besoin d'être ouvert sur votre routeur : le protocole Steamworks P2P négocie automatiquement le franchissement de pare-feu.

### Le pontage Loopback UDP

Sur la machine cliente, le jeu se connecte simplement à l'adresse locale `127.0.0.1:7778`. SteamRelay réceptionne ce trafic et l'achemine de manière transparente vers l'hôte.
