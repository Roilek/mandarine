# Instructions pour l'IA qui modifie ce site

Tu aides **Mandarine & Co** (agence événementielle à Sion, Valais : événements d'entreprise,
séminaires, conférences, manifestations grand public, stands, événements privés, location de
mobilier, Selfie Box) à modifier son site web. La personne qui te parle n'est pas développeuse :
explique simplement, sans jargon technique, et ne lui demande jamais de taper des commandes.

Hébergement : GitHub Pages. Chaque modification enregistrée sur la branche `main`
est mise en ligne automatiquement en 1 à 2 minutes.

## Comment le site est construit

Un site d'une seule page, sans outil de build, en français uniquement :

| Fichier | Contenu |
|---|---|
| `index.html` | Toute la page : textes, design (balise `<style>` en haut) et scripts (balise `<script>` en bas) |
| `img/` | Photos, logos et icônes, au format `.webp` (les photos envoyées depuis le téléphone arrivent dans `assets/photos/`, en `.jpg`) |

Sections de la page, dans l'ordre (attribut `id`) : `agence` (accueil), `evenements`
(types d'événements, en onglets), `entreprise`, `prestations`, `communication`, `selfie-box`,
`mobilier`, `realisations`, `a-propos`, `faq`, `contact`. Le menu du haut (`<nav id="menu">`)
et le pied de page pointent vers ces `id` : si tu renommes ou ajoutes une section, mets à jour
les liens.

## Règle n°1 : la location de mobilier existe à deux endroits

Chaque article de mobilier apparaît :
1. dans le HTML de la section `mobilier` : une carte `<div class="mob" data-id="…" data-cat="…">`
   avec photo, nom, description et prix affiché (`<span class="px">CHF 20.–</span>`) ;
2. dans la liste `MOB` au début du `<script>` en bas de page (`id`, `nom`, `prix`, `unite`),
   qui sert à calculer le total du panier et à rédiger la demande de devis.

Quand tu changes un prix, un nom, ou que tu ajoutes ou retires un article, **modifie les deux**,
avec le même `id`. Les catégories (`data-cat`) possibles sont celles des boutons de filtre :
`tables`, `assises`, `guidage`, `textiles`, `deco`, `luminaires`, `accessoires`.

## Ce qu'il ne faut pas casser

- Les demandes de devis (formulaire de contact, panier de mobilier, Selfie Box) ouvrent la
  messagerie du visiteur vers `info@mandarineandco.ch`. Si l'adresse e-mail change, la remplacer
  partout (liens `mailto:` et scripts en bas de page).
- Les coordonnées apparaissent aussi dans le bloc `application/ld+json` en haut de page
  (utilisé par Google) : les tenir à jour en même temps que la section contact.
- Garder le style existant (couleurs, polices Jost et DM Sans, arrondis) pour tout nouvel élément.
- Toute nouvelle image : texte `alt` descriptif, `loading="lazy"`, largeur et hauteur indiquées.
- Ne pas toucher à `.nojekyll`, ni à `CNAME` s'il existe (nom de domaine du site).
