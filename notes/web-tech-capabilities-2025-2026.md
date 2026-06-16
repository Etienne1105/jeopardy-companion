# Capacités web modifiables (HTML/CSS/JS) — état 2025-2026

> Source : référence exhaustive fournie par Etienne (2026-06-15). Nomenclature complète conservée comme référence ; ci-dessous l'**essentiel opérationnel** pour CETTE app (single-file, Netlify, **compat cross-device ACTIVE** par CLAUDE.md d'Etienne).

## ✅ Socle sûr (Baseline — utiliser sans réserve)
Balises sémantiques + ARIA · Flexbox/Grid (+ subgrid) · custom properties `var()` · `clamp()/min()/max()` · `aspect-ratio` · **container queries de taille** (widely available août 2025) · **`:has()`** (Baseline déc. 2023) · **nesting CSS natif** · **`@layer`** · **`@property`** (typage + animation de custom props) · **`@scope`** · **`color-mix()` / OKLCH/OKLAB / `light-dark()`** · `@starting-style` + `transition-behavior: allow-discrete` (animer `display`, entrées/sorties) · **Popover API** (Baseline 27 jan. 2025) · **view transitions same-document** (`document.startViewTransition`, oct. 2025) · `text-wrap: balance` · unités viewport dynamiques `dvh/svh/lvh` · `scroll-snap` · Web Audio · localStorage · Web Animations API (`element.animate`) · Canvas 2D · SVG + filtres.

## ⚠️ Progressive enhancement obligatoire (encadrer par `@supports`, repli propre)
scroll-driven animations (`animation-timeline`) · `if()` inline (Chromium) · `interpolate-size`/`calc-size()` · customizable `<select>` (`appearance: base-select`) · carousels CSS (`::scroll-marker/-button`) · `sibling-index()/sibling-count()` · `scroll-state()` container queries · view transitions **cross-document** (manque Firefox) · masonry (`grid-lanes`) · `field-sizing: content` · interest invokers · `contrast-color()`.
**Anchor positioning** = Baseline récent (jan. 2026) mais garder un repli (sous-valeurs ont traîné).

## Règle de décision
Passer une feature de « progressive enhancement » à « socle sûr » quand elle est **Baseline dans les 3 moteurs** (Chromium/Firefox/WebKit). Pattern : écrire le style par défaut d'abord, puis layer l'avancé dans `@supports`. **L'absence de support doit dégrader proprement, jamais casser.**

## Implications pour Géopardie/Jeopardy! (single-file)
- Cible = navigateurs récents (Etienne + mobile devant TV). « Newly available » suffit pour les artifacts perso, mais **garder la dégradation gracieuse** (compat technique active).
- On utilise déjà : Canvas 2D (fond accueil), Web Animations/CSS anim, SVG (pips/couronne), localStorage (stats), custom properties, clamp, dvh. Tout Baseline. ✅
- Candidats Baseline utiles non encore exploités : **view transitions same-document** (transitions entre écrans home/selector/game/stats — plus fluide que showScreen display:none) ; `@property` (animer des dégradés/glow proprement) ; container queries (tuiles responsives). À considérer en polish, en restant dégradable.
- Éviter en dur (sans `@supports`) : scroll-driven anim, `if()`, anchor positioning sans repli.

## Caveats
Scroll-driven animations = encore expérimental (Firefox derrière flag mi-2026). Anchor positioning = sous-valeurs à tester. Numéros de version exacts variables ; les verdicts Baseline (interop vs Chromium-only) sont fiables. Re-valider via webstatus.dev/MDN/caniuse au moment de livrer une feature émergente.
