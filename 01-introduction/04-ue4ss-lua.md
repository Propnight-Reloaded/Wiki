---
title: "UE4SS & injection des scripts Lua"
category: "Introduction"
slug: "ue4ss-lua"
description: "Comment RE-UE4SS interagit avec le moteur Unreal Engine 4 pour injecter des scripts Lua sans modifier les binaires du jeu."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~5 min"
order: 4
---

# UE4SS & injection des scripts Lua

RE-UE4SS (Unreal Engine 4/5 Scripting System) est un mod loader puissant permettant d'exécuter du code Lua en temps réel au cœur du runtime Unreal Engine. Il analyse la mémoire du jeu et résout dynamiquement les UObjects et UFunctions sans modifier l'exécutable sur disque.

## Qu'est-ce que RE-UE4SS ?

RE-UE4SS fonctionne en tant que proxy DLL (`dwmapi.dll` ou injecteur direct) chargé au démarrage du processus de jeu. Il initialise un environnement Lua complet avec accès à la table globale des objets du moteur Unreal (`GUObjectArray`).

## Hooks clés injectés

Nos scripts Lua interceptent les écrans de connexion et les commandes console du jeu pour lier le gameplay à SteamRelay :

```lua
-- Exemple d'enregistrement de commande console dans UE4SS
RegisterConsoleCommandHandler("propnight_host", function(cmd, args)
  print("[Relay] Lancement de l'hébergement pour la map : " .. (args[1] or "Default"))
  SendRelayCommand("start_host", { map = args[1] or "Farm_House" })
end)
```

### Contournement PlayFab

Le script `AuthBypass.lua` détecte l'apparition de l'écran « Press Any Key » et déclenche immédiatement la transition interne vers le menu principal sans attendre la réponse du serveur PlayFab officiel décommissionné.
