# Guide ultra-pratique: ajouter une galerie ou un article blog

Ce guide est fait pour une personne non technique.
Tu n'as presque rien à coder: tu crées des dossiers, tu ajoutes des images, tu donnes un prompt à l'agent.

## 1) Avant de commencer (1 minute)

1. Ouvre le projet dans VS Code.
2. Vérifie que tu vois la colonne de gauche `Explorateur` avec les dossiers (`galleries`, `blog-techniques-photographiques`, etc.).

Repère visuel:
`Explorateur (gauche) -> racine du projet -> index.html`

## 2) Règles de nommage (important)

1. Pas d'espace dans les noms de fichiers ou dossiers.
2. Utilise `_` (underscore) si besoin.
3. Garde un nom cohérent:
- Galerie: `Islande`, images `Islande_1.jpg`, `Islande_2.jpg`, etc. OU `Islande_1_nom_plus_precis.jpg` , `Islande_2_nom_plus_precis.jpg`
- Blog: `blog_2`, images `image_1.jpg`, `image_2.jpg`, etc. OU `image_1_nom_plus_precis.jpg`, `image_2_nom_plus_precis.jpg`
4. Les images doivent être déjà optimisées et finales avant ajout.




## 3) Ajouter une nouvelle galerie (pas à pas humain)

Exemple: tu veux ajouter la galerie `Islande`.

### Étape A - Ajouter l'image de couverture à la racine

1. Dans `Explorateur`, repère la racine du projet (là où il y a `index.html`).
2. Glisse-dépose l'image de couverture dans cette racine.
3. Nom recommandé: `image_Islande.jpg`.

Repère visuel:
`racine projet -> index.html + style.css + image_Islande.jpg`

### Étape B - Créer le dossier de la galerie

1. Dans `Explorateur`, va sur le dossier `galleries`.
2. `Ctrl + clic` sur `galleries` (ou clic droit).
3. Clique `Nouveau dossier` (`New Folder`).
4. Tape `Islande`, puis `Entrée`.

Repère visuel:
`galleries/Islande/`

### Étape C - Créer le sous-dossier images

1. `Ctrl + clic` sur `galleries/Islande`.
2. Clique `Nouveau dossier` (`New Folder`).
3. Tape `images`, puis `Entrée`.

Repère visuel:
`galleries/Islande/images/`

### Étape D - Ajouter les photos de la galerie

1. Ouvre ton dossier local de photos.
2. Glisse-dépose les photos dans `galleries/Islande/images/`.
3. Vérifie les noms:
`Islande_1.jpg`, `Islande_2.jpg`, `Islande_3.jpg`, etc.

### Étape E - Préparer les infos à donner à l'agent

Tu dois fournir:
1. `Nom affiché (= Nom du titre)`: `Islande`
2. `Nom dossier`: `Islande`
3. `Image couverture`: `image_Islande.jpg`
4. `Description`: texte court ou long qui apparaîtra dans `index.html`

## 4) Prompt copier-coller pour l'agent (galerie)

```text
Tu modifies ce repo statique sans refactor.

Je veux ajouter une nouvelle galerie.

Données:
- Nom affiché: [NOM_AFFICHE]
- Nom dossier galerie: [NOM_DOSSIER]
- Image couverture (déjà ajoutée à la racine): [NOM_IMAGE_COUVERTURE]
- Description du post (index): [TEXTE_DESCRIPTION]
- Images déjà présentes dans: galleries/[NOM_DOSSIER]/images/

Actions demandées (déterministes):
1) Crée le fichier galleries/[NOM_DOSSIER]/[NOM_DOSSIER].html en copiant la structure d'une galerie existante.
2) Dans ce fichier, garde le même header/nav que les autres galeries.
3) Génère les blocs <img> dans l'ordre alphanumérique des fichiers présents dans galleries/[NOM_DOSSIER]/images/.
4) Ajoute un nouveau bloc <div class="post"> à la fin de la liste dans index.html.
5) Dans ce bloc:
   - src image = [NOM_IMAGE_COUVERTURE]
   - lien = galleries/[NOM_DOSSIER]/[NOM_DOSSIER].html
   - titre = [NOM_AFFICHE]
   - description = [TEXTE_DESCRIPTION]
6) Assure la validité HTML:
   - <title> correct
   - <h1> correct
   - balises fermées (<main>, <p>, etc.)
7) Ne modifie pas les anciens posts.
8) Donne la liste exacte des fichiers créés/modifiés.
```





## 5) Ajouter un article de blog technique (pas à pas humain)

Exemple: tu veux ajouter `blog_2`.

### Étape A - Ajouter l'image de carte (aperçu article)

1. Dans `Explorateur`, ouvre `blog-techniques-photographiques`.
2. Glisse-dépose l'image de carte dans ce dossier.
3. Nom recommandé: `blog_2.jpg`.

Repère visuel:
`blog-techniques-photographiques/blog_2.jpg`

### Étape B - Créer le dossier de l'article

1. Va dans `blog-techniques-photographiques/posts`.
2. `Ctrl + clic` sur `posts` (ou clic droit).
3. Clique `Nouveau dossier` (`New Folder`).
4. Tape `blog_2`, puis `Entrée`.

Repère visuel:
`blog-techniques-photographiques/posts/blog_2/`

### Étape C - Créer le sous-dossier images

1. `Ctrl + clic` sur `blog-techniques-photographiques/posts/blog_2`.
2. Clique `Nouveau dossier` (`New Folder`).
3. Tape `images`, puis `Entrée`.

Repère visuel:
`blog-techniques-photographiques/posts/blog_2/images/`

### Étape D - Ajouter les images de l'article

1. Glisse-dépose les images dans `.../blog_2/images/`.
2. Noms recommandés:
`image_1.jpg`, `image_2.jpg`, `image_3.jpg`, etc.

### Étape E - Préparer le texte à donner à l'agent

Tu dois fournir:
1. `Titre article`
2. `Description courte` pour la carte de la page blog
3. Un plan texte/image clair, dans l'ordre de lecture

### Étape F - Format simple recommandé pour le contenu blog (très important)

Le plus simple: écrire le contenu dans un fichier texte (ou le coller dans le prompt) avec des marqueurs.

Où créer ce fichier:
`blog-techniques-photographiques/posts/[BLOG_ID]/PLAN_ARTICLE.txt`

Exemple concret:
`blog-techniques-photographiques/posts/blog_2/PLAN_ARTICLE.txt`

Format à suivre:

```text
[TITRE]
Mon titre d'article

[INTRO]
Texte d'introduction...

[TEXTE]
Premier bloc de texte...

[IMAGE:image_1.jpg]

[TEXTE]
Texte après la première image...

[IMAGE:image_2.jpg]

[TEXTE]
Conclusion...
```

Règles:
1. Chaque image référencée dans `[IMAGE:nom.jpg]` doit exister dans `posts/[BLOG_ID]/images/`.
2. L'ordre des blocs dans ce texte = l'ordre final de l'article.
3. Si tu veux texte -> image -> texte -> image, écris exactement cet enchaînement.

## 6) Prompt copier-coller pour l'agent (blog technique)

```text
Tu modifies ce repo statique sans refactor.

Je veux ajouter un nouvel article de blog technique.

Données:
- Identifiant article: [BLOG_ID] (ex: blog_2)
- Titre article: [TITRE]
- Description courte pour la carte sur la page blog index: [DESCRIPTION_CARTE]
- Image carte déjà ajoutée dans blog-techniques-photographiques/: [NOM_IMAGE_CARTE] (ex: blog_2.jpg)
- Fichier plan (optionnel): blog-techniques-photographiques/posts/[BLOG_ID]/PLAN_ARTICLE.txt
- Contenu article avec marqueurs [TEXTE] et [IMAGE:nom_fichier]: [COLLER_ICI_LE_PLAN]
- Images déjà présentes dans: blog-techniques-photographiques/posts/[BLOG_ID]/images/

Actions demandées (déterministes):
1) Crée le fichier blog-techniques-photographiques/posts/[BLOG_ID]/[BLOG_ID].html.
2) Utilise la même structure que blog-techniques-photographiques/posts/blog_1/blog_1.html (header/nav/main).
3) Respecte strictement l'ordre de mes blocs:
   - [TEXTE] -> bloc texte HTML
   - [IMAGE:nom.jpg] -> bloc image HTML avec ce fichier précis
4) Le texte de l'article doit rester strictement identique à mon contenu (mêmes mots, même langue, pas de reformulation).
5) Tu peux uniquement améliorer la mise en forme HTML pour la lisibilité:
   - découper en paragraphes
   - créer des listes si le texte contient déjà des puces/numéros
   - structurer en sections
   - sans ajouter ni retirer de contenu texte
6) Ne pas inventer d'image ni changer l'ordre.
7) Dans blog-techniques-photographiques/blog-techniques-photographiques.html, ajoute une nouvelle carte à la fin de <section class="blog-posts">:
   - lien vers posts/[BLOG_ID]/[BLOG_ID].html
   - image [NOM_IMAGE_CARTE]
   - titre [TITRE]
   - description [DESCRIPTION_CARTE]
8) Assure la validité HTML:
   - <title> correct
   - <h1> correct
   - balises fermées (<main>, <p>, etc.)
9) Ne modifie pas les anciens articles.
10) Donne la liste exacte des fichiers créés/modifiés.
```

## 7) Check rapide après modification (méthode non technique)

À faire avant de pousser (`push`) les changements.

### Étape A - Lancer le site avec Live Server

1. Dans VS Code, clique sur `index.html` dans `Explorateur`.
2. `Ctrl + clic` sur `index.html` (ou clic droit).
3. Clique `Ouvrir avec Live Server` (`Open with Live Server`).

Alternative si tu ne vois pas l'option:
1. Clique le bouton `Aller en direct` (`Go Live`) en bas à droite de VS Code.
2. Puis ouvre `index.html`.

### Étape B - Vérifier dans le navigateur

1. Le navigateur s'ouvre sur une adresse de type:
`http://127.0.0.1:5501/index.html`
2. Vérifie que la nouvelle carte galerie ou blog apparaît bien.
3. Clique sur la nouvelle carte.
4. Vérifie:
- les images se chargent
- le titre est bon
- la navigation en haut fonctionne
5. Reviens en arrière et re-clique pour confirmer.

### Étape C - Si quelque chose ne va pas

1. Ne pousse pas (`push`) tout de suite.
2. Retourne dans VS Code.
3. Redonne le prompt à l'agent en précisant ce qui ne va pas.
4. Relance le check avec `Ouvrir avec Live Server`.

## 8) Mini check-list "prêt à push"

1. Les fichiers/dossiers sont au bon endroit.
2. Les noms de fichiers sont corrects et sans espaces.
3. La nouvelle carte est visible sur la bonne page.
4. Le clic ouvre la bonne page.
5. Les images se chargent.
6. La navigation fonctionne.
7. Seulement après ça: passer à `commit` puis `push`.

## 9) Commit + Push (méthode terminal, plus simple)

### Étape A - Ouvrir le terminal dans VS Code

1. Raccourci clavier (Mac, clavier QWERTY): `Shift + Command + ~`.
2. Si ça ne marche pas: menu `Terminal` -> `Nouveau terminal`.

### Étape B - Ajouter tous les fichiers modifiés

Dans le terminal, tape:

```bash
git add .
```

### Étape C - Faire un commit avec un message clair

Dans le terminal, tape:

```bash
git commit -m "Ajout blog technique blog_2"
```

Tu peux adapter le message, par exemple:
- `Ajout galerie Islande`
- `Ajout blog technique blog_2`

Pourquoi c'est important:
Chaque commit est un point de retour. Si un problème arrive plus tard, on peut revenir à une version précédente.

### Étape D - Pousser sur GitHub

Dans le terminal, tape:

```bash
git push origin main
```


## 10) Vérifier que le site est en ligne (GitHub Pages)

Après le push, attends en général 1 à 5 minutes.

URL du site:
`https://dume-peraldi.github.io`

Vérification:
1. Ouvre cette URL dans le navigateur.
2. Recharge la page (Ctrl+R / Cmd+R).
3. Vérifie que la nouvelle galerie ou le nouvel article est visible.
4. Clique dessus pour confirmer que tout fonctionne en ligne.

## 11) Résumé en une ligne

Humain: créer dossiers + ajouter images + fournir texte.
Agent: créer/mettre à jour HTML selon le prompt.
Humain: vérifier avec `Ouvrir avec Live Server`, puis `commit`, puis `push`, puis vérifier `https://dume-peraldi.github.io`.