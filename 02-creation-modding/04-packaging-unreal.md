---
title: "Packaging Unreal Engine"
category: "Création & Modding"
slug: "packaging-unreal"
description: "Utilisation d'UnrealPak et configuration d'Unreal Engine 4.26 pour compiler des fichiers .pak compatibles."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~5 min"
order: 9
---

# Packaging Unreal Engine

Pour distribuer vos cartes personnalisées et vos assets dans Propnight, vous devez les compiler pour la version exacte du moteur : **Unreal Engine 4.26.2**.

## 1. Configuration du Cook UE4.26

Dans l'Unreal Editor :
- **Target Platform** : Windows (64-bit).
- **Cook Mode** : By the book.
- **Compression** : Oodle standard.

## 2. Utiliser UnrealPak.exe

UnrealPak est l'outil officiel d'Epic Games situé dans `Engine/Binaries/Win64/UnrealPak.exe` :

```cmd
UnrealPak.exe "C:\Output\MaMap.pak" -create="C:\Sources\filelist.txt" -compress
```

### Arborescence interne requise

L'arborescence interne du `.pak` doit impérativement reproduire le chemin relatif de Propnight :
`../../../Propnight/Content/Maps/...`
