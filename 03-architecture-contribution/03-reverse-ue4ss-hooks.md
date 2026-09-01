---
title: "Reverse-Engineering & Hooks"
category: "Architecture & Contribution"
slug: "reverse-ue4ss-hooks"
description: "Détails sur le contournement d'authentification PlayFab, la redirection ClientTravel et l'émulateur Goldberg."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~6 min"
order: 12
---

# Reverse-Engineering & Hooks

L'intégration dans Unreal Engine 4 repose sur des hooks mémoire ciblés et l'injection de l'émulateur Goldberg pour Steam.

## 1. Goldberg Emulator (`steam_api64.dll`)

Le launcher remplace la DLL Steam d'origine par Goldberg Emulator :
- La DLL originale est sauvegardée sous `steam_api64_o.dll`.
- Le fichier `steam_settings/steam_appid.txt` est configuré sur `1549180` (AppID officiel de Propnight).
- Le nom de compte local est injecté dynamiquement dans `steam_settings/account_name.txt`.

## 2. Scripts Clés dans `Mods/Reloaded`

- **`AuthBypass.lua`** : Intercepte le chargement du widget de titre et appelle directement `PlayfabReady()` pour court-circuiter le timeout réseau.
- **`RelayConnector.lua`** : Enregistre les commandes de console (`propnight_host`, `propnight_join`, `propnight_servers`) et déclenche le `ClientTravel("127.0.0.1:7778")` après confirmation du handshake P2P.
- **`PartyManager.lua`** : Synchronise les membres du groupe pour que le chef d'équipe entraîne automatiquement ses coéquipiers dans la partie.
