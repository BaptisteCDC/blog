# Blog

Ensemble des articles - Blog personnel propulsé par Jekyll

## Installation

### Prérequis

- Ruby (version 2.7 ou supérieure)
- RubyGems
- GCC et Make

### Installation locale

1. Cloner le repository :
```bash
git clone https://github.com/BaptisteCDC/blog.git
cd blog
```

2. Installer les dépendances :
```bash
bundle install
```

3. Lancer le serveur de développement :
```bash
bundle exec jekyll serve
```

4. Ouvrir votre navigateur à l'adresse : `http://localhost:4000/blog/`

## Utilisation

### Créer un nouvel article

Les articles sont situés dans le dossier `_posts/`. Pour créer un nouvel article :

1. Créer un fichier au format `YYYY-MM-DD-titre-de-larticle.md`
2. Ajouter le front matter en haut du fichier :
```yaml
---
layout: post
title: "Titre de l'article"
date: YYYY-MM-DD HH:MM:SS +0100
categories: categorie
author: BaptisteCDC
---
```
3. Écrire le contenu en Markdown

### Créer un brouillon

Les brouillons sont situés dans le dossier `_drafts/`. Ils ne seront pas publiés automatiquement.

Pour prévisualiser les brouillons en local :
```bash
bundle exec jekyll serve --drafts
```

## Structure du projet

```
.
├── _config.yml       # Configuration du site
├── _posts/           # Articles publiés
├── _drafts/          # Brouillons
├── _layouts/         # Templates de mise en page
├── _includes/        # Composants réutilisables
├── assets/           # Fichiers CSS, JS, images
├── about.md          # Page "À propos"
├── index.md          # Page d'accueil
└── Gemfile           # Dépendances Ruby
```

## Déploiement

Ce blog peut être déployé sur GitHub Pages :

1. Configurer les GitHub Pages dans les paramètres du repository
2. Sélectionner la branche principale comme source
3. Le site sera disponible à l'adresse : `https://baptistecdc.github.io/blog/`

## Technologies

- [Jekyll](https://jekyllrb.com/) - Générateur de site statique
- [Minima](https://github.com/jekyll/minima) - Thème par défaut
- Markdown pour le contenu

## Licence

Voir le fichier [LICENSE](LICENSE) pour plus de détails.
