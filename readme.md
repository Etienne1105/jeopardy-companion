# Jeopardy! — Compagnon de pointage

Tableau de pointage compagnon pour suivre **ton** score en regardant Jeopardy!. Ce n'est pas un jeu de questions : c'est un *board* interactif qui reproduit la grille de l'émission pour que tu marques tes gains, tes pertes et les cases passées en temps réel, manche par manche — et qui récompense tes performances avec des médailles et une streak.

Couvre plusieurs éditions : **Pop Culture Jeopardy!** (Prime Video) et **Jeopardy! classique** (Crave / données J-Archive).

## Ce que ça fait

- **Navigation à 3 niveaux** : Édition → Collection → Épisode (présentés en tuiles-niveaux à la Donkey Kong Country / Candy Crush).
- **89 épisodes jouables**, chacun avec ses 6 catégories Simple, ses 6 catégories Double, sa finale, ses participants et le résultat réel.
- **Marquage d'une case** :
  - **1 clic** = réussie (+ la valeur)
  - **2 clics** = échec (− la valeur)
  - **clic long** = passée (ni gain ni perte — pour les cases jouées par d'autres à l'écran)
- **Daily Doubles automatiques** : les positions réelles sont intégrées, donc cliquer une case Daily Double ouvre tout seul l'encart de mise (Réussi / Raté), plafonnée à la mise max officielle. Sur les épisodes non marqués (ex. Pop Culture), un **triple clic** déclenche un DD manuel — un bandeau te le rappelle.
- **Reveal en damier** : à l'ouverture d'une manche, les montants se remplissent colonne par colonne, comme à l'écran.
- **Anti-spoiler** : le vrai résultat (scores + gagnant) reste caché derrière un bouton « Révéler le vrai résultat ». Les Daily Doubles ne sont pas révélés visuellement avant le clic.
- **En-têtes éditables** : si une catégorie diffère à l'écran, touche l'en-tête pour la corriger.
- **Son authentique Jeopardy!** (bouton mute) : le sting Daily Double à l'ouverture, le *ding* sur les bonnes réponses, le buzzer sur les mauvaises, le remplissage du plateau au reveal, la musique *Think!* en boucle pendant la finale, et le thème quand tu décroches une streak/PARFAIT.
- Animation de score, annuler / recommencer.

## Médailles, streak & statistiques

Deux mécaniques de suivi distinctes qui cohabitent :

- **Médailles par épisode** (échelle de points d'exclamation, selon ta précision) :
  - **!** — précision ≥ 70 %
  - **!!** — précision ≥ 85 %
  - **!!!** — sans-faute (100 %)
  - Affichées sous chaque tuile-niveau, en pips dorés.
- **Streak** — le marqueur de prestige : enchaîner les épisodes où tu **bats le n°1 dans les règles de l'art** (sans-faute *et* score final supérieur au vrai gagnant). Une **bannière champion** « façon Johnny Gilbert » te couronne tant que la streak tient.
- **PARFAIT** — récompense rare : une streak sur un épisode où tu couvres quasi tout le plateau débloque un **emblème diamant 3D**.
- **Écran Statistiques** : un **tableau de bord interactif de bulles néon** (une couleur par stat) — touche une bulle pour ouvrir son détail et sa barre de progression vs la légende. Streak (vs les 74 de Ken Jennings), précision, Coryat moyen, Daily Doubles, couverture, total carrière (vs Ken), meilleur épisode (vs Holzhauer), parties jouées, médailles.

Tout est **sauvegardé localement** (`localStorage`) : tes médailles, ta streak et tes totaux de carrière persistent entre les sessions.

## Identité visuelle — Néon Pop

Esthétique inspirée de **Pop Culture Jeopardy!** (l'édition Prime Video) :

- **Accueil vivant** : fond en *sunburst* deux-tons (rayons bleus rayonnants, signature de l'émission) rendu en Canvas, wordmark JEOPARDY! or à extrusion 3D, scintillement, boutons à reflet.
- **Accents néon** : glow cyan sur les titres, bannière champion en magenta néon — pendant que le bleu et l'or restent le cœur de la palette.
- **Intensité graduée** : l'accueil et les titres pètent ; le plateau de jeu reste sobre et lisible (les montants priment).
- **Tuiles-niveaux** texturées, pips dorés en volume, emblème diamant facetté en CSS 3D.

### Juice & récompense

Le « wow » est réservé aux moments rares, pour qu'il garde sa valeur :

- **Confetti à la montée de palier** : un burst de particules (Canvas maison, palette Néon Pop) se déclenche **une seule fois** quand tu décroches un nouveau palier — densité graduée : `!!!` (or) → streak (magenta + or) → **PARFAIT** (or + magenta + cyan). Pas de rejeu sur un *annuler*/recommit.
- **Daily Double réussi renforcé** : anneau or large autour du score + pulse du montant qui gonfle. Un raté garde le flash de perte normal (ça doit piquer).

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

Ouvre l'URL Netlify (ou `index.html` dans un navigateur). Choisis l'édition, la collection, puis l'épisode que tu regardes, et suis ton pointage. Bats les légendes, une émission à la fois.

## Stack

HTML / CSS / JavaScript vanilla. **Zéro dépendance, zéro build.** Un seul fichier : `index.html`. Rendu maison : Canvas 2D (accueil + confetti), SVG (pips), CSS 3D (diamant), `localStorage` (stats). **Son embarqué** : 6 samples Jeopardy! encodés en base64 directement dans le fichier (data-URI, lus via `HTMLAudioElement`), pour rester un seul fichier autonome — `index.html` pèse ~1,4 MB de ce fait. Polices Anton + Oswald (Google Fonts).

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

- **Persistance** : tes statistiques (médailles, streak, carrière) sont sauvegardées via `localStorage`. En revanche, le **pointage en cours d'un épisode** repart à zéro si tu recharges en pleine partie.
- **Mobile / iOS** : overscroll bloqué (`overscroll-behavior`) pour éviter le rubber-band haut/bas, et châssis Safari teinté en bleu (`theme-color`) — plein écran sans bandes blanches. Le son se débloque au premier *tap* (politique d'autoplay).
- **Son** : samples issus de la communauté (soundboards Jeopardy!). Marques et sons de l'émission appartiennent à Sony Pictures Television — usage **perso/solo** ici. Pour une diffusion publique, remplacer par des sons libres de droits.
- **Données** — catégories, finales, scores réels et positions des Daily Doubles parsés depuis le HTML brut de **J-Archive** (épisodes classiques) ; Pop Culture vient de **The Jeopardy! Fan**. Le détail du périmètre vit dans `notes/`.
- Les **finales de tournoi** se jouent sur 2 games (score cumulé) : le « gagnant » affiché par épisode est celui *du game*, pas forcément le champion du tournoi.
- Les **anciens épisodes** (avant nov. 2001, ex. Brad Rutter 2000) utilisaient des valeurs $100–$500 / $200–$1000 ; l'app affiche les valeurs modernes — un repère, pas un calque exact.
