---
title: "Écriture de scripts et mods Lua personnalisés"
category: "Création & Modding"
slug: "scripts-lua"
description: "Développer des modules Lua pour interagir avec les acteurs de la scène, créer des commandes de triche ou des modes de jeu custom."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~7 min"
order: 11
---

# Écriture de scripts et mods Lua personnalisés

UE4SS fournit une API Lua complète pour manipuler les classes, appeler des fonctions virtuelles du moteur et écouter les événements du gameplay en temps réel.

## Structure d'un script Lua

Tous les scripts Lua résident dans le dossier `UE4SS/Mods/<NomDuMod>/scripts/main.lua`. Pour que le mod soit actif, il doit être déclaré dans `mods.txt` avec la valeur `1`.

## Écouter les événements du jeu

UE4SS fournit les fonctions globales `RegisterHook` et `StaticFindObject` pour s'accrocher à n'importe quelle fonction du jeu.

### Exemple de script minimal

Exemple d'écoute d'une touche de raccourci pour afficher un message console :

```lua
RegisterKeyBind(Key.F8, function()
  print("[MyCustomMod] Touche F8 actionnée !")
  local playerController = GetPlayerController()
  if playerController:IsValid() then
    print("Contrôleur joueur valide : " .. playerController:GetFullName())
  end
end)
```
