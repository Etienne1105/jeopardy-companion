# Géopardie — Compagnon Pop Culture Jeopardy

Tableau de pointage compagnon pour suivre ton score en regardant **Pop Culture Jeopardy!** (Amazon Prime), saison 1. Ce n’est pas un jeu de questions : c’est un *board* interactif qui reproduit la grille de l’émission pour que tu marques tes gains et tes pertes en temps réel, manche par manche.

## Ce que ça fait

- **20 Knockout Games** de la saison 1 — chacun avec ses 6 catégories Jeopardy!, ses 6 catégories Double Jeopardy!, sa finale, ses 3 équipes et le score final réel.
- **1 tape = gagné (+), 2 tapes = perdu (−)** sur chaque case (fenêtre de 260 ms).
- **Appui long sur une case = Daily Double** : un encart de mise s’ouvre (Réussi / Raté). Tu le déclenches toi-même au bon moment — aucun DD n’est marqué d’avance.
- **Anti-spoiler** : le vrai résultat (scores des équipes + gagnant) reste caché derrière un bouton « Révéler le vrai résultat ».
- **En-têtes éditables** : si une catégorie diffère à l’écran, touche l’en-tête pour la corriger.
- Effets sonores Web Audio (avec bouton mute).

## Utilisation

Ouvre l’URL Netlify (ou `index.html` dans un navigateur). Choisis l’épisode que tu regardes, puis suis ton pointage.

## Stack

HTML / CSS / JavaScript vanilla. **Zéro dépendance, zéro build.** Un seul fichier : `index.html`. Polices Anton + Oswald (Google Fonts).

## Déploiement

Hébergé sur **Netlify** en déploiement continu depuis ce repo : chaque `push` sur `main` redéploie l’app automatiquement, sans étape manuelle.

- Publish directory : racine (`.`)
- Build command : aucune

## Développement local

Aucune installation. Ouvre `index.html` dans un navigateur, ou sers le dossier :

```bash
python3 -m http.server 8000
# puis http://localhost:8000
```

## Notes

- Le pointage **n’est pas sauvegardé** entre deux rechargements. Recharger = repartir à zéro. *(Réactivable via `localStorage` maintenant que l’app tourne hors de l’iframe claude.ai.)*
- Données des catégories et scores : [The Jeopardy! Fan](https://thejeopardyfan.com).