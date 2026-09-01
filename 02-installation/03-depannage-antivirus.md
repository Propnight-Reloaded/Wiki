---
title: "Dépannage des faux positifs antivirus"
category: "Guide d'installation"
slug: "depannage-antivirus"
description: "Comprendre pourquoi Windows Defender et certains antivirus signalent les injecteurs DLL et comment configurer une exclusion sécurisée."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~4 min"
order: 7
---

# Dépannage des faux positifs antivirus

Les mod loaders comme RE-UE4SS injectent du code dans la mémoire vive de l'exécutable du jeu au moment de son démarrage. Cette technique d'injection mémoire (DLL injection) est courante dans le monde du modding de jeux vidéo, mais est souvent signalée par précaution heuristique par Windows Defender.

## Pourquoi ce signalement ?

L'injecteur accède au thread principal du processus Unreal Engine pour charger les hooks Lua. Les moteurs antivirus modernes considèrent tout comportement d'injection mémoire comme potentiellement suspect s'il n'est pas issu d'un éditeur certifié par un certificat d'entreprise onéreux.

## Ajouter une exclusion dans Defender

Si Windows Defender bloque le chargement de UE4SS ou de Goldberg Emulator, ajoutez une exclusion sur le dossier du launcher :

1. Ouvrez **Sécurité Windows** → **Protection contre les virus et menaces**.
2. Cliquez sur **Gérer les paramètres** sous « Paramètres de protection contre les virus ».
3. Dans la section **Exclusions**, cliquez sur **Ajouter ou supprimer des exclusions**.
4. Sélectionnez **Dossier** et désignez le répertoire de Propnight Reloaded.

> **Avertissement**
> Ne téléchargez jamais le launcher en dehors de notre site officiel ou de notre GitHub pour éviter les copies malveillantes.
