---
title: "Jouer en ligne & Commandes"
category: "Guide du Joueur"
slug: "jouer-en-ligne"
description: "Comment créer un lobby, inviter des amis avec Steam Overlay, rejoindre une partie et utiliser les commandes console en jeu."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~5 min"
order: 3
---

# Jouer en ligne & Commandes

Propnight Reloaded intègre un pontage complet entre l'overlay Steam, la console Unreal Engine (touche `F10` ou `~`) et le démon réseau P2P.

## 1. Créer une partie (Hôte)

Pour héberger une partie :
- Directement depuis la console en jeu (touche **F10**) :
  ```text
  propnight_host abbey_main
  ```
  *(ou `host camp`, `host school`, `host farm`)*
- Le démon `SteamRelay` passe automatiquement en mode hôte, enregistre le salon sur le Master Server et déclenche la transition `ClientTravel` locale vers la carte avec l'option `?listen`.

## 2. Inviter et Rejoindre des Amis (Steam Overlay)

Le projet supporte les invitations Steam Rich Presence :
1. Créez un groupe en tapant :
   ```text
   create_party
   ```
2. Tapez simplement dans la console :
   ```text
   invite
   ```
3. L'overlay Steam s'ouvre pour inviter vos amis en un clic. Vos amis peuvent également faire un clic-droit sur votre profil Steam → « Rejoindre la partie ».

## 3. Commandes Console Principales (F10)

| Commande | Action |
|---|---|
| `propnight_servers` | Affiche la liste des serveurs et lobbys publics actifs |
| `propnight_join <SteamID>` | Rejoint directement l'hôte via son identifiant Steam |
| `create_party` | Crée un salon d'équipe avec synchronisation de groupe |
| `invite` | Ouvre l'overlay Steam pour inviter des amis |
| `party_leave` | Quitte le groupe d'amis actuel |
| `status` | Affiche l'état du démon local SteamRelay et la latence |
