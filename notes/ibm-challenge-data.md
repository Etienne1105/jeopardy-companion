# Pilote — IBM Challenge (S27, fév. 2011) — données J-Archive

> Source : J! Archive (j-archive.com), récupéré 2026-06-15.
> Joueurs : **Ken Jennings**, **Brad Rutter**, **Watson** (IA d'IBM). Format = joueurs individuels (pas d'équipes).

## ⚠️ DÉCOUVERTE DU PILOTE (à trancher au design)

Crave montre **3 épisodes**, mais en termes de *jeu Jeopardy* (board Simple + Double + Finale) il n'y a que **2 games** — parce que **Game 1 est étalé sur 2 épisodes TV** :

| Épisode Crave / Show J-Archive | Date | Contenu réel |
|---|---|---|
| Show #6086 (game_id 3575) | 14 fév 2011 | **Game 1 — manche Simple seulement** (6 cat.) |
| Show #6087 (game_id 3576) | 15 fév 2011 | **Game 1 — manche Double + Finale** (6 cat. + finale) |
| Show #6088 (game_id 3577) | 16 fév 2011 | **Game 2 — game complet** (Simple + Double + Finale) |

→ **Question de design** : on modélise par *game* (2 boards complets) ou par *épisode TV* (3 entrées, dont 2 « partielles ») ? Voir section finale.
→ **Bonne nouvelle** : c'est une **bizarrerie propre aux events spéciaux** (practice round + format sur 3 jours). Les épisodes normaux (Brad Rutter S17, ToCs, Holzhauer) = 1 épisode = 1 game complet.

---

## GAME 1 (board complet = shows 6086 + 6087)

- **Simple** (14 fév) : `Literary Character APB` · `Beatles People` · `Olympic Oddities` · `Name the Decade` · `Final Frontiers` · `Alternate Meanings`
- **Double** (15 fév) : `Etude, Brute` · `Hedgehog-Podge` · `Don't Worry About It` · `The Art of the Steal` · `Cambridge` · `"Church" & "State"`
- **Finale** : `U.S. Cities`
- **Scores finaux Game 1** : Watson **$35 734** · Brad Rutter **$10 400** · Ken Jennings **$4 800**
- **Gagnant Game 1** : Watson
- **Détail savoureux (line anti-spoiler)** : en Finale (catégorie *U.S. Cities*), Watson répond « What is Toronto????? » — un ratage resté célèbre — mais gagne quand même la manche haut la main.

## GAME 2 (board complet = show 6088, 16 fév)

- **Simple** : `EU, the European Union` · `Actors Who Direct` · `Dialing for Dialects` · `Breaking News` · `One Buck or Less` · `Also on Your Computer Keys`
- **Double** : `Nonfiction` · `Legal "E"s` · `What to Wear?` · `U.S. Geographic Nicknames` · `Magical Mouse-tery Tour` · `Familiar Sayings`
- **Finale** : `19th Century Novelists`
- **Scores finaux Game 2** : Watson **$41 413** · Ken Jennings **$19 200** · Brad Rutter **$11 200**
- **Gagnant Game 2** : Watson
- **Détail (line)** : les trois répondent juste en Finale (« Bram Stoker »).

## RÉSULTAT GLOBAL DU MATCH (2-game total points)

- **Watson $77 147** · Ken Jennings $24 000 · Brad Rutter $21 600
- **Watson remporte le million** (1 M$ → reversés à World Vision + World Community Grid).

---

## Questions de design ouvertes (pour Etienne)

1. **Game 1 sur 2 épisodes** : board par *game* (2 entrées) ou par *épisode TV* (3 entrées dont 2 partielles) ?
2. **Joueurs individuels vs équipes** : le modèle actuel (`teams:[3]`) doit accepter des **joueurs** pour le classique. Renommer en `players` ou garder générique ?
3. **Résultat de tournoi** : afficher le score par game, le cumul, ou les deux ?
