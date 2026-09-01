---
title: "Création et installation de maps personnalisées (.pak)"
category: "Création & Modding"
slug: "maps-custom"
description: "Guide pour concevoir, packager et installer des niveaux communautaires au format .pak pour Propnight Reloaded."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~8 min"
order: 9
---

# Création et installation de maps personnalisées (.pak)

Propnight Reloaded permet aux joueurs de charger et d'héberger des cartes créées par la communauté en Unreal Engine 4.

## Structure d'un fichier .pak

Les maps personnalisées de Propnight sont des archives d'assets Unreal Engine 4.26 packagées. Elles sont déposées dans le sous-dossier `Propnight/Content/Paks/~mods/`.

## Installer une map communautaire

Téléchargez le fichier `.pak` fourni par le créateur et déposez-le dans le dossier mods de votre jeu. Le launcher vérifie automatiquement la présence de la map et calcule son hash SHA-256 pour s'assurer qu'elle correspond exactement à celle de l'hôte.

> **Avertissement**
> Si un joueur dans le salon possède une version différente du fichier .pak, il ne pourra pas charger la partie.

### Recommandations pour le cook UE4

Les créateurs doivent utiliser Unreal Engine version 4.26.2 avec la compression Oodle standard activée pour garantir une compatibilité parfaite avec le moteur du jeu.
