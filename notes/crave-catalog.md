# Catalogue Crave — Jeopardy! classique (collections)

> Source : app Crave d'Etienne (source primaire), capturée le 2026-06-15.
> **Statut : PROVISOIRE — à confirmer si la liste est complète.**
> Données d'épisodes à récupérer depuis **J-Archive** (Crave = vidéos seulement).

## Collections disponibles (hors saison en cours S42, à exclure)

| Saison | Épisodes | ~Nb | Identification (à vérifier) |
|--------|----------|-----|------------------------------|
| **S17** | 41–45 | 5 | Brad Rutter — run original. ✅ **LIVRÉ** (vraies dates J-Archive : 30 oct → 3 nov 2000 ; Crave avait décalé d'un jour). |
| **S21** | 40–75 | 36 | Probable **Ultimate Tournament of Champions 2005**. |
| **S27** | IBM Challenge | 3 | **Watson vs Ken Jennings & Brad Rutter** (fév. 2011). ✅ **LIVRÉ** (2 games). |
| **S32** | 41–50 | 10 | **Tournament of Champions 2015**. |
| **S34** | 41–50 | 10 | **Tournament of Champions 2017**. |
| **S35** | 163–194 | 32 | Probable **run de James Holzhauer** (avr.–juin 2019). |
| **S36** | 41–50 | 10 | **Tournament of Champions 2019** (Holzhauer vs Boettcher vs Barcomb). |

**Total ≈ 106 épisodes.**

## Notes de format
- Format standard Jeopardy! : 6 catégories Simple ($200–$1000), 6 Double ($400–$2000), Finale. → colle à la structure de l'app.
- **Spécificité tournois** : finales de ToC sur 2 jours (scores cumulés), demi-finales, wild cards. Le *board* reste standard ; c'est la sémantique du « résultat » (gagnant) qui diffère.
- L'IBM Challenge (Watson) : format spécial sur 2 matchs / 3 jours.

## À trancher
- [ ] La liste est-elle complète ? (d'autres collections ?) — **en attente**
- [x] Méthode : pilote sur 1 collection avant de tout baker. **→ PILOTE = IBM Challenge (S27, 3 ép, Watson 2011)** *(validé par Etienne 2026-06-15)*
- [ ] Périmètre v1 complet (~106) : à décider après le pilote.

## Prochaine étape (reprise)
1. Récupérer les données J-Archive de l'IBM Challenge (3 matchs, fév. 2011) → `notes/`.
2. Valider les données avec Etienne.
3. Designer la structure (Itération → Saison/Collection → Épisode) + l'état de case « neutre ».
4. ⚠️ Gate brainstorming : design approuvé AVANT de baker dans `index.html`.
