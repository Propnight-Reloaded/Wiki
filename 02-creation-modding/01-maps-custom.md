---
title: "Maps personnalisées (.pak)"
category: "Création & Modding"
slug: "maps-custom"
description: "Guide pour concevoir, packager et installer des niveaux communautaires au format .pak pour Propnight Reloaded."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~8 min"
order: 6
---

# Maps personnalisées (.pak)

Propnight Reloaded permet aux joueurs de charger et d'héberger des cartes créées par la communauté en Unreal Engine 4.26.

## Structure et emplacement des fichiers

Les maps personnalisées sont des fichiers `.pak` déposés dans :
`Propnight/Content/Paks/~mods/` (ou `Propnight/Content/Paks/LogicMods/`).

## Détection et vérification de Hash par le Launcher

Le launcher calcule automatiquement la somme SHA-256 de chaque fichier `.pak` présent dans le dossier mods. Lors de la connexion à un lobby :
- L'hôte publie le hash de sa map personnalisée.
- Les clients vérifient la correspondance exacte avant d'autoriser le chargement pour éviter tout crash de désynchronisation.

> **Avertissement**
> Si un joueur dans le salon possède une version modifiée ou différente du fichier .pak, la connexion sera refusée par précaution.
