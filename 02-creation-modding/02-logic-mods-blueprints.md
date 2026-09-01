---
title: "Blueprints & Widgets UMG"
category: "Création & Modding"
slug: "logic-mods-blueprints"
description: "Personnaliser les menus, compteurs de score, réticules et affichages ATH via les Blueprints et LogicMods."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~6 min"
order: 7
---

# Blueprints & Widgets UMG

Les interfaces de Propnight sont construites avec le framework Unreal Motion Graphics (UMG). Grâce à UE4SS et au chargeur LogicMods, vous pouvez remplacer ou surcharger les widgets standards.

## Activation dans le Launcher

Dans les paramètres du launcher :
1. Cochez l'option **« Activer les mods Blueprint (LogicMods) »**.
2. Le launcher configure automatiquement `BPModLoaderMod : 1` dans le fichier `mods.txt` de UE4SS.
3. Si l'option est désactivée, le dossier est renommé en `LogicMods.disabled` pour empêcher tout chargement par le moteur.

## Hooks sur les Widgets Clés

Les scripts du projet interceptent plusieurs widgets essentiels au démarrage :
- `W_PressAnyKeyScreen_C` : Intercepté par `AuthBypass.lua` pour appeler `PlayfabReady()`.
- `W_VictoryScreen_C` : Intercepté par `RewardSystem.lua` pour déclencher les récompenses de fin de partie.
