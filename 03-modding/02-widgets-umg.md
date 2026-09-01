---
title: "Modification des widgets d'interface UMG"
category: "Création & Modding"
slug: "widgets-umg"
description: "Personnaliser les menus, compteurs de score, réticules et affichages ATH via les Blueprints et widgets UMG."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~6 min"
order: 10
---

# Modification des widgets d'interface UMG

Les interfaces de Propnight sont construites avec le framework Unreal Motion Graphics (UMG). Grâce à UE4SS et au chargeur LogicMods, vous pouvez remplacer ou surcharger les widgets standards.

## Comment fonctionnent les widgets UMG

Les widgets UMG sont des classes Blueprint héritant de `UserWidget`. Lors de la création d'un widget (par exemple `W_PressAnyKeyScreen_C`), le moteur instancie l'arbre hiérarchique d'éléments graphiques (Canvas, Text, Button, Image).

## LogicMods & BPModLoaderMod

En activant l'option « Activer les mods Blueprint » dans le launcher, le dossier `LogicMods` est analysé au lancement du jeu pour injecter vos interfaces personnalisées sans décompiler les fichiers de base.
