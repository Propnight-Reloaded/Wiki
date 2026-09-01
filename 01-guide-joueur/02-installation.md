---
title: "Installation du jeu & launcher"
category: "Guide du Joueur"
slug: "installation"
description: "Guide étape par étape pour installer le launcher officiel, télécharger les fichiers du jeu via SteamCMD et lier votre installation."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~5 min"
order: 2
---

# Installation du jeu & launcher

Le launcher Propnight Reloaded est une application de bureau légère propulsée par Tauri v2. Il gère l'installation automatique des dépendances (Goldberg Emulator, RE-UE4SS v3, mods Lua) et le lancement sécurisé du jeu.

## Téléchargement du launcher

1. Rendez-vous sur la page [Télécharger](/download) du site.
2. Récupérez le programme d'installation Windows (`.exe`).
3. Exécutez l'installateur et choisissez votre dossier d'installation (ex: `C:\Jeux\Propnight Reloaded`).

## Téléchargement ou Liaison de Propnight

Le launcher vous propose deux méthodes simples :
- **Détection automatique Steam** : Si Propnight est déjà installé sur votre compte Steam, le launcher le détectera automatiquement dans vos `SteamApps/common/Propnight`.
- **Téléchargement propre via SteamCMD intégré** : Si le jeu n'est pas installé, le launcher intègre SteamCMD pour télécharger les fichiers officiels du jeu (AppID `1549180`) en toute légalité avec vos identifiants Steam.

```powershell
# Vérification de la somme SHA-256 du launcher
Get-FileHash -Algorithm SHA256 .\Propnight-Reloaded-Setup.exe
```

### Premier lancement

Au clic sur « Lancer », le launcher :
1. Prépare l'émulateur Goldberg (`steam_api64.dll`) avec votre nom de compte.
2. Extrait la version stable de RE-UE4SS v3 et les scripts Lua.
3. Démarre en arrière-plan le démon réseau local `SteamRelay`.
4. Lance l'exécutable `Propnight-Win64-Shipping.exe`.
