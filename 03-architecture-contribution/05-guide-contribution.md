---
title: "Guide du contributeur"
category: "Architecture & Contribution"
slug: "guide-contribution"
description: "Comment configurer l'environnement de développement local, cloner les 4 repos, compiler les binaires et soumettre des PRs."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~6 min"
order: 14
---

# Guide du contributeur

Vous souhaitez contribuer au code source de Propnight Reloaded ? Ce guide décrit la configuration de votre environnement de développement.

## Prérequis de Développement

- **Node.js** : `>= 20.18.0` & **pnpm** : `>= 10.0.0`
- **Rust Toolchain** : `rustc >= 1.80` & `cargo`
- **Tauri CLI v2** : `cargo install tauri-cli`
- **Git** : avec support des sous-modules

## Structure des Dépôts

Clonez les dépôts dans un même dossier de travail :
- `pnr_launcher/` : `npm run tauri dev`
- `SteamRelay/` : `cargo run -- --daemon --port 8080`
- `Mods/` : Tests des scripts Lua dans le dossier de jeu
- `Website/` : `pnpm dev`
- `Wiki/` : Documentation Markdown

## Conventions de Commit

Nous appliquons la convention *Conventional Commits* :
- `feat(relay): support multi-lobby broadcast`
- `fix(launcher): resolve steamcmd download timeout`
- `docs(wiki): update UMG blueprint hooks`
