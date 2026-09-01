---
title: "Serveur ShipGate & Mises à jour"
category: "Architecture & Contribution"
slug: "shipgate-api"
description: "Architecture du serveur Node.js/Express, distribution des mises à jour Tauri v2 signées Minisign et proxy GitHub."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~5 min"
order: 13
---

# Serveur ShipGate & Mises à jour

`ShipGate` est le serveur cloud d'authentification et de distribution sécurisée (portier), hébergé à l'adresse `shipgate.zekyro.dev`.

## Rôles de ShipGate

1. **Fournisseur de Mises à Jour Tauri v2** : Expose la route standard `/api/update/:app` qui lit les métadonnées `latest.json` et extrait la signature Minisign (`.exe.sig`) pour valider les mises à jour automatiques du launcher.
2. **Proxy de Releases Privées GitHub** : Télécharge, compresse et met en cache localement les archives de mods (`mods-lua.zip`, `mods-manifest.json`) et dépendances DLL pour contourner les quotas de l'API GitHub.
3. **Webhooks GitHub** : Reçoit les notifications d'événements de publication de release validées par signature HMAC pour synchroniser instantanément les assets.
