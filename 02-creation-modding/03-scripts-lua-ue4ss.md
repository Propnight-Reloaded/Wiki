---
title: "Scripts Lua UE4SS"
category: "Création & Modding"
slug: "scripts-lua-ue4ss"
description: "Développer des modules Lua pour interagir avec les acteurs de la scène, créer des commandes de console et des hooks de gameplay."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~7 min"
order: 8
---

# Scripts Lua UE4SS

RE-UE4SS fournit une API Lua complète pour manipuler les classes, appeler des fonctions virtuelles du moteur et écouter les événements du gameplay en temps réel.

## Structure d'un mod Lua

Tous les scripts Lua résident dans le dossier :
`Propnight/Binaries/Win64/ue4ss/Mods/<NomDuMod>/scripts/main.lua`

Pour que le mod soit actif, il doit être déclaré dans `mods.txt` avec la valeur `1`.

## Exemple d'écoute d'événement et raccourci

```lua
-- Exemple d'écoute de la touche F3 pour inspecter le joueur local
RegisterKeyBind(Key.F3, function()
  print("[DevMod] Inspection des acteurs...")
  local PCs = FindAllOf("PlayerController")
  if PCs then
    for _, PC in ipairs(PCs) do
      if PC:IsValid() then
        print("PlayerController actif : " .. PC:GetFullName())
      end
    end
  end
end)
```
