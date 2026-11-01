---
title: "Serveur ShipGate & Mises à jour"
category: "Architecture & Contribution"
slug: "shipgate-api"
description: "Architecture du serveur Node.js/Express, publication des builds par la CI et distribution des mises à jour Tauri v2 signées Minisign."
lastRevision: "28.08.2026"
version: "v0.9.4"
readTime: "~5 min"
order: 13
---

# Serveur ShipGate & Mises à jour

`ShipGate` est le serveur cloud d'authentification et de distribution sécurisée (portier), hébergé à l'adresse `shipgate.zekyro.dev`.

## Rôles de ShipGate

1. **Fournisseur de Mises à Jour Tauri v2** : Expose la route standard `/api/update/:app` qui lit les métadonnées `latest.json` et extrait la signature Minisign (`.exe.sig`) pour valider les mises à jour automatiques du launcher.
2. **Réception des builds de la CI** : les pipelines GitHub Actions poussent leurs fichiers via `PUT /api/publish/:app/:version/:fichier`, puis `POST …/release` bascule le canal (`stable` ou `dev`) de façon atomique. ShipGate ne va jamais chercher de releases sur GitHub.
3. **Téléchargements protégés** : codes d'accès révocables (`/redeem/:code`), modes d'accès par application et URLs signées à durée limitée pour l'updater.
