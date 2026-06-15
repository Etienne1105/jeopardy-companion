# Géopardie — Compagnon Jeopardy!

Tableau de pointage compagnon pour suivre **ton** score en regardant Jeopardy!. Ce n'est pas un jeu de questions : c'est un *board* interactif qui reproduit la grille de l'émission pour que tu marques tes gains, tes pertes et les cases passées en temps réel, manche par manche.

Couvre plusieurs éditions : **Pop Culture Jeopardy!** (Prime Video) et **Jeopardy! classique** (Crave / données J-Archive).

## Ce que ça fait

- **Navigation à 3 niveaux** : Édition → Collection → Épisode.
- **89 épisodes jouables**, chacun avec ses 6 catégories Simple, ses 6 catégories Double, sa finale, ses participants et le résultat réel.
- **Marquage d'une case** :
  - **1 clic** = réussie (+ la valeur)
  - **2 clics** = échec (− la valeur)
  - **clic long** = passée (ni gain ni perte — pour les cases jouées par d'autres à l'écran)
- **Daily Doubles automatiques** : les positions réelles sont intégrées, donc cliquer une case Daily Double ouvre tout seul l'encart de mise (Réussi / Raté). Sur les épisodes non marqués (ex. Pop Culture), un **triple clic** déclenche un DD manuel — un bandeau te le rappelle.
- **Anti-spoiler** : le vrai résultat (scores + gagnant) reste caché derrière un bouton « Révéler le vrai résultat ». Les Daily Doubles ne sont pas révélés visuellement avant le clic.
- **En-têtes éditables** : si une catégorie diffère à l'écran, touche l'en-tête pour la corriger.
- Effets sonores Web Audio (bouton mute), animation de score, annuler / recommencer.

## Contenu

**Pop Culture Jeopardy!** — Prime Video, format Knockout (3 équipes)
- Saison 1 — 20 Knockout Games

**Jeopardy! classique** — format standard, joueurs solo (données J-Archive)
- The IBM Challenge (Watson vs Jennings & Rutter, 2011) — 2 games
- Brad Rutter — run original (S17, 2000) — 5 games
- Tournament of Champions 2015 / 2017 / 2019 — 10 games chacun
- James Holzhauer (S35, 2019) — 32 victoires
- *Ultimate Tournament of Champions (S21, 2005) — à venir*

## Utilisation

Ouvre l'URL Netlify (ou `index.html` dans un navigateur). Choisis l'édition, la collection, puis l'épisode que tu regardes, et suis ton pointage.

## Stack

HTML / CSS / JavaScript vanilla. **Zéro dépendance, zéro build.** Un seul fichier : `index.html`. Polices Anton + Oswald (Google Fonts).

## Déploiement

Hébergé sur **Netlify** en déploiement continu depuis ce repo : chaque `push` sur `main` redéploie l'app automatiquement.

- Publish directory : racine (`.`)
- Build command : aucune

## Développement local

Aucune installation. Ouvre `index.html` dans un navigateur, ou sers le dossier :

```bash
python3 -m http.server 8000
# puis http://localhost:8000
```

## Notes

- Le pointage **n'est pas sauvegardé** entre deux rechargements. Recharger = repartir à zéro. *(Réactivable via `localStorage`.)*
- **Données** — catégories, finales, scores réels et positions des Daily Doubles parsés depuis le HTML brut de **J-Archive** (épisodes classiques) ; Pop Culture vient de **The Jeopardy! Fan**. Le détail du périmètre vit dans `notes/`.
- Les **finales de tournoi** se jouent sur 2 games (score cumulé) : le « gagnant » affiché par épisode est celui *du game*, pas forcément le champion du tournoi.
- Les **anciens épisodes** (avant nov. 2001, ex. Brad Rutter 2000) utilisaient des valeurs $100–$500 / $200–$1000 ; l'app affiche les valeurs modernes — un repère, pas un calque exact.
