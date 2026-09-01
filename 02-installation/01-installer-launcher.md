---
title: "Installer et configurer le launcher"
category: "Guide d'installation"
slug: "installer-launcher"
description: "Guide étape par étape pour installer le launcher officiel, vérifier les signatures et démarrer en toute sécurité."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~3 min"
order: 5
---

# Installer et configurer le launcher

Le launcher Propnight Reloaded est une application de bureau légère propulsée par Tauri v2. Il gère l'installation des dépendances, la vérification des fichiers et le lancement sécurisé du jeu.

## Téléchargement de l'exécutable

Rendez-vous sur la page [Télécharger](/download) du site et récupérez le programme d'installation Windows (.exe). Le binaire est auto-contenu et ne nécessite aucun runtime lourd externe.

## Vérification SHA-256

Pour vous assurer que le fichier n'a pas été altéré pendant le téléchargement, vous pouvez exécuter la commande PowerShell suivante pour comparer la somme de contrôle :

```powershell
Get-FileHash -Algorithm SHA256 .\Propnight-Reloaded-Setup.exe
```

Le résultat doit correspondre exactement à l'empreinte publiée sur la page de téléchargement :
`9f4c1b7e26a08d5531ee7f0c94ab13d8e5720c6b8a41f9d3c07e5b62a8149fce`

### Premier lancement

Lors du premier démarrage, le launcher effectuera une vérification de votre installation Steam et créera automatiquement les dossiers nécessaires dans le répertoire de l'application.
