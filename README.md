# LOL Draft Guessr

[![Website](https://img.shields.io/badge/Website-online-brightgreen.svg)](https://plantim.github.io/LOL-Draft-Guessr/)

Sélectionne jusqu'à 5 champions ennemis : l'outil attribue à chacun le rôle le plus probable via un **assignement global au maximum de vraisemblance** (chaque rôle est unique dans l'équipe). Tu peux forcer le rôle d'un champion (menu déroulant) : le reste est alors recalculé automatiquement.

## Contenu

- `index.html`, `style.css`, `guesser.js` — l'application.
- `role_data.json` — taux de sélection par rôle et par champion (données embarquées).

Les icônes de champions et la liste des champions proviennent de **Data Dragon** (CDN officiel de Riot), chargées dynamiquement — il faut donc une connexion internet.

## Mettre à jour les données de rôle

`role_data.json` a la forme `{ "championRoles": { "NomChampion": { "top": 97, "jungle": 0.5, "middle": 2.5, "bottom": 0, "support": 0 }, ... } }` (pourcentages de pick par lane). Remplace ce fichier pour rafraîchir les données ou ajouter de nouveaux champions.

## Comment ça marche

Pour chaque champion, on connaît la répartition de ses parties par lane. On cherche l'attribution des 5 rôles (un par joueur, tous distincts) qui **maximise la vraisemblance** (somme des log-pickrates). Un rôle jamais joué par un champion garde une probabilité plancher très faible, ce qui permet quand même de le placer si nécessaire. La « confiance » affichée est la part du pickrate de ce rôle parmi les rôles encore disponibles pour ce champion.

---

Projet non officiel, non affilié à Riot Games. Données de jeu © Riot Games.
