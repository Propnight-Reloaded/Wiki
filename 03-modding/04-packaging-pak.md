---
title: "Packaging d'assets et mods Unreal Engine 4"
category: "Création & Modding"
slug: "packaging-pak"
description: "Utilisation d'UnrealPak et des outils de packaging pour compiler des fichiers .pak valides et optimisés."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~5 min"
order: 12
---

# Packaging d'assets et mods Unreal Engine 4

Pour distribuer vos cartes personnalisées et vos assets dans Propnight, vous devez les compresser dans une archive au format `.pak`.

## Utiliser UnrealPak.exe

UnrealPak.exe est l'outil officiel d'Epic Games pour compresser des dossiers de contenu cuit (.uasset, .uexp, .ubulk) en une archive unique .pak.

```cmd
UnrealPak.exe "C:\Output\MonMod.pak" -create="C:\MonMod_Source\responsefile.txt" -compress
```

## Arborescence requise

L'arborescence interne du .pak doit impérativement reproduire le chemin relatif de Propnight, par exemple : `../../../Propnight/Content/...`.
