---
title: "Lier son installation originale Propnight"
category: "Guide d'installation"
slug: "lier-jeu"
description: "Comment détecter automatiquement ou spécifier manuellement le chemin du dossier Propnight sur votre machine."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~3 min"
order: 6
---

# Lier son installation originale Propnight

Le launcher a besoin de connaître l'emplacement de votre jeu Propnight pour pouvoir y attacher le démon de relais réseau et le chargeur UE4SS.

## Détection automatique Steam

Le launcher inspecte la clé de registre de Steam et le fichier `libraryfolders.vdf` pour localiser automatiquement le dossier `SteamApps/common/Propnight`. Si le jeu est trouvé, un badge vert confirme la liaison.

## Sélection manuelle du dossier

Si votre jeu est installé sur un disque externe ou un dossier personnalisé, cliquez sur « Parcourir » dans les paramètres du launcher et sélectionnez le dossier contenant `Propnight.exe`.

> **Information**
> Le dossier doit contenir l'arborescence standard : `Propnight/Binaries/Win64/Propnight-Win64-Shipping.exe`.
